# Best Practice Guide for Using Containment Integrations
Source: https://help.zscaler.com/deception/best-practice-guide-using-containment-integrations
PDF: https://help.zscaler.com/pdf/com/en/1531587.pdf

This guide provides detailed deployment recommendations for integrating various decoys with third-party security solutions, along with suggested containment scenarios.
The following are some of the containment scenarios along with recommended security solutions for different types of decoys:
- [Containment Scenarios and Configurations for Threat Intelligence (TI) Decoys](#ti-containment)
- [Containment Scenarios and Configurations for Network Decoys](#network-decoy-containment)
- [Containment Scenarios and Configurations for Zero Trust Decoys](#zero-trust-containment)
- [Containment Scenarios and Configurations for Active Directory (AD) Decoys](#ad-containment)
- [Containment Scenarios and Configurations for Endpoint Deception](#endpoint-containment)
- [Containment Scenarios and Configurations for Cloud Deception](#cloud-containment)
[]
-
-
-
-
-
| Containment Scenario | Recommended Integrations | Recommended Orchestration Rule |
| -------------------- | ------------------------ | ------------------------------ |
| When someone submits a credential on decoys having a username within a domain of your organization | You can use any of the following integrations:Palo Alto Networks (External Dynamic List - Attacker IPs)Palo Alto Networks (External Dynamic List - Attacker Hostnames)Fortinet (Threat Feeds - Attacker IPs)Fortinet (Threat Feeds - Attacker Domains)Check Point Firewall | `recon.post_data.username like /.*\@``<your_Org_Domain>``\.com.*/` |
| When someone tries to log in to an application with hard-coded default credentials | `threat_parse_ids is "recon_creds_submitted_hicontainer"` |
| When the payload is submitted by a source marked as denylisted on AbuseIPDB | `abuseip.abuseConfidenceScore greater than 74 and recon.method in ["PUT","POST"]` |
| When the payload submitted on a decoy is a known CVE exploit of a web application | `mitre_ids in ["T1190","T1595.002"]` |
| When the payload submitted on a decoy is a known CVE exploit of a VPN | `mitre_ids in ["T1133","T1595.002"]` |
[]
-
-
-
| Containment Scenario | Recommended Integrations | Orchestration Rule |
| -------------------- | ------------------------ | ------------------ |
| Running commands on a MySQL database | You can use any of the following integrations:CrowdStrike (based on IP address)Microsoft DefenderVMware Carbon Black | `sub_type is "mysql"` |
| Running commands on a PostgreSQL database | `type is "postgresql" and sub_type is "connect"` |
| Running commands on a MongoDB database | `type is "mongodb"` |
| Running command in SSH Shell | `linux.command_line like /.*(vi|vim|nano|ed).*\.(profile|bashrc|bash\_profile).*`/ |
| When someone submits a credential on web decoys | `web.post_data.password like /.*./ and web.post_data.username like /.*./` |
| When someone tries to log in to an internal web application with hard-coded default credentials | `threat_parse_ids is "web_hicontainer_login"` |
| When the payload submitted on a decoy is a known CVE exploit of a web application | `mitre_ids in ["T1190","T1595.002"]` |
| When the payload submitted on a decoy is known CVE exploit of a VPN | `mitre_ids in ["T1133","T1595.002"]` |
| When there is a login attempt on an FTP server decoy with the username "Anonymous" | `ftp.command is "USER anonymous"` |
| When there is a login attempt on an FTP server decoy with any credential | `ftp.command_message is "USER"` |
| Attempts to enumerate Windows SMB sessions remotely | `"NetrSessionEnum" in dce_rpc.operation` |
| When some payload is submitted on a web decoy | `web.method in ["POST","PUT"]` |
| Authentication attempts on SSH Shell of a decoy | `type is "ssh" and sub_type is "auth"` |
| Target discovery | `(sub_type is "scan" and scan.type is "port_scan") or (type is "network" and sub_type is "scan" and scan.type is "ip_scan")` |
[]
-
-
-
-
| Containment Scenario | Recommended Integrations | Recommended Orchestration Rule |
| -------------------- | ------------------------ | ------------------------------ |
| Running commands on a MySQL database | You can use any of the following integrations:CrowdStrike (based on IP address)Zscaler Private Access (ZPA)Microsoft DefenderVMware Carbon Black | `sub_type is "mysql"` |
| Running commands on a PostgreSQL database | `type is "postgresql" and sub_type is "connect"` |
| Running commands on a MongoDB database | `type is "mongodb"` |
| Running command in SSH Shell | `linux.command_line like /.*(vi|vim|nano|ed).*\.(profile|bashrc|bash\_profile).*/` |
| When someone submits a credential on web decoys | `web.post_data.password like /.*./ and web.post_data.username like /.*./` |
| When someone tries to log in to an internal web application with hard-coded default credentials | `threat_parse_ids is "web_hicontainer_login"` |
| When the payload submitted on a decoy is a known CVE exploit of a web application | `mitre_ids in ["T1190","T1595.002"]` |
| When the payload submitted on a decoy is a known CVE exploit of VPN | `mitre_ids in ["T1133","T1595.002"]` |
| When there is a login attempt on an FTP server decoy with the username "Anonymous" | `ftp.command is "USER anonymous"` |
| When there is a login attempt on an FTP server decoy with any credentials | `ftp.command_message is "USER"` |
| Attempt to enumerate Windows SMB sessions remotely | `"NetrSessionEnum" in dce_rpc.operation` |
| When some payload is submitted on a web decoy | `web.method in ["POST","PUT"]` |
| Authentication attempt on SSH Shell of a decoy | `type is "ssh" and sub_type is "auth"` |
| Target discovery | `(sub_type is "scan" and scan.type is "port_scan") or (type is "network" and sub_type is "scan" and scan.type is "ip_scan")` |
[]
-
-
-
| Containment Scenario | Recommended Integrations | Recommended Orchestration Rule |
| -------------------- | ------------------------ | ------------------------------ |
| When someone tries to log in to an environment using a decoy account | You can use any of the following integrations:CrowdStrike (based on IP address)Microsoft DefenderVMware Carbon Black | `type is "credtheft" and credtheft.event_id is not "4769" and sub_type is not "honeypot-buster"` |
| When a kerberoasting attack is attempted | `credtheft.event_id is "4769"` |
| When an AS-REP roasting attack is attempted | `type is "credtheft" and credtheft.event_id is "4768" and credtheft.pre_auth_type is "0"` |
[]
-
-
-
| Containment Scenario | Recommended Integrations | Recommended Orchestration Rule |
| -------------------- | ------------------------ | ------------------------------ |
| When someone successfully harvests a credential from Local Security Authority Subsystem Service (LSASS), and uses decoy breadcrumbs to authenticate further | You can use any of the following integrations:CrowdStrikeZscaler Private Access (ZPA)Zscaler Internet Access (ZIA) | `type is "endpoint" and sub_type is "imc"` |
| When someone tries to capture New Technology LAN Manager (NTLM) hashes using Link-Local Multicast Name Resolution (LLMNR) poisoning on a subnet | `type is "endpoint" and sub_type is "mitm"` |
| When someone tries connecting to an endpoint remotely via PSexec | `sub_type is "psexec"` |
[]
-
-
-
-
-
| Containment Scenario | Recommended Integrations | Recommended Orchestration Rule |
| -------------------- | ------------------------ | ------------------------------ |
| Login attempt using the decoy credential for IAM decoy, Entra ID user decoy, or service principal decoy | You can use any of the following integrations:Palo Alto Networks (External Dynamic List - Attacker IPs)Palo Alto Networks (External Dynamic List - Attacker Hostnames)Fortinet (Threat Feeds - Attacker IPs)Fortinet (Threat Feeds - Attacker Domains)Check Point Firewall | `threat_parse_ids in ["azure_user","azure_service_principal"]` |
| Azure App Service decoy's kudu endpoint was exploited with code execution | `threat_parse_ids is "azure_app_service_kudu_endpoint"` |
| Amazon Elastic Container Registry (ECR) repository was accessed to list, pull, or push images | `threat_parse_ids is "aws_ecr" and decoy.public is false` |
| Private Amazon Simple Storage Service (S3) Bucket accessed | `threat_parse_ids is "aws_s3" and decoy.public is false` |
| Amazon Web Services (AWS) Database queried | `threat_parse_ids in ["aws_dynamodb"] or (type is "aws" and sub_type is "rds" and aws.event_source is "mysql") or (type is "aws" and sub_type is "rds" and aws.event_source is "postgres")` |
| VM snapshot stolen for a potential data theft | `(type is ""aws"" and sub_type is ""vmsnapshot"") or (type is ""azure"" and sub_type is "vmsnapshot")` |