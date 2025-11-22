# Release Upgrade Summary (2025)
Source: https://help.zscaler.com/deception/release-upgrade-summary-2025

This article provides a summary of all new features and enhancements for Zscaler Deception.
The illusionblack.com cloud represents all clouds, and updates to specific clouds might take a few weeks to deploy. Some functions are not available until deployment completes.

**Clouds:** illusionblack.com
The following service updates were deployed to illusionblack.com on

## November 04, 2025
### Feature Available
#### Accessing Error Logs for Endpoint Agents
An icon to access error logs was added for endpoint agents.
[See image.](#Endpoint_errorlogs)
[]![Endpoint agents error logs](/sites/default/files/downloads/itdr/endpoint-settings/agents/about-endpoint-settings/endpoint_logs.png)
To learn more, see [About Landmine Agent and Agentless.](/deception/about-landmine-agent-agentless)

### Feature Available
#### AI-Powered Recommendations for Threat Intelligence Decoys
Zscaler Deception leverages AI to generate Threat Intelligence (TI) decoy recommendations with preselected hostnames, datasets, server banners, etc. This simplifies decoy creation and deployment, and reduces manual effort.
[See image.](#deception-rn-ai-ti-decoys)
To learn more, see [Creating a Threat Intelligence Decoy](/deception/creating-threat-intelligence-decoy).
[]![View AI-powered TI decoys](/sites/default/files/downloads/deception/release-notes/release-upgrade-summary-2025/deception-release-notes-ai-ti-decoys.png)

### Feature Available
#### Deprecation of Keychain-Based Lures
Keychain-based lures in macOS landmine policies are no longer supported.
To learn more, see [Configuring the Session Lures Module](/deception/configuring-session-lures-module).

### Feature Available
#### OS Upgrade for Decoy Connectors and Aggregators
The operating system for Decoy Connectors and Aggregators was upgraded to FreeBSD 14.3.

### Feature Available
#### User Interface Changes and Enhancements
The following UI changes were made to the Zscaler Deception Admin Portal:
-
On the Agents page (Endpoint Settings > Agents), a Client Connector Version column was added. This column provides information on the Zscaler Client Connector version used on the endpoints.
[See image.](#client-connetorn-version-column)
To learn more, see [About Landmine Agent and Agentless](/deception/about-landmine-agent-agentless).
-
In landmine policies, the option to hide file decoys in Linux endpoints (via Landmine Agentless) was updated to use dot (.) as a prefix before the filename, aligning with standard Linux conventions.
[See image.](#linux-hide-file)
To learn more, see [Configuring the File Decoys Module](/deception/configuring-file-decoys-module).
[]![Agents page showing the Client Connector Version column](/sites/default/files/downloads/deception/release-notes/release-upgrade-summary-2025/zscaler-deception-zcc-version-rn.jpg)
[]![File decoys configuriation showing the usage of prefix to hide files](/sites/default/files/downloads/deception/release-notes/release-upgrade-summary-2025/zscaler-deception-landmine-agentless-hide-file-linux.jpg)

## August 18, 2025
### Feature Available
#### AI-Powered Recommendations for Zero Trust Network Decoys
Zscaler Deception analyzes your Zscaler Private Access (ZPA) deployment and leverages AI to generate Zero Trust Network decoy recommendations with preselected datasets, banners, services, and ports. This simplifies decoy creation and deployment, and reduces manual effort.
[See image.](#deception-rn-ai-powered-zpa-decoys)
To learn more, see [Creating a Zero Trust Network Decoy](/deception/creating-zero-trust-network-decoy).
[]![View AI-Powered Zero Trust Network decoys](/sites/default/files/downloads/deception/release-notes/release-upgrade-summary-2025/deception-release-notes-ai-powered-zpa-decoys.png)

### Feature Available
#### Dashboard Enhancements
The Zscaler Deception dashboard includes the following enhancements:
-
The following advanced queries are available in the Select Query drop-down menu:
- Internal - High Priority Threat Detection
- Active Directory Threat Detection
- Identity Threat Detection
- CVE Threat Detection
- External - High Priority Threat
- Lateral Movement
- Database Threat Detection
- GenAI Threat Detection
- Cloud Threat Detection
- Whitelisted Events
[See image.](#selectquery)
-
The Attack Types filter includes two new options to filter alerts: GenAI and Cloud.
[See image.](#filters-window)
To learn more, see [Understanding the Zscaler Deception Dashboard](/deception/understanding-zscaler-deception-dashboard).
[]![The Select Query drop-down menu with the list of saved queries.](/sites/default/files/downloads/deception/release-notes/release-upgrade-summary-2025/deception-rn-saved-queries-dropdown-menu.png)
[]
![The Filters window listing the available filter types.](/sites/default/files/downloads/deception/release-notes/release-upgrade-summary-2025/deception-attack-types.png)

### Feature Available
#### New ThreatParse Rules
The following new ThreatParse rules that detect exploits of different application vulnerabilities were added:
| Application | CVE ID | Vulnerability Description |
| ----------- | ------ | ------------------------- |
| Ivanti Endpoint Manager Mobile | CVE-2025-4427 | An authentication bypass vulnerability in Ivanti Endpoint Manager Mobile allows attackers to access protected resources without proper credentials. This leads to unauthenticated remote code execution via unsafe user input processed by a bean validator that serves as a sink for Server-Side Template Injection. |
| Themewinter Eventin | CVE-2025-47539 | An unauthenticated privilege escalation vulnerability in the Eventin WordPress plugin version 4.0.27 or earlier leads to a full site compromise. Due to a missing permission check in a REST API endpoint, unauthenticated attackers can import users with arbitrary roles, including administrator. |
| Dassault Systèmes DELMIA Apriso | CVE-2025-5086 | A deserialization of untrusted data vulnerability affecting DELMIA Apriso from Release 2020 through Release 2025 can lead to remote code execution. |
| Commvault Command Center | CVE-2025-34028 | A path traversal vulnerability in Commvault Command Center (Innovation Release 11.38) allows an unauthenticated actor to upload ZIP files that, when expanded by the target server, result in remote code execution. |
| Microsoft Sharepoint | CVE-2025-53770 | A deserialization vulnerability in the on-premises Microsoft SharePoint Server allows unauthorized attackers to execute code remotely. |
To learn more, see [About ThreatParse Rules](/deception/about-threatparse-rules).

### Feature Available
#### User Interface Changes and Enhancements
The following tabs were renamed in the Zscaler Deception Admin Portal:
| **Old** | **New** |
| ------- | ------- |
| Settings > User & Roles > SSO | Settings > User & Roles > IdP Providers |
| Settings > Users & Roles > Support Users | Settings > Users & Roles > Zscaler Remote Assistance |
| Settings > Advanced Settings > Maintenance | Settings > Advanced Settings > Manage Events & Evidence |
| Settings > Advanced Settings > Debugging | Settings > Advanced Settings > Show/Hide Internal Components |
[See image.](#deception-rn-user-role-adv-sett-tabs)
To learn more, see:
- [About Users & Roles](/deception/about-users-roles)
- [About Identity Providers](/deception/about-identity-providers)
- [About Advanced Settings](/deception/about-advanced-settings)
[]![Image]()
![View Users & Roles and Advanced Settings tabs](/sites/default/files/downloads/deception/release-notes/release-upgrade-summary-2025/deception-release-notes-idp-maint-remote-support-ui-2.png)

### Feature Available
#### View Landmine Policies in Landmine-Based Events
The landmine.applied_policies field is added to the Events page in the Zscaler Deception Admin Portal. With this field, you can view the landmine policies associated with the endpoints that generate landmine-based events.
[See image.](#event-details-pane)
To learn more, see [About Event Logs](/deception/about-event-logs).
[]![Event details pane with the field showing landmine policies.](/sites/default/files/downloads/deception/release-notes/release-upgrade-summary-2025/zd-rn-ladnmine-policies-event.jpeg)

## June 23, 2025
### Feature Available
#### Customization of Landmine Agent's Service Name in macOS Endpoints
The landmine agent's service name in macOS endpoints can be customized to prevent the agent from being fingerprinted.
[See image.](#rn-ednpoint-settings-agent-name)
To learn more, see [Customizing Landmine Installer](/deception/customizing-landmine-installer).
[]![Configuring agent properties with the name field highlighted](/sites/default/files/downloads/deception/release-notes/release-upgrade-summary-2025/deception-rn-agent-macos.png)

### Feature Available
#### Gen AI Adaptive Decoys
You can deploy a generative AI (Gen AI) adaptive decoy, which dynamically adjusts to attackers' requests, and provides contextually appropriate responses using AI.
[See image.](#itdr-rn-gen-ai-adaptive-app)
To learn more, see [Configuring Services on a Network Decoy](/deception/configuring-services-network-decoy).
[]![Configure the Adaptive Generative AI application](/sites/default/files/downloads/deception/release-notes/release-upgrade-summary-2025/deception-release-notes-adaptive-gen-ai-app-1.png)

### Feature Available
#### Generative AI Decoys in Azure
You can create generative AI decoys in Microsoft Azure using OpenAI models. The generative AI decoys are interactive, and you can customize the decoys to generate fake responses to lure attackers into entering more prompts.
[See image.](#rn-gen-ai-azure-decoy)
To learn more, see [Creating a Generative AI Decoy in Azure](/deception/creating-generative-ai-decoy-azure).
[]![Configuring a generative AI decoy in Azure](/sites/default/files/downloads/deception/release-notes/release-upgrade-summary-2025/deception-azure-gen-ai-decoy-details.png)

### Feature Available
#### IPv6 Decoys
You can configure an IPv6-enabled subnet or VLAN to deploy IPv6-enabled Internal decoys. For an IPv6-enabled subnet or VLAN, you can either configure DNS servers using IPv6-based DHCP or an IPv6-based gateway/mask. To configure an IPv6-enabled subnet or VLAN, go to Settings > Topology > Interfaces.
[See image.](#network-interface-ipv6)
To learn more, see [Configuring a Subnet](/deception/configuring-subnet).
After you configure an IPv6 subnet, you can deploy an Internal decoy on the associated subnet.
[See image.](#decepion-rn-nw-decoy-ipv6)
To learn more, see [Creating an Internal Decoy](/deception/creating-internal-network-decoy) and [Deploying a Strategy](/deception/deploying-strategy).
The Decoy Connectors support dual-stack deployment with both IPv4 and IPv6 addresses.
[See image.](#decoy-connectors-ipv6)
To learn more, see [About Decoy Connectors](/deception/about-decoy-connectors).
Dual-stack networking with support for both IPv4 and IPv6 protocols is extended to aggregators and service backends.
[See image.](#components-ipv6)
[]![Image]()
![Configuring IPv6-enabled subnet of VLAN](/sites/default/files/downloads/deception/release-notes/release-upgrade-summary-2025/deception-rn-subnet-configuration.png)
[]![Decoy Connectors page highlighting dual-stack networking support](/sites/default/files/downloads/deception/release-notes/release-upgrade-summary-2025/deception-rn-decoy-connectors.png)
[]![Dual-stak network support highlighted for aggregators and service backends](/sites/default/files/downloads/deception/release-notes/release-upgrade-summary-2025/deception-rn-topology-components.png)
[]![Configure an Internal decoy](/sites/default/files/downloads/deception/miragemaker/strategy-builder/deception-strategy/creating-strategy/deception-release-notes-ipv6-nw-decoys.png)

## April 14, 2025
### Feature Available
#### Custom Names for File Decoys
You can add custom names for file decoys created using preconfigured file datasets.
[See image.](#zd-rn-file-name-support-file-decoy)
To learn more, see [Configuring the File Decoys Module](/deception/configuring-file-decoys-module).
[]![File decoy configuration with the Name field highlighted](/sites/default/files/downloads/deception/release-notes/release-upgrade-summary-2025/zd-rn-datasets-file-name-field.png)

### Feature Available
#### Datalist Keys with Value Restrictions
Zscaler Deception supports datalist keys with value restrictions. When you select specific keys while creating a datalist, the maximum number of values that can be added is restricted to 20. The following keys have value restrictions:
- Endpoint - Browser Lures Usernames (Max Values Allowed: 20)
- Endpoint - Database Lures Usernames (Max Values Allowed: 20)
- Endpoint - SSH/FTP Lures Usernames (Max Values Allowed: 20)
- Endpoint - Windows Credential Lures Usernames (Max Values Allowed: 20)
[See image.](#datalist_keys_with_value_restrictions)
To learn more, see [Configuring and Managing Datalists](/deception/configuring-and-managing-datalists).
[]
![View datalist keys with value restrictions](/sites/default/files/downloads/deception-release-notes-datalist-keys.png)

### Feature Available
#### Deprecation of Using a Decoy Connector as a Proxy
Zscaler no longer supports using a Decoy Connector as a proxy to landmine agents.

### Feature Available
#### Generative AI Decoys in AWS
You can create generative AI decoys in AWS using foundation models that are optimized for Amazon Bedrock. The generative AI decoys are interactive, and you can customize the decoys to generate fake responses to lure attackers into entering more prompts. You can also log the prompts and responses between the adversary and the generative AI decoy to gain insights into the objectives of the adversaries.
[See image.](#gen-ai-decoy-window)
The following ThreatParse rules were added to process events relating to the generative AI decoys in AWS:
| ThreatParse Rules | Description |
| ----------------- | ----------- |
| AWS GenAI Agent was accessed | Adversaries run queries to list details about the agent |
| AWS GenAI Agent was invoked | Adversaries target agents to invoke models and run malicious prompts |
| AWS GenAI Model was invoked | Adversaries target models run malicious prompts and get access to security information |
To learn more, see [Creating a Generative AI Decoy in AWS](/deception/v4_27/creating-generative-ai-decoy-aws).
[]![Configuringa generative AI decoy in AWS](/sites/default/files/downloads/deception/release-notes/release-upgrade-summary-2025/deception-gen-ai-decoy-window.png)

### Feature Available
#### Generative AI Lures Authentication
You can enable the Authentication option when configuring a generative AI decoy service. When enabled, adversaries can use decoy credentials deployed via browser lures or file decoys to authenticate and access the decoy. The authentication feature makes the decoys look more realistic and captures adversary activities.
[See image.](#deception-rn-auth-gen-ai)
To learn more, see [Configuring Services on a Network Decoy](/deception/configuring-services-network-decoy), [Configuring the Browser Lures Module](/deception/configuring-browser-lures-module), and [Configuring the File Decoys Module](/deception/configuring-file-decoys-module).
[]![Enable authentication for an Gen AI decoy](/sites/default/files/downloads/deception/release-notes/release-upgrade-summary-2025/deception-release-note-gen-ai-authentication-new.png)

### Feature Available
#### Mark Events or Attackers as Unsafe
You can select an event or attacker and mark it as unsafe. When you mark an event or attacker as unsafe, the allowlist rules are removed, and the attacker is flagged for further investigation.
[See image.](#mark_as_unsafe_option)
To learn more, see [Taking Action from the Dashboard](/deception/taking-action-from-the-dashboard).
[]
![View mark as unsafe option](/sites/default/files/downloads/deception-release-notes-mark-as-unsafe.png)

### Feature Available
#### Multiple Accounts and Regions in Azure Cloud Deception
You can set up cloud deception with Microsoft Azure for multiple accounts. Azure decoys can be deployed across multiple regions within the same account.
[See image.](#azure-multiple-accounts-support)
To learn more, see [About Cloud Deception with Azure](/deception/about-cloud-deception-with-azure).
[]![Cloud Deception configuration page listing multiple Azure accounts](/sites/default/files/downloads/deception/release-notes/release-upgrade-summary-2025/zscaler-deception-release-note-azure-multi-account.png)

### Feature Available
#### New Criteria in Landmine Policies
The following new criteria for selecting endpoints were added to landmine policies:
| Selection Criterion | Description |
| ------------------- | ----------- |
| DNS Hostname (Specific) | To select endpoints based on their FQDNs by specifying the complete FQDN value |
| DNS Hostname (RegEx) | To select endpoints based on their FQDNs by specifying a regular expression for the FQDN value |
To learn more, see [Creating a Landmine Policy](/deception/creating-landmine-policy#specifying-criteria).

### Feature Available
#### OS Upgrade on Decoy Connectors and Aggregators
The operating system for Decoy Connectors and Aggregators was upgraded to FreeBSD 14.2.

### Feature Available
#### Requirement to Run Deployment Script in Microsoft Azure
Following the latest update of Zscaler Deception, customers with an existing deployment of cloud decoys in Microsoft Azure must run the Azure deployment script to sync settings. This is required to ensure continued normal operation of the health check function app deployed by Deception in the Azure cloud.
To learn more, see [About Cloud Deception with Azure](/deception/about-cloud-deception-with-azure), [Setting Up Cloud Deception with Microsoft Azure](/deception/setting-cloud-deception-microsoft-azure), [Understanding the Functions of the Azure Deployment Script](/deception/understanding-functions-azure-deployment-script), and [Obtaining the Deployment Script for Azure](/deception/obtaining-deployment-script-azure).

### Feature Available
#### Shares Service Enhancements
When configuring the Shares service in a network decoy, you can disable the Guest Accessible option to specify custom user credentials for accessing the shared folder.
[See image.](#deception-rn-shares-cust-creds)
To learn more, see [Configuring Services on a Network Decoy](/deception/configuring-services-network-decoy).
[]![Specify custom user credentials](/sites/default/files/downloads/deception/release-notes/release-upgrade-summary-2025/deception-release-notes-cust-user-pwd-shares-1.png)

### Feature Available
#### Support for DbVisualizer Lures for macOS Endpoints
The DbVisualizer lure was added to Session Lures in landmine policies for macOS endpoints.
[See image.](#macos-db-visualizer)
To learn more, see [Configuring the Session Lures Module](/deception/configuring-session-lures-module#mac-lures).
[]![Session lures list for macOS endpointd with DbVisualizer option highlighted](/sites/default/files/downloads/deception/release-notes/release-upgrade-summary-2025/zd-rn-session-lures-dbvisualizer.png)

### Feature Available
#### User Interface Changes and Enhancements
The option to select multiple entries and delete them was added to the Policies page (Landmine > Policies).
[See image.](#deception-policies-multi-select-delete)
[]![Landmine policies page with options to select and delete multiple entries highlighted](/sites/default/files/downloads/deception/release-notes/release-upgrade-summary-2025/deception-release-note-options-multi-select-delete-policies.png)

### Feature Available
#### View Allowlisted Rules
When an event or attacker is marked as safe due to an allowlist rule, you can view the specific rule that triggered the action on the Event Logs page.
[See image.](#whitelisted_rule)
To learn more, see [About Event Logs](/deception/about-event-logs).
[]
![View whitelisted rule](/sites/default/files/downloads/deception-release-notes-whitelist-rule.png)

## March 05, 2025
### Feature Available
#### Customizing an Interactive Generative AI Decoy
When deploying an interactive generative AI decoy using high-interaction datasets, you can customize the decoy using the following decoy types:
- UI: Allows you to configure a custom user interface (UI) application using the theme builder available in the Zscaler Deception Admin Portal.
- API: Provides APIs that are fully compatible with OpenAI specifications. These APIs support functionalities such as chat completion and model retrieval.
[See image.](#itdr-rn-gen-ai-customize-theme)
You can preview your customizations before deploying the interactive generative AI decoy.
[See image.](#itdr-rn-gen-ai-preview)
[]![Customize interactive Gen AI decoy](/sites/default/files/downloads/itdr/release-notes/release-upgrade-summary-2025/itdr-release-notes-customize-gen-AI-theme-2.png)
[]![Preview customization](/sites/default/files/downloads/itdr/release-notes/release-upgrade-summary-2025/itdr-release-notes-customize-gen-AI-preview-theme-2.png)

### Feature Available
#### Export Event Fields in JSON
Deception supports exporting event fields in JSON format. You can export all the event fields and use them for further analysis and investigation.
[See image.](#export_event_logs)
To learn more, see [Exporting Event Logs](/deception/exporting-event-logs).
[]
![Export event fields as JSON](/sites/default/files/downloads/deception/release-notes/release-upgrade-summary-2025/deception-release-notes-exporting-event-log.png)

### Feature Available
#### Integration with Amazon GuardDuty
Zscaler Deception supports integration with Amazon GuardDuty to isolate and contain attackers who interact with decoys by blocking access to those users across AWS resources.
[See image.](#aws-guardduty-1519641)
[]![Configuring AWS GuardDuty Intgeration](/sites/default/files/downloads/deception/orchestrate/containment-integrations/containment-configuration-guide-zscaler-private-access-zpa/zscaler-awsguardduty.png)

### Feature Available
#### Multiple Accounts and Regions in AWS Cloud Deception
You can set up cloud deception with AWS for multiple accounts. AWS decoys can be deployed across multiple regions within the same account.
[See image.](#rn-aws-multiple-accounts)
To learn more, see [About Cloud Deception with AWS](/deception/v4_26/about-cloud-deception-with-aws).
[]![Setting up  cloud deception with AWS](/sites/default/files/downloads/deception/deceive/cloud-deception/aws/creating-and-managing-tags-aws/zscaler-dception-release-note-aws-multiple-accounts.png)

### Feature Available
#### New Datasets
New Application Datasets
The following application datasets were added:
| Application | CVE/Static | Description of Vulnerability |
| ----------- | ---------- | ---------------------------- |
| Grafana | High interaction | Grafana open source software enables you to query, visualize, alert, and explore your metrics, logs, and traces wherever they are stored. Attackers exploit Grafana to steal sensitive data, pivot to other systems using stored credentials, deploy malware, or maintain persistence by creating admin accounts. They can also exploit vulnerabilities to gain deeper access, launch phishing attacks, or use the system for cryptojacking. |
| BitBucket | Static | Web-based version control repository hosting service which is primarily used for source code management (SCM) that allows teams of developers to collaborate on software development projects effectively. |
| Fortinet SSL VPN | Static | Web-based Fortinet Secure Sockets Layer Virtual Private Network (SSL VPN) solution, a feature of Fortinet's FortiGate firewalls that enables secure remote access to private networks using an encrypted SSL tunnel. |
| NextCloud | Static | Web-based self-hosted file sharing and collaboration platform that enables individuals and organizations to store, access, sync, and share their data securely over the cloud. |
| VMware Aria | Static | VMware Aria is a transformational multi-cloud management solution thatfeatures VMware Aria Hub, a single platform unifying cost, performance,configuration, and delivery automation to optimize business outcomes for anycloud, any platform, any tool, and every persona. However if misconfigured or compromised, attackers can exploit VMware Aria Hub to gain unauthorized access to cloud environments, manipulate configurations, and exfiltrate sensitive data. Additionally, they can leverage its automation features to deploy malicious workloads or escalate privileges across multi-cloud infrastructures. |
| SAP HANA Web UI | Static | SAP HANA Web UI is a web-based interface for managing and interacting with SAP HANA databases, providing tools for administration, monitoring, and development. It allows users to configure settings, execute queries, and manage database resources via a browser. However if misconfigured or vulnerable, attackers can exploit weak authentication or exposed endpoints to gain unauthorized access, execute malicious queries, and exfiltrate sensitive business data. Additionally, they can escalate privileges to manipulate database configurations or deploy backdoors for persistent access. |
To learn more, see [About Static Application Datasets](/deception/about-static-application-datasets) and [About High-Interaction Containers](/deception/about-high-interaction-containers).
New Application Datasets for Vulnerabilities
The following datasets for different application vulnerabilities were added:
| Application | CVE/Static | Description of Vulnerability |
| ----------- | ---------- | ---------------------------- |
| Journyx | CVE-2024-6893 | Improper Restriction of XML External Entity Reference (XXE) vulnerability allows the XML body of SOAP requests to contain references to external entities via the soap_cgi.pyc API handler. This allows an unauthenticated attacker to read local files, perform server-side request forgery, and overwhelm the web server resources. |
| Palo Alto Expedition | CVE-2024-9463 | OS command injection vulnerability in Palo Alto Networks Expedition allows an unauthenticated attacker to run arbitrary OS commands as root in Expedition, resulting in disclosure of usernames, cleartext passwords, device configurations, and device API keys of PAN-OS firewalls. |
| Apache Solr | CVE-2024-45216 | Improper Authentication vulnerability in Apache Solr affects instances using the PKIAuthenticationPlugin, which is enabled by default when Solr Authentication is used. This is vulnerable to authentication bypass. A fake ending at the end of any Solr API URL path allows requests to skip authentication while maintaining the API contract with the original URL path. This fake ending looks like an unprotected API path, however it is stripped off internally after authentication but before API routing. |
| Microsoft Exchange Server | CVE-2021-26855 | Microsoft Exchange Server Remote Code Execution Vulnerability, which is part of an attack chain that can allow remote code execution on Microsoft Exchange Server. The initial attack requires the ability to make an untrusted connection to Exchange server port 443. Other portions of the chain can be triggered if an attacker already has access or can convince an administrator to open a malicious file. |
| Palo Alto PAN-OS | CVE-2024-9474 | Privilege escalation vulnerability that allows a PAN-OS administrator with access to the management web interface to execute root-level commands, granting full control over the affected device. When combined, these vulnerabilities (CVE-2024-0012 and CVE-2024-9474) enable unauthenticated adversaries to execute arbitrary commands on the firewall with root privileges. |
| Palo Alto PAN-OS | CVE-2024-0012 | Authentication bypass vulnerability in Palo Alto Networks PAN-OS software enables an unauthenticated attacker with network access to the management web interface to gain PAN-OS administrator privileges to perform administrative actions, tamper with the configuration, or exploit other authenticated privilege escalation vulnerabilities like CVE-2024-9474. |
| Apache OFBiz | CVE-2023-49070 | Apache OFBiz Authentication Bypass Vulnerability affects Apache OFBiz versions earlier than 18.12.10. CVE-2023-49070 stems from the existence of a deprecated XML-RPC component within Apache OFBiz. This vulnerability can be exploited by sending a HTTP POST request with empty or invalid USERNAME and PASSWORD parameters, and thus the login function inadequately validates these empty or invalid usernames and passwords. This exposes a risk wherein an attacker can execute arbitrary code (ACE) on the targeted Apache OFBiz server without the need for prior authentication. |
| SonicWall GMS | CVE-2023-34124 | Remote Code Execution (RCE) vulnerability in SonicWall Global Management System allows Web Service Authentication Bypass. By crafting specific requests, an attacker can authenticate without proper credentials and execute commands. This vulnerability impacts GMS versions 9.3.2-SP1 and earlier. |
| Zyxel NAS326 | CVE-2024-29972 | Command injection vulnerability identified in the CGI program remote_help-cgi affecting Zyxel NAS326 firmware versions earlier than V5.21(AAZF.17)C0 and NAS542 firmware versions earlier than V5.21(ABAG.14)C0. This vulnerability can allow an unauthenticated attacker to execute arbitrary operating system (OS) commands by sending a specially crafted HTTP POST request. |
| Apache OFBiz | CVE-2023-51467 | Apache OFBiz Authentication Bypass Vulnerability allows attackers to bypass authentication mechanisms, granting them unauthorized access to the system. If exploited, attackers can remotely execute arbitrary code, potentially compromising the device and its data. |
To learn more, see [About Vulnerable Application Datasets (CVE Datasets)](/deception/about-vulnerable-application-datasets-cve-datasets).

### Feature Available
#### New ThreatParse Rules
The following ThreatParse rules that detect exploits of different application vulnerabilities were added:
| Application | CVE ID | Description |
| ----------- | ------ | ----------- |
| Journyx | CVE-2024-6893 | Improper Restriction of XML External Entity Reference (XXE) vulnerability allows the XML body of SOAP requests to contain references to external entities via the soap_cgi.pyc API handler. This allows an unauthenticated attacker to read local files, perform server-side request forgery, and overwhelm the web server resources. |
| Palo Alto Expedition | CVE-2024-9463 | OS command injection vulnerability in Palo Alto Networks Expedition allows an unauthenticated attacker to run arbitrary OS commands as root in Expedition, resulting in disclosure of usernames, cleartext passwords, device configurations, and device API keys of PAN-OS firewalls. |
| Palo Alto Expedition | CVE-2024-9465 | SQL injection vulnerability in Palo Alto Networks Expedition allows an unauthenticated attacker to reveal Expedition database contents, such as password hashes, usernames, device configurations, and device API keys. With this, attackers can also create and read arbitrary files on the Expedition system. |
| Palo Alto Expedition | CVE-2024-5910 | Palo Alto Networks Expedition Missing Authentication Vulnerability impacts versions earlier than 1.2.92 of missing authentication for a critical function, which leads to an Expedition admin account takeover for attackers with network access to Expedition. |
| Apache Solr | CVE-2024-45216 | Improper Authentication vulnerability in Apache Solr affects instances using the PKIAuthenticationPlugin, which is enabled by default when Solr Authentication is used. This is vulnerable to authentication bypass. A fake ending at the end of any Solr API URL path allows requests to skip authentication while maintaining the API contract with the original URL path. This fake ending looks like an unprotected API path, however it is stripped off internally after authentication but before API routing. |
| Microsoft Exchange Server | CVE-2021-26855 | Microsoft Exchange Server Remote Code Execution Vulnerability, which is part of an attack chain that can allow remote code execution on Microsoft Exchange Server. The initial attack requires the ability to make an untrusted connection to Exchange server port 443. Other portions of the chain can be triggered if an attacker already has access or can convince an administrator to open a malicious file. |
| D-Link NAS | CVE-2024-10914 | OS command injection vulnerability is found in D-Link DNS-320, DNS-320LW, DNS-325, and DNS-340L up to 20241028. It is a vulnerability that is declared as critical. Affected by this vulnerability is the function cgi_user_add of the file/cgi-bin/account_mgr.cgi?cmd=cgi_user_add. The manipulation of the argument name leads to OS command injection. |
| Palo Alto PAN-OS | CVE-2024-9474 | Privilege escalation vulnerability that allows a PAN-OS administrator with access to the management web interface to execute root-level commands, granting full control over the affected device. When combined, these vulnerabilities (CVE-2024-0012 and CVE-2024-9474) enable unauthenticated adversaries to execute arbitrary commands on the firewall with root privileges. |
| Apache OFBiz | CVE-2023-49070 | Apache OFBiz Authentication Bypass Vulnerability affects Apache OFBiz versions earlier than 18.12.10. CVE-2023-49070 stems from the existence of a deprecated XML-RPC component within Apache OFBiz. This vulnerability can be exploited by sending a HTTP POST request with empty or invalid USERNAME and PASSWORD parameters, and thus the login function inadequately validates these empty or invalid usernames and passwords. This exposes a risk wherein an attacker can execute arbitrary code (ACE) on the targeted Apache OFBiz server without the need for prior authentication. |
| SonicWall GMS | CVE-2023-34124 | Remote Code Execution (RCE) vulnerability in SonicWall Global Management System allows Web Service Authentication Bypass. By crafting specific requests, an attacker can authenticate without proper credentials and execute commands. This vulnerability impacts GMS versions 9.3.2-SP1 and earlier. |
| Apache OFBiz | CVE-2023-51467 | Apache OFBiz Authentication Bypass Vulnerability allows attackers to bypass authentication mechanisms, granting them unauthorized access to the system. If exploited, attackers can remotely execute arbitrary code, potentially compromising the device and its data. |
| Zyxel NAS326 | CVE-2024-29972 | Command injection vulnerability identified in the CGI program remote_help-cgi affecting Zyxel NAS326 firmware versions earlier than V5.21(AAZF.17)C0 and NAS542 firmware versions earlier than V5.21(ABAG.14)C0. This vulnerability can allow an unauthenticated attacker to execute arbitrary operating system (OS) commands by sending a specially crafted HTTP POST request. |
| Microsoft SharePoint | CVE-2024-38094 | Critical Remote Code Execution (RCE) vulnerability identified in Microsoft SharePoint, potentially allowing attackers to execute arbitrary code on affected servers. If exploited, an attacker can gain unauthorized access, deploy malicious payloads, or compromise sensitive data within the SharePoint environment. |
To learn more, see [About ThreatParse Rules](/deception/about-threatparse-rules).

### Feature Available
#### QoS Rate Limit for Threat Intelligence (TI) Decoys
An attacker generating 1,000 events via a TI decoy is blocked for one hour, and a Quality of Service (QoS) event is generated. A cool-down period of two hours applies to the QoS events, and no new QoS event is generated during this period for the same attacker.

### Feature Available
#### ZPA Containment Support for ZIdentity-Enabled Tenants
Support for containment with Zscaler Private Access (ZPA) is extended to ZIdentity-enabled tenants. If a user is contained with ZPA, then real apps become inaccessible and only app decoys remain accessible.
To learn more, see [Containment Configuration Guide for Zscaler Private Access (ZPA)](/deception/containment-configuration-guide-zscaler-private-access-zpa).

### Feature in Limited Availability
#### Active Directory Decoy Deployment Using Server Agents
You can manage Active Directory (AD) decoy (users and computer objects) deployment by installing a server agent on a domain controller (DC) and designating it to an AD domain. The AD domains managed by server agents are listed on the Domains page (Deceive > Active Directory Decoys > Domains).
[See image.](#deception-rn-server-agent-ad-domains)
Server agents provide the following benefits:
- Automates AD decoy deployment without the need to manually download and run deployment scripts from the Zscaler Deception Admin Portal.
- Streamlines event log collection without the need to configure trigger scripts for forwarding AD event logs. All server agents installed on a DC automatically monitor events and forward logs to the Deception Admin Portal or SIEM solutions.
- Improves the effectiveness of AD decoys by automatically refreshing them. The server agent periodically simulates activities on AD decoy objects by performing password resets, login actions, etc., every few months. This ensures that decoys appear active and frequently used, mimicking legitimate assets.
With the server agent feature, the following user interface enhancements were made to the Decoy Users (Deceive > Active Directory Decoys > Decoy Users) and Decoy Computers (Deceive > Active Directory Decoys > Decoy Computers) pages:
- The AD decoy deployment status icons were added. The color-coded icons (green, yellow, etc.) indicate the deployment status of the decoys.
- The Domain filter was added to filter AD decoys by domain.
- The Last Updated column was added to track updates to the AD decoys.
[See image.](#deception-ad-server-agent-ui-changes)
To learn more, see [About Server Agents](/deception/about-server-agents), [Adding an Active Directory Domain](/deception/adding-active-directory-domain), and [About Active Directory Decoys](/deception/about-active-directory-decoys).
[]![View AD domains managed by server agent](/sites/default/files/downloads/deception/release-notes/release-upgrade-summary-2025/deception-release-notes-server-ad-agent-domains-page-1.png)
[]![UI enhancements to AD Decoys](/sites/default/files/downloads/deception/release-notes/release-upgrade-summary-2025/deception-release-notes-server-agent-ad-user-computer.png)
