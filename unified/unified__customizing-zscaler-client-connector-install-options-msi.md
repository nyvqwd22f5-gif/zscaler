# Customizing Zscaler Client Connector with Install Options for MSI
Source: https://help.zscaler.com/unified/customizing-zscaler-client-connector-install-options-msi
PDF: https://help.zscaler.com/pdf/com/en/1491916.pdf

You can use the MSI file to manually install Zscaler Client Connector on a device or if you're deploying the app to your users using GPO, SCCM, or other device management methods that support MSI files. After downloading the Zscaler Client Connector MSI installer file in the [Admin Portal](/unified/about-zscaler-client-connector-app-store), you can deploy the file as is with your device management method. If you want to customize the MSI file and add install options (for example, to enable strict enforcement), you must first create an MST file.
You can also add to the file install options to customize the app for your organization using one of the following methods:
- [Creating an MST and Deploying it Using GPO or a Compatible Device Management Tool](#CreateZAppMSTFile)
- [Running the MSI with CLI Options](#RunZAppMSICmdLine)
- [Deploying Zscaler Client Connector with Non-Persistent Citrix VDIs](#InstallVDI)
[]Orca.exe is available in the [Microsoft Windows Software Development Kit (SDK)](https://developer.microsoft.com/en-us/windows/downloads/windows-10-sdk). To learn more, refer to the [Microsoft documentation](https://learn.microsoft.com/en-us/windows/win32/msi/orca-exe).
Windows installers use an MST file to enable customized installations of an original MSI package during installation. You can create an MST file and then deploy it to users using a Group Policy Object (GPO) or a compatible device management tool such as Microsoft Intune or Jamf Pro.
To create an MST file using Orca:
- Open Orca and go to **File** > **Open**.
- Locate and double-click the MSI file.
- Go to** Transform** > **New Transform**.
![Clicking the New Transform option to create a MST file for Zscaler Client Connector](/downloads/z-app/downloading-deployment/customizing-zscaler-app-install-options-msi/Zscaler-App-MSI-New-Transform.png)
- In the **Tables** column, click **Property**.
![The Zscaler Client Connector MSI file properties](/downloads/z-app/downloading-deployment/customizing-zscaler-app-install-options-msi/Zscaler-App-MSI-Property.png)
-
Edit the values for the following install options or add more options:
- [CLOUDNAME](#cn)
- [DEVICETOKEN](#dt)
- [HIDEAPPUIONLAUNCH](#hideapp)
- [POLICYTOKEN](#pt)
- [REINSTALLDRIVER](#reinstall)
- [STRICTENFORCEMENT](#se)
- [UNINSTALLPASSWORDCMDLINE](#uninstallpw)
- [USERDOMAIN](#ud)
- [UNAME](#uname-mst)
- [ENABLEANTITAMPERING](#enable-at)
- [EXTERNALDEVICEID](#externaldeviceid)
- [ENABLEIMPRIVATAINTEGRATION](#imprivata2)
- [BCPCONFIGFILEPATH](#bcpconfigfile)
- [BCPMAPUBKEYHASH](#bcpmapubkeyhash)
To modify any of these parameters post-installation, app reinstallation with the new values is required.
- To save your changes after adding the options you want, go to **Transform** > **Generate Transform...**
![The Generate Transform option to create a MST file for Zscaler Client Connector](/downloads/z-app/downloading-deployment/customizing-zscaler-app-install-options-msi/Zscaler-App-MSI-Generate-Transform.png)
- In the **Save Transform As** window, enter a file name and click **Save**.
![Saving the Zscaler Client Connector MST file](/downloads/z-app/downloading-deployment/customizing-zscaler-app-install-options-msi/Zscaler-App-MSI-Saving.png?1602182163)
After creating the MST, you can use it when [deploying Zscaler Client Connector to your users with Active Directory](/unified/deploying-zscaler-client-connector-active-directory-windows).
[]If your organization is provisioned on more than one cloud, your users are asked to select the cloud where their traffic is sent during the enrollment process.
[See image.](#cnimage)
With this install option, you can specify the cloud where the app sends user traffic so your users don't have to make the selection during enrollment. This option is not needed if your organization is provisioned on one cloud. The app automatically sends traffic to the proper cloud and your users don't need to make a selection during enrollment.
This install option is required if you enable the [STRICTENFORCEMENT](/zscaler-client-connector/customizing-zscaler-app-install-options-msi#se) option.
To add the CLOUDNAME install option:
- Click **Tables** from the top menu, and then click **Add Row**.
-
In the **Add Row** window:
- For **Property**, enter** **`CLOUDNAME`.
- Press `Enter` or click the **Value** field.
- For **Value**, enter the name of the cloud where your organization is provisioned in lowercase letters. For example, if your cloud name is zscalertwo.net, you'd enter zscalertwo.
![Adding the CLOUDNAME install option for the Zscaler Client Connector MST file](/downloads/z-app/downloading-deployment/customizing-zscaler-app-install-options-msi/CLOUDNAME-Add-Row-Window.png)
-
Click **OK**.
The install option appears on a new line.
![CLOUDNAME install option for the Zscaler Client Connector MST file](/downloads/z-app/downloading-deployment/customizing-zscaler-app-install-options-msi/CLOUDNAME-Zscaler-App-MSI.png)
[]![Selecting a cloud on the Zscaler Client Connector](/downloads/zia/documentation-knowledgebase/forwarding-your-traffic/zscaler-app/downloading-and-deploying-zscaler-app/customizing-zscaler-app-install-options-msi/73c7ab73-95fe-4542-8ab4-499a40f650ef.png)
[]The DEVICETOKEN install option only applies to Internet & SaaS. It is not supported by Private Applications.
This install option allows you to use Zscaler Client Connector as an IdP. The Zscaler service silently provisions and authenticates users even if you don't have an authentication mechanism in place. Before adding this option, you must generate a device token in the Admin Portal and complete the full configuration described in [Using Zscaler Client Connector as an IdP](/unified/using-zscaler-client-connector-identity-provider).
To add the DEVICETOKEN install option:
- Click **Tables** from the top menu, and then click **Add Row**.
- In the **Add Row** window:
- For **Property**, enter** **`DEVICETOKEN`.
- Press `Enter` or click the **Value** field.
-
For **Value**, enter the appropriate device token from the Admin Portal. To learn more, see [Using Zscaler Client Connector as an IdP](/unified/using-zscaler-client-connector-identity-provider).
[See image.](#device-token-image)
-
Click **OK**.
![Adding the DEVICETOKEN install option for the Zscaler Client Connector MST file](/downloads/z-app/downloading-deployment/customizing-zscaler-app-install-options-msi/DEVICETOKEN-Add-Row-Window.png)
The install option appears on a new line.
![DEVICETOKEN install option for the Zscaler Client Connector MST file](/downloads/z-app/downloading-deployment/customizing-zscaler-app-install-options-msi/DEVICETOKEN-Zscaler-App-MSI.png)
[]![Device Token from the Zscaler Client Connector Portal](/downloads/z-app/downloading-deployment/customizing-zscaler-app-install-options-msi/Device-Token-Zscaler-App-Portal.png)
[]This install option forces the app window to stay hidden before users enroll. Users can always open the window by clicking the app icon in the system tray.
To enable the HIDEAPPUIONLAUNCH install option:
- In the table, double-click on the **HIDEAPPUIONLAUNCH** value.
- Enter `1` as the value. By default, the value is 0 (i.e., disabled).
![HIDEAPPUIONLAUNCH install option for the Zscaler Client Connector MST file](/downloads/z-app/downloading-deployment/customizing-zscaler-app-install-options-msi/HIDEAPPUIONLAUNCH-Zscaler-App-MSI.png)
[]This install option allows you to specify which app profile policy you want to enforce for the app before the user enrolls. All relevant settings associated with the policy apply, including the bypass of the IdP login page. After the user enrolls, this policy is replaced with an app profile policy that matches the user based on group affiliation.
Prerequisites:
- This install option is only applicable and required if:
- You enable the [STRICTENFORCEMENT](/zscaler-client-connector/customizing-zscaler-app-install-options-msi#se2) option and want users to enroll with the app before accessing the internet.
- If you configure the machine tunnel and you want the users to access Private Applications before logging in to the device.
To add the POLICYTOKEN install option:
- Click **Tables** from the top menu, and then click **Add Row**.
- In the **Add Row** window:
- For **Property**, enter** **`POLICYTOKEN`.
- Press `Enter` or click the **Value** field.
-
For **Value**, enter the policy token associated with the policy you want to enforce before enrollment. To learn more, see [Configuring Zscaler Client Connector App Profiles](/unified/configuring-zscaler-client-connector-app-profiles).
[See image.](#policy-token-image)
-
Click **OK**.
![Adding the POLICYTOKEN install option for the Zscaler Client Connector MST file](/downloads/z-app/downloading-deployment/customizing-zscaler-app-install-options-msi/POLICYTOKEN-Add-Row-Window.png)
The install option appears on a new line.
![POLICYTOKEN install option for the Zscaler Client Connector MST file](/downloads/z-app/downloading-deployment/customizing-zscaler-app-install-options-msi/POLICYTOKEN-Zscaler-App-MSI.png)
[]![Policy Token from the Zscaler Client Connector Portal](/downloads/z-app/downloading-deployment/customizing-zscaler-app-install-options-msi/Policy-Token-Zscaler-App-Portal.png)
[]This install option forces a reinstallation of the driver, even if you already have a driver installed. Use this option if you're having issues with your current driver.
To enable the REINSTALLDRIVER install option:
- In the table, double-click the **REINSTALLDRIVER** value.
- Enter `1` as the value. By default, the value is 0 (i.e., disabled).
![Adding the REINSTALLDRIVER install option for the Zscaler Client Connector MST file](/downloads/z-app/downloading-deployment/customizing-zscaler-app-install-options-msi/REINSTALLDRIVER-Zscaler-App-MSI.png)
[]This install option only works when the forwarding profile action for Zscaler Client Connector is **Tunnel** or **Tunnel with Local Proxy**. To learn more, see [Configuring Forwarding Profiles for Zscaler Client Connector](/unified/configuring-forwarding-profiles-zscaler-client-connector).
This install option allows you to require users to enroll with the app before accessing the internet and blocks traffic in the following situations:
- The user has not yet logged in after a new install.
- A user logs in and logs out.
- An administrator removes a device.
This install option does not affect users that remain logged in and disable the Internet & SaaS service.
If you enable this install option, the --cloudName and --policyToken options are required.
To enable this option using the CLI, enter `STRICTENFORCEMENT=1`. By default, the value is 0 (i.e., disabled).
![Adding the STRICTENFORCEMENT install option for the Zscaler Client Connector MST file](/downloads/z-app/downloading-deployment/customizing-zscaler-app-install-options-msi/STRICTENFORCEMENT-Zscaler-App-MSI.png)
[]This install option allows you to silently uninstall the app from users' devices using device management methods like GPO. This option is only available when using MSI. The password you add for this option must match the uninstall **Password** [configured for access in unattended mode](/unified/configuring-passwords-access-unattended-mode). Using the password, you can uninstall the app from your users' devices by removing the MST file from the GPO.
Prerequisites:
- Your users must be enrolled in the app. If users have the app installed on their devices but have not enrolled, you cannot uninstall the app using this method.
- You must have an **Uninstall Password** enabled and an unexpired uninstall password generated. To learn more, see [Configuring Passwords for Access in Unattended Mode](/unified/configuring-passwords-access-unattended-mode).
To add the UNINSTALLPASSWORDCMDLINE install option:
- Click **Tables** from the top menu, and then click **Add Row**.
- In the **Add Row** window:
- For **Property**, enter** **`UNINSTALLPASSWORDCMDLINE`.
- Press `Enter` or click the **Value** field.
- For **Value**, enter the uninstall **Password **[configured for access in unattended mode](/unified/configuring-passwords-access-unattended-mode).
-
Click **OK**.
![Adding the UNINSTALLPASSWORD install option for the Zscaler Client Connector MST file](/downloads/client-connector/downloading-deployment/customizing-zscaler-app-install-options-msi/UNINSTALLPASSWORDCMDLINE-Add-Row-Window_0.png)
The install option appears on a new line.
![UNINSTALLPASSWORD install option for the Zscaler Client Connector MST file](/downloads/client-connector/downloading-deployment/customizing-zscaler-app-install-options-msi/UNINSTALLPASSWORDCMDLINE-MSI-Install-Option.png)
The uninstall password for unattended mode is available only in Zscaler Client Connector version 4.2.1 for Windows or later. If you use an earlier version or you prefer to use the password configured in the [app profile](/unified/configuring-zscaler-client-connector-app-profiles), enter the following in the **Add Row** window:
- A **Property **of `UNINSTALLPASSWORD`
- A **Value** of the **Uninstall Password** configured in the [app profile](/unified/configuring-zscaler-client-connector-app-profiles).
[]This install option allows users to skip the app enrollment page. If SSO is enabled for your organization, users are taken directly to your organization's SSO login page. If you've integrated SSO with the app (i.e., using a mechanism like Integrated Windows Authentication [IWA]), users can also skip the SSO login page and are automatically enrolled with Zscaler service and logged in.
[See image.](#udimage)
To add the USERDOMAIN install option:
- Click **Tables** from the top menu, and then click **Add Row**.
- In the **Add Row** window:
- For **Property**, enter** **`USERDOMAIN`.
- Press `Enter` or click the **Value** field.
- For **Value**, enter your organization's domain name. If your instance has multiple domains associated with it, enter the primary domain for your instance. The primary domain is only valid if you are using a single IdP with multiple domains. The primary domain won’t work if you have multiple domains across multiple IdPs.
-
Click **OK.**
.![Adding the USERDOMAIN install option for the Zscaler Client Connector MST file](/downloads/z-app/downloading-deployment/customizing-zscaler-app-install-options-msi/USERDOMAIN-Add-Row-Window.png)
The install option appears on a new line.
![USERDOMAIN install option for the Zscaler Client Connector MST file](/downloads/z-app/downloading-deployment/customizing-zscaler-app-install-options-msi/USERDOMAIN-Zscaler-App-MSI.png)
[]You can specify a unique username for each device using the UNAME parameter in the CLI.
The following conditions apply:
- The UNAME parameter requires the userDomain parameter to be non-empty.
- The UNAME parameter can have a maximum of 255 alphanumeric and special characters.
To add the UNAME install option:
- Click **Tables** from the top menu, and then click **Add Row**.
- In the **Add Row** window:
- For **Property**, enter** **`UNAME`.
- Press `Enter` or click the **Value** field.
- For **Value**, enter `test`.
-
Click **OK**.
![Add the UNAME install option for the Zscaler Client Connector MST file](/downloads/tech-pubs-drafts/client-connector-draft-articles/customizing-zscaler-client-connector-install-options-msi-draft-0/UNAME-add-row.png?1661983700)
The install option appears on a new line.
![UNAME install option for the Zscaler Client Connector MST file](/downloads/tech-pubs-drafts/client-connector-draft-articles/customizing-zscaler-client-connector-install-options-msi-draft-0/UNAME-add%20property-value.png)
[]This install option enables [integration with Imprivata OneSign](/unified/zscaler-client-connector-and-imprivata-integration). If enabled, Zscaler Client Connector silently logs in an Imprivata OneSign user to Zscaler Client Connector, applies security policies, and logs the end user activity in Zscaler Client Connector.
- In the table, double-click the **ENABLEIMPRIVATAINTEGRATION** value.
- Enter `1` as the value. By default, the value is 0 (i.e., disabled).
![ENABLEIMPRIVATAINTEGRATION install option](/downloads/client-connector/downloading-deployment/customizing-zscaler-app-install-options-msi/zscaler-client-connector-orca-install-imprivata.png)
[]![The Zscaler Client Connector enrollment page and an organization SSO login page](/downloads/zia/documentation-knowledgebase/forwarding-your-traffic/zscaler-app/downloading-and-deploying-zscaler-app/customizing-zscaler-app-install-options-msi/ee569ae8-2732-45b8-b0a6-33ceff3b1efc.png?1602182648)
[]This install option prevents end users from stopping, modifying, and deleting Zscaler products and services.
To add the ENABLEANTITAMPERING install option:
- Click **Tables** from the top menu, and then select the `ENABLEANTITAMPERING` property.
- For** Value**, replace the `0` with a `1`.
[![ENABLEANTITAMPERING install option for the Zscaler Client Connector MST file](/downloads/tech-pubs-drafts/client-connector-draft-articles/customizing-zscaler-client-connector-install-options-msi-draft-doc-51334/msi-enable-at-install-option.png)
](/downloads/client-connector/downloading-deployment/customizing-zscaler-app-install-options-msi/msi-enable-at-install-option.png)
[]The identifier that associates an external MDM device ID with devices in the Admin Portal. You can use this to associate devices in an MDM solution with devices in the Admin Portal.
To enable this option using the CLI, enter `--externalDeviceId `. By default, the value is 0 (i.e., disabled).
The `--externalDeviceId` parameter is not supported on Zscaler Client Connector version 4.1 and earlier for macOS and on Zscaler Client Connector version 4.0 and earlier for Windows.
[]This install option allows you to install Zscaler Client Connector to enroll new users during a Private Applications-related cloud outage or Internet Service Provider (ISP) outage. You can pass a predownloaded configuration file with Business Continuity settings from the Admin Portal. To learn more, see [About Business Continuity](/unified/about-business-continuity).
If you pass this install option, you must also pass the BCPMAPUBKEYHASH option.
To add the BCPCONFIGFILEPATH install option:
- Click **Tables** from the top menu, and then click **Add Row**.
- In the **Add Row** window:
- For **Property**, enter** **`BCPCONFIGFILEPATH`.
- Press `Enter` or click the **Value** field.
- For **Value**, enter the path to the configuration file.
-
Click **OK**.
![Adding the BCPCONFIGFILEPATH Install Option](/downloads/zscaler-client-connector/downloading-deployment/customizing-zscaler-app-install-options-msi/zclient-connector-msi-BCPCONFIGFILEPATH.png)
The install option appears on a new line.
![BCPCONFIGFILEPATH](/downloads/zscaler-client-connector/downloading-deployment/customizing-zscaler-app-install-options-msi/zclient-connector-msi-BCPCONFIGFILEPATH-property.png)
[]This install option allows you to install Zscaler Client Connector to enroll new users during a Private Applications-related cloud outage or Internet Service Provider (ISP) outage. You can pass a public key copied from the Admin Portal. To learn more, see [About Business Continuity](/zscaler-client-connector/about-business-continuity).
If you pass this install option, you must also pass the BCPCONFIGFILEPATH option.
To add the BCPMAPUBKEYHASH install option:
- Click **Tables** from the top menu, and then click **Add Row**.
- In the **Add Row** window:
- For **Property**, enter** **`BCPMAPUBKEYHASH`.
- Press `Enter` or click the **Value** field.
- For **Value**, enter the public key.
-
Click **OK**.
![Adding the BCPMAPUBKEYHASH Install Option](/downloads/zscaler-client-connector/downloading-deployment/customizing-zscaler-app-install-options-msi/zclient-connector-msi-BCPMAPUBKEYHASH.png)
The install option appears on a new line.
![BCPMAPUBKEYHASH](/downloads/zscaler-client-connector/downloading-deployment/customizing-zscaler-app-install-options-msi/zclient-connector-msi-BCPMAPUBKEYHASH-property.png)
[][]Zscaler recommends using the MST file to install Zscaler Client Connector with custom options. However, if you have a device management tool that does not support MST (e.g., SCCM or PSEXEC) or you are manually installing the MSI file, you can run the MSI file using the CLI and add the options needed.
To run the MSI file using CLI options:
- Start a command prompt as an administrator:
- Click **Start**.
- In the **Start Search** box, enter cmd, then press `CTRL+SHIFT+ENTER`.
- If the User Account Control (UAC) window appears, confirm that you want to continue.
![Running the command prompt as an administrator to run the Zscaler Client Connector MSI file](/downloads/zia/documentation-knowledgebase/forwarding-your-traffic/zscaler-app/downloading-and-deploying-zscaler-app/customizing-zscaler-app-install-options-msi/5154fdeb-9591-4089-8262-a3e692a4c799_display.png)
- Enter the following command:
`msiexec /i "<complete path>" /quiet <install options>`
- Replace `<complete path>` with the absolute pathname to the MSI install file. For example, `C:\Users\User\Downloads\Zscaler-windows-1.0.2.000018-installer.msi`
- Use the /`quiet `switch to install the app in silent mode.
-
Replace <install options> with one or more of the following install options:
- [CLOUDNAME](#cn2)
- [DEVICETOKEN](#dt2)
- [HIDEAPPUIONLAUNCH](#hi2)
- [POLICYTOKEN](#pt2)
- [REINSTALLDRIVER](#rd)
- [STRICTENFORCEMENT](#se2)
- [USERDOMAIN](#ud2)
- [UNAME](#uname)
- [ENABLEIMPRIVATAINTEGRATION](#imprivata)
- [ENABLEANTITAMPERING](#msi-enable-at)
- [EXTERNALDEVICEID](#externaldeviceid2)
- [BCPCONFIGFILEPATH](#bcpconfigfile2)
- [BCPMAPUBKEYHASH](#bcpmapubkeyhash2)
- [IMPORTSEFAILCLOSECONFIG](#import-se-fail-close-config2)
- [SEFAILCLOSECONFIGTHUMBPRINT](#fail-close-config-thumbprint2)
To modify any of these parameters post-installation, app reinstallation with the new values is required.
The following image is an example of a CLI where:
- The absolute path to the MSI file is C:\Users\User\Downloads\Zscaler-windows-1.2.0.000311-installer.msi.
- The /quiet switch is used to** **install the app in silent mode.
- The cloud on which the organization is provisioned is zscalertwo.
- The device token value is 4e36647447326e5a553335303232416e6279784b51513d3d.
- The policy token value is 32343A343A312E31204D6967726174696F6E.
- The organization's domain name is safemarch.com.
- The UNAME is test.
- The EXTERNALDEVICEID is `TestDevice`.
- ANTITAMPERING is `1`.
![Running the Zscaler Client Connector MSI file with a command line](/downloads/tech-pubs-drafts/client-connector-draft-articles/customizing-zscaler-client-connector-install-options-msi-doc-39855/MSI-install-options-example.png)
[]If your organization is provisioned on more than one cloud, your users are asked to select the cloud where their traffic is sent during the enrollment process.
[See image.](#cnimage2)
With this install option, you can specify the cloud where the app sends user traffic so that your users do not have to make the selection during enrollment. Do not use this option if your organization is provisioned on one cloud. The app automatically sends traffic to the proper cloud and your users do not need to make a selection during enrollment.
This install option is required if you enable the [STRICTENFORCEMENT](/zscaler-client-connector/customizing-zscaler-app-install-options-msi#se2) option.
To add this option using the CLI, enter CLOUDNAME=<organization's cloud name in lowercase>. For example, if your cloud name is zscalertwo.net, you would enter zscalertwo.
[]![Selecting a cloud on the Zscaler Client Connector](/downloads/zia/documentation-knowledgebase/forwarding-your-traffic/zscaler-app/downloading-and-deploying-zscaler-app/customizing-zscaler-app-install-options-msi/c750410e-4f94-4399-a335-0d590bc80578.png)
[]The DEVICETOKEN install option only applies to Internet & SaaS. It is not supported by Private Applications.
This install option allows you to use Zscaler Client Connector as an IdP. The Zscaler service silently provisions and authenticates users even if you don't have an authentication mechanism in place. Before adding this option, you must generate a device token in the Admin Portal and must have completed the full configuration detailed in [Using Zscaler Client Connector as an IdP](/unified/using-zscaler-client-connector-identity-provider).
To add this option using the CLI, enter DEVICETOKEN=<device token from the Admin Portal>.
[]This install option forces the app window to stay hidden before users enroll. Users can always open the window by clicking the app icon in the system tray.
To enable this option using the CLI, enter HIDEAPPUIONLAUNCH=1. By default, the value is 0 (i.e., disabled).
[]This install option allows you to specify which app profile policy you want to enforce for the app before the user enrolls. All relevant settings associated with the policy apply, including the bypass of the IdP login page. After the user enrolls, this policy is replaced with the app profile policy that matches the user based on group affiliation.
- This install option is only applicable, and required, if:
- You enable the [STRICTENFORCEMENT](/zscaler-client-connector/customizing-zscaler-app-install-options-msi#se2) option and want users to enroll with the app before accessing the internet.
- If you configure the machine tunnel and you want the users to access Private Applications before logging in to the device.
To add this option using the command-line, enter POLICYTOKEN=<policy token from the Admin Portal>.
![The policy token for a Zscaler Client Connector profile policy](/downloads/zia/documentation-knowledgebase/forwarding-your-traffic/zscaler-app/downloading-and-deploying-zscaler-app/customizing-zscaler-app-install-options-msi/ddb34838-3ca8-4606-8474-f9e445c3f91a_display.png)
[]This install option forces a reinstallation of the driver, even if you already have a driver installed. Use this option if you are having issues with the currently installed driver.
To enable this option using the CLI, enter REINSTALLDRIVER=1. By default, the value is 0 (i.e., disabled).
[]This install option only works when the forwarding profile action for Zscaler Client Connector is **Tunnel** or **Tunnel with Local Proxy**. To learn more, see [Configuring Forwarding Profiles for Zscaler Client Connector](/unified/configuring-forwarding-profiles-zscaler-client-connector).
This install option allows you to require users to enroll with the app before accessing the internet and blocks traffic in the following situations:
- The user has not yet logged in after a new install.
- A user logs in and logs out.
- An administrator removes a device.
This install option does not affect users that remain logged in and disable the Internet & SaaS service.
If you enable this install option, the --cloudName and --policyToken options are required.
To enable this option using the CLI, enter `STRICTENFORCEMENT=1`. By default, the value is 0 (i.e., disabled).
[]This install option allows users to skip the app enrollment page. If SSO is enabled for your organization, users are taken directly to your organization's SSO login page. If you've integrated SSO with the app (i.e., using a mechanism like Integrated Windows Authentication [IWA]), users can also skip the SSO login page and are automatically enrolled with Zscaler service and logged in.
[See image.](#ud2image)
To add this option using the CLI, enter USERDOMAIN=<organization's domain name>. If your instance has multiple domains associated with it, enter the primary domain for your instance. The primary domain is only valid if you are using a single IdP with multiple domains. The primary domain won’t work if you have multiple domains across multiple IdPs.
[]![The Zscaler Client Connector enrollment page and an organization SSO login page](/downloads/zia/documentation-knowledgebase/forwarding-your-traffic/zscaler-app/downloading-and-deploying-zscaler-app/customizing-zscaler-app-install-options-msi/be04e7c4-a913-41ff-92bb-624082d47b8a.png?1602182710)
[]You can specify a unique username for each device using the UNAME parameter in the CLI.
The following conditions apply:
- The UNAME parameter requires the userDomain parameter to be non-empty.
- The UNAME parameter can have a maximum of 255 alphanumeric and special characters.
[]This install option enables [integration with Imprivata OneSign](/unified/zscaler-client-connector-and-imprivata-integration). If enabled, Zscaler Client Connector silently logs in an Imprivata OneSign user to Zscaler Client Connector, applies security policies, and logs the end-user activity in Zscaler Client Connector.
[]This install option prevents end users from stopping, modifying, and deleting Zscaler products and services. To enable this option using the CLI, enter `ENABLEANTITAMPERING=1`. By default, the value is `0` (i.e., disabled).
[]The identifier that associates an external MDM device ID with devices in the Zscaler Client Connector Portal. You can use this to associate devices in an MDM solution with devices in the Zscaler Client Connector Portal.
To enable this option using the CLI, enter `--externalDeviceId `. By default, the value is 0 (i.e., disabled).
The `--externalDeviceId` parameter is not supported on Zscaler Client Connector version 4.1 and earlier for macOS and on Zscaler Client Connector version 4.0 and earlier for Windows.
[]This install option allows you to install Zscaler Client Connector to enroll new users during a Private Applications-related cloud outage or Internet Service Provider (ISP) outage. You can pass a predownloaded configuration file with Business Continuity settings from the Admin Portal. To learn more, see [About Business Continuity](/unified/about-business-continuity).
If you pass this install option, you must also pass the `BCPMAPUBKEYHASH` option.
To add this option using the CLI, enter `BCPCONFIGFILEPATH`=<path to the configuration file>.
[]This install option allows you to install Zscaler Client Connector to enroll new users during a Private Applications-related cloud outage or Internet Service Provider (ISP) outage. You can pass a public key copied from the Admin Portal. To learn more, see [About Business Continuity](/zscaler-client-connector/about-business-continuity).
If you pass this install option, you must also pass the `BCPCONFIGFILEPATH` option.
To add this option using the CLI, enter `BCPMAPUBKEYHASH`=<public key from the Admin Portal>.
[]This install option allows you to pass a predownloaded configuration file with [fail-close settings](/unified/configuring-zscaler-client-connector-app-profiles) to use when Zscaler Client Connector is in strict enforcement mode.
If you pass this install option, you must also pass the `STRICTENFORCEMENT` and `SEFAILCLOSECONFIGTHUMBPRINT` options.
To add this option using the CLI, enter `IMPORTSEFAILCLOSECONFIG`=<path to the configuration file>.
[]This install option allows you to pass the public key for a predownloaded configuration file with [fail-close settings](/unified/configuring-zscaler-client-connector-app-profiles) to use when Zscaler Client Connector is in strict enforcement mode.
If you pass this install option, you must also pass the `STRICTENFORCEMENT` and `IMPORTSEFAILCLOSECONFIG` options.
To add this option using the CLI, enter `SEFAILCLOSECONFIGTHUMBPRINT`=<public key from the Admin Portal>.
[]
Zscaler Client Connector only supports a dedicated, single-user virtual desktop infrastructure (VDI) model. Multi-session VDIs are not supported.
Follow these best practices when using Zscaler Client Connector in a VDI:
- Zscaler recommends that you don't log in to Zscaler Client Connector on the master VM.
- [To use the ](>)[STRICTENFORCEMENT install option](/zscaler-client-connector/customizing-zscaler-app-install-options-msi#se), you must have the [HIDEAPPUIONLAUNCH install option](/zscaler-client-connector/customizing-zscaler-app-install-options-msi#hideapp) disabled. This allows Zscaler Client Connector to remind users to enroll with Zscaler Client Connector before accessing the internet.
- To use the [USERDOMAIN install option](/zscaler-client-connector/customizing-zscaler-app-install-options-msi#ud), you must use Integrated Windows Authentication (IWA).
Behavior of Install Parameters for VDI
The install parameters for VDI behave in the following manner:
- `VDI=1` : Configures the Zscaler Client Connector to store configuration data in the `%USERPROFILE%\AppData\Roaming\Zscaler` user profile store so it is roamed using a profile management tool instead of the default `%ProgramData%\Zscaler`. This allows admins to restore Zscaler's configuration as part of users' profiles using tools such as Citrix UPM as described in the [Installing Zscaler Client Connector on the Master VM](#install-vm) section.
- `CONFIGTIMEOUT=300` : If the Zscaler Client Connector configuration data is not found, Zscaler Client Connector waits for the specified interval for configuration data to be restored. In environments with roaming profiles such as non-persistent VDIs, it might take additional time for the profile management solution to restore the Zscaler Client Connector configuration data to the user profile.
- `INSTALLLWFDRIVER=1` : Install the lightweight filter driver used for traffic interception during installation of the Zscaler Client Connector. Without this parameter, Zscaler Client Connector doesn't install the LWF driver until configured to do so by a forwarding profile during policy download, which might cause network connection disruption and VDI disconnection.
- `LWFBOOTSTART=1` : Configures the LWF driver to load at system boot instead of the default at system startup. This prevents a blue screen during OS boot in environments where the OS is booted over the network, such as in Citrix Provisioning Services.
[]Installing Zscaler Client Connector on the Master VM
Install Zscaler Client Connector on the master VM using the following steps:
- Configure Citrix UPM to backup and restore to the following folder: `{UserProfileFolder}\AppData\Roaming\Zscaler`
- Run your MSI installer: msiexec/i ZCC_installer.msi `USERDOMAIN=`<AD domain> `CLOUDNAME=`<cloudname> `VDI=1` `CONFIGTIMEOUT=300` `INSTALLLWFDRIVER=1` `LWFBOOTSTART=1`
The parameters listed earlier are samples for a VDI installation Zscaler Client Connector. Consult the installation parameters for Zscaler Client Connector to remove/add any options as necessary for the deployment requirements. For example, to support seamless SSO authentication with IWA, adding `USERDOMAIN` and `CLOUDNAME` parameters might be necessary. If the VDI deployment does not use a profile management solution, it's not necessary to apply the `CONFIGTIMEOUT` parameter. If you are using Citrix Provisioning Server, you must use the `LWFBOOTSTART` option.
For a complete list of the installation parameters, refer to [Running the MSI with CLI Options](#running-MSI-CLI-options).