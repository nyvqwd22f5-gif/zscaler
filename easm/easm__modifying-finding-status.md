# Modifying Finding Status
Source: https://help.zscaler.com/easm/modifying-finding-status
PDF: https://help.zscaler.com/pdf/com/en/1503601.pdf

[Findings](/easm/about-findings) offer deeper insights into your external attack surface, enabling you to identify, prioritize, and remediate business-critical risks and vulnerabilities. EASM supports various statuses for findings to help you effectively manage findings from discovery to closure, with different types of processing and management options based on the findings' statuses. For example, only findings in specific statuses relevant to the management of risks are highlighted on the [Insights Overview dashboard](/accessing-interacting-insights-overview-dashboard).
When the risk parameters are initially detected in assets, they are populated in the EASM Admin Portal, automatically tagged with the label "Not Verified". You can validate the findings reported by EASM individually and mark them as "Verified" if they need to be managed as risks. The available finding statuses are:
- **Not Verified**: All the risk findings identified by EASM in your organization's attack surface are tagged with the label "Not Verified".
- **Verified**: Risk findings are investigated manually and it's verified that the risk is present (e.g., verifying an open port flagged on a host).
- **Risk Accepted**: Represents risk findings that are deemed acceptable. For example, a jump server with port 22 open and exposed to the internet might be for intended use.
- **Resolved**: Risk findings for which remediation steps are taken or are planned can be marked as resolved. With the previous example, if the server is decided to be moved behind Zscaler Private Access (ZPA) for example, then it could be marked as resolved. However, if the finding is discovered again in a subsequent scan, then it is marked as "Not Verified".
- **Disputed**: If the manual verification of the finding turns out differently from the risk finding, the finding can be moved to the Disputed status, indicating that it might be a false positive.
The Insights Overview dashboard focuses on findings that are in Not Verified and Verified statuses, highlighting risks that need immediate attention to prevent threats and penetration by bad actors into your network. Findings that are in Risk Accepted, Resolved, or Disputed statuses are excluded from the dashboard, as these risks are considered as not requiring any further actions from your security team. However, risks in these statuses can be moved to Not Verified or Verified if they require further examination.
To modify the status of a finding:
The data on the Findings page is specific to the organization selected on the top-right corner. Before you begin, ensure that the desired organization is selected.
- Go to the **Findings** page.
-
Click the finding record for which you want to modify the status.
The **Finding Details** drawer opens on the right side.
-
In the **Finding Details** drawer, under the **Finding Details** tab, you can modify the finding's status by using the **Status** drop-down menu. Alternatively, you can click the **View More Details** button to go to the finding details page and modify the status from there.
[See image.](#changing-finding-status)
A **Status Update Confirmation** window appears.
- In the **Status Update Confirmation** window, enter the reason for modifying the finding's status which can be useful for auditing trails and general tracking purposes.
- Click **Accept**.
[]![Changing finding status from Finding Details drawer and Finding Details page in EASM Admin Portal](/downloads/easm/insights/changing-finding-status/EASM-finding-status.gif)