# About Zscaler Incident Receiver
Source: https://help.zscaler.com/unified/about-zscaler-incident-receiver
PDF: https://help.zscaler.com/pdf/com/en/1492941.pdf

The Zscaler Incident Receiver is a tool that allows you to receive information about DLP policy violations securely. It can run on an EC2 instance on Amazon Web Services (AWS), on an Azure VM, or on-premises. The Zscaler service sends information about policy violations via ICAP to the Incident Receiver. This tool sends the policy-violating content and a JSON file containing the metadata for the inline web and CASB DLP policy scan (e.g., the URL, Collaborators, DLP dictionaries, DLP engines, etc.).
The incident receiver is only available for organizations that do not already own an ICAP server.
The Zscaler Incident Receiver provides the following benefits and allows you to:
- Securely receive information about DLP policy violations.
- Isolate policy-violating content for further inspection.
- Host the Incident Receiver VM on an AWS EC2 instance, on an Azure VM, or on-premises.
After a [Zscaler Incident Receiver](/unified/adding-zscaler-incident-receiver) is created and the virtual machine (VM) for the tool is installed, you can add it to a DLP policy rule ([with content inspection](/unified/configuring-dlp-policy-rules-content-inspection), [without content inspection](/unified/configuring-dlp-policy-rules-without-content-inspection), [SaaS Security API](/unified/configuring-saas-security-api-dlp-policy), or [Endpoint DLP](/unified/configuring-endpoint-dlp-policy-rules)) as a DLP incident receiver.
The Zscaler Incident Receiver does not store files locally and requires either an S3 storage bucket or a storage server or to store data. To learn more, see [Configuring the Zscaler Incident Receiver for Amazon Web Services EC2 VMs](/unified/configuring-zscaler-incident-receiver-amazon-web-services-ec2-vms), [Configuring the Zscaler Incident Receiver for Azure VMs](/unified/configuring-zscaler-incident-receiver-azure-vms), and [Configuring the Zscaler Incident Receiver for On-Premises VMs](/unified/configuring-zscaler-incident-receiver-premises-vms).
About the Zscaler Incident Receiver Page
On the Zscaler Incident Receiver page (Policies > Data Protection > Common Resources > DLP Incident Receiver > Zscaler Incident Receiver), you can do the following:
- [Add a Zscaler Incident Receiver.](/unified/adding-zscaler-incident-receiver)
- [Download the VM (.ova) for the Zscaler Incident Receiver.](/unified/configuring-zscaler-incident-receiver-premises-vms)
- Search for a Zscaler Incident Receiver.
- View a list of all the Zscaler Incident Receivers for your organization. For each Zscaler Incident Receiver, you can see and sort the following:
- **Name**: The name of the incident receiver.
- **URI**: The incident receiver URI.
- **Status**: Displays whether the incident receiver is enabled or disabled.
- **Certificate**: Displays a link that allows you to download the certificate used by the incident receiver.
- [Modify the table and its columns.](/unified/using-tables)
- [Add a new client certificate](/unified/adding-zscaler-incident-receiver).
- [Edit a Zscaler Incident Receiver](/zia/modifying-zscaler-incident-receiver), including the ability to delete a configuration.
- View the ICAP Settings page. To learn more, see [About ICAP Receivers for DLP](/unified/about-icap-receivers-dlp).
- View the Cloud-to-Cloud Incident Forwarding page. To learn more, see [About Cloud-to-Cloud Incident Forwarding](/unified/about-cloud-cloud-incident-forwarding).
![Tasks for the Zscaler Incident Receiver page](/downloads/zia/policies/data-loss-prevention/dlp-incident-receiver/about-zscaler-incident-receiver/About-ZIA-Zscaler-Incident-Receiver-page-C2C.png)