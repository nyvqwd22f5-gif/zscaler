# Authorizing a Custom Zscaler Connector for Salesforce
Source: https://help.zscaler.com/zia/authorizing-custom-zscaler-connector-salesforce
PDF: https://help.zscaler.com/pdf/com/en/1529827.pdf

The Zscaler service supports custom, client-side connector onboarding for access to Salesforce. With this functionality, instead of requiring full administrator credentials, the Zscaler service can use a minimum set of credentials to access Salesforce.
When you create a custom connector for Salesforce for SSPM Scan, you must provide the client ID, client secret, integration user's username, and instance URL in the ZIA Admin Portal so that the Zscaler service can access the application. For DLP and Malware scanning SaaS API onboarding, you additionally must include the Malware and DLP quarantine library names.
To create a custom connector for Salesforce:
- [][Sandbox Tenant](#Sandbox)
- [][Production Tenant](#Production)
- [][1. Create a system administrator profile with a Salesforce license.](#admin_role_sand)
- [2. Create permission set.](#permission_set_sand)
- [3. Assign permission set to admin user.](#assign_set_sand)
- [4. Create a connected app.](#create_app_sand)
- [5. Create libraries for quarantine policy actions. (DLP and Malware only)](#quarantine_sand)
- [6. Finish setup settings.](#setup_sand)
- [7. Generate Private Key file.](#private_sand)
- [8. Copy Client ID and Client Secret.](#client_sand)
- [9. Authorize the custom connector.](#authorize_sand)
- [][][1. Create a system administrator profile with a Salesforce license.](#admin_role_pro)
- [2. Create permission set.](#permission_set_pro)
- [3. Assign permission set to admin user.](#assign_set_pro)
- [4. Create a connected app.](#create_app_pro)
- [5. Create libraries for quarantine policy actions. (DLP and Malware only)](#quarantine_pro)
- [6. Finish setup settings.](#setup_pro)
- [7. Generate Private Key file.](#private_pro)
- [8. Copy Client ID and Client Secret.](#client_pro)
- [9. Authorize the custom connector.](#authorize_pro)
When creating custom connectors, provide the following application-specific API permissions to ensure that the Zscaler service has the access it needs.
- [][API Permissions for Salesforce](#api_permissions)
- []Log in to Salesforce.
- In the left-side navigation, under **Administration**, click the **Users** drop-down menu and select **Users**.
-
Click **New User**.
[See image.](#sf_new_user_sand)
The **New User** page appears.
-
On the **New User** page, enter all the required fields (marked with a red line next to them), selecting **Salesforce** for the **User License**, and **System Administrator** for the **Profile**.
- Under **General Information**, deselect the following checkboxes:
- **Quick Access Menu**
- **Salesforce CRM Content User**
- **Receive Salesforce CRM Content Email Alerts**
- **Receive Salesforce CRM Content Alerts as Daily Digest**
- Under **Approver Settings**, keep the **Generate new password and notify user immediately** checkbox selected.
[See image.](#sf_userinfo_sand)
- Click **Save**. The email address you entered for the user receives an email to generate a password. Follow the instructions and save the password for future purposes.
- [][]In the left-side navigation, under **Administration**, click the **Users** drop-down menu and select **Permission Sets**.
-
Click **New**.
[See image.](#sf_permission_sand)
The **Permission Set Create** page appears.
-
On the **Permission Set Create** page:
- **Label**: Enter a name (e.g., Zscaler SaaS Integration Permission Set).
- **API Name**: Enter a name (e.g., Zscaler SaaS Integration Permission Set API).
- **License**: Select **Salesforce**.
[See image.](#sf_permissionset_info_sand)
- Click **Save**.
-
Select either **System Permissions** or **App Permissions** depending on the required permissions found in the [API Permissions](#api_tables) section.
[See image.](#sf_permissions_apps_sand)
-
Click **Edit** to enable the ability to select the appropriate permissions, and click **Save** when done.
[See image.](#sf_edit_perm_sand)
- []In the left-side navigation, under **Administration**, click the **Users** drop-down menu and select **Users**.
- Select the admin user you created in the previous section.
-
Under **Permission Set Assignments**, click **Edit Assignments.**
[See image.](#sf_permissionset_adduser_sand)
The **Permission Set Assignments** page appears.
-
On the **Permission Set Assignments** page:
- **Available Permission Sets**: Select the permission set you created previously.
- Click **Add**. The permission set appears in the **Enable Permission Sets** section.
- Click **Save**.
[See image.](#sf_perm_add_sand)
- []In the left-side navigation, under the **Apps **drop-down menu, click the **App Manager**.
-
Select **New Connected App**.
[See image.](#sf_connected_app_sand)
The **Create a Connected App** window appears.
-
In the **Create a Connected App** window, select **Create a Connected App** and click **Continue**.
The **App Manager** page appears.
-
On the **App Manager** page, complete the following fields:
- Enter a **Connected App Name**.
- Enter an** API Name**.
- Enter a **Contact Email**.
- Select the **Enable OAuth Settings** checkbox.
- Enter the following for **Callback URL**: `https://test.salesforce.com`.
- Select **Use Digital Signatures**.
- Select **Choose File** and upload the file that contains your digital certificate (e.g., `salesforce.crt`).
- Select the following **OAuth Scopes**:
- **Perform Requests at any time** (refresh_token, offline_access)
- **Manage user data via APIs** (api)
[See image.](#sf_connected_info_sand)
- Click **Save** and click **Continue.**
-
Return to the **App Manager** page, go to the app you created, and select the **Manage** option.
[See image.](#sf_app_manage_sand)
The app management page appears.
-
On the app management page, complete the following sections:
- Under **OAuth Policies**:
- **Permitted Users**: Select **Admin approved users are pre-authorized**.
- **IP Relaxation**: Select **Relax IP restrictions**.
- **Refresh Token Policy**: Select **Refresh token is valid until revoked**.
- Under **Session Policies, **select** 24 hours **for the** Timeout Value**.
[See image.](#sf_oauth_policies_sand)
- Click **Save** and return to the **Manage Connected Apps** page.
- On the **Manage Connected Apps** page for your connected app, under **Profiles**, click **Manage Profiles** to go to the **Application Profile Assignment** page.
-
On the **Application Profile Assignment** page, select **System Administrator** and click **Save**.
The **Manage Connected Apps **page appears.
- On the **Manage Connected Apps** page for your connected app, under **Permissions Sets**, click **Manage Permission Sets** and the **Permissions Sets** page appears.
- Select the permission set that you created previously and click **Save**.
[]If you are onboarding the tenant for DLP and Malware, you need to create two libraries for quarantine policy actions.
- In the **Libraries** tab of your Salesforce homepage, go to the **My Libraries** section and click **New**.
-
To define library information:
- **Name**: Enter `Zscaler Quarantine`.
- **Unique Name**: Enter `Malware Quarantine`.
[See image.](#sf_library_sand)
- Click **Save and Add Members**, and the **Manage Library Members** window appears.
-
In the **Manage Library Members** window, add the system admin user you created earlier, set their permission to **Library Administrator**, and click **Add**.
[See image.](#sf_lib_perm_sand)
- Repeat steps a–d but enter `Zscaler_DLP_Quarantine` for the **Name** and `DLP Quarantine` for the **Unique Name**.
- []In the left-side navigation search box, enter `Session Settings` and click **Session Settings**.
-
Uncheck the **Lock sessions to the IP address from which they originated** checkbox and click **Save**.
[See image.](#sf_sessions_setting_sand)
- In the left-side navigation search box, enter `Salesforce CRM` and select **Salesforce CRM Content**.
-
Check the **Enable Salesforce CRM Content** checkbox and click **Save**.
[See image.](#sf_crm_sand)
[]The custom onboarding process for Salesforce requires uploading your private key file to the ZIA Admin Portal. Zscaler recommends generating a certificate authority-signed (CA-signed) certificate which can be a more authoritative way to prove that your organization’s data communications are genuine. If you are unable to obtain the CA-signed certificate, a self-signed certificate can also be used. To learn more, refer to the [Salesforce documentation](https://help.salesforce.com/s/articleView?id=xcloud.security_keys_uploading_signed_cert.htm&type=5).
- []In the left-side navigation search box, enter `App` in the search box and select **App Manager**.
-
Go to the app you previously created, click the drop-down arrow, and select **View**.
[See image.](#sf_view_app_sand)
The **Manage Connected Apps** page appears.
-
On the **Manage Connected Apps** page, under **API (Enable OAuth Settings)**, click **Manage Consumer Details**.
[See image.](#sf_con_details_sand)
- After receiving an email with a verification code, enter the code and click **Verify**.
- In the next window, copy your **Consumer Key**, and the **Consumer Secret**. In the ZIA Admin Portal these are used for your **Client ID** and **Client Secret**.
- []In the ZIA Admin Portal, go to **Administration** > **SaaS Application Tenants**.
-
Click **Add SaaS Application Tenant**.
[See image.](#sf_addtenant_sand)
- Under **Choose the SaaS Application Provider**, select **Salesforce**.
-
In the **Tenant Name** field, provide a name.
[See image.](#sf_addtenant_name_sand)
-
Under **Onboard SaaS Application for**, select the checkbox for the functionality you want to enable.
[See image.](#sf_addtenant_onboard_sand)
-
Select **Sandbox Account** for the **Tenant Type**.
[See image.](#sf_addtenant_type_sand)
-
Under **Authorize the SaaS Application**:
- **SaaS Connector**: Select **Custom**.
- Enter the previously gathered information in these fields:
- **Client ID**
- **Client Secret**
- **Username of Integration User**
- **Instance URL**
- **Malware Quarantine Library Name **(DLP and Malware onboarding only)
- **DLP Quarantine Library Name **(DLP and Malware onboarding only)
[See image.](#sf_sand_auth)
- Click **Authorize**.
-
(Optional) Under **(Optional) Configure External Trusted Domains & User Profiles**:
- **External Trusted Domains**: Enter trusted email domains that are outside your organization (i.e., using a different domain). The Zscaler service views any email addresses from the added domains as trusted. For example, if your organization's domain is safemarch.com and your organization recently acquired a company with the domain example.com, you can add example.com to this list, and the service treats any email addresses from example.com (e.g., johnsmith@example.com) as internal users from safemarch.com. You can add up to 1,000 domains.
- **External Trusted Users**: Enter trusted email addresses that are outside your organization (i.e., using a different email domain). The Zscaler service views the email addresses as trusted. For example, if your organization's email domain is safemarch.com and your organization recently contracted with someone using an external email domain (e.g., johnsmith@example.com), you can add the contractor's email to this list, and the service treats the contractor as an internal user from safemarch.com. You can add up to 1,000 email addresses.
[See image.](#sf_addtenant_domain_sand)
- In the ZIA Admin Portal, click **Save** and activate the change.
[]![Users page with New User button highlighted.](/downloads/zia/policies/saas-security-api/saas-application-tenants/salesforce-custom/sf_new_user02.png)
[]![Permissions Sets page with New button highlighted.](/downloads/zia/policies/saas-security-api/saas-application-tenants/salesforce-custom/sf_permissionset_new.png)
[]![System Permissions page with the Edit button highlighted.](/downloads/zia/policies/saas-security-api/saas-application-tenants/salesforce-custom/sf_system_permissions.png)
[]![Available permission sets with the Add button highlighted.](/downloads/zia/policies/saas-security-api/saas-application-tenants/salesforce-custom/sf_permissions_add_02.png)
[]![App Manager page with New Connected App button highlighted.](/downloads/zia/policies/saas-security-api/saas-application-tenants/salesforce-custom/sf_connected_app.png)
[]![App Manager page with Manage setting highlighted.](/downloads/zia/policies/saas-security-api/saas-application-tenants/salesforce-custom/sf_app_manage.png)
[]![New Library Wizard.](/downloads/zia/policies/saas-security-api/saas-application-tenants/salesforce-custom/sf_library.png)
[]![App Manager page with View setting highlighted.](/downloads/zia/policies/saas-security-api/saas-application-tenants/salesforce-custom/sf_app_view.png)
[]![ZIA Admin Portal Authorization step](/downloads/zia/policies/saas-security-api/saas-application-tenants/salesforce-custom/sf_addtenant_authorize.png)
[]![Enter required fields (annotated with red) in the General Information section](/downloads/zia/policies/saas-security-api/saas-application-tenants/salesforce-custom/sf_user_info_02.png)
![Approver Settings section with Generate new password checkbox highlighted](/downloads/zia/policies/saas-security-api/saas-application-tenants/salesforce-custom/sf_generate_pass.png)
[]![Enter permission set information section with Label and API Name fields highlighted](/downloads/zia/policies/saas-security-api/saas-application-tenants/salesforce-custom/sf_permissionset_info.png)
[]![Permission Sets page with Apps section showing different permission selections.](/downloads/zia/policies/saas-security-api/saas-application-tenants/salesforce-custom/sf_permissions_apps.png)
[]![Users setup page with Edit Assignments highlighted in the Permission Set Assignments section](/downloads/zia/policies/saas-security-api/saas-application-tenants/salesforce-custom/sf_permissionset_adduser.png)
[]![App Manager page with required Basic Information fields highlighted and Enable OAuth Settings checkbox](/downloads/zia/policies/saas-security-api/saas-application-tenants/salesforce-custom/sf_connected_app_info.png)
![App Manager API (enable OAuth Settings) page with Callback URL and Selected OAuth Scopes sections highlighted](/downloads/zia/policies/saas-security-api/saas-application-tenants/salesforce-custom/sf_appmanager_api_annot02.png)
[]![OAuth Policies sections with required fields highlighted](/downloads/zia/policies/saas-security-api/saas-application-tenants/salesforce-custom/sf_connected_app_oauth_policies24.png)
[]![Manage Library Members window with Library Administrator access selected](/downloads/zia/policies/saas-security-api/saas-application-tenants/salesforce-custom/sf_library_permission.png)
[]![Session Settings page with Lock sessions checkbox highlighted to uncheck](/downloads/zia/policies/saas-security-api/saas-application-tenants/salesforce-custom/sf_session_settings.png)
[]![Salesforce CRM Content page with Enable Salesforce CRM Content checkbox selected.](/downloads/zia/policies/saas-security-api/saas-application-tenants/salesforce-custom/sf_crm_content.png)
[]![Manage Connected Apps page with Manage Consumer Details highlighted](/downloads/zia/policies/saas-security-api/saas-application-tenants/salesforce-custom/sf_consumer_details.png)
[]![SaaS Application Tenants page with Add SaaS Application Tenant highlighted](/downloads/zia/policies/saas-security-api/saas-application-tenants/salesforce-custom/sf_addtenant.png)
[]![Add SaaS Application Tenant page with name, onboarding, and tenant type](/downloads/zia/policies/saas-security-api/saas-application-tenants/salesforce-custom/sf_addtenant_name02.png)
[]![Onboard SaaS Application functionality: choose App Governance, DLP and Malware scanning SaaS API, or SSPM Scan](/downloads/zia/policies/saas-security-api/saas-application-tenants/salesforce-custom/sf_addtenant_onboard.png)
[]![Select Tenant Type: choose either Sandbox Account or Production Account](/downloads/zia/policies/saas-security-api/saas-application-tenants/salesforce-custom/sf_addtenant_type.png)
[]![Optional Configure External Trusted Domain Profiles & User Profiles step](/downloads/zia/policies/saas-security-api/saas-application-tenants/salesforce-custom/sf_addtenant_domain.png)
- []Log in to Salesforce.
- In the left-side navigation, under **Administration**, click the **Users** drop-down menu and select **Users**.
-
Click **New User**.
[See image.](#sf_new_user_pro)
The **New User** page appears.
-
On the **New User** page, enter all the required fields (marked with a red line next to them), selecting **Salesforce** for the **User License**, and **System Administrator** for the **Profile**.
- Under **General Information**, deselect the following checkboxes:
- **Quick Access Menu**
- **Salesforce CRM Content User**
- **Receive Salesforce CRM Content Email Alerts**
- **Receive Salesforce CRM Content Alerts as Daily Digest**
- Under **Approver Settings**, keep the **Generate new password and notify user immediately** checkbox selected.
[See image.](#sf_userinfo_pro)
- Click **Save**. The email address you entered for the user receives an email to generate a password. Follow the instructions and save the password for future purposes.
- [][]In the left-side navigation, under **Administration**, click the **Users** drop-down menu and select **Permission Sets**.
-
Click **New**.
[See image.](#sf_permission_pro)
The **Permission Set Create** page appears.
-
On the **Permission Set Create** page:
- **Label**: Enter a name (e.g., Zscaler SaaS Integration Permission Set).
- **API Name**: Enter a name (e.g., Zscaler SaaS Integration Permission Set API).
- **License**: Select **Salesforce API Integration**.
[See image.](#sf_permissionset_info_pro)
- Click **Save**.
-
Select either **System Permissions** or **App Permissions** depending on the required permissions found in the [API Permissions](#api_tables) section.
[See image.](#sf_permissions_apps_pro)
-
Click **Edit** to enable the ability to select the appropriate permissions, and click **Save** when done.
[See image.](#sf_edit_perm_pro)
- []In the left-side navigation, under **Administration**, click the **Users** drop-down menu and select **Users**.
- Select the Salesforce integration user you created in the previous section.
-
Under **Permission Set Assignments**, click **Edit Assignments**.
[See image.](#sf_permissionset_adduser_pro)
The **Permission Set Assignments** page appears.
-
On the **Permission Set Assignments** page:
- **Available Permission Sets**: Select the permission set you created previously.
- Click **Add**. The permission set appears in the **Enable Permission Sets** section.
- Click **Save**.
[See image.](#sf_perm_add_pro)
- []In the left-side navigation, under the **Apps **drop-down menu, click the **App Manager**.
-
Select **New Connected App.**
[See image.](#sf_connected_app_pro)
The **Create a Connected App** window appears.
-
In the **Create a Connected App** window, select **Create a Connected App** and click **Continue**.
The **App Manager** page appears.
-
On the **App Manager** page, complete the following fields:
- Enter a **Connected App Name**.
- Enter an** API Name**.
- Enter a **Contact Email**.
- Select the **Enable OAuth Settings** checkbox.
- Enter the following for **Callback URL**: `https://login.salesforce.com/oauth2/callback`.
- Select **Use Digital Signatures**.
- Select **Choose File** and upload the file that contains your digital certificate (e.g., `salesforce.crt`).
- Select the following **OAuth Scopes**:
- **Perform Requests at any time** (refresh_token, offline_access)
- **Manage user data via APIs** (api)
[See image.](#sf_connected_info_pro)
- Click **Save** and click **Continue.**
-
Return to the **App Manager** page, go to the app you created, and select the **Manage** option.
[See image.](#sf_app_manage_pro)
The app management page appears.
-
On the app management page, complete the following sections:
- Under **OAuth Policies**:
- **Permitted Users**: Select **Admin approved users are pre-authorized**.
- **IP Relaxation**: Select **Relax IP restrictions**.
- **Refresh Token Policy**: Select **Refresh token is valid until revoked**.
- Under **Session Policies**, select **24 hours** for the** Timeout Value**.
[See image.](#sf_oauth_policies_pro)
- Click **Save** and return to the **Manage Connected Apps** page.
- On the **Manage Connected Apps** page for your connected app, under **Profiles**, click **Manage Profiles** to go to the **Application Profile Assignment** page.
- On the **Application Profile Assignment** page, select the **Minimum Access - API Only Integrations** and click **Save**.
[]If you are onboarding the tenant for DLP and Malware, you need to create two libraries for quarantine policy actions.
- In the **Libraries** tab of your Salesforce homepage, go to the **My Libraries** section and click **New**.
-
To define library information:
- **Name**: Enter `Zscaler Quarantine`.
- **Unique Name**: Enter `Malware Quarantine`.
[See image.](#sf_library_pro)
- Click **Save and Add Members**, and the **Manage Library Members** window appears.
-
In the **Manage Library Members** window, add the integration user you created earlier, set their permission to **Library Administrator**, and click **Add**.
[See image.](#sf_lib_perm_pro)
- Repeat steps a–d, but enter `Zscaler_DLP_Quarantine` for the **Name** and `DLP Quarantine` for the **Unique Name**.
- []In the left-side navigation search box, enter `Session Settings` and click on **Session Settings**.
-
Uncheck the **Lock sessions to the IP address from which they originated** checkbox and click **Save**.
[See image.](#sf_sessions_setting_pro)
[]The custom onboarding process for Salesforce requires uploading your private key file to the ZIA Admin Portal. Zscaler recommends generating a certificate authority-signed (CA-signed) certificate which can be a more authoritative way to prove that your organization’s data communications are genuine. If you are unable to obtain the CA-signed certificate, a self-signed certificate can also be used. To learn more, refer to the [Salesforce documentation](https://help.salesforce.com/s/articleView?id=xcloud.security_keys_uploading_signed_cert.htm&type=5).
- []In the left-side navigation search box, enter `App` in the search box and select **App Manager**.
-
Go to the app you previously created, click the drop-down arrow, and select **View**.
[See image.](#sf_view_app_pro)
The **Manage Connected Apps** page appears.
-
On the **Manage Connected Apps** page, under **API (Enable OAuth Settings)**, click **Manage Consumer Details**.
[See image.](#sf_con_details_pro)
- After receiving an email with a verification code, enter the code and click **Verify**.
- In the next window, copy your **Consumer Key**, and the **Consumer Secret**. In the ZIA Admin Portal these are used for your **Client ID** and **Client Secret**.
- []In the ZIA Admin Portal, go to **Administration** > **SaaS Application Tenants**.
-
Click **Add SaaS Application Tenant**.
[See image.](#sf_addtenant_pro)
- Under **Choose the SaaS Application Provider**, select **Salesforce**.
-
In the **Tenant Name** field, provide a name.
[See image.](#sf_addtenant_name_pro)
-
Under **Onboard SaaS Application for**, select the checkbox for the functionality you want to enable.
[See image.](#sf_addtenant_onboard_pro)
-
Select **Sandbox Account** for the **Tenant Type**.
[See image.](#sf_addtenant_type_pro)
-
Under **Authorize the SaaS Application**:
- **SaaS Connector**: Select **Custom**.
- Enter the previously gathered information in these fields:
- **Client ID**
- **Client Secret**
- **Username of Integration User**
- **Instance URL**
- **Malware Quarantine Library Name **(DLP and Malware onboarding only)
- **DLP Quarantine Library Name **(DLP and Malware onboarding only)
[See image.](#sf_pro_auth)
- Click **Authorize**.
-
(Optional) Under **(Optional) Configure External Trusted Domains & User Profiles**:
- **External Trusted Domains**: Enter trusted email domains that are outside your organization (i.e., using a different domain). The Zscaler service views any email addresses from the added domains as trusted. For example, if your organization's domain is safemarch.com and your organization recently acquired a company with the domain example.com, you can add example.com to this list, and the service treats any email addresses from example.com (e.g., johnsmith@example.com) as internal users from safemarch.com. You can add up to 1,000 domains.
- **External Trusted Users**: Enter trusted email addresses that are outside your organization (i.e., using a different email domain). The Zscaler service views the email addresses as trusted. For example, if your organization's email domain is safemarch.com and your organization recently contracted with someone using an external email domain (e.g., johnsmith@example.com), you can add the contractor's email to this list, and the service treats the contractor as an internal user from safemarch.com. You can add up to 1,000 email addresses.
[See image.](#sf_addtenant_domain_pro)
- In the ZIA Admin Portal, click **Save** and activate the change.
[]![Users page with New User button highlighted.](/downloads/zia/policies/saas-security-api/saas-application-tenants/salesforce-custom/sf_new_user02.png)
[]![Permissions Sets page with New button highlighted.](/downloads/zia/policies/saas-security-api/saas-application-tenants/salesforce-custom/sf_permissionset_new.png)
[]![System Permissions page with the Edit button highlighted.](/downloads/zia/policies/saas-security-api/saas-application-tenants/salesforce-custom/sf_system_permissions.png)
[]![Available permission sets with the Add button highlighted.](/downloads/zia/policies/saas-security-api/saas-application-tenants/salesforce-custom/sf_permissions_add_02.png)
[]![App Manager page with New Connected App button highlighted.](/downloads/zia/policies/saas-security-api/saas-application-tenants/salesforce-custom/sf_connected_app.png)
[]![App Manager page with Manage setting highlighted.](/downloads/zia/policies/saas-security-api/saas-application-tenants/salesforce-custom/sf_app_manage.png)
[]![New Library Wizard.](/downloads/zia/policies/saas-security-api/saas-application-tenants/salesforce-custom/sf_library.png)
[]![App Manager page with View setting highlighted.](/downloads/zia/policies/saas-security-api/saas-application-tenants/salesforce-custom/sf_app_view.png)
[][]
In the following API tables, you need to select between the Sandbox and Production Tenants and select the appropriate permissions.
- [Sandbox Permissions Table](#sandbox_api)
- [Production Permission Table](#production_api)
[]Instructions for adding permissions can be found in the [Create permission set](#permission_table_pro) section for Production tenants.
| Salesforce Production Permission Type | Zscaler Onboarding | Salesforce Permissions | Associated Zscaler Actions |
| ------------------------------------- | ------------------ | ---------------------- | -------------------------- |
| App Permissions | DLP and Malware | Manage Salesforce CRM Content | Scanning |
| Query All Files | Scanning |
| SSPM | Query All Files | SSPM Scan |
| System Permissions | DLP and Malware | Access Libraries | Scanning |
| View Event Log Files | Generate SaaS Activities |
| View All Users | Scanning |
| Modify All Data | Scanning |
| Manage Chatter Messages and Direct Messages | Scanning |
| Manage Unlisted Groups | Scanning |
| SSPM | View Health Check | SSPM Scan |
| Modify All Data | SSPM Scan |
| Modify Metadata Through Metadata API Functions | SSPM Scan |
| Manage Certificates | SSPM Scan |
| Manage Sharing | SSPM Scan |
| Field Permissions | DLP and Malware | Read Access for Description, Subject, and Type Fields | Scanning |
[]Instructions for adding permissions can be found in the [Create permission set](#permission_table_sand) section for Sandbox tenants.
| Salesforce Sandbox Permission Type | Zscaler Onboarding | Salesforce Permissions | Associated Zscaler Actions |
| ---------------------------------- | ------------------ | ---------------------- | -------------------------- |
| App Permissions | DLP and Malware | Manage Salesforce CRM Content | Scanning |
| Query All Files | Scanning |
| SSPM | Query All Files | SSPM Scan |
| System Permissions | DLP and Malware | Access Libraries | Scanning |
| View Event Log Files | Scanning |
| View All Users | Scanning |
| Modify All Data | Apply Policy Actions |
| Manage Chatter Messages and Direct Messages | Scanning |
| Manage Unlisted Groups | Scanning |
| SSPM | View Health Check | SSPM Scan |
| Modify All Data | SSPM Scan |
| Modify Metadata Through Metadata API Functions | SSPM Scan |
| Manage Certificates | SSPM Scan |
| Manage Sharing | SSPM Scan |
[]![ZIA Admin Portal Authorization step](/downloads/zia/policies/saas-security-api/saas-application-tenants/salesforce-custom/sf_addtenant_authorize.png)
[]![Enter required fields (annotated with red) in the General Information section](/downloads/zia/policies/saas-security-api/saas-application-tenants/salesforce-custom/sf_user_info_02.png)
![Approver Settings section with Generate new password checkbox highlighted](/downloads/zia/policies/saas-security-api/saas-application-tenants/salesforce-custom/sf_generate_pass.png)
[]![Enter permission set information section with Label and API Name fields highlighted](/downloads/zia/policies/saas-security-api/saas-application-tenants/salesforce-custom/sf_permissionset_info_api.png)
[]![Permission Sets page with Apps section showing different permission selections.](/downloads/zia/policies/saas-security-api/saas-application-tenants/salesforce-custom/sf_permissions_apps.png)
[]![Users setup page with Edit Assignments highlighted in the Permission Set Assignments section](/downloads/zia/policies/saas-security-api/saas-application-tenants/salesforce-custom/sf_permissionset_adduser.png)
[]![App Manager page with required Basic Information fields highlighted and Enable OAuth Settings checkbox](/downloads/zia/policies/saas-security-api/saas-application-tenants/salesforce-custom/sf_connected_app_info.png)
![App Manager API (enable OAuth Settings) page with Callback URL and Selected OAuth Scopes sections highlighted](/downloads/zia/policies/saas-security-api/saas-application-tenants/salesforce-custom/sf_appmanager_api_annot02.png)
[]![OAuth Policies sections with required fields highlighted](/downloads/zia/policies/saas-security-api/saas-application-tenants/salesforce-custom/sf_connected_app_oauth_policies24.png)
[]![Manage Library Members window with Library Administrator access selected](/downloads/zia/policies/saas-security-api/saas-application-tenants/salesforce-custom/sf_library_permission.png)
[]![Session Settings page with Lock sessions checkbox highlighted to uncheck](/downloads/zia/policies/saas-security-api/saas-application-tenants/salesforce-custom/sf_session_settings.png)
[]![SaaS Application Tenants page with Add SaaS Application Tenant highlighted](/downloads/zia/policies/saas-security-api/saas-application-tenants/salesforce-custom/sf_addtenant.png)
[]![Add SaaS Application Tenant page with name, onboarding, and tenant type](/downloads/zia/policies/saas-security-api/saas-application-tenants/salesforce-custom/sf_addtenant_name02.png)
[]![Onboard SaaS Application functionality: choose App Governance, DLP and Malware scanning SaaS API, or SSPM Scan](/downloads/zia/policies/saas-security-api/saas-application-tenants/salesforce-custom/sf_addtenant_onboard.png)
[]![Select Tenant Type: choose either Sandbox Account or Production Account](/downloads/zia/policies/saas-security-api/saas-application-tenants/salesforce-custom/sf_addtenant_type.png)
[]![Optional Configure External Trusted Domain Profiles & User Profiles step](/downloads/zia/policies/saas-security-api/saas-application-tenants/salesforce-custom/sf_addtenant_domain.png)
[]![Manage Connected Apps page with Manage Consumer Details highlighted](/downloads/zia/policies/saas-security-api/saas-application-tenants/salesforce-custom/sf_consumer_details.png)