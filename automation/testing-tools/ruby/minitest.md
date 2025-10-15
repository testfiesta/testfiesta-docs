# MiniTest

<figure><img src="../../../.gitbook/assets/ruby.png" alt="" width="188"><figcaption></figcaption></figure>

Minitest is Ruby's default testing framework that comes built-in with Ruby. It provides a clean, simple syntax for writing tests with support for both test-unit style and spec-style testing. Minitest is fast, lightweight, and includes features like assertions, mocking, benchmarking, and parallel test execution. It's the perfect choice for Ruby applications that need reliable testing without the overhead of larger frameworks. Check out simple MinTest [example](https://github.com/testfiesta/tacotruck-examples/tree/main/demo-ruby-minitest-tf).

### Generate XML Report

Minitest can generate XML reports using the `minitest-reporters` gem, which provides JUnit-style XML output compatible with CI/CD systems.

#### Gemfile Configuration

Add the required gems to your `Gemfile`:

```ruby
group :test do
  gem 'minitest', '~> 5.20'
  gem 'minitest-reporters', '~> 1.6'
end
```

#### Test Helper Configuration

Configure XML reporting in your `test/test_helper.rb`:

```ruby
require 'minitest/autorun'
require 'minitest/reporters'

# Configure JUnit XML reporter
Minitest::Reporters.use! [
  Minitest::Reporters::JUnitReporter.new('test/reports')
]
```

#### Alternative Configuration with Multiple Reporters

For both console and XML output:

```ruby
require 'minitest/autorun'
require 'minitest/reporters'

Minitest::Reporters.use! [
  Minitest::Reporters::SpecReporter.new,
  Minitest::Reporters::JUnitReporter.new('test/reports')
]
```

#### Rake Task Configuration

Create a `Rakefile` for running tests:

```ruby
require 'rake/testtask'

Rake::TestTask.new(:test) do |t|
  t.libs << 'test'
  t.libs << 'lib'
  t.test_files = FileList['test/**/*_test.rb']
  t.verbose = true
end

task default: :test
```

### Install Tacotruck CLI

```bash
$ npm install -g @testfiesta/tacotruck
```

### Submit Test Results

{% tabs %}
{% tab title="Testfiesta" %}
```bash
  run:submit \
  --token testfiesta_... \
  --handle orgHandle \
  --project projectKey \
  --name runName \
  --data test/reports/*.xml
```
{% endtab %}
{% endtabs %}

### GitHub Action

```yaml
name: minitest-tests
on:
  pull_request:
    branches:
      - main
  push:
    branches:
      - main

jobs:
  test:
    runs-on: ubuntu-latest
    strategy:
      matrix:
        ruby-version: ['3.0', '3.1', '3.2']
    
    steps:
      - uses: actions/checkout@v4
      
      - name: Set up Ruby ${{ matrix.ruby-version }}
        uses: ruby/setup-ruby@v1
        with:
          ruby-version: ${{ matrix.ruby-version }}
          bundler-cache: true
          
      - name: Create test reports directory
        run: mkdir -p test/reports
        
      - name: 🧪 Run Minitest Tests
        run: bundle exec rake test
        
      - name: Report Results
        if: always()
        uses: testfiesta/tacotruck-action@v1
        with:
          provider: testfiesta
          handle: handle
          project: project
          base-url: https://api.testfiesta.com
          credentials: ${{ secrets.TESTFIESTA_API_KEY }}
          run-name: Minitest CI run ${{ github.run_number }}
          results-path: ./test/reports/*.xml
```

### Rails Application GitHub Action

For Rails applications with Minitest:

```yaml
name: rails-minitest-tests
on:
  pull_request:
    branches:
      - main
  push:
    branches:
      - main

jobs:
  test:
    runs-on: ubuntu-latest
    
    services:
      postgres:
        image: postgres:14
        env:
          POSTGRES_PASSWORD: postgres
        options: >-
          --health-cmd pg_isready
          --health-interval 10s
          --health-timeout 5s
          --health-retries 5
    
    steps:
      - uses: actions/checkout@v4
      
      - name: Set up Ruby
        uses: ruby/setup-ruby@v1
        with:
          ruby-version: '3.2'
          bundler-cache: true
          
      - name: Set up Database
        env:
          DATABASE_URL: postgres://postgres:postgres@localhost:5432/test
        run: |
          bundle exec rails db:create
          bundle exec rails db:migrate
          
      - name: Create test reports directory
        run: mkdir -p test/reports
        
      - name: 🧪 Run Rails Tests
        env:
          DATABASE_URL: postgres://postgres:postgres@localhost:5432/test
        run: bundle exec rails test
        
      - name: Report Results
        if: always()
        uses: testfiesta/tacotruck-action@v1
        with:
          provider: testfiesta
          handle: handle
          project: project
          base-url: https://api.testfiesta.com
          credentials: ${{ secrets.TESTFIESTA_API_KEY }}
          run-name: Rails Minitest CI run ${{ github.run_number }}
          results-path: ./test/reports/*.xml
```

### Minitest Parallel Execution

Minitest supports parallel test execution out of the box. Configure in your test helper:

#### Basic Parallel Configuration

```ruby
# test/test_helper.rb
require 'minitest/autorun'
require 'minitest/reporters'

# Enable parallel execution
Minitest.parallel_executor = Minitest::Parallel::Executor.new(4)

Minitest::Reporters.use! [
  Minitest::Reporters::JUnitReporter.new('test/reports')
]
```

#### Rails Parallel Testing

For Rails applications, use the built-in parallel testing:

```bash
# Run tests in parallel (Rails 6+)
bundle exec rails test:parallel

# Specify number of workers
PARALLEL_WORKERS=4 bundle exec rails test:parallel
```

### Support and Resources

* [TacoTruck Examples](https://github.com/testfiesta/tacotruck-examples)
* [MiniTest Docs](https://app.gitbook.com/u/gS6tbNiokYObe8a29Tb0OBWSW1x1)
* [Tacotruck Issues](https://github.com/testfiesta/tacotruck/issues)
* [**CLI Reference**](../../tacotruck-cli/)
* [Tacotruck Github Action](https://github.com/testfiesta/tacotruck-action)
