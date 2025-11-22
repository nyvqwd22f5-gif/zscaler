# About Safe Processes
Source: https://help.zscaler.com/deception/about-safe-processes
PDF: https://help.zscaler.com/pdf/com/en/1531454.pdf

Landmine processes that detect defense evasion sometimes generate false positives when tripped by security processes, such as antivirus or Endpoint Detection and Response (EDR) scans. To prevent generating false positives, you can designate known and trusted processes in your environment as safe processes. In addition, Zscaler Deception provides a set of predesignated safe processes called internal processes that can be enabled or disabled based on your requirements.
Safe processes provide the following benefits and allow you to:
- Configure safe landmine processes that don't generate events when accessed by legitimate security processes. Alerts are generated only when an attacker interacts with these landmine processes.
- Configure safe landmine processes using the parameters, such as the executable file path, executable file hash, certificate details, etc.
About the Safe Processes Page
On the Safe Processes page (Settings > Endpoint Settings > Safe Processes), you can do the following:
- View a list of safe processes. For each configured safe process, you can see:
- **Name**: A unique identifier to categorize the safe processes.
- **Enabled**: Shows whether a safe process is enabled or disabled. A green check mark indicates enabled, and a red X indicates disabled.
- **Check Process Tree**: Shows whether a safe process is included in the process tree check while generating events for decoy interactions. A green check mark indicates enabled, and a red X indicates disabled.
- **Executable File Path**: The executable file path expressed in absolute values.
- **Executable File Regex: **The executable file path expressed in regular expressions.
- **Executable File Hash**: The executable file hash (eg., md5, sha1, and sha256).
- **Certificate Issuer**: A unique certificate issuer name that identifies the issuer of the digital certificate.
- **Certificate Serial**: A unique certificate serial number issued by a certificate authority.
- **Certificate Thumbprint**: A unique certificate thumbprint that is a hash of a certificate.
- **Type**: Shows whether a safe process is internal or not. The internal safe processes are identified using the "Internal" label.
- View or hide internal safe processes using the **Show Internal **toggle.
- [Configure a safe process](/deception/configuring-safe-process).
- [Edit or delete a safe process.](/deception/editing-or-deleting-safe-process)
![About the Safe Processes page](/downloads/deception/settings/endpoint-settings/safe-processes/about-safe-processes/zscaler-deception-about-articles.png)