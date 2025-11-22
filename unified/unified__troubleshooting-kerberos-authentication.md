# Troubleshooting Kerberos Authentication
Source: https://help.zscaler.com/unified/troubleshooting-kerberos-authentication
PDF: https://help.zscaler.com/pdf/com/en/1491661.pdf

Kerberos authentication can be affected by some network configuration parameters, such as time synchronization. This article provides guidelines for troubleshooting Kerberos on your domain controller and on your users' devices.
There are four major components involved with Kerberos authentication:
- Your Zscaler cloud, which includes the Kerberos server (KDC), the Zscaler Central Authority (CA), and the Internet & SaaS Public Service Edge.
- Your domain controller, which includes a KDC configured to do cross-real authentication.
- Your users' devices, which are joined to your domain and have obtained cross-real settings from the domain controller through GPO.
- A network infrastructure which connects all three of the above components, includes switches, routers, firewalls, etc.
Zscaler recommends that you first troubleshoot Kerberos on your domain controller.
To learn more about using Kerberos for your organization, see [About Kerberos Authentication](/unified/about-kerberos-authentication).
[Troubleshooting on the Domain Controller]
Before troubleshooting, ensure that the administrator has been provisioned on the Zscaler service as a user so that Kerberos authentication doesn't fail.
To troubleshoot on your domain controller:
- Log in to your domain controller.
- Ensure that your domain controller has the correct time and date, because the Kerberos protocol uses timestamps. If the time and date settings on your domain controller differ from the Zscaler KDC by more than five minutes, authentication will fail.
- Configure the browser to use Zscaler cloud on port 8800, the default Kerberos authentication port on the Internet & SaaS Public Service Edges. Internet Explorer and Mozilla Firefox browsers support Kerberos authentication by default.
- Open [https://www.zscaler.com/](https://www.zscaler.com/). If the page is rendered properly, then the cross-realm settings are configured properly, and you can skip the next step and go to step 6.
- If the cross-realm settings are configured incorrectly, then the Internet & SaaS Public Service Edge displays a page with an error code. For more information about the error codes, see [Internet & SaaS Public Service Edge Error Codes for Kerberos](/unified/error-codes-kerberos-authentication).
- Open Microsoft PowerShell and run the command klist purge** **to clear the Kerberos ticket cache.
[See image.](#seeimage6)
- After clearing the Kerberos ticket cache, open [https://www.zscaler.com/](https://www.zscaler.com/).
- In Windows PowerShell, run the command klist. If the following three Kerberos ticket-granting tickets (krbtgt) are not displayed when you run klist, then there is an issue with the server of that ticket.
- **Zscaler KDC krbtgt ticket**:** **The user device obtains this ticket from your organization's domain controller. This ticket grants access to the Zscaler KDC. If this ticket is not displayed, then the configuration on your KDC may be incorrect. Please configure your KDC again.
- **Your company's KDC krbtgt ticket**: The user device obtains this ticket from your organization's domain controller. This ticket grants access to that domain controller. If this ticket is not displayed, then your company's internal KDC is not issuing Zscaler KDC tickets. Please contact your company's IT support.
- **Internet & SaaS Public Service Edge krbtgt ticket**: The user device obtains this ticket from the Zscaler KDC. This ticket grants access to the Internet & SaaS Public Service Edge. If this ticket is not displayed, then the Internet & SaaS Public Service Edge is not issuing tickets. Please contact Zscaler Support.
[See image.](#seeimage8)
-
In Windows PowerShell, run the command nltest /domain_trusts. The Zscaler domain must be in the domain trusts list as an inbound trust.
[See image.](#seeimage9)
Your Zscaler domain name is the same as your Zscaler cloud name. In this example, it is ZSCALERTWO.NET.
If you do not see the Zscaler domain in the domain trusts list, you must add it as a trusted domain. See [Create the New Trust](/unified/kerberos-trust-relationship-configuration-guide-windows-server-2012-gpo-push#create-new-trust) in *Kerberos Trust Relationship Configuration Guide for Windows Server 2012 and GPO Push*.
-
If the Zscaler KDC domain is registered correctly, you run the command ping kerberos.<Zscaler Cloud> in Windows PowerShell. The IP address displayed must be the Zscaler CA's IP address.
[See image.](#seeimage10)
If the Zscaler KDC domain has been configured incorrectly, reconfigure the KDC. For instructions, see [Kerberos Trust Relationship Configuration Guide for Windows Server 2012 and GPO Push](/unified/kerberos-trust-relationship-configuration-guide-windows-server-2012-gpo-push).
- To check cross-realm configuration:
- Log in to the Windows server as administrator. Open the Server Manager and go to **DNS**. From the Tools menu, choose **Active Directory Domains and Trusts**.
- Right-click on your domain and select **Properties**. In the Properties window, go to the **Trusts** tab.
-
Select the Zscaler domain, and then click **Properties**.
[See image.](#seeimg1)
If the Zscaler domain is not displayed, you must add the Zscaler domain as a trusted domain. See [Create the New Trust](/unified/kerberos-trust-relationship-configuration-guide-windows-server-2012-gpo-push#create-new-trust) in *Kerberos Trust Relationship Configuration Guide for Windows Server 2012 and GPO Push*.
-
Ensure that the option **The other domain support Kerberos AES Encryption** is enabled.
[See image.](#seeimg2)
There is no way to check the cross-realm password of an added trust. You must delete the domain trust and re-add the trust with the correct password.
- To validate the GPO configuration:
-
Open Windows PowerShell and enter the following command to list the GPO registry value for the Zscaler KDC:
get-gpregistryvalue -key "HKLM\SOFTWARE\Microsoft\Windows\CurrentVersion\Policies\System\Kerberos\MitRealms" -name "Default Domain Policy"
- Verify the following values:
- **ValueName**: <Zscaler Cloud>. In this example, the value is ZSCALERTWO.NET
- **Value**: <k>kerberos.<Zscaler Cloud></k>. In this example, the value is <k>kerberos.zscalertwo.net</k>.
[See image.](#seeimg3)
-
Enter the following command to list the GPO registry value for the Zscaler domain:
get-gpregistryvalue -key "HKLM\SOFTWARE\Microsoft\Windows\CurrentVersion\Policies\System\Kerberos\domain_realm" -name "Default Domain Policy"
-
Verify the following values:
- **ValueName**: <Zscaler Cloud>. In this example, the value is ZSCALERTWO.NET.
- **Value**: .<Zscaler Cloud>; .gateway.<Zscaler Cloud>. In this example, the value is .zscalertwo.net; .gateway.zscalertwo.net.
[See image.](#seeimg4)
If the correct values are not displayed, verify your configuration. For instructions, see [Kerberos Trust Relationship Configuration Guide for Windows Server 2012 and GPO Push](/unified/kerberos-trust-relationship-configuration-guide-windows-server-2012-gpo-push).
Troubleshooting on User Devices
It is possible for Kerberos authentication to work on the domain controller, but to not work on a user's device. In this case, there may be an error with the GPO settings. You must check if GPO settings have been propagated from the domain controller to users. See[ Configure GPO to Push the Configuration to Users](/unified/kerberos-trust-relationship-configuration-guide-windows-server-2012-gpo-push#configure-gpo-push-users) in *Kerberos Trust Relationship Configuration Guide for Windows Server 2012 and GPO Push*.
After configuring GPO to push the cross-realm trust to your users, complete step 6 of this article on your user's device to check for the cached Kerberos tickets. Then, complete the rest of the steps to finish troubleshooting on your user's device.
[]![Screenshot of the klist purge command in Windows PowerShell](/downloads/zia/documentation-knowledgebase/authenticating-and-managing-users/kerberos/kerberos-deployment-guide/troubleshooting-kerberos/klist_purge_command_in_windows_powershell.png)
[]![Screenshot of the Zscaler KDC krbtgt ticket, Your company's KDC krbtgt ticket, and the ZIA Public Service Edge krbtgt ticket in Windows PowerShell](/downloads/zia/documentation-knowledgebase/authenticating-and-managing-users/kerberos/kerberos-deployment-guide/troubleshooting-kerberos/the_zscaler_kdc_krbtgt_ticket,_your_company's_kdc_krbtgt_ticket,_and_the_zen_krbtgt_ticket_in_windows_powershell.png)
[]![Screenshot of the nltest /domain_trusts command and response in Windows PowerShell](/downloads/zia/documentation-knowledgebase/authenticating-and-managing-users/kerberos/kerberos-deployment-guide/troubleshooting-kerberos/43d5a2b4-6e3e-49ca-97ab-5f0f9d06fa05_display.png)
[]![Screenshot pinging the Zscaler KDC domain in Windows PowerShell](/downloads/zia/documentation-knowledgebase/authenticating-and-managing-users/kerberos/kerberos-deployment-guide/troubleshooting-kerberos/pinging_the_zscaler_kdc_domain_in_windows_powershell.png)
[]![Screenshot of the Properties... button in the Trusts tab](/downloads/zia/documentation-knowledgebase/authenticating-and-managing-users/kerberos/kerberos-deployment-guide/troubleshooting-kerberos/properties..._button_in_the_trusts_tab.png)
[]![Screenshot choosing The other domain support Kerberos AES Encryption option in the Properties window](/downloads/zia/documentation-knowledgebase/authenticating-and-managing-users/kerberos/kerberos-deployment-guide/troubleshooting-kerberos/the_other_domain_support_kerberos_aes_encryption_option_in_the_properties_window.png)
[]![Screenshot of the ValueName and Value fields for MitRealms](/downloads/zia/documentation-knowledgebase/authenticating-and-managing-users/kerberos/kerberos-deployment-guide/troubleshooting-kerberos/valuename_and_value_fields_for_mitrealms.png)
[]![Screenshot of the ValueName and Value fields for domain_realm](/downloads/zia/documentation-knowledgebase/authenticating-and-managing-users/kerberos/kerberos-deployment-guide/troubleshooting-kerberos/valuename_and_value_fields_for_domain_realm.png)