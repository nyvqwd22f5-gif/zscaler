# Understanding the Data at Rest Scanning Policy
Source: https://help.zscaler.com/unified/understanding-data-rest-scanning-policy
PDF: https://help.zscaler.com/pdf/com/en/1493006.pdf

To enable Amazon S3, Google Cloud Platform, and Microsoft Azure for your organization, contact your Zscaler Account team.
The Data at Rest Scanning policy consists of the [Data Loss Prevention (DLP)](/unified/about-data-rest-scanning-dlp) and [Malware Detection](/unified/about-data-rest-scanning-malware-detection) policies. You can configure these policies for the following SaaS application types:
- Collaboration
- CRM
- Email
- File sharing
- ITSM
- Public cloud storage
- Source code repository
Configuring the Data at Rest Scanning Policy
To configure the Data at Rest Scanning policy:
- Configure the resources that the policies will reference:
- [SaaS application tenants](/unified/adding-saas-application-tenants) for both your Data at Rest Scanning DLP and Malware Detection policies.
- [Users](/unified/about-users), [groups](/unified/about-groups), [departments](/unified/about-departments), and [DLP engines](/unified/about-dlp-engines) for your Data at Rest Scanning DLP policies.
- Define the rules for each policy:
- [SaaS Security DLP](/unified/configuring-data-rest-scanning-dlp-policy)
- [SaaS Security Malware Detection](/unified/configuring-data-rest-scanning-malware-detection-policy)
-
[Configure SaaS Security scan schedules](/unified/configuring-saas-security-scan-schedules) for the DLP and Malware Detection policies to inspect content in sanctioned SaaS applications.
When you define a DLP or Malware Detection rule for public cloud storage applications, you can specify buckets or blob containers for inspection. To specify buckets or blob containers for the Zscaler service to inspect:
- When you first define a policy rule for a public cloud storage application, the following fields can’t be changed: Buckets, Bucket Owner, Blob Containers, and Blob Container Owner. You must create and save the rule without configuring these fields.
- After saving the policy rule, create a scan schedule for the tenant. In the table, select the bucket or blob container names to create a list of available buckets or blob containers for the DLP and Malware Detection policies.
- After you create the list and save the scan schedule, you can edit the rule and configure the Buckets, Bucket Owner, Blob Containers, or Blob Container Owner fields.
- Start scheduled scans from the [SaaS Security Scan Configuration](/unified/about-saas-security-scan-configuration) page.