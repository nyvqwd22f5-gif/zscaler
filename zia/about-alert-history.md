# About Alert History
Source: https://help.zscaler.com/zia/about-alert-history
PDF: https://help.zscaler.com/pdf/com/en/1415171.pdf

The Alert History page displays the list of all the alerts with their evaluation status as ended. The page also displays alerts up to a period of 14 days from the time that the status was changed to Ended.
The Alert History page provides the following benefits and enables you to:
- View the complete list of triggered alerts under one table.
- View past alerts triggered up to 14 days to analyze threat patterns.
On the Alert History page, by default, you can view the Alert Summary section for all alert classes. You can customize the summary table to display the Security alerts or UEBA alerts by selecting Security or UEBA in the Customize View field.
![Select the type of alerts from the Customize View drop-down.](/downloads/zia/security-alerts/about-alert-history/Alert-History-All%20Alerts.png)
Security Alerts
[]The Alert History page for Security alerts includes the following sections:
- [Alert Summary](#securityalert-history-summary)
- [Details](#securityalerts-history-details)
- [Impacted Systems](#securityalert-history-impactedsystem)
[]The Alert Summary section displays a full list of all the alerts that have ended. You can choose to sort the table to prioritize incidents based on most impacted users, most blocked transactions, or most frequently seen activity. You can also use the filter bar to narrow down this list of results based on your organizational requirements.
On the Alert Summary page (Alerts > Alerts > Alert History), you can do the following:
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
You can add advanced filters to tailor certain fields to your specific searches. For example, you might want to filter your page to include a specific alert ID; in that case, you can add the advanced filter for **Alert ID** and include the ID **Equals**. You can also select or add other advanced filters to your fields:
- Equals
- Ends with
- Starts with
- Contains
- Does not equal
- Does not start with
- Does not end with
- Does not contain
You can add or remove multiple advanced filters, and you can select, add, or remove alert summary types to best tailor your filtering. Click **Apply** to update the page to reflect your filters or **Reset** to start over.
- **Reset**: Click to reset the summary table to the default values.
- **Apply**: Click to apply all the selected filters.
- Hide all the alert summary filters.
- View the list of all ended alert rules.
- **Sort By**: Sort the summary table based on the most impacted systems, last known attempt, most allowed transactions, or longest duration. By default, the table is listed for the most impacted systems.
- [Modify the table and its columns](/zia/using-tables).
![The Alert Summary table lists all the alerts triggered for each configured event type.](/downloads/zia/security-alerts/about-alert-history/Alert-History-Summary.png)
[]The Details section displays information on each individual alert. To view the details of an alert, click on the alert rule name from the Alert Summary table. The Details page is displayed.
On the Details page, (Alerts > Alerts > Alert History > Alert Name > Details), you can do the following:
-
**Alert Overview**: View the information on the alert rule name, the alert ID, where the alert applies to the organization or a department, the event type, and the type of policy action for the selected alert.
You can edit the Alert Rule Name by clicking the **Edit** icon in the Alerts Overview section.
- **Alert Details**: View the details of the first and last attempt, the number of allowed versus total transactions, the evaluation status, and the duration of the alert.
- **File Information**: View the file type and sandbox information for the alert. Click on the **Sandbox Report** to view the report for the selected alert.
-
**First Destination**: View the details of the destination IP, the hostname, URL category, the application type, category, and the risk score.
The First Destination section displays the information for the first user and the destination the user visited that triggered the alert.
- **View All Logs**: Click to view the list of all [Insight logs](/zia/about-insights) for the alert.
![The alert details page displays all the alert details for the selected alert rule.](/downloads/zia/security-alerts/about-alert-history/Security%20Alerts%20History%20Details.png)
[]The Impacted Systems displays a breakdown of the number of systems impacted by department and location. It also provides a list of all the impacted systems and the insight logs for each user.
On the Impacted Systems page, you can view each unique and individual system that was impacted by the particular threat. You can also view additional information related to the IP addresses, timestamps of events, and a count of allowed over total transactions.
Authenticated users can view additional metadata related to their device, OS, and traffic forwarding methods.
Additionally, by clicking on either of the options in the Actions column, you can view all logged transactions by the users or get redirected to the alerts table to view the other incidents related to the system.
On the Impacted Systems page (Alerts > Alerts > Alert History > Alert Name > Impacted Systems), you can do the following:
- View the total number of impacted systems by department.
- View the total number of impacted systems by location.
- View a complete list of the total impacted systems.
- View other incidents related to this impacted system.
- View all the [logged transactions](/zia/about-insights) by the user.
- View all the logged transactions on the [Insights](/zia/about-insights) page.
- Download a CSV file of the impacted system details.
![The impacted systems page displays the breakdown of the number of systems impacted by department and location.](/downloads/zia/security-alerts/about-alert-history/Security-Alerts-Impacted-Systems.png)
UEBA Alerts
[]The Alert History page for UEBA alerts includes the following sections:
- [Alert Summary](#ueba-alert-history-summary)
- [Details](#ueba-alert-details)
[]The Alert Summary section for UEBA alerts displays a full list of all the alerts that have already been triggered. You can use the filter bar to narrow down this list of results based on your organizational requirements.
On the Alert Summary page (Alerts > Alerts > Alert History), you can do the following:
- **Event Type**: Select an event or multiple events to display in the summary table.
- **Alert Type**: Select an alert or multiple alerts to display in the summary table.
- **User**: Select a user or multiple users to display in the summary table.
- **Reset**: Click to reset the summary table to the default values.
- **Apply**: Click to apply all the selected filters.
- Download a CSV file of the alerts.
- Hide all the alert summary filters.
- Select a time period to display the alert summary from the drop-down menu.
- [Modify the table and its columns](/zia/using-tables).
![The Alert Summary table lists all the alerts triggered for each configured event type.](/downloads/zia/security-alerts/about-alert-history/Alert-Summary-UEBA.png)
[]The Details section displays information on each individual alert. To view the details of an alert, click on the alert rule name from the Alert Summary table. The Details page is displayed.
On the Details page (Alerts > Alerts > Alert History > Alert Name > Details), you can do the following:
- **Alert Overview**: View the information on the alert rule name, the alert ID, the identified user, the type of policy action, the event type, the start and end time of the alert, the timestamp of when the alert was generated, the user risk score, and the [Web Insights](/zia/about-insights) log and [SaaS Security Insights](/zia/saas-security-insights) log for the selected alert.
- **Description**: View a graphical representation to understand the number of sensitive files that were downloaded by a user.
- **Create Exception**: Add the user to the alert exception list.
- Download a pdf file of the alert details.
![The details page for the selected UEBA alerts displays the details of each alert.](/downloads/zia/security-alerts/about-alert-history/Alert-Details-Page-UEBA.png)