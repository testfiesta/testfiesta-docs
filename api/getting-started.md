# Getting Started with TestFiesta API

TestFiesta provides a RESTful API that allows you to programmatically interact with your test cases, test runs, and other resources. This guide will help you get started with using our API.

## Authentication

All API requests must be authenticated using an API token. This token should be included in the `Authorization` header of your HTTP requests using the Bearer authentication scheme:

```bash
Authorization: Bearer your_api_token_here
```

### Creating an API Token

First, log in to your TestFiesta account.

On the top navigation bar, there is a user dropdown menu. Click on it and select "Settings".
<image src="../.gitbook/assets/api-getting-started-1.png" alt="Settings menu" >

On the settings page, navigate to the "API Keys" section.
<image src="../.gitbook/assets/api-getting-started-2.png" alt="API Keys section" >

After clicking on the "Create API key" button, a slide-out form will open.
<image src="../.gitbook/assets/api-getting-started-3.png" alt="Create API key form" >

Fill in the form with the following details:
- Give your token a descriptive name
- Set an expiration date. You can also customize the expiration date if not available on the dropdown using a custom date picker in the form by choosing "Custom Date" option. Also you can set the token to never expire by choosing "No expiration" option.
- Set the token permissions. You can select the permissions you want to grant to the API key.


After you fill in the form, click on the "Create" button. A dialog will open asking you to copy the API key.
<image src="../.gitbook/assets/api-getting-started-4.png" alt="Copy API key" >
API Key is prefixed with `testfiesta_`. You can use this API key in your HTTP requests. Click on the "I've saved my API code" checkbox and then click "Got it" to close the dialog after you have copied the API key.

⚠️ **Important**: Keep your API token secure and never share it. If your token is compromised, revoke it immediately and create a new one.

## Next Steps

- Check out our [API Endpoints](./api-endpoints.md) documentation for detailed information about available endpoints.