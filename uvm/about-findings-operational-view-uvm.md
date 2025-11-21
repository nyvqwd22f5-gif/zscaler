# About Findings
Source: https://help.zscaler.com/uvm/about-findings-operational-view-uvm
PDF: https://help.zscaler.com/pdf/com/en/1527991.pdf

The Findings page provides a centralized view of all findings within your organization's Zscaler Unified Vulnerability Management (UVM) app. Each finding represents a vulnerability or misconfiguration detected on an asset and contextualized with additional information from multiple sources, such as CVE details, exposed secrets, or misconfigurations. Findings are grouped into tickets based on factors like remediation teams or the affected product. On this page, you can explore finding details, analyze their impact and status, and prioritize remediation using risk-driven insights.
The Findings page provides the following benefits and enables you to:
- Access and filter findings using system-saved views, grouping options, customizable table columns, and advanced filters to focus on specific scenarios.
- Dive into detailed information about each finding, including associated assets, severity scores, and related tickets to prioritize actions effectively.
- Dispatch remediation campaigns by manually grouping findings into a single ticket.
About the Findings Page
On the Findings page (Vulnerabilities > Findings), you can do the following:
- Select from system-saved views, or views [you previously saved](/uvm/creating-managing-saved-views).
- [List of System-Saved Views](#system-saved-views-list)
- [Save your view](/uvm/creating-managing-saved-views) for quick access after making adjustments to it (e.g., applying filters, adjusting columns or grouping).
- [Filter](/uvm/using-filters) findings by **Severity**, **Source**, **Asset Type**, **First Seen**,** **or **Last Seen**.
- Search for specific findings by entering keywords in the search bar.
- Explore the **Overview **charts to gain high-level insights into the findings and their risk level in your environment. The charts are adjusted by the selected view and filters.
- **Findings by Severity**: Categorizes findings by severity, comparing their original severity scores (left bar) to recalculated contextualized scores (right bar) for each severity category. This highlights how contextualized scores provide more accurate severity assessments. To learn more, see [Understanding Severity Score](/uvm/understanding-severity-score).
- **Findings Count by Source Name**: Displays the number of findings grouped by source, showing the top 5 most frequently occurring sources.
- **Finding Duplication**: Details the number of findings retrieved from different sources, showcasing how duplicates are reduced and findings are consolidated into actionable tickets for efficient remediation.
- Apply actions to multiple findings:
- **Update**: Update finding details (e.g., finding SLA, state).
- **Create Ticket**: Create a ticket to split the selected findings from their current ticket, and adds them to a new ticket. The new ticket is locked, and the tickets that the findings originate from are listed on the new ticket's [Related Tickets](/uvm/managing-tickets-uvm) tab.
- [Group findings](/uvm/grouping-operational-views-group) by fields such as **Severity Score**, **Finding Type**, or **Source**.
- Refresh the page to reflect the most current information.
- Export the list of findings and their details as a CSV file.
- [Modify the columns displayed in the table.](/uvm/managing-table-columns)
- Select all findings on the page.
- Click a finding to open individual [finding drawers](/uvm/managing-findings-uvm). When the default **Active Critical and High Findings **saved view is selected, you can see the following details for each finding:
- **ID**: The unique UVM finding ID.
- **Severity Score**: The severity score assigned to the finding, calculated based on [severity score settings](/uvm/configuring-severity-scores).
- **Title**: The name or description of the finding.
- **Sources**: The sources from which the finding was ingested.
- **Asset ID**: The ID of the asset that the finding was detected on.
- **Asset Type**: The category or classification of the asset related to the finding (e.g., server, application, device).
- **CVE**: The CVE of the finding, if applicable (i.e., relevant to CVE type findings only).
- **First Seen**: The date the finding was first detected on your sources.
- **Last Seen**: The most recent date the finding was detected.
![about findings page numbered](/downloads/uvm/vulnerability-management/remediate-uvm/about-findings-operational-view-uvm/about%20findings%20operational%20view_1.png)
[]The Findings page includes system views with predefined filter selections, providing quick access to common data scopes:
- **Active Critical and High Findings**: Active findings with critical or high severity. This is the default view.
- **New Findings**: Findings detected within the last 7 days.
- **Active CVE Vulnerabilities**: Active findings classified as CVE-type vulnerabilities.
- **Active Misconfigurations**: Active findings classified as misconfigurations.
- **Known Exploited Active Findings**: Active findings with a high likelihood of being exploited as indicated by the Known Exploited [filter](/uvm/using-filters) value set to TRUE.