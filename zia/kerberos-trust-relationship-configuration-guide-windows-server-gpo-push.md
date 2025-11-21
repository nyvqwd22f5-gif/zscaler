# Kerberos Trust Relationship Configuration Guide for Windows Server & GPO Push
Source: https://help.zscaler.com/zia/kerberos-trust-relationship-configuration-guide-windows-server-gpo-push
PDF: https://help.zscaler.com/pdf/com/en/1399571.pdf

This configuration guide illustrates how to establish a one-way cross-realm trust from your organization's server to the Zscaler service. This one-way trust enables Zscaler to trust the authenticated users of the domain and NOT the reverse. Administrator access to the domain controller is required to establish a cross-realm trust and to use GPO to push configuration settings. To learn more about Kerberos, see [About Kerberos Authentication](/zia/about-kerberos-authentication). To learn more about deploying Kerberos, see [Deploying Kerberos Authentication](/zia/how-do-i-deploy-kerberos).
In this guide:
- The KDC in the organization's realm is Windows Server configured as a Domain Controller
- The Windows client is running Windows 8.1 and is joined to the domain
- The domain user, Jane Doe, can log in to the Windows client using domain credentials
- The Zscaler domain is the Zscaler cloud name. In this example, it is ZSCALERBETA.NET. To learn how you can find your cloud name, see [What is my cloud name for ZIA?](/zia/what-my-cloud-name-zia)
![Kerberos Trust Relationship Configuration Guide Diagram](/downloads/zia/authentication-administration/user-management-authentication-settings/kerberos-authentication/kerberos-trust-relationship-configuration-guide-windows-server-2012-gpo-push/ZIA-Kerberos-Trust-Relationship-Diagram.png)
Configure the Cross-Realm Trust on Windows Server
This section describes how to configure the KDC and the Active Directory GPO feature on a Windows Server. For information on Active Directory GPO and GPMC, refer to the Windows Active Directory and GPMC documentation.
To configure the cross-realm trust on Windows Server:
- [1. Create the New Trust](#create-new-trust)
- [2. Configure the Trust Properties](#configure-trust-properties)
- [3. Validate the Settings](#validate-settings)
- [4. Configure GPO to Push the Configuration to Users](#configure-gpo-push-users)
- [5. Validate the GPO Configuration](#validate-gpo-configuration)
- [6. Configure the Windows Workstation](#configure-windows-workstation)
Troubleshooting
To troubleshoot your Kerberos configuration, see [Troubleshooting Kerberos](/zia/troubleshooting-kerberos) and [ZIA Public Service Edge Error Codes for Kerberos](/zia/zen-error-codes-kerberos).
The following are some helpful Microsoft documents:
- [Setting Kerberos Realm Flags](https://docs.microsoft.com/en-us/windows-server/administration/windows-commands/ksetup-setrealmflags)
- [Forcing Kerberos to Use TCP Instead of UDP](https://support.microsoft.com/en-us/help/244474/how-to-force-kerberos-to-use-tcp-instead-of-udp-in-windows)
[]Log in to the Windows server as administrator. Open the Server Manager and do the following:
- Go to **DNS** and from the Tools menu, choose **Active Directory Domains and Trusts**.
[See image.](#seeimage1)
- In the Active Directory Domains and Trusts window, hover over your domain, right-click and select **Properties**.
[See image.](#seeimage2)
- In the Properties window, go to the **Trusts** tab and click **New Trust**.
[See image.](#seeimage3)
- When the New Trust wizard appears, click **Next**.
- For **Trust Name**, enter the [Zscaler cloud name](/zia/what-my-cloud-name) in uppercase letters and click **Next**.
You can find your cloud name by looking at the URL you use to log in to the ZIA Admin Portal. For example, if you log in to [https://admin.zscalerbeta.net/](https://admin.zscalerbeta.net/), your cloud name is ZSCALERBETA.NET as shown in the following image.
[See image.](#seeimage4)
- For **Trust Type**, select **Realm trust** and click **Next**.
[See image.](#seeimage5)
- For **Transitivity of Trust**, select **Nontransitive** and click **Next**.
[See image.](#seeimage6)
- For **Direction of Trust**, select **One-way: incoming** and click **Next**.
[See image.](#seeimage7)
- For **Trust Password**, paste the password that you copied from Zscaler.
[See image.](#seeimage8)
- When the Wizard displays your settings, verify them and click **Next**.
[See image.](#seeimage9)
[]Configure the properties of the newly configured trust.
- Open the Properties window of your domain.
[See image.](#seeimage10)
- In the Properties windows, select the following and click **OK**:
- **The other domain supports Kerberos AES Encryption**.
- **Non-transitive: only users from the directly trusted domain may authenticate in the trusting domain.**
[See image.](#seeimage11)
[]Ensure that your configuration is correct before you proceed to the next step.
- On the Windows server, open the Windows PowerShell and enter the following command. Replace `Zscaler Cloud` with the name of the Zscaler cloud that you use.
Get-ADObject -Filter {trustPartner -eq "`Zscaler Cloud`"} -Properties *
- Ensure that the following values are displayed:
- **CN**: Zscaler cloud name (In this example, it is ZSCALERBETA.NET).
- **msDS-SupportedEncryptionTypes**:** **24
- **Name**: Zscaler cloud name (In this example, it is ZSCALERBETA.NET).
- **objectClass**:** **trustedDomain
- **trustAttributes**:** **1
- **trustDirection**:** **1
- **trustPartner**: Zscaler cloud name (In this example, it is ZSCALERBETA.NET).
- **trustType**: 3
[See image.](#seeimage12)
[]On the Windows server, open the Server Manager and do the following:
- Go to the Dashboard, and from the **Tools** menu, select **Group Policy Management**.
[See image.](#seeimage13)
- Go to **Group Policy Management** > **Forest** > **Domains** > Domain Name > **Default Domain Policy**, right-click and select **Edit**.
[See image.](#seeimage14)
- On the Group Policy Management Editor, go to **Computer Configuration **>** Policies **>** Administrative Templates **>** System **>** Kerberos** and from the Settings panel, select **Define Interoperable Kerberos V5 realm settings**.
[See image.](#seeimage15)
- In the **Define interoperable Kerberos V5 realm settings** window, select **Enabled** and click **Show...**.
[See image.](#seeimage16)
- In the **Show Contents** window:
- **Value name**: Enter the Zscaler cloud name (In this example, it is ZSCALERBETA.NET).
- **Value**: Enter `<k>kerberos.``Zscaler Cloud``</k>`. In this example, the value is `<k>kerberos.zscalerbeta.net</k>`.
[See image.](#seeimage17)
- Click **OK**, and then click **OK** in the **Define interoperable Kerberos V5 realm settings** window.
- Select **Define host name-to-Kerberos realm mappings**.
[See image.](#seeimage18)
- In the **Define host name-to-Kerberos realm mappings** window, select **Enabled** and click **Show...**.
[See image.](#seeimage19)
- In the **Show Contents** window:
- **Value name**: Enter the Zscaler cloud name. In this example, it is ZSCALERBETA.NET.
- **Value**: Enter the Zscaler domain names. In this example, it is .zscalerbeta.net; .gateway.zscalerbeta.net.
[See image.](#seeimage20)
Both the domain names must have leading dots to match all subdomains.
- Click **OK**, click **OK** in the **Define host name-to-Kerberos realm mappings** window, and close the **Group Policy Management Editor**.
- Go to **Group Policy Management** > **Default Domain Policy **and click the **Settings** tab.
[See image.](#seeimage21)
- Expand **Computer Configuration** > **Administrative Templates** > **System/Kerberos** and verify each policy.
- Scroll to the next policy.
[]To validate the GPO configuration:
- Open the Windows PowerShell and enter the following command to list the GPO registry value for the Zscaler KDC:
get-gpregistryvalue -key "HKLM\SOFTWARE\Microsoft\Windows\CurrentVersion\Policies\System\Kerberos\MitRealms" -name "Default Domain Policy"
- Verify the following values:
- **ValueName**: ZSCALERBETA.NET
- **Value**: kerberos.zscalerbeta.net
[See image.](#seeimage24)
- Enter the following command to list the GPO registry value for the Zscaler domain:
get-gpregistryvalue -key "HKLM\SOFTWARE\Microsoft\Windows\CurrentVersion\Policies\System\Kerberos\domain_realm" -name "Default Domain Policy"
- Verify the following values:
- **ValueName**: ZSCALERBETA.NET
- **Value**: .zscalerbeta.net; .gateway.zscalerbeta.net
[See image.](#seeimage25)
[]Log in to the Windows workstation, open the command prompt, and run the following commands:
klist ensures that you are logged in to the domain and can contact the domain controller. It displays the Kerberos tickets that were used by the workstation to log in to the domain. If, when you run klist, the Kerberos tickets are not displayed, then there is an inherent domain or workstation configuration issue that must be resolved before you proceed.
![Screenshot of the the klist command and response in Command Prompt ](/downloads/zia/documentation-knowledgebase/authenticating-and-managing-users/kerberos/kerberos-deployment-guide/kerberos-configuration-example-trust-relationship-windows-server-2012-and-gpo-push/klist_command_and_response_in_command_prompt.png)
gpupdate /force
![Screenshot of the gpupdate /force command and response in Command Prompt](/downloads/zia/documentation-knowledgebase/authenticating-and-managing-users/kerberos/kerberos-deployment-guide/kerberos-configuration-example-trust-relationship-windows-server-2012-and-gpo-push/88141b04-0a84-4798-9bca-f47b42bb07bb_display.png)
You can verify that the Zscaler Kerberos settings have been synchronized to the client and that the registry was updated by doing one of the following:
- Run the following queries in the Windows command prompt or the Windows Powershell:
reg query
HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows\CurrentVersion\Policies\System\Kerberos\domain_realm
![Screenshot running the domain_realm query in Command Prompt](/downloads/zia/documentation-knowledgebase/authenticating-and-managing-users/kerberos/kerberos-deployment-guide/kerberos-configuration-example-trust-relationship-windows-server-2012-and-gpo-push/domain_realm_query_in_command_prompt.png)
reg query
HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows\CurrentVersion\Policies\System\Kerberos\MitRealms
![Screenshot running a query in Command Prompt](/downloads/zia/documentation-knowledgebase/authenticating-and-managing-users/kerberos/kerberos-deployment-guide/kerberos-configuration-example-trust-relationship-windows-server-2012-and-gpo-push/mitrealms_query_in_command_prompt.png)
OR
- Open the Registry editor and verify the **domain_realm** entries, as shown next.
![Screenshot of the domain_realm entries in the Registry Editor window](/downloads/zia/documentation-knowledgebase/authenticating-and-managing-users/kerberos/kerberos-deployment-guide/kerberos-configuration-example-trust-relationship-windows-server-2012-and-gpo-push/the_domain_realm_entries_in_the_registry_editor_window.png)
Verify the **MitRealms **entries as shown next.
![Screenshot of the MitRealms entries in the Registry Editor window](/downloads/zia/documentation-knowledgebase/authenticating-and-managing-users/kerberos/kerberos-deployment-guide/kerberos-configuration-example-trust-relationship-windows-server-2012-and-gpo-push/the_mitrealms_entries_in_the_registry_editor_window.png)
Ensure that the browser is configured with the Kerberos PAC file URL.
![Screenshot of the Local Area Network (LAN) Settings window](/downloads/zia/documentation-knowledgebase/authenticating-and-managing-users/kerberos/kerberos-deployment-guide/kerberos-configuration-example-trust-relationship-windows-server-2012-and-gpo-push/local_area_network_(lan)_settings_window.png)
Open the browser and browse to a site to ensure that you are not challenged for authentication or that the browser displays an “Internet Access Denied” error page.
[]![Screenshot of the Active Directory Domains and Trusts option in the Tools menu](/downloads/zia/authentication-administration/user-management-authentication-settings/kerberos-authentication/kerberos-trust-relationship-configuration-guide-windows-server-2012-gpo-push/01.a2%20active_directory_domains_and_trusts.png)
[]![Screenshot of the Properties option for your Active Directory domain](/downloads/zia/authentication-administration/user-management-authentication-settings/kerberos-authentication/kerberos-trust-relationship-configuration-guide-windows-server-2012-gpo-push/01.b2%20properties_option_for_your_active.png)
[]![Screenshot of the New Trust... button in the Trusts tab](/downloads/zia/authentication-administration/user-management-authentication-settings/kerberos-authentication/kerberos-trust-relationship-configuration-guide-windows-server-2012-gpo-push/01.c2%20new_trust..._button_in_the_trusts.png)
[]![Screenshot of the Name field under Trust Name ](/downloads/zia/authentication-administration/user-management-authentication-settings/kerberos-authentication/kerberos-trust-relationship-configuration-guide-windows-server-2012-gpo-push/01.e2%20name_field_under_trust_name.png)
[]![Screenshot choosing Realm trust for the Trust Type](/downloads/zia/authentication-administration/user-management-authentication-settings/kerberos-authentication/kerberos-trust-relationship-configuration-guide-windows-server-2012-gpo-push/01.f2%20realm_trust_for_the_trust_type.png)
[]![Screenshot choosing Nontransitive for the Transitivity of Trust](/downloads/zia/authentication-administration/user-management-authentication-settings/kerberos-authentication/kerberos-trust-relationship-configuration-guide-windows-server-2012-gpo-push/01.g2%20nontransitive.png)
[]![Screenshot choosing One-way: incoming for the Direction of Trust](/downloads/zia/authentication-administration/user-management-authentication-settings/kerberos-authentication/kerberos-trust-relationship-configuration-guide-windows-server-2012-gpo-push/01.h2%20one-way__incoming_for_the_direction.png)
[]![admin password in zscaler admin portal](/downloads/zia/authentication-administration/user-management-authentication-settings/kerberos-authentication/kerberos-trust-relationship-configuration-guide-windows-server-2012-gpo-push/01.i2%20domain_trust_password_in_the_zscaler_admin.png)
[]![Screenshot of the Trust Selections Complete section in the New Trust Wizard](/downloads/zia/documentation-knowledgebase/authenticating-and-managing-users/kerberos/kerberos-deployment-guide/kerberos-configuration-example-trust-relationship-windows-server-2012-and-gpo-push/trust_selections_complete_section_in_the_new_trust_wizard.png)
[]![Screenshot of the Properties... button in the Trusts tab](/downloads/zia/authentication-administration/user-management-authentication-settings/kerberos-authentication/kerberos-trust-relationship-configuration-guide-windows-server-2012-gpo-push/02.a2%20properties..._option_in_the_trusts_tab.png)
[]![Zscaler domain properties](/downloads/zia/authentication-administration/user-management-authentication-settings/kerberos-authentication/kerberos-trust-relationship-configuration-guide-windows-server-2012-gpo-push/02.b2%20the_other_domain_supports_kerberos_aes_encryption.png)
[]![Screenshot of the following values in Windows PowerShell: CN, msDS-SupportedEncryptionTypes, Name, objectClass, trustAttributes, trustDirection, trustPartner, trustType](/downloads/zia/documentation-knowledgebase/authenticating-and-managing-users/kerberos/kerberos-deployment-guide/kerberos-configuration-example-trust-relationship-windows-server-2012-and-gpo-push/the_cn,_msds-supportedencryptiontypes,_name,_objectclass,_trustattributes,_trustdirection,_trustpartner,_and_trusttype_values_in_windows_powershell.png)
[]![Screenshot of the Group Policy Management option in the Tools menu](/downloads/zia/authentication-administration/user-management-authentication-settings/kerberos-authentication/kerberos-trust-relationship-configuration-guide-windows-server-2012-gpo-push/04.a2%20group_policy_management_option_in_the_tools_menu.png)
[]![Screenshot of the Edit... option for Default Domain Policy](/downloads/zia/authentication-administration/user-management-authentication-settings/kerberos-authentication/kerberos-trust-relationship-configuration-guide-windows-server-2012-gpo-push/04.b2%20edit..._option_for_default_domain_policy.png)
[]![Screenshot of Define Interoperable Kerberos V5 realm settings in the Group Policy Management Editor window](/downloads/zia/documentation-knowledgebase/authenticating-and-managing-users/kerberos/kerberos-deployment-guide/kerberos-configuration-example-trust-relationship-windows-server-2012-and-gpo-push/define_interoperable_kerberos_v5_realm_settings_in_the_group_policy_management_editor_window.png)
[]![Define interoperable Kerberos VS realm settings](/downloads/zia/authentication-administration/user-management-authentication-settings/kerberos-authentication/kerberos-trust-relationship-configuration-guide-windows-server-2012-gpo-push/04.d2%20enabled_setting_%26_show..._button.png)
[]![seeimage#17 kerberos realm settings](/downloads/zia/documentation-knowledgebase/authenticating-and-managing-users/kerberos/kerberos-trust-relationship-configuration-guide-windows-server-2012-gpo-push/ZIA-Kerberos-trust-value.png)
[]![Screenshot of the Define host name-to-Kerberos realm mappings setting in the Group Policy Management Editor window](/downloads/zia/authentication-administration/user-management-authentication-settings/kerberos-authentication/kerberos-trust-relationship-configuration-guide-windows-server-2012-gpo-push/04.g2%20define_host_name-to-kerberos_realm_mappings_setting.png)
[]![Define host name-to-Kerberos realm mappings](/downloads/zia/authentication-administration/user-management-authentication-settings/kerberos-authentication/kerberos-trust-relationship-configuration-guide-windows-server-2012-gpo-push/04.h2%20enabled_setting_%26_show..._button.png)
[]![Screenshot of the Value name and Value fields in the Show Contents window](/downloads/zia/documentation-knowledgebase/authenticating-and-managing-users/kerberos/kerberos-deployment-guide/kerberos-configuration-example-trust-relationship-windows-server-2012-and-gpo-push/value_name_&_value_fields_in_the_show_contents_window.png)
[]![Screenshot of the Settings tab for Default Domain Policy](/downloads/zia/documentation-knowledgebase/authenticating-and-managing-users/kerberos/kerberos-deployment-guide/kerberos-configuration-example-trust-relationship-windows-server-2012-and-gpo-push/settings_tab_for_default_domain_policy.png)
[]![Screenshot of the Define host name-to-Kerberos realm mappings setting in the Group Policy Management Editor window](/downloads/zia/authentication-administration/user-management-authentication-settings/kerberos-authentication/kerberos-trust-relationship-configuration-guide-windows-server-2012-gpo-push/04.g2%20define_host_name-to-kerberos_realm_mappings_setting.png)
[]![Screenshot of the Define interoperable Kerberos V5 realm settings policy under System/Kerberos](/downloads/zia/documentation-knowledgebase/authenticating-and-managing-users/kerberos/kerberos-deployment-guide/kerberos-configuration-example-trust-relationship-windows-server-2012-and-gpo-push/define_interoperable_kerberos_v5_realm_settings_in_the_group_policy_management_editor_window.png)
[]![Screenshot of the ValueName and Value fields for MitRealms](/downloads/zia/authentication-administration/user-management-authentication-settings/kerberos-authentication/kerberos-trust-relationship-configuration-guide-windows-server-2012-gpo-push/05.b2%20value_name_and_value_fields_for_mitrealms.png)
[]![Screenshot of the ValueName and Value fields for domain_realm](/downloads/zia/documentation-knowledgebase/authenticating-and-managing-users/kerberos/kerberos-deployment-guide/kerberos-configuration-example-trust-relationship-windows-server-2012-and-gpo-push/valuename_and_value_fields_for_domain_realm.png)