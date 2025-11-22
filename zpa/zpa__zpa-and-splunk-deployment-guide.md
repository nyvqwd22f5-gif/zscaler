# ZPA and Splunk Deployment Guide
Source: https://help.zscaler.com/zpa/zpa-and-splunk-deployment-guide
PDF: https://help.zscaler.com/pdf/com/en/1485466.pdf

This deployment guide provides information on configuring ZPA and Splunk, downloading the Zscaler Splunk App and Zscaler Technical Add-On, the Zscaler Splunk App requirements, and how to add the log sources in the Splunk SIEM. To learn more about the Zscaler Splunk App, including instructions on how to integrate Zscaler Internet Access (ZIA) and ZPA, see [Zscaler and Splunk Deployment Guide](/zscaler-technology-partners/zscaler-and-splunk-deployment-guide).
In ZPA, the [Log Streaming Service (LSS)](/zpa/about-log-streaming-service) uses a log receiver and an [App Connector](/zpa/about-connectors) to stream traffic logs in real time from the log receiver to your security information and event management (SIEM), such as Splunk, enabling you to receive information about App Connectors and users.
While the LSS is used to capture log data about App Connectors and users in ZPA using a log receiver, the Nanolog Streaming Service (NSS) resides in ZIA and allows streaming of traffic logs from the Zscaler Nanolog to your SIEM. To learn more, see [About Nanolog Streaming Service](/zia/about-nanolog-streaming-service) and the [Zscaler and Splunk Deployment Guide](/zscaler-technology-partners/zscaler-and-splunk-deployment-guide).
- [Step 1: ][Configure an LSS Log Receiver](/zpa/configuring-log-receiver)
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
| zscalerlss-zpa-bba | Browser Access Logs (LSS) |
| zscalerlss-zpa-connector | App Connector Logs (LSS) |
| zscalerlss-zpa-pse | ZPA Private Service Edge Status Logs (LSS) |
To learn more about the data bound to the different log types, see [Log Streaming Service (LSS)](/zpa/log-streaming-service).
Your Splunk administrator might need to create aliases in these fields for data to be presented into the Zscaler Splunk App.
The Zscaler Splunk App requires data to be in the Zscaler Index named `zscaler`. If your organization places Zscaler data in a different index, you can edit the base macros to reflect your setup. Zscaler requires all field names to use those that are seen in the ZPA LSS using JSON as the expected output format.
The Zscaler Splunk App has a dependency to the [Splunk Common Information Model](https://splunkbase.splunk.com/app/1621/) (CIM).
Ensure that the Web and Network Sessions data models are accelerated. This is necessary for some functions within the Zscaler Splunk App.
[]To add the Zscaler LSS as a log source:
- In Splunk, go to **Manager **> **Data Inputs**.
- Click **Add new** next to **TCP**.
- On the **Add New** page, complete the following and repeat this for each Zscaler source type you'll add in Splunk:
- Specify the TCP port where the logs are received.
- For **Source Type**, choose the Zscaler source type from the source type list. To learn more, see [ZPA Source Types](#reqSourceTypes).
- Click **More Settings** to expand the page.
- For **Set host**, click **DNS**.
- From the Index list, choose **zscaler**.
[See image.](#splunkLogSource)
- Click **Save**.
If you require further assistance after deployment, contact Zscaler Support.
[]![Adding Zscaler LSS as a log source in Splunk](/downloads/tech-pubs-drafts/zpa-draft-articles/zpa-and-splunk-deployment-guide/zpa-splunk-log-source.png)