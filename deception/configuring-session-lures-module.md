# Configuring the Session Lures Module
Source: https://help.zscaler.com/deception/configuring-session-lures-module
PDF: https://help.zscaler.com/pdf/com/en/1531306.pdf

The Session Lures module enables you to add decoy credentials and settings in various popular software applications, such as FileZilla, DbVisualizer, PuTTY, Remote Desktop Protocol (RDP), SQuirreL SQL, WinSCP, etc. An event is generated when an adversary interacts with the decoys using the decoy credentials.
To configure session lures for a landmine policy:
- Go to **Deceive **> **Landmine **> **Policies**.
-
In the landmine policies table, locate the landmine policy you want to use to deploy session lures on endpoints, and click the **Edit **icon.
[See image.](#option-to-edit-policy)
- In the policy configuration window, click **Session Lures**.
-
Locate the software application on which you want to deploy the decoys and for each of them:
- Select **Enabled**.
-
Select one or more decoys from the **Target decoys** drop-down menu as targets for the lures. When no decoy is selected, a target decoy is chosen randomly if a decoy with a supported service is enabled and deployed.
The **GenAI** icon indicates lures that support generative AI decoys as target decoys.
- [Windows](#windows-lures)
- [macOS](#mac-lures)
- [Linux](#linux-lures)
[See image.](#zd-session-lures)
If the **Target decoys** field is blank, all of the decoys running the corresponding service are used as a default pool. The landmine agent randomly selects the decoys from the pool of target decoys and adds them to the browser. A maximum of two decoys are deployed for each lure type.
- Click **Save**.
[]The following table lists the different types of lures that can be deployed on Windows endpoints.
-
-
-
-
| Application | Supported Target Decoys | Description |
| ----------- | ----------------------- | ----------- |
| DbVisualizer | Network decoys with these services enabled:MySQLPostgreSQL | Credentials to access the decoys are generated and placed into the required configuration files of DbVisualizer. The credentials are accessible to adversaries from the DbVisualizer client. When an adversary connects to the decoys using these credentials, an event is generated. |
| FileZilla | Network decoys with the FTP service enabled | Credentials to access the decoys are generated and placed into the required configuration files of FileZilla. The credentials are accessible to adversaries from the FileZilla client. When an adversary connects to the decoys using these credentials, an event is generated.Supports file-based generative AI decoys deployed as an FTP service via an internal network decoy or Zero Trust network decoy. |
| Network Drives | Network decoys with the Shares service enabled | Credentials to access the decoys network drives are generated and placed into Windows credentials Manager. When an adversary connects to the decoy network drives using these credentials, an event is generated.Supports file-based generative AI decoys deployed as a Share service via an internal network decoy or Zero Trust network decoy. |
| PuTTY | Network decoys with the SSH service enabled | Credentials to access the decoys are generated and placed into the required configuration files of PuTTY. The credentials are accessible to adversaries from the PuTTY client. When an adversary connects to the decoys using these credentials, an event is generated. |
| RDP | Network decoys with the Windows service enabled | Credentials to access the decoy Windows VM is added to Windows Credential Manager. In addition, a file to initiate a connection to the decoy Windows VM is added to the current user's Documents folder (`%userprofile%\Documents`). When an adversary connects to the decoy Windows VM using the credentials from the Windows Credential Manger or using the RDP file from the Documents folder, an event is generated.You can prevent users from using the RDP file by selecting **Hidden**. |
| SQuirrel DB | Network decoys with these services enabled:MySQLPostgreSQL | Credentials to access the selected decoys are generated and placed into the required configuration files of SQuirrel DB. The credentials are accessible to adversaries from the SQuirrel SQL Client. When an adversary connects to the decoys using these credentials, an event is generated. |
| Windows Credentials | Network decoys with the Windows service enabled | Credentials to access network decoys are generated and placed into Windows Credentials Manager. When an adversary connects to the network decoys using these credentials, an event is generated. |
| WinSCP Session | Network decoys with the SSH service enabled | Credentials to access the selected decoys are generated and placed into the required configuration files of WinSCP. The credentials are accessible to adversaries from the WinSCP Client. When an adversary connects to the decoys using these credentials, an event is generated. |
[]The following table lists the different types of lures that can be deployed on macOS endpoints.
-
-
-
-
-
-
-
-
-
-
-
-
-
-
-
-
-
-
| Application | Supported Target Decoys | Description |
| ----------- | ----------------------- | ----------- |
| DbVisualizer | Network decoys with these services enabled:MySQLPostgreSQL | Credentials to access the decoys are generated and placed into the required configuration files of DbVisualizer. The credentials are accessible to adversaries from the DbVisualizer client. When an adversary connects to the decoys using these credentials, an event is generated. |
| FileZilla | Network decoys with the FTP service enabled | Credentials to access the decoys are generated and placed into the required configuration files of FileZilla. The credentials are accessible to adversaries from the FileZilla client. When an adversary connects to the decoys using these credentials, an event is generated.Supports file-based generative AI decoys deployed as an FTP service via an internal network decoy or Zero Trust network decoy. |
| /etc/hosts file | Network decoys with Web service enabled and TI decoys | Hostname and IP combination to access the web-based decoys are generated and placed into the `/etc/hosts` file. When an adversary connects to the decoys via hostnames added to the `/etc/hosts` file, an event is generated.Supports interactive generative AI decoys deployed in your internal network or Zero Trust network. |
| Bash/Zsh History | Network decoys with these services enabled:WebFTPSSHTI decoysAzure decoys:User DecoysService Principal DecoysApp Service DecoysStorage Account Container DecoysAWS decoys:IAM DecoysS3 DecoysRDS DecoysECR DecoysDynamo DB Decoys | Commands to access network, TI, and cloud decoys are added to the bash or Z Shell history. When an adversary connects to the decoys by using the commands from the bash or Z Shell history, an event is generated.Supports both interactive and file-based generative AI decoys deployed. |
| SSH Config File | Network decoys with the SSH service enabled | Information to access the decoy SSH servers is generated and placed into the `/etc/ssh/ssh_config` file. When an adversary connects to the decoy SSH server using the details added to the `/etc/ssh/ssh_config` file, an event is generated. |
[]The following table lists the different types of lures that can be deployed on Linux endpoints.
-
-
-
-
-
| Application | Supported Target Decoys | Description |
| ----------- | ----------------------- | ----------- |
| FileZilla | Network decoys with the FTP service enabled | Credentials to access the decoys are generated and placed into the required configuration files of FileZilla. The credentials are accessible to adversaries from the FileZilla client. When an adversary connects to the decoys using these credentials, an event is generated.Supports file-based generative AI decoys deployed as an FTP service via an internal network decoy or Zero Trust network decoy. |
| /etc/hosts file | Network decoys with Web service enabled and TI decoys | Hostname and IP combination to access the web-based decoys are generated and placed into the `/etc/hosts` file. When an adversary connects to the decoys via hostnames added to the `/etc/hosts` file, an event is generated.Supports interactive generative AI decoys deployed on your internal network or Zero Trust network. |
| Bash/Zsh History | Network decoys with these services enabled:WebFTPSSHTI decoys | Commands to access Web, FTP, and SSH decoys are added to the bash or Z shell history. When an adversary connects to the decoys by using the commands from the bash Z Shell history, an event is generated.Supports both interactive and file-based generative AI decoys deployed. |
| SSH Config File | Network decoys with the SSH service enabled | Information to access the decoy SSH servers is generated and placed into the `/etc/ssh/ssh_config` file. When an adversary connects to the decoy SSH server using the details added to the `/etc/ssh/ssh_config` file, an event is generated. |
[]![A screenshot capturing the option to edit a landmine policy](/downloads/deception/deceive/landmine-decoys/policies/configuring-session-lures-module/deception-landmine-policy-edit-two.png)
[]![A screenshot of the Session Lures module in a landmine policy](/downloads/deception/deceive/landmine-decoys/policies/configuring-session-lures-module/zscaler-deception-session-lures.png)