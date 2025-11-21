# About Integrations
Source: https://help.zscaler.com/zpa/about-integrations
PDF: https://help.zscaler.com/pdf/com/en/1485521.pdf

Files can be transferred securely through the ZPA cloud via a designated privileged console from a Privileged Remote Access (PRA) portal. These files can then be downloaded or uploaded with the option to inspect the files using Zscaler Internet Access (ZIA) Sandbox File Transfer.
Configuring the integrations for the ZIA Sandbox File Transfer provides the following benefit and enables you to:
- Inspect files you are uploading in a privileged console for malware or malicious content.
- Safeguard the privileged console by inspecting larger files.
To enable the Inspect option for the File Transfer feature for privileged consoles, you first need to set up the parameters for the ZIA Sandbox integration. If you do not set up the integration configurations, then the Inspect option is automatically disabled.
After you have configured the ZIA Sandbox integration, set up the privileged capabilities policy for the privileged consoles.
About the Integrations Page
The Integrations page is read-only for [Microtenant](/zpa/about-microtenants) admins.
On the Integrations page (Configuration & Control > Administration Control > Integrations), you can do the following:
- Refresh the Integrations page to reflect the most current information.
- View and manage the Integration settings.
- Go to the [Administrators](/zpa/about-administrators) page to add new admins or manage existing admins.
- Go to the [Roles](/zpa/about-roles) page to add new admin roles or manage existing roles.
- Go to the [Audit Logs](/zpa/about-audit-logs) page to view and download admin audit log records.
- Go to the [Acceptable Use Policy](/zpa/about-user-portal-acceptable-use-policy) page to view or update the AUP for your user portals.
- Go to the [Microtenants](/zpa/about-microtenants) page to add new Microtenants or manage existing Microtenants.
The Microtenants page is only visible for Default Microtenant admins.
- Go to the [Client Sessions](/zpa/about-client-sessions) page to view or delete current sessions.
- Go to the [Disaster Recovery](/zpa/about-disaster-recovery) page to view critical application segments, ZPA Private Service Edge groups, or App Connector groups that are designated for disaster recovery. You can also view and configure the [disaster recovery settings](/zpa/about-disaster-recovery-settings).
- Go to the [Client Connector IP Assignment](/zpa/about-client-connector-ip-assignment) page to manage Zscaler virtual IP addresses and view IP bindings for use with server-to-client connectivity.
![Using the Integrations page ](/downloads/zpa/administration/about-integrations/zpa-integrations-page_0.png)
Configuring Integration Settings
To configure Integration settings (Configuration & Control > Administration Control > Integrations):
- Complete the following fields:
- **ZIA Cloud**: Enter the name of the ZIA Cloud with the Sandbox you are accessing.
- **Cloud Service API Key**: Enter the API key for the ZIA Cloud.
- **ZIA Admin Username**: Enter the username for that specific ZIA Admin account.
- **ZIA Admin Password**: Enter the password for that specific ZIA Admin account.
- **Sandbox API Token**: Enter the API key for the ZIA Sandbox.
If you don’t include the username, password, or token, you cannot continue. All fields must be completed before you can move forward.
- Click **Save**.
[See image.](#Integration)
[]![Configuring the Integration fields in the ZPA Admin Portal ](/downloads/zpa/administration/disaster-recovery-administration/about-disaster-recovery-settings/complete%20fields.png)