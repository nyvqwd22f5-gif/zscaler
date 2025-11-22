# Responding to an End User Notification for Events
Source: https://help.zscaler.com/workflow-automation/responding-end-user-notification-events
PDF: https://help.zscaler.com/pdf/com/en/1503401.pdf

The format of the notification and survey might not be the same as illustrated in this article. It depends upon the notification and the survey template that your organization configured in the Workflow Automation Admin Portal.
As an end user, when you haven't used a SaaS application license provisioned to you by your organization for a period of time, the details are recorded in the Workflow Automation application as events. Your organization's Business Insights admins investigating the events can notify you about the event through an email notification. This notification comes from the Workflow Automation Admin Portal, where the organization records and evaluates all events. The notification contains a link with the survey that you must complete to justify that event.
Viewing the Notification
When an event occurs, you receive a notification requesting justification. The notification contains the following information:
- **Application**: The name of the application.
- **Plan Type**: The plan type under which your organization has provisioned you this application.
- **Event ID**: The Event ID.
- **Event Detail Link**: A link to access the **Event** page where you can view the event details and also take a survey to justify the event. This link is only valid for 24 hours.
- **Inactivity Period**: The inactivity period in days.
- **Note to the User**: A note to the user from the admin who initiated the notification. This note appears only if the admin enters a note.
The following image is an example of a user notification email.
[See image.](#Email-Notification-Image)
Depending on your email settings, notification emails might be tagged as spam and sent to your spam folder. Change your settings to receive the notification emails directly in your inbox.
Viewing the Event Details
To view the details of the event, click the **Event Detail Link** provided in the user notification. You are redirected to the **Event** page, where you can view the following details:
- **Event ID**: The ID of the event.
- **Event Date**: The date and time when the event occurred.
- **Priority**: The priority of the event.
- **Application**: The application for which the event is created.
- **Event Type**: The type of the event.
- **Plan Type**: The plan type under which the application is provisioned.
[See image.](#overview-image)
Completing the Survey
After reviewing the event details, you might be required to complete a survey at the end of the **Event** page to justify the inactivity. To provide justification, complete the following survey and then click **Submit**:
- **Justification Type**: Select a justification type for the event.
- **Justification Reason**: Enter a justification reason in detail for the event.
[See image.](#justification-image)
Your justification response is sent to the organization's admin who is investigating the event for further review.
[]![Viewing the End User's Event Notification Email.  The notification displays the Application, Plan Type, Event ID, Inactivity Period, Note to the User, and an Event Detail Link. ](/downloads/workflow-automation/business-insights/events/responding-end-user-notification-events/WA-BI-End-User-Event-Not-Email.png)
[]![Viewing the justification survey on the Event page. The survey includes a Justification Type field and a Justification Reason field.](/downloads/workflow-automation/business-insights/events/responding-end-user-notification-events/WA-BI-End-User-Event-Email-Notification-Survey-Section.png)
[]![Viewing the Overview section on the Event page](/downloads/workflow-automation/business-insights/events/responding-end-user-notification-events/WA-BI-End-User-Event-Email-Notification-Event-PG-Overview.png)