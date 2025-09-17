# TestRail API Integration Deep Dive

This page provides a detailed guide for TestRail users transitioning to TestFiesta, focusing on migration and integration with TestRail. It covers what data migrates, how synchronization works, strategic migration approaches, and best practices to ensure a smooth transition with minimal disruption.

## What Is/Isn't Migrated

The table below outlines which TestRail data migrates to TestFiesta and what remains behind, helping you plan your migration.

| Data Type              | Status       | Details                                                                                                                                                        |
| ---------------------- | ------------ | -------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| Test Cases             | Migrated     | &#xD;Includes all case details: steps, expected results, priorities, preconditions, custom fields, and TestFiesta’s shared steps (e.g., reusable login flows). |
| Test Runs/Executions   | Migrated     | Includes runs, execution statuses (e.g., Passed, Failed), comments, and timestamps.                                                                            |
| Test Plans             | Migrated     | Includes full plan structure, linked runs, and configurations.                                                                                                 |
| Milestones             | Migrated     | Includes milestone details, due dates, and linked runs/plans.                                                                                                  |
| Attachments            | Migrated     | Includes all files attached to cases, runs, or plans (e.g., screenshots, test data).                                                                           |
| History                | Migrated     | Includes audit trails and execution history (e.g., who ran a test, when, and results).                                                                         |
| User Settings          | Not Migrated | Personal preferences (e.g., UI color schemes, notification settings) are not transferred; reset in TestFiesta.                                                 |
| External Integrations  | Not Migrated | TestRail’s integrations (e.g., Jira, GitHub) must be reconfigured in TestFiesta via Admin > Integrations.                                                      |
| Temporary Session Data | Not Migrated | Ephemeral data (e.g., active user sessions, temporary exports) is not migrated, as it’s not part of TestRail’s core database.                                  |

## How The Sync Works & When

* **Mechanism:** TestFiesta’s TestRail API integration enables bidirectional synchronization. Connect via Admin > Integrations > TestRail using your TestRail API credentials [TestRail API docs](https://support.testrail.com/hc/en-us/articles/7076948376724-API-reference). Changes in TestRail (e.g., new test cases) or TestFiesta (e.g., updated run statuses) sync with precise field mappings (e.g., TestRail’s “Priority” to TestFiesta’s “Priority”).
* **Timing:**
  * Initial Import: Completes in minutes (e.g., 5–10 minutes for a medium-sized TestRail project), pulling all data into a TestFiesta project.
  * Ongoing Sync: Updates occur in near real-time, with configurable polling intervals (e.g., every 5 minutes) to balance performance and data consistency.
  * Disabling Sync: Turn off sync in Admin > Integrations after full migration to prevent conflicts or duplicate updates.
* **Validation:** Review migrated data in a TestFiesta project or staging environment. Refresh the UI to resolve minor display issues (e.g., folder loading glitches noted in testing).
* **For TestRail Users:** Unlike TestRail’s one-way exports, TestFiesta’s bidirectional sync supports parallel use during evaluation, ensuring no data loss.
* **Tip:** Test sync in a demo project first to confirm mappings. Use Help & Feedback for sync issues.\


Tip: Before migration, export critical user settings or integration configurations from TestRail to reference during TestFiesta setup. See [docs.testfiesta.com/getting-started/testrail-migration](https://docs.testfiesta.com/getting-started/testrail-migration).

Learn more about the terminology/methodology differences between TestFiesta & TestRail, Click "Next" to open "Terminology and Methodology Differences".
