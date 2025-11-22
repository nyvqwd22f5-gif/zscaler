# Customizing Zscaler Client Connector with Install Options for EXE
Source: https://help.zscaler.com/unified/customizing-zscaler-client-connector-install-options-exe
PDF: https://help.zscaler.com/pdf/com/en/1491921.pdf

You can use the EXE file to manually install Zscaler Client Connector on a device, or if you're deploying the app to your users through device management methods that do not support MSI files. After downloading the Zscaler Client Connector EXE installer file, you can deploy the file as is with your device management method.
You can also add install options to customize the app for your organization. This article covers the following options:
- [Running the EXE File with CLI Options](#RunZAppEXECmdLine)
- [Allowing Users to Log into Zscaler Client Connector Without Entering Domains](#ZAppLoginNoDomain)
- [Deploying Zscaler Client Connector with Non-Persistent Citrix VDIs](#InstallVDIexe)
If you're deploying the app in an Active Directory (AD) environment, you can add install options as parameters when assigning a system start-up script to install the app. To learn more, see [Deploying Zscaler Client Connector for Windows with Active Directory](/unified/deploying-zscaler-client-connector-active-directory-windows).
[]To run the EXE file using CLI options:
- Start a command prompt as an administrator.
- Click **Start**.
- In the **Start Search** box, enter cmd, then press `CTRL+SHIFT+ENTER`.
- If the User Account Control (UAC) window appears, confirm that you want to continue.
-
Enter the absolute path to the EXE file using one or more of the following install options:
- [--cloudName](#cn)
- [--deviceToken](#dt)
- [--hideAppUIOnLaunch](#hide)
- [--mode](#mode)
- [--policyToken](#pt)
- [--reinstallDriver](#rd1)
- [--strictEnforcement](#se)
- [--unattendedmodeui](#umui)
- [--userDomain](#ud)
- [--userName](#username)
- [--enableAntiTampering](#antitampering)
- [--externalDeviceId](#externaldeviceid)
- [--enableImprivataIntegration](#imprivata)
- [--bcpConfigFilePath](#bcpconfigfile)
- [--bcpMAPublicKeyHash](#bcpmapublickeyhash)
- [--importSEFailCloseConfig](#import-se-fail-close-config)
- [--failCloseConfigThumbprint](#fail-close-config-thumbprint)
To modify any of these parameters post-installation, app reinstallation with the new values is required.
The following image is an example of a CLI where:
- The absolute path to the EXE file is C:\Users\User\Downloads\Zscaler-windows-1.2.0.000311-installer.exe
- The cloud on which the organization is provisioned is zscalertwo
- The device token value is 123456789
- The policy token value is 987654321
- The organization's domain name is safemarch.com
- The userName is `test`
- The externalDeviceId is TestDevice
![EXE install options](/downloads/zscaler-client-connector/downloading-deployment/customizing-zscaler-app-install-options-exe/ZClientConnector-Install-Options-EXE-Command-Prompt.png)
[]If your organization is provisioned on more than one cloud, your users are asked to select the cloud to which their traffic is sent during the enrollment process.
[See image.](#cnimage2)
With this install option, you can specify the cloud to which the app must send user traffic so your users don't have to make the selection during enrollment. Do not use this option if your organization is provisioned on one cloud. The app automatically sends traffic to the proper cloud. Your users don't need to make a selection during enrollment.
This install option is required if you enable the `--strictEnforcement` option.
To add this option using the CLI, enter --cloudName <organization's cloud name in lowercase>. For example, if your cloud name is zscalertwo.net, you would enter zscalertwo.
[]![Selecting a cloud on the Zscaler Client Connector](/downloads/zia/documentation-knowledgebase/forwarding-your-traffic/zscaler-app/downloading-and-deploying-zscaler-app/customizing-zscaler-app-install-options-exe/24f92544-ad8c-4691-9519-14a36c465838.png)
[]The --deviceToken install option only applies to Internet & SaaS. It is not supported by Private Applications.
This install option allows you to use Zscaler Client Connector as an IdP. The Zscaler service silently provisions and authenticates users even if you don't have an authentication mechanism in place. Before adding this option, you must generate a device token in the Admin Portal and complete the full configuration detailed in [Using Zscaler Client Connector as an IdP](/unified/using-zscaler-client-connector-identity-provider).
To add this option using the CLI, enter --deviceToken* **<*device token from the Admin Portal>.
[]This install option forces the app window to stay hidden before users enroll. Users can always open the window by clicking the app icon in the system tray.
To enable this option using the CLI, enter --hideAppUIOnLaunch 1. By default, the value is 0 (i.e., disabled).
[]This install option allows you to install the app in silent mode.
To add this option using the CLI, enter --mode unattended.
[]This install option allows you to specify which app profile policy you want to enforce for the app before the user enrolls. All relevant settings associated with the policy are applied, including the bypass of the IdP login page. After the user enrolls, this policy is replaced with the app profile policy that matches the user based on group affiliation.
Prerequisites:
- This install option is only applicable, and required, if you enable the --strictEnforcement option and want users to enroll with the app before accessing the internet.
- In the Admin Portal, you must [configure the app profile policy](/unified/configuring-zscaler-client-connector-app-profiles) that you want to enforce and ensure that the custom PAC file associated with that policy includes a bypass for your IdP login page. This allows the user to access the IdP page to log in as necessary before enrolling with the app.
To add this option using the CLI, enter --policyToken <policy token from the Admin Portal>.
![The policy token for a Zscaler Client Connector profile policy](/downloads/z-app/downloading-and-deploying-zscaler-app/customizing-zscaler-app-install-options-exe/zapp-exe-policytoken.png)
[]This install option forces a reinstallation of the driver, even if you already have a driver installed. Use this option if you are having issues with the currently installed driver.
To enable this option using the CLI, enter** **--reinstallDriver 1. By default, the value is 0 (i.e., disabled).
[]This install option only works when the forwarding profile action for Zscaler Client Connector is **Tunnel** or **Tunnel with Local Proxy**. To learn more, see [Configuring Forwarding Profiles for Zscaler Client Connector](/unified/configuring-forwarding-profiles-zscaler-client-connector).
This install option allows you to require users to enroll with the app before accessing the internet and blocks traffic in the following situations:
- The user has not yet logged in after a new install.
- A user logs in and logs out.
- An administrator removes a device.
This install option does not affect users that remain logged in and disable the Internet & SaaS service.
If you enable this install option, the `--cloudName` and `--policyToken` options are required.
To enable this option using the CLI, enter --strictEnforcement 1. By default, the value is 0 (i.e., disabled).
[]This install option allows you to control what's displayed to users if you are performing an unattended installation of the app.
To add the install option using the CLI, enter --unattendedmodeui <value>, where <value> is one of the following:
- none: Nothing is displayed to the user and no interaction is required. If you included the `--mode unattended` install option, none is the default value for `--unattendedmodeui`.
- minimal: A small progress bar showing installation progress is displayed to the user and no interaction is required.
- minimalWithDialogs: More information is displayed to the user with some dialogs that require user interaction.
[]This install option allows users to skip the app enrollment page. If SSO is enabled for your organization, users are taken directly to your organization's SSO login page. If you've integrated SSO with the app (i.e., using a mechanism like Integrated Windows Authentication [IWA]), users can also skip the SSO login page and are automatically enrolled in the Zscaler service and logged in.
[See image.](#udimage2)
An alternative to using this install option is to change the name of the installer file. To learn more, see [Allow Users to Log into Zscaler Client Connector Without Entering Domains](/unified/customizing-zscaler-client-connector-install-options-exe#ZAppLoginNoDomain).
To add the install option using the CLI, enter --userDomain <organization's domain name>. If your instance has multiple domains associated with it, enter the primary domain for your instance. The primary domain is only valid if you are using a single IdP with multiple domains. The primary domain won’t work if you have multiple domains across multiple IdPs.
[]![The Zscaler Client Connector enrollment page and an organization SSO login page](/downloads/zia/documentation-knowledgebase/forwarding-your-traffic/zscaler-app/downloading-and-deploying-zscaler-app/customizing-zscaler-app-install-options-exe/19897a56-8004-4068-aaf7-dd52975a8e4c.png)
[]You can specify a unique username for each device using the userName parameter in the command line.
The following conditions apply:
- The userName parameter requires the userDomain parameter to be non-empty.
- The userName parameter can have a maximum of 255 alphanumeric and special characters.
[See image.](#username-in-command-line)
[]This install option prevents end users from stopping, modifying, and deleting Zscaler products and services.
To enable this option using the CLI, enter --enableAntiTampering 1. By default, the value is 0 (i.e., disabled).
[]The identifier that associates an external MDM device ID with devices in the Admin Portal. You can use this ID to associate devices in an MDM solution with devices in the Admin Portal.
To enable this option using the CLI, enter `--externalDeviceId`. By default, the value is 0 (i.e., disabled).
The `--externalDeviceId` parameter is not supported on Zscaler Client Connector version 4.1 and earlier for macOS and on Zscaler Client Connector version 4.0 and earlier for Windows.
[]This install option enables integration with Imprivata OneSign. If enabled, Zscaler Client Connector silently logs in an Imprivata OneSign user to Zscaler Client Connector, applies security policies, and logs the end-user activity in Zscaler Client Connector.
To enable this option using the CLI, enter `--enableImprivataIntegration 1`.
[]This install option allows you to install Zscaler Client Connector to enroll new users during a Private Applications-related cloud outage or Internet Service Provider (ISP) outage. You can pass a predownloaded configuration file with Business Continuity settings from the Admin Portal. To learn more, see [About Business Continuity](/unified/about-business-continuity).
If you pass this install option, you must also pass the `--bcpMAPublicKeyHash` option.
To add this option using the CLI, enter `--bcpConfigFilePath` <path to the configuration file>.
[]This install option allows you to install Zscaler Client Connector to enroll new users during a Private Applications-related cloud outage or Internet Service Provider (ISP) outage. You can pass a public key copied from the Admin Portal. To learn more, see [About Business Continuity](/unified/about-business-continuity).
If you pass this install option, you must also pass the `--bcpConfigFilePath` option.
To add this option using the CLI, enter `--bcpMAPublicKeyHash` <public key from the Admin Portal.
[]This install option allows you to pass a predownloaded configuration file with [fail-close settings](/unified/configuring-zscaler-client-connector-app-profiles) to use when Zscaler Client Connector is in strict enforcement mode.
If you pass this install option, you must also pass the `--failCloseConfigThumbprint` and `--strictEnforcement` options.
To add this option using the CLI, enter `--importSEFailCloseConfig` <path to the configuration file>.
[]This install option allows you to pass the public key for a predownloaded configuration file with [fail-close settings](/unified/configuring-zscaler-client-connector-app-profiles) to use when Zscaler Client Connector is in strict enforcement mode.
If you pass this install option, you must also pass the `--importSEFailCloseConfig` and `--strictEnforcement` options.
To add this option using the CLI, enter `--failCloseConfigThumbprint` <public key from the Admin Portal>.
[]![UserName parameter](/downloads/z-app/downloading-deployment/customizing-zscaler-app-install-options-exe/Username.png)
[]In addition to the custom features enabled by the install options, you can also modify the EXE file to allow users to log into the app without entering a domain name.
You can use this configuration only if your organization's domain is registered on a single cloud. If your organization's domain is registered on multiple clouds, use the CLI options described earlier.
This configuration achieves the same function as the --userDomain install option. The following guidelines apply:
- SSO must be enabled for your organization.
- If you've integrated your SSO with Zscaler Client Connector using a mechanism like Integrated Windows Authentication (IWA), users can also skip the SSO login page and are automatically enrolled in the Zscaler service and logged in.
To allow users to log into the app without entering domains:
- Locate the EXE file.
- Prefix the file name with your organization's domain name. For example, if the file name is Zscaler-windows-1.1.0.000213-installer and your organization's domain is safemarch.com, you would rename the file to safemarch.com-Zscaler-windows-1.1.0.000213-installer.
![A configured Zscaler Client Connector EXE file that allows users to log in without entering domains](/downloads/zia/documentation-knowledgebase/forwarding-your-traffic/zscaler-app/downloading-and-deploying-zscaler-app/customizing-zscaler-app-install-options-exe/de0904c5-b98e-4e08-8e17-e734842e7ba2_display.png)
[]
Zscaler Client Connector only supports a dedicated, single-user virtual desktop infrastructure (VDI) model.
Follow these best practices when using Zscaler Client Connector in a VDI:
- Zscaler recommends that you don't log in to Zscaler Client Connector on the master VM.
- [To use the ](/unified/customizing-zscaler-client-connector-install-options-exe#se)[STRICTENFORCEMENT install option], you must have the [HIDEAPPUIONLAUNCH install option](/zscaler-client-connector/customizing-zscaler-app-install-options-msi#hideapp) disabled. This allows Zscaler Client Connector to remind users to enroll with Zscaler Client Connector before accessing the internet.
- To use the [USERDOMAIN install option](/zscaler-client-connector/customizing-zscaler-app-install-options-msi#ud), you must use Integrated Windows Authentication (IWA).
Behavior of Install Parameters for VDI
The install parameters for VDI behave in the following manner:
- `--vdi` `1` : Configures the Zscaler Client Connector to store configuration data in the `%USERPROFILE%\AppData\Roaming\Zscaler` user profile store so it is roamed using a profile management tool instead of the default `%ProgramData%\Zscaler`. This allows admins to restore Zscaler's configuration as part of users' profiles using tools such as Citrix UPM as described in the [Installing Zscaler Client Connector on the Master VM](#install-vm) section.
- `--configTimeout` `300` : If the Zscaler Client Connector configuration data is not found, Zscaler Client Connector waits for the specified interval for configuration data to be restored. In environments with roaming profiles such as non-persistent VDIs, it might take additional time for the profile management solution to restore the Zscaler Client Connector configuration data to the user profile.
- `--installLWFDriver` `1` : Install the lightweight filter (LWF) driver used for traffic interception during installation of the Zscaler Client Connector. Without this parameter, Zscaler Client Connector doesn't install the LWF driver until configured to do so by a forwarding profile during policy download, which might cause network connection disruption and VDI disconnection.
- `--LWFBootStart` `1` : Configures the LWF driver to load at system boot instead of the default at system startup. This prevents a blue screen during OS boot in environments where the OS is booted over the network, such as in Citrix Provisioning Services.
[]Installing Zscaler Client Connector on the Master VM
Install Zscaler Client Connector on the master VM using the following parameters:
- Configure Citrix UPM to backup and restore to the following folder: `{UserProfileFolder}\AppData\Roaming\Zscaler`
- Run your installer and run the installer executable file: `--vdi 1 --configTimeout 300 --installLWFDriver 1 --LWFBootStart 1`
The parameters listed earlier are samples for a VDI installation Zscaler Client Connector. Consult the installation parameters for Zscaler Client Connector to remove/add any options as necessary for the deployment requirements. For example, to support seamless SSO authentication with IWA, adding `--userDomain` and `--cloudName` parameters might be necessary. If the VDI deployment does not use a profile management solution, it's not necessary to apply the `--configTimeout` parameter. If you are using Citrix Provisioning Server, you must use the `--LWFBootStart` option.