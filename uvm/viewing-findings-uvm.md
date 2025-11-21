# Viewing Findings in UVM
Source: https://help.zscaler.com/uvm/viewing-findings-uvm
PDF: https://help.zscaler.com/pdf/com/en/1531067.pdf

Zscaler Unified Vulnerability Management (UVM) findings represent vulnerabilities or misconfigurations detected on assets and linked to specific sources. Selecting a finding on the Findings page opens its drawer, where you can view detailed information. To learn more, see [About Findings](/uvm/about-findings-operational-view-uvm).
The actions you can perform in the finding drawer depend on your user role in the UVM app. To learn more, see [Understanding System Roles](/uvm/understanding-system-roles) and [Creating Custom Roles](/uvm/creating-custom-roles).
The finding drawer can be configured by admins and might look different in your account. The information in this article refers to the default finding drawer settings. To learn more, see [Configuring Entity Drawers in UVM](/uvm/configuring-uvm-entity-drawers-ui-config).
To view the finding drawer:
-
Go to **Vulnerabilities **> **Findings**.
[See image.](#findings-operational-view)
-
Click the finding you want to view.
[See image.](#finding-drawer)
A drawer appears with the following details and tabs:
- [Top Panel](#finding-drawer-top-panel)
- [Details](#finding-drawer-details-tab)
- [Vulnerability](#finding-drawer-vulnerability-tab)
- Click **Apply Changes** after updating the finding's details, or close the drawer.
[]![findings table in UVM](/downloads/uvm/vulnerability-management/remediate-uvm/managing-findings-uvm/findings%20table.png)
[]![finding drawer](/downloads/uvm/vulnerability-management/remediate-uvm/viewing-findings-uvm/finding%20drawer.png)
[]In the top panel of the finding drawer, you can view:
- **Title**: The finding's title as assigned by the source.
- **First Seen**: The date the finding was first detected.
- **Severity Score**: Both the original severity score and the contextualized severity score for the finding. You can manually override the score.
Additionally, you can perform the following actions:
- Copy a shareable link to the finding.
- View the finding's ID.
- Expand the finding drawer to full screen.
- Close the finding drawer.
[]On the **Details **tab, you can view:
- **Asset**: The related asset affected by the finding.
- **Ticket**: The related ticket that aggregated the finding.
- **Sources**: The source that reported the finding.
- **CVE ID**: If applicable, the CVE ID linked to the issue, with a direct link to the National Vulnerability Database (NVD) for further information.
- **First Seen**: The date the finding was first detected.
- **Last Seen**: The most recent date the finding was detected.
- **Description**: The description of the finding as provided by the source.
- **Score Explanation**: A detailed breakdown of the factors that contributed to the finding's severity score and how the score was calculated, including risk and mitigation criteria. To learn more, see [Understanding Severity Score](/uvm/understanding-severity-score).
[]On the **Vulnerability **tab, you can explore additional information about CVE findings, including vulnerability insights provided by related sources.