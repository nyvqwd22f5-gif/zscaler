# About the App Panel
Source: https://help.zscaler.com/unified/about-app-panel
PDF: https://help.zscaler.com/pdf/com/en/1516096.pdf

The App Panel provides a deep dive into an app for a comprehensive picture of its security and posture. The App Panel consists of the following:
- [App Panel Header](#app-panel-header)
- [Overview Tab](#app-panel-overview)
- [Access Tab](#app-panel-access)
- [Activities Tab](#app-panel-activities)
- [Details Tab](#app-panel-details)
- [Notes Tab](#Notes-tab)
The contents of the App Panel vary depending on your 3rd-Party App Governance license. For questions about your license, contact your Zscaler Account team.
[]On the App Panel header, you can do the following:
- View the app's name, description, publisher, status (e.g., Enabled), origin (e.g., 3rd Party), category (e.g., Productivity), and other basic information. You can also see if the app is verified by the Zscaler 3rd-Party App Governance Threat Intelligence team. A Zscaler-verified app can still be malicious or pose a risk due to a compromised publisher, vulnerabilities, and overprivileged permissions. The app status can be:
- **Enabled**: The app is enabled on your Software as a Service (SaaS) platform and has enabled users assigned to it.
- **Deleted**: This status differs for each platform.
- Microsoft Azure: The app is deleted from the admin console.
- Google Workspace: The app no longer exists on your SaaS platform and the user tokens are revoked.
- Slack: The app is deleted if the last uninstallation date is later than the last consent date, or if there are no users using the app.
- Okta: The app is deleted if no entity is received from the Okta API after a certain threshold.
- GitHub: The app is deleted if no entity is received from the GitHub API after a certain threshold.
- Salesforce: The app is deleted if no entity is received from the Salesforce API after a certain threshold.
- Atlassian: Not applicable.
- **Disabled**: This status differs for each platform.
- Microsoft Azure: The app is disabled if the service principal is disabled.
- Google Workspace: The app is disabled if the users who are granted access are no longer active users.
- Slack: Not applicable.
- Okta: The core apps are disabled if they are inactive.
- GitHub: The app is disabled if the user account is suspended.
- Salesforce: Not applicable.
- Atlassian: Not applicable.
- **Not Installed**: The app was added to your inventory, but does not exist on your SaaS platform admin console.
- View or change the app's **Risk Score**. Hover over the risk score to view a breakdown of the score. To learn more about the risk score and how to update it, see [Updating the App Risk Score](/unified/updating-app-risk-score). Refer to the following table for the components used to calculate each app's risk score.
- View or change the app's **Classification**. To learn more, see [Classifying Apps](/unified/classifying-apps).
- View or change the app's **Automated Workflow** (e.g., [End User Review](/unified/configuring-end-user-review) or [Revoked/Banned](/unified/revoking-and-banning-apps)) if supported by the platform.
- Add the app to your inventory. The App Panel header appears in blue if the app is not currently in your inventory. To learn more, see [Add an App to Your Inventory](/unified/pre-vetting-apps#add-app-inventory).
- Add a note to the app detailing the reason for an action taken on the app. You can also add a custom notation or a score on the app. The person who recently added the note and the date and time the note was last updated are displayed. You can also modify the note by clicking the **Edit** icon next to the note.
![App Panel Header showing app info](/downloads/zia/policies/data-loss-prevention/apptotal/using-apptotal/about-app-panel/App_Panel_New.png)
The following table lists the findings and permissions scores for various apps:
| **Application** | **Findings** | **Permissions** | **Non-Contextual Findings** | **Non-Contextual Permissions** |
| --------------- | ------------ | --------------- | --------------------------- | ------------------------------ |
| Google Workspace | 0.7 | 0.3 | 0.75 | 0.25 |
| GitHub | 0.7 | 0.3 | 0.7 | 0.3 |
| Microsoft | 0.7 | 0.3 | 0.75 | 0.25 |
| Slack | 0.6 | 0.4 | 0.75 | 0.25 |
| Atlassian | 0.6 | 0.4 | 0.75 | 0.25 |
| Chrome Extensions | 0.6 | 0.4 | 0.85 | 0.15 |
| Okta | 0.6 | 0.4 | 0.5 | 0.5 |
| Salesforce | 0.7 | 0.3 | 0.7 | 0.3 |
| ServiceNow | 0.7 | 0.3 | 0.7 | 0.3 |
| Box | 0.7 | 0.3 | 0.7 | 0.3 |
| Zoom | 0.7 | 0.3 | 0.7 | 0.3 |
| Webex | 0.7 | 0.3 | 0.7 | 0.3 |
[]On the **Overview **tab, you can do the following:
- View a blast radius, showing the users who have access to the app, the services (e.g., Gmail) accessible by the app, and the access type (e.g., Broad Data Access).
- View **Usage **details, including who first authorized the app and who performed the last activity in the app.
- View **Findings** associated with the app. You can also change the status of a finding. To learn more, see[ Updating the App Finding Status](/unified/updating-app-finding-status).
![App Panel Overview tab displaying an overview of the app](/downloads/zia/policies/data-loss-prevention/apptotal/using-apptotal/about-app-panel/Overview_Tab.png)
[]On the **Access** tab, you can do the following:
- View the permission and access types (e.g., Sign in) granted to the app. Hover over each type for more information.
- View the scope of the permissions granted to the app. Click each permission for more information.
- View the users who have access to the app.
- View a breakdown of the API calls generated by the app.
- View information about the IP addresses associated with the app. Click the **VirusTotal** link for further security analysis.
![App Panel Access tab showing app access and permission info](/downloads/zia/policies/data-loss-prevention/apptotal/using-apptotal/about-app-panel/Access_Tab.png)
[]On the **Activities** tab, you can do the following:
- Search for a specific activity or user performing an activity associated with the app.
- Filter your search by the following activity types: **User Activity**, **Security Event**, **Findings**, and **Threat Insights**.
- Export your search results to a CSV file.
![App Panel Activities tab showing user activity](/downloads/zia/policies/data-loss-prevention/apptotal/using-apptotal/about-app-panel/Activities_Tab.png)
[]On the **Details **tab, you can do the following:
- View general information about the app, including the client ID, categories (e.g., Mail Client), and consent type (e.g., Individual). You can also see if the app comes from a marketplace and if it is platform verified. The following are the different consent types:
- **Domain wide:** Application permissions are granted tenant-wide by the admin, allowing all users to access the application unless otherwise restricted. This is supported on Google.
- **Individual:** Application permissions are granted per user (by the user). This is supported on Google.
- **Delegated:** Application permissions are an intersection between what the user is allowed to do and what the application is allowed to do. The app acts on behalf of the user. This is supported on Microsoft. To learn more, refer to the [Microsoft documentation](https://learn.microsoft.com/en-us/graph/auth/auth-concepts).
- **Application: **Application permissions are not limited by what a particular user can do. The app acts on its own behalf. This is supported on Microsoft. To learn more, refer to the [Microsoft documentation](https://learn.microsoft.com/en-us/security/zero-trust/develop/developer-strategy-application-permissions).
- View data protection and privacy information, including the app's terms of service, privacy policy, and vendor certifications (e.g., GDPR).
- View threat intelligence information associated with the app.
- View forensics information, including seen IP addresses, redirect and login URLs, and an image of the app's consent screen.
![App Panel Details tab showing the list of app info](/downloads/zia/policies/data-loss-prevention/apptotal/using-apptotal/about-app-panel/Details_Tab.png)
[]On the **Notes **tab, you can add a note to the app that details the reason for an action taken on the app. You can also add a custom notation or a score on the app. The person's name who recently added the note and the date and time the note was added display. Additionally, you can comment on notes that other users add.
You must have user or admin permissions to add notes to the app. To learn more, see [About Roles in 3rd-Party App Governance](/unified/about-roles-3rd-party-app-governance).
![App Panel Notes tab showing user notes](/downloads/tech-pubs-drafts/zia-draft-articles/about-app-panel-draft-doc-57316/App_Panel_Notes1.png)