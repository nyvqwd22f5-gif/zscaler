# About the Log Streaming Service
Source: https://help.zscaler.com/unified/about-log-streaming-service
PDF: https://help.zscaler.com/pdf/com/en/1495091.pdf

The Log Streaming Service (LSS) provides a better understanding of the information coming from the Private Applications service by allowing you to create log receivers that receive information about App Connectors and users.
The LSS provides the following benefits and enables you to:
- Forward your diagnostics and status logs to a SIEM.
- Store logs for longer than the cloud retention period.
- Create analytical charts and graphs using your own in-house SIEM.
- Create events and alerts using third-party log correlation.
Zscaler retains User Activity, User Status, and App Connector log information for rolling periods of at least 14 days during the subscription term. Zscaler retains Audit log information for at least 6-month periods during the subscription term. For access to logs beyond the 14 days they are available in the Admin Portal, setting up the LSS is necessary.
LSS is deployed using two components: a log receiver and a App Connector for Private Applications. LSS resides in Private Applications and initiates a log stream through a Public Service Edge. The App Connector resides in your company's enterprise environment. It receives the log stream and then forwards it to a log receiver.
Zscaler supports third-party SIEM integrations for the LSS. To learn more, see the [Private Applications and Splunk Deployment Guide](/unified/private-applications-and-splunk-deployment-guide) and [Zscaler and Splunk Deployment Guide](/zscaler-technology-partners/zscaler-and-splunk-deployment-guide).
While the LSS is used to capture log data about App Connectors and users in Private Applications (ZPA) using a log receiver, the Nanolog Streaming Service (NSS) resides in Internet & SaaS (ZIA) and allows streaming of traffic logs from the Zscaler Nanolog to your SIEM. To learn more, see [Understanding the Nanolog Streaming Service](/unified/understanding-nanolog-streaming-service).
![Log Streaming Service Deployment](/downloads/zpa/documentation-knowledgebase/log-streaming-service/about-log-streaming/ZPA-LSS-Diagram.png)
Your App Connectors must be deployed prior to [configuring a log receiver](/unified/configuring-log-receiver). To learn more, see the [App Connector Deployment Guides for Supported Platforms](/unified/networking/private-applications/app-connector-management/app-connector-deployment-guides-supported-platforms).
[]It is possible to use mutual TLS encryption between the log receiver and the App Connector, which you can enable when [configuring a log receiver](/unified/configuring-log-receiver). LSS traffic only occurs between the App Connector and the log receiver after mutual authentication is established. This requires them to exchange certificates. The App Connector trusts a certificate signed by a public root certificate authority (CA) in addition to certificates signed privately by a custom CA, which it gets automatically when the App Connector is [deployed](/unified/networking/private-applications/app-connector-management/app-connector-deployment-guides-supported-platforms). The log receiver must have a certificate signed by a public root certificate authority (CA).
To use TLS encryption, you must meet the requirements to ensure successful communication:
- Log receiver:
- Supports TLS communication.
- Has a client certificate for mutual TLS encryption that uses a public root CA.
App Connectors trust certificates that are signed by a public or custom root CA.
- Validates the chain of trust to the App Connector’s [enrollment certificate](/unified/about-enrollment-ca-certificates). One way to enable the log receiver to validate the chain of trust is to add the App Connector’s enrollment certificate in the log receiver’s certificate trust store.
- App Connector: Automatically receives a root certificate during deployment. The App Connector is designed to trust log receiver certificates that are either signed by the global public root CAs, or signed by custom root CAs that are used as the App Connector's enrollment certificate.
A log receiver can capture the following log types:
- AppProtection: Information related to AppProtection policy activity in your organization. To learn more, see [About AppProtection Log Fields](/unified/about-appprotection-log-fields).
- Audit Logs: Session information for all admins accessing the Admin Portal. To learn more, see [About Audit Log Fields](/unified/about-audit-log-fields) and [About Private Access Audit Logs](/unified/about-private-access-audit-logs).
- App Connector Metrics: Information related to an App Connector's metrics. To learn more, see [About App Connector Metrics Log Fields](/unified/about-app-connector-metrics-log-fields).
- App Connector Status: Information related to an App Connector's availability and connection to Private Applications. To learn more, see [About App Connector Status Log Fields](/unified/about-app-connector-status-log-fields).
- Browser Access Logs: HTTP log information related to Browser Access. To learn more, see [About Browser Access Log Fields](/zpa/about-browser-access-log-fields) and [About Browser Access](/unified/about-browser-access).
- Private Cloud Controller Metrics: Information related to a Private Cloud Controller’s metrics. To learn more, see [About Private Cloud Controller Metrics Log Fields](/unified/understanding-private-cloud-controller-metrics-log-fields).
- Private Cloud Controller Status: Information related to a Private Cloud Controller’s availability and connection to Private Applications. To learn more, see [About Private Cloud Controller Status Log Fields](/unified/understanding-private-cloud-controller-status-log-fields).
- Private Service Edge Metrics: Information related to a Private Service Edge's for Private Applications metrics. To learn more, see [About Private Service Edge Metrics Log Fields](/unified/about-private-service-edge-metrics-log-fields).
- Private Service Edge Status: Information related to a Private Service Edge's availability and connection to Private Applications. To learn more, see [About Private Service Edge Status Log Fields](/unified/about-private-service-edge-status-log-fields).
- User Activity: Information on end user requests to Applications. To learn more, see [About User Activity Log Fields](/unified/about-user-activity-log-fields).
- User Status: Information related to an end user's availability and connection to Private Applications. To learn more, see [About User Status Log Fields](/unified/about-user-status-log-fields).
After you select which log type to capture, you can configure a streaming policy for the information.
The LSS does not transmit any log data generated during a connection loss between Private Applications and the App Connectors. After the connection is restored, it can retransmit the last 15 minutes of the log data. However, the delivery of that log data is not guaranteed. With the exception of Audit Log data, the LSS does not transmit any log data generated during a connection loss between the App Connector and the SIEM.
About the Log Receivers Page
[]On the Log Receivers page (Logs > Log Streaming > Log Receivers), you can do the following:
- View a list of applied filters available from the current and previous user sessions. Applied filters must be saved to the user session first before they can be viewed. Use the drop-down menu to select the applied filters to view.
- Hide the filters on the page by clicking **Hide Filters**. Click **Show Filters** to display the filters.
- Refresh the Log Receivers page to reflect the most current information.
- Filter the information that appears in the table. By default, no filters are applied. You can also save applied filters to your preferences so that they're visible in future user sessions.
- [Add a new log receiver](/unified/configuring-log-receiver).
- Expand all of the rows in the table to see more information about each log receiver.
- View a list of all log receivers that are configured for your organization. For each receiver, you can see:
- **Name**: The name of the receiver.
- **Domain Name or IP Address**: The domain name or IP address for the receiver.
- **TCP Port**: The TCP port number for the receiver.
- **TLS Encryption**: Indicates that TLS encryption is enabled or disabled for the receiver.
- **Log Type**: The log type the receiver is capturing (i.e., **User Activity**, **User Status**, **App Connector Status**, **Browser Access**).
- [Copy a log receiver's configuration](/unified/configuring-log-receiver) and use it to create a new configuration.
- [Edit an existing log receiver](/unified/configuring-log-receiver).
-
Delete a log receiver.
If a log receiver is configured using Zscaler Deception, then the copy, edit, and delete options are unavailable.
- Modify the columns displayed in the table.
- Display more rows or a different page of the table.
- Go to the [App Connector Groups](/zpa/about-connectorgroups) page to view and configure the App Connector groups that are specifically associated with your log receivers.