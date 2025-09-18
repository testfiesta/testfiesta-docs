---
description: >-
  This page details TestFiesta’s automation capabilities for TestRail users,
  focusing on tacotruck and data management to support seamless integration with
  existing workflows.
---

# API & Automation

## Taco Truck For Automation

* **Overview:** Tacotruck [github.com/testfiesta/tacotruck](https://github.com/testfiesta/tacotruck) is an open-source tool that pushes automated test results into TestFiesta runs or exports data, simplifying automation for TestRail users.
* **Setup:**
  1. Visit [github.com/testfiesta/tacotruck](https://github.com/testfiesta/tacotruck) for setup guides.
  2. Generate an API key in Admin > API Keys.
  3. Configure tacotruck in your CI/CD pipeline (e.g., GitHub Actions, Jenkins) to send results.
  4. Map statuses (e.g., “pass” to “passed”) per [docs.testfiesta.com/automation](https://docs.testfiesta.com/automation).
  5. Test in a demo project to verify run progress bars.
* **Benefits:** Unifies automated (e.g., Selenium, Cypress) and manual results; supports GitHub Actions for CI/CD; enables data export for custom analytics.
* **For TestRail Users:** Tacotruck simplifies automation compared to TestRail’s scripting-heavy API, with pre-built pipeline support.

## Data Management

* **Policies:** In Admin > Data, set auto-archive/delete rules for entities (e.g., runs, plans) based on inactivity (e.g., archive after 20 days). Schedule jobs off-peak.
* **Benefits:** Prevents database bloat, ensuring scalability for automation-heavy workflows.
* **For TestRail Users:** Unlike TestRail, TestFiesta’s policies optimize performance for large datasets.

TestFiesta’s tacotruck and data management make it a flexible alternative to TestRail’s automation.
