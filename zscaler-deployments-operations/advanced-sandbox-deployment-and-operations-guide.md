# Advanced Sandbox Deployment and Operations Guide
Source: https://help.zscaler.com/zscaler-deployments-operations/advanced-sandbox-deployment-and-operations-guide
PDF: https://help.zscaler.com/pdf/com/en/1417931.pdf

This guide describes the benefits of using Advanced Sandbox and the steps necessary for configuring Zscaler Internet Access (ZIA) to add Advanced Sandbox to your security posture.
Advanced Sandbox provides an additional layer of security by analyzing suspected malware files in a virtual environment to detect malicious behavior. It distributes a hash of malicious files to all ZIA Public Service Edges, effectively maintaining a real-time denylist. The analysis based on the denylist prevents users (anywhere) from downloading malicious files.
To learn more, see [About Sandbox](/zia/about-sandbox).
Value of Deploying Advanced Sandbox
Using Advanced Sandbox provides more capabilities and more security options than Basic Sandbox:
- Scans more file types than .exe and .dll, including .jar, archives, scripts in MS files, MS macros, .pdf, .swf, and .apk.
- Scans files sized higher than 2 MB.
- Quarantines files via configuration rules.
Deployment Phase
The deployment phase initially sets up and integrates ZIA solutions into an existing network infrastructure. During the deployment phase, you configure ZIA Advanced Sandbox to meet the needs of your infrastructure. The following sections discuss the steps to deploy ZIA Advanced Sandbox.
Prerequisites
One of the following Zscaler subscriptions is required:
- ZIA Transformation Edition and later.
- Advanced Sandbox Add-On.
Deployment Steps
The following steps explain how to deploy ZIA Advanced Sandbox:
- Make sure to [enable the inspection on inbound and outbound traffic](/zia/configuring-default-sandbox-rule#enable-inbound-outbound-traffic-inspection).
- (Optional) [Review and implement the recommended policies for Sandbox](/zia/what-recommended-sandbox-policy).
- (Optional) [Edit the default Sandbox rule](/zia/configuring-default-sandbox-rule#edit-default-sandbox-rule) if necessary.
- [Add policies to Sandbox](/zia/configuring-sandbox-policy#add-sandbox-rule) that match your organization’s needs.
- (Optional) [Configuring the Patient 0 Alert](/zia/configuring-patient-0-alert) and other [Alert Definitions](/zia/about-alerts).
- (Optional) [Configure Sandbox end user](/zia/about-sandbox-end-user-notifications) notifications.
Considerations
Review the following considerations:
- Rules in the Rule Order List are applied first to last. The last rule checked is the default rule.
- Any rule that applies to unauthenticated traffic must apply to all groups and departments.
- The Zscaler service does an initial static analysis for unknown PDF or Microsoft Office files to check for active content:
- If the Zscaler service detects active content, it sends the files to the Sandbox for behavioral analysis.
- If the Zscaler service does not detect active content, the files are classified as benign and allowed to download.
- If you choose Allow as the action for subsequent downloads, and a user attempts to download a malicious Sandbox classified file, the service allows the download. Zscaler recommends disallowing subsequent downloads of flagged malicious content (unless it is for testing).
Operations Phase
This section describes common practices used to operate Zscaler solutions when integrated with your environment. You can monitor and tune ZIA Advanced Sandbox during operations to meet your infrastructure needs.
Prerequisites
For Advanced Sandbox operation, complete the following prerequisites:
- The operations team should familiarize themselves with the following reports and tools. Support can view a variety of Sandbox data and reports under Dashboard and Analytics:
- [Security Dashboard](/zia/viewing-sandbox-reports-data#security-dashboard)
- [Web Insights](/zia/viewing-sandbox-reports-data#web-insights)
- [Sandbox Detail Report](/zia/viewing-sandbox-reports-data#about-sandbox-detail-report)
- Examine Sandbox activity in the [Sandbox Activity Report](/zia/about-sandbox-activity-report):
- Review the Sandbox [Files Found Malicious](/zia/about-sandbox-files-found-malicious-report) report for information on what files are quarantined.
- Check the Endpoint Hit Reports for endpoints exposed to malicious files (if integrated with [CrowdStrike](/zia/configuring-crowdstrike-integration), [VMware Carbon Black](/zscaler-technology-partners/zscaler-and-vmware-carbon-black-deployment-guide), or [Microsoft Defender for Endpoint](/zia/integrating-microsoft-defender-endpoint)).
- Use the [Sandbox Scanning Portal](http://filecheck.zscaler.com/) to submit suspicious files for behavioral analysis.
Deployment Checklist
Zscaler recommends downloading the [Advanced Sandbox Deployment and Operations Checklist](/downloads/zscaler-deployments-operations/zia-deployments-operations/advanced-cloud-sandbox-deployment-and-operations-guide/Advanced-Sandbox-Deployment-Operations-Checklist.pdf) to help plan and implement ZIA Advanced Sandbox: [Download PDF](/downloads/zscaler-deployments-operations/zia-deployments-operations/advanced-cloud-sandbox-deployment-and-operations-guide/Advanced-Sandbox-Deployment-Operations-Checklist.pdf)
Additional Information
For more SaaS Security information and troubleshooting instructions, see the [Zscaler Support Portal](https://zscaler.my.site.com/customers/s/) and the [Zscaler Zenith Community](http://community.zscaler.com/).