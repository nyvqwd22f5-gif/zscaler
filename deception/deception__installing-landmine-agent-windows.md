# Installing a Landmine Agent on Windows
Source: https://help.zscaler.com/deception/installing-landmine-agent-windows
PDF: https://help.zscaler.com/pdf/com/en/1531311.pdf

This article provides instructions for installing a landmine agent on the Windows platform using the command line interface (CLI).
Prerequisites
Before installing a landmine agent, ensure that your endpoints have:
-
Windows 10 (64-bit only) or Windows 11 (64-bit only) with Windows Installer and .NET version 4.6.1 or later
- Microsoft Windows 7, Windows 8, and Windows 8.1 are not supported.
- Zscaler recommends using the latest version of .NET framework. For Windows 10 version 1607 and earlier, installing the latest version of the .NET framework is mandatory for the installation to succeed.
- 100 MB of free memory
- 1 GB of free storage, preferably in an SSD
- A minimum of 256 Kbps internet bandwidth and an open outbound port 443 on the system where the agent is installed to connect to the Zscaler Deception Admin Portal. This connection is proxy ware, and you can either use a statically defined proxy or the proxy configured for the `SYSTEM` user.
The resource requirements listed here are also the landmine agent's maximum limits of utilization.
Installing a Landmine Agent on Windows
You can install a landmine agent on a single or multiple systems. If you install an agent on multiple systems, use a deployment management tool, such as Microsoft Endpoint Configuration Manager (MECM) (formerly known as Microsoft System Center Configuration Manager (SCCM)). Zscaler recommends installing landmine agents on a few systems prior to a broader deployment.
You can run the installation commands on an administrator command prompt, or use an automation tool that runs the commands as an administrator.
To install a landmine agent on Windows:
- [Download the Windows EXE installer](/deception/downloading-landmine-agents) file from the Deception Admin Portal.
- Start a command prompt as an administrator.
- Click **Start**.
- In the **Start Search** box, enter `cmd`, and then press `CTRL+SHIFT+ENTER`.
- When the **User Account Control** (UAC) dialog box appears, click **Yes**.
- In the command prompt, choose a command per your installation requirements:
-
Enter the following command to install the agent without proxies or debug logs:
Landmine.exe /qn CMC=<instance name> REGKEY=<Registration Token>
-
Enter the following command to install the landmine agent with debug logs stored in the `C:\agent-install.log` file:
Landmine.exe /qn CMC=<instance name> REGKEY=<Registration Token> /l*v C:\agent-install.log
-
Enter the following command to install the landmine agent with a proxy:
Landmine.exe /qn CMC=<instance name> REGKEY=<Registration Token> PROXIES=http://proxy-server:3128
The standalone landmine agent is a proxy-aware application. It can automatically detect and apply the proxy configurations if they are already available in the system.
The following table describes the installation parameters:
| Parameter | Description | Required |
| --------- | ----------- | -------- |
| `/qn` | Enables silent mode installation | Yes |
| `CMC=<instance name>` | The hostname of the Deception Admin Portal | Yes |
| `REGKEY=<Registration Token>` | The Agent Registration Token | Yes |
| `PROXIES=<Proxy String>` | Proxies to connect to the Deception Admin Portal. If there is more than one proxy, separate them with a comma. Make sure that there are no white spaces in the `PROXIES` parameter. | No |
| `/l*v <Path to Log File>` | Enables verbose logging and sets the destination log file path | No |
After you run the command, the landmine agent is installed and appears in the **Agents** table (**Settings **> **Endpoint Settings **> **Agents**).
Configuring Proxies
The standalone landmine agent is a proxy-aware application. It can automatically detect and apply the proxy configurations if they are already available in the system.
You can use the `PROXIES` parameter in the installation command to configure multiple proxies. The `PROXIES` parameter consists of a list of proxies separated by commas. When the landmine agent starts, it attempts to connect to the Deception Admin Portal using the list of proxies in a sequence from left to right. If the proxy is not configured, the agent attempts to connect to the Deception Admin Portal directly, or it uses a proxy configured for the `SYSTEM` user.
To configure multiple proxies, open the command prompt and enter the following command:
Landmine.exe /qn CMC=<instance name> REGKEY=<Registration Token> PROXIES=http://proxy-server/proxy.pac,http://user:password@proxy-server:8888,http://proxy-server:3128
After you run the command, the landmine agent connects to the Deception Admin Portal using one of the following methods:
- Downloads the PAC file from `http://proxy-server/proxy.pac` and uses the PAC file configuration to establish the connection.
- Connects via `http://user:password@proxy-server:8888/proxy`.
- Connects via `http://proxy-server:3128/proxy`.
If all of the above methods fail, the agent attempts to connect to the Deception Admin Portal using the `SYSTEM` users proxy. If this also fails, the agent attempts a direct no-proxy connection.
You can configure proxies using the following URL format:
http://[username:password]@<ip/host>:<port>
If the username and password have special characters (e.g., Username = user#2211 and password = pass@123), you must URL-encode them. For example:
http://user%232211:pass%40123@proxy-server-1:8888
You can perform URL encoding using the following PowerShell function:
Add-Type -AssemblyName System.Web; [System.Web.HttpUtility]::UrlEncode(<string>)
![URL encoding using the PowerShell function](/downloads/deception/deceive/endpoint-decoys/agents/download-and-install-landmine-agents/installing-landmine-agent-windows/zscaler-deception-url-encoding-windows.png)
Example proxy URLs:
- `http://192.0.2.2:3128/`: Connect to a proxy server with an IP address = 192.0.2.2 and port number = 3128.
- `http://proxy-server:8888/`: Connect to a proxy server with the DNS name = proxy-server and port number = 8888.
- `http://proxyuser:proxypassword@192.0.2.18:3128/`: Connect to a proxy server with an IP address = 192.0.2.18, port number = 3128, username = proxyuser, and password = proxypassword.
- `http://user%232211:pass%40123@proxy-server-1:8888/`: Connect to a proxy server with the DNS name = proxy-server, port number = 8888, username= user#2211, and password = pass@123.
Configuring Proxies to Use a PAC File
To configure a proxy to use a PAC file, you must direct the landmine agent to a URL where the PAC file is hosted.
You can configure a proxy using the following URL format:
http://<ip/host>/<pacfile>.pac
Example PAC file URLs:
- `http://192.0.2.6/proxy.pac`: Connect to an HTTP server with an IP address = 192.0.2.6 and download the proxy.pac file.
- `http://pac-server/proxies.pac`: Connect to an HTTP server with the DNS name = pac-server and download the proxies.pac file.
- `http://pac-server:33234/proxy.pac`: Connect to an HTTP server with the DNS name = pac-server, port number = 33234, and download the proxy file.