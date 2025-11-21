# Adding Cloud NSS Feeds for Tunnel Logs
Source: https://help.zscaler.com/zia/adding-cloud-nss-feeds-tunnel-logs
PDF: https://help.zscaler.com/pdf/com/en/1402061.pdf

To configure a Cloud NSS feed for tunnel logs:
- Go to **Administration **>** Nanolog Streaming Service**.
-
From the **Cloud** **NSS Feeds** tab, click **Add Cloud NSS Feed**.
The **Add Cloud NSS Feed** window appears.
- In the **Add Cloud NSS Feed** window:
- **Feed Name**: Enter or edit the name of the feed. Each feed is a connection between the NSS and your SIEM.
- **NSS Type**: **NSS for Web** is selected by default.
- **Status**:** **The NSS feed is **Enabled** by default. Choose **Disabled** if you want to activate it at a later time.
- **SIEM Rate**: Leave as **Unlimited**, unless you need to throttle the output stream due to licensing or other constraints.
- **SIEM Rate Limit (Events per Second)**: This is only applicable if you selected **Limited** under SIEM Rate. Enter an appropriate rate limit for the events per second that you want streamed to your SIEM. This number must be between 100 and 1,000,000. A limit that is too low for the traffic volume causes log loss.
- **SIEM Type**: Choose a SIEM type from the list.
- **OAuth 2.0 Authentication**: This setting is enabled by default if it is applicable to the SIEM type.
- **Max Batch Size**: Enter a size limit for an individual HTTP request payload to the SIEM's best practice.
-
**API URL**: Enter the HTTP/S URL of the SIEM log collection API endpoint.
The HTTPS URL must be configured with a publicly trusted SSL certificate. Self-signed or internally issued certificates do not pass the SIEM connectivity test.
- **HTTP Headers**: Enter HTTP header information:
- **Key 1**: Enter the key for the HTTP header.
- **Value 1**: Enter the token value for the HTTP header.
- **Add HTTP Header**: Click to add more HTTP headers (keys and values).
- **Log Type**:** **Choose **Tunnel**.
- **Record Type**: Specify the tunnel log record types to send in the single NSS Feed:
- **IKE Phase 1**: Details for IPSec Phase 1 negotiation (applies to IPSec only)
- **IKE Phase 2**: Details for IPSec Phase 2 negotiation (applies to IPSec only)
- **Sample**: Statistics collected in 60-second sample windows (applies to both GRE and IPSec)
- **Tunnel Event**: Status change events (applies to both GRE and IPSec)
-
**Feed Output Type**:** **The output is **JSON** by default. Choose **Tab-separated **to create a tab-separated list. Choose **Custom **to use a different delimiter, such as a dash, and enter the delimiter when you specify the feed output format. This menu also lists feed output types for specific SIEMs.
If you select **JSON** as the **Feed Output Type**, special characters such as `\` present in string fields may cause a parsing issue for your SIEM. To prevent the issue, enter `,\"` as the **Feed Escape Character** and use hex encoded fields (e.g., `%s{elogin}`instead of `%s{login}`) in the **Feed Output Format**`.`
- **JSON Array Notation**: When **JSON** is selected, the **JSON Array Notation** setting is enabled by default. This setting allows the NSS to stream a batch of logs in a JSON Array format: Individual logs are ordered in a list, separated by commas, and surrounded by square brackets (e.g., [\{JSON1},\{JSON2}]). You can disable this setting.
- **Time Zone**:** **By default, this is set to the organization's time zone. The time zone you set applies to the time field in the output file. The time zone automatically adjusts to changes in daylight savings in the specific time zone. The configured time zone can be output to the logs as a separate field. The list of time zones is derived from the IANA Time Zone database. Direct GMT offsets can also be specified.
- **Feed Output Format**:** **These are the fields that are displayed in the output. You can edit the default list, and if you choose **Custom **as the **Feed Output Type**, change the delimiter as well. See [NSS Feed Output Format: Tunnel Logs](/zia/nss-feed-output-format-tunnel-logs) for information about the available fields and their syntax.
- Define the filters:
- **Tunnel Type**: You can limit the logs based on the tunnel types:
- **Extranet**: IPSec tunnels that connect a business partner’s data center to the Zscaler service. The partner (i.e., Extranet Resource) establishes the connection to Zscaler. To learn more, see [About Extranet](/zia/about-extranet).
- **GRE**: Generic Routing Encapsulation tunnels.
- **IPSec IKEv1**: IPSec tunnels that use the Internet Key Exchange Version 1 negotiation process.
- **IPSec IKEv2**: IPSec tunnels that use the Internet Key Exchange Version 2 negotiation process.
- **Z-Tunnel 2.0**: Tunnel that uses DTLS, TLS, or UDP to send packets to the Zscaler service. Note that only Zscaler Cloud Connector supports UDP.
- **Location**: Use this filter to limit the logs to specific locations from which transactions were generated. You can search for locations. There is no limit on the number of locations that you can select. Locations that are deleted after they are selected appear with a strikethrough line.
- **VPN Credentials**: For IPSec tunnels, you can limit the logs to specific tunnel VPN credentials. You can search for VPN credentials. There is no limit to the number of VPN credentials that you can select. VPN credentials that are deleted after they are selected appear with a strikethrough line.
-
**Source IPs**: You can limit the logs based on the tunnel's source IP address. You can enter:
- An IP address (e.g., 198.51.100.100)
- A range of IP addresses (e.g., 192.0.2.1-192.0.2.10)
- An IP address with a netmask (e.g., 203.0.113.0/24)
You can enter multiple entries. Press `Enter` after each entry, then click **Add Items**. For item lists, you can view up to 500 items on a page; filter the list by searching for a word, phrase, or number contained in an item; and remove all items from the list (**Remove All**) or only items from a specific page (**Remove Page**). If you select **Remove All** or **Remove Page**, a confirmation window appears.
-
**Destination VIPs**:** **You can limit the logs based on the tunnel's destination VIP address. You can enter:
- An IP address (e.g., 198.51.100.100)
- A range of IP addresses (e.g., 192.0.2.1-192.0.2.10)
- An IP address with a netmask (e.g., 203.0.113.0/24)
You can enter multiple entries. Press `Enter` after each entry, then click **Add Items**. For item lists, you can view up to 500 items on a page; filter the list by searching for a word, phrase, or number contained in an item; and remove all items from the list (**Remove All**) or only items from a specific page (**Remove Page**). If you select **Remove All** or **Remove Page**, a confirmation window appears.
-
**Tunnel Source Port**:** **You can limit the logs based on the tunnel's source ports. You can specify individual ports or a range of ports (e.g., 1-65535).
You can enter multiple entries. Press `Enter` after each entry, then click **Add Items**. For item lists, you can view up to 500 items on a page; filter the list by searching for a word, phrase, or number contained in an item; and remove all items from the list (**Remove All**) or only items from a specific page (**Remove Page**). If you select **Remove All** or **Remove Page**, a confirmation window appears.
- Click **Save** and [activate the change](/zia/saving-and-activating-changes-admin-portal).