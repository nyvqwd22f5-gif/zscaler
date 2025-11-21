# Analyzing Portable Device Details
Source: https://help.zscaler.com/zia/analyzing-portable-device-details
PDF: https://help.zscaler.com/pdf/com/en/1515456.pdf

The Mobile Device Details page (Inventory> Portable Device> click a Portable Device Name) displays mobile device details for the device you select. The page shows all the details from the mobile device's perspective. The Mobile Device Details page is divided into the following tabs:
- [1. Device Details](#device_details)
- [2. Overall total](#overall_total_sec)
- [3. Overview](#overview_tab_sec)
- [4. Activities & Incidents](#activities&incidents_tab)
[]This section displays the vendor ID, product ID, and serial number of the connected device.
![This image shows the Mobile Device Details](/downloads/zia/policies/endpoint-data-loss-prevention/analyzing-portable-device-details/mobile_device_details.png)
[]This section consists of the following widgets:
- **Activities**:** **The total number of activities performed by the user over the last month.
- **Incidents**: The total number of incidents over the last one month.
- **Users**: The total number of users accessing the storage device over the last month.
- **Endpoints**: The total number of endpoints accessed over the last one month.
![This image shows the Overall total section](/downloads/zia/policies/endpoint-data-loss-prevention/analyzing-portable-device-details/overall_total_mobile_device.png)
[]The Overview tab displays the **Users Using the Device** table with the following information:
- **User**: The email address of the user.
- **Department**: The name of the department that the user belongs to.
- **Endpoint Name**: The name of the endpoints connected to the user's device.
- **Action**: The action taken when the policy rule is triggered.
- **Date**: The date the device was plugged in.
![This image shows the overview section](/downloads/zia/policies/endpoint-data-loss-prevention/analyzing-portable-device-details/mobile_details_overview.png)
[]Activities & Incidents tab shows activities and incidents from the following perspectives:
- Filter the data shown in this tab by its **Type** (**Activity or Incident)**, **Actions**, **Severity**, **DLP Engines**, **AI & ML Categories**, and **User**.
- **Analytics**: You can view the following information:
- **Activities and Incidents by Severity over the Last Month**: The graph shows the number of activities and incidents trend by their severity for the last 30 days. Hover over a date in the graph to view the number of activities, incidents, and split by severity (Info, Low, Medium, or High) for that day.
- **Top DLP Engines**: The DLP engines that the file triggered.
- **Top AI & ML Categories**: The AI & ML categories under which the file is classified.
- **Top Destinations**: This section shows the top destinations for the activities and incidents performed by the user along with the total count (Removable Storage, My Printer, etc.).
- **Timeline**: Shows the following information for each activity or incident:
- **Rule Name**: Name of the rule that got triggered.
- **Action**: The action taken when the policy rule got triggered.
- **Destination**: The destination of the file involved in the activity or incident
- **Event Details**: Click on a particular time on the timeline to view the event details:
- **Severity**: Displays the severity of the violation.
- **Transaction ID**: Allows you to copy the transaction ID for further analysis.
- **Time/Date**: The date and local time at the endpoint location when the activity or incident was performed.
- **Who**: Displays the user name and device name that triggered the rule.
- **Why**: Displays the triggered rule (the other rules that matched) and DLP engine name.
- **What**: Displays details of source path.
- **How**: Displays the destination, vendor ID, product ID, and serial number.
![This image shows the Activities & Incidents tab](/downloads/zia/policies/endpoint-data-loss-prevention/analyzing-portable-device-details/activities_incidents_mobile.png)
![This image shows the Mobile Device Details page](/downloads/zia/policies/endpoint-data-loss-prevention/analyzing-portable-device-details/Mobile_device_details_numbered_newest.png)