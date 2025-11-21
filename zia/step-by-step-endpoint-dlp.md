# Step-by-Step Configuration Guide for Zscaler Endpoint DLP
Source: https://help.zscaler.com/zia/step-by-step-endpoint-dlp
PDF: https://help.zscaler.com/pdf/com/en/1463211.pdf

[]This guide takes you through the configuration steps you need to complete to begin using Zscaler Endpoint Data Loss Prevention (DLP) for your organization. Because Endpoint DLP integrates with Zscaler Client Connector, you can set up and configure Endpoint DLP policies before pushing those policies to Zscaler Client Connector. To learn more, see the [Step-by-Step Configuration Guide for Zscaler Client Connector](/client-connector/step-step-configuration-guide-zscaler-client-connector).
Before you begin configuring Endpoint DLP, Zscaler recommends reading the following articles:
- [About Endpoint Data Loss Prevention](/zia/about-endpoint-dlp)
- [About NSS Feeds](/zia/about-nss-feeds)
- [About Dashboards](/zia/about-dashboards)
- [About Interactive Reports](/zia/about-interactive-reports)
- [What is Zscaler Client Connector?](/zscaler-client-connector/what-is-zscaler-client-connector)
Configuring Zscaler Endpoint DLP
To configure Zscaler Endpoint DLP, complete the following steps:
- [Step 1: Complete System Requirements and Prerequisite Tasks](#system-requirements)
- [Step 2: Create DLP Resources](#create-dlp-resources)
- [Step 3: Create DLP Rules and Policies for Endpoints](#create-dlp-rules)
- [Step 4: Use Zscaler Client Connector to Deploy Policies to Endpoints](#use-zcc-to-deploy-policies)
- [Step 5: Configure Endpoint NSS Feeds](#configure-endpoint-nss)
- [Step 6: Monitor Activity with Dashboards and Reports](#monitor-dashboards-reports)
- []Endpoints running Windows 11 or Windows 10 (64-bit)
Endpoint DLP is not supported on ARM processor-based Windows machines.
- Endpoints running macOS 13, 14, or 15 (Ventura, Sonoma, or Sequoia)
- Zscaler Client Connector:
- Windows: Version 4.3.0 or later
- macOS: Version 4.2.0 or later
- Endpoint DLP file paths included in the [allowlist for Zscaler Client Connector](/client-connector/zscaler-client-connector-processes-allowlist).
- Virtual desktop infrastructure (VDI) support:
- VMWare vSphere-hosted VDI
- Amazon WorkSpaces VDI
- To ensure that [Endpoint Data Scan](/zia/about-endpoint-data-scan) properly scans all the endpoints connected to your organization's traffic, you must place the following URLs on [the allowlist](/zia/adding-urls-allowlist):
- [URLs to Add to the Allowlist](#data-scan-allowlist)
- []endpoints.prod.us-east-1.m0.dataprotection.zscaler.net
- endpoints.prod.us-east-1.w1.dataprotection.zscaler.net
- endpoints.prod.eu-central-1.w2.dataprotection.zscaler.net
- storage.prod.eu-central-1.w2.dataprotection.zscaler.net
- storage.prod.us-east-1.w1.dataprotection.zscaler.net
[]Creating a DLP resource is the first step in setting up an Endpoint DLP policy. You can use the resources you create to configure an Endpoint DLP policy that protects your organization from data loss by monitoring and taking action on sensitive data that end users interact with on endpoints.
The Zscaler service supports the following DLP resources:
- Network shares
- Printers
- Removable storage
The Zscaler service automatically supports Box, Dropbox, Google Drive, iCloud for macOS, and OneDrive personal cloud storage accounts. No extra configuration is available for those services as DLP resources.
To learn more, see [About DLP Resources](/zia/about-dlp-resources).
[]You can use Zscaler's DLP engines to detect data, allow or block transactions, and notify your organization's auditor when a user's activity on an endpoint triggers an Endpoint DLP rule. You create rules based on the DLP resources available to your organization. You can create rules that monitor all instances of a resource, or you can monitor specific instances.
To learn more, see [Configuring Endpoint DLP Policy Rules](/zia/configuring-endpoint-dlp-policy-rules).
[]After you configure and activate Endpoint DLP policy in Zscaler Internet Access (ZIA), you can silently deploy the policy to Zscaler Client Connector on users' devices so that endpoints automatically retrieve the policy from the Zscaler cloud. After that, the DLP policy is enforced and incidents are logged even if endpoints don't have a network connection.
To learn more, see [Configuring Zscaler Client Connector App Profiles](/zscaler-client-connector/configuring-zscaler-client-connector-app-profiles).
[]You can configure Nanolog Streaming Service (NSS) feeds to specify the data from the Endpoint DLP logs that the NSS sends to your security information and event management (SIEM) system. To learn more, see [Adding NSS Feeds for Endpoint DLP Logs](/zia/adding-nss-feeds-endpoint-dlp-logs).
[]You can use Endpoint DLP reports and logs to gain visibility and insight into your organization's Endpoint DLP activity. Specifically, dashboard or report widgets, or charts on an Insights page allow you to work with Endpoint DLP data types and filters to define the Endpoint DLP information that you want to view.
To learn more, see [About Endpoint DLP Report](/zia/about-endpoint-dlp-report) and [Endpoint DLP Data Types and Filters](/zia/endpoint-dlp-data-types-and-filters).