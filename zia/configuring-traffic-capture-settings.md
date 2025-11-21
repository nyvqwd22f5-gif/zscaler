# Configuring Traffic Capture Settings
Source: https://help.zscaler.com/zia/configuring-traffic-capture-settings
PDF: https://help.zscaler.com/pdf/com/en/1463531.pdf

The Zscaler service can be configured to capture traffic that matches a policy criteria, content scan signature, or any other detection logic for later analysis. Zscaler offers multiple ways to capture network traffic. With Zscaler Traffic Capture Essentials, you can capture traffic as PCAP files for supported actions with ZIA policies. With Traffic Capture for Network Detection and Response (NDR), you can capture traffic as PCAPNG files with the Traffic Capture policy (Policy > Traffic Capture). To learn more, see [Configuring the Traffic Capture Policy](/zia/configuring-traffic-capture-policy). To learn more about Traffic Capture, see [About Traffic Capture Settings](/zia/about-traffic-capture). Captured traffic is stored in an Amazon S3 bucket. Your organization must have an S3 bucket configured to store capture data for all Traffic Capture methods. To learn more about Amazon S3, refer to the [Amazon S3 documentation](https://docs.aws.amazon.com/AmazonS3/latest/userguide/Welcome.html). Your Amazon S3 bucket configuration must have the appropriate permissions to ensure that capture files are uploaded and ingested properly. For an example, see page 23 of the [Zscaler and Vectra Deployment Guide](/zscaler-technology-partners/zscaler-and-vectra-deployment-guide).
When configuring your S3 bucket, Zscaler recommends using dual-stack storage endpoints for all cloud destinations.
To configure the Traffic Capture settings:
- Go to **Administration** > **Traffic Capture**.
- Click **Enable Traffic Capture**. This enables both Traffic Capture Essentials and Traffic Capture for NDR.
-
In the **AWS S3 Settings** section:
- **AWS Access ID**: Enter the ID associated with your organization's S3 bucket.
- **AWS Secret Key**: Enter the password associated with your organization's S3 bucket.
-
**S3 Folder URL**: Enter the URL associated with your organization's S3 bucket.
The Zscaler service does not support custom or directory-style bucket URLs that include non-standard prefixes, additional subdomains (e.g., s3express), or unconventional naming patterns (such as double dashes). You must use a general purpose S3 bucket URL following the standard format `https://<``bucket-name``>.s3.<``region``>.amazonaws.com/<``path``>`.
-
**HTTP Headers**:** **(Optional) Enter a string to add metadata to the Amazon S3 REST request:
- **Key**: The case-sensitive name of the HTTP header.
- **Value**: The parameters for the HTTP header.
For example, you can use HTTP headers to include the information necessary for configuring server-side encryption with customer-provided keys (SSE-C).
After you have entered the information, you can click **Test Connection **to verify the status of the connection.
[See image.](#AWS-S3-settings)
-
(Optional) Set limits or use the defaults for Traffic Capture Essentials in the **Per Occurrence Limits** section:
- **Storage Limit**: The maximum amount of data to be kept in the file when a policy configured for Traffic Capture Essentials triggers.
- **Sampling**: The percentage of traffic that is sampled for capturing when Traffic Capture Essentials is triggered.
[See image.](#per-occurrence-limits)
-
(Optional) in the **Obfuscate **section, choose to obfuscate information in Traffic Capture for NDR data:
- **User Names**: Choose whether usernames in created PCAPNG files are **Visible** or **Obfuscated**.
- **Devices**: Choose whether device information in created PCAPNG files is **Visible** or **Obfuscated**.
[See image.](#obfuscation)
- Click **Save**.
- For the following policies that allow Traffic Capture Essentials, you can enable the **Capture **option:
- [Advanced Threat Protection](/zia/configuring-advanced-threat-protection-policy)
- [File Type Control](/zia/configuring-file-type-control-policy)
- [Firewall Filtering](/zia/configuring-firewall-filtering-policy)
- [DNS Filtering](/zia/configuring-dns-control-policy)
- [IPS Control](/zia/configuring-ips-control-policy)
- [Malware Protection](/zia/configuring-malware-protection-policy)
- [URL Filtering](/zia/configuring-url-filtering-policy)
- Click **Save **and [activate the change](/zia/saving-and-activating-changes-zia-admin-portal).
[]![The AWS S3 Settings show Amazon S3 bucket information](/downloads/zia/traffic-forwarding/traffic-capture/configuring-traffic-capture/aws-s3-settings.png)
[]![The Per Occurrence Limits section is where you can set limits for event-based Traffic Capture](/downloads/zia/traffic-forwarding/traffic-capture/configuring-traffic-capture/per-occurrence-limits.png)
[]![Choose whether User Names and Devices are Visible or Obfuscated in captured traffic](/downloads/zia/traffic-forwarding/traffic-capture/configuring-traffic-capture/ZIA-traffic-capture-obfuscation.png)