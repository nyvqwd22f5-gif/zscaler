# About Ongoing Alerts
Source: https://help.zscaler.com/zia/about-ongoing-alerts
PDF: https://help.zscaler.com/pdf/com/en/1415176.pdf

The Ongoing Alerts page displays the information about all the ongoing alerts in a graphical and detailed view. It provides high-level details of what is happening within your organization during a given time period to quickly take action and prioritize investigation. It helps you to check the responses based on the type of detectable threats within the organization and the scope of impact.
The Ongoing Alerts page provides the following benefits and enables you to:
- View the detailed information about all ongoing alerts using multiple widgets.
- Assess the threats at a high level for quick action and prioritize the investigations.
About the Ongoing Alerts Page
On the Ongoing Alerts page (Alerts > Alerts > Alerts > Ongoing Alerts), you can view the following sections:
[]Overview
The Overview displays the top 5 threats and event types for each tenant. You can also view the number of ongoing alerts, impacted systems, impacted departments, and impacted locations on this page. The ongoing alerts can be viewed for a period of 1 hour to 14 days.
On the Overview page (Alerts > Ongoing Alerts), you can do the following:
- View the top 5 threats by the type of system being impacted. Click each bar to apply the filter to the [Alert Summary](#ongoing-alert-summary) table.
- View the top 5 events by the total number of alert count. Click each bar to apply the filter to the [Alert Summary](#ongoing-alert-summary) table.
- View the total number of impacted locations.
- View the total number of impacted systems.
- View the total number of ongoing alerts.
- View the total number of impacted departments.
- Select a time range to filter the alert rules from the drop-down menu.
![The Overview page for ongoing alerts displays the top 5 threats by impacted systems and event types.](/downloads/zia/security-alerts/about-ongoing-alerts/Alerts-Overview-UEBA.png)
[]Alert Summary
The Alert Summary displays a full list of all the ongoing ZIA alerts that you can view and manage. You can choose to sort the table to prioritize incidents based on most impacted users, most blocked transactions, or most frequently seen activity. You can also use the filter bar to narrow down this list of results based on your organizational requirements.
On the Alert Summary page (Alerts > Ongoing Alerts), you can do the following:
- **Event Type**: Select an event or multiple events to display in the summary table.
- **User**: Select a user or multiple users to display in the summary table.
-
**Add Filter**: Filter the summary table based on the following fields:
- **Alert ID**: The alert ID created by the service.
- **Indexed By**: The unique identifier value by which the alerts are indexed that are used for aggregating systems impacted as part of the same incident. All alerts attempt to be indexed by the available threat name or other unique identifiers such as Hostname, Server Destination IP, or MD5 hash.
- **Client IP**: The IP address of the client for which the alert is triggered.
- **Client Ext. IP**: The internet gateway location IP address.
- **Alert Rule Name**: The alert name added during creation of the rule.
- **Location**: The internet gateway location from which the alert originated. If the transaction did not originate from a location that was defined in the alert rule, then it is recorded as coming from a remote user. You can sort and search through this field.
- **Department**: The department which was impacted by a particular threat or which was a part of a preconfigured alert.
You can add advanced filters to tailor certain fields to your specific searches. For example, you may want to filter your page to include a specific alert ID; in that case, you can add the advanced filter for **Alert ID** and include the ID Equals. You can also select or add other advanced filters to your fields:
- Equals
- Ends with
- Starts with
- Contains
- Does not equal
- Does not start with
- Does not end with
- Does not contain
You can add or remove multiple advanced filters, and you can select, add, or remove alert summary types to best tailor your filtering. Click **Apply **to update the page to reflect your filters or **Reset** to start over.
- **Reset**: Click to reset the summary table to the default values.
- **Apply**: Click to apply all the selected filters.
- Hide all the alert summary filters.
- View the list of all alert rules.
- **Sort By**: Sort the summary table based on the most impacted systems, last known attempt, most allowed transactions or longest duration. By default, the table is listed for the most impacted systems.
- [Modify the table and its columns](/zia/using-tables).
![The Alert Summary table lists all the alerts triggered for each configured event type.](/downloads/zia/security-alerts/about-ongoing-alerts/Alert-History-Summary.png)