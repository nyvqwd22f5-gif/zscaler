# Installing a Landmine Agent on Linux
Source: https://help.zscaler.com/deception/installing-landmine-agent-linux
PDF: https://help.zscaler.com/pdf/com/en/1531327.pdf

This article provides instructions for installing a landmine agent on the Linux platform using the command line interface (CLI).
You can run a landmine agent on the desktop versions of Linux operating systems. Headless server operating systems are not supported.
Prerequisites
Before installing a landmine agent, make sure you have:
- Endpoints running 64-bit (AMD64 or x86_64) versions of supported Linux distributions:
- Debian 10 or later
- Ubuntu 20.04 or later LTS releases
- Red Hat Enterprise Linux version 8 or later
- Fedora 35 or later
- openSUSE Leap 15.3 or later
- Network connectivity from the endpoints where the agent is installed to the Zscaler Deception Admin Portal instance on port 443. This connection is proxy aware, and you can optionally define a list of proxies for the agent to connect through.
Installing a Landmine Agent on Linux Using the RPM Package
To install a landmine agent on Linux (rpm):
- [Download the Linux (rpm) installer](/deception/downloading-landmine-agents) file from the Deception Admin Portal.
- Create a text file (`landmine.txt`) in the `tmp` folder. To create a file:
- Open a terminal window.
- Use a text editor (e.g., Vi or Nano) to create a text file.
-
Copy the Deception Admin Portal's instance name and the Agent Registration Token from the **Download Landmine Agent** window and paste it into the text file:
[See image.](#linux-rpm)
-
Run the following command in a terminal from the path where the .rpm file is downloaded:
sudo rpm -ivh/tmp/Landmine.rpm
Installing a Landmine Agent on Linux Using the DEB Package
To install a landmine agent on Linux (deb):
- [Download the Linux (deb) installer](/deception/downloading-landmine-agents) file from the Deception Admin Portal.
- Create a text file (`landmine.txt`) in the `tmp` folder. To create a file:
- Open a terminal window.
- Use a text editor (e.g., Vi or Nano) to create a text file.
-
Copy the Deception Admin Portal's instance name and the Agent Registration Token from the **Download Landmine Agent** window and paste it into the text file:
[See image.](#linux-deb)
-
Run the following command in a terminal from the path where the .rpm file is downloaded:
sudo dpkg -i/tmp/Landmine.deb
Configuring Proxies
To configure proxies for Linux, add the proxy definition to the text file (`/tmp/landmine.txt`). To configure multiple proxies, add a list of proxies separated by commas.
For example:
<instance name>
<Agent Registration Token>
http://user:password@proxy-server:8888,http://proxy-server:3128
When the landmine agent starts, it attempts to connect to the Deception Admin Portal using the list of proxies in a sequence from left to right. If the proxy is not configured, the agent attempts to connect to the portal directly.
After you run the command, the landmine agent connects to the portal using one of the following methods:
- Connects via `http://user:password@proxy-server:8888/proxy`.
- Connects via `http://proxy-server:3128/proxy`.
If all of the above methods fail, the agent attempts to connect to the portal using a direct no-proxy connection.
You can configure proxies using the following URL format:
http://[username:password]@<ip/host>:<port>
If the username and password have special characters (e.g., Username = user#2211 and password = pass@123), you must URL-encode them. For example:
http://user%232211:pass%40123@proxy-server-1:8888
Example proxy URLs:
- `http://192.0.2.2:3128/`: Connect to a proxy server with an IP address = 192.0.2.2 and port number = 3128.
- `http://proxy-server:8888/`: Connect to a proxy server with the DNS name = proxy-server and port number = 8888.
- `http://proxyuser:proxypassword@192.0.2.18:3128/`: Connect to a proxy server with an IP address = 192.0.2.18, port number = 3128, username = proxyuser, and password = proxypassword.
- `http://user%232211:pass%40123@proxy-server-1:8888/`: Connect to a proxy server with the DNS name = proxy-server, port number = 8888, username= user#2211, and password = pass@123.
[]
![Download landmine agent Linux (rpm) installer ](/downloads/deception/product-documentation/deceive/endpoint-decoys/agents/installing-landmine-agent-linux/zscaler-deception-agent-linux-pop-up.jpg)
[]
![Download landmine agent Linux (deb) installer ](/downloads/deception/product-documentation/deceive/endpoint-decoys/agents/installing-landmine-agent-linux/zscaler-deception-agent-linux-deb-pop-up.jpg)