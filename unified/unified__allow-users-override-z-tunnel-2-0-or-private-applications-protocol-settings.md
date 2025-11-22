# Allow Users to Override Z-Tunnel 2.0 or Private Applications Protocol Settings
Source: https://help.zscaler.com/unified/allow-users-override-z-tunnel-2-0-or-private-applications-protocol-settings
PDF: https://help.zscaler.com/pdf/com/en/1496076.pdf

When you enable **Allow end user to override Z-Tunnel 2.0 or ZPA protocol settings**, your end users can change the default parameters for Zscaler Tunnel (Z-Tunnel) 2.0 or Private Applications protocol settings by browsing to a website. To learn more, see [About User Privacy](/unified/about-user-privacy).
Override settings are applied per session and continue until the next keepalive is sent, or the user logs out and then logs back in again.
![Override Z-Tunnel 2.0 ZPA Protocol Settings](/downloads/client-connector-allow-user-override-ztunnel.png)
Overriding Z-Tunnel 2.0 or Private Applications Protocol Settings
Overriding Z-Tunnel 2.0 or Private Applications Protocol settings allows you to configure additional settings by browsing to a local configuration website. To override Z-Tunnel 2.0 or Private Applications Protocol settings:
- Enable **Allow end user to override Z-Tunnel 2.0 or ZPA protocol settings** in the Admin Portal.
- In your browser, enter `http://localhost:9000/zconfig` and browse to the website.
- On the website, in the **Zscaler User Configuration** window, configure the following settings:
- **PAC**: Enter a link.
- **PROTOCOL**: Select **Default**, **DTLS**, or **TLS**.
- **MTU**: Select **1200**, **1300**, **1350**, or **1400** for the Maximum Transmission Unit (MTU) value. The default value is 1,500 bytes.
- **DEBUG**: Select **Enabled** or **Disabled**. This setting determines the status of the log mode in Zscaler Client Connector.
- **LONG RUNNING PACKET CAPTURE**: Select **Enabled** or **Disabled**. The default running time is 5 minutes.
-
**IGNORE KEEPALIVE FAILURE**: Select **Enabled** or **Disabled**.
[See image.](#overridingtunnelzpa)
- Click **Save**.
[]![The Zscaler User Configuration window where additional Zscaler Client Connector settings are configured.](/downloads/Client%20Connector%20Zscaler%20User%20Configuration.png)