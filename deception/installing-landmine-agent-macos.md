# Installing a Landmine Agent on macOS
Source: https://help.zscaler.com/deception/installing-landmine-agent-macos
PDF: https://help.zscaler.com/pdf/com/en/1531314.pdf

This article provides instructions for installing a landmine agent on the macOS platform using the command line interface (CLI).
Prerequisites
Before installing a landmine agent, ensure that you have:
- A Mac computer with macOS Ventura (version 13) or later.
- Network connectivity from the system where the agent is installed to the Zscaler Deception Admin Portal instance on port 443. This connection is proxy-aware, and you can optionally define a list of proxies for the agent to connect through.
- (Optional) Enabled Full Disk Access for the agent. This is required to use the Defense Evasion feature.
- [Snippet to grant Full Disk Access that can be added to the MDM profile.](#snippet-mdm-profile)
Installing Agent on macOS
To install a landmine agent on macOS:
- [Download the macOS installer (Intel or Apple Silicon)](/deception/downloading-landmine-agents) file from the Deception Admin Portal.
- Create a text file (`landmine.txt`) in the `/tmp` folder.
-
Copy the Deception Admin Portal's instance name and the Agent Registration Token from the **Download Landmine Agent** window and paste it into the text file.
[See image.](#mac-os-installers)
-
Run the following command in a terminal from the path where the .pkg file is downloaded:
For Intel-based macOS endpoints:
sudo installer -pkg Landmine_Intel.pkg -target /
For Apple Silicon-based macOS endpoints:
sudo installer -pkg Landmine_AppleSilicon.pkg -target /
Configuring Proxies
To configure proxies for macOS, add the proxy definition to the text file (`/tmp/landmine.txt`). To configure multiple proxies, add a list of proxies separated by commas.
For example:
<instance name>
<Agent Registration Token>
http://user:password@proxy-server:8888,http://proxy-server:3128
When the landmine agent starts, it attempts to connect to the Deception Admin Portal using the list of proxies in a sequence from left to right. Finally, the agent tries to connect directly without a proxy.
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
[]![A screenshot capturing the Download Landmine Agent window with macOS-specific tabs highlighted](/downloads/deception/product-documentation/deceive/endpoint-decoys/agents/installing-landmine-agent-macos/zscaler-deception-download-landmine-agent-macos.jpg)
[]
`<key>SystemPolicyAllFiles</key>
<array>
<dict>
<key>Allowed</key>
<true/>
<key>CodeRequirement</key>
<string>identifier "com.zscaler.deception.XPCServerApp" and anchor apple generic and certificate 1[field.1.2.840.113635.100.6.2.6] /* exists */ and certificate leaf[field.1.2.840.113635.100.6.1.13] /* exists */ and certificate leaf[subject.OU] = PCBCQZJ7S7</string>
<key>Identifier</key>
<string>com.zscaler.deception.XPCServerApp</string>
<key>IdentifierType</key>
<string>bundleID</string>
<key>StaticCode</key>
<false/>
</dict>
</array>`