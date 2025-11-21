# Using Fiddler with Zscaler Client Connector
Source: https://help.zscaler.com/zscaler-client-connector/using-fiddler-zscaler-app
PDF: https://help.zscaler.com/pdf/com/en/1333356.pdf

To use the Telerik Fiddler application with Zscaler Client Connector, you must configure Zscaler Client Connector to use a PAC file to point to a specific port. Then, you must ensure that Fiddler is listening to that port.
At a high level, the flow of traffic should be: Browser > Fiddler > Zscaler Client Connector > Destination Page.
To learn more, see [Best Practices for Using PAC Files with Zscaler Client Connector](/zscaler-client-connector/best-practices-using-pac-files-zscaler-app).
Configuring Zscaler Client Connector and Fiddler
For more information on Fiddler, refer to the [Telerik documentation](https://www.telerik.com/support). The version used for the following steps is Fiddler 5.0.20182.28034.
To use Fiddler with Zscaler Client Connector:
- [1. Create a custom PAC file.](#Step-1)
- [2. Add the PAC file to a forwarding profile.](#Step-2)
- [3. Add the forwarding profile to an app profile.](#Step-3)
- [4. Configure the proxy and port for Fiddler.](#Step-4)
After you finish the configuration for both Zscaler Client Connector and Fiddler:
- Enroll in Zscaler Client Connector if you have not already.
- When** Internet Security** for Zscaler Client Connector is **ON**, you can open and use Fiddler.
Ignore any errors that Fiddler displays during startup.
[]To learn more about creating a custom PAC file, see [Writing a PAC File](/zia/writing-pac-file).
Create a custom PAC file with the following return statement:
return "PROXY 127.0.0.1:<Port for Fiddler>; PROXY ${ZAPP_LOCAL_PROXY};";
You must add the port to the return statement. For example, if you choose port 8888, then the return statement is as follows:
return "PROXY 127.0.0.1:8888; PROXY ${ZAPP_LOCAL_PROXY};";
You can host the PAC file in the Zscaler Admin Portal. To learn more, see [Adding a Custom PAC File to the ZIA Admin Portal](/zia/how-do-i-use-custom-pac-file-forward-traffic-zia#AddCustomPAC).
If you want to debug on a local web server, the browser’s PAC file may ignore the request for 127.0.0.1. As a workaround, create a host file entry pointing to 127.0.0.1(e.g., 127.0.0.1  server.local).
This step is not required if you are using Fiddler to automatically configure the system proxy, as Fiddler manages the system proxy settings.
[][Create a new forwarding profile](/zscaler-client-connector/configuring-forwarding-profiles-zscaler-app) or update an existing one, and then add the custom PAC file.
You must configure the forwarding profile with the following settings:
- Select **Tunnel with Local Proxy **or **Tunnel** mode for any application network (i.e., On Trusted Network, VPN Trusted Network, Off Trusted Network).
If you have configured Fiddler to automatically populate system proxy settings, you must use **Tunnel** mode and not **Tunnel With Local Proxy** mode. This is because the Zscaler Client Connector enforces its own system proxy in **Tunnel With Local Proxy** mode.
- For the **Use Automatic Configuration Script** field, click the checkbox and enter the custom PAC URL.
The PAC URL in this example is http://pac.zscaler.net/safemarch.net/fiddler.
![Adding a custom PAC file to a Zscaler Client Connector forwarding profile](/downloads/z-app/knowledge-base/using-fiddler-zscaler-app/fiddler-forwarding-profile.png)
[][Create a Zscaler Client Connector profile](/zscaler-client-connector/configuring-zscaler-app-profiles) or update an existing one, and then add the configured forwarding profile.
The forwarding profile in this example is Fiddler.
You must configure the app profile with the following settings:
- The **Rule Order** must be **1**.
- The app profile must be enabled.
- The **Disabled Loopback Restriction** switch must be enabled.
![Adding the forwarding profile to a Zscaler Client Connector profile](/downloads/z-app/knowledge-base/using-fiddler-zscaler-app/fiddler-app-profile.png)
[]To configure Fiddler:
- Open the Fiddler application.
- Go to **Tools** > **Options…**
![Navigating to the Fiddler options menu to configure settings for Zscaler Client Connector](/downloads/z-app/knowledge-base/using-fiddler-zscaler-app/fiddler-2.png)
- In the **Options** window, click the **Connections** tab and do the following:
- **Fiddler listens on port**: Enter the port that you configured in the forwarding profile PAC file.
The port in this example is 8888.
![Configuring Fiddler to listen to the port from the Zscaler Client Connector forwarding profile PAC file](/downloads/z-app/knowledge-base/using-fiddler-zscaler-app/fiddler-3.png)
- Click the** Gateway** tab and do the following:
- **Manual Proxy Configuration**: Select this option. In the first field, enter the following proxy string.
http=127.0.0.1:<Zscaler Client Connector Port>;https=127.0.0.1:<Zscaler Client Connector Port>;ftp=127.0.0.1:<Zscaler Client Connector Port>;
You must add [the port that Zscaler Client Connector listens on](/zscaler-client-connector/configuring-port-zscaler-app-listen) to the proxy string. For example, if Zscaler Client Connector listens on port 9000, then the proxy string is the following:
http=127.0.0.1:9000;https=127.0.0.1:9000;ftp=127.0.0.1:9000;
Optionally, to debug on a local web server, enter Bypass list: <local>; in the second **Manual Proxy Configuration** field.
![Configuring Fiddler manual proxy configuration settings with the port Zscaler Client Connector listens on](/downloads/z-app/knowledge-base/using-fiddler-zscaler-app/fiddler-4.png)
If you are using the Fiddler AutoResponder feature, the **Accept all CONNECTs** option must be disabled.
- Click **OK**.