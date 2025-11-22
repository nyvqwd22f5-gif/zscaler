# Managing Event Details
Source: https://help.zscaler.com/workflow-automation/managing-event-details
PDF: https://help.zscaler.com/pdf/com/en/1500326.pdf

The Event Details page displays detailed information about an event, such as an overview of the event, user information related to the event, the current status of the event, etc. This page provides two tabs, Event and User Notifications, which allow you to view and manage details of each event and the user notifications associated with the event, respectively.
Viewing Event Details
The Event page displays various sections that provide in-depth information about the Business Insights event that occurred in your organization. You can use the **Next **and **Previous **icons at the top of the page to navigate through the list of events.
[See image.](#event-details-event-tab)
You can view the following details about the event:
- [Overview](#overview)
- [Event Details](#violation-details)
- [State Changes](#change-state)
[]In the **Overview** section, you can see:
- **Event ID**: The ID of the event.
- **Event Date**: The date and time when the event occurred. The date and time are displayed in the local time zone of the user.
- **Priority**: The priority of the event. Priorities are **Critical**, **High**, **Medium**, or **Low**.
- **Event Groups**: The event groups mapped to the event.
[See image.](#overview-section-image)
[]In the **Event Details** section, you can see:
- **Event Type**: The type of the event.
- **Application**: The application for which the event is created.
- **Users Count By Plan Type**: The plan types for the application associated with the event along with the number of impacted users under those plan types for the event. By default, the first 5 plan types appear. If there are more than 5 plan types, a **Show More** link appears. Click this link to see the rest of the plan types with their user counts.
[See image.](#event-details-section-image)
[][]The **State Changes** section acts as an audit log for the event. It provides a table that records and displays all the changes to the event. All the actions you perform are logged in this table.
The table displays the following information:
- **State**: The state of the event. The latest state is displayed at the top.
- **Date**: The date and time when the event's status changed. The date and time are displayed in the local time zone of the user who caused the event.
- **Changed By**: The name of the user or service that updated the event.
- **Comment**: The system-generated comments or comments that the user added about the event.
[See image.](#state-changes-image)
Managing Event Details
The **Event Details **page allows you to close the events assigned to you. The **Close Event** action is logged in the [State Changes](#state-changes-link) table.
At the top right of the page, the **Actions** drop-down menu contains the **Close Event** action.
[See image.](#actions-drop-down-menu)
To close the event:
- From the **Actions** drop-down menu, select **Close Event**. The **Close Event** window appears, displaying a message asking if you are sure you want to close the selected event.
- Click **Yes**.
The status changes to Closed. You cannot reopen a closed event.
Viewing and Managing User Notifications
The User Notification page displays a table that provides in-depth information about those users to whom the notification was sent for the event. You can use the **Next **and **Previous **icons at the top of the page to navigate through the list of events.
The table displays the following information:
- **Email**: The email ID of the user.
- **User Name**: The name of the user.
- **Last Status**: The current status of the event. Click the status to view details of the action performed that triggered the current status of the event.
- **Plan Type**: The plan type through which the application is provisioned to the user.
- **Last Active Date**: The latest date that the user accessed the application.
- **Justification Type**: The justification type received from the user for the event.
- **Justification Reason**: The justification reason received from the user for the event.
[See image.](#users-tab-image)
![Viewing the Overview Section on the Event Details page in Workflow Automation](/downloads/workflow-automation/business-insights/events/managing-event-details/WA-BI-Event-Details-Page-Overview-Section.png)
[]
![Viewing the event details for an event on the Event Details page - Events tab](/downloads/workflow-automation/business-insights/events/managing-event-details/WA-BI-Event-Details-Page-Event-Tab.png)
[]
![Viewing the Event Details Section on the Event Details page in Workflow Automation](/downloads/workflow-automation/business-insights/events/managing-event-details/WA-BI-Event-Details-Page-Event-Details-Section.png)
[]
![Viewing the State Changes Section on the Event Details page in Workflow Automation](/downloads/workflow-automation/business-insights/events/managing-event-details/WA-BI-Event-Details-Page-State-Changes-Section.png)
[]
[]![Viewing the menu options in the Actions drop-down menu on the Event Details page](/downloads/workflow-automation/business-insights/events/managing-event-details/WA-BI-Event-Details-Page-Actions-Menu.png)
![Viewing the user notifications on the Event Details page - User Notifications tab. The user notifications are listed in a table that has columns for Email, User Name, Last Status, Plan Type, Last Active Date, Justification Type, and Justification Reason.](/downloads/workflow-automation/business-insights/events/managing-event-details/WA-BI-Event-Details-Page-User-Notifications-Tab_0.png)
[]