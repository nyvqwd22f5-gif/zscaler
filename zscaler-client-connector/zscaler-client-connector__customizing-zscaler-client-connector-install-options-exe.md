# Customizing Zscaler Client Connector with Install Options for EXE
Source: https://help.zscaler.com/zscaler-client-connector/customizing-zscaler-client-connector-install-options-exe
PDF: https://help.zscaler.com/pdf/com/en/1285461.pdf

You can use the EXE file to manually install Zscaler Client Connector on a device, or if you're deploying the app to your users through device management methods that do not support MSI files. After downloading the Zscaler Client Connector EXE installer file, you can deploy the file as is with your device management method.
You can also add install options to customize the app for your organization. This article covers the following options:
- [Running the EXE File with CLI Options](#RunZAppEXECmdLine)
- [Allowing Users to Log into Zscaler Client Connector Without Entering Domains](#ZAppLoginNoDomain)
- [Deploying Zscaler Client Connector with Non-Persistent Citrix VDIs](#InstallVDIexe)
If you're deploying the app in an Active Directory (AD) environment, you can add install options as parameters when assigning a system start-up script to install the app. To learn more, see [Deploying Zscaler Client Connector for Windows with Active Directory](/zscaler-client-connector/deploying-zscaler-app-active-directory-windows#EXE).
[]To run the EXE file using CLI options:
- Start a command prompt as an administrator.
- Click **Start**.
- In the **Start Search** box, enter cmd, then press `CTRL+SHIFT+ENTER`.
- If the User Account Control (UAC) window appears, confirm that you want to continue.
- Enter the absolute path to the EXE file using one or more of the [Zscaler configuration parameters](/zscaler-client-connector/supported-parameters-zscaler-client-connector-windows) in the `--<install option>` format.
To modify any of these parameters post-installation, app reinstallation with the new values is required.
The following image is an example of a CLI where:
- The absolute path to the EXE file is `C:\Users\User\Downloads\Zscaler-windows-1.2.0.000311-installer.exe`
- The cloud on which the organization is provisioned is `zscalertwo`
- The device token value is `123456789`
- The policy token value is `987654321`
- The organization's domain name is `safemarch.com`
- The userName is `test`
- The externalDeviceId is `TestDevice`.
![EXE install options](/downloads/zscaler-client-connector/downloading-deployment/customizing-zscaler-app-install-options-exe/ZClientConnector-Install-Options-EXE-Command-Prompt.png)
[]In addition to the custom features enabled by the install options, you can also modify the EXE file to allow users to log in to the app without entering a domain name.
You can use this configuration only if your organization's domain is registered on a single cloud. If your organization's domain is registered on multiple clouds, use the CLI install options described earlier.
This configuration achieves the same function as the --userDomain install option. The following guidelines apply:
- SSO must be enabled for your organization.
- If you've integrated your SSO with Zscaler Client Connector using a mechanism like Integrated Windows Authentication (IWA), users can also skip the SSO login page and are automatically enrolled in the Zscaler service and logged in.
To allow users to log into the app without entering domains:
- Locate the EXE file.
- Prefix the file name with your organization's domain name. For example, if the file name is Zscaler-windows-1.1.0.000213-installer and your organization's domain is safemarch.com, you would rename the file to safemarch.com-Zscaler-windows-1.1.0.000213-installer.
![A configured Zscaler Client Connector EXE file that allows users to log in without entering domains](/downloads/zia/documentation-knowledgebase/forwarding-your-traffic/zscaler-app/downloading-and-deploying-zscaler-app/customizing-zscaler-app-install-options-exe/de0904c5-b98e-4e08-8e17-e734842e7ba2_display.png)
[]
Zscaler Client Connector only supports a dedicated, single-user virtual desktop infrastructure (VDI) model. For multi-session VDIs, [Zscaler Client Connector for VDI](/cloud-branch-connector/what-zscaler-client-connector-vdi) is required.
Follow these best practices when using Zscaler Client Connector in a VDI:
- Zscaler recommends that you don't log in to Zscaler Client Connector on the master VM.
- To use the --strictEnforcement install option, you must have the --hideAppUIOnLaunch install option disabled. This allows Zscaler Client Connector to remind users to enroll with Zscaler Client Connector before accessing the internet.
- To use the --userDomain install option, you must use Integrated Windows Authentication (IWA).
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