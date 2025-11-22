# Viewing Onboarding Issues
Source: https://help.zscaler.com/dspm/viewing-onboarding-issues
PDF: https://help.zscaler.com/pdf/com/en/1474921.pdf

DSPM detects issues in the [onboarded AWS organization](/dspm/onboarding-aws-organization), [GCP organization](/dspm/onboarding-gcp-organization), or [Azure tenant](/dspm/onboarding-microsoft-azure-tenant) and lists them on the Issues tab. You can also view the resolution steps to resolve the issue.
If the issues are not addressed, they might impact the [scanning of the data stores](/dspm/about-scan-settings).
The following issues might occur while onboarding accounts:
| AWS | Microsoft Azure | GCP |
| --- | --------------- | --- |
| Role not found in the orchestrator or target accounts | Role not present or misconfigured in the Microsoft Entra tenant | Missing permissions in the target project |
| Missing permissions in the orchestrator or target accounts | Admin consent not granted | Missing permissions in the Orchestrator project |
| Configuration issues in the orchestrator account | Client Secret is invalid | Missing permissions in the service account |
| Configuration issues in the CloudTrail or incorrect CloudTrail configuration | Application object unavailable | Missing resources in the Orchestrator project |
| Orchestrator validation is pending | Role not found or misconfigured in the orchestrator subscription. | Orchestrator validation is pending |
| Orchestrator unable to communicate with DSPM | Onboarded account is currently suspended. | Orchestrator is unable to communicate with the DSPM |
| Resources missing in the orchestrator account | Onboarded account is deleted | Onboarded account is deleted |
| Onboarded account is currently suspended | Onboarded account is currently suspended | Onboarded account is currently suspended |
If an issue is detected in the target accounts, or projects, the status of the target accounts or projects moves to the **Needs Attention** state until the issue is resolved.
To view the onboarding issues:
- Go to **Administration** > **Configuration** > **Cloud Accounts**.
- Select the organization, project, or tenant from the list.
- Select the **Issues** tab to view the list of issues along with the resolution steps.
[See image.](#issues-tab)
- Click **See Accounts** to view the list of affected accounts, projects, or subscriptions.
[See image.](#target-acount-issues)
[]![View the issues in the onboarded account](/downloads/dspm/administration/cloud-account-management/resolving-onboarding-issues/dspm-cloud-accounts-issues-tab.png)
[]![Target account issues](/downloads/dspm/administration/cloud-account-management/resolving-onboarding-issues/dspm-target-account-issues.png)