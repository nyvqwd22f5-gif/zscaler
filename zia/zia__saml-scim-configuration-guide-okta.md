# SAML & SCIM Configuration Guide for Okta
Source: https://help.zscaler.com/zia/saml-scim-configuration-guide-okta
PDF: https://help.zscaler.com/pdf/com/en/1399671.pdf

This guide illustrates how to configure and install the Zscaler Internet Access (ZIA) app in Okta, which enables the user to use SAML as the method of authentication and System for Cross-domain Identity Management (SCIM) as the method of provisioning.
Zscaler and Okta are technology partners. To learn more about the Zscaler and Okta integration, see the [Zscaler and Okta Deployment Guide](/zscaler-technology-partners/zscaler-and-okta-deployment-guide).
Supported Features
The SAML features supported by the Zscaler and Okta integration are:
- [SP-initiated SSO](#sp-initiated-sso)
- Just-in-Time (JIT) Provisioning (SAML auto-provisioning)
The SCIM features supported by the Zscaler and Okta integration are:
- Create Users
- Update User Attributes
- Deactivate Users
- Group Push
Prerequisites
Ensure that you have the following before you start configuring Okta:
- An Okta account with admin privileges.
- A SCIM provisioning subscription for Okta. Contact your Okta representative to ensure your organization has the appropriate subscription.
Configuring Okta as the IdP for the Zscaler Service
To configure an Okta SAML and SCIM integration with Zscaler:
- [1. Integrate Active Directory with Okta.](#ad)
- [2. Add the Zscaler Internet Access app in Okta.](#inst-okta)
- [3. Configure SAML in the ZIA Admin Portal.](#conf-zscaler)
- [4. Configure SCIM In the ZIA Admin Portal.](#conf-scim)
- [5. Configure SCIM in Okta.](#conf-okta)
- [6. Assign people or groups in Okta.](#asg-group)
- [7. Provision people or groups in Okta.](#prov-group)
- [8. Configure the Zscaler Authentication Exemptions list.](#authentication-exemptions-list)
Testing the SAML and SCIM Configuration
[]When your configuration is complete, you can test your work on another device.
Test the configuration with one or both of the following methods:
- [Test the SAML Configuration by Logging Out of the Zscaler Service](#test-saml-1)
- [Test the SAML Configuration with the Test URL](#test-saml-2)
To test the SCIM configuration, in the ZIA Admin Portal, go to **Administration** >** User Management**. You should see a complete list of the users and groups added to your user database.
Troubleshooting
If any errors occur, see [Troubleshooting SAML](/zia/saml-troubleshooting-guidelines) to troubleshoot browser settings and SAML error codes.
[]This testing method only applies if you're forwarding traffic using Proxy Auto-Configuration (PAC) files, Generic Routing Encapsulation (GRE) tunnels, or IPSec tunnels, and you've enabled Enforce Authentication for the location or sublocation.
- On the device, browse to [ip.zscaler.com](http://ip.zscaler.com).
- If you are already logged in to the Zscaler service, click **Logout**. Otherwise, ensure that your traffic is being forwarded to the Zscaler service.
- Browse to a website. You are redirected to Okta and prompted to log in.
- Log in using your Okta credentials, and you are automatically redirected to the original URL request.
- Go to [ip.zscaler.com](http://ip.zscaler.com). The status window shows the username indicating that authentication was successful.
-
[]On the device, enter `https://login.``<Zscaler Cloud Name>``/clstart?version=1&_domain=``<Tenant Domain>``&redrurl=https://mobile.``<Zscaler Cloud Name>`. To learn how you can find your cloud name, see [What Is My Cloud Name for ZIA?](/zia/what-my-cloud-name-zia) The <Tenant Domain> is your organization's domain that is used to log in to the Zscaler service. For example, if you logged in to the Zscaler service with the username `admin@``zscaler.com`, then zscaler.com is your <Tenant Domain>.
Given an organization on the `zscalerbeta.net` cloud with `zscaler.com` as the <Tenant Domain>, the completed URL would be:
``https://login.``zscalerbeta.net``/clstart?version=1&_domain=``zscaler.com``&redrurl=https://mobile.``zscalerbeta.net``
- If you are redirected to the ZIA Admin Portal, the SAML configuration is successful. You might be prompted to authenticate with your IdP.
[]Okta allows you to integrate with your existing Active Directory using the Okta AD Agent. To learn more, refer to the [Okta documentation](https://help.okta.com/en/prod/Content/Topics/Directory/ad-agent-new-integration.htm).
[]To add the Zscaler Internet Access app in the Okta administrator portal:
- Log in to Okta.
-
Click the **Admin **button at the top of the page to enter the administrator view.
The Dashboard is displayed.
[See image.](#okta-admin-button)
-
On the Dashboard, click the **Menu **icon.
[See image.](#okta-menu-button)
-
Go to **Applications > Applications.**
[See image.](#okta-navigation-apps)
-
On the **Applications** page, click **Browse App Catalog.**
[See image.](#okta-browse-app-catalog-button)
- On the** Browse App Integration Catalog **page,** **enter** **`**Zscaler** Internet Access`** **in the** Search **field.
-
Select **Zscaler Internet Access **in the list of results.
[See image.](#okta-browse-app-integration-catalog-page)
-
On the **Zscaler Internet Access Application** page, click** Add Integration. **This adds the application.
[See image.](#okta-add-integration-button)
-
In the **General Settings**, define the following fields:
- **Application Label**: Specify the display name for the service.
-
**Your Zscaler Domain**: Enter your cloud name (e.g., zscalerbeta.net). To learn how to find your domain, see [What Is My Cloud Name for ZIA?](/zia/what-my-cloud-name)
Make sure to enter the correct value. Using the wrong value prevents you from authenticating via SAML to Zscaler.
- **Application Visibility**: Configure as desired.
- **Browser plugin auto-submit**: Configure as desired.
[See image.](#Okta-general-settings)
- Click **Next.**
- In the **Sign on methods** section, select **SAML 2.0**.
-
Use the drop-down menu in the **memberOf **field to select a condition type and then enter an expression that specifies the groups you would like to send in your SAML assertion. Zscaler recommends to set the condition to a regular expression (**Regex**) with the expression being `.*`. This means that all groups the user belongs to are sent in the SAML assertion.
[See image.](#memberof)
-
In the **Metadata details **section, click **More details**. Copy the **Sign on URL **and download the **Signing Certificate**. You need them when configuring Okta as the identity provider (IdP) in the ZIA Admin Portal.
[See image.](#saml-details)
-
Ensure the certificate file name:
- Has a **.pem** extension (e.g., rename it to Okta.pem). The Zscaler service only accepts certificates with the .pem extension.
- Contains only one dot (".").
[See image.](#saml-certificate-pem)
By default, Windows hides extensions for known file types.
- [Change the Windows Folder Properties to View and Edit Extensions](#samlver-pem-instructions)
- Click **Done.**
[]To configure SAML in the ZIA Admin Portal:
- Go to **Administration** > **Authentication Settings**.
- Click the **Identity Providers **tab.
- Click **Add IdP**.
If you have an existing IdP configuration, the **What do you want to do?** window appears. Click **Add another SAML IdP for a subset of users or locations** and then **Next**.
[See image.](#what-to-do)
-
In the **Add IdP **window:
- **SAML Portal URL**: Enter the **Sign on URL **that you copied from Okta in step 2.m.
- **Login Name Attribute**: Enter `NameID` (case sensitive).
- **IdP SAML Certificate**: Upload the .pem certificate that you downloaded from Okta.
-
**Org-Specific Entity ID**: Enable if you have more than one organization instance on the same Zscaler cloud. For example, if you have two organization instances on the same Zscaler cloud and must authenticate both instances against the same Okta account, you can't use the same entity ID for multiple apps in Okta. For this situation, you must enable this setting for both instances to generate a unique organization-specific entity ID.
The **Org-Specific Entity ID **is formatted like the following example:
`https://login.zscalerbeta.net/sfc_sso/3829920`
- **Locations**: Select the [locations](/zia/about-locations) to map to this IdP. You can also search for a location. Any unselected locations are mapped to the default IdP. This field is set to **Any** for the default IdP, and you can't modify it.
- **Authentication Domains**: Select the domains to map to this IdP. This allows the Zscaler service to display the correct IdP to authenticate an incoming user. Any unselected domains are mapped to the default IdP. This field is set to **Any** for the default IdP, and you can't modify it. Apart from the default IdP, any additional IdPs must be mapped to at least one domain.
[See image.](#idp-config)
Ensure the **Sign SAML Request** option is disabled in the ZIA Admin Portal. Okta doesn't support signed SAML responses from the service provider.
-
(Optional) If you want to configure SAML without SCIM, in the **Provisioning Options **section:
- **Enable SAML Auto-Provisioning**: Enable this option.
- **User Display Name Attribute**: Enter `DisplayName` (case sensitive).
- **Group Name Attribute**: Enter `memberOf` (case sensitive).
- **Department Name Attribute**: Enter `Department` (case sensitive).
[See image.](#saml-auto-provisioning)
Zscaler recommends using SCIM to provision users. Skip this step if you are using SCIM provisioning.
- Click **Save**.
-
Go to the **Default Settings **tab and select **SAML **as the **Authentication Type**.
[See image.](#zia-enable-saml)
- Click **Save** and [activate the changes](/zia/saving-and-activating-changes-zia-admin-portal).
To learn more about configuring an IdP in the ZIA Admin Portal, see [Adding Identity Providers](/zia/adding-identity-providers).
[]To configure SCIM in the ZIA Admin Portal:
- Go to **Administration **>** Authentication Settings**.
- Click the **Identity Providers** tab.
-
Click the **Edit** icon for the IdP you configured for Okta (step 3).
The **Edit IdP** window appears.
-
In the **Edit IdP** window:
- **Enable SAML Auto-Provisioning**: Disable this option when enabling SCIM-based provisioning.
- **Enable SCIM Provisioning**: Enable to activate SCIM-based provisioning for users on the Zscaler service. To learn more, see [About SCIM](/zia/about-scim). SCIM provisioning isn't supported with Active Directory or OpenLDAP user repositories. If you want to migrate from directory synchronization to SCIM provisioning, enable **Disable Directory Sync & Enable SCIM Provisioning** on the [Authentication Profile page](/zia/about-authentication-profile). After enabling SCIM provisioning, the following fields appear:
-
**Base URL**: Copy the Base URL for the SCIM server. You need this URL when configuring your IdP for SCIM provisioning. Okta only accepts strings with the following format. In this example it is `37146169/1605333`.
``<Organization ID>``/``<IdP ID>``
The old SCIM Base URL marked as **(Deprecated)** will be removed in the future.
- **Bearer Token**: Copy the bearer token. It's a unique alphanumeric string that is used by the SCIM client to make authenticated API calls to the Zscaler SCIM server. You need this token when configuring your IdP for SCIM provisioning.
- **Generate Token**: Click to generate a new bearer token for security reasons. If you're generating a new bearer token for an existing SCIM configuration, ensure you update the token for your IdP.
[See image.](#enable-scim)
- Click **Save** to exit the window.
- Click **Save **and [activate the change](/zia/saving-and-activating-changes-admin-portal).
To learn more about configuring SCIM in the ZIA Admin Portal, see [Configuring SCIM](/zia/configuring-scim).
[]After the app is installed, you need to configure it in the Okta administrator portal:
-
In Okta, go to the **Provisioning** tab and click **Configure API Integration**.
[See image.](#okta-configure-api-integration)
- Select **Enable API Integration**.
- Enter the following information:
-
**Zscaler ID**: Enter the Organization ID and IdP ID of the [Base URL](/zia/configuring-scim) in the following format:
`<Organization ID>/<IdP ID>`
For example, if your **Base URL** is `https://scim.zscalerbeta.net/``1234567``/``098``/scim`, enter `1234567``/``098`.
-
**API Token**: Enter the **Bearer Token** you copied in step 4.d.
[See image.](#okta-enable-api-integration-2)
- Click **Test API Credentials**. If the test fails, verify that your bearer token is correct.
- Click **Save**.
- Select **To App** in the left-side navigation.
- Select **Edit**.
-
Enable these checkboxes:
- **Create Users**: When a user is created and is assigned Zscaler Internet Access, the user is automatically provisioned on the Zscaler service with SCIM.
- **Update User Attributes**: If a user’s attributes are changed in Okta, the attributes are also updated in the Zscaler service. This is done with a SCIM API call.
- **Deactivate Users**: If a user account is deleted or deactivated in Okta or has Zscaler Internet Access unassigned, the user is also deactivated in the Zscaler service.
[See image.](#okta-enable-api-integration_3)
- Click **Save**.
-
(Optional) If you use the Workflow Automation Admin Portal, add and map additional user attributes that Workflow Automation uses.
- [i. Add additional user attributes.](#add-additional-user-attributes-WA)
- [ii. Map additional user attributes.](#map-additional-user-attributes-WA)
When you are finished, click **Save**.
[]The following table lists the additional user attributes to add for Workflow Automation:
| Data Type | Display Name | Variable Name | External Name | External Namespace | Attribute Length | Attribute Type |
| --------- | ------------ | ------------- | ------------- | ------------------ | ---------------- | -------------- |
| string | manager | manager | manager | urn:ietf:params:scim:schemas:core:2.0:User | Between 1 and 128 | Personal |
| string | title | title | title | urn:ietf:params:scim:schemas:core:2.0:User | Between 1 and 32 | Personal |
| string | streetAddress | streetAddress | streetAddress | urn:ietf:params:scim:schemas:core:2.0:User | Between 1 and 64 | Personal |
| string | city | city | city | urn:ietf:params:scim:schemas:core:2.0:User | Between 1 and 32 | Personal |
| string | state | state | state | urn:ietf:params:scim:schemas:core:2.0:User | Between 1 and 32 | Personal |
| string | zipCode | zipCode | zipCode | urn:ietf:params:scim:schemas:core:2.0:User | Between 1 and 32 | Personal |
| string | countryCode | countryCode | countryCode | urn:ietf:params:scim:schemas:core:2.0:User | Between 1 and 32 | Personal |
| string | postalAddress | postalAddress | postalAddress | urn:ietf:params:scim:schemas:core:2.0:User | Between 1 and 32 | Personal |
| string | locale | locale | locale | urn:ietf:params:scim:schemas:core:2.0:User | Between 1 and 32 | Personal |
| string | mobilePhones | mobilePhones | mobilePhones | urn:ietf:params:scim:schemas:core:2.0:User | Between 1 and 32 | Personal |
| string | preferredLanguage | preferredLanguage | preferredLanguage | urn:ietf:params:scim:schemas:core:2.0:User | Between 1 and 32 | Personal |
| string | employeeNumber | employeeNumber | employeeNumber | urn:ietf:params:scim:schemas:core:2.0:User | Between 1 and 32 | Personal |
To add additional user attributes:
-
In the **Zscaler Internet Access Attribute Mappings** section, click **Go to Profile Editor**.
[See image.](#mapping-1)
-
In the **Profile Editor**, click **Add Attribute**.
[See image.](#mapping-2)
-
In the **Add Attribute **window, enter the values for each attribute from the table provided and click **Save and Add Another **until you have added all the attributes, then click **Save**.
[See image.](#mapping-3)
[]![Go to the Profile Editor in the Okta administrator portal](/downloads/zia/authentication-administration/provisioning-authenticating-users/saml-scim/saml-scim-configuration-guide-okta/ZIA-okta-go-profile-editor.png)
[]![Add Attribute in the Profile Editor](/downloads/zia/authentication-administration/provisioning-authenticating-users/saml-scim/saml-scim-configuration-guide-okta/ZIA-okta-add-attribute.png)
[]![Add Attribute window](/downloads/zia/authentication-administration/provisioning-authenticating-users/saml-scim/saml-scim-configuration-guide-okta/ZIA-okta-add-attribute-window.png)
[]The following table lists the mapping information to use when mapping the additional user attributes you previously added:
| Okta User Profile | Zscaler Internet Access User Profile |
| ----------------- | ------------------------------------ |
| user.firstName | givenName |
| user.lastName | familyName |
| user.email | email |
| user.firstName + ' ' + user.lastname | displayName |
| user.department | department |
| user.managerId | manager |
| user.city | city |
| user.locale | locale |
| user.title | title |
| user.streetAddress | streetAddress |
| user.state | state |
| user.zipcode | zipcode |
| user.countrycode | countryCode |
| user.preferredLanguage | preferredLanguage |
| user.employeeNumber | employeeNumber |
| user.mobilePhone | mobilePhones |
To map additional user attributes:
-
In the **Zscaler Internet Access Attribute Mappings** section, click **Go to Profile Editor**.
[See image.](#mapping-4)
-
In the **Profile Editor**, click **Mappings**.
[See image.](#mapping-5)
-
On the mappings page, click **Okta User to Zscaler Internet Access**.
[See image.](#mapping-6)
-
Configure the mappings based on the table provided. Click **Save Mappings **when you are finished**.**
[See image.](#mapping-7)
[]![Go to the Profile Editor in the Okta administrator portal](/downloads/zia/authentication-administration/provisioning-authenticating-users/saml-scim/saml-scim-configuration-guide-okta/ZIA-okta-go-profile-editor.png)
[]![Add Mappings in the Profile Editor](/downloads/zia/authentication-administration/provisioning-authenticating-users/saml-scim/saml-scim-configuration-guide-okta/ZIA-okta-add-mappings.png)
[]![Select Okta User to Zscaler Internet Access](/downloads/zia/authentication-administration/provisioning-authenticating-users/saml-scim/saml-scim-configuration-guide-okta/ZIA-okta-to-zscaler.png)
[]![Okta Attribute Mappings](/downloads/zia/authentication-administration/provisioning-authenticating-users/saml-scim/saml-scim-configuration-guide-okta/ZIA-okta-mappings.png)
[]To assign people or groups to the app:
- In Okta, go to the **Assignments** tab.
- From the **Assign** drop-down menu, select** Assign to People** or** Assign to Groups**.
[See image.](#okta-assignments)
- Click **Assign** next to the people or groups you want to assign Zscaler Internet Access to. When you assign a group to Zscaler Internet Access, all users in that group are automatically assigned to the application.
[See image.](#okta-assignments_2)
- Click **Done**.
At this point, Okta takes several minutes to sync the user database with the Zscaler service. The service accepts provisioning requests at the rate of 5 requests per second. To calculate your approximate sync time in seconds, divide your total number of users by 5 and then add 4% of your total users to accommodate for network drops and errors.
For example, if you have 3,000 users:
- 3,000/5 = 600
- 0.04*3,000 = 120
- 600+120 = 720
This means the expected time for this database sync is 720 seconds or 12 minutes.
[]To provision groups:
-
In Okta, go to **Dashboard** > **Tasks **to track the progress of your provisioning. If any errors have occurred, you can see them here. If you have multiple apps, you can filter by Zscaler Internet Access to see the relevant errors.
Many errors happen because users and groups are still in the queue to be synced to the Zscaler service with SCIM provisioning. These types of errors are resolved when provisioning is complete. Before you take any further action, make sure you have calculated your approximate sync time and allowed it to sufficiently elapse.
[See image.](#okta-tasks)
-
Click the errors and a new page that lists all errors related to Zscaler Internet Access appears. To see details on the errors, click the **Expand** icon.
[See image.](#okta-tasks-2)
-
Select all errors by selecting the checkbox in the top-left corner and click **Retry Selected**.
This triggers another round of synchronization for the failed tasks. The same rate-limit applies to resynchronization of failed tasks. For example, if you have 300 failed tasks, it would take a little more than one minute to resynchronize. You might have to repeat this step multiple times if you continue to see failed tasks.
Do not move to the next step until the entire database is synced. Failure to do so might result in unrecoverable errors.
[See image.](#okta-tasks-3)
- To sync the group information with the Zscaler service, go to the **Push Groups** tab.
- Click **Push Groups** > **Find groups by name**.
[See image.](#okta-push-groups)
- Search and select the groups to sync with the Zscaler service, making sure to select **Push group memberships immediately**.
[See image.](#okta-push-groups-2)
- Click **Save** to only add a single group or **Save & Add Another** if you want to push multiple groups.
- Click **Close**.
- On the **Push Groups** page, verify that all of your groups have been added.
[See image.](#okta-push-groups-3)
[]To configure the Zscaler Authentication Exemptions list and enable users access to Okta:
- In the ZIA Admin Portal, go to **Administration **>** Advanced Settings**.
- In the **Authentication Exemptions** section, enter the required Okta domains in **Exempted URLs**. To learn more, refer to the [Okta documentation](https://help.okta.com/oie/en-us/Content/Topics/Security/ip-address-allow-listing.htm).
- Click **Save** and [activate the change](/zia/saving-and-activating-changes-admin-portal).
If you are using PAC files, enter the required Okta domains in the [PAC file](/zia/using-default-pac-files-forward-traffic-zia) exemption list. Otherwise, the authentication fails.
If (shExpMatch(host, "*.okta.com", "*.oktacdn.com"))
return "DIRECT";
This option only applies to user traffic from known locations. For more information, see [Exempting URLs and Cloud Apps from Authentication](/zia/exempting-urls-cloud-apps-authentication).
- []Start Windows 10 Control Panel.
- Go to **Appearance & Personalization** > **File Explorer Options**.
- When the **File Explorer Options** window appears, click the **View **tab.
-
In **Advanced settings**, deselect **Hide extensions for known file types** to view extensions.
[See image.](#file-explorer)
- Rename the certificate to change the extension.
[]![The What do you want to do? window](/downloads/zia/authentication-administration/provisioning-authenticating-users/saml-scim/saml-scim-configuration-guide-okta/ZIA-What-do-you-want-to-do-window.png)
[]![The administrator portal button in Okta](/downloads/zia/authentication-administration/provisioning-authenticating-users/saml-scim/saml-scim-configuration-guide-okta/ZIA-click-okta-admin-button.png)
[]![The Menu icon in Okta](/downloads/zia/authentication-administration/provisioning-authenticating-users/saml-scim/saml-scim-configuration-guide-okta/ZIA-okta-click-menu-button.png)
[]![The IdP configuration](/downloads/zia/authentication-administration/provisioning-authenticating-users/saml-scim/saml-scim-configuration-guide-okta/ZIA-add-idp-general-info.png)
[]![The SAML Auto-Provisioning settings](/downloads/zia/authentication-administration/provisioning-authenticating-users/saml-scim/saml-scim-configuration-guide-okta/ZIA-saml-auto-provisioning.png)
[]![The SAML option in the ZIA Admin Portal](/downloads/zia/authentication-administration/provisioning-authenticating-users/saml-scim/saml-scim-configuration-guide-okta/ZIA-enable-saml.png)
[]![The Okta navigation menu](/downloads/zia/authentication-administration/provisioning-authenticating-users/saml-scim/saml-scim-configuration-guide-okta/ZIA-okta-navigation-apps.png)
[]![The Enable SCIM Provisioning option](/downloads/zia/authentication-administration/provisioning-authenticating-users/saml-scim/saml-scim-configuration-guide-okta/ZIA-enable-scim.png)
[]![The memberOf field with the Regex expression](/downloads/zia/authentication-administration/provisioning-authenticating-users/saml-scim/saml-scim-configuration-guide-okta/ZIA-okta-memberof.png)
[]![The SAML details in the Okta administrator portal](/downloads/zia/authentication-administration/provisioning-authenticating-users/saml-scim/saml-scim-configuration-guide-okta/ZIA-okta-copy-saml-details.png)
[]![The Okta SAML certificate with the .pem extension](/downloads/zia/authentication-administration/provisioning-authenticating-users/saml-scim/saml-scim-configuration-guide-okta/ZIA-okta-certificate-pem.png)
[]![The Windows File Explorer Options](/downloads/zia/authentication-administration/provisioning-authenticating-users/saml-scim/saml-scim-configuration-guide-okta/Windows-File-Explorer-Options-View-Hide-extensions-for-known-file-types.png)
[]![Clicking the Browse App Catalog Button on the Application Page](/downloads/zia/authentication-administration/provisioning-authenticating-users/saml-scim/saml-scim-configuration-guide-okta/ZIA-okta-select-browse-app-catalog.png)
[]![Selecting the Zscaler Internet Access Application in the Okta Admin Portal](/downloads/zia/authentication-administration/provisioning-authenticating-users/saml-scim/saml-scim-configuration-guide-okta/ZIA-okta-search-app-catalog.png)
[]![Clicking the Add Integration Button in Okta](/downloads/zia/authentication-administration/provisioning-authenticating-users/saml-scim/saml-scim-configuration-guide-okta/ZIA-okta-select-add-integration.png)
[]![Defining General Settings for an Application on the General Settings Page in Okta](/downloads/zia/authentication-administration/provisioning-authenticating-users/saml-scim/saml-scim-configuration-guide-okta/ZIA-okta-general-settings.png)
[]![Clicking the Configure API Integration Button on the Provisioning Tab](/downloads/zia/authentication-administration/provisioning-authenticating-users/saml-scim/saml-scim-configuration-guide-okta/ZIA-okta-select-configure-integration.png)
[]![The Zscaler ID and API Token fields](/downloads/zia/authentication-administration/provisioning-authenticating-users/saml-scim/saml-scim-configuration-guide-okta/ZIA-okta-api-integration-id-token.png)
[]![The To App checkboxes enabled](/downloads/zia/authentication-administration/provisioning-authenticating-users/saml-scim/saml-scim-configuration-guide-okta/ZIA-okta-edit-provisioning-to-app.png)
[]![The Assign to People or Groups options](/downloads/zia/authentication-administration/provisioning-authenticating-users/saml-scim/saml-scim-configuration-guide-okta/ZIA-okta-assign-people-groups.png)
[]![Assigning a group using the Assign button](/downloads/zia/authentication-administration/provisioning-authenticating-users/saml-scim/saml-scim-configuration-guide-okta/ZIA-okta-assign-to-groups.png)
[]![The Okta Dashboard with errors](/downloads/zia/documentation-knowledgebase/authenticating-and-managing-users/saml/saml-scim-configuration-guide-okta/Okta_Tasks_Page.png)
[]![Error details displayed on the Tasks page](/downloads/zia/authentication-administration/provisioning-authenticating-users/saml-scim/saml-scim-configuration-guide-okta/ZIA-okta-tasks-expand.png)
[]![The Retry Selected option](/downloads/zia/authentication-administration/provisioning-authenticating-users/saml-scim/saml-scim-configuration-guide-okta/ZIA-okta-tasks-retry-selected.png)
[]![The Find groups by name option under the Push Groups tab](/downloads/zia/authentication-administration/provisioning-authenticating-users/saml-scim/saml-scim-configuration-guide-okta/ZIA-okta-select-push-groups.png)
[]![Pushing groups by name page under the Push groups tab](/downloads/zia/authentication-administration/provisioning-authenticating-users/saml-scim/saml-scim-configuration-guide-okta/ZIA-okta-push-groups-by-name.png)
[]![A successful group push status](/downloads/zia/authentication-administration/provisioning-authenticating-users/saml-scim/saml-scim-configuration-guide-okta/ZIA-okta-push-status.png)
[]To perform SP-initiated SSO:
- Open your site.
- You are redirected to `https://gateway.``<Zscaler Cloud Name>``.net` and prompted for a **User Name**.
- Enter your **User Name** and click **Sign in**.