# Customizing Zscaler Client Connector with Install Options for MSI
Source: https://help.zscaler.com/zscaler-client-connector/customizing-zscaler-client-connector-install-options-msi
PDF: https://help.zscaler.com/pdf/com/en/1285456.pdf

You can use the MSI file to manually install Zscaler Client Connector on a device or if you're deploying the app to your users using GPO, SCCM, or other device management methods that support MSI files. After downloading the Zscaler Client Connector MSI installer file in the [Zscaler Client Connector Portal](/zscaler-client-connector/about-zscaler-client-connector-store), you can deploy the file as is with your device management method. If you want to customize the MSI file and add install options (for example, to enable strict enforcement), you must first create an MST file.
You can also add to the file install options to customize the app for your organization using one of the following methods:
- [Creating an MST and Deploying It Using GPO or a Compatible Device Management Tool](#CreateZAppMSTFile)
- [Running the MSI with CLI Options](#RunZAppMSICmdLine)
- [Deploying Zscaler Client Connector with Non-Persistent Citrix VDIs](#InstallVDI)
[]Orca.exe is available in the [Microsoft Windows Software Development Kit (SDK)](https://developer.microsoft.com/en-us/windows/downloads/windows-10-sdk). To learn more, refer to the [Microsoft documentation](https://learn.microsoft.com/en-us/windows/win32/msi/orca-exe).
Windows installers use an MST file to enable customized installations of an original MSI package during installation. You can create an MST file and then deploy it to users using a Group Policy Object (GPO) or a compatible device management tool such as Microsoft Intune or Jamf Pro.
To create an MST file using Orca:
Open Orca and go to **File** > **Open**.
- Locate and double-click the MSI file.
![Clicking the New Transform option to create a MST file for Zscaler Client Connector](/downloads/z-app/downloading-deployment/customizing-zscaler-app-install-options-msi/Zscaler-App-MSI-New-Transform.png)
- Go to** Transform** > **New Transform**.
![The Zscaler Client Connector MSI file properties](/downloads/z-app/downloading-deployment/customizing-zscaler-app-install-options-msi/Zscaler-App-MSI-Property.png)
- In the **Tables** column, click **Property**.
-
Add [Zscaler configuration parameters](/zscaler-client-connector/supported-parameters-zscaler-client-connector-windows) and their corresponding values per your organization's needs.
To modify any of these parameters post-installation, app reinstallation with the new values is required.
- To save your changes after adding the options you want, go to **Transform** > **Generate Transform.**
![The Generate Transform option to create a MST file for Zscaler Client Connector](/downloads/z-app/downloading-deployment/customizing-zscaler-app-install-options-msi/Zscaler-App-MSI-Generate-Transform.png)
- In the **Save Transform As** window, enter a file name and click **Save**.
![Saving the Zscaler Client Connector MST file](/downloads/z-app/downloading-deployment/customizing-zscaler-app-install-options-msi/Zscaler-App-MSI-Saving.png?1602182163)
After creating the MST, you can use it when [deploying Zscaler Client Connector to your users with Active Directory](/zscaler-client-connector/deploying-zscaler-app-active-directory-windows).
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
- Replace <install options> with one or more of the [Zscaler configuration parameters.](/zscaler-client-connector/supported-parameters-zscaler-client-connector-windows)
To modify any of these parameters post-installation, app reinstallation with the new values is required.
The following image is an example of a CLI where:
- The absolute path to the MSI file is `C:\Users\User\Downloads\Zscaler-windows-1.2.0.000311-installer.msi`.
- The `/quiet` switch is used to** **install the app in silent mode.
- The cloud on which the organization is provisioned is `zscalertwo`.
- The device token value is `4e36647447326e5a553335303232416e6279784b51513d3d`.
- The policy token value is `32343A343A312E31204D6967726174696F6E`.
- The organization's domain name is `safemarch.com`.
- The UNAME is `test`.
- The EXTERNALDEVICEID is `TestDevice`.
- ANTITAMPERING is `1`.
![Running the Zscaler Client Connector MSI file with a command line](/downloads/tech-pubs-drafts/client-connector-draft-articles/customizing-zscaler-client-connector-install-options-msi-doc-39855/MSI-install-options-example.png)
[]
Zscaler Client Connector only supports a dedicated, single-user virtual desktop infrastructure (VDI) model. For multi-session VDIs, [Zscaler Client Connector for VDI](/cloud-branch-connector/what-zscaler-client-connector-vdi) is required.
Follow these best practices when using Zscaler Client Connector in a VDI:
- Zscaler recommends that you don't log in to Zscaler Client Connector on the master VM.
- To use the STRICTENFORCEMENT install option, you must have the HIDEAPPUIONLAUNCH install option disabled. This allows Zscaler Client Connector to remind users to enroll with Zscaler Client Connector before accessing the internet.
- To use the USERDOMAIN install option, you must use Integrated Windows Authentication (IWA).
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