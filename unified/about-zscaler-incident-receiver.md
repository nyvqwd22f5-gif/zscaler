# About Zscaler Incident Receiver
Source: https://help.zscaler.com/zia/about-zscaler-incident-receiver
PDF: https://help.zscaler.com/pdf/com/en/1401706.pdf

The Zscaler Incident Receiver is a tool that allows you to receive information about DLP policy violations securely. It can run on an EC2 instance on Amazon Web Services (AWS), on an Azure VM, or on-premises. The Zscaler service sends information about policy violations via ICAP to the Incident Receiver. This tool sends the policy-violating content and a JSON file containing the metadata for the inline web and CASB DLP policy scan (e.g., the URL, Collaborators, DLP dictionaries, DLP engines, etc.).
The incident receiver is only available for organizations that do not already own an ICAP server.
The Zscaler Incident Receiver provides the following benefits and allows you to:
- Securely receive information about DLP policy violations.
- Isolate policy-violating content for further inspection.
- Host the Incident Receiver VM on an AWS EC2 instance, on an Azure VM, or on-premises.
After a [Zscaler Incident Receiver](/zia/adding-zscaler-incident-receiver) is created and the [virtual machine (VM)](/zia/configuring-zscaler-incident-receiver) for the tool is installed, you can add it to a DLP policy rule ([with content inspection](/zia/configuring-dlp-policy-rules-content-inspection), [without content inspection](/zia/configuring-dlp-policy-rules-without-content-inspection), or [SaaS Security API](/zia/configuring-saas-security-api-dlp-policy)) as a DLP incident receiver.
The Zscaler Incident Receiver does not store files locally and requires either an S3 storage bucket or a storage server or to store data. To learn more, see [Configuring the Zscaler Incident Receiver for Amazon Web Services EC2 VMs](/zia/configuring-zscaler-incident-receiver-for-ec2), [Configuring the Zscaler Incident Receiver for Azure VMs](/zia/configuring-zscaler-incident-receiver-azure-vms), and [Configuring the Zscaler Incident Receiver for On-Premises VMs](/zia/configuring-zscaler-incident-receiver).
About the Zscaler Incident Receiver Page
On the Zscaler Incident Receiver page (Administration > DLP Incident Receiver > Zscaler Incident Receiver), you can do the following:
- [Add a Zscaler Incident Receiver.](/zia/adding-zscaler-incident-receiver)
- [Download the VM (.ova) for the Zscaler Incident Receiver.](/zia/configuring-zscaler-incident-receiver)
- Search for a Zscaler Incident Receiver.
- View a list of all the Zscaler Incident Receivers for your organization. For each Zscaler Incident Receiver, you can see and sort the following:
- **Name**: The name of the incident receiver.
- **Status**: Displays whether the incident receiver is enabled or disabled.
- **URI**: The incident receiver URI.
- **Certificate**: Displays a link that allows you to download the certificate used by the incident receiver.
- [Modify the table and its columns.](/zia/using-tables)
- [Add a new client certificate](/zia/adding-zscaler-incident-receiver).
- [Edit a Zscaler Incident Receiver](/zia/modifying-zscaler-incident-receiver), including the ability to delete a configuration.
- View the ICAP Settings page. To learn more, see [About ICAP Receivers for DLP](/zia/about-icap-servers).
- View the Cloud-to-Cloud Incident Forwarding page. To learn more, see [About Cloud-to-Cloud Incident Forwarding](/zia/about-cloud-cloud-incident-forwarding).
![Tasks for the Zscaler Incident Receiver page](/downloads/zia/policies/data-loss-prevention/dlp-incident-receiver/about-zscaler-incident-receiver/About-ZIA-Zscaler-Incident-Receiver-page-C2C.png)