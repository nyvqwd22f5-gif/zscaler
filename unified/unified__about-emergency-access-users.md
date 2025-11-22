# About Emergency Access Users
Source: https://help.zscaler.com/unified/about-emergency-access-users
PDF: https://help.zscaler.com/pdf/com/en/1491426.pdf

Emergency access users are third-party users (e.g., contractors and vendors) that are created in an Okta IdP and configured on the [Emergency Access](/unified/configuring-emergency-access) page of the Admin Portal.
Emergency access users provide the following benefits and enable you to:
- Create emergency access users with permissions limited to privileged approvals in the specified IdP that is enabled for emergency access.
- Provision or deprovision third-party users.
- Authenticate and notify third-party users via email-based authentication and email-based notifications.
Prior to viewing and managing emergency access users, a list of prerequisites must be met. To learn more, see [Configuring Emergency Access](/unified/configuring-emergency-access).
About the Emergency Access Users Page
The Emergency Access Users page is not visible if you are within a Microtenant that has **Privileged Approvals** disabled. To learn more, see [About Microtenants](/unified/about-microtenants).
On the Emergency Access Users page (**Administration** > **Identity** > **Private Access** > **Emergency Access Users**), you can do the following:
- Refresh the Emergency Access Users page to reflect the most current information.
- Filter the information that appears in the table. By default, no filter is applied.
- View a list of emergency access users that were added. For each emergency access user, you can see:
- **First Name**: The first name of the emergency access user, as provided by the admin.
- **Last Name**: The last name of the emergency access user, as provided by the admin.
- **Email Address**: The email address of the emergency access user, as provided by the admin.
- **Status**: The status of the emergency user. The emergency access user can be in one of the following states:
- **Active**: Indicates when the user is activated and has completed the email-based authentication.
- **Staged**: Indicates when the user is created in the IdP but neither activated or deactivated.
- **Provisioned**: Indicates when the user is created and activated in the IdP, but still needs to complete activation via email-based authentication.
- **Deprovisioned**: Indicates when the user is created in the IdP but not activated.
- **Suspended**: Indicates when the user does not have access to applications within the IdP.
Other statuses (e.g., **Password Expired**, **Locked Out**, **Recovery**) might appear. To learn more, refer to the [Okta Help Center](https://support.okta.com/help/s/article/What-are-the-different-user-statuses-in-the-Okta-Password-Health-Check-Report?language=en_US).
- **Activation Date**: The date and time when the emergency access user was activated by the admin.
- **Last Login Date**: The date and time when the emergency access user last logged in.
- [Edit an emergency access user](/unified/editing-emergency-access-users).
- Activate an emergency access user.
- Deactivate an emergency access user.
![Viewing the Emergency Access Users page](/downloads/unified/administration/private-applications/identity/idp-device-configuration/emergency-access-authentication/configuring-emergency-access/unified-emergency-access-users.png)