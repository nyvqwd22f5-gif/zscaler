# Installing a Server Agent
Source: https://help.zscaler.com/deception/installing-server-agent
PDF: https://help.zscaler.com/pdf/com/en/1531601.pdf

This article provides instructions for installing a server agent on a domain controller.
Prerequisites
Before installing a server agent, ensure that your domain controllers have the following:
- Operating System: Windows Server 2012 R2 or later with an active Domain Controller or a Read-only Domain Controller
- Free memory: 4 GB
- Disk space: 500 MB (5 GB for Password Analysis)
- Internet bandwidth: 256 Kbps (1 Mbps for Password Analysis)
- Connectivity over HTTPS (port 443) to the following domains:
- ib.smokescreen.io
- Zscaler Deception Admin Portal
Installing a Server Agent
You can install a server agent on a single or multiple domain controllers.
To install a server agent:
- [Download the Windows EXE installer](/deception/downloading-server-agent) file from the Deception Admin Portal.
- Open the Command Prompt as an administrator.
- Click **Start**.
- In the **Start Search** box, enter `cmd`, and then press `CTRL+SHIFT+ENTER`.
- When the **User Account Control** (UAC) dialog box appears, click **Yes**.
- In the command prompt, choose a command as per your installation requirements:
-
To install the agent without proxies:
ZSServerAgentInstaller.exe /qn /CMC=<instance name> /REGKEY=<Registration Token>
-
To install the server agent with a proxy:
ZSServerAgentInstaller.exe /qn /CMC=<instance name> /REGKEY=<Registration Token> /PROXIES=<proxy list comma separated>
The server agent is a proxy-aware application. It can automatically detect and apply the proxy configurations if they are already available in the domain controller.
The following table describes the installation parameters:
| Parameter | Description | Required |
| --------- | ----------- | -------- |
| `/qn` | Enables silent mode installation | Yes |
| `/CMC=<instance name>` | The hostname of the Deception Admin Portal | Yes |
| `/REGKEY=<Registration Token>` | The Server Agent Registration Token | Yes |
| `/PROXIES=<Proxy String>` | Proxies to connect to the Deception Admin Portal. If there is more than one proxy, separate them with a comma. Make sure that there are no white spaces in the `PROXIES` parameter. | No |
After you run the command, the server agent is installed on a domain controller and appears in the [Agents](/deception/about-server-agent) table (Settings > Server Agents Settings > Agents).
The domain you selected to install a server agent appears in the [Domains](/deception/about-server-agent-domains) table (Settings > Server Agents Settings > Domains).
Configuring Proxies
The server agent is a proxy-aware application. It can automatically detect and apply the proxy configurations if they are already available in the system.
You can use the `PROXIES` parameter in the installation command to configure multiple proxies. The `PROXIES` parameter consists of a list of proxies separated by commas. When the server agent starts, it attempts to connect to the Deception Admin Portal using the list of proxies in a sequence from left to right. If the proxy is not configured, the agent attempts to connect to the Deception Admin Portal directly, or it uses a proxy configured for the `SYSTEM` user.
To configure multiple proxies, open the command prompt and enter the following command:
ZSServerAgentInstaller.exe /qn /CMC=<instance name> /REGKEY=<Registration Token> /PROXIES=http://proxy-server/proxy.pac,http://user:password@proxy-server:8888,http://proxy-server:3128
After you run the command, the server agent connects to the Deception Admin Portal using one of the following methods:
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
To configure a proxy to use a PAC file, you must direct the server agent to a URL where the PAC file is hosted.
You can configure a proxy using the following URL format:
http://<ip/host>/<pacfile>.pac
Example PAC file URLs:
- `http://192.0.2.6/proxy.pac`: Connect to an HTTP server with an IP address = 192.0.2.6 and download the proxy.pac file.
- `http://pac-server/proxies.pac`: Connect to an HTTP server with the DNS name = pac-server and download the proxies.pac file.
- `http://pac-server:33234/proxy.pac`: Connect to an HTTP server with the DNS name = pac-server, port number = 33234, and download the proxy file.