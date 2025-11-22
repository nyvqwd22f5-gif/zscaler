# Release Upgrade Summary (2022)
Source: https://help.zscaler.com/deception/release-upgrade-summary-2022

This article provides a summary of all new features and enhancements for Zscaler Deception.
The illusionblack.com cloud represents all clouds, and updates to specific clouds might take a few weeks to deploy. Some functions are not available until deployment completes.

**Clouds:** illusionblack.com
The following service updates were deployed to illusionblack.com on

## October 20, 2022
### Feature Available
#### Browser Lures Enhancements
You can view the bookmark folder names for Google Chrome and Mozilla Firefox favorite lures on the Policy Preview page for a landmine agent.
[See image.](#release-notes-zd-bookmark-folder-path)
To learn more, see [Viewing Policy Details](/deception/viewing-policy-details).
[]![Bookmark folder path displayed for browser favorite lures](/sites/default/files/downloads/deception/release-notes/release-upgrade-summary-2022/release-notes-zscaler-deception-folder-path-browser-favorite-lure.png)

### Feature Available
#### Continuous Updates to Miragemaker Decoy Datasets
Updates to Miragemaker decoy datasets are not tied to release cycles. Whenever Zscaler adds or modifies a decoy dataset, the updates are available in your Zscaler Deception instance. For example, if there is a new zero-day exploiting a vulnerability in a VPN application, Zscaler adds this vulnerable VPN to the decoy datasets, and this dataset is available in your Deception instance.

### Feature Available
#### IP Allowlist Enhancements
You can allow all IP addresses to access a particular module in the Zscaler Deception Admin Portal when you configure the allowlist on the Allowed IPs page (Settings > Network Settings > Allowed IPs).
[See image.](#release-notes-zd-allow-all-landmine-agents)
To learn more, see [Adding IP Addresses to the Zscaler Deception Admin Portal Allowlist](/deception/adding-ip-addresses-zscaler-deception-admin-portal-allowlist).
[]![Allow all IPs to access specific modules in the Zscaler Deception Admin Portal](/sites/default/files/downloads/deception/release-notes/release-upgrade-summary-2022/release-notes-zscaler-allow-all-ips-landmine-agent.png?1665115919)

### Feature Available
#### License Page Enhancements
You can view the active Zscaler Deception subscription plan your organization is licensed to on the License page (Settings > Advanced Settings > License).
[See image.](#release-notes-zd-license-page)
To learn more, see [Viewing License Details](/deception/viewing-license-details).
[]![Zscaler Deception subscription plan details](/sites/default/files/downloads/deception/release-notes/release-upgrade-summary-2022/release-notes-zscaler-deception-sub-plan-license.png)

### Feature Available
#### OpenAPI Specification Enhancements
Zscaler Deception supports OpenAPI Specification version OAS 3.0.0 for Orchestrate, Miragemaker, Deceive, Landmine, Investigate, and Settings features. You can programmatically configure and deploy decoys, manage event logs and evidence, configure Miragemaker datasets and personalities, etc.
You can add and configure API tokens for authentication on the API tokens page (Orchestrate > API tokens > Add API Token) and make API calls. You can access the API documentation on the API tokens page.
[See image.](#release-notes-zd-add-api-token)
[]![Create an API token and access API docs on the API tokens page](/sites/default/files/downloads/deception/release-notes/release-upgrade-summary-2022/release-notes-zscaler-deception-api-token.png?1665121408)

### Feature Available
#### Standalone Landmine Agent to Zscaler Client Connector Migration
If you are running endpoint deception using a standalone landmine agent and want to migrate to Zscaler Client Connector, you can automatically migrate when you upgrade Zscaler Client Connector to 3.9 or later for Windows. During the upgrade, important information such as lures applied and decoys deployed are automatically copied to the new installation location, and the standalone landmine agent is uninstalled.
To learn more, see [What is Zscaler Client Connector?](/z-app/what-zscaler-app) and [Deploying Endpoint Deception With Zscaler Client Connector for Windows](/deception/deploying-endpoint-deception-zscaler-client-connector-windows).

### Feature Available
#### User Interface Enhancements
The following user interface updates were made to the Zscaler Deception Admin Portal:
- The Connectors and Integrations tabs on the SIEM page (Orchestrate > SIEM) were removed. The tabs were replaced with SIEM Connectors (Orchestrate > SIEM Connectors) and SIEM Integrations pages (Orchestrate > SIEM Integrations).
[See image. ](#release-notes-zd-siem-connectors-page)
To learn more, see [About SIEM Connectors](/deception/about-siem-connectors).
[See image.](#release-notes-zd-siem-integrations-page)
To learn more, see [About SIEM Integrations](/deception/about-siem-integrations).
- The Carbon Black Defense and Carbon Black Response solutions on the Containment page (Orchestrate > Containment) were renamed to VMware Carbon Black Endpoint Standard and VMware Carbon Black EDR respectively, to reflect the rebranding after the VMWare acquisition.
[See image.](#release-notes-zd-carbon-black-containment)
- The Netmonastery solution on the SIEM Integrations page (Orchestrate > SIEM Integrations) was renamed to Netmonastery DNIF to match the official brand name.
[See image.](#release-notes-zd-netmonastery-dnif)
To learn more, see [Deception and Netmonastery DNIF Deployment Guide](/deception/deception-and-netmonastery-deployment-guide).
- The Phone Template field on the Event Templates page (Orchestrate > Event Templates) was renamed to Phone Call Notification to reflect the current capabilities of this feature.
[See image.](#release-notes-zd-phone-call-notification)
To learn more, see [Customizing Event Notification Templates](/deception/customizing-event-notification-templates).
- The Internal Decoys page (Deceive > Network Decoys > Internal Decoys) was renamed to Internal to reflect the extent of use cases this capability supports.
[See image.](#release-notes-zd-internal-decoy-renamed)
[]![SIEM Connectors page](/sites/default/files/downloads/deception/release-notes/release-upgrade-summary-2022/release-notes-zscaler-deception-folder-siem-connectors-page.png)
[] ![SIEM Integrations page](/sites/default/files/downloads/deception/release-notes/release-upgrade-summary-2022/release-notes-zscaler-deception-folder-siem-integrations-page.png)
[]![VMware Carbon Black Containment Solutions](/sites/default/files/downloads/deception/release-notes/release-upgrade-summary-2022/release-notes-zscaler-deception-vmware-carbon-black-containment-solutions.png)
[]![Netmonastery DNIF SEIM integration details](/sites/default/files/downloads/deception/release-notes/release-upgrade-summary-2022/release-notes-zscaler-deception-netmonastery.png)
[]![Phone call notification template](/sites/default/files/downloads/deception/release-notes/release-upgrade-summary-2022/release-notes-zscaler-deception-phone-call-notification-template.png)
[]![Internal decoys page](/sites/default/files/downloads/deception/release-notes/release-upgrade-summary-2022/release-notes-zscaler-deception-internal-decoys.png)

## September 12, 2022
### Feature Available
#### Deception Release 4.14 Enhancements and Fixes
- Integration with Zscaler Sandbox: Deception supports improved threat investigation and a native integration with Sandbox. You can send evidence to Sandbox to enrich attack information with threat intelligence and generate an analysis report with detailed Indicators of Compromise (IOC) information.
[See image.](#Deception-Sandbox-Support)
To learn more, see [About Evidence](/deception/about-evidence), [Sending an Evidence File to a Sandbox](/deception/sending-evidence-file-sandbox), and [Downloading a Sandbox Report](/deception/downloading-sandbox-report).
- Threat Containment Integration with Microsoft Windows Defender: For Windows Defender, you can leverage Deception alerts to isolate infected endpoints by sending a block request. You can block or quarantine an infected endpoint automatically based on the orchestration rule (Orchestrate > Containment > Microsoft Defender), or manually within the Zscaler Deception Dashboard.
- Endpoint Deception Integration with Zscaler Client Connector: If you are running Client Connector, you automatically gain access to endpoint deception capabilities by upgrading to Client Connector 3.9 or later. To enable this feature for your organization, contact your Zscaler Account Team. To learn more, see [What is Zscaler Client Connector?](/z-app/what-zscaler-app) and [Enabling Deception for a Group of Users](/client-connector/selective-entitlement-enabling-deception-group-users).
- LDAP Detection Support: You can detect high-fidelity LDAP activity on your endpoints.
- Export Agent Logs from Endpoints: Added the ability to export logs from active endpoints to significantly expedite the troubleshooting process.
[See image.](#Deception-Export-Logs)
To learn more, see [Downloading Landmine Agent Logs from an Endpoint](/deception/downloading-landmine-agent-logs-endpoint).
- Decoy Licensing: In order provide more control over the use cases you want to operationalize, Deception has implemented a unified decoy licensing system that no longer requires differentiating between decoy types. For example, if you have 40 Network decoy licenses, 20 Active Directory decoy licenses, and 10 Private Threat Intelligence decoy licenses those are now considered 70 licenses total that you can use towards any use case.
This update will not impact your existing deployment but will benefit your organization by allowing you to expand into additional use cases. For example, before this licensing update, if you had exhausted all your Private Threat Intelligence decoys but wanted to deploy more you would have had to purchase additional decoys. Now, you can use the licenses remaining from other decoys (i.e., Network decoys, Active Directory decoys).
[]![Zscaler Deception Admin Portal with View Evidence and send to Sandbox button](/sites/default/files/downloads/deception/release-notes/release-upgrade-summary-2022/releasenotes-zscaler-deception-view-evidence-send-to-sandbox-icon.png)
[]![Download Agent logs button in Zscaler Deception Admin Portal](/sites/default/files/downloads/deception/release-notes/release-upgrade-summary-2022/releasenotes-zscaler-deception-landmine-agents-download-icon.png)
