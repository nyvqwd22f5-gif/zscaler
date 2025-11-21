# Adding NSS Feeds for Event Logs
Source: https://help.zscaler.com/unified/adding-nss-feeds-event-logs
PDF: https://help.zscaler.com/pdf/com/en/1519531.pdf

You can configure up to 16 NSS feeds to specify the data from the Event logs that the NSS sends to the SIEM. For each feed, you can configure multiple types of filters. Numerous filters or complex filters, such as string searches, can impact the performance of the NSS.
To configure a feed for Event logs:
- Go to **Infrastructure **>** Connectors > Cloud > Nanolog Streaming Service**.
- On the **NSS Feeds** tab, select **Add NSS Feed**.
[See image.](#AddNSSFeed)
[]![Dialog for adding an NSS feed](/downloads/unified/infrastructure/cloud-branch-connector/nanolog-streaming-service/nss-feeds/adding-nss-feeds/adding-nss-feeds-event-logs/Add%20NSS%20feed%20eventsmetrics.png)
- In the** Add NSS Feed** window:
- **Feed Name**:** **Enter the name of the feed. Each feed is a connection between NSS and your SIEM.
- **NSS Type**: The NSS type is set to **NSS for Firewall, Cloud and Branch Connector **by default.
- **NSS Server**:** **Select an NSS server from the list.
- **Status**: The status is** Enabled** by default. Click **Disabled** if you want to activate it at a later time.
- **SIEM Destination Type**: The type of destination.
- **SIEM IP Address**:** **Enter the IP address of the SIEM to which the logs are streamed.
- **FQDN**: Enter the destination for the TCP connection to which the logs are streamed. This allows failover from one IP to the other without manual intervention, but without relying on updating the DNS entry. The NSS re-resolves the FQDN only when the existing connection goes down. You cannot use this feature for DNS-based load balancing.
- **SIEM TCP Port**: Enter the port number of the SIEM to which the logs are streamed. Ensure that the SIEM is configured to accept the feed from the NSS.
- **SIEM Rate**: The SIEM rate** **set to **Unlimited** by default. Select **Limited **if** **you need to control the output stream due to SIEM licensing or other constraints.
- **Log Type**: Select **Event**.
- **Feed Output Type**:** **The output is a comma-separated values (**CSV**) list by default. You can also select **Custom**, **JSON**, **Name Value Pairs**, or **Tab Separated** if your SIEM accepts any of these formats.
- **Feed Escape Character**: (Optional) Type a character that you want to hex encode when it appears in a URL, hostname, or referrer URL. For example, type a comma (`,`) to encode it as `%2C`. This is useful if you are using this character as your delimiter and want to ensure it does not cause erroneous delimitation. If custom encoding was done for a record, the `%s{eedone}` field displays **YES** for that record.
- **Feed Output Format**: These are the fields that are displayed in the output.
- **Timezone**:** **By default, this is set to the organization's time zone. The time zone you set applies to the time field in the output file. The time zone automatically adjusts to changes in daylight savings in the specific time zone. The configured time zone can be output to the logs as a separate field. The list of time zones is derived from the IANA Time Zone Database. You can also specify direct GMT offsets.
- **Duplicate Logs**: To ensure that no logs are skipped during any downtime, specify the number of minutes that the NSS sends duplicate logs. This is **Disabled** by default.
- **Locations**: Use this filter to limit the logs to specific[ locations](/unified/about-locations-1). To use the search function, enter the location name in the search box and click **Search**. There is no limit on the number of locations that you can select. Locations that are deleted after they are selected appear with a strikethrough line.
- **Cloud/Branch Connector Groups**: Use this filter to limit the logs to specific Cloud or Branch Connector groups.
- **Cloud/Branch Connector VM**: Use this filter to limit the logs to specific Cloud or Branch Connector VMs.
[See image.](#AddNSSFeedwindow)
[][![Add NSS Feed window in the Zscaler Cloud & Branch Connector Admin Portal](/downloads/cloud-branch-connector/nanolog-streaming-service/nss-feeds/adding-nss-feeds/adding-nss-feeds-event-logs/Add%20NSS%20Feed%20window%20Evenets.png)
]
- Click **Save** and [activate the change](/unified/saving-and-activating-changes-admin-portal).