# About Cloud-to-Cloud Incident Forwarding
Source: https://help.zscaler.com/zia/about-cloud-cloud-incident-forwarding
PDF: https://help.zscaler.com/pdf/com/en/1531106.pdf

With Cloud-to-Cloud Incident Forwarding, you can send information about transactions that violate Data Loss Prevention (DLP) policy rules directly to public cloud storage accounts you defined in the ZIA Admin Portal. After you set up your storage accounts, you can then configure your DLP policy rules to use Cloud-to-Cloud Incident Forwarding.
Cloud-to-Cloud Incident Forwarding provides the following benefits and allows you to:
- Send information about transactions that violate DLP policy rules directly to public cloud storage accounts without deploying appliances.
- Apply Cloud-to-Cloud Incident Forwarding configurations to policy rules for Inline Web DLP, Data at Rest Scanning DLP, Outbound Email DLP, and Endpoint DLP.
About the Cloud-to-Cloud Incident Forwarding Page
On the Cloud-to-Cloud Incident Forwarding page (Administration > DLP Incident Receiver), you can do the following:
- [Add a public cloud account](/zia/configure-dlp-cloud-cloud-incident-forwarding).
- Search for a Cloud-to-Cloud Incident Forwarding configuration.
- View a list of all Cloud-to-Cloud Incident Forwarding configurations that were configured for your organization. For Cloud-to-Cloud Incident Forwarding configurations, you can see the following:
- **Configuration Name**: The name of the Cloud-to-Cloud Incident Forwarding configuration. You can sort this column.
- **Tenant Name**: The name of the cloud storage tenant. You can sort this column.
- **Application**: The SaaS application that hosts the public cloud storage.
- **Bucket Name for Evidence**: The storage container for evidence data about the DLP policy violation.
- **Bucket Name for Metadata JSON**: The storage container for metadata JSON associated with the DLP policy violation.
- **Status**: Indicates whether the configuration is enabled or disabled.
- [Edit or Delete a Cloud-to-Cloud Incident Forwarding configuration](/zia/how-do-i-edit-delete-or-duplicate-items-admin-portal).
- [Modify the table and its columns](/zia/how-do-i-use-tables-admin-portal).
- View the ICAP Settings page. To learn more, see [About ICAP Receivers for DLP](/zia/about-icap-receivers-dlp).
- View the Zscaler Incident Receiver page. To learn more, see [About Zscaler Incident Receiver](/zia/about-dlp-incident-receiver).
![The Cloud-to-Cloud Incident Forwarding Settings page and its features](/downloads/zia/policies/data-loss-prevention/dlp-incident-receiver/about-cloud-cloud-incident-forwarding/ZIA-DLP-Incident-Receiver-Page-C2C-Incident-Forwarding-Tab.png)