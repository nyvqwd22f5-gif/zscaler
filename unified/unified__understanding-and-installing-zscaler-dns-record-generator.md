# Understanding and Installing the Zscaler DNS Record Generator
Source: https://help.zscaler.com/unified/understanding-and-installing-zscaler-dns-record-generator
PDF: https://help.zscaler.com/pdf/com/en/1496971.pdf

The Zscaler DNS Record Generator creates the DNS TXT records and the public and private keys for disaster recovery. The public key is used to verify the activation of Disaster Recovery Mode. The private key is used to sign the DNS TXT record.
The public key is uploaded on the [Disaster Recovery Settings](/unified/about-disaster-recovery-settings) page and when configuring Zscaler Client Connector Profiles, and is used to trigger Disaster Recovery Mode. This is considered a signed disaster recovery activation. For improved security, Zscaler recommends that the signed DNS TXT records are used with the Zscaler DNS Record Generator.
In the case of an unsigned disaster recovery activation, the public key does not need to be uploaded.
The Zscaler DNS Record Generator creates the DNS TXT records in the correct format. However, you can create the DNS TXT records manually without the Zscaler DNS Record Generator. Zscaler recommends using the Zscaler DNS Record Generator for simplicity.
The DNS TXT records created by the Zscaler DNS Record Generator use a record format similar to the Domain Key Identified Mail (DKIM) record format. Provided are the DNS TXT record tags:
- `v=<1>`: The version of the DNS record.
- `b=<...>`: The body indicates if Disaster Recovery Mode is enabled (`on`) or disabled (`off`), or if Disaster Recovery Test Mode is enabled (`test`).
- `m=<...>`: The Internet & SaaS forwarding profile actions indicate if the traffic is sent directly (`fo`) or if the internet access is disabled (`fc`).
- `t=<...>`: The start time of disaster recovery in Coordinated Universal Time (UTC) seconds. This tag is optional and can be skipped for both signed and unsigned disaster recovery activations.
- `x=<...>`: The end time of disaster recovery in UTC seconds. This tag is optional and can be skipped for both signed and unsigned disaster recovery activations.
- `n=<...>`: The total number of DNS TXT records required for a multiple-part disaster recovery activation (e.g., `n=2`). This is only present for signed DNS TXT records.
- `p=<...>`: The first or second part of the DNS TXT record activation (e.g., `p=2`). This is only present for signed DNS TXT records.
- `bh=<...>`: The body hash indicates the signed hash of tag values (`v`, `d`, `b`, `m` , `t`, and `x`) in RSA-SHA256 and Base64 formats. This is only present for signed DNS TXT records.
Zscaler recommends that the DNS TXT records used to activate disaster recovery must have valid record tags. Invalid `t`, `x`, `n`, `p`, and `bh` tags can result in disaster recovery activation to fail. The Zscaler DNS Record Generator creates DNS TXT records with valid formats and record tags.
The following table lists the format, sample, and supported values for the signed and unsigned DNS TXT records.
-
-
-
-
-
-
-
-
-
-
-
-
-
-
-
-
-
-
-
-
| DNS TXT Record Format | Example DNS TXT Record | Supported Values |
| --------------------- | ---------------------- | ---------------- |
| Signed DNS TXT records are in two parts, and are in the following formats:`v=1;k=zpa|zia|all;b=on|off|test;m=fo|fc;t=<start time>;x=<end time>;n=2;p=1;bh=<first part of hash of all tags before 'n='>``v=1;k=zpa|zia|all;b=on|off|test;m=fo|fc;t=<start time>;x=<end time>;n=2;p=2;bh=<second part of hash of all tags before 'n='>` | `v=1;d=pse.zpa.customer.com;b=on;t=1652153049;x=16521539999;n=2;p=1;bh=TukwDQXnOEqC+HJ0T3MubNs0h6nZHa0QoQpHaOy3wSgKAMnEif7RZZM/ANJ3sMXApph1pRD76WG6FDpIA0LPKV8Z66AP048eog31fXl8UIi5XEqUOHSbc1dK1Artu1PNtJkqQ1mA5VkfAMgaGN3MYTeUkF7KAljyBxquSp9W2+``v=1;b=on;t=1652153049;x=16521539999;n=2;p=2;bh=QyvM59ZYPm/6czwOUR8dOUhiIPEo9+DJvp1uT4myWhDLJblyRaeVXUveE5HzTIba1DReRucylysTIMF1f0JpnD6Y1AD2QLFNgO90jtgfMvRCb7dmbXPWC2ABeKAKTKDXrFWRizXa3N6lozH+eOYvYPcrkDMMxrRVG2J3k3m21EJQ==` | The version (`v`) is 1.The following values are supported for the activation types (`k`):`zia`: Internet & SaaS`zpa`: Private Applications`all`: Both Internet & SaaS and Private ApplicationsThe following values are supported for the body (`b`):`on`: Enable Disaster Recovery Mode`off`: Disable Disaster Recovery Mode`test`: Enable Disaster Recovery Test ModeThe following values are supported for the Internet & SaaS forwarding profile actions (`m`):`fo`: Fail-open, meaning the traffic is sent directly.`fc`: Fail-close, meaning the internet access is disabled.The Internet & SaaS forwarding profile actions (`m`) can be skipped if you do not want to overwrite the Zscaler Client Connector Portal configuration.The UTC start time (`t`) and end time (`x`) are in seconds and can be skipped for both signed and unsigned disaster recovery activations if the specific start and end times for activation are not needed.The total number of DNS TXT records required for the multiple-part disaster recovery activation (`n`) supports integers. For example: `n=2`.The message part index (`p`) indicates the expected number of DNS TXT record message parts in a multiple-part disaster recovery activation. Signed activation requires two parts of the disaster recovery activation TXT records. The first TXT record includes the record index value (e.g., `p=1`). The second TXT record includes the record index value (e.g., `p=2`).The body hash (`bh`) value is in Base64 format (2048-bit keys signed with the RSA-SHA256 algorithm) and is obtained by concatenating the hash subparts in order.For example, the first `bh` value `TukwDQXnOEqC+HJ0T3MubNs0h6nZHa0QoQpHaOy3wSgKAMnEif7RZZM/ANJ3sMXApph1pRD76WG6FDpIA0LPKV8Z66AP048eog31fXl8UIi5XEqUOHSbc1dK1Artu1PNtJkqQ1mA5VkfAMgaGN3MYTeUkF7KAljyBxquSp9W2+` is combined or concatenated with `QyvM59ZYPm/6czwOUR8dOUhiIPEo9+DJvp1uT4myWhDLJblyRaeVXUveE5HzTIba1DReRucylysTIMF1f0JpnD6Y1AD2QLFNgO90jtgfMvRCb7dmbXPWC2ABeKAKTKDXrFWRizXa3N6lozH+eOYvYPcrkDMMxrRVG2J3k3m21EJQ==`.The `v`, `b`, `t`, `x`, and `n` tags must match across different DNS TXT records for their `bh` tag values to be combined or concatenated for a valid disaster recovery activation. |
| Unsigned DNS TXT records are in the following format:`v=1;b=on|off|test;t=<start time>;x=<end time>` | `v=1;k=zpa;b=on;m=fo` | The version (`v`) is 1.The following values are supported for the activation types (`k`):`zia`: Internet & SaaS`zpa`: Private Applications`all`: Both Internet & SaaS and Private ApplicationsThe following values are supported for the body (`b`):`on`: Enable Disaster Recovery Mode`off`: Disable Disaster Recovery Mode`test`: Enable Disaster Recovery Test ModeThe following values are supported for the Internet & SaaS forwarding profile actions (`m`):`fo`: Fail-open, meaning the traffic is sent directly.`fc`: Fail-close, meaning the internet access is disabled.The Internet & SaaS forwarding profile actions (`m`) can be skipped if you do not want to overwrite the Zscaler Client Connector Portal configuration.The UTC start time (`t`) and end time (`x`) are in seconds and can be skipped for both signed and unsigned disaster recovery activations if the specific start and end times for activation are not needed.. A given tag is not shown if it does not have a value.For example, a simple unsigned DNS TXT record is `v=1;k=zpa;b=on;m=wf` if start time (`t`) or end time (`x`) is not entered. |
[]Installation
To install the Zscaler DNS Record Generator:
- Go to the **Disaster Recovery **page (Infrastructure > Private Access > Business Continuity> Disaster Recovery).
- Click **Download DNS Record Generator**.
[See image.](#dnsRecordGenerator)
The Zscaler DNS Record Generator is only supported for Windows OS devices.
- Open the installer and click **Next**.
- Select the checkbox to confirm that you have accepted the terms in the License Agreement, and then click **Next**.
- (Optional) Click **Change…** to specify where the Zscaler DNS Record Generator is installed. Select the destination and click **OK**.
- Click **Next**.
- Click **Install**.
- Click **Finish**.
After the Zscaler DNS Record Generator is installed, you can proceed to [create the DNS TXT records](/unified/creating-dns-txt-records) used to activate disaster recovery.
[]![Downloading the DNS Record Generator ](/downloads/zpa/administration/disaster-recovery-administration/understanding-and-installing-zscaler-dns-record-generator/zpa-dns-record-generator.png)