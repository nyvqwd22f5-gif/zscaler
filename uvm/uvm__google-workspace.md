# Google Workspace
Source: https://help.zscaler.com/uvm/google-workspace
PDF: https://help.zscaler.com/pdf/com/en/1528366.pdf

![The Google Workspace tile](/downloads/uvm/configure/sources/google-workspace/Screen%20Shot%202023-11-06%20at%2010.40.02.png)
Google Workspace is a suite of cloud-based productivity tools, including Gmail, Google Drive, Docs, Sheets, and Meet, designed to facilitate communication, collaboration, and productivity for businesses and organizations.
Required Parameters:
- Service account credentials: To learn more, refer to the [Google Workspace documentation](https://developers.google.com/workspace/guides/create-credentials#service-account).
- The email address of the workspace admin who created the service account.
To create a service account with delegated domain-wide authority:
- Create access credentials. This account must be created by an administrator of the Google Workspace. To learn more, refer to the [Google Workspace documentation](https://developers.google.com/workspace/guides/create-credentials).
- Grant the following OAuth scopes to the service user:
- `https://www.googleapis.com/auth/admin.reports.audit.readonly`
- `https://www.googleapis.com/auth/admin.reports.usage.readonly`
The SecOps platform can connect to the following Google Workspace applications:
| **Application** | **Description** |
| --------------- | --------------- |
| Admin Activity | Provides information about administrative actions taken within the Google Workspace domain, including user management, settings changes, and other administrative tasks. |
| Mobile Activity | Tracks mobile device usage within the Google Workspace domain, including information about device types, operating systems, and user activities on mobile devices. |
| Rules Activity | Monitors activities related to organizational rules and policies, providing insights into rule enforcement and any actions taken based on these rules. |
| Tokens Activity | Offers details about token usage within the domain, including authentication tokens used for accessing various Google services and applications. |
| User Accounts Activity | Provides information about user account activities, such as account creation, deletion, or modification, offering insights into user management processes. |
| Drive Activity | Monitors activities related to Google Drive, offering insights into file uploads, downloads, sharing, and other interactions with documents stored in Google Drive. |
| Login Activity | Provides information about user login events, including details like login times, IP addresses, and devices used for authentication. |
| OAuth Tokens Activity | Offers information about OAuth tokens usage, including details about the creation, expiration, and revocation of OAuth tokens. |
| Transparency Activity | Provides insights into activities related to Google's transparency reports, which may include information about government requests for user data. |
| Calendar Activity | Monitors activities related to Google Calendar, including event creation, modification, and attendance information. |
| Chat Activity | Tracks activities within Google Chat, including messages sent, conversations, and other interactions within the chat platform. |
| Chrome Activity | Provides insights into activities related to the Google Chrome browser within the domain, including browser usage and settings. |
| Context-Aware Access Activity | Monitors activities related to context-aware access policies, which help control access to resources based on factors like location, device, and user identity. |
| Data Studio Activity | Tracks activities related to Google Data Studio, a data visualization and reporting tool, including report creation, sharing, and interaction. |
| Google Cloud Platform Activity | Provides information about activities related to the Google Cloud Platform (GCP), which includes services like computing, storage, and data analytics |
| Google+ Activity | Monitors activities related to Google+. Google+ has been discontinued. |
| Groups Activity | Provides insights into activities related to Google Groups, including group creation, membership changes, and group interactions. |
| Jamboard Activity | Tracks activities related to Google Jamboard, a collaborative digital whiteboard tool, including board creation, edits, and sharing. |
| Keep Activity | Monitors activities related to Google Keep, a note-taking app, including note creation, edits, and sharing. |
| SAML Activity | Provides insights into activities related to Security Assertion Markup Language (SAML) authentication, which is used for single sign-on (SSO) in Google Workspace. |
| Enterprise Groups Activity | Tracks activities related to enterprise groups within Google Workspace, including group creation, membership changes, and group interactions. |