# Managing Forced Reauthentication
Source: https://help.zscaler.com/zia/managing-forced-reauthentication
PDF: https://help.zscaler.com/pdf/com/en/1458906.pdf

You can force all users to reauthenticate on the Default Settings page (Administration > Authentication Settings > Default Settings).
Instead of forcing reauthentication, Zscaler recommends using [SCIM](/zia/about-scim) [provisioning](/zia/choosing-provisioning-and-authentication-methods) for complete user lifecycle management.
The Force Reauthentication for all Users section shows the following information:
- **Last Reauthentication**: Displays the last time **Force Reauthentication** was completed.
- **Force Reauthentication**: Click **Start** to log out all users in your organization and force them to reauthenticate to the Zscaler service. This may take several minutes depending on the number of users in your organization. During this process, the Central Authority (CA) invalidates all authentication cookies for the users in your organization. When your users try to access the internet, the Zscaler service detects that their authentication cookies have expired, and as a result, the users must log in again.
This feature doesn't apply to users with Zscaler Client Connector.
- **Reauthentication Status**: Displays one of the following logout states.
- **Completed**: The CA logged out all users successfully. The **Last Reauthentication **field updates the time accordingly.
- **In Progress**: The CA is in the process of logging out all users.
- **Error**: The CA failed to log out all users. Under **Force Reauthentication**, an error message displays explaining why the logout failed. You can click **Retry** after the error is addressed.
[See image.](#Error-status)
- **None**: Displays if you have never executed **Force Reauthentication** in the ZIA Admin Portal.
![Image of the Force Reauthentication for All Users section](/downloads/zia/authentication-administration/user-management-authentication-settings/managing-forced-reauthentication/Force%20reauthentication.png)
[]![Reauthentication Status error message](/downloads/zia/authentication-administration/user-management-authentication-settings/managing-forced-reauthentication/reauthentication_error_status.png)