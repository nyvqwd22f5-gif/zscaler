# About Emergency Access Users
Source: https://help.zscaler.com/zpa/about-emergency-access-users
PDF: https://help.zscaler.com/pdf/com/en/1485696.pdf

Emergency access users are third-party users (e.g., contractors and vendors) that are created in an Okta IdP and configured on the [Emergency Access](/zpa/configuring-emergency-access) page of the Zscaler Private Access (ZPA) Admin Portal.
Emergency access users provide the following benefits and enable you to:
- Create emergency access users with permissions limited to privileged approvals in the specified IdP that is enabled for emergency access.
- Provision or deprovision third-party users.
- Authenticate and notify third-party users via email-based authentication and email-based notifications.
Prior to viewing and managing emergency access users, a list of prerequisites must be met. To learn more, see [Configuring Emergency Access](/zpa/configuring-emergency-access).
About the Emergency Access Users Page
The Emergency Access Users page is not visible if you are within a Microtenant that has **Privileged Approvals** disabled. To learn more, see [About Microtenants](/zpa/about-microtenants).
On the Emergency Access Users page (Authentication > User Authentication > Emergency Access Users), you can do the following:
- View a list of applied filters available from the current and previous user sessions. Applied filters must be saved to the user session first before they can be viewed. Use the drop-down menu to select the applied filters to view. To learn more, see [Using Tables](/zpa/using-tables#filterData).
- Hide the filters on the page by clicking **Hide Filters**. Click **Show Filters** to display the filters.
- Refresh the Emergency Access Users page to reflect the most current information.
- Filter the information that appears in the table. By default, no filter is applied. You can also save applied filters to your preferences so that they're visible in future user sessions. To learn more, see [Using Tables](/zpa/using-tables#filterData).
- View a list of emergency access users that were added. For each emergency access user, you can see:
- **First Name**: The first name of the emergency access user, as provided by the admin.
- **Last Name**: The last name of the emergency access user, as provided by the admin.
- **Email Address**: The email address of the emergency access user, as provided by the admin.
- **Status**: The status of the emergency user. The emergency access user can be in one of the following states:
- **Active**: Indicates when the user is activated and has completed the email-based authentication.
- **Staged**: Indicates when the user is created in the IdP but neither activated nor deactivated.
- **Provisioned**: Indicates when the user is created and activated in the IdP, but still needs to complete activation via email-based authentication.
- **Deprovisioned**: Indicates when the user is created in the IdP but not activated.
- **Suspended**: Indicates when the user does not have access to applications within the IdP.
Other statuses (e.g., **Password Expired**, **Locked Out**, **Recovery**) might appear. To learn more, refer to the [Okta Help Center](https://support.okta.com/help/s/article/What-are-the-different-user-statuses-in-the-Okta-Password-Health-Check-Report?language=en_US).
- **Activation Date**: The date and time when the emergency access user was activated by the admin.
- **Last Login Date**: The date and time when the emergency access user last logged in.
- [Edit an emergency access user](/zpa/editing-emergency-access-users).
- Activate an emergency access user.
- Deactivate an emergency access user.
- [Modify the columns displayed in the table.](/zpa/using-tables)
- Open the [Zscaler Help Browser](/zpa/using-zscaler-help-browser) and view Help Portal articles without leaving the ZPA Admin Portal.
- Go to the [IdP Configuration](/zpa/about-idp-configuration) page to add a new IdP for single sign-on (SSO) or manage existing configurations.
- Go to the [SAML Attributes](/zpa/about-saml-attributes) page to import attributes or add them manually.
- Go to the [Settings](/zpa/configuring-authentication-settings) page to modify authentication settings (e.g., enabling Remote Assistance).
- Go to the [Emergency Access](/zpa/configuring-emergency-access) page to configure emergency access for third-party users.
![Viewing the Emergency Access Users page](/downloads/zpa/authentication/emergency-access-authentication/about-emergency-access-users/zpa-emergency-access-users-page-react.png)