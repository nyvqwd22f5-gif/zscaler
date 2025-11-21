# Adding NSS Feeds for Alerts
Source: https://help.zscaler.com/zia/adding-nss-feeds-alerts
PDF: https://help.zscaler.com/pdf/com/en/1399091.pdf

You can configure a separate feed for alerts, so you can monitor the Nanolog Streaming Service (NSS). You can select the level at which alerts are sent: Critical, Warn, or both. You can select multiple alert levels.
To configure an NSS feed for alerts:
- Go to **Administration **>** Nanolog Streaming Service**.
-
In the **NSS Feeds** tab, click **Add NSS Feed**.
The **Add NSS Feed** window appears.
- In the** Add NSS Feed** window:
- **Feed Name**:** **Enter or edit the name of the feed. Each feed is a connection between the NSS and your security information and event management (SIEM) system.
- **NSS Type**:** **Select which type of feed you are configuring. **NSS for Web** is selected by default.
- **NSS Server**:** **Select an NSS server from the list. A [configured NSS server](/zia/adding-nss-servers) is required to add an NSS feed.
- **Status**: The NSS feed is** Enabled** by default. Click **Disabled** if you want to activate it at a later time.
- **SIEM Destination Type**: Select the type of destination:
- **SIEM IP Address**:** **Enter the IP address of the SIEM to which the logs are streamed.
- **FQDN**: Enter the destination for the TCP connection to which the logs are streamed. This allows failover from one IP to the other without manual intervention, but rather relying on updating the DNS entry. The NSS re-resolves the FQDN only when the existing connection goes down. This feature cannot be used for DNS-based load balancing.
- **SIEM TCP Port**: Enter the port number of the SIEM to which the logs are streamed. Ensure that the SIEM is configured to accept the feed from the NSS.
- **SIEM Rate**: Leave as **Unlimited**, unless you need to throttle the output stream due to licensing or other constraints.
- **SIEM Rate Limit (Events per Second)**: This is only applicable if you selected **Limited** under SIEM Rate. Enter an appropriate rate limit for the events per second that you want streamed to your SIEM. This number must be between 100 and 1,000,000. A limit that is too low for the traffic volume causes log loss.
- **Log Type**:** **Choose **Alert**.
- **Time Zone**: By default, this is set to the organization's time zone. The time zone you set applies to the time field in the output file. The time zone automatically adjusts to changes in daylight savings in the specific time zone. The configured time zone can be output to the logs as a separate field. The list of time zones is derived from the IANA Time Zone database. Direct GMT offsets can also be specified.
- **Duplicate Logs**: To ensure that no logs are skipped during downtime, specify the number of minutes that the NSS sends duplicate logs. Zscaler recommends setting the number to 5 minutes, or more if required. This allows the NSS to send up to 60 minutes (one hour) of logs to the SIEM after the connection is restored. To learn more, see [General Guidelines for NSS Feeds and Feed Formats](/zia/general-guidelines-nss-feeds-and-feed-formats#duplicate-logs-example).
- Select at which levels alerts are sent: **Critical**,** Warn**,** **or both. You can select multiple alert levels.
- Click **Save** and [activate the change](/zia/saving-and-activating-changes-admin-portal).
Sending Alerts
The service sends the alerts in [RFC 3164 The BSD syslog Protocol](https://tools.ietf.org/html/rfc3164) format to the specified IP address and port. The table lists the alerts that are sent for each level.
-
-
-
| Warning | Critical |
| ------- | -------- |
| The connection to the SIEM is down | Memory is low |
| The connection to the Zscaler Central Authority (CA) is down | Disk space is low |
| The connection to the Nanolog is down | The connection between the NSS and the SIEM is poor. The NSS can drop some logs if connectivity doesn't improve.The CPU utilization is highMemory swap is high |
Sending Warnings
An alert is sent if the SIEM-to-NSS connection is down for 5 minutes. After that, an alert is generated every 30 minutes to say the connection is down. The alert is generated if the NSS to CA / Nanolog connection is down for 30 minutes, and an alert is generated every 1 hour after that.
If the CPU utilization is more than 85% for 3 minutes, a warning alert is sent. If the CPU utilization is more than 95% for 1 minute, then a critical alert is sent.
If the swap memory utilization is more than 30%, a warning alert is sent. If the utilization is more than 70%, a critical alert is sent.