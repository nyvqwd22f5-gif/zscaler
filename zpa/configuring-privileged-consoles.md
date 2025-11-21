# Configuring Privileged Consoles
Source: https://help.zscaler.com/zpa/configuring-privileged-consoles
PDF: https://help.zscaler.com/pdf/com/en/1485121.pdf

After you have added an application segment with Privileged Remote Access, you can go to the Privileged Consoles page. For a complete list of ranges and limits per feature, see [Ranges & Limitations](/zpa/ranges-limitations).
When configuring a privileged portal within the Default Microtenant, you can link a maximum number of privileged consoles to the privileged portal. To learn more, see [Ranges & Limitations](/zpa/ranges-limitations).
To add a privileged console:
- Go to **Resource Management **>** Privileged Remote Access **>** Privileged Consoles**.
- Click **Add Console**. The **Add Console** window appears.
- In the **Add Console** window:
- [1. Console Type](#ApplicationSegments)
- [2. Consoles](#LinkType)
- [3. Review](#Review)
- []Configure the following privileged console information as needed:
-
**Privileged Remote Access Portal**: Select an existing portal(s) from the drop-down menu.
You can select both the Default [Microtenant](/zpa/about-microtenants) portal and the Microtenant portals that are assigned to the Microtenants. The portals that are assigned to the Microtenants are assigned by the Default Microtenant.
-
**Privileged Remote Access Applications**: Select an application(s) from the drop-down menu.
If you are using an application that is inherited from the Default Microtenant, Zscaler recommends that you check with the Default Microtenant admin to confirm if a privileged approval is required.
- Click **Next**.
[See image.](#ConsoleType)
- []On the **Consoles** tab, configure the following privileged console information as needed:
- **Name**: Enter a name for the privileged console. The name cannot contain special characters, with the exception of periods (.), hyphens (-), and underscores ( _ ).
- **Display on Console**: Enable to display the privileged console on the end user’s Privileged Remote Access portal.
- **Protocol**: Select the protocol type for the privileged console. There are 4 types available to use for Privileged Remote Access: VNC, RealVNC, SSH, or RDP.
If you select VNC or RealVNC and are enabling [File Transfer](/zpa/uploading-and-downloading-file-transfer) in a [privileged capabilities policy](/zpa/configuring-privileged-capabilities-policies), the SFTP service needs to be enabled on the VNC or RealVNC server prior to creating the privileged capabilities policy, and the authentication for SFTP needs to match the VNC or RealVNC configuration. If SFTP is not configured, end users cannot connect to the privileged console.
SSH-enabled privileged consoles support modern elliptic-curve host algorithms (i.e., ecdsa-sha2-nistp521, ecdsa-sha2-nistp384, and ecdsa-sha2-nistp256).
- **Domain**: Enter a valid domain name.
- **Port**: Enter the port number used for the privileged console.
- **Description**: The description for the privileged console, if available.
- **Logo/Favicon**: The logo represents if it is a VNC, RealVNC, SSH, or RDP connection.
- Click **Next**.
[See image.](#Consolestab)
[]On the **Review** tab, review the console's configuration, then click **Save**.
[See image.](#Reviewtab)
[][![Add Console window with Console Type tab](/downloads/Add%20Console%20Window%20Console%20Type_0.png)
]
[][![Add Console window with Consoles tab](/downloads/zpa/configuring-privileged-consoles/Add%20Console%20Window%20Consoles.png)
]
[][![Add Console window with Review tab](/downloads/zpa/user-portal/configuring-application-links-user-portals/Add%20Console%20Window%20Review.png)
]