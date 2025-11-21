# Installing a Landmine Agent Using an Active Directory Group Policy Object
Source: https://help.zscaler.com/deception/installing-landmine-agent-using-active-directory-gpo
PDF: https://help.zscaler.com/pdf/com/en/1531484.pdf

You can install a landmine agent on domain-joined user machines using Active Directory (AD) Group Policy Object (GPO).
Prerequisites
Before installing a landmine agent, make sure that the following prerequisites are met:
-
Windows installer and .NET framework
- 64-bit versions of Windows 10 or later
- .NET version 4.6.1 or later (Zscaler recommends using the latest version of .NET framework)
For Windows 10 version 1607 and earlier, install the latest version of the .NET framework for the installation to succeed.
Microsoft Windows 7, Windows 8, and Windows 8.1 are not supported.
- RAM: 100 MB of free memory
- Storage: 1 GB of free storage, preferably in an SSD
- Network Connectivity: A minimum of 256 Kbps internet bandwidth and an open outbound port 443 on the system where the agent is installed to connect to the Zscaler Deception Admin Portal. This connection is proxy-aware, and you can either use a statically defined proxy or the proxy configured for the `SYSTEM` user.
The resource requirements listed here are also the landmine agent's maximum limits of utilization.
Installing a Landmine Agent Using an Active Directory
To install a landmine agent using an AD GPO:
-
[Download the Windows EXE installer](/deception/downloading-landmine-agents) file and copy the installation command from the Deception Admin Portal.
[See image.](#deception-install-landmine-gpo-copy-command)
-
Create a batch file using the following installation command:
Landmine.exe /qn CMC=<Deception Admin Portal instance> REGKEY=<Key> /l*v <Path to Landmine installation logs>
- The command must contain the complete path of the landmine EXE installer if it is stored in a shared folder. The last part of the command `/l*v <Path to Landmine installation logs>` is optional.
- If a proxy is required to access the Zscaler Deception from endpoints, then add the proxy parameters to the installation command. To learn more, see [Installing a Landmine Agent on Windows](/deception/installing-landmine-agent-windows).
- Press the `Windows key+R` in your domain controller (DC).
- In the **Run** window, enter `gpmc.msc` to open the Group Policy Management console.
- Create or select a GPO on which you want to install the landmine agent. To create a GPO, refer to the [Microsoft Technical documentation](https://learn.microsoft.com/en-us/windows/security/operating-system-security/network-security/windows-firewall/create-a-group-policy-object).
- Go to **Computer configuration** > **Policies** > **Windows settings** > **Scripts (Startup/Shutdown)**.
-
In the **Scripts (Startup/Shutdown) **pane, double-click **Startup**.
[See image.](#deception-install-landmine-installer-gpo-startup)
-
In the **Startup Properties** window, click **Show Files** to open the **Startup** folder.
[See image.](#deception-landmine-install-gpo-show-files)
-
Copy the landmine EXE installer and batch files.
[See image.](#deception-landmine-installer-gpo-save-files)
-
In the **Startup Properties** window, click **Add** and select the landmine batch file.
[See image.](#deception-landmine-installer-gpo-add-batch-file)
- Click **OK**.
[]![Copy the Landmine installer command](/downloads/deception/product-documentation/deceive/endpoint-decoys/agents/installing-landmine-agent-using-active-directory-gpo/zscaler-deception-landmine-ad-copy-command-1.png)
[]![Configure startup script](/downloads/deception/product-documentation/deceive/endpoint-decoys/agents/installing-landmine-agent-using-active-directory-gpo/zscaler-deception-landmine-ad-startup.png)
[]![View script files](/downloads/deception/product-documentation/deceive/endpoint-decoys/agents/installing-landmine-agent-using-active-directory-gpo/zscaler-deception-landmine-ad-showfiles.png)
[]![Save the installer and batch files in the Startup folder](/downloads/deception/product-documentation/deceive/endpoint-decoys/agents/installing-landmine-agent-using-active-directory-gpo/zscaler-deception-landmine-ad-save-files-1.png)
[]![Add the batch file](/downloads/deception/product-documentation/deceive/endpoint-decoys/agents/installing-landmine-agent-using-active-directory-gpo/zscaler-deception-landmine-ad-add-landmine-bat.png)