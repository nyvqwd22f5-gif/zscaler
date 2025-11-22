# Distributing a PAC File URL to Users
Source: https://help.zscaler.com/zia/distributing-pac-file-url-my-users
PDF: https://help.zscaler.com/pdf/com/en/1399431.pdf

If your organization uses Active Directory along with Microsoft Internet Explorer, Microsoft Edge, Google Chrome, Mozilla Firefox, or Opera, you can use Group Policy Objects (GPOs) to distribute a PAC file URL to all Windows (Professional, Enterprise, Education, and Ultimate Editions Only) and Windows Server devices in your organization. When you configure Internet Explorer to use a PAC file, browsers such as Microsoft Edge, Google Chrome, and Opera follow the same configuration. However, Mozilla Firefox requires a separate method of configuration. To distribute a PAC file URL to Firefox browsers using GPOs, download the ADMX templates for Firefox at [https://support.mozilla.org/en-US/kb/customizing-firefox-using-group-policy-windows](https://support.mozilla.org/en-US/kb/customizing-firefox-using-group-policy-windows).
Distributing a PAC File URL To Mozilla Firefox
To distribute a PAC file URL to Mozilla Firefox:
- [1. Download and install GPO templates for Mozilla Firefox.](#install-mozilla-gpo)
- [2. Create a new GPO.](#create-gpo)
- [3. Deploy and enforce PAC file setting for Mozilla Firefox using GPO.](#deploy-enforce-pac)
Distributing a PAC File URL To Other Browsers
To distribute a PAC file URL using browsers other than Mozilla Firefox, such as  Microsoft Internet Explorer, Microsoft Edge, Google Chrome, or Opera:
- [1. Create a new GPO.](#create-gpo-other-browsers)
- [2. Distribute the PAC file URL.](#distribute-pac-other-browsers)
- [3. Enforce the PAC file setting.](#enforce-pac-other-browsers)
[]Mozilla Firefox does not follow the system proxy configuration like the other browsers do. You must download and install separate Group Policy templates for Firefox to use GPOs to deploy and enforce the PAC file setting.
- [Download and install Mozilla Firefox GPO templates for Windows Server Core.](#windows-server-core)
- [Download and install Mozilla Firefox GPO templates for Windows Server with Desktop Experience.](#windows-desktop-experience)
- []Log in to a domain-joined Windows 10 client as a user with administrative permissions on the domain.
- Open a remote PowerShell session into your domain controller.
- Execute the following PowerShell commands:
Invoke-WebRequest -Uri https://github.com/mozilla/policy-templates/archive/master.zip -OutFile .\master.zip
Expand-Archive -Path .\master.zip -DestinationPath .\master
Copy-Item -Path .\master\policy-templates-master\windows\*.admx -Destination C:\Windows\PolicyDefinitions
Copy-Item -Path .\master\policy-templates-master\windows\en-US\*.adml -Destination C:\Windows\PolicyDefinitions\en-US
If you are using a Group Policy Central Store, replace the file path in the `Destination` parameter with that of your Central Store.
- []Log in to your domain controller with administrative permissions on the domain.
- Open the **Start Menu >** **Windows PowerShell** folder. Right-click on **Windows PowerShell** and select **Run as administrator**.
- Execute the following PowerShell commands:
Invoke-WebRequest -Uri https://github.com/mozilla/policy-templates/archive/master.zip -OutFile .\master.zip
Expand-Archive -Path .\master.zip -DestinationPath .\master
Copy-Item -Path .\master\policy-templates-master\windows\*.admx -Destination C:\Windows\PolicyDefinitions
Copy-Item -Path .\master\policy-templates-master\windows\en-US\*.adml -Destination C:\Windows\PolicyDefinitions\en-US
If you are using a Group Policy Central Store, replace the file path in the Destination parameter with that of your Central Store.
[]You can use the Group Policy Management Console (GPMC) to create a new GPO for distributing a PAC file URL to the Windows devices in your organization. To access the GPMC on a Windows Server Core, you need a Windows client machine (Professional, Enterprise, Education, and Ultimate Editions Only) that is installed with Remote Server Administration Tools (RSAT).
Ensure that your client machine is compatible with your server version and has the appropriate administrative permissions on your domain.
On a Windows Server with Desktop Experience, the GPMC is already installed.
To create a new GPO:
- Open the GPMC.
- In the **Group Policy** management tree, navigate to the forest, domain or organizational unit to which you are applying the GPO.
- Right-click on the forest, domain or organizational unit and select **Create a GPO in this domain, and Link it here**.
The **New GPO** window appears.
- In the** New GPO **window, provide a name for the GPO and leave the **Source Starter GPO** field blank.
- Click **OK**.
A new GPO is created under your domain or organizational unit.
- Right-click on the newly created GPO and then select **Link Enabled**.
[See image.](#link-enabled)
- Select your forest, domain or organizational unit and then move the new GPO to **Link order 1** under the **Linked Group Policy Objects** tab.
[See image.](#link-order-new-gpo)
It may take up to 20 minutes for the GPO to be replicated to your Windows client machine.
[]To deploy and enforce the PAC file setting for Mozilla Firefox:
- Open the GPMC.
- Navigate to the domain or organizational unit to which you applied the GPO and expand it.
- Right-click on the newly created GPO and select **Edit**.
- To apply the policy to the entire computer, navigate to **Computer Configuration > Policies > Administrative Templates > Mozilla > Firefox**.
[See image.](#ff-gpmc-comp-config)
- To apply the policy only for the domain users, navigate to **User Configuration > Policies > Administrative Templates > Mozilla > Firefox**.
[See image.](#ff-gpmc-user-config)
- From the Firefox folder, double-click **Proxy Settings**.
The **Proxy Settings** window appears.
- Under **Proxy Settings**, select **Enabled**.
- Under **Options**, configure the following fields:
[See image.](#ff-proxy-setting)
- **Don’t allow proxy settings to be changed:** Select this option to enforce the PAC file settings.
- **Connection Type:** Select **Manual proxy configuration** to configure your custom proxy settings. To use the proxy configured in your system, choose **Use system proxy settings**.
- **SOCKS Version:** Select **SOCKS v5**.
- **Automatic proxy configuration URL:** Enter the PAC file URL in this field if you selected **Manual proxy configuration** in the **Connection Type** field.
- Click **OK**.
Users can no longer modify the proxy settings in Mozilla Firefox.
[]![Computer configuration for Firefox in GPMC](/downloads/zia/documentation-knowledgebase/forwarding-your-traffic/pac-files/using-pac-files/distributing-pac-file-url-my-users/ZIA-firefox-gpmc-computer-config.png)
[]![User configuration for Firefox in GPMC](/downloads/zia/documentation-knowledgebase/forwarding-your-traffic/pac-files/using-pac-files/distributing-pac-file-url-my-users/ZIA-firefox-gpmc-user-config.png)
[] ![Proxy setting for Firefox browser to distribute a PAC file URL](/downloads/zia/documentation-knowledgebase/forwarding-your-traffic/pac-files/using-pac-files/distributing-pac-file-url-my-users/ZIA-firefox-proxy-setting.png)
[]You can use the GPMC to create a new GPO for distributing a PAC file URL to the Windows devices in your organization. To access GPMC from a Windows server core, you need a Windows client machine (Professional, Enterprise, Education or Ultimate Editions Only) that is installed with Remote Server Administration Tools (RSAT).
Ensure that your client machine is compatible with your server version and has the appropriate administrative permissions on your domain.
On a Windows server with Desktop Experience, the GPMC is already installed.
To create a new GPO:
- Open the GPMC.
- In the **Group Policy** management tree, navigate to the forest, domain or organizational unit to which you are applying the GPO.
- Right-click on the forest, domain or organizational unit and select **Create a GPO in this domain, and Link it here**.
The **New GPO** window appears.
- In the** New GPO **window, provide a name for the GPO and leave the **Source Starter GPO** field blank.
- Click **OK**.
[]To distribute the PAC file URL using the GPO:
- Open the GPMC.
- Navigate to the domain or organizational unit to which you applied the GPO and expand it.
- Right-click on the newly created GPO and select **Edit**.
- Navigate to **User Configuration > Preferences > Control Panel Settings**.
- Right-click on **Internet Settings** and select **New > Internet Explorer 10**.
[See image.](#ie-internet-settings)
- From the **Connections** tab, click **LAN settings**.
[See image.](#ie-10-properties-lan-conn)
- Enter the PAC file URL in the **Address** field.
If you see a red dotted underline in the **Address** field, ensure to place your cursor in the text box and press the **F6** function key. This enables the field and is indicated by a solid green underline.
[See image.](#ie-pac-url)
- Click **OK**.
- (Optional) If you want to apply the GPO to the entire computer irrespective of the signed in user:
- Navigate to **Computer Configuration > Policies > Administrative Templates > Windows Components > Internet Explorer** in the GPMC.
- From the **Internet Explorer** folder, double-click **Make proxy settings per-machine (rather than per-user)**.
The **Make proxy settings per-machine (rather than per-user)** window appears.
- Under **Make proxy settings per-machine (rather than per-user)**, select **Enabled** and click **OK**.
[See image.](#optional-make-proxy-settings)
You can use the Group Policy Results wizard to verify the policy settings of the users or computers in the domain.
[![Screenshot of Link Enabled option selected for the new GPO ](/downloads/zia/documentation-knowledgebase/forwarding-your-traffic/pac-files/using-pac-files/distributing-pac-file-url-my-users/ZIA-distrubuting-pac-file-link-enabled-page.png)
]
[![Screenshot of the new GPO's Link Order in the organizational unit page](/downloads/zia/documentation-knowledgebase/forwarding-your-traffic/pac-files/using-pac-files/distributing-pac-file-url-my-users/ZIA-distrubuting-pac-file-rearraging-link-order.png)
]
[] ![Internet settings for IE in GPMC](/downloads/zia/documentation-knowledgebase/forwarding-your-traffic/pac-files/using-pac-files/distributing-pac-file-url-my-users/ZIA-ie-internet-settings.png)
[] ![Internet Explorer Properties in GPMC ](/downloads/zia/documentation-knowledgebase/forwarding-your-traffic/pac-files/using-pac-files/distributing-pac-file-url-my-users/ZIA-gpmc-ie10-properties.png)
[] ![Internet Explorer PAC URL Settings in GPMC](/downloads/zia/documentation-knowledgebase/forwarding-your-traffic/pac-files/using-pac-files/distributing-pac-file-url-my-users/ZIA-ie-pac-url.png)
[]![Internet Explorer Optional configuration in GPMC](/downloads/zia/documentation-knowledgebase/forwarding-your-traffic/pac-files/using-pac-files/distributing-pac-file-url-my-users/ZIA-ie-optional-config.png)
[]You can enforce the PAC file setting so that the users in your organization cannot modify it even when logged in as an administrator.
To enforce the PAC file setting:
- Open the GPMC.
- Navigate to the domain or organizational unit to which you applied the GPO and expand it.
- Right-click on the newly created GPO and select **Edit**.
- To apply the policy to the entire computer, navigate to **Computer Configuration > Policies > Administrative Templates > Windows Components > Internet Explorer**.
- To apply the policy only for the domain users, navigate to **User Configuration > Policies > Administrative Templates > Windows Components > Internet Explorer**.
- From the **Internet Explorer** folder, double-click **Disable changing Automatic Configuration settings**.
The **Disable changing Automatic Configuration settings** window appears.
- Under **Disable changing Automatic Configuration settings**, select **Enabled** and click **OK**.
[See image.](#disable-change-auto-config)
- Double-click **Prevent changing proxy settings**.
The **Prevent changing proxy settings** window appears.
- Under **Prevent changing proxy settings**, select **Enabled** and click **OK**.
[See image.](#prevent-change-proxy-setting)
Users can no longer change the proxy settings.
Based on your authentication configuration, your users must log in to the service at least once for the service to start protecting their web traffic. If the users log into a captive portal, such as those present on public Wi-Fi networks (e.g. Starbucks and McDonalds), they must close the browser and open it again to reload the PAC file. The browser tries to fetch the PAC file only when there is a PAC URL timeout.
[]![Internet Explorer Disable Changing Auto Config Settings](/downloads/zia/documentation-knowledgebase/forwarding-your-traffic/pac-files/using-pac-files/distributing-pac-file-url-my-users/ZIA-ie-disable-auto-config.png)
[] ![Internet Explorer Prevent Changing Proxy Settings](/downloads/zia/documentation-knowledgebase/forwarding-your-traffic/pac-files/using-pac-files/distributing-pac-file-url-my-users/ZIA-ie-prevent-change-proxy.png)