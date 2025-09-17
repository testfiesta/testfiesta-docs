---
description: >-
  Integrations connect TestFiesta to external tools, enhancing defect tracking,
  storage, and automation for TestRail users transitioning to a more flexible
  platform.
---

# Integrations For TestRail Users

## Setting Up Integrations

These integrations streamline workflows, mirroring TestRail’s capabilities while adding modern efficiencies. Below, we detail how to set up each integration, with steps to ensure a smooth start.

<details>

<summary>Issue Tracking (Jira &#x26; GitHub)</summary>

* **Purpose:** Link TestFiesta to Jira or GitHub to manage defects directly from test executions, similar to TestRail’s defect plugins but with a more intuitive workflow.
* **Setup:**
  1. Navigate to Admin > Integrations in TestFiesta.
  2. Select Jira or GitHub and enter your account credentials (e.g., Jira API token or GitHub personal access token; see [docs.testfiesta.com/integrations](https://docs.testfiesta.com/integrations)).
  3. Map defect fields (e.g., title, description) to ensure consistency with TestFiesta’s test execution data.
  4. Test the integration by creating a defect from a failed test execution—bugs link automatically to the execution, viewable in the Defects tab or the external tool.
* **Benefits:** Defects created during testing open directly in Jira or GitHub, with full details (e.g., comments, attachments) preserved. Supports standalone defect logging outside executions.
* **Tip:** Validate the integration in a demo project to confirm defect linking before rolling out to your team.

</details>

<details>

<summary>Storage (Bring Your Own Storage - BYOS)</summary>

* **Purpose:** Each user gets 50GB of free storage for attachments (e.g., screenshots, test data). For larger needs, BYOS integrates with cloud providers to scale storage seamlessly.
* **Setup:**
  1. Go to Admin > Storage and enable BYOS.
  2. Choose a provider (AWS, Google Cloud, or Dropbox) and provide access credentials (e.g., AWS S3 bucket keys).
  3. Specify the storage bucket for TestFiesta’s data, ensuring attachments are stored externally.
* **Benefits:** Extends storage beyond 50GB without hidden fees, ideal for teams with large datasets (e.g., video attachments). Maintains performance for enterprise-scale testing.
* **Tip:** Schedule storage jobs off-peak (configurable in Admin > Data) to avoid impacting testing.

</details>

<details>

<summary>Automation (TestFiesta's 🚚 <a href="https://github.com/testfiesta/tacotruck?tab=readme-ov-file#getting-started">Tacotruck</a>)</summary>

* **Purpose:** Tacotruck is an open-source tool that pushes automated test results into TestFiesta runs or exports quality data to other systems, simplifying automation for TestRail users transitioning to TestFiesta. It integrates with CI/CD pipelines for seamless test reporting.
* **Setup:**
  1. Visit [github.com/testfiesta/tacotruck](https://github.com/testfiesta/tacotruck) for setup guides and documentation.
  2. In TestFiesta, go to Admin > API Keys and generate an API key for your project or organization.
  3. Configure tacotruck in your CI/CD pipeline (e.g., GitHub Actions, Jenkins) using the API key to send results to TestFiesta.
  4. Map test result statuses (e.g., “pass” to “passed,” “fail” to “failed”) to align with TestFiesta’s reporting (see [docs.testfiesta.com/automation](https://docs.testfiesta.com/automation)).
  5. Test the setup in a demo project to confirm results display in TestFiesta’s run progress bars.
* **Benefits:**
  * Combines automated (e.g., Selenium, Cypress) and manual test results in TestFiesta runs, with real-time pass/fail ratios.
  * Supports GitHub Actions for easy pipeline integration, ideal for developer-driven teams.
  * Enables data export for custom analytics or third-party tools.
* **For TestRail Users:** Unlike TestRail’s API, which requires custom scripting for automation, tacotruck offers pre-built CI/CD integration, making it easier to report automated results.
* **Tip:** Validate tacotruck in a staging project to ensure correct status mapping. For issues, use Help & Feedback or contact [testfiesta.com/contact-us](https://testfiesta.com/contact-us).

</details>

Learn all about TestFiesta's full TestRail integration that allow for a full migration from TestRail on the next page! Click "Next" to open "TestRail API Integration Guide".
