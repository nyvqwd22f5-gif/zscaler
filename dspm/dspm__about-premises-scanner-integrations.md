# About On-Premises Scanner Integrations
Source: https://help.zscaler.com/dspm/about-premises-scanner-integrations
PDF: https://help.zscaler.com/pdf/com/en/1532039.pdf

DSPM provides support to integrate the on-premises scanners deployed in your organization's network and use them to scan the data stored in on-premises systems such as file servers and unmanaged resources. On-premesis scanners provide direct access to internal data sources, enabling granular visibility into sensitive data and maintain the data security posture across hybrid environments by extending scanning capabilities to internal systems.
Integrating on-premises scanners with DSPM provides the following benefits and enables you to:
- Gain visibility into sensitive data stored in on-premises environments.
- Strengthen the security posture of the internal infrastructure.
- Maintain consistent data protection policies across on-premises environments.
- Detect misconfigurations, vulnerabilities, and potential threats that could lead to data exposure.
- Respond to security risks and take corrective actions to prevent data breaches.
System Requirements
For optimal DSPM scanner performance, ensure the following system requirements are met:
- [Virtual Machine](#vmspec)
- [Network Requirements](#network-requirements)
- [Supported File Server Protocols](#fs-protocols)
[]
| Component | Minimum Requirement | Details |
| --------- | ------------------- | ------- |
| CPU | 16 Virtual Cores | Intel Xeon or AMD EPYC, or the latest.ARM processors are not supported. |
| RAM | 32 GB | Dedicated memory for the VM. |
| Storage | 100 GB SSD | High-performance storage is crucial for efficient scanning. |
| Operating System | Embedded within OVA (Ubuntu 22.04) | The image includes the OS; no separate license is required. |
[]The DSPM scanner for on-premises file servers requires specific network configurations to operate correctly and securely.
| Component | Requirement | Details |
| --------- | ----------- | ------- |
| Network Interface | 10 Gigabit Ethernet (GbE) | Dedicated to the VM.Wired connection preferred. |
| IP Addressing | Static IP Address | For consistent connectivity and management. |
| DNS Resolution | To resolve internal and external hosts | Required for communication with file servers and cloud services. |
| **Firewall Rules (Outbound)** |
| Port 443 (HTTPS) | To DSPM Cloud Management Platform | For updates and configuration synchronization. |
| Port 445 (SMB) | To SMB File Servers | For scanning SMB file shares. |
| Port 2049 (NFS) | To NFS File Servers | For scanning NFS file shares. |
| Port 53 (DNS) | To DNS Server | For DNS resolution. |
| Port 88 (Kerberos) | To Kerberos | For Kerberos authentication. |
| Port 111 (NFS) | To NFS File Servers | For NFS Portmapper. |
[]The on‑premises file‑server scanning solution supports the following protocol versions for scanning file servers:
| Protocol | Versions | Details |
| -------- | -------- | ------- |
| SMB | 2.0, 2.1, 3.0, 3.02, 3.1.1 | Required for scanning Windows file shares. |
| NFS | v4.0, v4.1, v4.2 | Required for scanning Linux/Windows shares. |
About the On-Premises Scanner Integrations Page
On the On-Premises Scanner Integrations page (Administration > Configuration > On-Premises Scanners), you can do the following:
- [Add an on-premises scanner to DSPM](/dspm/adding-premises-scanner-integration).
- View the list of on-premises scanner integrations. For each scanner integration, you can view:
- **Integration**: The name assigned to the scanner integration. Click the integration name to see the following details:
- [Scanner Integration Details](#dc-details)
- **Scanner**: The scanner instance name.
- **Version**: The version of the scanner software.
- **IP Address**: The IP address of the scanner.
- **Scanner Status**: Whether the scanner is operational or pending.
- **Added On**: The date and time the scanner was added to DSPM.
- **Added By**: The user who added the scanner.
- Sort the column data.
- [Modify the table and its columns](/dspm/using-tables).
- [Delete](/dspm/adding-premises-scanner-integration#delete) the scanner integration.
[]
- **General Information**:
- **Scanner**: The scanner instance name.
- **Version**: The version of the scanner software.
- **IP Address**: The IP address of the scanner.
- **Status**: Whether the scanner is operational or not.
- **Added On**: The date and time the scanner was added to DSPM.
- **Added By**: The user who added the scanner.
- **API Key Management**:
- **API Key**: The key used to authenticate the scanner.
- **Regenerate Key**: Click to generate a new API key when the key is compromised, exceeds your rotation threshold, or you need to rotate credentials per policy.
- **Scanner Image Download**:
- **Select Virtualization Platform**: Choose the platform on which the DSPM scanner image must be downloaded (i.e., **VMware** or **Hyper-V**).
- Name and format of the scanner image: OVA for VMware and VHD for Hyper-V.
- **Checksum**: The checksum value for image verification.
- **Size**: The file size of the scanner image.
- **Download Scanner Image**: Click to download the image file.
- **Data Center Association**: Download and install the scanner image to scan and monitor data stored within the on-premises data center. To learn more, see [Adding On-Premises Scanner Integration](/dspm/adding-premises-scanner-integration).
- [Delete the scanner integration](/dspm/adding-premises-scanner-integration#delete).
![Scanner integration details showing, status operational, and API key information.](/downloads/dspm/administration/premise-scanners/about-premises-scanner-integrations/ds-admin-on-prem-scanner-detail.png)
![The On-Premises Scanner Integration page with a list of scanners and annotations on different parts of the page.](/downloads/dspm/administration/premise-scanners/about-premises-scanner-integrations/ds-admin-on-prem-scanner-about.png)