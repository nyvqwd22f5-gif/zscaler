# Analyzing Device Details
Source: https://help.zscaler.com/zia/analyzing-device-details
PDF: https://help.zscaler.com/pdf/com/en/1515441.pdf

The Device Details page (Inventory> Removable Storage > User Investigation > click a Device-Friendly Name) displays device details for the device you select. The page shows all the details from the device's perspective. The Device Details page is divided into the following tabs:
- [1. Device Details](#device_details)
- [2. Actions](#actions)
- [3. Overall Total](#overall_total_sec)
- [4. Overview](#overview_tab_sec)
- [5. Activities & Incidents](#activities&incidents_tab)
[]You can create a new removable storage device rule based on the parameters of the device you selected.
-
Click **Actions **> **Create a Device Rule**.
The **Add Removable Storage Device Rule** page appears.
-
In the **Add Removable Storage Device Rule** page, modify the settings as required.
[See Image.](#create_new_device_gif)
- Click **Save **and [activate the change](/zia/activating-device-control-policy-rules-configuration-changes).
[]This section displays the vendor ID, product ID, and serial number of the connected device.
![This image shows the Device Details of the connected device.](/downloads/zia/policies/endpoint-data-loss-prevention/analyzing-device-details/Device_details.png)
[]This section consists of the following widgets:
- **Activities**:** **The total number of activities performed by the user over the last month.
- **Incidents**: The total number of incidents over the last one month.
- **Users**: The total number of users accessing the storage device over the last month.
- **Endpoints**: The total number of endpoints accessed over the last one month.
![This image shows the overall total section](/downloads/zia/policies/endpoint-data-loss-prevention/analyzing-device-details/Device_overall.png)
[]The Overview tab displays the **Users Using the Device** table with the following information:
- **User**: The email address of the user.
- **Department**: The name of the department that the user belongs to.
- **Endpoint Name**: The name of the endpoints connected to the user's device.
- **Action**: The action taken when the policy rule is triggered.
- **Date**: The date the device was plugged in.
![This image shows the Device Overview section](/downloads/zia/policies/endpoint-data-loss-prevention/analyzing-device-details/Device_Overview_section.png)
[]Activities & Incidents tab shows activities and incidents associated with the selected device from the following perspectives:
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
- **Event Details**: Click on a particular time on the timeline to view the following details:
- **Severity**: Displays the severity of the violation.
- **Transaction ID**: Allows you to copy the transaction ID for further analysis.
- **Time/Date**: The date and local time at the endpoint location when the activity or incident was performed.
- **Who**: Displays the user name and device name that triggered the rule.
- **Why**: Displays the triggered rule (the other rules that matched) and DLP engine name.
- **What**: Displays details of file name, source path, true file type, file extension, and SHA-256 details.
- **How**: Displays the destination, destination path, vendor ID, and product ID.
![This image shows the Activities & Incidents page of the connected deviceDevice Details of the connected device.](/downloads/zia/policies/endpoint-data-loss-prevention/analyzing-device-details/Device_Activities_Incidents_details_page_1.png)
![This image shows the Create New Device Rule window](/downloads/zia/policies/endpoint-data-loss-prevention/analyzing-device-details/Create_new_device_rule.gif)
[]
![This image shows the Device Details Page](/downloads/zia/policies/endpoint-data-loss-prevention/analyzing-device-details/Device_details_with_numbers_all_page.png)