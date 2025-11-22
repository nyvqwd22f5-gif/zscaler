# Viewing Policy Violations in AEM
Source: https://help.zscaler.com/uvm/viewing-policy-violations-aem
PDF: https://help.zscaler.com/pdf/com/en/1531117.pdf

Policy violations represent deviations from established security policies detected on assets within the Asset Exposure Management (AEM) app in the Zscaler SecOps platform. Clicking a policy violation on the Policy Violations page opens the violation's drawer, where you can view detailed information including the affected asset, policy name, and severity score. You can also perform multiple actions for the violation. To learn more, see [About Policy Violations](/uvm/about-policy-violations-operational-view-aem).
The actions you can perform in the violation drawer depend on your user role in the AEM app. To learn more, see [Understanding System Roles](/uvm/understanding-system-roles) and [Creating Custom Roles](/uvm/creating-custom-roles).
To view the policy violation drawer:
- Go to the AEM app.
-
In the left-side navigation, click **Policy Violations**.
[See image.](#violations-operational-view)
-
Click the policy violation you want to view.
[See image.](#policy-violation-drawer)
A drawer appears with the following details:
- [Top Panel](#violation-drawer-top-panel)
- [Details](#violation-drawer-details-tab)
- [Asset Info](#violation-drawer-asset-info-tab)
- Close the drawer to return to the **Policy Violations** page.
[]![policy violations table in AEM](/downloads/uvm/asset-exposure-management-aem/remediate-aem/managing-violation-tickets-aem/policy%20violations%20table.png)
[]![policy violation drawer](/downloads/uvm/asset-exposure-management-aem/remediate-aem/viewing-policy-violations-aem/policy%20violation%20drawer.png)
[]In the top panel of the policy violation drawer, you can view:
- **Title:** The policy violation's title, as assigned by the source.
- **First Seen:** The date the policy violation was first detected.
- **Severity Score:** The original severity score and the contextualized score for the policy violation.
- **ID:** The unique identifier of the policy violation.
- **State:** The current state of the policy violation (e.g., **Active **or **Inactive**).
Additionally, you can perform the following actions:
- Copy a shareable link to the violation.
- Expand the violation drawer to full screen.
- Close the violation drawer.
[]On the **Details **tab, you can view:
- **Asset Name:** The name of the asset affected by the policy violation.
- **Type:** The type of asset impacted (e.g., **Workstation**, **Web Application**).
- **Sources:** The source that reported the policy violation.
- **First Seen:** The date the policy violation was initially detected.
- **Last Seen:** The most recent date the policy violation was detected.
- **Policy Name:** The name of the policy that was violated (e.g., **EDR Coverage**).
- **Policy Violation Type:** The category of the policy violation (e.g., **Tool Coverage**).
- **Assignee:** The user or team assigned to remediate this policy violation.
- **SLA:** The service level agreement (SLA) date that the policy violation must be remediated by.
[]On the **Asset Info **tab, you can view:
- **Asset IP**: The IP address assigned to the asset (e.g., **74.69.111.39**).
- **Asset Type**: The category or classification of the asset (e.g., **Web Application**).
- **Asset Name**: The name of the asset (e.g., **https://acmeprod.com**).
- **Asset Owner**: The team or individual responsible for managing the asset (e.g., **Networking Team**).