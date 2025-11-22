# About Notifications
Source: https://help.zscaler.com/itdr/about-notifications
PDF: https://help.zscaler.com/pdf/com/en/1531779.pdf

The ITDR Notifications feature enables you to configure email notifications to keep you informed about vulnerabilities present in the identity platforms (Active Directory (AD), Entra ID, etc.) and endpoints. After AD domains, Entra ID tenants, and endpoints are successfully scanned for vulnerabilities and results are generated, the configured recipients receive emails with the executive summary reports or bad changes.
The Notifications feature provides the following benefits and enables you to:
- Continuously monitor your identity platforms and endpoints for misconfigurations and vulnerabilities.
- Be informed about the critical risks in your identity platforms and endpoints via emails.
- Swiftly prioritize and remediate issues to reduce the overall risk.
About the Notifications Page
On the Notifications page (ITDR > Notifications > Configure), you can do the following:
- Configure notifications for the following alert types:
- [AD posture](/itdr/configuring-active-directory-posture-notification): Generate emails with AD executive summary reports after the configured AD domains are successfully scanned.
- [AD change detection](/itdr/configuring-active-directory-change-detection-notification): Generate emails with bad change details after the configured AD domains are successfully scanned.
- [Endpoint credential scan](/itdr/configuring-endpoint-credential-scan-notification): Generate emails with endpoint credential exposure executive reports after the endpoints are successfully scanned.
- [Entra ID posture](/itdr/configuring-entra-id-posture-notification): Generate emails with Entra ID executive summary reports after the configured Entra ID tenants are successfully scanned.
- [Entra ID change detection](/itdr/configuring-entra-id-change-detection-notification): Generate emails with bad change details after the configured Entra ID tenants are successfully scanned.
- View a list of configured notifications. For each notification, you can view:
- **Enabled**: The status of the notification. The checkmark icon indicates that the notification is enabled, and the **X** icon indicates that the notification is disabled.
- **Name**: The name of the notification. You can filter the notifications based on name.
- **Type**: The type of alert (**Active Directory Posture**, **Active Directory Change Detection**, **Credential Scanning**, **Entra Posture**, and **Entra Change Detection**). You can filter the notifications based on alert type.
- **Domains**: The AD domain or Entra ID tenant name.
- **Recipients**: The email recipient's name and email address.
- [Edit or delete a notification](/itdr/editing-or-deleting-notification).
![About the ITDR Notifications page](/downloads/itdr/notifications/about-notifications/itdr-about-notifications-configure-page-2.png)