# Analyzing Printer Details
Source: https://help.zscaler.com/zia/analyzing-printer-details
PDF: https://help.zscaler.com/pdf/com/en/1515451.pdf

The Printer Details page (Inventory> Printers > click Printer Name) displays details for the printer you selected. The page shows all the details from the printer's perspective. The Printer Details page is divided into the following tabs:
- [1. Printer Details](#printer_details)
- [2. Actions](#actions)
- [3. Overall Total](#overall_total_sec)
- [4. Overview](#overview_tab)
- [5. Activities & Incidents](#activities_incidents_tab)
[]You can create a new printer rule based on the parameters of the printer you selected.
-
Click **Actions **> **Create Printer Rule**.
The **Add Printer Rule** page appears.
- In the **Add Printer Rule** page, modify the settings as required.
-
Click **Save **and [activate the change](/zia/activating-device-control-policy-rules-configuration-changes).
[See Image.](#create_printer_rule_img)
[]This section displays the UNC path, hardware ID, and port of the printer connected.
![This image shows the Printer Details.](/downloads/zia/policies/endpoint-data-loss-prevention/analyzing-printer-details/printer_details.png)
[]This section consists of the following widgets:
- **Activities**:** **The total number of actions performed by the user over the last one month.
- **Incidents**: The total number of incidents by the user over the last one month.
- **Users**: The total number of users accessing the printer over the last month.
- **Endpoints**: The total number of endpoints accessed over the last one month.
![This image shows the overall total section](/downloads/zia/policies/endpoint-data-loss-prevention/analyzing-printer-details/Printer_overall_.png)
[]The Overview tab displays the **Users Using the Printer **table with the following information:
- **User**: The email address of the user.
- **Department**: The name of the department that the user belongs to.
- **Endpoint Name**: The name of the endpoints connected to the user's device.
- **Action**: The action taken when the policy rule is triggered.
- **Date**: The date the printer was detected.
![This image shows the Overview section of the Printer's page](/downloads/zia/policies/endpoint-data-loss-prevention/analyzing-printer-details/Printer_overview.png)
[]The Activities & Incidents tab shows the activities and incidents associated with the selected printer from the following perspectives:
- Filter the data shown in this tab by its **Type** (**Activity or Incident)**, **Actions**, **Severity**, **DLP Engines**, and **AI & ML Categories**.
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
- **Who**: Displays the user name and printer name that triggered the rule.
- **Why**: Displays the triggered rule (the other rules that matched) and DLP engine name.
- **What**: Displays details of file name.
- **How**: Displays the destination, destination path, printer local name, hardware, port, and UNC path.
![This image shows the Activities & Incidents tab in the Printer's Detail page](/downloads/zia/policies/endpoint-data-loss-prevention/analyzing-printer-details/Activities_Incidents_printer.png)
![This image shows the Create a Printer Rule window](/downloads/zia/policies/endpoint-data-loss-prevention/analyzing-printer-details/Create_new_printer_rule.gif)
[]
![This image shows the Printer Details page ](/downloads/zia/policies/endpoint-data-loss-prevention/analyzing-printer-details/Printer_details_numbered.png)