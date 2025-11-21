# Best Practice Guide for Network Decoys
Source: https://help.zscaler.com/deception/best-practice-guide-network-decoys
PDF: https://help.zscaler.com/pdf/com/en/1531588.pdf

This guide provides use cases and deployment recommendations for network decoys.
Network decoys are deployed within an organization's network. Depending on your organization's network environment, you can deploy network decoys as [standalone network decoys](/deception/creating-internal-network-decoy) or [Zero Trust network decoys](/deception/creating-zero-trust-network-decoy). The network decoys are typically deployed to detect different types of techniques defined in the MITRE ATT&CK  framework, such as lateral movement ([T1021](https://attack.mitre.org/techniques/T1021/) and [T1210](https://attack.mitre.org/techniques/T1210/)), discovery ([T1046](https://attack.mitre.org/techniques/T1046/)), impact ([T1565.001](https://attack.mitre.org/techniques/T1565/001/)), collection ([T1039](https://attack.mitre.org/techniques/T1039/)), and execution ([T1047](https://attack.mitre.org/techniques/T1047/)).
To set up network deception, Zscaler recommends a minimum of 50 network decoys, which includes the following different types of decoys.
| Decoy Type | Decoy Count |
| ---------- | ----------- |
| Decoy File Servers with Business-Critical Shares | 10 |
| Decoy Web Servers | 10 |
| Decoys of business-critical applications (e.g., SAP, email, etc.) | 5 |
| Decoys of services, such as SSH, Telnet, and FTP | 5 |
| Decoy High-Interaction Windows Server | 5 |
| Decoy Database Servers | 5 |
| Decoy Dev Servers | 5 |
| Decoys of commonly used IoT devices | 2 |
| Decoys as Custom Servers | 2 |
| Decoys as PAM Server | 1 |
In addition, you can use the following configuration options for different types of network decoys.
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
-
-
-
-
-
-
| Decoy Type | Recommendation |
| ---------- | -------------- |
| File Servers | **Hostname**: Use a name that follows your network environment conventions, or you can use keywords, such as fs, file, bkp, backup, nas, and share.**Services**: You can configure the following based on the operating system:**Linux**: Shared folders without admin shares, FTP, and SSH.**Windows**:** **Shared folders with admin shares and Windows (Server). |
| PAM Servers | **Hostname**: Use a name that follows your network environment conventions, or you can use keywords, such as PIM, PAM, ARC, and CYAK.**Services**: Web with an application dataset (e.g., Arcon/Arcos and Cyberarc). |
| Database Servers | **Hostname**: Use a name that follows your network environment conventions, or you can use keywords, such as DB, CLUST, MYSQL, SQL, and MSSQL.**Services**: You can configure the following based on the operating system:**Linux**: PostgreSQL, MongoDB, MySQL, and SSH**Windows**:** **Windows (Server with MSSQL) |
| Common IoT Devices | **Hostname**: Use a name that follows your network environment conventions, or you can use keywords, such as IOT, CCTV, GPS, and GRID.**Services**: Web with an application dataset (e.g., SpectralIPcam-CCTV, HIKVision-CCTV, DASDEC Digital Alert System, and Printer Datasets). |
| Development Servers | **Hostname**: Use a name that follows your network environment conventions, or you can use keywords, such as UAT, TEST, DEV, and PREPROD.**Services**: You can configure the following based on the operating system:**Linux**: PostgreSQL, MongoDB, MySQL Web, FTP, and SSH**Windows**: Shares, Web, and Windows (Server with MSSQL) |
| Workstations | **Hostname**: Use a name that follows your network environment conventions, or you can use keywords, such as ADMIN, ADM, SYSADM, WKS, LPT, DPT, WIN7, and WIN10.**Services**: Shares and Windows (version 7 and 10) |
| Generic Web Servers | **Hostname**: Use a name that follows your network environment conventions, or you can use keywords, such as BKP, SRV, WEB, and HTTP.**Services**: Web |
| Generic *NIX Servers | **Hostname**: Use a name that follows your network environment conventions, or you can use keywords, such as RHEL, NIX, LINUX, UNIX, and CENT.**Services**: SSH |
| Network Devices | **Hostname**: Use a name that follows your network environment conventions, or you can use keywords, such as SW, RW, CISCO, FW, and VPN.**Services**: SSH and Web with an application dataset (e.g., Cisco and F5 VPN). |
- To generate realistic hostnames for your network decoys, you can use the keyword datasets functionality to add names such as company name, location name, company alias, internally used keywords, and business keywords. These values are used in different combinations to generate hostnames. To learn more, see [Understanding Keyword Datasets](/deception/understanding-keyword-datasets).
- Ensure that you have a decoy for each key zone and segment in your network.
- Ensure that a decoy for each service is created. In addition, consider adding network decoys to the Active Directory (AD).
To learn how to create a network decoy, see [Creating an Internal Decoy](/deception/creating-internal-network-decoy) and [Creating a Zero Trust Network Decoy](/deception/creating-zero-trust-network-decoy).
Some use cases for creating network decoys are as follows:
- [Use Case: Decoy File Servers](#decoy-file-servers)
- [Use Case: Decoy Database Servers](#decoy-database-servers)
- [Use Case: Decoy Common IoT Devices](#decoy-common-iot-devices)
- [Use Case: Decoy Development Servers](#decoy-development-servers)
- [Use Case: Commonly Targeted Decoy Web Servers](#decoy-web-servers)
- [Use Case: Decoy Generic *NIX Servers](#devoy-generic-nix-servers)
- [Use Case: Decoy Network Devices](#decoy-network-devices)
- [Use Case: Decoy PIM/PAM Servers](#decoy-pim-pamservers)
- [Use Case: Decoy High-Interaction Windows Servers](#decoy-hi-windows-servers)
- [Use Case (Advanced): Decoy Business-Critical Applications](#decoy-business-critical-applications)
- [Use Case (Advanced): Decoy Custom Services](#decoy-custom-services)
[]Adversaries can target file servers for multiple reasons, such as collection, impact, and exploitation of services. If weak permissions are discovered, attackers can leverage this to get access to internal documents including asset inventory and password files, or they can replace the file with malicious executables. File servers can also be a primary target for ransomware.
**Recommendations**: Create a network decoy with the following configurations:
- **Name**: Enter a value in the `"``<service>``"+"PROD"` format (e.g., NASBKPPROD).
- **Services**: Enable **Shares, **select **Admin$ share** and **C$ share, **and add multiple dynamic shares, such as IT-security, Human Resources, Finance: Finance-Strategy, Confidential: None, VA reports: IT-security.
[]Adversaries can target database servers for multiple reasons, such as collection, impact, exploitation of services, and lateral movement. A well-configured database decoy can detect an adversary targeting databases in pursuit of sensitive information and PII.
**Recommendations**: Create a network decoy with the following configurations:
- **Name**: Enter a name in the `"``<SQL_service>``" + "DB" + "``<server_number>``"` format (e.g., SQLDB05).
- **Services**: Enable **SSH, MySQL**, and **Web**.** **For the **Web **service, set server type to `apache`, select **PHPmyadmin** as the dataset, and set ports to `80`, `8080`.
[]Adversaries can target IoT devices, such as CCTV and Monitoring and Alert systems, for multiple types of attacks. You can use decoy IoT devices to understand the adversary's behavior and help detect attacks by cyber espionage.
**Recommendations**: Create a network decoy with the following configurations:
- **Name**: Enter a name in the `"``<IoT_service>``"+ "``<location/floor>``" + "``<device_number>``"` format (e.g., CCTVLOB03).
- **Services**: Enable **Web**, set server type to `App-webs/`, and select **HIKVision-CCTV **as the dataset.
[]Development servers are used for testing before launching the features in the production environment. Adversaries target these servers as they are prone to misconfigurations.
**Recommendations**: Create a network decoy with the following configurations:
- **Name**: Enter a name in the `"``<location>``" + "``<Dev_keyword>``" + "``<server number>``"` format (e.g., RVDTESTSRV03).
- **Services**: Enable **Web**, set server type to `nginx`, and select **Generic Login PostgreSQL **as dataset.
[]Creating different types of decoy systems can give adversaries multiple options for attacks. These decoys can provide insights into understanding the adversary's behavior and tactics and techniques.
**Recommendations**: Create a network decoy with the following configurations:
- **Name**: Enter a name in the `"``<service>``" + "``<server_name>``"` format (e.g., SAPSRV09).
- **Services**: Enable **Web**, set server type to `SAP NetWeaver Application Server/ABAP 700`, and select **SAP Netweaver** as the dataset.
[]You can use Linux decoys to detect any attacks on Linux servers within your network environment. Creating different types of decoy systems can give adversaries multiple options for attacks. These decoys can provide insights into understanding the adversary's behavior and tactics and techniques.
**Recommendations**: Create a network decoy with the following configurations:
- **Name**: Enter a name in the `"``<OS_name>``" + "``<server name>``"` format (e.g., RHELSRV11 ).
- **Services**: Configure the following services:
- Enable **SSH**,** **and select **RHEL **as the operating system.
- Enable **Telnet**, and select **RHEL **as the operating system.
- Enable **FTP**, and select **VSFTPD **as the banner and **IT **as the dataset.
[]Adversaries can target networking devices to perform lateral movement or disrupt internal connections. There are different types of vulnerabilities associated with networking devices, such as F5 and Cisco, that can be leveraged by attackers to perform remote code execution (RCE) internally or externally.
**Recommendations**: Create a network decoy with the following configurations:
- **Name**: Enter a name in the `"``<device_name>``" + "``<location>``" + "``<device_number>``"` format (e.g., CISCO-RW04-01).
- **Services**: Enable **Web**, set **Apache **as the server type, and select **Cisco RV320 SSH** as the dataset.
[]Creating different types of decoy systems, including PIM servers, can give adversaries multiple options for attacks. These decoys can provide insights into understanding the adversary's behavior and tactics and techniques.
**Recommendations**: Create a network decoy with the following configurations:
- **Name**: Enter a name in the `"``<PIM keyword>"`` + "``<PIM server>``" + "``<location>``"` format (e.g., PIMARCRVD).
- **Services**: Enable **Web**, set the server type to `blank`, and select **Arcon PAM** as the dataset.
[]Decoy high-interaction Windows servers allow full telemetry capture, video recording, and malicious program capture when attacks are executed against these decoys.
**Recommendations**: Create a network decoy with the following configurations:
- **Name**: Enter a name in the `"``<PIM keyword>"`` + "``<PIM server>``" + "``<location>``"` format (e.g., PIMARCRVD).
- **Services**: Enable **Web**, set the server type to `blank`, and select **Arcon PAM** as the dataset.
[]To detect attacks against any sensitive business-critical applications, decoys can be customized to look and behave like the original application. Follow these steps to create a decoy for business-critical applications:
- Clone the sensitive application web page.
- Select an appropriate decoy name and services, including the web service, for the decoy application.
- Add the created web page as a decoy dataset.
[]Creating decoys of different types of well-known services and protocols can give adversaries multiple options for attacks that can provide insights into understanding the adversary's behavior and tactics. To detect attacks against any sensitive business-critical applications that use custom protocols:
- Create a custom service for any internal application or well-known service, such as VNC and SMTP.
- Select an appropriate decoy name and services, including custom service, for the decoy application.
- Add the created service as a decoy dataset.