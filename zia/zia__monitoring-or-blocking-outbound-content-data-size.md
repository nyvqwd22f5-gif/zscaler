# Monitoring or Blocking Outbound Content by Data Size
Source: https://help.zscaler.com/zia/monitoring-or-blocking-outbound-content-data-size
PDF: https://help.zscaler.com/pdf/com/en/1400001.pdf

You might want to leverage Zscaler's DLP policy to monitor or block specific types of outbound content by data size, without scanning for specific data within the content. For example, you could block outbound image files (such as GIF or JPEG), but only those that exceed a certain data size. In Policy > File Type Control, you can set policy to block image files, but you cannot specify data size.
For this scenario, you can leverage the Rule Without Content Inspection policy option. When configuring the policy, you can specify the criteria Zscaler uses for monitoring or blocking content, but refrain from specifying an ICAP server. Zscaler will monitor or block outbound content based on the criteria you specify, but will not send content to any external DLP engines. The illustration below details the process that takes place when you configure DLP policies for this scenario:
[]
![Diagram showing the process that takes place when you configure DLP policies for the External DLP Engine policy option](/downloads/zia/documentation-knowledgebase/policies/data-loss-prevention/monitoring-or-blocking-outbound-content-data-size/zia-dlp-external-size.png)
To configure rules for this scenario:
- [Configure your DLP notification templates.](/zia/configuring-dlp-notification-templates) Once configured, email notifications are sent to your organization's auditor when DLP rules are applied to users' content.
- [][Define your DLP policy rule without content inspection.](/zia/configuring-dlp-policy-rules-without-content-inspection#Add)