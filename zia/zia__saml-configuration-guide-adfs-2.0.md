# SAML Configuration Guide for AD FS 2.0
Source: https://help.zscaler.com/zia/saml-configuration-guide-adfs-2.0
PDF: https://help.zscaler.com/pdf/com/en/1399686.pdf

This guide illustrates how to configure a Windows Server 2008 R2 running Active Directory Federation Services 2.0 (AD FS) as the identity provider (IdP) for the Zscaler service. It assumes that AD FS 2.0 is already installed on the Windows server. To learn more about the steps in Windows Server 2008 R2, see the [Microsoft AD FS documentation](https://docs.microsoft.com/en-us/windows-server/identity/active-directory-federation-services).
Prerequisites
Ensure that you have the following before you start configuring the AD FS server:
- An AD FS account with admin privileges
- Existing Active Directory (AD)
- [Zscaler cloud name](/zia/what-my-cloud-name)
- [The Zscaler SP SAML certificate](/zia/adding-identity-providers#SP-SAML-Certificate)
Configuring AD FS as the IdP for the Zscaler Service
To configure SAML with AD FS:
- [1. Add a Relying Party Trust](#relying-party-trust)
- [2. Upload the Zscaler SAML SSL Certificate](#upload-zscaler-ssl-cert)
- [3. Add a Claim Rule](#add-claim-rule)
- [4. Download the AD FS SAML Certificate](#export-adfs-ssl-cert)
- [5. (Optional) Restrict Groups](#restrict-groups)
- [6. Add AD FS as the IdP for the Zscaler service](/zia/adding-identity-providers)
- [7. Configure SAML SSO in the ZIA Admin Portal](#saml-zscaler-admin-portal)
- [8. Configure the Zscaler Authentication Exemptions List](#authentication-exemptions-list)
Testing the SAML Configuration
This testing method only applies if you're forwarding traffic using PAC files, GRE tunnels, or IPSec tunnels, and you've enabled **Enforce Authentication** for the [location](/zia/configuring-locations#EnforceAuthentication) or [sublocation](/zia/configuring-sublocations#EnforceAuthentication).
To test the SAML configuration with AD FS:
- If you're already logged in to the Zscaler service, browse to https://login.<Zscaler Cloud Name>.net/zscaler.portal, and click **Logout**. Replace <Zscaler Cloud Name> with your Zscaler Cloud name. To learn more, see [What is my cloud name for ZIA?](/zia/what-my-cloud-name-zia)
- Browse to a website. You will be redirected to AD FS and prompted to log in.
- Enter your AD FS credentials, and you will automatically be redirected to the original URL request.
- Browse to [ip.zscaler.com](http://ip.zscaler.com/), and the status window will show the username indicating the authentication was successful.
Troubleshooting
To troubleshoot browser settings and SAML error codes, see [Troubleshooting SAML](/zia/saml-troubleshooting-guidelines).
To troubleshoot Integrated Windows Authentication (IWA) in AD FS, see the Microsoft documentation for [AD FS Troubleshooting](https://docs.microsoft.com/en-us/windows-server/identity/ad-fs/troubleshooting/ad-fs-tshoot-iwa) and [IWA Browser Configuration](https://docs.microsoft.com/en-us/windows-server/identity/ad-fs/operations/configure-ad-fs-browser-wia).
[]In AD FS, a relying party is a Federation Service or application that requests and consumes claims from a claims' provider in a particular transaction. Configure the Zscaler service as a relying party trust.
- Open **AD FS 2.0**.
- In the** AD FS 2.0 **window, open the **Trust Relationships** folder, and then right-click **Relying Party Trust **to add a relying party trust.
[See image.](#img1)
- When the **Add Relying Party Trust **wizard appears, click **Start**.
[See image.](#im2)
- In **Select Data Source**, choose **Enter data about the relying party **manually and click **Next**.
[See image.](#im3)
- In **Specify Display Name**, enter a display name for the Zscaler service, such as Zscaler-SAML, and then click **Next**.
- In** Choose Profile**, select AD FS 2.0 Profile, and click **Next**.
- In **Configure Certificate**, click **Next** and proceed to the next step.
- In **Configure URL**, select **Enable support for the SAML 2.0 WebSSO protocol **and enter the Zscaler SSO URL in the following format: https://login.<Zscaler Cloud>:443/sfc_sso. Replace <Zscaler Cloud> with your cloud name. For example, if your organization logs into https://admin.zscalerbeta.net, then the Zscaler SSO URL is https://login.zscalerbeta.net:443/sfc_sso.
[See image.](#img4)
- In **Configure Identifiers**, enter the Zscaler service domain name. This depends on the domain name in the administrative URL you use to log in to the service. For example, if you log in to https://admin.zscalertwo.net, then enter zscalertwo.net, and then click **Add** to add it to the list of identifiers, as shown in the following figure. The domain name must be in lower case.
[See image.](#img5)
- In **Choose Issuance Authorization Rules**, select **Permit all users to access this relying party** and click **Next**.
- In **Ready to Add Trust**, the wizard displays the configured settings. Click **Next**.
- Click **Finish** to add the relying party trust to the database. Clear the option to open the **Edit Claim Rules **dialog. Before you define a claim rule, you will first upload the Zscaler certificate.
[]Edit the Zscaler SAML configuration on the AD FS server so you can add the Zscaler signature verification certificate:
- In the** AD FS 2.0 window**, open the** Trust Relationships **>** Relying Party Trusts** folder.
- Right-click the relying party trust that you created and open its **Properties**.
- Do the following:
- In the **Signature** tab, click **Add**, navigate to the Zscaler certificate, and then click **Open**.
[See image.](#img6)
- In the **Advanced** tab, select **SHA-1** from the** Secure hash algorithm **menu, and then click **OK**.
[]Configure the SAML assertions to be federated to Zscaler to identify the user. It includes the group membership, department and full name parameters, which the Zscaler service uses to determine whether a user is allowed access.
To add a claim rule:
- In the **AD FS 2.0 window**, open the **Trust Relationships **> **Relying Party Trusts** folder.
- Right-click the relying party trust that you created and select **Edit Claim Rules**.
- When the **Edit Claim Rules** window appears, click** Add Rule**.
[See image.](#img7)
- In the **Choose Rule Type** of the** Add Transform Claim Rule** wizard, select **Send LDAP Attributes as Claims** as the claim rule template, so the claims contain LDAP attribute values from the attribute store, AD. Then click **Next**.
[See image.](#img8)
- In **Configure Claim Rule**, do the following and click **Next**:
- Enter a name for the claim rule.
- From the **Attribute Store** menu, choose **Active Directory**.
- Map the LDAP attributes that represent the user's login name, full name, department, and group to fields in the outgoing claim.
- Map the LDAP attribute for login name to an outgoing claim type.
From the **LDAP Attribute** column, select the attribute for the login name. Select **SAM-Account-Name** only if you have one domain hosted by the Zscaler service. Otherwise, select **User-Principal-Name**. Selecting **E-Mail-Addresses **is not recommended because users can have multiple email addresses and this could result in multiple user credentials in the Zscaler service.
From the **Outgoing Claim Type** column, select **Name ID**.** **Ensure that the Name ID is two words.
- Map the LDAP attribute for full name to an outgoing claim type. Select **Display-Name** from the **LDAP Attribute **column, and type in **displayName** in the **Outgoing Claim Type **column.
- Map the LDAP attribute for a department to an outgoing claim type. This attribute is used to populate the **Department** field in the reports produced by the Zscaler service.
You can specify any attribute that identifies the information that should appear in the **Department** field. For example, you can choose **Department** or **Organizational-Unit** from the **LDAP Attribute** column. Type in **department** in the **Outgoing Claim Type** column.
- Map the LDAP attribute for the group to an outgoing claim type. Select **Token Groups – Unqualified Names** from the **LDAP Attribute** column, and type in **memberOf** in the **Outgoing Claim Type** column.
Using the **Is-Member-Of-DL** attribute from the** LDAP Attribute** column is not advisable, as the groups can be displayed in the form of LDAP paths instead of just the group name.
[See image.](#img9)
- When the wizard displays the newly added claim rule in the list, click **OK**.
[See image.](#img10)
[]To export the AD FS SAML certificate that you will import to the ZIA Admin Portal:
- In the** AD FS 2.0** window, open the **Service **> **Certificates** folder, right-click the Token-signing certificate, and click **View Certificate**.
[See image.](#img11)
- In the **Certificate** window, go to the **Details** tab and click **Copy to File…** to open the **Certificate Export** wizard.
[See image.](#img12)
- Start the **Certificate Export Wizard**.
- In **Export Private Key**, choose **No**,** do not export the private key **and click **Next**.
- In** Export File Format**, choose Base-64 encoded as the file format of the certificate you want to export and click **Next**.
[See image.](#img13)
- In **File to Export**, either click **Browse** to navigate to the file you want to export or enter the file name. Click **Next**.
- Click **Finish** to exit the wizard.
- Navigate to the downloaded certificate and ensure the file name:
- Has a **.pem** extension (e.g., rename it to adfs.pem). The Zscaler service only accepts certificates with the .pem extension.
- Contains only one dot (".").
By default, Windows hides extensions for known file types. To change the Windows folder properties to view and edit extensions, [follow these instructions.](#pem-instructions)
- []Start Windows 10 **Control Panel**.
- Go to **Appearance & Personalization** > **File Explorer Options**.
- When the **File Explorer Options** window appears, click the **View **tab.
- In **Advanced settings:**, deselect **Hide extensions for known file types** to view extensions.
- Rename the certificate to change the extension.
[]AD FS 2.0 federates all the groups of a user, by default. You can restrict the groups to only those to which policies will be applied. Zscaler recommends putting users in groups that begin with a specific word, such as Internet, to facilitate applying restrictions on group federations. For example, you can create groups such as Internet General, Internet Restricted, etc.
To restrict the groups:
- [a. Remove the group mapping from the rule that you created when you added a claim rule.](#restrictgroups1) (See [Add a Claim Rule](/zia/saml-configuration-example-adfs#add-claim-rule) above.)
- [b. Create a new rule for group membership.](#restrictgroups2)
[]To edit the existing claim rule:
- In the **AD FS 2.0 Management **window, open the **Trust Relationships **>** Relying Party** **Trusts **folder.
- Right-click the relying party trust that you created and select **Edit Claim Rules**.
- When the** Edit Claim Rules **window appears, click **Edit Rule **to modify the rule that you created when adding a claim rule.
- In the **Configure Claim Rule** window, delete the row that mapped the LDAP attribute for group to a claim rule type.
- Click **OK**.
[]To add a new rule for group membership:
- In the **AD FS 2.0** window, open the **Trust Relationships **>** Relying Party Trusts **folder.
- Right-click the relying party trust that you created and select **Edit Claim Rules**.
- When the **Edit Claim Rules **window appears, click **Add Rule**.
- Select** Send Claims Using a Custom Rule** and click **Next**.
- In the **Custom Rule **window, do the following:
- Enter a name for this rule, such as “Return Group Membership”.
- In the custom rule box, enter the following text to enumerate the group membership and put it into an array called (memberOf):
c:[Type == "http://schemas.microsoft.com/ws/2008/06/identity/claims/windowsaccountname", Issuer == "AD AUTHORITY"] => add(store = "Active Directory", types = ("memberOf"), query = ";tokenGroups;{0}", param = c.Value);
- Click **Finish**.
- Click **Add Rule**.
- Select **Send Claims Using a Custom Rule**, and click **Next**.
- In the** Custom Rule **window, do the following:
- Enter a name for this rule, such as “Restrict Group Membership”.
- In the custom rule box, enter something like the following:
c:[Type == "memberOf", Value =~ "Internet.+"] => issue(claim = c);
The preceding regular expression matches any group name that begins with “Internet”. E.g. ‘Internet Access’ or ‘InternetGroup3’ or ‘Internet Restricted’
c:[Type == "memberOf", Value =~ "Sales|Marketing|HR"] => issue(claim = c);
The preceding regular expression matches only 3 groups - “Sales”, “Marketing” and “HR”
c:[Type == "memberOf", Value =~ "AccessLevel[1-9]"] => issue(claim = c);
The preceding regular expression matches any group name that begins with “AccessLevel” and then has a number 1 to 9. E.g. ‘AccessLevel1’ or ‘AccessLevel7’
- Click **Finish**.
[]To configure SAML SSO in the ZIA Admin Portal:
- Go to **Administration **>** Authentication Settings**.
- Under **Authentication Frequency**,** **choose how often users are required to authenticate to the Zscaler service. To learn more, see [About Authentication Profile](/zia/about-authentication-profile#authentication-frequency). If you select **Custom**, the following field will appear:
- **Custom Authentication Frequency (days)**: Specify 1 to 180 days.
- Under** Authentication Type**, choose **SAML**.
[See image.](#seeimage-2c)
- Click **Save **and [activate the change](/zia/saving-and-activating-changes-admin-portal).
[]![Screenshot highlighting the SAML option under Authentication Type on the Authentication Profile page.](/downloads/zia/authentication-administration/provisioning-authenticating-users/saml-scim/configuring-saml/ZIA-Authentication-Profile-Authentication-Type.png)
[]To configure the Zscaler Authentication Exemptions list and enable users access to AD FS:
- Go to **Administration **>** Advanced Settings**.
- In the **Authentication Exemptions** section, enter your organization's AD FS URL in **Exempted URLs**.
- Click **Save** and [activate the change](/zia/saving-and-activating-changes-admin-portal).
If you are using PAC files, enter the AD FS URL in the [PAC file](/zia/using-default-pac-files-forward-traffic-zia) exemption list. Otherwise, the authentication will fail.
[]![Screenshot showing how to add Relying Party Trust from a menu](/downloads/zia/documentation-knowledgebase/authenticating-and-managing-users/saml/saml-configuration-guide/saml-configuration-example-adfs/relying_party_trust.png)
[]![Screenshot showing the initial text of the Add Relying Party Trust wizard](/downloads/zia/documentation-knowledgebase/authenticating-and-managing-users/saml/saml-configuration-guide/saml-configuration-example-adfs/start_add_relying_party_trust_wizard_.png)
[]![Screenshot from installation wizard about entering data about the relying party manually](/downloads/zia/documentation-knowledgebase/authenticating-and-managing-users/saml/saml-configuration-guide/saml-configuration-example-adfs/enter_data_about_the_relying_party_manually.png)
[]![Screenshot from installation wizard about enabling support for the SAML 2.0 WebSSO protocol and what format to use ](/downloads/zia/documentation-knowledgebase/authenticating-and-managing-users/saml/saml-configuration-guide/saml-configuration-example-adfs/enable_support_for_the_saml_2.0_websso_protocol.png)
[]![Screenshot from wizard about how to configure indentifiers](/downloads/zia/documentation-knowledgebase/authenticating-and-managing-users/saml/saml-configuration-guide/saml-configuration-example-adfs/configure_identifiers_.png)
[]![Screenshot illustrating how to add the Zscaler certificate](/downloads/zia/documentation-knowledgebase/authenticating-and-managing-users/saml/saml-configuration-guide/saml-configuration-example-adfs/upload_the_zscaler_saml_certificate.png)
[]![Screenshot showing the window for edit claim rules](/downloads/zia/documentation-knowledgebase/authenticating-and-managing-users/saml/saml-configuration-guide/saml-configuration-example-adfs/edit_claim_rules.png)
[]![Screenshot from the installation wizard showing to Send LDAP Attributes as Claims](/downloads/zia/documentation-knowledgebase/authenticating-and-managing-users/saml/saml-configuration-guide/saml-configuration-example-adfs/send_ldap_attributes_as_claims.png)
[]![Screenshot from installation wizard showing Token Groups – Unqualified Names from the LDAP Attribute column](/downloads/zia/documentation-knowledgebase/authenticating-and-managing-users/saml/saml-configuration-guide/saml-configuration-example-adfs/token_groups_%C3%A2%C2%80%C2%93_unqualified_names.png)
[]![Screenshot showing the results of adding the new rule](/downloads/zia/documentation-knowledgebase/authenticating-and-managing-users/saml/saml-configuration-guide/saml-configuration-example-adfs/new_claim_rule.png)
[]![Screenshot from ADFS 2.0 Management allowing people to view new certificate](/downloads/zia/documentation-knowledgebase/authenticating-and-managing-users/saml/saml-configuration-guide/saml-configuration-example-adfs/_view_certificate.png)
[]![Screenshot showing the details tab of the certificate window](/downloads/zia/documentation-knowledgebase/authenticating-and-managing-users/saml/saml-configuration-guide/saml-configuration-example-adfs/details_tab.png)
[]![Screenshot from certificate export wizard ](/downloads/zia/documentation-knowledgebase/authenticating-and-managing-users/saml/saml-configuration-guide/saml-configuration-example-adfs/export_file_format.png)