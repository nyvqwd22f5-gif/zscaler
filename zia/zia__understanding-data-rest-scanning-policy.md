# Understanding the Data at Rest Scanning Policy
Source: https://help.zscaler.com/zia/understanding-data-rest-scanning-policy
PDF: https://help.zscaler.com/pdf/com/en/1401626.pdf

To enable Amazon S3, Google Cloud Platform, and Microsoft Azure for your organization, contact your Zscaler Account team.
The Data at Rest Scanning policy consists of the [Data Loss Prevention (DLP)](/zia/about-saas-security-api-dlp) and [Malware Detection](/zia/about-saas-security-api-malware-detection) policies. You can configure these policies for the following SaaS application types:
- Collaboration
- CRM
- Email
- File sharing
- Gen AI
- ITSM
- Public cloud storage
- Source code repository
Policy Execution
The Data at Rest Scanning rules consist of a series of logical operators between their criteria. The rules are triggered based on the result of the following logical operations between the criteria:
DLP Engines (`AND`) SaaS Application Tenants (`AND`) [Owners (`OR`) Groups (`OR`) Departments] (`AND`) Collaboration Scope (`AND`) File Type (`AND`) [Trusted Domains (`OR`) Trusted Users].
Configuring the Data at Rest Scanning Policy
To configure the Data at Rest Scanning policy:
- Configure the resources that the policies reference:
- [SaaS application tenants](/zia/adding-saas-application-tenants) for both your DLP and Malware Detection policies.
- [Users](/zia/about-users), [groups](/zia/about-groups), [departments](/zia/about-departments), and [DLP engines](/zia/about-dlp-engines) for your Data at Rest Scanning DLP policies.
- Define the rules for each policy:
- [SaaS Security DLP](/zia/configuring-saas-security-api-dlp-policy)
- [SaaS Security Malware Detection](/zia/configuring-saas-security-api-malware-detection-policy)
- [Configure SaaS Security Scan Schedules](/zia/configuring-saas-security-api-scan-schedules) for the DLP and Malware Detection policies to inspect content in sanctioned SaaS applications.
When you define a DLP or Malware Detection rule for public cloud storage applications, you can specify buckets or blob containers for inspection. To specify buckets or blob containers for the Zscaler service to inspect:
- When you first define a policy rule for a public cloud storage application, the following fields can’t be changed: Buckets, Bucket Owner, Blob Containers, and Blob Container Owner. You must create and save the rule without configuring these fields.
- After saving the policy rule, create a scan schedule for the tenant. In the table, select the bucket or blob container names to create a list of available buckets or blob containers for the DLP and Malware Detection policies.
- After you create the list and save the scan schedule, you can edit the rule and configure the Buckets, Bucket Owner, Blob Containers, or Blob Container Owner fields.
- Start scheduled scans from the [SaaS Security Scan Configuration page](/zia/about-saas-security-api-scan-configuration).