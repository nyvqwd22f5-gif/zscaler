# Configuring the Advanced Deception Capabilities Module
Source: https://help.zscaler.com/deception/configuring-advanced-deception-capabilities-module
PDF: https://help.zscaler.com/pdf/com/en/1531309.pdf

The Advanced Deception Capabilities module enables you to deploy enhanced threat detection capabilities, such as PsExec Detection, Ransomware, and Triage on endpoints.
- **PsExec Detection**: PsExec is a system administration utility that executes programs on remote Windows hosts. PsExec uses Windows file shares or server message block (SMB) protocol to connect to the remote system and installs a Windows service that runs the commands. If a system has the Admin$ read or write share option enabled, PsExec runs commands with the highest privileges on the system. When the PsExec Detection feature is enabled on a target system, it monitors connections to the Windows share and any subsequent creation of the services.
- **Ransomware Detection**: The Ransomware feature deploys special files and processes decoys that are generally targeted by ransomware. It also detects if the shadow copy is deleted from the endpoint, which is a common activity of ransomware. Zscaler Deception adds in-memory mutex to the system, which inoculates it against certain strains of ransomware.
- **Triage**: The Triage feature monitors and raises events for processes on the system that make an outbound connection to your network or Threat Intelligence (TI) decoys. This feature provides additional contextual information regarding events, such as process names, process hashes, user details, etc.
To enable advanced deception features for a landmine policy:
- Go to **Deceive **> **Landmine **> **Policies**.
-
In the landmine policies table, locate the landmine policy you want to use to deploy the advanced deception capabilities on endpoints, and click the **Edit **icon.
[See image.](#option-to-edit-policy)
-
In the policy configuration window, click **Advanced Deception Capabilities**, and enable the required options:
- **PsExec Detection**
- **Ransomware Detection**
- **Triage**
- **Suspicious Process Detection**
- **Suspicious Powershell Execution Detection**
-
**Kerberoast Detection (Decoy)**
The** Kerberoast Detection (Decoy) **option is shown in the **Advanced Deception Module** for tenants with Deception-only licenses. For tenants with Deception and ITDR licenses, this option is included in the **Active Directory Threat Detection Module **under **ITDR** > **Manage **> **Threat Detection**.
[See image.](#zd-advanced-capabalities)
- Click **Save**.
[][![A screenshot capturing the option to edit a landmine policy](/downloads/deception/deceive/landmine-decoys/policies/configuring-advanced-deception-capabilities-module/deception-landmine-policy-edit-one.png)
]
[]![A screenshot of Advanced Deception Capabilities module](/downloads/deception/deceive/landmine-decoys/policies/configuring-advanced-deception-capabilities-module/zscaler-deception-advanced-deception-module.png)