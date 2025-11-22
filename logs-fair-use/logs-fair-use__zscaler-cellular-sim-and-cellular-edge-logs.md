# Zscaler Cellular (SIM and Cellular Edge) Logs
Source: https://help.zscaler.com/logs-fair-use/zscaler-cellular-sim-and-cellular-edge-logs
PDF: https://help.zscaler.com/pdf/com/en/1507366.pdf

In order to provide the Zscaler SIM and Zscaler Cellular Edge services, Zscaler has the right to process, use, reproduce, store, modify, and display the information from logs as defined in this article.
Zscaler Cellular Edge Logs
Zscaler Cellular Edge logs are defined as Session Logs, Tunnel Logs, DNS Logs, and Audit Logs. To learn more, see [About Insights Logs](/cloud-branch-connector/about-insights-logs).
- Session Logs: Traffic flow of information related to the sessions originating from your cloud workloads. To learn more, see [Session Insights Logs: Filters](/cloud-branch-connector/session-insights-logs-filters) and [Session Insights Log: Columns](/cloud-branch-connector/session-insights-logs-columns).
- Tunnel Logs: Information related to the connectivity from the Cellular Edge to the Zscaler cloud. To learn more, see [Tunnel Insights Logs: Filters](/cloud-branch-connector/zia-tunnel-insights-logs-filters) and [Tunnel Insights Logs: Columns](/cloud-branch-connector/tunnel-insights-logs-columns).
- DNS Logs: Information related to the destination domains and the DNS responses for those domains. To learn more, see [DNS Insights Logs: Filters](/cloud-branch-connector/dns-insights-logs-filters) and [DNS Insights Logs: Columns](/cloud-branch-connector/dns-insights-logs-columns).
- Audit Logs: Zscaler Cellular Edge leverages the Cloud & Branch Connector Admin Portal, thus Audit Logs for Zscaler Cellular Edge consist of Activity logs of the configuration changes made via the Cloud & Branch Connector Admin Portal or API for Cloud Connector or Branch Connector. To learn more, see [About Audit Logs](/cloud-branch-connector/about-audit-logs).
Zscaler SIM Logs
Logs for Zscaler SIM services will source information from the mobile network operators used, and include IMSI, IMEI, and CDR information.
These are only applicable to the Zscaler SIM services.
- SIM Event Logs: Whenever a device connects to the Zscaler Cellular Edge, the logging service will receive events like SIM authenticated time, location of the SIM card, network change, etc.
- SIM Data Usage Logs: Usage metrics like bytes transferred and time of usage from the mobile network operator.
Retention Period
Zscaler retains log information for a rolling period of up to 180 days during the subscription term. Zscaler retains audit log information for a rolling period of six months during the subscription term. When the subscription term ends or expires, the logs are deleted by Zscaler according to the applicable retention cycles. You can also view your logs or stream logs in real-time using the Nanolog Streaming Service (NSS).
During the deployment process, you can choose to have the logs stored in either the United States or the European Union.