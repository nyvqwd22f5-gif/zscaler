# Private Applications and Splunk Deployment Guide
Source: https://help.zscaler.com/unified/private-applications-and-splunk-deployment-guide
PDF: https://help.zscaler.com/pdf/com/en/1496031.pdf

This deployment guide provides information on configuring Private Applications and Splunk, downloading the Zscaler Splunk App and Zscaler Technical Add-On, the Zscaler Splunk App requirements, and how to add the log sources in the Splunk SIEM.
In Private Applications, the [Log Streaming Service (LSS)](/unified/about-log-streaming-service) uses a log receiver and an [App Connector](/unified/about-app-connectors) to stream traffic logs in real time from the log receiver to your security information and event management (SIEM), such as Splunk, enabling you to receive information about App Connectors and users.
While the LSS is used to capture log data about App Connectors and users in Private Applications using a log receiver, the Nanolog Streaming Service (NSS) resides in Internet & SaaS and allows streaming of traffic logs from the Zscaler Nanolog to your SIEM. To learn more, see [Understanding Nanolog Streaming Service (NSS)](/unified/understanding-nanolog-streaming-service).
- [Step 1: ][Configure an LSS Log Receiver](/unified/configuring-log-receiver)
- [Step 2: Download the Zscaler Splunk App and the Zscaler Technical Add-On from Splunkbase](#downloadSplunk)
- [Step 3: Review the Zscaler Splunk App Requirements](#reviewSplunkRequirements)
- [Step 4: In the Splunk SIEM, Add the Zscaler LSS as a Log Source](#addLssLogSource)
[]Zscaler on Splunk comes in two parts: [Zscaler Technical Add-On (TA) for Splunk](https://splunkbase.splunk.com/app/3865/) and the [Zscaler Splunk App](https://splunkbase.splunk.com/app/3866/).
The Zscaler TA for Splunk is a required component for the Zscaler Splunk App.
[]The Zscaler Splunk App expects to find data bound to the following source types:
| Source Type | Description |
| ----------- | ----------- |
| zscalerlss-zpa-app | User Activity Logs (LSS) |
| zscalerlss-zpa-web-inspection | AppProtection Logs (LSS) |
| zscalerlss-zpa-audit | Audit Logs (LSS) |
| zscalerlss-zpa-auth | User Status Logs (LSS) |
| zscalerlss-zpa-bba | Browser Access (LSS) |
| zscalerlss-zpa-connector | App Connector Logs (LSS) |
| zscalerlss-zpa-pse | Private Service Edge Status Logs (LSS) for Private Applications |
To learn more about the data bound to the different log types, see [Log Streaming Service (LSS)](/unified/logs/private-applications/log-streaming).
Your Splunk administrator might need to create aliases in these fields for data to be presented into the Zscaler Splunk App.
The Zscaler Splunk App requires data to be in the Zscaler Index named `zscaler`. If your organization places Zscaler data in a different index, you can edit the base macros to reflect your setup. Zscaler requires all field names to use those that are seen in the LSS using JSON as the expected output format.
The Zscaler Splunk App has a dependency to the [Splunk Common Information Model](https://splunkbase.splunk.com/app/1621/) (CIM).
Ensure that the Web and Network Sessions data models are accelerated. This is necessary for some functions within the Zscaler Splunk App.
[]To add the Zscaler LSS as a log source:
- In Splunk, go to **Manager **> **Data Inputs**.
- Click **Add new** next to TCP.
- On the **Add New** page, complete the following and repeat this for each Zscaler source type you'll add in Splunk:
- Specify the TCP port where the logs are received.
- For **Source Type**, choose the Zscaler source type from the source type list. To learn more, see [Source Types for Private Applications](#reqSourceTypes).
- Click **More Settings** to expand the page.
- For **Set host**, click **DNS**.
- From the Index list, choose **zscaler**.
[See image.](#splunkLogSource)
- Click **Save**.
If you require further assistance after deployment, contact Zscaler Support.
[]![Adding Zscaler LSS as a log source in Splunk](/downloads/tech-pubs-drafts/zpa-draft-articles/zpa-and-splunk-deployment-guide/zpa-splunk-log-source.png)