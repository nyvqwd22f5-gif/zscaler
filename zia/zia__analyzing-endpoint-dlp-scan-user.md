# Analyzing Endpoint DLP Scan for a User
Source: https://help.zscaler.com/zia/analyzing-endpoint-dlp-scan-user
PDF: https://help.zscaler.com/pdf/com/en/1480106.pdf

The User Scan Details drawer (Analytics > Endpoint Data Scan > User Investigation > click a user) displays Endpoint Data Loss Prevention (DLP) scan details for the user you select on the [User Investigation](/zia/about-user-investigation) page. The drawer shows all the scan details from the user's perspective.
The following sections are available in the drawer:
- [1. User & Endpoint Details](#User_Endpoint_Details_Section)
- [2. Overall Totals](#Overall_Totals_Section)
- [3. Sensitive Files Discovered](#sensitive_files_discovered)
- [4. Activities & Incidents](#activities_incidents_tab)
[]
- **User Details**:
- **Email Address**: The email address of the user.
- **User Risk Profile**: The risk profile assigned to the user (Low, Medium, High, or Critical). Zscaler analyzes your organization's user behavior trends and builds a risk profile dynamically by assigning a user risk score to each user. To learn more, see [Understanding User Risk Score](/zia/understanding-user-risk-score).
- **Department**: The name of the department that the user belongs to.
- **Endpoint Details**:
- **Device Name**: The device name of the endpoint.
- **Device ID**: The device ID assigned to the endpoint. Each endpoint is assigned a unique device ID.
- **Device OS**: The operating system of the device on which it's running.
- **DLP Version**: The DLP version currently running on your Zscaler Client Connector. To learn more, see [Viewing Information About Zscaler Endpoint DLP on Zscaler Client Connector](/client-connector/viewing-information-about-zscaler-endpoint-dlp-zscaler-client-connector).
- **Device Trust Level**: The device trust level assigned to the device. To learn more, see [Adding ZIA Posture Profiles](/client-connector/adding-zia-posture-profiles).
- **Last Update**: The last update on the endpoint based on an incident, activity, or scan.
- **Last Scan**: The date and time when the last scan was performed on the endpoint.
- **Nearby Sharing Status**: The status of nearby sharing for the endpoint.
![This image shows the User & Endpoint Details](/downloads/zia/policies/endpoint-data-loss-prevention/endpoint-data-scan/analyzing-endpoint-dlp-scan-user/user_endpoint_details.png)
[]This section consists of the following widgets:
- **Sensitive Files Discovered**: The total number of sensitive files discovered on the user's endpoints from the last scan. The scan is performed every day.
- **Activities**:** **The total number of actions performed by the user over the last one month.
- **Incidents**: The total number of incidents by the user over the last one month.
![This image shows the Overall Total section.](/downloads/zia/policies/endpoint-data-loss-prevention/endpoint-data-scan/analyzing-endpoint-dlp-scan-user/Overall_total_user_data_scan.png)
[]This tab shows sensitive file details discovered on the user's endpoints from the following perspectives:
- **DLP Engines**: The number of sensitive files discovered for the** **DLP engines category on the endpoints.
- **AI & ML Categories**: The number of sensitive files discovered for the AI & ML categories on the endpoints.
- **Distribution by File Type:** The number of sensitive files discovered by the file type (e.g., PDF, TXT, ZIP)
- **Top Sensitive Files Discovered**:** **This table shows all the sensitive files discovered on the endpoints. For each file, you can view:
- **Export**: You can export the details of the sensitive file discovered in a CSV format.
- **File Name**: The name of the file.
- **File Size**: The file size.
- **DLP Engines**: The DLP engines that the file triggered.
- **AI & ML Categories**: The AL & ML categories under which the file is classified.
- **Path**: The path where the file is stored on the endpoint.
- **Dictionaries**: The list of DLP dictionaries triggered by the file.
- **File Type**: The file type (TXT, ZIP, DOCX).
- **SHA-256**: The unique and irreversible hash of the file used for cryptographic security.
![This image shows the Sensitive Files Discovered tab. Details](/downloads/zia/policies/endpoint-data-loss-prevention/endpoint-data-scan/analyzing-endpoint-dlp-scan-user/Sensitive_files_discovered.png)
[]This tab shows activities and incidents performed by the user from the following perspectives.
- Filter the data shown in this tab by its **Type **(**Activity **or **Incident**), **Destination**, **Severity**, **DLP Engines**, and **AI & ML Categories**.
- **Analytics: **You can view the following information:
- **Activities and Incidents by Severity over the Last Month**: The graph shows the number of activities and incidents trend by their severity for the last 30 days. Hover over a date in the graph to view the number of activities, incidents, and split by severity (Info, Low, Medium, or High) for that day.
- **Top DLP Engines**: The DLP engines that the file triggered.
- **Top AI & ML Categories**: The AI & ML categories under which the file is classified.
- **Top Destinations**: This section shows the top destinations for the activities and incidents performed by the user, along with the total count (Removable Storage, My Printer, etc.).
- **Timeline**: The table shows the following information for each activity or incident:
- **Rule Name**: Name of the rule that got triggered.
- **Action**: The action taken when the policy rule got triggered.
- **Destination**: The destination of the file involved in the activity or incident
- **Event Details**: Click on a particular time on the timeline to view the event details:
- **Severity**: Displays the severity of the violation.
- **Transaction ID**: Allows you to copy the transaction ID for further analysis.
- **Time/Date**: The date and local time at the endpoint location when the activity or incident was performed.
- **Who**: Displays the user name and device name that triggered the rule.
- **Why**: Displays the triggered rule (the other rules that matched) and DLP engine name.
- **What**: Displays details of file name, source path, true file type, file extension, and SHA-256 details.
-
**How**: Displays the destination, destination path, vendor ID, and product ID.
![This image shows the Activities & Incidents tab.etails](/downloads/zia/policies/endpoint-data-loss-prevention/endpoint-data-scan/analyzing-endpoint-dlp-scan-user/activities_incidents_user_data_san.png)
![This image shows the User Investigation Details Page.tails](/downloads/zia/policies/endpoint-data-loss-prevention/endpoint-data-scan/analyzing-endpoint-dlp-scan-user/User_data_scan_numbered.png)