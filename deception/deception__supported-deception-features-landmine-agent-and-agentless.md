# Supported Deception Features for Landmine Agent and Agentless Installers
Source: https://help.zscaler.com/deception/supported-deception-features-landmine-agent-and-agentless
PDF: https://help.zscaler.com/pdf/com/en/1531325.pdf

The landmine agent and agentless installers support the following modules.
Defense Evasion and Privilege Escalation
The following table shows features supported in the [Defense Evasion](/deception/configuring-privilege-escalation-module) and [Privilege Escalation](/deception/configuring-privilege-escalation-module) modules for landmine agent and agentless installers across operating systems.
| Modules | Features/Browsers/Software/File Decoys | Landmine Agent | Landmine Agentless |
| ------- | -------------------------------------- | -------------- | ------------------ |
| Windows | macOS | Linux | Windows | macOS | Linux |
| Defense Evasion | Fake Security Process | Yes | No | No | No | No | No |
| Privilege Escalation | MITM Detection | Yes | Yes | Yes | No | No | No |
| Brute Force Detection | Yes | No | No | No | No | No |
| Kerberoast Detection | Yes | No | No | No | No | No |
| In Memory Credential Detection | Yes | No | No | No | No | No |
Cloud, Browser, and Session Lures
The following table shows features supported in the [Cloud Lures](/deception/configuring-cloud-lures-module), [Browser Lures](/deception/configuring-browser-lures-module), and [Session Lures](/deception/configuring-session-lures-module) modules for landmine agent and agentless installers across operating systems.
| Modules | Features/Browsers/Software/File Decoys | Landmine Agent | Landmine Agentless |
| ------- | -------------------------------------- | -------------- | ------------------ |
| Windows | macOS | Linux | Windows | macOS | Linux |
| Cloud Lures | Amazon Web Services (AWS) Identity Access Management (IAM) | Yes | Yes | Yes | Yes | Yes | Yes |
| Browser Lures | Chrome | Yes | Yes | Yes | Yes | Yes | Yes |
| Firefox | Yes | No | No | Yes | No | No |
| Internet Explorer | Yes | No | No | Yes | No | No |
| Session Lures | DbVisualizer | Yes | No | No | Yes | No | No |
| Network Drives | Yes | No | No | Yes | No | No |
| FileZilla | Yes | Yes | Yes | Yes | Yes | Yes |
| PuTTY | Yes | No | No | Yes | No | No |
| Remote Desktop Protocol (RDP) | Yes | No | No | Yes | No | No |
| Squirrel DB | Yes | No | No | Yes | No | No |
| Windows Credentials | Yes | No | No | Yes | No | No |
| WinSCP Session | Yes | No | No | Yes | No | No |
| /etc/hosts File | No | Yes | Yes | No | No | No |
| Bash History | No | Yes | Yes | No | Yes | Yes |
| SSH Config | No | Yes | Yes | No | Yes | Yes |
File Decoys
The following table shows features supported in the [File Decoys](/deception/configuring-file-decoys-module) module for landmine agent and agentless installers across operating systems.
| Modules | Features/Browsers/Software/File Decoys | Landmine Agent | Landmine Agentless |
| ------- | -------------------------------------- | -------------- | ------------------ |
| Windows | macOS | Linux | Windows | macOS | Linux |
| File Decoys | Custom File Decoys | Yes | No | No | Yes | No | No |
| Credential File Decoys | Yes | No | No | No | No | Yes |
| Preconfigured File Dataset Decoys | Yes | No | No | No | No | No |
Advanced Deception Capabilities
The following table shows features supported in the [Advanced Deception Capabilities](/deception/configuring-advanced-deception-capabilities-module) module for landmine agent and agentless installers across operating systems.
| Modules | Features/Browsers/Software/File Decoys | Landmine Agent | Landmine Agentless |
| ------- | -------------------------------------- | -------------- | ------------------ |
| Windows | macOS | Linux | Windows | macOS | Linux |
| Advanced Deception Capabilities | PsExec Detection | Yes | No | No | No | No | No |
| Ransomware Detection | Yes | No | No | No | No | No |
| Triage | Yes | No | No | No | No | No |