# Viewing Alert Notifications
Source: https://help.zscaler.com/workflow-automation/viewing-alert-notifications
PDF: https://help.zscaler.com/pdf/com/en/1452701.pdf

The Notification Center page in Workflow Automation displays alerts that affect the operation of Workflow Automation. The following are the alert notifications that you might view on the Notification Center page:
| Module | Alert Summary | Severity |
| ------ | ------------- | -------- |
| Filewatcher | The Filewatcher is experiencing issues for Host IP: {`hostIP` } SystemId: {`systemId`} with integration: {`integrationName`} | High |
| Incident Group | Default incident group does not have an admin | High |
| Incident Receiver | The IR is experiencing issues for SystemId: `{systemId}` with integration: {`integrationName}` | High |
| Integration | `{integrationName}` integration is not working | High |
| Notification | No active channel for user digest notification | High |
| Notification | No active channel for admin digest notification | High |
To view alert notifications:
In the Workflow Automation Admin Portal, from the left-side navigation, click the **Notification** icon. The **Notification Center** page appears, listing all the alert notifications.
[See image.](#alert-notification-icon)
For each alert notification, you can view:
- **ID**: The ID associated with the alert notification. It is a unique generated sequential ID.
- **Module**: The feature area of Workflow Automation that is related to this alert notification. For example, Filewatcher, Integration, Notification, Incident Receiver, or Incident Group.
- **Severity**: The severity of the alert notification.
- **Summary**: The summary description of the alert notification.
- **First Detected**: The date and time the alert issue was first detected.
- **Last Detected**: The date and time the alert issue was last detected.
[See image.](#Notification-Center-Page-Image)
[]![Viewing the Alert Notification icon on the left-side menu of the Workflow Automation Admin Portal](/downloads/workflow-automation/getting-started/admin-portal/viewing-alert-notifications/WA-Notification-Center-Menu-Navigation.png)
[]![Viewing Alert Notifications on the Notification Center page](/downloads/workflow-automation/getting-started/admin-portal/viewing-alert-notifications/WA-Notification-Center-Page.png)