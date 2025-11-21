# Role-Based Administration Configuration Examples
Source: https://help.zscaler.com/zia/role-based-administration-configuration-examples
PDF: https://help.zscaler.com/pdf/com/en/1399741.pdf

With [role-based administration](/zia/configuring-role-based-administration), organizations can [add admins](/zia/adding-admins) and assign them specific [roles](/zia/adding-admin-roles) with different levels of access to the ZIA Admin Portal features.
The following examples illustrate how an organization can leverage role-based administration for various scenarios:
- [Allow HR Admins Access to Access Control Policies](#hr-admin-access-control)
- [Allow Security Admins Access to Security Policies](#security-admin)
- [Allow Admins View Only Access to the Zscaler Client Connector Portal](#configuration-for-administrator)
Admins with **Full** or **View Only** permissions for the **Dashboard**, **Reporting Access**, and **Insights Access** can only view the ZIA features if the corresponding** **functional scope is enabled.
[]For this example, let's consider your organization has an office located in the US and another office located in the UK, and requires HR admins with the following conditions in these two locations:
- They should manage access-control policies like URL filtering and bandwidth usage.
- They are responsible for providing reports on employee web usage to measure productivity and ensure compliance.
- They are ranked lower than the VP of HR, who has an admin account with an admin rank of 2, to ensure that the VP has the final say on access-control policies.
- They have access to logs for an unrestricted period of time.
- They have full access to the dashboard and reporting, and view-only access to insights.
- They have full access to access-control policies.
- They don't have access to administration controls.
- They cannot see real usernames and device information (i.e., device name, device hostname, and device owner) in logs.
- They cannot view or make changes to any other policies beyond access-control policies.
- They do not need to receive Zscaler security, product, or service updates.
- They can log in to the ZIA Admin Portal directly from the organization's single sign-on (SSO) provider portal (password-based login is not required).
To configure an admin with the preceding specifications:
- [Step 1: Add the Admin Role](#admin-role-us-uk)
- [Step 2: Add the US Admin Account](#us-admin)
- [Step 3: Add the UK Admin Account](#uk-admin)
To configure an admin role:
- []Go to **Administration **> **Role Management**.
- Click **Add Administrator Role**.
-
In the **Add Administrator Role** window:
- **Name**:** **Enter a name for the admin role.
- **Enable Permissions for Executive Insights**: Disable this option.
- **Permissions**: Select permissions for the following categories:
- **Admin Rank**: Select an admin rank lower than 2. For example, select **3**.
- **Logs Limit (Days)**:** **Select** Unrestricted**.
- **Dashboard Access**:** **Select **Full**.
- **Reporting Access**: Select **Full**.
- **Insights Access**: Select **View Only**.
- **Alerts Access**: Select **View Only**.
- **User Names**: Select **Obfuscated**.
- **Device Information**: Select **Obfuscated**.
- Select permissions for the following scopes:
- **Policy & Components**: Assign **Full** permission for all the features under the **Policy Control** and **Policy Components** sections in the **Access Control** tab. Assign **None **permission** **for **Security**, **Data Protection**, **Decryption**, **URL Categories**, and **Shared Policy Components** tabs in this scope.
- **Cloud Configuration & Integration**: Assign **None** permission for integrations and cloud-configurations features under the **Integrations** and **Cloud Configuration **tabs, respectively.
- **Traffic Forwarding**: Assign **None** permission for **Traffic Forwarding**, **Traffic Forwarding Methods**, and **Traffic Forwarding Components** features.
- **Administration Controls**: Assign **None** permission for **Administration Controls** and **Backup Controls** features.
- **Reporting Data**: Assign **None** permission for the reporting features.
[See image.](#hr-admin-role)
This role can then be assigned to both admins since they are performing the same tasks in the ZIA Admin Portal. To learn more about configuring admin roles with different permissions and scope, see [Adding Admin Roles](/zia/adding-admin-roles).
To configure an admin for the US location:
- []Go to **Administration **>** Administrator Management**.
- Click **Add Administrator**.
-
In the **Add Administrator** window:
- **Login ID**: Enter a login ID for the admin.
- **Email**: Enter an email address for the admin.
- **Name**:** **Enter a name for the admin.
- **Role**: Choose the role you added in the previous [step](/zia/examples-role-based-administration#admin-role-us-uk).
- **Scope**: Choose **Location**. The** Locations** field appears.
- **Locations**: Select your US office location. In this example, it is **USA Office**.
- **Executive Insights App Access**: Disable this option.
- **Comments**: Enter any additional notes or information.
- **Security Updates**: Disable this option.
- **Service Updates**: Disable this option.
- **Product Updates**: Disable this option.
- **Password Based Login**: Disable this option.
[See image.](#seeimage-us-admin)
To configure an admin for the UK location:
- []Go to **Administration **>** Administrator Management**.
- Click **Add Administrator**.
-
In the **Add Administrator** window:
- **Login ID**: Enter a login ID for the admin.
- **Email**: Enter an email address for the admin.
- **Name**:** **Enter a name for the admin.
- **Role**: Choose the role you added in the initial [step](/zia/examples-role-based-administration#admin-role-us-uk).
- **Scope**: Choose **Location**.
- **Locations**: Select your UK office location. In this example, it is **UK Office**.
- **Executive Insights App Access**: Disable this option.
- **Comments**: Enter any additional notes or information.
- **Security Updates**: Disable this option.
- **Service Updates**: Disable this option.
- **Product Updates**: Disable this option.
- **Password Based Login**: Disable this option.
[See image.](#seeimage-uk-admin)
[]For this example, let's consider that your organization requires that admins have access to configure security policies for the organization, and you require two types of admin accounts, CISO and Security Response Manager, with the following conditions:
- A CISO admin account that has:
- A higher admin rank than the Security Response Manager, but a lower rank than the CEO, who has an admin account with a rank of 1.
- Access to logs for an unrestricted period of time.
- Full access to dashboards and reporting, and view-only access to insights.
- Full access to configure security policies for the organization.
- No access to administration controls.
- Ability to view usernames and device information (i.e., device name, device hostname, and device owner).
- Access to Zscaler security, product, and service updates.
- Ability to log in to the ZIA Admin Portal directly fro
- m the organization's SSO provider portal (password-based login is not required).
- A Security Response Manager admin account that has:
- A lower admin rank than the CISO.
- Access to logs for 30 days.
- Full access to dashboards and reporting and view-only access to insights.
- View-only access to the organization's security policies.
- No access to administration controls.
- Ability to view usernames and device information (i.e., device name, device hostname, and device owner).
- Access to Zscaler security, product, and service updates.
- Ability to log in to the ZIA Admin Portal directly from the organization's SSO provider portal (password-based login is not required).
To configure an admin with the preceding specifications:
- [Step 1: Add the CISO Admin Role](#ciso-admin-role)
- [Step 2: Add the Security Response Manager Admin Role](#security-response-admin-role)
- [Step 3: Add the CISO Admin Account](#ciso-admin-account)
- [Step 4: Add the Security Response Manager Admin Account](#security-response-admin-acc)
To configure a CISO admin role:
- []Go to **Administration **> **Role Management**.
- Click **Add Administrator Role**.
-
In the **Add Administrator Role** window:
- **Name**:** **Enter a name for the admin role.
- **Enable Permissions for Executive Insights**: Disable this option.
- **Permissions**: Select permissions for the following categories:
- **Admin Rank**: Select an admin rank lower than 1. For example, select **2**.
- **Logs Limit (Days)**:** **Select** Unrestricted**.
- **Dashboard Access**:** **Select **Full**.
- **Reporting Access**: Select **Full**.
- **Insights Access**: Select **View Only**.
- **Alerts Access**: Select **View Only**.
- **User Names**: Select **Visible**.
- **Device Information**: Select **Visible**.
- Select permissions for the following scopes:
- **Policy & Components**: Assign **Full** permission for all the features under the **Security** tab. Assign **None **permission** **for **Access Control**, **Data Protection**, **Decryption**, **URL Categories**, and **Shared Policy Components** tabs in this scope.
- **Cloud Configuration & Integration**: Assign **None** permission for integrations and cloud-configurations features under the **Integrations** and **Cloud Configuration **tabs, respectively.
- **Traffic Forwarding**: Assign **None** permission for **Traffic Forwarding**, **Traffic Forwarding Methods**, and **Traffic Forwarding Components** features.
- **Administration Controls**: Assign **None** permission for **Administration Controls** and **Backup Controls** features.
- **Reporting Data**: Assign **None** permission for the reporting features.
[See image.](#ciso-admin-role-image)
To learn more about configuring admin roles with different permissions and scope, see [Adding Admin Roles](/zia/adding-admin-roles).
To configure a Security Response Manager admin role:
- []Go to **Administration **> **Role Management**.
- Click **Add Administrator Role**.
-
In the **Add Administrator Role** window:
- **Name**:** **Enter a name for the admin role.
- **Enable Permissions for Executive Insights**: Disable this option.
- **Permissions**: Select permissions for the following categories:
- **Admin Rank**: Select an admin rank lower than the CISO admin. For example, select **3**.
- **Logs Limit (Days)**:** **Select** 30**.
- **Dashboard Access**:** **Select **Full**.
- **Reporting Access**: Select **Full**.
- **Insights Access**: Select **View Only**.
- **Alerts Access**: Select **View Only**.
- **User Names**: Select **Visible**.
- **Device Information**: Select **Visible**.
- Select permissions for the following scopes:
- **Policy & Components**: Assign **View Only** permission for all the features under the **Security** tab. Assign **None **permission** **for **Access Control**, **Data Protection**, **Decryption**, **URL Categories**, and **Shared Policy Components** tabs in this scope.
- **Cloud Configuration & Integration**: Assign **None** permission for integrations and cloud-configurations features under the **Integrations** and **Cloud Configuration **tabs, respectively.
- **Traffic Forwarding**: Assign **None** permission for **Traffic Forwarding**, **Traffic Forwarding Methods**, and **Traffic Forwarding Components** features.
- **Administration Controls**: Assign **None** permission for **Administration Controls** and **Backup Controls** features.
- **Reporting Data**: Assign **None** permission for the reporting features.
[See image.](#srm-admin-role)
To learn more about configuring admin roles with different permissions and scope, see [Adding Admin Roles](/zia/adding-admin-roles).
[]To configure a CISO admin:
- Go to **Administration **>** Administrator Management**.
- Click **Add Administrator**.
-
In the **Add Administrator** window:
- **Login ID**: Enter a login ID for the admin.
- **Email**: Enter an email address for the admin.
- **Name**:** **Enter a name for the admin.
- **Role**: Choose the role you added in the initial [step](/zia/examples-role-based-administration#ciso-admin-role).
- **Scope**: Choose **Organization**.
- **Executive Insights App Access**: Disable this option.
- **Comments**: Enter any additional notes or information.
- **Security Updates**: Enable this option.
- **Service Updates**: Enable this option.
- **Product Updates**: Enable this option.
- **Password Based Login**: Disable this option.
[See image.](#seeimage22c)
[]To configure a Security Response Manager admin:
- Go to **Administration **>** Administrator Management**.
- Click **Add Administrator**.
-
In the **Add Administrator** window:
- **Login ID**: Enter a login ID for the admin.
- **Email**: Enter an email address for the admin.
- **Name**:** **Enter a name for the admin.
- **Role**: Choose the role you added in the previous [step](/zia/examples-role-based-administration#security-response-admin-role).
- **Scope**: Choose **Organization**.
- **Executive Insights App Access**: Disable this option.
- **Comments**: Enter any additional notes or information.
- **Security Updates**: Enable this option.
- **Service Updates**: Enable this option.
- **Product Updates**: Enable this option.
- **Password Based Login**: Disable this option.
[See image.](#seeimage24b)
[]For this example, let's consider that your organization requires admins to have view-only access to the Zscaler Client Connector Portal and you require admins with the following conditions:
- They need view-only access to the dashboard.
- They should have access to logs for an unrestricted period of time.
- They should have view-only access to traffic-forwarding components.
- They don't have reporting access.
- They don't have access to administration controls.
- They cannot view usernames and device information (i.e., device name, device hostname, and device owner) in logs.
- They do not need to receive Zscaler security, product, or service updates.
To configure an admin with the preceding specifications:
- [Step 1: Add the Admin Role](#role-management-steps)
- [Step 2: Add the Admin](#administrator-management-steps)
[]To configure an admin role with view-only access to Zscaler Client Connector Portal:
- Go to **Administration **> **Role Management**.
- Click **Add Administrator Role**.
-
In the **Add Administrator Role** window:
- **Name**:** **Enter a name for the admin role.
- **Enable Permissions for Executive Insights**: Disable this option.
- **Permissions**: Select permissions for the following categories:
- **Admin Rank**: Select a lower admin rank.
- **Logs Limit (Days)**:** **Select** Unrestricted**.
- **Dashboard Access**:** **Select **View Only**.
- **Reporting Access**: Select **View Only**.
- **Insights Access**: Select **None**.
- **Alerts Access**: Select **None**.
- **User Names**: Select **Obfuscated**.
- **Device Information**: Select **Obfuscated**.
- Select permissions for the following scopes:
- **Policy & Components**: Assign **None** permission for all the features under the **Security**, **Access Control**, **Data Protection**, **Decryption**, **URL Categories**, and **Shared Policy Components** tabs in this scope.
- **Cloud Configuration & Integration**: Assign **None** permission for integrations and cloud-configurations features under the **Integrations** and **Cloud Configuration **tabs, respectively.
- **Traffic Forwarding**: Assign **View Only** permission only to the Zscaler Client Connector Portal feature under the **Traffic Forwarding Components** section. Assign **None** permission to all other features in the **Traffic Forwarding Components** section and all the features in the **Traffic Forwarding** and **Traffic Forwarding Methods** sections in this scope.
- **Administration Controls**: Assign **None** permission for **Administration Controls** and **Backup Controls** features.
- **Reporting Data**: Assign **None** permission for the reporting features.
[See image.](#zcc-admin-role)
To learn more about configuring admin roles with different permissions and scope, see [Adding Admin Roles](/zia/adding-admin-roles).
[]To configure an admin:
- Go to **Administrator** > **Administrator Management**.
- Click **Add Administrator**.
-
In the **Add Administrator **window:
- **Login ID**: Enter a login ID for the admin.
- **Email**: Enter an email address for the admin.
- **Name**:** **Enter a name for the admin.
- **Role**: Choose the role you added in the previous [step](#role-management-steps).
- **Scope**: Choose **Organization**.
- **Executive Insights App Access**: Disable this option.
- **Comments**: Enter any additional notes or information.
- **Security Updates**: Disable this option.
- **Service Updates**: Disable this option.
- **Product Updates**: Disable this option.
- **Password Based Login**: Disable this option.
[See image.](#Admin-management)
![The Add Administrator Role window displaying configurations for an admin with Full access to Access Control policies](/downloads/zia/authentication-administration/administrator-role-management/role-based-administration-configuration-examples/zia-admin-role-configuration-examples-hr-admin-role.png)
[]
[]![The Add Administrator window displaying configurations for HR-Access Control](/downloads/zscaler-tech-pubs-style-guide/draft-articles/role-based-administration-configuration-examples-draft/Add%20Administrator%20for%20HR-Access%20Control.png?1622222945)
[]![The Add Administrator window displaying configurations for UK HR-Access Control](/downloads/zscaler-tech-pubs-style-guide/draft-articles/role-based-administration-configuration-examples-draft/Add%20Administrator%20for%20UK%20HR-Access%20Control.png)
![The Add Administrator Role window displaying configurations for an admin with Full access to Security policies](/downloads/zia/authentication-administration/administrator-role-management/role-based-administration-configuration-examples/zia-admin-role-configuration-examples-ciso-admin-role.png)
[]
![The Add Administrator Role window displaying configurations for an admin with View Only access to Security policies](/downloads/zia/authentication-administration/administrator-role-management/role-based-administration-configuration-examples/zia-admin-role-configuration-examples-security-response-manager-admin-role.png)
[]
[]![The Add Administrator window displaying configurations for CISO admin account](/downloads/zscaler-tech-pubs-style-guide/draft-articles/role-based-administration-configuration-examples-draft/Add%20the%20CISO%20admin%20account.png)
[]![ The Add Administrator window displaying configurations for Security Response Manager admin account](/downloads/zscaler-tech-pubs-style-guide/draft-articles/role-based-administration-configuration-examples-draft/Add%20the%20Security%20Response%20Manager%20admin%20account.png)
![The Add Administrator Role window displaying configurations for an admin with View Only access to Zscaler Client Connector Portal](/downloads/zia/authentication-administration/administrator-role-management/role-based-administration-configuration-examples/zia-admin-role-configuration-examples-zcc-admin-role.png)
[]
[]![The Add Administrator window displaying configurations for a Read-Only (view-only) admin role](/downloads/zscaler-tech-pubs-style-guide/draft-articles/role-based-administration-configuration-examples-draft/Add%20Administrator%20for%20Read-only_0.png)