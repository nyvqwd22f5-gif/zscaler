# SAML & SCIM Configuration Guide for PingOne
Source: https://help.zscaler.com/zia/saml-scim-configuration-guide-pingone
PDF: https://help.zscaler.com/pdf/com/en/1524896.pdf

This guide illustrates how to configure SAML and SCIM with Ping Identity's PingOne server as the identity provider (IdP) for the Zscaler service.
Supported Features
The SAML features supported by the Zscaler and PingOne integration are:
[SP-initiated SSO](#sp-initiated-sso)
- Just-in-Time (JIT) Provisioning (SAML auto-provisioning)
The following SCIM features are supported by the Zscaler and PingOne integration:
- Create Users
- Update User Attributes
- Delete Users
- Group Push
Prerequisites
Ensure that you have the following before you start configuring PingOne as your IdP:
- PingOne server with the Zscaler Connector add-on
- PingOne admin account
- [Zscaler cloud name](/zia/what-my-cloud-name)
Configuring PingOne as the IdP for the Zscaler service
To configure SAML Single Sign-On (SSO) and SCIM Provisioning with Zscaler and PingOne:
- [1. Configure the Zscaler app in the PingOne admin console.](#pingone-saml)
- [2. Add PingOne as the IdP in the ZIA Admin Portal.](#zia-saml)
- [3. Enable SAML in the ZIA Admin Portal.](#zia-enable-saml)
- [4. Enable SCIM in the ZIA Admin Portal.](#zia-scim)
- [5. Configure SCIM in the PingOne admin console.](#pingone-scim)
- [6. Configure the Zscaler Authentication Exemptions list.](#authentication_exemptions)
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
- Browse to a website. You are redirected to PingOne and prompted to log in.
- Log in using your PingOne credentials, and you are automatically redirected to the original URL request.
- Go to [ip.zscaler.com](http://ip.zscaler.com). The status window shows the username indicating that authentication was successful.
-
[]On the device, enter `https://login.``<Zscaler Cloud Name>``/clstart?version=1&_domain=``<Tenant Domain>``&redrurl=https://mobile.``<Zscaler Cloud Name>`. To learn how you can find your cloud name, see [What Is My Cloud Name for ZIA?](/zia/what-my-cloud-name-zia) The <Tenant Domain> is your organization's domain that is used to log in to the Zscaler service. For example, if you logged in to the Zscaler service with the username `admin@``zscaler.com`, then zscaler.com is your <Tenant Domain>.
Given an organization on the `zscalerbeta.net` cloud with `zscaler.com` as the <Tenant Domain>, the completed URL would be:
``https://login.``zscalerbeta.net``/clstart?version=1&_domain=``zscaler.com``&redrurl=https://mobile.``zscalerbeta.net``
- If you are redirected to the ZIA Admin Portal, the SAML configuration is successful. You might be prompted to authenticate with your IdP.
[]
- [Log in to the PingOne admin console](https://docs.pingidentity.com/r/en-us/pingone/p1_access_admin_console).
- Go to **Applications **> **Application catalog**.
-
Enter `zscaler` in the search bar and select the application that corresponds to your cloud name. In this example configuration, the cloud is **Zscaler Two**, so the **Zscaler Two** application is selected.
[See image.](#see-image-1c)
-
In the **Quick Setup **section, confirm the **Name** and **Entity ID** of the application and click **Next**.
If you have more than one organization instance on the same Zscaler cloud, you must use an org-specific entity ID. You can see the org-specific entity ID for your instance in the ZIA Admin Portal while [adding or editing an identity provider](/zia/adding-identity-providers).
The org-specific entity ID is formatted like the following example:
`https://login.zscalertwo.net/sfc_sso/3829920`
[See image.](#see-image-1d)
-
In the **Map Attributes** section, click the **Advanced Expression **icon for the **displayName **attribute.
[See image.](#see-image-1e)
-
In the **Build and Test Expression **window, enter `user.name.given + " " + user.name.family`. Click **Test Expression **to verify that the expression is working properly.
[See image.](#see-image-1f)
- Click **Save**.
- For the **department **attribute, select **Department **from the list and click **Next**.
- In the **Select Groups **section, choose the groups you want to assign to the application and click **Next**.
- In the **Application instances** section, click the newly configured application to view the **Connection Details**.
-
Click **Download Signing Certificate **and copy the **Single Signon Service **URL. You need these to configure SAML in the ZIA Admin Portal.
[See image.](#see-image-1l)
Ensure the certificate file name:
-
Has a .pem extension (e.g., rename it to pingone.pem). The Zscaler service only accepts certificates with the .pem extension.
By default, Windows hides extensions for known file types.
- [Change the Windows Folder Properties to View and Edit Extensions](#pem-instructions)
-
Contains only one dot (".").
[See image.](#pingone-pem)
[]
- Go to **Administration** > **Authentication Settings** > **Identity Providers**.
-
Click **Add IdP**.
If you have an existing IdP configuration, the **What do you want to do?** window appears. Click **Add another SAML IdP for a subset of users or locations** and then **Next**.
[See image.](#what-to-do)
-
In the **Add IdP **window:
- **SAML Portal URL**: Enter the **Single Signon Service **that you copied from the PingOne admin console.
- **Login Name Attribute**: Enter `NameID` (case-sensitive).
- **IdP SAML Certificate**: Upload the .pem certificate that you downloaded from the PingOne admin console.
- **Org-Specific Entity ID**: Enable if you have more than one organization instance on the same Zscaler cloud. For example, if you have two organization instances on the same Zscaler cloud and must authenticate both instances against the same PingOne account, you can't use the same entity ID for multiple apps in the PingOne admin console. For this situation, you must enable this setting for both instances to generate a unique org-specific entity ID.
- **Locations**: Select the [locations](/zia/about-locations) to map to this IdP. You can also search for a location. Any unselected locations are mapped to the default IdP. This field is set to **Any** for the default IdP, and you can't modify it.
- **Authentication Domains**: Select the domains to map to this IdP. This allows the Zscaler service to display the correct IdP to authenticate an incoming user. Any unselected domains are mapped to the default IdP. This field is set to **Any** for the default IdP, and you can't modify it. Apart from the default IdP, any additional IdPs must be mapped to at least one domain.
- **Vendor**: Select **PingOne**.
[See image.](#see-image-2c)
- (Optional) If you want to enable **Sign SAML Request **for additional security:
-
After enabling **Sign SAML Request:**
- **Signature Algorithm**: Zscaler recommends selecting **SHA-2 (256-bit)**.
- **Request Signing SAML Certificate**: Select the most recent certificate.
- **SP SAML Certificate**: Click **Download Certificate**.
[See image.](#see-image-2d-i)
- In the PingOne admin console, go to **Applications **and select your previously configured Zscaler cloud** **application.
-
On the **Overview **tab, click **Enable Advanced Configuration **to reveal the option for uploading the SAML signing certificate.
[See image.](#see-image-2d-iii)
- Go to the **Configuration **tab.
-
Click the **Edit **icon.
[See image.](#see-image-2d-v)
- Enable **Enforce Signed AuthRequest**.
-
In the **Verification Certificate **section, select **Import **and click **Choose File **to upload the **SP SAML Certificate **that you downloaded from the ZIA Admin Portal.
[See image.](#see-image-2d-vii)
- Click **Save**.
-
In the **Provisioning Options **section:
- **Enable SAML Auto-Provisioning**: Enable this option.
- **User Display Name Attribute**: Enter `displayName` (case-sensitive).
- **Group Name Attribute**: Enter `memberOf` (case-sensitive).
- **Department Name Attribute**: Enter `department` (case-sensitive).
[See image.](#see-image-2e)
- Click **Save **and [activate the change](/zia/saving-and-activating-changes-zia-admin-portal).
[]
- Go to **Administration** > **Authentication Settings** > **Identity Providers**.
- Click the **Edit **icon for your previously configured PingOne IdP.
- In the **Edit IdP **window, click **Enable SCIM Provisioning**.
-
Copy the **Base URL **and **Bearer Token**. You need them to configure SCIM in the PingOne admin console.
[See image.](#see-image-3d)
- Click **Save **and [activate the change](/zia/saving-and-activating-changes-zia-admin-portal).
[]
- In the PingOne admin console, go to **Integrations** > **Provisioning **> **Connections**.
-
Click the **Add** icon.
[See image.](#see-image-4b)
The **Create a New Connection **window appears.
- In the **Create a New Connection **window, click **Select **for **Identity Store**.
- In the search bar, enter `scim`.
-
Select **SCIM Outbound **and click **Next**.
[See image.](#see-image-4e)
- Provide a name for the SCIM connection and click **Next**.
-
In the **Configure Authentication section**:
- **SCIM Base URL**: Enter the **Base URL **you copied from the ZIA Admin Portal.
- **User Resource**: Enter `/Users`.
- **SCIM Version**: Select **2.0**.
- **Group Resource**: Enter `/Groups`.
- **Authentication Method**: Select **OAuth 2 Bearer Token**.
- **OAuth Access Token**: Enter the **Bearer Token **you copied from the ZIA Admin Portal.
- **Auth Type Header**: Select **Bearer**.
Click **Test Connection** to verify that the integration is working. Click **Next **after the integration is verified.
[See image.](#see-image-4h)
-
Review the **Configure Preferences **section and the **Actions **section. Click **Save **when you are satisfied.
[See image.](#see-image-4j)
-
In the **Overview** tab of the newly created provisioning connection, click the toggle to enable provisioning.
[See image.](#see-image-4k)
-
Go to the **Rules **tab on the **Provisioning **page and click the **Add** icon.
The **Create a New Rule **window appears.
- In the **Create a New Rule **window, provide a name for the rule and click **Create Rule**.
-
Use the search bar to find your newly created SCIM connection and select it.
[See image.](#see-image-4o)
- Click **Save**.
-
In the **User Filter **section, select the **Attribute **and **Value **to specify which users and groups are provisioned.
In the following example screenshot, the selected **Value **is a nested group that contains multiple separate groups and users.
[See image.](#see-image-4q)
- Click **Save**.
-
Click **Attribute Mapping**.
[See image.](#see-image-4s)
-
Click the **Edit **icon for the **Attribute Mapping **section.
[See image.](#see-image-4t)
- Click the **Advanced Expression **icon for the **displayName **attribute.
-
In the **Build and Test Expression **window, enter `user.name.given + " " + user.name.family`. Click **Test Expression **to verify that the expression is working properly. Click **Next **after the expression is verified.
[See image.](#see-image-4v)
-
Modify the rest of the attribute mappings so they match the following table:
| PingOne Attribute | Zscaler Attribute |
| ----------------- | ----------------- |
| Enabled | active |
| See step 4.v. | displayName |
| Family Name | familyName |
| Given Name | givenName |
| Username | userName |
| Email Address | workEmail |
| Department | department |
- Click **Save**.
- Click **Group Provisioning**.
-
Click the **Edit **icon.
[See image.](#see-image-4aa)
- Select the groups you want to provision and click **Save**.
- Click **Target **to review the configuration.
-
Click the toggle to enable the rule.
[See image.](#see-image-4ae)
After provisioning is enabled, the provisioning details are available.
- []Go to **Administration **>** Authentication Settings**.
- Under **Authentication Frequency**,** **choose how often users are required to authenticate to the Zscaler service. To learn more, see [About Authentication Default Settings](/zia/about-authentication-default-settings). If you select **Custom**, the following field appears:
- **Custom Authentication Frequency (days)**: Specify 1 to 180 days.
-
Under** Authentication Type**, choose **SAML**.
[See image.](#enable-saml-zia)
- Click **Save **and [activate the change](/zia/saving-and-activating-changes-admin-portal).
- []Start the Windows 10 Control Panel.
- Go to **Appearance & Personalization** > **File Explorer Options**.
- When the **File Explorer Options** window appears, click the **View **tab.
-
In **Advanced settings**, deselect **Hide extensions for known file types** to view extensions.
[See image.](#change-file-type)
- Rename the certificate to change the extension.
[]To configure the list and enable users access to PingOne:
- Go to **Administration **>** Advanced Settings**.
- In the **Authentication Exemptions** section, enter the required PingOne domains in **Exempted URLs**. To see the list of PingOne domains, refer to the IP address and domain reference section in the [PingOne documentation](https://docs.pingidentity.com/pingone/p1_cloud__platform_main_landing_page.html).
- Click **Save** and [activate the change](/zia/saving-and-activating-changes-admin-portal).
If you are using PAC files, enter the required PingOne domains in the [PAC file](/zia/how-do-i-use-default-pac-files-forward-traffic-zia) exemption list. Otherwise, the authentication fails.
This option only applies to user traffic from known locations. To learn more, see [Exempting URLs and Cloud Apps from Authentication](/zia/exempting-urls-cloud-apps-authentication).
[]![Image of the button to enable SAML in the ZIA Admin Portal](/downloads/zia/authentication-administration/provisioning-authenticating-users/saml-scim/saml-scim-configuration-guide-pingone/ZIA-enable-saml.png)
[]![Image of the File Explorer Options window](/downloads/zia/authentication-administration/provisioning-authenticating-users/saml-scim/saml-scim-configuration-guide-pingone/Windows-File-Explorer-Options-View-Hide-extensions-for-known-file-types.png)
[]![Image of the Application Catalog in the PingOne admin console](/downloads/zia/authentication-administration/provisioning-authenticating-users/saml-scim/saml-scim-configuration-guide-pingone/ZIA-pingone-app-catalog-1c.png)
[]![Quick Setup Section in the PingOne Admin Console](/downloads/zia/authentication-administration/provisioning-authenticating-users/saml-scim/saml-scim-configuration-guide-pingone/ZIA-pingone-app-quick-setup-1d.png)
[]![Image of the Advanced Expression icon in the PingOne Admin Console](/downloads/zia/authentication-administration/provisioning-authenticating-users/saml-scim/saml-scim-configuration-guide-pingone/ZIA-pingone-map-attributes-1e.png)
[]![Image of the Build and Test Expression window in the PingOne admin console](/downloads/zia/authentication-administration/provisioning-authenticating-users/saml-scim/saml-scim-configuration-guide-pingone/ZIA-pingone-edit-expression-1f.png)
[]![Connection Details Section in the PingOne Admin Console](/downloads/zia/authentication-administration/provisioning-authenticating-users/saml-scim/saml-scim-configuration-guide-pingone/ZIA-pingone-saml-connection-details-1l.png)
[]![Image of the .pem certificate file](/downloads/zia/authentication-administration/provisioning-authenticating-users/saml-scim/saml-scim-configuration-guide-pingone/ZIA-pingone-pem.png)
[]![Image of the What do you want to do? window](/downloads/zia/authentication-administration/provisioning-authenticating-users/saml-scim/saml-scim-configuration-guide-pingone/ZIA-pingone-what-to-do.png)
[]![Image of the General Info section in the Add IdP window](/downloads/zia/authentication-administration/provisioning-authenticating-users/saml-scim/saml-scim-configuration-guide-pingone/ZIA-pingone-IdP-general-info-2c.png)
[]![Image of the Sign SAML Request options](/downloads/zia/authentication-administration/provisioning-authenticating-users/saml-scim/saml-scim-configuration-guide-pingone/ZIA-pingone-sign-saml-2d-i.png)
[]![Image of the Enable Advanced Configuration button](/downloads/zia/authentication-administration/provisioning-authenticating-users/saml-scim/saml-scim-configuration-guide-pingone/ZIA-pingone-sign-saml-2d-iii.png)
[]![Image of the Edit icon for the Connection Details](/downloads/zia/authentication-administration/provisioning-authenticating-users/saml-scim/saml-scim-configuration-guide-pingone/ZIA-pingone-sign-saml-2d-v.png)
[]![Image of the Verification Certificate section](/downloads/zia/authentication-administration/provisioning-authenticating-users/saml-scim/saml-scim-configuration-guide-pingone/ZIA-pingone-sign-saml-2d-vii.png)
[]![Image of the SAML Auto-Provisioning options](/downloads/zia/authentication-administration/provisioning-authenticating-users/saml-scim/saml-scim-configuration-guide-pingone/ZIA-pingone-saml-auto-2e.png)
[]![Image of the Base URL and Bearer Token in the ZIA Admin Portal](/downloads/zia/authentication-administration/provisioning-authenticating-users/saml-scim/saml-scim-configuration-guide-pingone/ZIA-pingone-edit-idp-3d.png)
[]![Image of the Provisioning page in the PingOne admin console](/downloads/zia/authentication-administration/provisioning-authenticating-users/saml-scim/saml-scim-configuration-guide-pingone/ZIA-pingone-new-connection-4b.png)
[]![Image of the SCIM Outbound connection in the PingOne admin console](/downloads/zia/authentication-administration/provisioning-authenticating-users/saml-scim/saml-scim-configuration-guide-pingone/ZIA-pingone-scim-outbound-4e.png)
[]![Image of the Configure Authentication section in the PingOne admin console](/downloads/zia/authentication-administration/provisioning-authenticating-users/saml-scim/saml-scim-configuration-guide-pingone/ZIA-pingone-configure-auth-4h.png)
[]![Image of the Configure Preferences and Actions sections in the PingOne admin console](/downloads/zia/authentication-administration/provisioning-authenticating-users/saml-scim/saml-scim-configuration-guide-pingone/ZIA-pingone-review-preferences-4j.png)
[]![Enable the SCIM Connection in the PingOne Admin Console](/downloads/zia/authentication-administration/provisioning-authenticating-users/saml-scim/saml-scim-configuration-guide-pingone/ZIA-pingone-enable-scim-toggle-4k.png)
[]![Image of the newly created SCIM connection in the PingOne admin console](/downloads/zia/authentication-administration/provisioning-authenticating-users/saml-scim/saml-scim-configuration-guide-pingone/ZIA-pingone-select-connection-4o.png)
[]![Image of the User Filter in the PingOne admin console](/downloads/zia/authentication-administration/provisioning-authenticating-users/saml-scim/saml-scim-configuration-guide-pingone/ZIA-pingone-attribute-value-4q.png)
[]![Image of the Attribute Mapping icon in the PingOne admin console](/downloads/zia/authentication-administration/provisioning-authenticating-users/saml-scim/saml-scim-configuration-guide-pingone/ZIA-pingone-user-filter-4s.png)
[]![Image of the Edit icon for the Attribute Mapping section in the PingOne admin console](/downloads/zia/authentication-administration/provisioning-authenticating-users/saml-scim/saml-scim-configuration-guide-pingone/ZIA-pingone-edit-attribute-mapping-4t.png)
[]![Image of the Build and Test Expression window in the PingOne admin console](/downloads/zia/authentication-administration/provisioning-authenticating-users/saml-scim/saml-scim-configuration-guide-pingone/ZIA-pingone-edit-expression-1f.png)
[]![Image of the Edit icon for the Group Provisioning section in the PingOne admin console](/downloads/zia/authentication-administration/provisioning-authenticating-users/saml-scim/saml-scim-configuration-guide-pingone/ZIA-pingone-edit-groups-4aa.png)
[]![Image of the Sync Summary in the PingOne admin console](/downloads/zia/authentication-administration/provisioning-authenticating-users/saml-scim/saml-scim-configuration-guide-pingone/ZIA-pingone-review-provisioning-4ae.png)
[]To perform SP-initiated SSO:
-
Open any site secured with the Zscaler service.
You are redirected to `https://gateway.``<Zscaler Cloud Name>``.net` and prompted for a user name.
- Enter your **User Name** and click **Sign in**.