# Customizing Zscaler Client Connector for VDI with Install Options for MSI
Source: https://help.zscaler.com/cloud-branch-connector/customizing-zscaler-client-connector-vdi-install-options-msi
PDF: https://help.zscaler.com/pdf/com/en/1472251.pdf

If you are deploying Zscaler Client Connector for Virtual Desktop Infrastructure (VDI) to your users using Microsoft Azure, Citrix XenCenter, or other device-management methods that support Microsoft Software Installer (MSI) files, you can download and use the MSI file. After downloading and configuring Zscaler Client Connector for VDI, you can deploy the file as is using your device-management method. Alternatively, you can use the MSI file to manually install Zscaler Client Connector for VDI on a device. To learn more about the required configuration tasks, see [Step-by-Step Configuration Guide for Zscaler Client Connector for VDI](/cloud-branch-connector/step-step-configuration-guide-zscaler-client-connector-vdi).
To enable this feature, contact Zscaler Support.
You can also customize the app for your organization by using one of the following methods to add to the file install options:
- [Implementing Zscaler Client Connector for VDI Golden Image in Microsoft Azure Virtual Desktop](#Azure)
- [Implementing Zscaler Client Connector for VDI Golden Image in Citrix XenDesktop Virtual Desktop Agent](#Citrix)
- [Running the MSI with Command-Line Options](#Commandline)
- [Deploying Zscaler Client Connector for VDI with Microsoft Intune](#Intune)
- [Preventing Zscaler Client Connector for VDI from Onboarding When Rebooting](#donotonboard)
[]
To create a golden image in Microsoft Azure:
- Log in to the Microsoft Azure Portal.
- Create a golden image for the Microsoft Azure Virtual Desktop (AVD). To learn more about the steps required for creating a golden image, refer to the [Microsoft documentation](https://learn.microsoft.com/en-us/azure/virtual-desktop/set-up-golden-image).
- Within the Microsoft AVD, from the command line, run the** ZCCVDIInstaller **MSI package using the following command as an example:
`msiexec /i ZCCVDIInstaller.msi PROVURL="<url>" TOKEN="<token>" ONBOARD=0`
You must use the `ONBOARD=0` flag for golden image deployments.
-
After Zscaler Client Connector for VDI is installed, it prompts you for authentication via the machine's default web browser. Do not immediately authenticate. Minimize Zscaler Client Connector for VDI and continue the golden image Sysprep process. This process typically includes performing a Windows Sysprep with the generalize option, shutting down a virtual machine (VM), and cloning or image capturing a VM.
Do not boot the prepared VM or image until after you clone it to the host pool instances, and do not start or reboot Zscaler Client Connector for VDI when creating a golden image.
-
After the golden image is created, you can use it to host pools in AVD. To learn more about host pools, refer to the [Microsoft documentation](https://learn.microsoft.com/en-us/azure/virtual-desktop/deploy-azure-virtual-desktop?tabs=portal).
When updating a golden image VM where Zscaler Client Connector for VDI has been installed using the `ONBOARD=0` flag, if the VM must be rebooted for any reason, you must uninstall Zscaler Client Connector for VDI and then reinstall Zscaler Client Connector for VDI using the `ONBOARD=0` flag prior to the Sysprep, shutdown, and clone process.
[]
To create a golden image in Citrix XenCenter:
- Log in to Citrix XenCenter.
- Create a golden image (or XenDesktop image). To learn more about the steps required for creating a golden image, refer to the [Citrix documentation](https://support.citrix.com/article/CTX130937/how-to-create-a-xendesktop-desktop-image).
- Within the golden image desktop, from the command line, run the** ZCCVDIInstaller **MSI package using the following command as an example:
`msiexec /i ZCCVDIInstaller.msi PROVURL="<url>" TOKEN="<token>" ONBOARD=0`
You must use the `ONBOARD=0` flag for golden image deployments.
-
After the golden image is created, you can use it to host pools in XenDesktop Virtual Desktop Agent. To learn more about host pools, refer to the [Citrix documentation](https://docs.citrix.com/en-us/provisioning/current-release/configure/xendesktop-setup-wizard.html).
When updating a golden image VM where Zscaler Client Connector for VDI has been installed using the `ONBOARD=0` flag, if the VM must be rebooted for any reason, you must uninstall Zscaler Client Connector for VDI and then reinstall Zscaler Client Connector for VDI using the `ONBOARD=0` flag prior to the Sysprep, shutdown, and clone process.
[]
To run the MSI file using command-line options:
- Start a command prompt as an administrator:
- Click **Start**.
- In the **Start Search** field, enter cmd, then press `Ctrl+Shift+Enter`.
-
If the User Account Control (UAC) dialog window appears, confirm that you want to continue.
![Running the Command Prompt as an Administrator](/downloads/cloud-branch-connector/zscaler-client-connector-vdi-management/customizing-zscaler-client-connector-vdi-install-options-msi/UAC.png)
- Enter the following command:
`msiexec /i ZCCVDIInstaller_1.0.0.XX.msi PROVURL="AAA" TOKEN="BBB" MODE="CCC" SERVERIP="DDD" ONBOARD="EEE" CONFIGREADTIMEOUT="FFF" HIDEAPPONUILAUNCH="GGG" USEEMBEDDEDBROWSER="HHH" SHOWREAUTHNOTIFICATION="III"`
- **PROVURL="AAA"**: Replace `"AAA"` with the provisioning URL from the [VDI Template](/cloud-branch-connector/about-vdi-templates).
- **TOKEN="BBB"**: Replace `"BBB"` with the token value from the [VDI Template](/cloud-branch-connector/about-vdi-templates).
- **MODE="CCC"**: Replace `"CCC"` with the tunneling mode (`1` or `0`).
- Point-to-Point (P2P) Tunneling Mode (Mode is 1): The P2P Tunneling Mode is the default mode of operation for Zscaler Client Connector for VDI and Cloud & Branch Connector tunnels. With P2P, the tunnel is created with a fixed destination IP address and destination port. The source port is copied from the inner header. Use this tunneling method if you want to have fixed IP addresses for outer header tunnels where destination IP addresses must be known. As part of deploying Zscaler Client Connector for VDI, a Zscaler anycast Global VIP address (185.46.212.80) is used as the destination IP address for the outer header. You must configure routing so that the next hop for the Global VIP points to the Cloud Connector or Branch Connector load balancer.
-
Any-to-Any (A2A) Tunneling Mode (Mode is 0): The A2A Tunneling Mode copies the inner header of the packet to the outer encapsulated header. This mode provides better load balancing because the source IP address, destination IP address, and source port are preserved. This results in better traffic distribution across multiple Cloud & Branch Connector instances. A2A Tunneling Mode requires a default route pointing to the Cloud Connector or Branch Connector because the destination IP addresses are dynamic.
A2A Tunneling Mode is not recommended and is being deprecated.
- **SERVERIP="DDD"**: Replace `"DDD"` with the IP address of the load balancer hosting the Cloud Connector or Branch Connector, or the service interface IP address of either the Cloud Connector or the Branch Connector. Alternatively, you can use a fully qualified domain name (FQDN) or the the global VIP address, `185.46.212.80`. This parameter is optional if the default route or `185.46.212.80` is routed to the Cloud Connector.
-
**ONBOARD="EEE"**: Replace `"EEE"` with the default onboarding behavior (`0` or `1`).
When you install Zscaler Client Connector for VDI, the default behavior for the CLI onboard flag is 1. Therefore, immediately after installation, Zscaler Client Connector for VDI automatically onboards itself to the Workload Communications (WLC) tenant. The alternate setting, 0, disables this automatic behavior. With the flag set to 0, Zscaler Client Connector for VDI does not onboard itself until you restart the VM or OS. In the case of a golden image clone process, Zscaler Client Connector for VDI does not onboard itself until you boot the child VMs for the first time.
-
**CONFIGREADTIMEOUT="FFF"**: Replace `"FFF"` with a value between 0 and 300 seconds. The default value is 0 seconds. The Zscaler service stores the user configuration file in the roaming folder and asks Zscaler Client Connector for VDI to wait a minimum of 0 and a maximum of 300 seconds for profiles to restore. After that time elapses, Zscaler Client Connector for VDI onboarding times out and requires intervention.
`CONFIGREADTIMEOUT` is only supported on Zscaler Client Connector for VDI version 1.1.0.8 and later.
- **HIDEAPPONUILAUNCH="GGG"**: Replace `"GGG"` with the application minimization behavior (`0` or `1`). The default value is 0. Entering `0` deactivates the minimization feature for Zscaler Client Connector for VDI. Entering `1` enables the minimization feature for Zscaler Client Connector for VDI, which minimizes the application when launching.
- **USEEMBEDDEDBROWSER="HHH"**: Replace `"HHH"` with the embedded browser behavior (`0` or `1`). The default value is 1. Entering `0` disables the embedded browser feature for Zscaler Client Connector for VDI. Entering `1` enables the embedded browser feature for Zscaler Client Connector for VDI, which avoids an external browser appearing during authentication.
-
**SHOWREAUTHNOTIFICATION="III"**: Replace `"III"` with the reauthentication notification behavior (`0` or `1`). The default value is 1. Entering `0` disables the reauthentication notification, which prevents it from appearing. Entering `1` enables the reauthentication notification, which allows it to appear.
`SHOWREAUTHNOTIFICATION` is only supported on Zscaler Client Connector for VDI version 1.7.0.4 and later.
The following image is an example of a command line that uses all the available install options described above:
![Administrator Command Prompt for install options for Zscaler VDI Agent. ](/downloads/cloud-branch-connector/zscaler-client-connector-vdi-management/customizing-zscaler-client-connector-vdi-install-options-msi/vdi-installation-parameters.png)
[][]To deploy Zscaler Client Connector for VDI with Microsoft Intune:
- Confirm that Zscaler Client Connector for VDI is enrolled with Microsoft Intune. For more information about enrolling devices with Microsoft Intune, refer to the [Microsoft documentation](https://learn.microsoft.com/en-us/mem/intune/fundamentals/deployment-guide-enrollment).
- Log in to the Microsoft Azure Portal.
- Go to **Services** > **Intune**.
- Click the **Intune **icon. You are redirected to the** Microsoft Endpoint Manager**.
- From the **Microsoft Endpoint Manager**, select **Apps **> **All Apps**.
- Click **Add**.
- For** App Type**, select **Line-of-business app**.
- Upload the `ZCCVDIInstaller.msi`** **file to** App Package File**.
- Click **OK**.
- In the** App Information** section:
- **Name**: Enter a name.
- **Description**: Enter a description.
- **Publisher**: Set the publisher as **Zscaler**.
- **Ignore app version**: Select **Yes**.
- **Command Line Arguments**: Enter `PROVURL="AAA" TOKEN="BBB" mode="CCC" SERVERIP="DDD" ONBOARD="EEE" CONFIGREADTIMEOUT="FFF" HIDEAPPONUILAUNCH="GGG" USEEMBEDDEDBROWSER="HHH" SHOWREAUTHNOTIFICATION="III"` where `"AAA"` is the provisioning URL, `"BBB"` is the token value, `"CCC"` is the tunneling mode (A2A or P2P), `"DDD"` is the IP address of the load balancer hosting Cloud Connector or Branch Connector, `"EEE"` is the default onboarding behavior, `"FFF"` is how long the Zscaler service stores the user configuration file in the roaming folder, `"GGG"` is the application minimization behavior, `"HHH"` is the embedded browser behavior, and `"III"` is the reauthentication notification behavior.
- On the **Assignments **tab, under the **Required** category, click **Add group **to add the appropriate groups that must be included.
- Click **Next**.
- Click **Review and Create**.
- Click** Create**.
[]
If you manually create the hKey in the Windows registry path `L"SOFTWARE\\Zscaler Inc.\\ZScaler VDI"`, you can use the `OnboardOnStart` registry option to override the `ONBOARD` installation parameter value (i.e., `ONBOARD=0` or `ONBOARD=1`). To make the `OnboardOnStart` registry option take precedence, you can add the `DWORD` value, or `dwValue`, as `0` or `1`. You can add the `DWORD` value in the registry for Zscaler to assign the `DWORD` value with the name `OnboardOnStart` and the data, or the registry value, as `0` or `1`. When you deploy a child image, Zscaler recommends removing the registry key so that the installation parameter can take precedence.
[See image.](#OnboardOnStart)
The following table describes how registry parameter values override installation parameter values:
| **Registry Value** | **Result** |
| ------------------ | ---------- |
| `OnboardOnStart=0` | If you add the registry key `dwValue=0`, Zscaler Client Connector for VDI does not onboard, even on system reboot. The registry value overrides the installation parameter `ONBOARD` value. |
| `OnboardOnStart=1` | If you add the registry key `dwValue=1`, Zscaler Client Connector for VDI onboards for all conditions. The registry value overrides the installation parameter `ONBOARD` value. |
[]
![The Windows Registry Editor showing the OnboardOnStart registry option.](/downloads/tech-pubs-drafts/cloud-connector-draft-articles/customizing-zscaler-client-connector-vdi-install-options-msi-draft-doc-56571/zccvdionboardonstart.png)