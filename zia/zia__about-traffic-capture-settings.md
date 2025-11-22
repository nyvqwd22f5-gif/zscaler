# About Traffic Capture Settings
Source: https://help.zscaler.com/zia/about-traffic-capture-settings
PDF: https://help.zscaler.com/pdf/com/en/1463526.pdf

Zscaler offers multiple ways to capture network traffic, which can be accessed later through an Amazon S3 bucket managed by your organization. With Zscaler Traffic Capture Essentials, you can capture traffic as PCAP files for supported actions with the following policies:
- Advanced Threat Protection
- File Type Control
- Firewall Filtering
- DNS Filtering
- IPS Control
- Malware Protection
- URL Filtering
With Traffic Capture for Network Detection and Response (NDR), you can capture traffic as PCAPNG files with the Traffic Capture policy (Policy > Traffic Capture). To learn more, see [About Traffic Capture Policy](/zia/about-traffic-capture-policy).
The Traffic Capture settings provide the following benefits and enable you to:
- Save time and effort by integrating Zscaler Traffic Capture Essentials directly into ZIA policies.
- Reduce the storage footprint of captured traffic data with granular control over sampling, the storage limit, and the type of traffic captured at the policy level.
- Keep capture data secure and limited to those who have the necessary administrative privileges.
- Limit exposure of personal identifying information (PII) with information obfuscation for Traffic Capture for NDR.
About the Traffic Capture Settings Page
On the Traffic Capture Settings page (Administration > Traffic Capture), you can do the following:
- [Enable Traffic Capture](/zia/configuring-traffic-capture). This enables both Traffic Capture Essentials and Traffic Capture for NDR.
- Connect or manage an Amazon S3 storage bucket. For the settings, you can see:
- **AWS Access ID**: The ID associated with your connected S3 bucket.
- **AWS Secret Key**: The password associated with your connected S3 bucket.
- **S3 Folder URL**: The URL associated with your connected S3 bucket.
- **HTTP Headers**: Optional strings that add metadata to the Amazon S3 REST request:
- **Key**: The case-sensitive name of the HTTP header.
- **Value**: The parameters for the HTTP header.
- Edit limits for Traffic Capture Essentials:
- **Storage Limit**: The maximum amount of data to be kept in the file when a policy configured for Traffic Capture Essentials triggers.
- **Sampling**: The percentage of traffic that is sampled for capturing when Traffic Capture Essentials is triggered.
- Obfuscate information in Traffic Capture for NDR data:
- **User Names**: Choose whether the username is **Visible** or **Obfuscated** in created PCAPNG files.
- **Devices**: Choose whether the device name is **Visible** or **Obfuscated **in created PCAPNG files.
- Save and [activate your changes](/zia/saving-and-activating-changes-zia-admin-portal) or cancel.
![The Traffic Capture Settings show AWS S3 settings and limits for event-based Traffic Capture](/downloads/zia/traffic-forwarding/traffic-capture/about-traffic-capture/ZIA-about-traffic-capture-settings-page.png)