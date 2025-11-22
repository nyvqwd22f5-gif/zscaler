# Release Upgrade Summary (2024)
Source: https://help.zscaler.com/deception/release-upgrade-summary-2024

This article provides a summary of all new features and enhancements for Zscaler Deception .
The illusionblack.com cloud represents all clouds, and updates to specific clouds might take a few weeks to deploy. Some functions are not available until deployment completes.

**Clouds:** illusionblack.com
The following service updates were deployed to illusionblack.com on

## December 04, 2024
### Feature Available
#### Adding Safe Processes to Process Tree Check
You can configure a program as a safe process and include it as part of the process tree check for generating events. Decoy interactions that involve process trees with these safe processes do not generate events.
[See image.](#rn-safe-process-check-tree)
To learn more, see [About Safe Processes](/deception/about-safe-processes) and [Configuring a Safe Process](/deception/configuring-safe-process).
[]![A screenshot highlighting the option to add safe process to process tree check](/sites/default/files/downloads/deception/release-notes/release-upgrade-summary-2024/zscaler-deception-check-process-tree.png)

### Feature Available
#### Blocklist Enhancements
On the Blocklists page (Deceive > Deceive Settings > Blocklist), you can create blocklists in bulk where the blocklist rule is applied to all decoy IP addresses on multiple Decoy Connectors.
[See image.](#deception-rn-blocklist-bulk)
To learn more, see [Creating Blocklists](/deception/creating-blocklist).
[]![Create blocklists in bulk](/sites/default/files/downloads/deception/release-notes/release-upgrade-summary-2024/deception-release-notes-blocklist-action-bulk.png)

### Feature Available
#### Deploy Strategy User Interface Enhancements
The following user interface enhancements were made to the Deploy Strategy page (Deceive > Deploy Strategy):
-
If the ZPA decoy type was selected when creating a strategy, the ZPA and Landmine toggles in the Deploy Network Strategy window are enabled by default. Also, all of the ZPA domains are automatically selected.
[See image.](#deception-rn-deploy-strategy-zpa-changes)
-
The Copy icon was added on the Network Decoys and Threat Intelligence (TI) Decoys tabs to copy the hostnames.
[See image.](#deception-rn-deploy-strategy-copy-hostname)
-
The default network strategy naming convention was changed to <`Strategy name`> <`Date and time`>.
[See image.](#deception-rn-deploy-strategy-name)
- The Create Decoys button appears only when there are decoys that are already deployed in the Zscaler Deception Admin Portal. This button allows you to just create the decoys and deploy them later without retriggering the deployment automatically at the time of decoy creation.
[See image.](#deception-rn-create-decoys)
To learn more, see [Deploying a Strategy](/deception/deploying-strategy).
[]![Configure ZPA decoy strategy](/sites/default/files/downloads/deception/release-notes/release-upgrade-summary-2024/deception-release-notes-zpa-landmine-enabled.png)
[]![Copy network and TI decoys hostname](/sites/default/files/downloads/deception/release-notes/release-upgrade-summary-2024/deception-release-notes-strategy-copy-icon.png)
[]![Strategy default naming convention](/sites/default/files/downloads/deception/release-notes/release-upgrade-summary-2024/deception-release-notes-strategy-naming-conv.png)
[]![Create decoy button](/sites/default/files/downloads/deception/release-notes/release-upgrade-summary-2024/deception-release-notes-strategy-create-decoy-conditional-hiding.png)

### Feature Available
#### Generative AI Decoys
Enterprises are increasingly adopting generative AI (Gen AI) technologies, such as large language models (LLMs) in their products, services, and internal operations. These systems have become a growing attack surface for adversaries. Threat actors target generative AI infrastructure for data exfiltration, asset compromise, organizational intelligence gathering, etc. Attackers target datasets for data poisoning and data exfiltration. They also use interactive attacks such as prompt injection to target AI systems and extract valuable data.
To address these emerging risks, Zscaler Deception provides high-interaction generative AI decoys that mimic assets like chatbots, LLM servers, APIs, etc. These decoys swiftly detect attacks and deflect the attacker from compromising the real assets. The generative AI decoy's capability extends advanced threat detection and mitigation to generative AI attack factors and prepares your organization to deal with the new rise of targeted attacks.
You can create interactive and file-based generative AI decoys.
Interactive Generative AI Decoys
Interactive generative AI decoys mimic common web-based generative AI infrastructure such as chatbots, LLM servers, APIs, etc. You can deploy these decoys by configuring generative AI services and AI-based high-interaction or static application datasets. You can configure these decoys according to your organization’s use case and generate responses based on the attacker’s intent. You can deploy interactive generative AI decoys on Zero Trust Networks via Zscaler Private Access (ZPA) decoys, customer-managed internal networks via Internal Decoys, and the internet via Threat Intelligence (TI) decoys.
[See image.](#deception-rn-web-gen-ai-decoy)
To learn more, see [Deploying Interactive Generative AI Decoys](/deception/deploying-interactive-generative-ai-decoys) and [Configuring Generative AI Services on a Network Decoy](/deception/configuring-services-network-decoy#deception-config-gen-ai-service-network-decoys).
The following application datasets were added to create interactive generative AI decoys:
| Application | Type |
| ----------- | ---- |
| GenAI OpenWebUI | High-interaction |
| Apache Airflow | Static |
| Bento-Frontend | Static |
| ClearML | Static |
| GitLab GenAI | Static |
| JupyterHub | Static |
| MetaFlow | Static |
| MLFlow | Static |
| RayServe | Static |
To learn more, see [About Static Application Datasets](/deception/about-static-application-datasets) and [About High-Interaction Containers](/deception/about-high-interaction-containers).
File-Based Gernerative AI Decoys
File-based generative AI decoys mimic the resources used to set up local LLMs. You can lure attackers by deploying these decoy file resources to one of the following assets:
- Endpoints via [landmine policies](/deception/about-policies)
- Azure Cloud via [storage account container decoy](/deception/creating-storage-account-container-decoy-azure) or [storage account file share decoy](/deception/creating-storage-account-file-share-decoy-azure)
- AWS Cloud via [S3 decoys](/deception/creating-s3-decoy-aws)
- [Network decoys](/deception/about-network-decoys) via [FTP service](/deception/configuring-services-network-decoy)
In addition, you can configure [session lures](/deception/configuring-session-lures-module) via [landmine polices](/deception/about-policies) to point to any file-based generative AI decoys.
The following new file datasets were added to create file-based generative AI decoys:
| File Dataset | Description |
| ------------ | ----------- |
| Falcon-7b | An LLM developed by the Technology Innovation Institute (TII) for use in summarization, text generation, and chatbots. |
| GPT-2 Large | An LLM developed by OpenAI optimized for generating high-quality, context-aware text across diverse applications. |
To learn more, see [About File Datasets](/deception/about-file-datasets).
Enhancements to Landmine Policies
The following lure modules in landmine polices were updated to support generative AI decoys:
| Lure Module | Enhancements |
| ----------- | ------------ |
| Browser Lures | Ability to add web-based generative AI decoys as target decoys |
| Session Lures | Ability to add web-based and file-based generative AI decoys as target decoys |
| File Decoys | Ability to deploy file-based decoys to endpoints or add a web-based decoy as a target decoy for credential file decoys |
[See image.](#landmine-genai-1510616)
To learn more, see [About Landmine Policies](/deception/about-policies).
Generative AI Network Personality
Deception provides a [generative AI decoy personality](/deception/about-network-decoy-personalities) that serves as templates to deploy generative AI decoys via network decoys. You can use this personality when configuring network decoys, or use them in a [deception strategy](/deception/about-deploy-strategy) to create decoys.
[See image.](#deception-rn-gen-ai-strategy)
To learn more, see [About Network Decoy Personalities](/deception/about-network-decoy-personalities).
ThreatParse Details and Event Logs
When an adversary compromises an endpoint and attempts a data exfiltration attack to find credentials to an internally hosted LLM application, which is a generative AI decoy, Deception detects the attack and generates event logs. It also captures the prompt and automatically categorizes it as malicious, etc., for further investigation using the generative AI Malicious Input Prompt ThreatParse rule.
In the Gen AI Malicious Input Prompt ThreatParse rule, the classification of whether the prompt is malicious and the categorization are determined by enriching data using Deception AI. Hence, the values for the `gen ai malicious` and `gen ai malicious category` fields might be inaccurate. Verify the details for accuracy or completeness before making any decisions.
[See image.](#gen-ai-fields-1510616)
After the threat is detected, the configured [orchestration rules](/deception/about-orchestration-rules) automatically contain the attack and block the compromised user from accessing any private applications in the environment.
The responses or content generated by the Deception AI is for information purposes only. The content is prone to inaccuracy and AI hallucinations. Verify the details for accuracy or completeness before making any decisions.
To learn more, see [Viewing ThreaParse Details](/deception/viewing-threatparse-details) and [About Event Logs](/deception/about-event-logs).
[]![View web-based Gen AI decoy](/sites/default/files/downloads/deception/release-notes/release-upgrade-summary-2024/deception-release-notes-gen-ai-web-decoys.png)
[]![View generative AI network decoy personality](/sites/default/files/downloads/deception/release-notes/release-upgrade-summary-2024/deception-release-notes-gen-ai-nw-personality.png)
[]![A screenshot showing the various landmine lure modules with Gen AI funtionaliites](/sites/default/files/downloads/deception/release-notes/release-upgrade-summary-2024/zd-rn-lure-modules.png)
[]![A screenshot highlighting the data enriched by Decpetion AI](/sites/default/files/downloads/deception/release-notes/release-upgrade-summary-2024/zd-rn-auto-generated.png)

### Feature Available
#### New Datasets
A static dataset for Ivanti Virtual Traffic Manager (vTM) was added. Ivanti vTM is a software-based application delivery controller (ADC) that optimizes web application performance, security, and scalability through load balancing, traffic shaping, and acceleration in virtual, cloud, or container environments.
To learn more, see [About Static Application Datasets](/deception/about-static-application-datasets).

### Feature Available
#### New ThreatParse Rules
The following datasets for different application vulnerabilities were added:
| Application | CVE ID | Description |
| ----------- | ------ | ----------- |
| Ivanti Virtual Traffic Manager (vTM) | CVE-2024-7593 | A flawed authentication algorithm in Ivanti Virtual Traffic Manager (vTM), except in versions 22.2R1 and 22.7R2, enables remote unauthenticated attackers to bypass admin panel authentication, potentially granting unauthorized access and control over the system. |
| Adobe Commerce and Magento | CVE-2024-34102 | Improper Restriction of XML External Entity Reference (XXE) vulnerability that can result in arbitrary code execution in Adobe Commerce versions 2.4.7, 2.4.6-p5, 2.4.5-p7, 2.4.4-p8, and earlier. |
To learn more, see [About ThreatParse Rules](/deception/about-threatparse-rules).

### Feature Available
#### Support for Target Decoys in Credential File Decoys
While configuring credential file decoys using landmine policies, you can select specific Threat Intelligence (TI) or network decoys as target decoys from the Target Decoys drop-down menu. Credentials to access the selected decoys are generated and placed in the credential files.
[See image.](#credentials-file-configuration-target-decoys)
To learn more, [Configuring the File Decoys Module](/deception/configuring-file-decoys-module) and [About Landmine Policies](/deception/about-policies).
[]![zscaler-deception-file-decoy-rn.png](/sites/default/files/downloads/deception/release-notes/release-upgrade-summary-2024/zscaler-deception-file-decoy-rn.png)

## August 14, 2024
### Feature Available
#### Changes to the Force Apply Option in Edge Lures
Due to changes in the deployment of browser lures on endpoints, the Force Apply option for Edge browsers does need not be enabled for landmine agent or agentless versions later than 4.23. The Force Apply option was used to deploy landmine policies when the Startup Boost option was enabled in Edge browsers. For older versions (up to 4.23) of landmine agent and agentless, the Force Apply option is required to apply the policies if the Startup Boost option is enabled in Edge browsers.
To learn more, see [Configuring the Browser Lures Module](/deception/configuring-browser-lures-module).

### Feature Available
#### Force Delete Cloud Deception Settings
The option to force delete Cloud Deception settings was added for both Azure and AWS configurations. This can be used when the deployment script fails to remove the entries of the cloud resources from the Zscaler Deception Admin Portal.
For Azure Cloud Deception, the Force Delete option was added to Deceive > Cloud Deception > Azure > Settings.
[See image.](#rn-azure-force-delete-button)
To learn more, see [Deleting Azure Deception Settings](/deception/deleting-azure-deception-settings).
For AWS Cloud Deception, the Force Delete option was added to Deceive > Cloud Deception > AWS > Settings.
[See image.](#rn-aws-force-delete-button)
To learn more, see [Deleting AWS Deception Settings](/deception/deleting-aws-deception-settings).
[]
![A screenshot highlighting the force Delete option for Azure Cloud Deception](/sites/default/files/downloads/deception/release-notes/release-upgrade-summary-2024/zscaler-deception-force-delete-azure.png)
[]
![AWS Force Delete Option](/sites/default/files/downloads/deception/deceive/landmine-decoys/about-landmine-decoys/zscaler-deception-force-delete-aws-new.png)

### Feature Available
#### New Datasets
The following datasets for different application vulnerabilities were added:
| Application | CVE ID | Description |
| ----------- | ------ | ----------- |
| CData API Server | CVE-2024-31848 | Path Traversal vulnerability in the Java version of CData API Server up to version 23.4.8844 while running with the embedded Jetty server. The vulnerability could be exploited by any unauthenticated remote attacker to gain complete administrative access to the application. |
| GitLab Server | CVE-2023-7028 | Account Takeover vulnerability in GitLab Server Community Edition and Enterprise Edition affecting all versions from 16.1 to 16.1.6, 16.2 to 16.2.9, 16.3 to 16.3.7, 16.4 to 16.4.5, 16.5 to 16.5.6, 16.6 to 16.6.4, and 16.7 to 16.7.2. By exploiting this vulnerability, an attacker can take over any GitLab account using the password reset feature, as tokens and password reset links could be delivered to an unverified email address without authentication. |
| ServiceNow | CVE-2024-4879, CVE-2024-5178, and CVE-2024-5217 | A vulnerability chain containing improper input validation and unauthenticated remote code execution vulnerabilities in the Vancouver and Washington DC Now Platform releases. CVE-2024-4879 involves a Jelly Template Injection flaw in ServiceNow UI Macros, and CVE-2024-5178 relates to an authorization bypass. The combined exploitation of these vulnerabilities poses a high security risk with a CVSS score up to 9.8. |
| Check Point Quantum Gateway | CVE-2024-24919 | Information Disclosure vulnerability that can allow an attacker to access certain information on internet-connected gateways which have been configured with IPSec VPN, remote access VPN, or mobile access software blade. |
| Atlassian Confluence Server and Data Center | CVE-2024-21683 | Remote Code Execution vulnerability was introduced in version 5.2 of Confluence Server and Data Center. This vulnerability has a CVSS Score of 7.2; allows an authenticated attacker to execute arbitrary code which has a high impact on confidentiality, integrity, and availability; and requires no user interaction. |
| Zyxel NAS326 | Not applicable | Network Access Storage solution from Zyxel. |
| Atlassian Jira | Not applicable | A comprehensive tool for tracking bugs, issues, and agile project management from Atlassian. |
| GitHub Enterprise | Not applicable | A collaborative software development and version control solution tailored for enterprises and businesses from GitHub. |
To learn more, see [About Vulnerable Application Datasets (CVE Datasets)](/deception/about-vulnerable-application-datasets-cve-datasets).

### Feature Available
#### New ThreatParse Rules
The following ThreatParse Rules that detect exploits of different application vulnerabilities were added:
| Application | CVE ID | Description |
| ----------- | ------ | ----------- |
| CData API Server | CVE-2024-31848 | Path Traversal vulnerability in the Java version of CData API Server up to version 23.4.8844 while running with the embedded Jetty server. The vulnerability could be exploited by any unauthenticated remote attacker to gain complete administrative access to the application. |
| GitLab Server | CVE-2023-7028 | Account Takeover vulnerability in GitLab Server Community Edition and Enterprise Edition affecting all versions from 16.1 to 16.1.6, 16.2 to 16.2.9, 16.3 to 16.3.7, 16.4 to 16.4.5, 16.5 to 16.5.6, 16.6 to 16.6.4, and 16.7 to 16.7.2. By exploiting this vulnerability, an attacker can take over any GitLab account using the password reset feature, as tokens and password reset links could be delivered to an unverified email address without authentication. |
| PHP-CGI | CVE-2024-4577 | Argument Injection vulnerability in PHP that allows any adversary to remotely execute malicious commands on any server hosting PHP systems. The vulnerability is exploited through the PHP-CGI script engine, even if PHP is not configured in CGI mode, and can be exploited in all versions of PHP for Windows. |
| ServiceNow | CVE-2024-4879, CVE-2024-5178, and CVE-2024-5217 | A vulnerability chain containing improper input validation and unauthenticated remote code execution vulnerabilities in the Vancouver and Washington DC Now Platform releases. CVE-2024-4879 involves a Jelly Template Injection flaw in ServiceNow UI Macros, and CVE-2024-5178 relates to an authorization bypass. The combined exploitation of these vulnerabilities poses a high security risk with a CVSS score up to 9.8. |
| Check Point Quantum Gateway | CVE-2024-24919 | Information Disclosure vulnerability that can allow an attacker to access certain information on internet-connected gateways which have been configured with IPSec VPN, remote access VPN, or mobile access software blade. |
| Atlassian Confluence Server and Data Center | CVE-2024-21683 | Remote Code Execution vulnerability was introduced in version 5.2 of Confluence Server and Data Center. This vulnerability has a CVSS Score of 7.2; allows an authenticated attacker to execute arbitrary code which has a high impact on confidentiality, integrity, and availability; and requires no user interaction. |
To learn more, see [About ThreatParse Rules](/deception/about-threatparse-rules).

### Feature Available
#### OS Upgrade on Decoy Connectors
The operating system on Decoy Connectors was upgraded to FreeBSD 14.1.

## June 05, 2024
### Feature Available
#### Dedicated User Profiles for Deploying Chrome Lures
For deploying browser lures in Chrome browsers, a new user profile is created instead of using the default user profile. The new profile is maintained as a hidden profile and exists alongside the default user profile. The browser lures in the Chrome browser are no longer visible from the default user profile.
To learn more, see [Configuring the Browser Lures Module](/deception/v4_23/configuring-browser-lures-module).

### Feature Available
#### New Datasets
The following datasets for different application vulnerabilities were added:
| Application | CVE ID | Vulnerability Description |
| ----------- | ------ | ------------------------- |
| Adobe ColdFusion | CVE-2024-20767 | Improper Access Control vulnerability in certain versions of ColdFusion, including 2023.6, 2021.12, and earlier. This vulnerability could be exploited by an attacker without any user interaction to read sensitive files on the system and perform unauthorized file system write operations. |
| JetBrains TeamCity | CVE-2024-27199 | Authentication Bypass vulnerability in JetBrains TeamCity version 2023.11.4 or earlier that allows for path traversal and thereby enables the attacker to perform a limited set of administrative actions. This vulnerability could be exploited by an attacker to access and manipulate files and perform certain administrative tasks beyond their authorized privileges. |
| pyLoad | CVE-2024-21644 | Configuration File Disclosure vulnerability in pyLoad that allows any unauthenticated user to access a specific URL and expose the Flask configuration, including the SECRET_KEY variable. The SECRET_KEY is a critical component used for cryptographic operations and should remain confidential. |
| JetBrains TeamCity | CVE-2024-27198 | Authentication Bypass vulnerability in JetBrains TeamCity version 2023.11.4 or earlier that allows unauthorized users to perform administrative actions. This vulnerability could allow attackers to gain access to administrative functionalities without providing proper authentication credentials. |
| Cisco IOS XE | CVE-2023-20198 | Privilege Escalation vulnerability that allows an attacker to gain initial access and then elevate their privilege and create a local user. Subsequently, the attacker exploits another web UI component, leveraging the new local user to elevate privilege to root and write an implant to the file system. |
To learn more, see [About Vulnerable Application Datasets (CVE Datasets)](/deception/about-vulnerable-application-datasets-cve-datasets).

### Feature Available
#### New ThreatParse Rules
The following ThreatParse Rules that detect exploits of different application vulnerabilities were added:
| Application | CVE ID | Vulnerability Description |
| ----------- | ------ | ------------------------- |
| Adobe ColdFusion | CVE-2024-20767 | Improper Access Control vulnerability in certain versions of ColdFusion, including 2023.6, 2021.12, and earlier. This vulnerability could be exploited by an attacker without any user interaction to read sensitive files on the system and perform unauthorized file system write operations. |
| Metabase | CVE-2023-38646 | Pre-Authentication Remote Code Execution vulnerability in Metabase Open Source version 0.46.6.6 or earlier and Metabase Enterprise version 1.46.6.1 or earlier that allows attackers to execute arbitrary commands on the server with the same privileges as the server itself. This vulnerability can be exploited without requiring authentication. |
| pyLoad | CVE-2024-21645 | Log Injection vulnerability in pyLoad that allows any unauthenticated actor to inject arbitrary messages into the logs collected by pyLoad. This vulnerability posed a risk as the forged or corrupted log files could be utilized to conceal an attacker's activities or falsely implicate another party. |
| JetBrains TeamCity | CVE-2024-27198 | Authentication Bypass vulnerability in JetBrains TeamCity version 2023.11.4 or earlier that allows unauthorized users to perform administrative actions. This vulnerability could allow attackers to gain access to administrative functionalities without providing proper authentication credentials. |
| JetBrains TeamCity | CVE-2024-27199 | Authentication Bypass vulnerability in JetBrains TeamCity version 2023.11.4 or earlier that allows for path traversal and thereby enables the attacker to perform a limited set of administrative actions. This vulnerability could be exploited by an attacker to access and manipulate files and perform certain administrative tasks beyond their authorized privileges. |
| pyLoad | CVE-2024-21644 | Configuration File Disclosure vulnerability in pyLoad that allows any unauthenticated user to access a specific URL and expose the Flask configuration, including the SECRET_KEY variable. The SECRET_KEY is a critical component used for cryptographic operations and should remain confidential. |
| Cisco IOS XE | CVE-2023-20198 | Privilege Escalation vulnerability that allows an attacker to gain initial access and then elevate their privilege and create a local user. Subsequently, the attacker exploits another web UI component, leveraging the new local user to elevate privilege to root and write an implant to the file system. |
| D-Link Network Attached Storage | CVE-2024-3273 | Remote Code Execution vulnerability in D-Link DNS-320L, DNS-325, DNS-327L, and DNS-340L up to 20240403 that affected an unknown function of the /cgi-bin/nas_sharing.cgi file in the HTTP GET Request Handler component. The manipulation of the argument system leads to command injection. This vulnerability allows attackers to launch the attack remotely. |
| IBM Operational Decision Manager | CVE-2024-22320 | Java Deserialization vulnerability in IBM Operational Decision Manager 8.10.3, 8.10.4, 8.10.5.1, 8.11, 8.11.0.1, and 8.12.0.1 that allows a remote authenticated attacker to execute arbitrary code on the system. By sending specially crafted requests, an attacker could exploit this vulnerability to execute arbitrary code in the context of SYSTEM. |
| Apache Airflow | CVE-2022-24288 | OS Command Injection vulnerability in Apache Airflow version 2.2.4 or earlier due to some Directed Acyclic Graphs that could not properly sanitize user-provider parameters, making them susceptible to command injection from the web UI. |
| WordPress RSVP | CVE-2022-1054 | Missing Authorization vulnerability that reveals sensitive information such as first name, last name, and email address of users registered for events. |
| Sophos Firewall | CVE-2022-1040 | Authentication Bypass vulnerability in Sophos Firewall version 18.5 MR3 or earlier that allows a remote attacker to execute code in the User Portal and Webadmin. |
| Atlassian Jira | CVE-2022-0540 | Authentication Bypass vulnerability in Jira Seraph that allows an unauthenticated attacker to remotely send specially created HTTP requests to Jira Server and Data Center (versions 8.13.18 or earlier, 8.14.0 to 8.20.6, and 8.21.0 to 8.22.0) and Jira Service Management Server and Data Center (versions 4.13.18 or earlier, 4.140 to 4.20.6, and 4.21.0 to 4.22.0). |
| Microweber | CVE-2022-0281 | Information Disclosure vulnerability in Microweber that allows exposure of sensitive information to an unauthorized actor in Packagist microweber/microweber prior to 1.2.11. |
| D-Link D-View | CVE-2023-5074 | Authentication Bypass vulnerability in D-Link D-View 8 v2.0.1.28 due to the use of a static key to protect a JWT token used in user authentication. |
| WordPress WPQA | CVE-2022-1598 | Improper Access Control vulnerability in WordPress WPQA plugin versions prior to 5.5 due to lack of authentication in a REST API endpoint. An attacker can potentially discover private questions sent between users on the site. |
To learn more, see [About ThreatParse Rules](/deception/about-threatparse-rules).

### Feature Available
#### Proxy Awareness in Standalone Landmine Agents for Windows
Standalone landmine agents for Windows include support for proxy awareness. This functionality allows the agents to automatically detect and apply the proxy configurations if they are already available in the system.
To learn more, see [Installing a Landmine Agent on Windows](/deception/v4_23/installing-landmine-agent-windows)[.]

## April 17, 2024
### Feature Available
#### Containment Integration for Identity Threat Protection with Okta AI
You can integrate Zscaler Deception with Okta to push user risk scores by leveraging the Shared Signals Framework (SSF). With this integration, Deception pushes user risk scores to Okta for Zscaler Client Connector users based on the events generated when users interact with decoys. Based on the risk score and Okta policies, Okta can end the user’s sessions, prompt a Multi-Factor Authentication (MFA) challenge, or invoke a workflow to restore your organization's security posture.
[See image.](#zd-rn-okta-ssf)
To learn more, see [Containment Configuration Guide for Identity Threat Protection with Okta AI](/deception/containment-configuration-guide-identity-threat-protection-okta-ai).
[]
![zscaler-deception-okta-base-url.png](/sites/default/files/downloads/deception/release-notes/release-upgrade-summary-2024/zscaler-deception-okta-base-url.png)

### Feature Available
#### New Datasets
The following new datasets for different application vulnerabilities were added:
| Application | CVE ID | Description |
| ----------- | ------ | ----------- |
| Ivanti Connect Secure | CVE-2024-22024 | XML External Entity (XXE) vulnerability in the SAML component of Ivanti Connect Secure (versions 9.x and 22.x). This vulnerability allows malicious actors to exploit the system and gain unauthorized access to restricted resources. By leveraging the XXE vulnerability, attackers can bypass authentication mechanisms and retrieve sensitive information or perform unauthorized actions within the affected systems. |
| Jenkins | CVE-2024-23897 | Jenkins versions 2.441 and earlier, as well as LTS versions 2.426.2 and earlier, contain a security vulnerability related to the Command Line Interface (CLI) command parser. This vulnerability allows unauthenticated attackers to read arbitrary files on the file system of the Jenkins controller. The vulnerability stems from a feature in the CLI command parser that replaces a specific pattern: an '@' character followed by a file path in an argument, with the contents of the referenced file. Due to the lack of proper authentication checks, an adversary can exploit this feature to retrieve sensitive information from any file accessible to the Jenkins controller. |
| Atlassian Confluence | CVE-2023-22527 | Template Injection vulnerability in Atlassian's Confluence Server and Data Center that enables unauthenticated attackers to inject OGNL (Object-Graph Navigation Language) expressions. Exploiting this vulnerability grants adversaries the ability to execute arbitrary code, including system commands, which can lead to the compromise of affected Confluence instances. The flaw allows attackers to manipulate templates within Confluence, injecting malicious OGNL expressions that are then executed by the application. |
| Citrix ShareFile | CVE-2023-24489 | Improper Access Control vulnerability in the customer-managed ShareFile storage zones controller that enables unauthenticated attackers to compromise the customer-managed ShareFile storage. As a result, sensitive data stored within the affected storage zones can be exfiltrated or tampered. The vulnerability arises from a lack of proper access controls, allowing unauthorized individuals to gain remote access to the customer-managed ShareFile storage. After access is obtained, attackers can manipulate or steal data, potentially leading to unauthorized disclosure, data breaches, or other malicious activities. |
| Adobe ColdFusion | CVE-2023-26360 | Improper Access Control vulnerability that allows adversaries to drop malware onto a system using HTTP POST commands. By exploiting this vulnerability, attackers can bypass proper access controls and execute arbitrary code remotely. This is achieved through a request containing an injected cfexecute tag, enabling the adversaries to compile and save a malicious file on the targeted system. The vulnerability arises due to inadequate access control mechanisms, allowing unauthorized individuals to send HTTP POST commands with malicious intent. By injecting the cfexecute tag into the request, attackers can execute arbitrary commands and potentially drop malware onto the compromised system. This can lead to unauthorized access, data theft, system compromise, and other malicious activities. |
To learn more, see [About Vulnerable Application Datasets (CVE Datasets)](/deception/about-vulnerable-application-datasets-cve-datasets).

### Feature Available
#### New ThreatParse Rules
The following new ThreatParse Rules that detect exploits of different application vulnerabilities were added:
| Application | CVE ID | Description |
| ----------- | ------ | ----------- |
| Ivanti Connect Secure | CVE-2024-22024 | XML External Entity (XXE) vulnerability in the SAML component of Ivanti Connect Secure (versions 9.x and 22.x). This vulnerability allows malicious actors to exploit the system and gain unauthorized access to restricted resources. By leveraging the XXE vulnerability, attackers can bypass authentication mechanisms and retrieve sensitive information or perform unauthorized actions within the affected systems. |
| Jenkins | CVE-2024-23897 | Jenkins versions 2.441 and earlier, as well as LTS versions 2.426.2 and earlier, contain a security vulnerability related to the Command Line Interface (CLI) command parser. This vulnerability allows unauthenticated attackers to read arbitrary files on the file system of the Jenkins controller. The vulnerability stems from a feature in the CLI command parser that replaces a specific pattern: an '@' character followed by a file path in an argument, with the contents of the referenced file. Due to the lack of proper authentication checks, an adversary can exploit this feature to retrieve sensitive information from any file accessible to the Jenkins controller. |
| Atlassian Confluence | CVE-2023-22527 | Template Injection vulnerability in Atlassian's Confluence Server and Data Center that enables unauthenticated attackers to inject OGNL (Object-Graph Navigation Language) expressions. Exploiting this vulnerability grants adversaries the ability to execute arbitrary code, including system commands, which can lead to the compromise of affected Confluence instances. The flaw allows attackers to manipulate templates within Confluence, injecting malicious OGNL expressions that are then executed by the application. |
| Citrix ShareFile | CVE-2023-24489 | Improper Access Control vulnerability in the customer-managed ShareFile storage zones controller that enables unauthenticated attackers to compromise the customer-managed ShareFile storage. As a result, sensitive data stored within the affected storage zones can be exfiltrated or tampered. The vulnerability arises from a lack of proper access controls, allowing unauthorized individuals to gain remote access to the customer-managed ShareFile storage. After access is obtained, attackers can manipulate or steal data, potentially leading to unauthorized disclosure, data breaches, or other malicious activities. |
| Adobe ColdFusion | CVE-2023-26360 | Improper Access Control vulnerability that allows adversaries to drop malware onto a system using HTTP POST commands. By exploiting this vulnerability, attackers can bypass proper access controls and execute arbitrary code remotely. This is achieved through a request containing an injected cfexecute tag, enabling the adversaries to compile and save a malicious file on the targeted system. The vulnerability arises due to inadequate access control mechanisms, allowing unauthorized individuals to send HTTP POST commands with malicious intent. By injecting the cfexecute tag into the request, attackers can execute arbitrary commands and potentially drop malware onto the compromised system. This can lead to unauthorized access, data theft, system compromise, and other malicious activities. |
| SysAid | CVE-2023-47246 | Path Traversal vulnerability leading to code execution after an attacker writes a file to the Tomcat webroot using this exploit. This vulnerability allows an attacker to write a file to the Tomcat webroot directory using a specific exploit. After the file is successfully written, the attacker can execute arbitrary code on the affected system. The vulnerability occurs due to insufficient input validation, allowing attackers to manipulate file paths and access files outside of the intended directory. By exploiting this flaw, an attacker can traverse the directory structure and write a malicious file to the Tomcat webroot. Subsequently, the attacker can execute arbitrary code, potentially leading to unauthorized access, data compromise, and other malicious activities. |
To learn more, see [About ThreatParse Rules](/deception/about-threatparse-rules).

### Feature Available
#### Removal of Phone and Text Message Notifications
Zscaler Deception no longer supports phone and text message notifications. As a result, the following changes were made across the Zscaler Deception Admin Portal:
-
Under Orchestrate > Rules, the Phone and SMS notification options were removed from the Rule Details window.
[See image.](#zd-notify-rule)
To learn more, see [Creating an Orchestration Rule](/deception/creating-orchestration-rule).
-
Under Orchestrate > Event Templates, the phone and text message notification template options were removed.
[See image.](#deception-rel-notes-event-templates)
To learn more, see [Customizing Event Notification Templates](/deception/customizing-event-notification-templates).
-
Under Settings > Users, the phone field was removed from the User Details window.
[See image.](#deception-rel-notes-add-user-details)
To learn more, see [Adding a User](/deception/adding-user).
-
Under Account Settings > Profile, the phone field was removed from the Edit Profile section.
[See image.](#deception-rel-notes-edit-your-profile)
To learn more, see [Editing the User Profile](/deception/editing-user-profile).
[]
![A screenshot capturing the Notify section in Orchestration rules](/sites/default/files/downloads/deception/release-notes/release-upgrade-summary-2024/zscaler-deception-email-rule.png)
[]![Customize event templates](/sites/default/files/downloads/deception/release-notes/release-upgrade-summary-2024/release-notes-zscaler-deception-event-templates.png)
[]![Add a user](/sites/default/files/downloads/deception/release-notes/release-upgrade-summary-2024/release-notes-zscaler-deception-user-details-2.png)
[]![Edit your user profile](/sites/default/files/downloads/deception/release-notes/release-upgrade-summary-2024/release-notes-zscaler-deception-edit-user-profile-1.png)

### Feature Available
#### User Interface Changes and Enhancements
On the Agent Update Groups page in the Zscaler Deception Admin Portal (Settings > Endpoint Settings > Agent Update Groups), the Agent Group window was renamed to Agent Update Group Details.
[See image.](#zd-rn-ui-lable-agent-group)
To learn more, see [About Agent Update Groups](/deception/about-agent-update-groups).
[]
![A screenshot highlighting the UI label Change in Agent Update Group Page](/sites/default/files/downloads/deception/release-notes/release-upgrade-summary-2024/zd-rn-agent-update-groups.png)

## February 14, 2024
### Feature Available
#### Configure Safe Processes Using Regular Expressions
You can add safe processes to Zscaler Deception using regular expressions. This allows you to configure a single safe process that accommodates multiple different processes by matching a specific pattern of strings in the process names.
[See image.](#zd-rn-regex-safe-processes)
To learn more, see [Configuring a Safe Process](/deception/configuring-safe-process).
[]
![zscaler-deception-safe-processes.jpg](/sites/default/files/downloads/deception/release-notes/release-upgrade-summary-2024/zscaler-deception-safe-processes.jpg)

### Feature Available
#### New Datasets
The following new datasets for different application vulnerabilities were added:
| Application | CVE ID | Vulnerability Description |
| ----------- | ------ | ------------------------- |
| JetBrains TeamCity < 2023.05.4 | CVE-2023-42793 | Authentication Bypass vulnerability that allows unauthenticated remote code execution against a vulnerable JetBrains TeamCity servers. All versions of TeamCity prior to version 2023.05.4 are vulnerable to this issue. |
| SysAid | CVE-2023-47246 | Path Traversal vulnerability leading to code execution after an attacker writes a file to the Tomcat webroot using this exploit. |
| D-Link D-View | CVE-2023-5074 | Hard-coded JWT Authentication Bypass vulnerability in D-Link D-View 8 v2.0.1.28. |
| Ivanti Connect Secure (Authentication Bypass) | CVE-2023-46805 | Authentication Bypass vulnerability in Ivanti Connect Secure (9.x and 22.x) which allows attackers to access restricted resources by bypassing control checks. Additionally, when combined with another exploit (CVE-2024-21887), attackers can achieve remote code execution. |
| Ivanti Connect Secure (Server-Side Request Forgery) | CVE-2024-21893 | Server-Side Request Forgery (SSRF) vulnerability in Ivanti Connect Secure (9.x and 22.x) which allows attackers to access restricted resources without authentication. It can also be combined with another vulnerability (CVE-2024-21887) to gain remote code execution (RCE) capabilities. |
| Ivanti Connect Secure (Command Injection) | CVE-2024-21887 | Command Injection vulnerability in the web components of Ivanti Connect Secure (9.x and 22.x) which allows an authenticated administrator to send specially crafted requests and execute arbitrary commands on the targeted appliance. Attackers exploiting this vulnerability can gain unauthorized access and potentially manipulate the system beyond its intended functionality. |
To learn more, see [About Vulnerable Application Datasets (CVE Datasets)](/deception/about-vulnerable-application-datasets-cve-datasets).

### Feature Available
#### New ThreatParse Rules
The following new ThreatParse Rules that detect exploits of different application vulnerabilities were added:
| Application | CVE ID | Vulnerability Description |
| ----------- | ------ | ------------------------- |
| Ivanti Connect Secure (Authentication Bypass) | CVE-2023-46805 | Authentication Bypass vulnerability in Ivanti Connect Secure (9.x and 22.x) which allows attackers to access restricted resources by bypassing control checks. Additionally, when combined with another exploit (CVE-2024-21887), attackers can achieve remote code execution. |
| Ivanti Connect Secure (Server-Side Request Forgery) | CVE-2024-21893 | Server-Side Request Forgery (SSRF) vulnerability in Ivanti Connect Secure (9.x and 22.x) which allows attackers to access restricted resources without authentication. It can also be combined with another vulnerability (CVE-2024-21887) to gain remote code execution (RCE) capabilities. |
| Ivanti Connect Secure (Command Injection) | CVE-2024-21887 | Command Injection vulnerability in the web components of Ivanti Connect Secure (9.x and 22.x) which allows an authenticated administrator to send specially crafted requests and execute arbitrary commands on the targeted appliance. Attackers exploiting this vulnerability can gain unauthorized access and potentially manipulate the system beyond its intended functionality. |
To learn more, see [About ThreatParse Rules](/deception/about-threatparse-rules).

### Feature Available
#### Option to Force Apply Lures for Edge Browsers
In the landmine policy configuration window, a Force Apply toggle was added in the Browser Lures module for Microsoft Edge lures. This toggle can enable or disable the Startup boost option in the Edge browser settings.
- If Force Apply is enabled, the Startup boost option in the Edge browser settings gets disabled.
- If Force Apply is disabled, the Startup boost option in the Edge browser settings gets enabled.
When configuring lures for Microsoft Edge browser, you can select the Force Apply option to disable the Startup boost option in the browser settings. When the Startup boost option is enabled in the browser settings, the browser runs in the background with minimal processes to improve performance. However, this can prevent landmine policies from being applied to the browser. By default, the Force Apply option is disabled.
[See image.](#zd-rn-edge)
To learn more, see [Configuring the Browser Lures Module](/deception/configuring-browser-lures-module).
[]![A screenshot capturing the Force Apply option for lures in Edge browsers ](/sites/default/files/downloads/deception/release-notes/release-upgrade-summary-2024/zd-rn-edge-forceapply.png)

### Feature Available
#### User Interface Changes and Enhancements
The following user interface changes and enhancements were made to the Zscaler Deception Admin Portal.
-
Under Settings, a new section "Endpoint Settings" was added, and certain options from Deceive > Landmine were moved to this new section with some UI label changes. The following table compares the UI changes before and after this update:
| Old | New |
| --- | --- |
| Deceive > Landmine > Agents | Settings > Endpoint Settings > Agents |
| Deceive > Landmine > Settings | Settings > Endpoint Settings > Agent Configuration |
| Deceive > Landmine > Update phase groups | Settings > Endpoint Settings > Agent Update Groups |
| Deceive > Landmine > Safe Processes | Settings > Endpoint Settings > Safe Processes |
[See image.](#endpoint-settings-menu)
To learn more, see [About Settings](/deception/about-settings).
-
On the Agents page (Settings > Endpoint Settings > Agents), a Show all agents toggle was added under the Actions drop-down menu. This toggle allows you to show or hide inactive agents from the Agents table. As a result, this toggle affects the list of options shown in the Version drop-down menu in the Agents table.
[See image.](#show-all-agents)
To learn more, see [About Landmine Agents and Agentless](/deception/about-landmine-agent-agentless).
- Under Deceive > Landmine > Policy, the ITDR-Active Directory module was removed from the landmine policy configuration window.
[]
![A screenshot highlighting the Endpoint Settings menu](/sites/default/files/downloads/deception/release-notes/release-upgrade-summary-2024/zd-rn-endpoint-setting-menu-new.jpg)
[]
![A screenshot highlighting the Show all agents option](/sites/default/files/downloads/deception/release-notes/release-upgrade-summary-2024/zd-rn-show-all-agents.png)

### Feature Available
#### ZPA App Connector Dashboard in Deception
In the Zscaler Deception Admin Portal, ZPA App Connectors hosted by Zscaler are used to deploy [Zero Trust Network decoys](/deception/creating-zero-trust-network-decoy) in the Zero Trust Exchange (ZTE) environment. The App Connectors create a secure interface between the Decoy Connector and the ZTE via Zscaler Private Access (ZPA).
You can view the App Connector details on the ZPA App Connectors page (Settings > Topology > ZPA App Connector). You can also view and download the update and debug logs of the App Connector.
[See image.](#deception-release-notes-zpa-app-connector)
To learn more, see [About ZPA App Connectors in Deception](/deception/about-zpa-app-connector-deception).
[]![View ZPA App Connectors Page](/sites/default/files/downloads/deception/release-notes/release-upgrade-summary-2024/release-notes-zscaler-deception-zpa-app-connector-page.png)
