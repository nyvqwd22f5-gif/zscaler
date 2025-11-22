# Installing Landmine Agents on Windows Using MECM or SCCM
Source: https://help.zscaler.com/deception/installing-landmine-agents-windows-using-mecm-or-sccm
PDF: https://help.zscaler.com/pdf/com/en/1531326.pdf

This article provides instructions for installing a landmine agent on the Windows platform using Microsoft Endpoint Configuration Manager (MECM) (formerly known as Microsoft System Center Configuration Manager (SCCM)).
Prerequisites
Before installing a landmine agent, make sure that the following prerequisites are met:
-
Windows installer and .NET framework
- 64-bit versions of Windows 10
- .NET version 4.6.1 or later (Zscaler recommends using the latest version of .NET framework)
- All Windows 10 editions include the .NET framework as an OS component.
Microsoft Windows 7, Windows 8, and Windows 8.1 are not supported.
- You must have a network file share that is accessible to all systems. This can be the system volume (SYSVOL) file share or any other file share that is accessible to all systems where the landmine agents are deployed.
- RAM: 100 MB of free memory
- Storage: 1 GB of free storage, preferably in an SSD
- Network Connectivity: A minimum of 256 Kbps internet bandwidth and an open port 443 on the systems where the agent is installed to connect to the Zscaler Deception. This connection is proxy-aware, and you can either use a statically defined proxy or the proxy configured for the `SYSTEM` user.
The resource requirements listed here are also the landmine agent's maximum limits of utilization.
Installing Agents on Windows Using MECM
Do not use the Windows MSI Installer with MECM. The landmine agents may not install properly using the MECM built-in MSI installation method.
To install a landmine agent on the Windows platform using MECM:
- [Step 1: Download and Publish the Installer](#download-publish-installer)
- [Step 2: Create an Application](#create-application)
- [Step 3: Deploy the Application](#deploy-application)
- [][Download the Windows EXE installer file](/deception/downloading-landmine-agents) from the Zscaler Deception Admin Portal.
- Copy the EXE file to a file share that is accessible to all systems or users.
- []Open MECM.
- Go to **Software Library** > **Overview** > **Application Management** > **Applications**.
- In the **Applications pane**, right-click on a blank area and select **Create Application**.
- After the **Create Application Wizard** opens, on the **General** page, select **Manually specify the application information.**
- Click **Next**.
- On the **General Information** page:
- **Name**: Enter the name of the application.
- **Software version**: Enter the software version of the EXE file and click **Next**.
- On the **Deployment Types** page, click **Add** to create a new deployment type.
- After the **Create Deployment Types Wizard** opens, on the **General** page:
- **Type**: Select **Script Installer** from the drop-down menu.
- Select **Manually specify the deployment type information**.
- Click **Next**.
- On the **General Information** page, enter a **Name** for the deployment type.
- On the **Content** page:
- **Content location**: Browse the location that contains the `Landmine.exe` file.
- **Installation program**: Enter "`Landmine.exe" /qn CMC=``<Deception Admin Portal instance name>`` REGKEY=``<Registration Token>`.
- **Uninstallation program**: Enter `msiexec /qn /x {94e4ac3b-2519-46eb-97bd-d6be9b6c8f55}`.
- Click **Next**.
- On the **Detection Method** page, click **Add Clause** to add a detection clause.
- On the **Detection Rule** page:
- **Setting Type**: Select **File System** from the drop-down menu.
- **Type**: Select **File** from the drop-down menu.
- **Path**: Enter or browse to the path where the landmine agent must be installed. This is usually `C:\ProgramData\``<Service name>`, where <`Service name>` is the name of the service specified in the Deception Admin Portal.
- **File or folder name**: Enter `<Service name>``.exe`.
- Unselect **This file or folder is associated with a 32-bit application on 64-bit systems**.
- Click **OK**.
-
On the **User Experience** page:
- **Installer behavior**: Select **Install for system** from the drop-down menu.
- **Installation program visibility**: Select **Hidden**.
- Click **Next**.
The application is created.
If the landmine service is renamed in the Deception Admin Portal, you must add a new detection clause to the system. Do not remove the existing detection clause as that might cause existing agents to not be detected.
- []Open MECM.
- Go to **Software Library** > **Overview** > **Application Management** > **Applications**.
- Select the application that you created and right-click.
- Select **Deploy** from the menu.
- After the **Deploy Software Wizard** opens, on the **General** page, select **All Desktops and Server Clients** from the** Collection** drop-down menu.
- Click **Next**.
- On the **Content** page, click **Add** to distribute the content for this application to a distribution point or a distribution point group.
- On the **Deployment Settings** page, in the **Purpose **field, select **Required** from the drop-down menu.
- Click **Next**.
- (Optional) On the **Scheduling** page, set a deployment schedule.
- On the **User Experience** page, in the **User notifications** field, select **Hide in Software Center and all notifications** from the drop-down menu.
- Click **Next**.
- Complete the application deployment.
The application is deployed. The value under **Compliance %** changes after the agents are deployed.