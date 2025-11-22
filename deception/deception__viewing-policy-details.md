# Viewing Policy Details
Source: https://help.zscaler.com/deception/viewing-policy-details
PDF: https://help.zscaler.com/pdf/com/en/1531419.pdf

You can view the details of the configured landmine deception modules in a policy that is deployed on a system. On the policy details page, you can view:
- **System Details**: The system name, username, policy name, operating system name and version, IP addresses of the system, the type of agent installed on the system (agent or agentless), date and time when the agent was installed, and date and time when the agent was last connected to the Zscaler Deception Admin Portal.
- **Fake Security Processes Details**: The name of the fake process, policy name, and folder path to the fake process.
- **Privilege Escalation Details**: The name of the detection (such as man-in-the-middle (MITM), brute force, kerberoast, and memory credential); status (enabled or disabled); and other configuration details.
- **Cloud Lures**: The policy name, usernames, Amazon Web Services (AWS) access key, and AWS secret keys.
- **Browser Lures**: For the supported browsers (Google Chrome, Mozilla Firefox, etc.), you can view:
- Cookie lure details such as username, cookie name, host, value, etc.
- Bookmark lure details, username, bookmark name, URL, folder name, etc.
- Browser lure credentials, username, perimeter application decoy, URL, etc.
- **Session Lures**: The decoy credentials, hostname, and port number of supported software such as FileZilla, DbVisualizer, PuTTY, Remote Desktop Protocol (RDP), SQuirreL SQL, WinSCP, etc.
- **File Decoys**: The name, path, and hidden attributes of decoy files such as custom files, credential files, and preconfigured file datasets.
- **Advanced Deception Capabilities**: The status (enabled or disabled) of advanced deception capabilities such as PsExec, Ransomware, and Triage.
To view the details of the configured deception modules applied to a system using the landmine agent:
- Go to **Settings **> **Endpoint Settings **> **Agents**.
-
Locate the system (using the **System Name** field) on which policies are applied by an agent, and click the **View** icon under the **Actions **column.
[See image.](#view-policy-details-icon)
The policy details page appears.
[See image.](#policy-details)
[]![View policy details icon](/downloads/deception/deceive/landmine-decoys/policies/policy-management/viewing-policy-details/zscaler-deception-view-details-agents.png)
[]![View policy details](/downloads/deception/deceive/landmine-decoys/policies/policy-management/viewing-policy-details/zscaler-deception-policy-preview-page.png)