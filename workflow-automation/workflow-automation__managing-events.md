# Managing Events
Source: https://help.zscaler.com/workflow-automation/managing-events
PDF: https://help.zscaler.com/pdf/com/en/1497931.pdf

The Events page in Workflow Automation displays a list of the events that were created due to unused or underutilized SaaS application licenses by the employees of different departments within an organization. This page enables you to review Business Insights events.
The primary process flow for Business Insights event resolution using the Workflow Automation Admin Portal is as follows:
- Workflow Automation assigns the events created to record the unused SaaS application licenses of an organization to an admin who has Edit access to that [event group](/workflow-automation/managing-event-groups).
- Workflow Automation automatically notifies the end user and creates a ticket for resolving the event based on the workflows configured by the Business Insights admins.
- An email notification requests justification from the end user for not using the license or approval to deprovision the application.
- The admin accesses the Events page in the Workflow Automation Admin Portal to review the events, and their latest status.
- Based on the justification response received from the end user, the admin performs the necessary action for the event type.
Viewing Events
On the Events page, you can do the following:
- Select a date range for the events displayed.
- Use and manage the event filters.
- Reset all the applied filters.
- Search for an event by **All** or **Event ID**. The search only shows results starting with or completely matching the search string.
- **All**: This option allows you to enter freeform text that can match multiple events.
- **Event ID**: This option allows you to search for an event by its Event ID.
- View a list of events that have occurred in your organization. For each event, you can view:
- **Event ID**: The transaction ID for the event.
- **Event Date**: The date and time when the event occurred. The date and time are displayed in the local time zone of the end user.
- **Last Change Date**: The date and time when the event was last modified. The date and time are displayed in the local time zone of the admin.
- **Priority**: The priority for the event. Priorities are **Critical**, **High**, **Medium**, or **Low**.
- **Event Type:** The type of event.
- **Admin**: The admin who is investigating the event.
- **Application**: The SaaS application associated with the event.
- **Status**: The status of the event. Statuses are **Open** or **Closed**.
- **Event Groups: **The event groups associated with the event.
- **Last Change**: The latest state of the event. This indicates the most recent change to the event.
- [Modify the table and its columns](/workflow-automation/using-tables-workflow-automation-events).
[See image.](#viewing-events-page)
Managing Events
The Events page allows you to perform certain actions to manage the events assigned to you.
- [Applying the Date Range Filter](#time-range-filter)
- [Applying Filters for the Events](#filters-section)
- [Viewing Event Details](#event-details)
[]On the Events page, you can filter the events that are displayed by the date of occurrence. By default, this page displays information about the Business Insights events that occurred in the current week. The date range filter applies to all widgets. Date ranges are:
- Current Day
- Last Day
- Current Week
- Last Week
- Current Month
- Last Month
-
Custom Date Range
To view the events that occurred in a specific date range, you can use the **Custom Date Range** option and specify the start and end dates. The **Custom Date Range** option only supports events that are up to 6 months old, and you can only search for a maximum of a one-month rolling window.
[See image.](#time-range-filter-image)
[]You can apply various filters using the Filters option to modify the events displayed on the Events page.
To apply filters:
-
On the **Events** page, click the **Filters** icon. The **Filters** window appears, displaying all the available filters on the left side of the window. The filters available are:
- Application Name
- Event Group
- Event Type
- Priority
- Status
[See image.](#events-filter-window)
-
Select a filter and then select or enter the filter values on the right side of the window. As you select or enter the filter values, the number of values selected appears next to the filter. You can select multiple filters and their values. To remove all the selected filters, click **Reset**.
[See image.](#adding-event-filters)
- Click **Apply**. The **Events** page reappears, displaying the events that match the filter criteria.
You can also save the selected filter criteria and apply them to modify the events. You can save multiple combinations of filters and use them whenever required for easy application.
To save and apply filters:
- On the **Events** page, click the **Filters** icon. The **Filters** window appears, displaying all the available filters on the left side of the window.
-
Select a filter and then select the filter values on the right side of the window and click **Save As**. The** My Filters** window appears.
[See image.](#saving-my-filters)
-
In the **My Filters** window, enter the name of the filter in the **Filter Name** field and then click **Save**.
The selected filters are saved for selection under the **My Filters** drop-down menu in the **Filters** window.
[See image.](#my-filter-name)
-
From the **My Filters** drop-down menu, select a saved filter. The **Filters** window reappears, displaying the filters associated with that saved filter.
[See image.](#selecting-saved-filters)
- Click **Apply**. The **Events** page reappears, displaying the events that match the filter criteria.
You can also delete the saved filters by using the **Delete** icon next to the filter in the **My Filters** section.
[]On the Events page, click the **Event ID** of an event to navigate to the [Event Details](/workflow-automation/managing-event-details)** **page. On the **Event Details** page, you can view the detailed information of each event such as event type, impacted application, number of users, priority, etc., and manage them.
[See image.](#event-details-navigation)
![Viewing the Events page in the Workflow Automation Admin Portal](/downloads/workflow-automation/business-insights/events/managing-events/WA-BI-Events-PG-Viewing.png)
[]
![Screenshot of the date range filters in the Events page on the Workflow Automation Admin Portal](/downloads/workflow-automation/business-insights/events/managing-events/WA-BI-Events-PG-Time-Range-Filter.png)
[]
![On the Event page, click an Event ID on the table to navigate to the Event Detail page](/downloads/workflow-automation/business-insights/events/managing-events/WA-BI-Events-PG-Nav-Event-Details.png)
[]
![Viewing the Filters window on the Events page in the Workflow Automation Admin Portal](/downloads/workflow-automation/business-insights/events/managing-events/WA-BI-Event-Filters-Parameters.png)
[]
![Selecting event filters in the Filters window in the Events page](/downloads/workflow-automation/business-insights/events/managing-events/WA-BI-Event-Filters-Adding-Filters.png)
[]
![On the Filters window, after selecting the filter parameters, click the Save As button to save the filter. The filter is displayed in the My Filters drop-down menu.](/downloads/workflow-automation/business-insights/events/managing-events/WA-BI-Event-Filters-Save-As-Button.png)
[]
![Add a Filter Name in the My Filters window](/downloads/workflow-automation/business-insights/events/managing-events/WA-BI-My-Filters-Filter-Name.png)
[]
![Selecting a saved event filter from the My Filters drop-down menu on the Filters window](/downloads/workflow-automation/business-insights/events/managing-events/WA-BI-My-Filters-Selecting-Filter.png)
[]