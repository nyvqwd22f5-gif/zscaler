# SAML Configuration Guide for AD FS 3.0
Source: https://help.zscaler.com/zia/saml-configuration-guide-adfs-3.0
PDF: https://help.zscaler.com/pdf/com/en/1402081.pdf

This guide illustrates how to configure a Windows Server 2012 R2 running Active Directory Federation Services 3.0 (AD FS) as the identity provider (IdP) for the Zscaler service. It assumes that AD FS 3.0 is already installed on the Windows server. To learn more about the steps in the Windows Server 2012 R2, see the [Microsoft AD FS documentation](https://docs.microsoft.com/en-us/windows-server/identity/active-directory-federation-services).
Prerequisites
Ensure that you have the following before you start configuring the AD FS server as your IdP:
- An AD FS account with admin privileges
- Existing Active Directory (AD)
- [Zscaler cloud name](/zia/what-my-cloud-name-zia)
- [The Zscaler SP SAML certificate](/zia/adding-identity-providers#SP-SAML-Certificate)
- [The Zscaler SP XML metadata](/zia/adding-identity-providers#SP-Metadata)
Configuring AD FS as the IdP for the Zscaler Service
To configure SAML with AD FS:
- [1. Add a Relying Party Trust and Claim Rule](#add-relying-trust-claim-rule)
- [2. Upload the Zscaler SAML Certificate](#upload-zscaler-saml-cert)
- [3. Download the AD FS SAML Certificate](#download-adfs-saml-cert)
- [4. (Optional) Restrict Groups](#restrict-groups)
- [5. Add AD FS as the IdP for the Zscaler Service](/zia/adding-identity-providers)
- [6. Configure SAML SSO in the ZIA Admin Portal](#configure-saml-zia-admin-portal)
- [7. Configure the Zscaler Authentication Exemptions List](#authentication-exemptions-list)
Testing the SAML Configuration
This testing method only applies if you're forwarding traffic using PAC files, GRE tunnels, or IPSec tunnels, and you've enabled **Enforce Authentication** for the [location](/zia/configuring-locations#EnforceAuthentication) or [sublocation](/zia/configuring-sublocations#EnforceAuthentication).
To test the SAML configuration with AD FS:
- If you're already logged in to the Zscaler service, browse to https://login.<Zscaler Cloud Name>.net/zscaler.portal, and click **Logout**. Replace <Zscaler Cloud Name> with your Zscaler cloud name. To learn more, see [What is my cloud name for ZIA?](/zia/what-my-cloud-name-zia)
- Browse to a website. You will be redirected to AD FS and prompted to log in.
- Enter your AD FS credentials, and you will automatically be redirected to the original URL request.
If you use Google Chrome to authenticate, you also need to provide domain information.
- Browse to [ip.zscaler.com](http://ip.zscaler.com), and the status window will show the username indicating the authentication was successful.
Troubleshooting
If any errors occur, see [Troubleshooting SAML](/zia/troubleshooting-saml) to troubleshoot browser settings and SAML error codes.
To troubleshoot Integrated Windows Authentication (IWA) in AD FS, see the Microsoft documentation for [AD FS Troubleshooting](https://docs.microsoft.com/en-us/windows-server/identity/ad-fs/troubleshooting/ad-fs-tshoot-iwa) and [IWA Browser Configuration](https://docs.microsoft.com/en-us/windows-server/identity/ad-fs/operations/configure-ad-fs-browser-wia).
[]In AD FS, a relying party is a Federation Service or application that requests and processes claims from a claims' provider in a particular transaction. You must configure the Zscaler service as a relying party trust and add a claim rule, which is a statement that provides information about a user. The Zscaler service uses the claim rule to determine if a user is allowed access.
To add Zscaler as a relying party trust and to add a claim rule:
- Open the **Server Manager**.
- Go to **Tools **>** AD FS Management**.
[See image.](#seeimage1b)
- In the left navigation pane, expand the **Trust Relationships **folder, and click the **Relying Party Trusts **folder.
[See image.](#seeimage1c)
- In the **Actions **section, click **Add Relying Party Trust…**.
[See image.](#seeimage1d)
The **Add Relying Party Trust Wizard** appears.
- In **Welcome**, click **Start**.
[See image.](#seeimage1e)
- In **Select Data Source**:
- Choose **Import data about the relying party from a file**.
- Under **Federation metadata file location:**, click **Browse**, navigate to the Zscaler SP XML metadata file, and then click **Open**.
- Click **Next**.
[See image.](#seeimage1f)
- In **Specify Display Name**, enter a display name for the Zscaler service, and click **Next**. In this example, it's Zscaler SAML.
[See image.](#seeimage1g)
- In **Configure Multi-factor Authentication Now?**,** **choose **I do not want to configure multi-factor authentication settings for this relying party trust at this time**,** **and click **Next**.
[See image.](#seeimage1h)
- In **Choose Issuance Authorization Rules**, choose **Permit all users to access this relying party**, and then click **Next**.
[See image.](#seeimage1i)
- In **Ready to Add Trust**, review your settings, and click **Next**.
[See image.](#seeimage1j)
- In **Finish**, select** Open the Edit Claim Rules dialog for this relying party trust when the wizard closes**, and click **Close **to add the relying party trust to the database.
[See image.](#seeimage1k)
- In the **Edit Claim Rules** window,** **click **Add Rule...**.
[See image.](#seeimage1l)
The **Add Transform Claim Rule Wizard** appears.
- In **Choose Rule Type**, choose **Send LDAP Attributes as Claims** from the dropdown menu,** **and click **Next**.
[See image.](#seeimage1m)
- In **Configure Claim Rule**:
- **Claim rule name**: Enter a name for the claim rule. In this example, it's Zscaler Claim Rule.
- **Attribute store**: Choose **Active Directory**.
- **Mapping of LDAP attributes to outgoing claim types**: Map the LDAP attributes that represent the user's login name, full name, group, and department to fields in the outgoing claim.
- Login name
- **LDAP Attribute**: Choose **SAM-Account-Name** if the Zscaler service is hosting one domain for your organization; otherwise, choose **User-Principal-Name**. Zscaler doesn't recommend choosing **E-Mail-Addresses** because users can have multiple email addresses, and this could result in multiple user credentials in the Zscaler service.
- **Outgoing Claim Type**: Choose **Name ID**.
- Full name
- **LDAP Attribute**: Choose **Display-Name**.
- **Outgoing Claim Type**: Enter `DisplayName`.
- Group
- **LDAP Attribute**: Choose** Token Groups - Unqualified Names**. Zscaler doesn't recommend choosing **Is-Member-Of-DL **because the groups can be displayed in the form of LDAP paths instead of the group name.
- **Outgoing Claim Type**: Enter `memberOf`.
- Department
- **LDAP Attribute**: Choose **Department** or **Organizational-Unit**.
- **Outgoing Claim Type**: Enter `department`.
The Zscaler services uses the department attribute to populate the **Department** field in the reports.
[See image.](#seeimage1n)
- Click **Finish **to add the claim rule.
- In the **Edit Claim Rules **window, click **Apply** and then **OK**.
[See image.](#seeimage1p)
[]![The AD FS Management menu under Tools](/downloads/zia/authentication-administration/provisioning-authenticating-users/saml-scim/saml-configuration-guide-adfs-30/ADFS-Tools-AD-FS-Management-Menu.png?1616529089)
[]![The Relying Party Trusts folder in the Trust Relationships folder.](/downloads/zia/authentication-administration/provisioning-authenticating-users/saml-scim/saml-configuration-guide-adfs-30/ADFS-Relying-Party-Trusts-Menu.png)
[]![The Add Relying Party Trust... option in the Actions section.](/downloads/zia/authentication-administration/provisioning-authenticating-users/saml-scim/saml-configuration-guide-adfs-30/ADFS-Actions-Add-Relying-Party-Trust.png)
[]![The Start button in the Welcome step](/downloads/zia/authentication-administration/provisioning-authenticating-users/saml-scim/saml-configuration-guide-adfs-30/ADFS-Add-Relying-Party-Trust-Wizard-Welcome.png)
[]![The configured Select Data Source step in the Add Relying Party Trust Wizard.](/downloads/zia/authentication-administration/provisioning-authenticating-users/saml-scim/saml-configuration-guide-adfs-30/ADFS-Add-Relying-Party-Trust-Wizard-Select-Data-Source.png)
[]![The configured Specify Display Name step in the Add Relying Party Trust Wizard.](/downloads/zia/authentication-administration/provisioning-authenticating-users/saml-scim/saml-configuration-guide-adfs-30/ADFS-Add-Relying-Party-Trust-Wizard-Specify-Display-Name.png)
[]![The I do not want to configure multi-factor authentication settings for this relying party trust at this time option in the Multi-factor Authentication Now? step.](/downloads/zia/authentication-administration/provisioning-authenticating-users/saml-scim/saml-configuration-guide-adfs-30/ADFS-Add-Relying-Party-Trust-Wizard-Configure-Multi-factor-Authentication-Now.png)
[]![The Permit all users to access this relying party option in the Choose Issuance Authorization Rules step.](/downloads/zia/authentication-administration/provisioning-authenticating-users/saml-scim/saml-configuration-guide-adfs-30/ADFS-Add-Relying-Party-Trust-Wizard-Choose-Issuance-Authorization-Rules.png)
[]![The Next button in the Ready to Add Trust step.](/downloads/zia/authentication-administration/provisioning-authenticating-users/saml-scim/saml-configuration-guide-adfs-30/ADFS-Add-Relying-Party-Trust-Wizard-Ready-to-Add-Trust.png)
[]![The Open the Edit Claim Rules dialog for this relying party trust when the wizard closes option in the Finish step.](/downloads/zia/authentication-administration/provisioning-authenticating-users/saml-scim/saml-configuration-guide-adfs-30/ADFS-Add-Relying-Party-Trust-Wizard-Finish.png)
[]![The Add Rule... button in the Edit Claim Rules window.](/downloads/zia/authentication-administration/provisioning-authenticating-users/saml-scim/saml-configuration-guide-adfs-30/ADFS-Edit-Claim-Rules-Add-Rule.png)
[]![The Claim rule template field in the Choose Rule Type step.](/downloads/zia/authentication-administration/provisioning-authenticating-users/saml-scim/saml-configuration-guide-adfs-30/ADFS-Add-Transform-Claim-Rule-Wizard-Choose-Rule-Type.png)
[]![The configured Configure Claim Rule step in the Add Transform Claim Rule Wizard.](/downloads/zia/authentication-administration/provisioning-authenticating-users/saml-scim/saml-configuration-guide-adfs-30/ADFS-Add-Transform-Claim-Rule-Wizard-Configure-Claim-Rule.png)
[]![The OK and Apply buttons in the Edit Claim Rules window.](/downloads/zia/authentication-administration/provisioning-authenticating-users/saml-scim/saml-configuration-guide-adfs-30/ADFS-Edit-Claim-Rules-Apply-OK.png)
[]To edit the Zscaler SAML configuration on the AD FS server so you can add the Zscaler signature verification certificate:
- In the **Relying Party Trusts** section, double-click the relying party trust you created in [Step 1](#add-relying-trust-claim-rule). In this example, it's Zscaler SAML.
[See image.](#seeimage2a)
- In the **Properties** window, click the **Signature **tab.
[See image.](#seeimage2b)
- Click **Add..**.
[See image.](#seeimage2c)
- Choose **All Files (*.*)** from the dropdown menu, navigate to the Zscaler SP SAML certificate,** **and then click **Open**.
- In the **Properties** window, click **Apply** and then **OK**.
[See image.](#seeimage2e)
[]![The Relying Party Trusts section in the AD FS window.](/downloads/zia/authentication-administration/provisioning-authenticating-users/saml-scim/saml-configuration-guide-adfs-30/ADFS-Relying-Party-Trusts-Section.png)
[]![The Signature tab in the Properties window.](/downloads/zia/authentication-administration/provisioning-authenticating-users/saml-scim/saml-configuration-guide-adfs-30/ADFS-Properties-Signature-Tab.png)
[]![The Add.. button in the Signature tab.](/downloads/zia/authentication-administration/provisioning-authenticating-users/saml-scim/saml-configuration-guide-adfs-30/ADFS-Properties-Signature-Add...png)
[]![The OK and Apply buttons in the Properties window.](/downloads/zia/authentication-administration/provisioning-authenticating-users/saml-scim/saml-configuration-guide-adfs-30/ADFS-Properties-Signature-Apply-OK.png)
[]To download the AD FS SAML certificate that you will import to the ZIA Admin Portal:
- In the left navigation pane, expand the **Service **folder, and click the **Certificates **folder.
[See image.](#seeimage3a)
- In the **Certificates** section, under **Token-signing**, right-click the certificate, and** **click **View Certificate...**.
[See image.](#seeimage3b)
- In the **Certificate** window, click the **Details **tab.
- Click **Copy to File...**.
[See image.](#seeimage3c)
The **Certificate Export Wizard** appears.
- In** Welcome to the Certificate Export Wizard**, click **Next**.
[See image.](#seeimage3e)
- In **Export File Format**, select **Base-64 encoded X.509 (.CER)**,** **and click **Next**.
[See image.](#seeimage3f)
- In **File to Export**, click **Browse**, enter a name for the certificate, and click **Save** and then **Next**. In this example, the certificate name is adfs.
[See image.](#seeimage3g)
- In **Completing the Certificate Export Wizard**, click **Finish**.
[See image.](#seeimage3h)
- In the **Certificate** window, click **OK**.
- Navigate to the downloaded certificate, and ensure the file name:
- Has a .pem extension (e.g., rename it to adfs.pem). The Zscaler service only accepts certificates with the .pem extension.
- Contains only one dot (".").
[See image.](#seeimage3j)
By default, Windows hides extensions for known file types.
- [Change the Windows Folder Properties to View and Edit Extensions](#pem-instructions)
- []Start Windows 10 Control Panel.
- Go to **Appearance & Personalization** > **File Explorer Options**.
- When the **File Explorer Options** window appears, click the **View **tab.
- In **Advanced settings:**, deselect **Hide extensions for known file types** to view extensions.
[See image.](#seeimage3iv)
- Rename the certificate to change the extension.
[]![The Certificates folder in the Service folder.](/downloads/zia/authentication-administration/provisioning-authenticating-users/saml-scim/saml-configuration-guide-adfs-30/ADFS-Certificates-Menu.png)
[]![The View Certificates... option for the Toke-signing AD FS certificate.](/downloads/zia/authentication-administration/provisioning-authenticating-users/saml-scim/saml-configuration-guide-adfs-30/ADFS-Certificates-View-Certificate-Option.png)
[]![The Copy to File... button in the Details tab of the Certificate window.](/downloads/zia/authentication-administration/provisioning-authenticating-users/saml-scim/saml-configuration-guide-adfs-30/ADFS-Certificate-Copy-to-File.png)
[]![The Next button in the Welcome to the Certificate Export Wizard step.](/downloads/zia/authentication-administration/provisioning-authenticating-users/saml-scim/saml-configuration-guide-adfs-30/ADFS-Welcome-Certificate-Export-Wizard.png)
[]![The Based-64 encoded X.509 (.CER) option in the Export File Format step.](/downloads/zia/authentication-administration/provisioning-authenticating-users/saml-scim/saml-configuration-guide-adfs-30/ADFS-Export-File-Format-Base-64-Encoded-X509-CER.png)
[]![The File name: field in the File to Export step.](/downloads/zia/authentication-administration/provisioning-authenticating-users/saml-scim/saml-configuration-guide-adfs-30/ADFS-File-to-Export-Browse.png)
[]![The Finish button in the Completing the Certificate Export Wizard step.](/downloads/zia/authentication-administration/provisioning-authenticating-users/saml-scim/saml-configuration-guide-adfs-30/ADFS-Completing-Certificate-Export-Wizard.png)
[]![The Hide extensions for known file types deselected in the View tab of the Windows File Explorer Options.](/downloads/zia/authentication-administration/provisioning-authenticating-users/saml-scim/saml-configuration-guide-adfs-30/Windows-File-Explorer-Options-View-Hide-extensions-for-known-file-types.png)
[]![The exported AD FS SAML certificate with the .pem extension.](/downloads/zia/authentication-administration/provisioning-authenticating-users/saml-scim/saml-configuration-guide-adfs-30/Windows-ADFS-Certificate-PEM-Extension.png)
[]AD FS 3.0 federates all user groups by default. You can restrict the groups to only those to which policies will be applied. Zscaler recommends putting users in groups that begin with a specific word (e.g., internet) to facilitate applying restrictions on group federations. For example, you can create groups such as Internet General, Internet Restricted, etc. To restrict groups, you must remove the group mapping from your existing claim rule, and add a new claim rule for your groups.
To restrict groups:
- In the left navigation pane, expand the **Trust Relationships **folder, and click the **Relying Party Trusts **folder.
[See image.](#seeimage4a)
- In the **Relying Party Trusts** section, right-click the relying party trust you created in [Step 1](#add-relying-trust-claim-rule), and click **Edit Claim Rules...**. In this example, it's Zscaler SAML.
[See image.](#seeimage4b)
- In the **Edit Claim Rules** window, select the claim rule that you created in [Step 1](#add-relying-trust-claim-rule), and click **Edit Rule...**. In this example, it's Zscaler Claim Rule.
[See image.](#seeimage4c)
- In the **Edit Rule** window, remove the row containing the group LDAP attribute and outgoing claim type, and click **OK**. In this example, the group LDAP attribute is Token-Groups - Unqualified Names, and the group outgoing claim type is memberOf.
[See image.](#seeimage4d)
- In the **Edit Claim Rules** window, click **Add Rule...**.
[See image.](#seeimage4e)
The **Add Transform Claim Rule Wizard **appears.
- In **Choose Rule Type**, choose **Send Claims Using a Custom Rule** from the dropdown menu,** **and click **Next**.
[See image.](#seeimage4f)
- In **Configure Claim Rule**:
- **Claim rule name**: Enter a name for the claim rule. In this example, it's Return Group Membership.
- **Custom rule**: Enter a similar custom rule to enumerate the group membership and put it into an array called `memberOf`.
c:[Type == "http://schemas.microsoft.com/ws/2008/06/identity/claims/windowsaccountname", Issuer == "AD AUTHORITY"] => add(store = "Active Directory", types = ("memberOf"), query = ";tokenGroups;{0}", param = c.Value);
[See image.](#seeimage4g)
- Click **Finish**.
- In the **Edit Claim Rules** window, click **Add Rule...**.
[See image.](#seeimage4i)
The **Add Transform Claim Rule Wizard **appears.
- In **Choose Rule Type**, choose **Send Claims Using a Custom Rule** from the dropdown menu,** **and click **Next**.
[See image.](#seeimage4j)
- In **Configure Claim Rule**:
- **Claim rule name**: Enter a name for the claim rule. In this example, it's Restrict Group Membership.
- **Custom rule**: Enter custom rules to authenticate specific groups.
The following rule matches any group names that begin with `Internet` (e.g., Internet Access, InternetGroup3, Internet Restricted, etc.):
c:[Type == "memberOf", Value =~ "Internet.+"] => issue(claim = c);
The following rule only matches three groups: `Sales`, `Marketing`, and `HR`.
c:[Type == "memberOf", Value =~ "Sales|Marketing|HR"] => issue(claim = c);
The following rule matches any group names that begin with `AccessLevel` and has a number from 1 to 9 (e.g., AccessLevel1, AccessLevel7, etc.):
c:[Type == "memberOf", Value =~ "AccessLevel[1-9]"] => issue(claim = c);
[See image.](#seeimage4k)
- Click **Finish**.
- In the **Edit Claim Rules **window, click **Apply** and then **OK**.
[]![The Relying Party Trusts folder in Trust Relationships folder.](/downloads/zia/authentication-administration/provisioning-authenticating-users/saml-scim/saml-configuration-guide-adfs-30/ADFS-Relying-Party-Trusts-Menu.png)
[]![The Edit Claim Rules... for Zscaler SAML in the Relying Party Trusts section.](/downloads/zia/authentication-administration/provisioning-authenticating-users/saml-scim/saml-configuration-guide-adfs-30/ADFS-Relying-Party-Trusts-Edit-Claim-Rules.png)
[]![The Edit Rule... button in the Edit Claim Rules window.](/downloads/zia/authentication-administration/provisioning-authenticating-users/saml-scim/saml-configuration-guide-adfs-30/ADFS-Edit-Claim-Rules-Edit-Rule.png)
[]![The memberOf group mapping removed in the Mapping of LDAP attributes to outgoing claim types field.](/downloads/zia/authentication-administration/provisioning-authenticating-users/saml-scim/saml-configuration-guide-adfs-30/ADFS-Edit-Rule-Remove-Group-LDAP-Attribute.png)
[]![The Add Rule... button in the Edit Claim Rules window.](/downloads/zia/authentication-administration/provisioning-authenticating-users/saml-scim/saml-configuration-guide-adfs-30/ADFS-Edit-Claim-Rules-Add-Rule-Groups.png)
[]![The Choose Rule Type step in the Add Transform Claim Rule Wizard.](/downloads/zia/authentication-administration/provisioning-authenticating-users/saml-scim/saml-configuration-guide-adfs-30/ADFS-Choose-Rule-Type.png)
[]![The configured Configure Claim Rule step in the Add Transform Claim Rule Wizard.](/downloads/zia/authentication-administration/provisioning-authenticating-users/saml-scim/saml-configuration-guide-adfs-30/ADFS-Configure-Claim-Rule-Return-Group-Membership.png?1617147266)
[]![The Add Rule... button in the Edit Claim Rules window.](/downloads/zia/authentication-administration/provisioning-authenticating-users/saml-scim/saml-configuration-guide-adfs-30/ADFS-Edit-Claim-Rules-Add-Rule-Groups2.png)
[]![The Choose Rule Type step in the Add Transform Claim Rule Wizard.](/downloads/zia/authentication-administration/provisioning-authenticating-users/saml-scim/saml-configuration-guide-adfs-30/ADFS-Choose-Rule-Type.png)
[]![The configured Configure Claim Rule step in the Add Transform Claim Rule Wizard.](/downloads/zia/authentication-administration/provisioning-authenticating-users/saml-scim/saml-configuration-guide-adfs-30/ADFS-Configure-Claim-Rule-Restrict-Group-Membership.png)
[]To configure SAML SSO in the ZIA Admin Portal:
- Go to **Administration **>** Authentication Settings**.
- Under **Authentication Frequency**,** **choose how often users are required to authenticate to the Zscaler service. To learn more, see [About Authentication Profile](/zia/about-authentication-profile#authentication-frequency). If you select **Custom**, the following field will appear:
- **Custom Authentication Frequency (days)**: Specify 1 to 180 days.
- Under** Authentication Type**, choose **SAML**.
[See image.](#seeimage-2c)
- Click **Save **and [activate the change](/zia/saving-and-activating-changes-admin-portal).
[]![The SAML option under Authentication Type on the Authentication Profile page.](/downloads/zia/authentication-administration/provisioning-authenticating-users/saml-scim/saml-configuration-guide-adfs-30/ZIA-Authentication-Profile-Authentication-Type-SAML.png)
[]To configure the Zscaler Authentication Exemptions list and enable users access to AD FS:
- Go to **Administration **>** Advanced Settings**.
- In the **Authentication Exemptions** section, enter your organization's AD FS URL in **Exempted URLs**.
[See image.](#seeimage7c)
- Click **Save** and [activate the change](/zia/saving-and-activating-changes-admin-portal).
If you are using PAC files, enter the AD FS URL in the [PAC file](/zia/using-default-pac-files-forward-traffic-zia) exemption list. Otherwise, the authentication will fail.
[]![The Exempted URLs field in the Authentication Exemptions section.](/downloads/zia/authentication-administration/provisioning-authenticating-users/saml-scim/saml-configuration-guide-adfs-30/ZIA-Authentication-Exemptions-Exempted%20URLs.png)