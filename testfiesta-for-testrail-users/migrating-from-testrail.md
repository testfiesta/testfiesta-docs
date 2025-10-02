---
description: >-
  This page covers TestFiesta's three flexible migration options to transition
  from TestRail, designed for teams of all sizes—from small startups to large
  enterprises.
---

# Migrating From TestRail

## Migration Options

Whether you’re using TestRail Cloud or Server, these methods ensure your test cases, runs, plans, milestones, attachments, and history are imported efficiently, with minimal disruption. Below, we detail each option, how to execute it, and which scenarios it suits best, drawing from TestFiesta’s intuitive migration tools and comprehensive integration capabilities.

<details>

<summary>CSV/XML Import (Small Teams)</summary>

* **Overview:** Ideal for small teams or those needing only test cases without historical data (e.g., results, execution history). This method is quick and straightforward, perfect for lightweight setups or rapid onboarding.
* **How It Works:**
  1. In TestRail, export your test cases as a CSV or XML file via the Test Cases section (refer to TestRail’s [export guide](https://support.testrail.com/hc/en-us/articles/15144643126932-Export-test-cases)).
  2. In TestFiesta, navigate to Admin > Import and upload the exported file.
  3. Map fields (e.g., title, steps, expected results) as prompted to align TestRail’s structure with TestFiesta’s test case repository.
  4. Review imported cases in a new or demo project to ensure accuracy.
* **When to Use:** Best for small shops or teams starting fresh, where history isn’t critical. It’s the simplest way to get testing in TestFiesta within minutes.
* **Limitations:** Excludes test runs, results, and history. Manual field mapping may be needed for custom fields.
* **Tips:** Check [https://docs.testfiesta.com/projects-tab/test-cases-tab/importing-exporting-test-cases](https://docs.testfiesta.com/projects-tab/test-cases-tab/importing-exporting-test-cases) for detailed import steps.

</details>

<details>

<summary>TestRail API Integration (Small to Medium Teams)</summary>

* **Overview:** Designed for small to medium teams, this method uses TestFiesta’s TestRail API integration to pull all TestRail data—test cases, runs, plans, milestones, attachments, custom fields, and history—in a single, automated process. It also supports bidirectional sync for evaluating TestFiesta while continuing TestRail operations.
* **How It Works:**
  1. In TestFiesta, go to Admin > Integrations > TestRail.
  2. Enter your TestRail API credentials (found in TestRail’s user settings; see [TestRail API docs](https://support.testrail.com/hc/en-us/articles/7076948376724-API-reference)).
  3. Initiate the import to pull all data into a TestFiesta project. The process completes in minutes, mapping TestRail’s structure (e.g., sections to folders, suites to repositories) to TestFiesta’s.
  4. Enable sync to keep TestFiesta and TestRail in lockstep—changes in one platform reflect in the other.
  5. Review data in TestFiesta’s project or staging environment. Use dashboards to verify completeness.
* **When to Use:** Perfect for teams wanting a full migration with history or those testing TestFiesta alongside TestRail. The sync feature supports gradual adoption without disrupting workflows.
* **Benefits:** Comprehensive data transfer, real-time sync, and minimal setup. Preserves folder structures, custom fields, and attachments.
* **Limitations:** Requires TestRail Cloud access and API credentials. Sync should be disabled post-migration to avoid conflicts.
* **Tips:** Test in a staging project to identify UI issues (e.g., folder loading glitches noted in testing). Disable sync once fully transitioned. Refer to [docs.testfiesta.com/getting-started/testrail-migration](https://docs.testfiesta.com/getting-started/testrail-migration) for setup guides

</details>

<details>

<summary>PartyInvites (Enterprise and TestRail Server Users)</summary>

* **Overview:** PartyInvites is a specialized tool for large-scale migrations, particularly for TestRail Server users or enterprises with full database copies (e.g., Meta-sized teams). It directly imports an entire TestRail database into TestFiesta, ensuring no data loss. (Note: “Piñata” appears to be a misnomer for PartyInvites, likely a transcription error; it’s not referenced in TestFiesta’s public docs.)
* **How It Works:**
  1. Contact TestFiesta support at [testfiesta.com/contact-us](https://testfiesta.com/contact-us) to initiate the process.
  2. Provide access to your TestRail Server database or a database copy (e.g., SQL dump or backup).
  3. TestFiesta’s team uses PartyInvites to map and import all data—test cases, runs, plans, milestones, attachments, and history—into a TestFiesta organization.
  4. Validate the migration in a dedicated TestFiesta project, using dashboards to confirm data integrity.
* **When to Use:** Best for enterprise teams with complex TestRail Server setups or large datasets requiring a hands-off, high-fidelity migration.
* **Benefits:** Handles massive datasets, preserves all metadata, and minimizes manual effort. Tailored for server-based instances not accessible via API.
* **Limitations:** Not publicly available yet; requires coordination with TestFiesta’s team. Primarily for TestFiesta’s internal use or large accounts.
* **Tips:** Schedule a consultation with support to plan the migration timeline. Use TestFiesta’s audit logs (Admin > Audit Log) to track imported data actions.

</details>

## Best Practices For Smooth Migration

* **Test in Staging:** Validate migrated data in TestFiesta’s staging environment or a demo project to ensure accuracy. Refresh the UI if test cases or folders don’t display correctly, as minor glitches may occur.
* **Leverage Support:** Use the in-app Help & Feedback tool to report issues directly to TestFiesta’s QA team, or contact [testfiesta.com/contact-us](https://testfiesta.com/contact-us) for personalized assistance.
* **Monitor with Dashboards:** Track migration progress and team adoption using TestFiesta’s customizable dashboards, filtering by project or milestone.
* **Plan for Automation:** If your team relies on TestRail’s API for automation, use TestFiesta’s TR API shim (see API and Automation section) to keep scripts running without changes during migration.

## Choosing Your Migration Path

* **CSV/XML Import:** Best for small teams needing only test cases, prioritizing speed over history.
* **TestRail API Integration:** Suits small to medium teams wanting full data transfer and the flexibility to evaluate TestFiesta alongside TestRail.
* **PartyInvites:** Ideal for enterprises or TestRail Server users with large, complex datasets requiring a comprehensive, supported migration.

TestFiesta’s migration tools are designed to minimize downtime and preserve your testing workflows, making it easy to transition to a more flexible and cost-effective platform.

Learn all about TestFiesta's varying options for integrations for TestRail users on the next page! Click "Next" to open "Integrations For TestRail Users"
