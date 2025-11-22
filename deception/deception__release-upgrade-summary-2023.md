# Release Upgrade Summary (2023)
Source: https://help.zscaler.com/deception/release-upgrade-summary-2023

This article provides a summary of all new features and enhancements for Zscaler Deception.
The illusionblack.com cloud represents all clouds, and updates to specific clouds might take a few weeks to deploy. Some functions are not available until deployment completes.

**Clouds:** illusionblack.com
The following service updates were deployed to illusionblack.com on

## December 22, 2023
### Feature Available
#### New Datasets
The following new datasets for different application vulnerabilities were added:
| Application | CVE ID | Vulnerability Description |
| ----------- | ------ | ------------------------- |
| Progress WS_FTP | CVE-2023-40044 | Remote Code Execution vulnerability caused by .NET deserialization flaw in the Ad Hoc Transfer module. The adversaries leverage a vulnerability associated with the improper handling of file uploads within the HTTP module. |
| Atlassian Confluence | CVE-2023-22518 | Improper Authorization vulnerability that allows unauthenticated attackers with network access to the Confluence instance to restore the database of the Confluence instance and eventually execute arbitrary system commands. |
To learn more, see [About Vulnerable Application Datasets (CVE Datasets)](/deception/about-vulnerable-application-datasets-cve-datasets).

### Feature Available
#### New ThreatParse Rules
The following new ThreatParse Rules that detect exploits of different application vulnerabilities were added:
| Application | CVE ID | Vulnerability Description |
| ----------- | ------ | ------------------------- |
| Sitecore | CVE-2023-35813 | Remote Code Execution vulnerability that allows unauthenticated adversaries to execute code through the exploitation of the ASP.NET TemplateParser, which is crucial in ASP.NET Web Forms for parsing various source files. |
| Progress WS_FTP | CVE-2023-40044 | Remote Code Execution vulnerability caused by .NET deserialization flaw in the Ad Hoc Transfer module. The adversaries leverage a vulnerability associated with the improper handling of file uploads within the HTTP module. |
| SonicWall GMS | CVE-2023-34124 | A web service authentication bypass vulnerability that potentially allows unauthenticated adversaries with network access to execute remote commands. |
| IBM Aspera Faspex | CVE-2022-47986 | Remote Code Execution vulnerability due to a YAML deserialization flaw. This can allow an attacker to send a specially crafted obsolete API call and thereby execute arbitrary code, obtain sensitive data, and execute other unauthorized operations. |
| Adobe ColdFusion | CVE-2023-38205 | Access Control Bypass vulnerability in Adobe ColdFusion, which allows a remote attacker to bypass the ColdFusion mechanisms that restrict unauthenticated external access to the ColdFusion Administrator. |
| Adobe ColdFusion | CVE-2023-29300 | Deserialization of Untrusted Data vulnerability in Adobe ColdFusion that could result in arbitrary code execution without any user interaction. |
| PaperCut | CVE-2023-27350 | Remote Code Execution vulnerability in PaperCut NG that allows a remote unauthenticated user to bypass authentication and execute arbitrary code in the context of SYSTEM. |
| Atlassian Confluence | CVE-2023-22515 | Broken Access Control vulnerability in the Atlassian Confluence Data Center and Server that allows an attacker to create unauthorized Confluence administrator accounts and access Confluence instances. |
| Atlassian Confluence | CVE-2023-22518 | Improper Authorization vulnerability that allows unauthenticated attackers with network access to the Confluence instance to restore the database of the Confluence instance and eventually execute arbitrary system commands. |
To learn more, see [About ThreatParse Rules](/deception/about-threatparse-rules).

## November 02, 2023
### Feature Available
#### Changes to Event Score Calculation
The event score for events that match multiple ThreatParse rules is now calculated by computing the highest score among the matching rules, instead of adding scores of all matching ThreatParse rules. For each event, the score is displayed in the Event Details pane, which can be accessed by clicking an event from the Event Logs page (Investigate > View Extended Details > Event Logs).
[See image.](#zd-rn-event-score)
To learn more, see [About Event Logs](/deception/about-event-logs).
[]![A screenshot capturing the Events Details pane with the score field highlighted](/sites/default/files/downloads/deception/release-notes/release-upgrade-summary-2023/zd-rn-event-score.jpg)

### Feature Available
#### Containment Synchronization with CrowdStrike
Zscaler Deception runs a scheduler every hour to update the list of CrowdStrike-contained endpoints in the Zscaler Deception Admin Portal. This ensures the removal of contained devices from the Zscaler Posture Control Admin Portal if the containment is lifted for those devices manually from the CrowdStrike Falcon Insight Platform.
To learn more, see [Viewing the Contained Attacker Details](/deception/viewing-contained-attacker-details).

### Feature Available
#### Delete Cloud Deception Settings
Options to delete settings for Cloud Deception with Microsoft Azure (Deceive > Cloud Deception > Azure > Settings) and Amazon Web Services (Deceive > Cloud Deception > AWS> Settings) are supported.
[See image.](#zd-azure-aws-deception-settings-delete-option)
To learn more, see [Deleting Azure Deception Settings](/deception/deleting-azure-deception-settings) and [Deleting AWS Deception Settings](/deception/deleting-aws-deception-settings).
[]![A screenshot highlighting the options to delete Azure and AWS deception settings](/sites/default/files/downloads/deception/release-notes/release-upgrade-summary-2023/zd-rn-azure-aws-delete-settings_1.png)

### Feature Available
#### Landmine Enhancements and Licensing Changes
- For the purpose of licensing, the total number of landmine decoys consumed from the allocated landmine license quota is computed as a sum of:
- Zscaler Client Connector Landmines: This counts the number of unique Zscaler Client Connector users across all landmines in the active state.
- Standalone Landmines: This counts the number of unique hostnames across all landmines in the active state.
- Agentless Landmines: This counts the number of unique hostnames across all landmines in the active state.
Landmine agents (ZCC Integrated and Standalone) whose last check-in time is older than 7 days are considered inactive and are removed from the Zscaler Deception Admin Portal. The landmine agentless is always active.
-
The following user interface changes were made to the Landmine Agents page (Deceive > Landmine > Agents):
- The System User Name column that shows the list of users that are logged in to the system was added.
- The Client Connector Users** **column that shows the list of users that are logged in to Zscaler Client Connector was renamed to Client Connector User.
[See image.](#zd-rn-column-name-changes)
- The Agentless column was replaced with the Type column, which allows you to filter the table based on the type of landmine agent (ZCC Integrated, Standalone, and Agentless).
[See image.](#zd-rn-landmine-type-column)
- The option to filter the values in the drop-down menu based on user input was added to the Version column.
[See image.](#zd-rn-landmine-version-column)
- The option to filter the agent table using a date range was added to the First Seen and the Last Seen columns.
[See image.](#zd-rn-date-range-filter)
[]![A screenshot capturing the UI label changes in the Agent table](/sites/default/files/downloads/deception/release-notes/release-upgrade-summary-2023/zd-rn-ui-label-changes-agents-table.jpg)
[]![A screenshot capturing the Landmine Agent Table with the Type Column highlighted](/sites/default/files/downloads/deception/release-notes/release-upgrade-summary-2023/zd-rn-agents-table-type-column.jpg)
[]![A screenshot capturing the Landmine Agent table with Version Colum drop-down](/sites/default/files/downloads/deception/release-notes/release-upgrade-summary-2023/zd-rn-version-column.jpg)
[]![A screenshot capturing the Landmine Agent table with Calendar Filter](/sites/default/files/downloads/deception/release-notes/release-upgrade-summary-2023/zd-rn-agents-table-seen-columns.jpg)

### Feature Available
#### Tags for AWS Resources
You can add tags to decoys and other resources deployed on the Amazon Web Services (AWS) cloud directly from the Zscaler Deception Admin Portal. Tags allow you to identify and distinguish the resources deployed by Zscaler Deception. The option to add tags is available on the Cloud Deception - AWS page (Deceive > Cloud Deception > AWS > Settings).
[See image.](#zd-rn-tagging-aws)
To learn more, see [Configuring and Managing Tags for AWS Resources](/deception/configuring-and-managing-tags-aws).
[]![A screenshopt captruing the option to add tags to AWS resources](/sites/default/files/downloads/deception/release-notes/release-upgrade-summary-2023/zd-rn-aws-tagging.png)

### Feature Available
#### User Interface Enhancements
The following user interface changes and enhancements were made to the Zscaler Deception Admin Portal:
- On the Threat Intelligence Decoys page (Deceive > Threat Intelligence Decoys), the Internal NAT IP column was removed, and the following new columns were added:
- Type: The type of the decoy application (Static, Dynamic, or High Interaction).
- Public IP: The public IP address assigned to the Threat Intelligence (TI) decoy.
[See image.](#deception-release-notes-ti-table)
To learn more, see [About Threat Intelligence Decoys](/deception/about-threat-intelligence-decoys) and [Creating a Threat Intelligence Decoy](/deception/creating-threat-intelligence-decoy).
- In the Download Deployment Script window for Microsoft Azure (Deceive > Cloud deception > Azure > Download Deployment Script) and Amazon Web Services (Deceive > Cloud deception > AWS > Download Deployment Script), a copy-to-clipboard button was added to both the automated and manual script sections.
[See image.](#zd-rn-copy-script-azure-aws)
- In the Agents table (Deceive > Landmine > Agents), a mouseover tooltip displaying the last date of upload of logs was added to the Download logs icon.
[See image.](#zd-rn-agent-logs)
The Download Logs icon appears only after using the Trigger Logs action. To learn more, see [Downloading Landmine Agent Logs from an Endpoint](/deception/downloading-landmine-agent-logs-endpoint).
[]![A screenshot capturing the Download Deployment Script window for both Azure and AWS](/sites/default/files/downloads/deception/release-notes/release-upgrade-summary-2023/zd-download-script-azure-aws-rn-copy-option.png)
[]![The Threat Intelligence Decoys table](/sites/default/files/downloads/deception/release-notes/release-upgrade-summary-2023/release-notes-zscaler-deception-ti-decoys-type-public-ip-columns-1.png)
[]![A screenshot capturing the mouseover tooltip showing agent log upload date](/sites/default/files/downloads/deception/deceive/landmine-decoys/agents/agent-management/downloading-landmine-agent-logs-endpoint/zd-rn-mousever-agent-log-tooltip.jpg)

## July 27, 2023
### Feature Available
#### Apple Silicon Support for Landmine Agent and Agentless
Landmine Agent and Agentless are supported on Mac computers with Apple Silicon. You can download the installers from the Download Agent drop-down menu under Deceive > Landmine > Agents.
[See image.](#zd-rn-download-installer)
[]![A screenshot capturing the option to download landmine agent and agentless for Apple Silicon computers](/sites/default/files/downloads/deception/deceive/landmine-decoys/agents/landmine-agentless/downloading-landmine-agentless/zscaler-deception-rn-apple-silicon-support.png)

### Feature Available
#### Apply Landmine Policies to Zscaler Client Connector Users
You can configure landmine policies with Zscaler Client Connecter users as its criteria.
[See image.](#zd-rn-user-criteria-landmine)
To learn more, see [Creating a Landmine Policy](/deception/creating-landmine-policy).
[]![A screenshot capturing the Landmine Policy window with user criteria configuration](/sites/default/files/downloads/deception/release-notes/release-upgrade-summary-2023/zscaler-deception-run-user-criteria-landmine-policy.png)

### Feature Available
#### Cloud Deception with Microsoft Azure and AWS
You can integrate Microsoft Azure and Amazon Web Services (AWS) with Zscaler Deception and deploy decoy resources specific to those public cloud platforms. You can deploy decoys to detect malicious activities originating from adversaries within or outside your organization, depending on the type and configuration of the decoys.
Cloud Deception with Azure
You can integrate Microsoft Azure with Zscaler Deception and deploy various Azure-specific resources as decoys. The following Azure-specific resources can be configured as decoys from the Zscaler Deception Admin Portal:
- [Users](/deception/creating-user-decoy-azure)
- [Service Principals](/deception/creating-service-principal-decoy-azure)
- [Managed Identities](/deception/creating-managed-identity-decoy-azure)
- [App Services](/deception/creating-app-service-decoy-azure)
- [Storage Account Containers](/deception/creating-storage-account-container-decoy-azure)
- [Storage Account File Shares](/deception/creating-storage-account-file-share-decoy-azure)
- [Key Vaults](/deception/creating-key-vault-decoy-azure)
- [ARM Templates](/deception/creating-arm-template-decoy-azure)
- [Container Registries](/deception/creating-container-registry-decoy-azure)
- [VM Images](/deception/creating-vm-image-decoy-azure)
[See image.](#zd-rn-cd-about-azure)
To learn more, see [About Cloud Deception with Azure](/deception/about-cloud-deception-using-azure) and [Setting Up Cloud Deception with Microsoft Azure](/deception/setting-cloud-deception-microsoft-azure).
Cloud Deception with AWS
You can integrate AWS with Zscaler Deception and deploy various AWS-specific resources as decoys. The following AWS-specific resources can be configured as decoys from the Zscaler Deception Admin Portal:
- [IAM](/deception/creating-iam-decoy-aws)
- [S3](/deception/creating-s3-decoy-aws)
- [RDS](/deception/creating-rds-decoy-aws)
- [ECR](/deception/creating-ecr-decoy-aws)
- [DynamoDB](/deception/creating-dynamo-db-decoy-aws)
- [VM Images](/deception/creating-vm-image-decoy-aws)
[See image.](#zd-rn-cd-aws)
To learn more, see [About Cloud Deception with AWS](/deception/about-cloud-deception-using-aws) and [Setting Up Cloud Deception with AWS](/deception/setting-cloud-deception-aws).
Configuring Lures for Cloud Decoys
You can deploy lures for Azure and AWS decoys on endpoints using the following landmine policies.
- [Cloud Lures](#zd-rn-cd-cloud-lures)
- [Browser Lures](#zd-rn-cd-browser-lures)
- [Session Lures](#zd-rn-cd-session-lures)
- [File Decoys](#zd-rn-cd-file-decoys-lures)
Depending on the type of decoy, you can also configure other lures and detect adversarial behaviors.
To learn more, see [Configuring Lures Using Azure Decoys](/deception/configuring-lures-using-azure-decoys) and [Configuring Lures Using AWS Decoys](/deception/configuring-lures-using-aws-decoys).
Deprecation of Existing AWS Decoys
The existing AWS Decoys feature (Deceive > AWS Decoys) is deprecated and all existing AWS IAM decoys and AWS S3 decoys will no longer work. Customers using these existing AWS decoys should migrate to new Cloud Deception with AWS manually.
[]Cloud lures allow you to configure lures using the following cloud decoys:
- AWS IAM
- Azure File Shares
- Azure Service Principals
- Azure Users
- Azure Storage Explorer
[See image.](#zd-rn-cd-cloud-lures-image)
To learn more, see [Configuring Cloud Lures](/deception/configuring-cloud-lures).
[]Browser lures allow you to configure lures using the following cloud decoys:
- Azure VM Images
- Azure App Services
- AWS S3
- AWS RDS
- AWS ECR
[See image.](#zd-rn-cd-browser-lures-image)
To learn more, see [Configuring Browser Lures](/deception/configuring-browser-lures).
[]Session lures allow you to configure Bash History lures for all Azure and AWS decoys.
[See image.](#zd-rn-cd-session-lures-image)
To learn more, see [Configuring Session Lures](/deception/configuring-session-lures).
[]File decoys allow you to configure lures for all Azure and AWS decoys that have secrets associated with them.
To learn more, see [Configuring File Decoys](/deception/configuring-file-decoys).
[]![A screenshot capturing Azure Cloud Deception Page](/downloads/deception/release-notes/release-upgrade-summary-2023/zscaler-deception-about-azure.png)
[]![A screenshot capturing AWS Cloud Deception Page](/downloads/deception/release-notes/release-upgrade-summary-2023/zscaler-deception-about-aws.png)
[]![A screenshot capturing Cloud Lures window](/downloads/deception/release-notes/release-upgrade-summary-2023/zd-rn-cloud-lures.png)
[]![A screenshot capturing Session Lures window](/downloads/deception/release-notes/release-upgrade-summary-2023/zd-rn-session-lures.png)
[]![A screenshot capturing Browser Lures window](/downloads/deception/release-notes/release-upgrade-summary-2023/zd-rn-browser-lures.png)

### Feature Available
#### Retention Period for Safe Events
Events that are marked as safe are retained for only 7 days. You cannot modify this retention period.
To learn more, see [Taking Action From](/deception/taking-actions-from-dashboard)[ ](/deception/taking-action-from-the-dashboard)[the ](/deception/taking-actions-from-dashboard)[Dashboard](/deception/taking-action-from-dashboard) and [Configuring a Retention Policy](/deception/configuring-retention-policy).

### Feature Available
#### User Interface Enhancements
The following user interface changes and enhancements were made to the Zscaler Deception Admin Portal:
- On the Vulnerable Application Datasets (CVE Datasets) page (Miragemaker > Vulnerable Application Datasets (CVE Datasets)), the Linked Dynamic Applications column that shows the list of all dynamic applications that are configured with the vulnerable application dataset was added.
[See image.](#zd-linked-dynamic-applications)
- On the Dynamic Application Datasets page (Miragemaker > Dynamic Application Datasets), the following columns were added:
- Static Application Datasets: Shows the static application dataset that is associated with the dynamic application dataset.
- Vulnerable Application Datasets: Shows the list of all vulnerable dynamic applications that are associated with the dynamic application dataset.
[See image.](#zd-static-vulnerable-applications)
[]![A screenshot capturing the newly added column in vulnerable application dataset page](/sites/default/files/downloads/deception/release-notes/release-upgrade-summary-2022/zd-rn-linked-dynamic-application.png)
[]![A screenshot capturing new columns in dynamic application datasets page](/sites/default/files/downloads/deception/release-notes/release-upgrade-summary-2022/zd-rn-stattic-and-vulnerable-columns.png)

## May 31, 2023
### Feature Available
#### Expiration Period for Connection Code in Decoy Connectors
The expiration period for the connection code in Decoy Connectors has been changed to 12 hours.
To learn more, see [Adding and Connecting a Decoy Connector to the Zscaler Deception](/deception/adding-connecting-decoy-connector-admin-portal).

### Feature Available
#### Integration with Zscaler Internet Access
Zscaler Deception supports integration with Zscaler Internet Access (ZIA) to contain and isolate Zscaler Client Connector users who interact with landmine decoys by blocking internet access to those users across devices.
[See image.](#zscaler-deception-ZIA-configuration)
To learn more, see [Zscaler Deception and Zscaler Internet Access Deployment Guide](/deception/zscaler-deception-and-zscaler-internet-access-deployment-guide).
[]![Configuring ZIA containment integration](/sites/default/files/downloads/deception/deceive/landmine-decoys/landmine-settings/customizing-landmine-installer/zscaler-deception-ZIA-contianment-configuration.png)

### Feature Available
#### Security Information and Event Management Integration with Sumo Logic
You can integrate Zscaler Deception with the Sumo Logic Security Information and Event Management (SIEM) solution to transmit logs in real time and enhance your security operations workflows.
[See image.](#deception-release-notes-sumo-logic-siem-integration)
To learn more, see [Deception and Sumo Logic Deployment Guide](/deception/deception-and-sumo-logic-deployment-guide).
[] ![Deception and Sumo Logic SIEM integration](/sites/default/files/downloads/deception/release-notes/release-upgrade-summary-2023/release-notes-zscaler-deception-sumo-logic-siem-integration-1.png)

### Feature Available
#### User Interface Enhancements
The following user interface changes and enhancements were made to the Zscaler Deception Admin Portal:
- On the Containment page (Orchestrate > Containment), the Blocked IPs/Hostnames column was renamed to Blocked Identities to reflect the current capabilities of various containment integrations.
[See image.](#zscaler-deception-blocked-identities)
To learn more, see [About Containment Integration](/deception/about-containment-integration).
- The Status column was renamed to Type on the Rules page (Orchestrate > Rules) and the Safe Processes page (Deceive > Landmine > Safe Processes).
[See image.](#zscaler-deception-column-name)
To learn more, see [About Orchestration Rules](/deception/about-orchestration-rules) and [About Safe Processes](/deception/about-safe-processes).
- The Deception Strategy page was moved from Deceive to Miragemaker (Miragemaker > Strategy Builder > Deception Strategy).
[See image.](#deception-release-notes-deception-strategy-navigation)
To learn more, see [About Deception Strategy](/deception/about-deception-strategy).
[]![Screenshot showing the UI change ](/sites/default/files/downloads/deception/deceive/landmine-decoys/landmine-settings/customizing-landmine-installer/zscaler-deception-blocked-identities.png)
[]![A screenshot capturing UI text changes](/sites/default/files/downloads/deception/deceive/landmine-decoys/landmine-settings/customizing-landmine-installer/zscaler-deception-type.png)
[]![Navigate to Deception Strategy](/sites/default/files/downloads/deception/release-notes/release-upgrade-summary-2023/release-notes-zscaler-deception-deception-strategy-miragemaker.png)

### Feature Available
#### Validation for Landmine Agent Service Name
Zscaler Deception validates the user-provided landmine agent service name and prevents users from configuring a name that matches the name of a default service to avoid landmine agent failures.
To learn more, see [Customizing Landmine Installer](/deception/customizing-landmine-installer).

### Feature Available
#### Zscaler Client Connector-Integrated Landmine Deception License Changes
The license calculation has changed for users [deploying endpoint deception with Zscaler Client Connector](/deception/deploying-endpoint-deception-zscaler-client-connector-windows). For Zscaler Client Connector - integrated landmines, the license is calculated per user logged into Zscaler Client Connector. For standalone landmines, licenses are still calculated per system.
To learn more, see [Ranges and Limitations](/deception/ranges-and-limitations).

## March 15, 2023
### Feature Available
#### Create a Zero Trust Network Decoy of a Real or Production Application in ZPA
You can add Zero Trust Network decoys to existing real application segments in Zscaler Private Access (ZPA). The application segments must be on unused ports and have at least one FQDN configured.
Zscaler Deception doesn't allow you to configure an IP address for Zero Trust Network or ZPA decoys. Alerts are generated only for connections to the decoy FQDN.
[See image.](#release-notes-zero-trust-zpa-prod-app)
To learn more, see [Creating a Zero Trust Network Decoy](/deception/creating-zero-trust-network-decoy) and [About ZPA Applications](/zpa/about-applications).
[]![Configure a Zero Trust Network Decoy of a prod app in ZPA](/sites/default/files/downloads/deception/release-notes/release-upgrade-summary-2023/release-notes-zscaler-deception-zero-trust-zpa-prod-app-1.png)

### Feature Available
#### Create and Deploy a Deception Strategy
The Deception Strategy feature enables you to leverage the ready-to-use personalities or tags to quickly configure Internal decoys, Threat Intelligence (TI) decoys, Active Directory (AD) decoys, and Landmine policies on a single page. You can configure realistic-looking decoys that have services, names, or configurations that mimic real assets on your network.
By default, Zscaler Deception provides built-in strategies that cover various business use cases to detect threats. You can create custom strategies for your business needs.
[See image.](#release-notes-deception-strategy)
To learn more, see [About Deception Strategy](/deception/about-deception-strategy) and [Creating a Strategy](/deception/creating-deception-strategy).
After you create strategies, you can deploy them using Internal or Zero Trust Network (ZTN) decoys.
[See image.](#release-notes-deception-deploy-strategy)
To learn more, see [About Deploy Strategy](/deception/about-deploy-strategy) and [Deploying a Strategy](/deception/deploying-strategy).
[]![Configure a Deception strategy](/sites/default/files/downloads/deception/release-notes/release-upgrade-summary-2023/release-notes-zscaler-deception-deception-strategy.png)
[]![Deploy a strategy](/sites/default/files/downloads/deception/release-notes/release-upgrade-summary-2023/release-notes-zscaler-deception-deploy-strategy.png)

### Feature Available
#### CrowdStrike Enhancements
You can configure a response rule to specify actions that the CrowdStrike solution can take when Zscaler Deception detects IOC IP, IOC Hash, and IOA process tree activities on an endpoint.
When IOC and IOA activities are detected, the response rule is triggered and IOCs and IOAs of the attacker's process are forwarded to the CrowdStrike solution with the required action specified in the response rule.
[See image.](#release-notes-deception-crowdstrike-ioc)
To learn more, see [Zscaler Deception and CrowdStrike Deployment Guide](/deception/zscaler-deception-and-crowdstrike-deployment-guide) and [Viewing the Contained Attacker Details](/deception/viewing-contained-attacker-details).
[] ![Configure a response rule for CrowdStrike to detect IOC and IOA activities ](/sites/default/files/downloads/deception/release-notes/release-upgrade-summary-2023/release-notes-zscaler-deception-crowdstrike-ioc-ioa-hash-1.png)

### Feature Available
#### Custom Response Headers for Threat Intelligence Decoys and Web Services On Internal Decoys
Threat Intelligence (TI) decoys and web services on Internal network decoys have custom response headers that you can use to manipulate the HTTP response headers. The response headers are visible in a browser when an adversary accesses a TI or Internal network decoy. Custom headers make the decoy look realistic, so that an adversary continues to interact with the decoy for a longer time.
[See image.](#release-notes-custom-response-headers-ti-decoy)
To learn more, see [Creating a Threat Intelligence Decoy](/deception/creating-threat-intelligence-decoy).
[See image.](#release-notes-custom-response-headers-web-serv)
To learn more, see [Configuring a Web Service on a Network Decoy](/deception/configuring-services-network-decoy#configuring-web-service).
[] ![Custom response headers in TI decoys](/sites/default/files/downloads/deception/release-notes/release-upgrade-summary-2023/release-notes-zscaler-deception-customer-response-headers-ti.png)
[]![Custom response headers in Internal decoy web service](/sites/default/files/downloads/deception/release-notes/release-upgrade-summary-2023/release-notes-zscaler-deception-customer-response-headers-internal-web-ser-decoy.png)

### Feature Available
#### Default Expiration Period for a Response Rule
You can configure the default expiration period (in hours) when configuring the containment integration with the Palo Alto Networks or Fortinet solution. The same expiration period is also applicable to the response rules.
[See image.](#release-notes-deception-palo-alto-default-exp)
To learn more, see [Zscaler Deception and Palo Alto Networks Deployment Guide](/deception/zscaler-deception-and-palo-alto-networks-deployment-guide).
[See image.](#release-notes-deception-fortinet-default-exp)
To learn more, see [Zscaler Deception and Fortinet Deployment Guide](/deception/zscaler-deception-fortinet-deployment-guide).
[] ![Palo Alto Networks containment integration default expiration period](/sites/default/files/downloads/deception/release-notes/release-upgrade-summary-2023/release-notes-zscaler-deception-palo-alto-default-expiration.png)
[]![Fortinet containment integration default expiration period](/sites/default/files/downloads/deception/release-notes/release-upgrade-summary-2023/release-notes-zscaler-deception-fortinet-default-expiration-1.png)

### Feature Available
#### Export the Evidence File Details
On the Investigate page, you can export a list of evidence files that are collected as a CSV or JSON file.
[See image.](#release-notes-deception-export-evidence-csv-json)
To learn more, see [About Evidence File](/deception/about-evidence) and [Exporting Evidence Details](/deception/exporting-evidence-details).
[]![Export evidence files](/sites/default/files/downloads/deception/release-notes/release-upgrade-summary-2023/release-notes-zscaler-deception-download-evidence-files.png)

### Feature Available
#### Safe Processes Enhancements
Zscaler Deception provides internal (built-in) safe processes. You can show or hide these internal safe processes on the Safe Processes page (Deceive > Landmine > Safe Processes).
[See image.](#release-notes-deception-display-internal-safe-process)
To learn more, see [About Safe Processes](/deception/about-safe-processes) and [Configuring a Safe Process](/deception/configuring-safe-process).
[]![Display internal safe processes](/sites/default/files/downloads/deception/release-notes/release-upgrade-summary-2023/release-notes-zscaler-deception-show-hide-internal-safe-process.png?1676288765)

### Feature Available
#### Security Headers for Web Services On Internal Decoys
Web Services on Internal decoys have prebuilt security and Strict-Transport-Security (HSTS) response headers to protect browsers and applications against attacks such as HTTP downgrade and cookie hijacking. The following headers are included:
- X-Content-Type-Options
- Referrer-Policy
- Permissions-Policy
- Content-Security-Policy
[See image.](#release-notes-deception-security-headers-web-ser)
To learn more, see [Configuring a Web Service on a Network Decoy](/deception/configuring-services-network-decoy#configuring-web-service).
[]![Enable security headers in web services](/sites/default/files/downloads/deception/release-notes/release-upgrade-summary-2023/release-notes-zscaler-deception-security-headers-internal-web-ser-1.png)

### Feature Available
#### Support for Microsoft Edge in Browser Lures
You can configure browser lures such as decoy cookies, favorites, and credentials in the Microsoft Edge browser on an endpoint.
[See image.](#release-notes-deception-browser-lures-edge)
To learn more, see [Configuring Browser Lures](/deception/configuring-browser-lures).
[]![Add browser lures in the Microsoft Edge browser](/sites/default/files/downloads/deception/release-notes/release-upgrade-summary-2023/release-notes-zscaler-deception-microsoft-edge-browser-lures.png)

### Feature Available
#### Support for openSUSE Leap 15.3 in Landmine Agent and Agentless
openSUSE Leap 15.3 and later versions were added to the supported Linux distribution list in Landmine Agent and Agentless installations on Linux.
To learn more, see [Installing a Landmine Agent on Linux](/deception/installing-landmine-agent-linux) and [Running Landmine Agentless on Linux](/deception/running-landmine-agentless-installer-linux).

### Feature Available
#### Support Users Enhancements
You can view the details of Zscaler Support team users who can access the Zscaler Deception Admin Portal on the Support Users page. You can view details such as the user name, login ID, role (Read-only or Admin), etc.
[See image.](#release-notes-deception-support-users-tab)
To learn more, see [Viewing Support Users Details](/deception/viewing-support-users-details).
On the Audit Logs page, the user names of the support users are appended with Zscaler Deception Support.
[See image.](#release-notes-deception-audit-log-support-user)
To learn more, see [Exporting Audit Logs](/deception/exporting-audit-logs).
[]![View Support Users tab](/sites/default/files/downloads/deception/release-notes/release-upgrade-summary-2023/release-notes-zscaler-deception-support-users-tab.png)
[]![View Support users details on the Audit Logs page](/sites/default/files/downloads/deception/release-notes/release-upgrade-summary-2023/release-notes-zscaler-deception-audit-logs-support-users.png)

## January 04, 2023
### Feature Available
#### Additional Information on the Virtual Machines Page
The Virtual Machines page (Settings > Virtual Machines) displays the operating system and version columns.
[See image.](#deception-release-notes-vm-os-version)
To learn more, see [Configuring Credentials for a Windows High-Interaction Virtual Machine](/deception/configuring-credentials-windows-high-interaction-virtual-machine).
[]![Operating System and Version columns on the Virtual Machines page](/sites/default/files/downloads/deception/release-notes/release-upgrade-summary-2022/release-notes-zscaler-deception-virtual-machine-os-version.png?1670824464)

### Feature Available
#### Export DNS Configuration for Threat Intelligence Decoys
You can export DNS configuration details for Threat Intelligence (TI) decoys.
[See image.](#deception-release-notes-ti-export-dns)
To learn more, see [Exporting Threat Intelligence Decoys DNS Configuration](/deception/exporting-threat-intelligence-decoys-dns-configuration) and [About Threat Intelligence Decoys](/deception/about-threat-intelligence-decoys).
[]![Export DNS configuration for Threat Intelligence decoys](/sites/default/files/downloads/deception/release-notes/release-upgrade-summary-2022/release-notes-zscaler-deception-ti-export-dns-1.png)

### Feature Available
#### Forward Safe Events to SIEM Solutions
For Security Information and Event Management (SIEM) integration, you can forward events marked as safe by Zscaler Deception to the supported SIEM solution.
[See image.](#release-notes-deception-forward-safe-events-siem)
To learn more, see [About SIEM Integrations](/deception/about-siem-integrations) and [Taking](/deception/taking-actions-from-dashboard)[ ](/deception/taking-action-from-the-dashboard)[Actions From the ](/deception/taking-actions-from-dashboard)[Dashboard](/deception/taking-action-from-dashboard).
[]![Forward safe events to Splunk SIEM](/sites/default/files/downloads/deception/release-notes/release-upgrade-summary-2022/release-notes-zscaler-deception-splunk-siem-integration.png)

### Feature Available
#### Managing ZPA and Threat Intelligence Components
If the following Zscaler Deception components are managed by Zscaler Private Access (ZPA) or Threat Intelligence (TI), you must contact Zscaler Support to manage them (i.e., edit, delete, etc.):
- Decoy Connector (ZPA and TI): Edit, obtain a connection code, configure proxy, and delete.
- Aggregator: Edit, obtain a connection code, and delete.
- Service back end: Edit, obtain a connection code, and delete.
- Subnet or interface: Edit or delete.
To learn more, see:
- [Editing or Deleting a Decoy Connector](/deception/editing-or-deleting-decoy-connector)
- [Configuring a Decoy Connector as a Proxy](/deception/configuring-decoy-connector-proxy)
- [Adding and Connecting a Decoy Connector to the Zscaler Deception Admin Portal](/deception/adding-connecting-decoy-connector-admin-portal)
- [Editing or Deleting a Subnet](/deception/editing-or-deleting-subnet)

### Feature Available
#### Quarantine Device With VMware Carbon Black Endpoint Standard
Zscaler Deception integration with VMWare Carbon Black Endpoint Standard supports the ability to block network communication with other devices by quarantining the infected endpoint, instead of using isolate policies to achieve the same outcome.
[See image.](#release-notes-deception-cb-ep-quarantine)
To learn more, see [Zscaler Deception and VMware Carbon Black Endpoint Standard Deployment Guide](/deception/zscaler-deception-and-vmware-carbon-black-endpoint-standard-deployment-guide).
[]![Contain attacker using the Quarantine option](/sites/default/files/downloads/deception/release-notes/release-upgrade-summary-2022/release-notes-zscaler-deception-cb-defense-action-type-quarantine.png)

### Feature Available
#### Security Headers for Threat Intelligence Decoys
Threat Intelligence decoys have prebuilt security and Strict-Transport-Security response (HSTS) headers to protect browsers and applications against HTTP downgrade attacks. The following headers are included:
- X-Content-Type-Options
- Referrer-Policy
- Permissions-Policy
- Content-Security-Policy
[See image.](#deception-release-notes-security-headers)
To learn more, see [Creating a Threat Intelligence Decoy](/deception/creating-threat-intelligence-decoy).
[]![Enable security headers in Threat Intelligence decoys](/sites/default/files/downloads/deception/release-notes/release-upgrade-summary-2022/release-notes-zscaler-deception-ti-enable-security-headers.png)

### Feature Available
#### Support for Safe Landmine Processes
Landmine processes that detect defense evasion sometimes generate false positives when tripped by security processes, such as an antivirus or Endpoint Detection and Response (EDR) scan. Zscaler Deception allows you to configure safe landmine processes that don’t generate events when accessed by legitimate security processes. Alerts are generated only when an attacker interacts with these landmine processes.
You can filter these safe landmine processes using the following parameters:
- Executable file path
- Executable file hash
- Certificate issuer
- Certificate serial number
- Certificate thumbprint
[See image.](#release-notes-deception-safe-process-filters)
To learn more, see [About Safe Processes](/deception/about-safe-processes) and [About Landmine Decoys](/deception/about-landmine-decoys).
[]![Configure a safe process with filters](/sites/default/files/downloads/deception/release-notes/release-upgrade-summary-2022/release-notes-zscaler-deception-safe-process-filter-details.png?1670486261)

### Feature Available
#### User Interface Enhancements
The following user interface updates were made to the Zscaler Deception Admin Portal.
Renamed SIEM Connectors
The SIEM Connectors page was renamed to Service Connectors (Orchestrate > Service Connectors) to reflect the expanding application and use of this Deception component.
[See image.](#deception-release-notes-service-connectors-page)
To learn more, see [About Service Connectors](/deception/about-service-connectors).
Renamed the Policies Column
The Policies column on the Agents page (Deceive > Landmine > Agents) was renamed to Matched Policies to indicate the policies that can be applied on the endpoint.
[See image.](#deception-release-notes-matched-policies)
To learn more, see [About Landmine Agents](/deception/about-landmine-agent-agentless) and [About Landmine Policies](/deception/about-policies).
[] ![The Service Connector page](/sites/default/files/downloads/deception/release-notes/release-upgrade-summary-2022/release-notes-zscaler-deception-service-connector-page.png)
[]![Matched Policies column on the Landmine Agents page](/sites/default/files/downloads/deception/release-notes/release-upgrade-summary-2022/release-notes-zscaler-deception-cb-agents-matched-policies.png)
