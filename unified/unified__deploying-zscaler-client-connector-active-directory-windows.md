# Deploying Zscaler Client Connector with Active Directory for Windows
Source: https://help.zscaler.com/unified/deploying-zscaler-client-connector-active-directory-windows
PDF: https://help.zscaler.com/pdf/com/en/1491971.pdf

This guide is for admins only. If you are an end-user, contact your organization’s administrator for deployment-related details.
This article provides instructions for deploying Zscaler Client Connector in an Active Directory (AD) environment. It also provides details on how to complete a silent installation on users' devices.
To deploy Zscaler Client Connector in an AD environment:
- [1. Prepare your AD environment.](#Prepare-your-AD-Environment)
- [2. Create a network share.](#Create-Network-Share)
- [3. Create a Group Policy (GPO) for Zscaler Client Connector installation.](#Create-Group-Policy)
- [4. Install Zscaler Client Connector on the OU's Windows systems.](#install-client-conn-ou-windows)
- [5. Verify the installation of Zscaler Client Connector on the OU's Windows systems.](#verify-installation)
- []Log in to the AD environment (Domain Controller) as an admin user.
- Ensure that you have a well-defined organizational unit (OU) in the AD where you want to deploy the app. If you do not have an appropriate OU, create one by going to **Server Manager** >** Active Directory Domain Services **>** ****[domain name]**** **> **New** >** Organizational Unit**.
[See image.](#PrepADEnv1)
Alternatively, you can also apply Group Policy (GPO) to a group. If you do not have an appropriate group, create one by going to **Server Manager** > **Active Directory Domain Services** > **[domain name]**** **> **New** > **Group**.
- Ensure that the newly created OU has all the users and computer systems on which you want to deploy Zscaler Client Connector.
[See image.](#PrepADEnv2)
[]You must ensure that Zscaler Client Connector installer is accessible to all relevant computers by creating a network share on the drive in the Domain Controller.
- Create a folder, then right-click **Properties**. Click **Enable Sharing**, and in the **Security** tab, provide the relevant domain Administrators and Authenticated Users with access permissions.
[See image.](#CreateNetworkShare1)
- Copy Zscaler Client Connector installer to this folder.
- Map this folder as a network drive and make sure it is accessible by client computers across the relevant OU within the domain.
[See image.](#CreateNetworkShare2)
[]You must create a new GPO policy for your OU in order to install Zscaler Client Connector.
- Go to **Run** and enter gpmc.msc to open the Group Policy Management editor.
- Select your OU, then right-click and select **Create a GPO in this domain, and Link it here**.
[See image.](#CreateGPOPolicy)
- Under **Security Filtering**, specify the users, groups, and computers to which the policy must apply.
[]You must now edit the GPO policy for the OU in order to install Zscaler Client Connector on the OU's Windows systems. You can use either the MSI or EXE file, but Zscaler recommends using the MSI file because it integrates well with GPO.
- [Deploying the MSI file to install Zscaler Client Connector](#MSI)
- [Deploying the EXE file to install Zscaler Client Connector](#EXE)
[]These steps provide details on how to complete a silent installation of the app on users' devices using an MSI file.
If you want to customize the MSI file and add install options (for example, you want to require users to enroll with Zscaler Client Connector before accessing the Internet), you must create an MST file before completing the steps below. To learn more, see [Customizing Zscaler Client Connector with Install Options (MSI)](/unified/customizing-zscaler-client-connector-install-options-msi).
- Right-click on the GPO Policy you created and select **Edit**.
- Go to **User Configuration **>** Policies **>** Software Settings **>** Software installation**.
- Right-click and select **New** > **Package**.
- Double-click the MSI Windows Installer Package.
- In the **Deploy Software** window, select **Advanced** for the deployment method.
- Click **OK**.
[See image.](#deploy)
- To install the app on in silent mode, do the following, in **Zscaler Properties** window, click the **Deployment** tab. Do the following:
- For **Deployment type**, select **Assigned**.
- For **Deployment options**, select **Install this application at logon**.
- For **Installation user interface option**, select **Basic**.
[See image.](#props)
- Do one of the following:
- If you did not create an MST, click **OK**.
- If you created an MST:
- Go to the **Modifications** tab.
- Click **Add...**.
- Select the MST file.
- Click **OK**.
[See image.](#modification)
Zscaler Client Connector is automatically deployed the next time users' log into to their computers.
[]![Selecting the deployment method for deploying the Zscaler Client Connector](/downloads/zia/documentation-knowledgebase/forwarding-your-traffic/zscaler-app/downloading-and-deploying-zscaler-app/deploying-zscaler-app-windows-active-directory/e57db634-7220-4fb1-9775-f4ddf0383bf9_display.png)
[]![The Deployment tab of the Zscaler Properties window](/downloads/zia/documentation-knowledgebase/forwarding-your-traffic/zscaler-app/downloading-and-deploying-zscaler-app/deploying-zscaler-app-windows-active-directory/fb2072d2-d83f-4938-b7f7-26192edf23dc_display.png)
[]![The Modifications tab of the Zscaler Properties window](/downloads/zia/documentation-knowledgebase/forwarding-your-traffic/zscaler-app/downloading-and-deploying-zscaler-app/deploying-zscaler-app-windows-active-directory/f33e5fad-5441-496f-812a-f204a6badb80_display.png?1603366354)
[]Below are instructions for defining a system start-up script to install Zscaler Client Connector on user devices with an EXE file.
- Select the **GPO Policy** and go to **Computer Configuration **>** Policies **>** Windows Settings **>** Scripts **>** Startup**.
- Double-click to open.
- Select **Add** to open a new wizard.
- In the **Script Name** field, specify the absolute path to the EXE file. For example,* *\\SERVER\\share\Zscaler-windows-1.1.0.000213-installer.exe.
- In the **Script Parameters **field, do one of the following:
- If you want to deploy the EXE file without any install options, leave the **Script Parameters **field blank.
- If you want to customize the EXE file and include install options (e.g., you want to require users to enroll with the app before they can access the Internet), add the options to the **Script Parameters **field as described in [Running the EXE File with Command-Line Options](/unified/customizing-zscaler-client-connector-install-options-exe).
- Click **OK**.
- Click** Apply**,** **then run the following command:
gpupdate.exe /force
- Remotely reboot the OU computers on which you want to install the app using the following command:
shutdown.exe –r –m \\<Remote Computer Name> –t 0
- []Once the OU system is rebooted, log in to a remote system.
- Verify that the app is running in the desktop foreground and that the desktop shortcut is installed.
![The Zscaler Client Connector and the desktop shortcut](/downloads/zia/documentation-knowledgebase/forwarding-your-traffic/zscaler-app/downloading-and-deploying-zscaler-app/deploying-zscaler-app-windows-active-directory/dd2f48bd-aa85-4a08-b9fc-e49ede69f1f0_display.png)
[]![Creating a new organizational unit for deploying the Zscaler Client Connector](/downloads/zia/documentation-knowledgebase/forwarding-your-traffic/zscaler-app/downloading-and-deploying-zscaler-app/deploying-zscaler-app-windows-active-directory/96ba9413-4a69-4536-8f77-1fd654e7089c_display.png)
[]![Users and computer systems on which to deploy Zscaler Client Connector in the OU](/downloads/zia/documentation-knowledgebase/forwarding-your-traffic/zscaler-app/downloading-and-deploying-zscaler-app/deploying-zscaler-app-windows-active-directory/046c76fd-24e7-42c9-86d0-e87174b7893a_display.png)
[]![Providing access permissions](/downloads/zia/documentation-knowledgebase/forwarding-your-traffic/zscaler-app/downloading-and-deploying-zscaler-app/deploying-zscaler-app-windows-active-directory/364d78e5-10a6-49c8-a60c-96fdf613f05f_display.png)
[]![Mapping the folder as a network drive](/downloads/zia/documentation-knowledgebase/forwarding-your-traffic/zscaler-app/downloading-and-deploying-zscaler-app/deploying-zscaler-app-windows-active-directory/10b5339c-523e-4f06-b8c0-b4db7e1351ee_display.png)
![The folder mapped as a network drive](/downloads/zia/documentation-knowledgebase/forwarding-your-traffic/zscaler-app/downloading-and-deploying-zscaler-app/deploying-zscaler-app-windows-active-directory/a452bebf-adc4-411a-b4b3-5c6e96c07f50_display.png)
[]![Creating a new GPO policy for the OU to install the Zscaler Client Connector](/downloads/zia/documentation-knowledgebase/forwarding-your-traffic/zscaler-app/downloading-and-deploying-zscaler-app/deploying-zscaler-app-windows-active-directory/2c96f578-400a-4c50-b123-32c631cebd6b_display.png?1603363977)