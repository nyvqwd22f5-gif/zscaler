# Configuring Traffic Capture
Source: https://help.zscaler.com/unified/configuring-traffic-capture
PDF: https://help.zscaler.com/pdf/com/en/1495046.pdf

Certain policies can be configured to capture traffic that matches policy criteria, content scan signature, or any other detection logic for later analysis. To learn more, see [About Traffic Capture](/unified/about-traffic-capture). Captured traffic is stored in an Amazon S3 bucket. Your organization must have an S3 bucket configured to store traffic capture data. To learn more about Amazon S3, refer to the [Amazon S3 documentation](https://docs.aws.amazon.com/AmazonS3/latest/userguide/Welcome.html).
To configure Traffic Capture:
- On the Traffic Capture Settings page, click **Enable Traffic Capture**.
-
In the AWS S3 Settings section, enter the necessary information to connect your organization's S3 bucket to Zscaler. After you have entered the information, you can click **Test Connection **to verify the status of the connection.
[See image.](#AWS-S3-settings)
-
In the Per Occurrence Limits section, you can specify the storage limit and sampling rate for each instance when traffic capture occurs.
[See image.](#per-occurrence-limits)
- Click **Save**.
- For the following policies that allow Traffic Capture, you can enable the **Capture **option:
- [Advanced Threat Protection](/unified/configuring-advanced-threat-protection-policy)
- [File Type Control](/unified/configuring-file-type-control-policy)
- [Firewall Filtering](/unified/configuring-firewall-filtering-policy)
- [DNS Filtering](/unified/configuring-dns-control-policy)
- [IPS Control](/unified/configuring-ips-control-policy)
- [Malware Protection](/unified/configuring-malware-protection-policy)
- [URL Filtering](/unified/configuring-url-filtering-policy)
- Click **Save **and activate the change.
[]![Image of the AWS S3 settings](/downloads/zia/traffic-forwarding/traffic-capture/configuring-traffic-capture/aws-s3-settings.png)
[]![Image of the Per Occurrence Limits settings](/downloads/zia/traffic-forwarding/traffic-capture/configuring-traffic-capture/per-occurrence-limits.png)