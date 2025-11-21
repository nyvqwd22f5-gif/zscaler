# About the Log Streaming Service
Source: https://help.zscaler.com/zpa/about-log-streaming-service
PDF: https://help.zscaler.com/pdf/com/en/1483941.pdf

[Watch a video about the Log Streaming Service.](https://fast.wistia.net/embed/iframe/fycyoh6xk5)
The Log Streaming Service (LSS) provides a better understanding of the information coming from the ZPA service by allowing you to create log receivers that receive information about App Connectors and users.
The LSS provides the following benefits and enables you to:
- Forward your diagnostics and status logs to a SIEM.
- Store logs for longer than the cloud retention period.
- Create analytical charts and graphs using your own in-house SIEM.
- Create events and alerts using third-party log correlation.
Zscaler retains User Activity, User Status, and App Connector log information for rolling periods of at least 14 days during the subscription term. Zscaler retains Audit log information for at least 6-month periods during the subscription term. For access to logs beyond the 14 days they are available in the ZPA Admin Portal, setting up the LSS is necessary.
LSS is deployed using two components: a log receiver and a ZPA App Connector. LSS resides in ZPA and initiates a log stream through a ZPA Public Service Edge. The App Connector resides in your company's enterprise environment. It receives the log stream and then forwards it to a log receiver.
Zscaler supports third-party SIEM integrations for the LSS. To learn more, see the [ZPA and Splunk Deployment Guide](/zpa/zpa-and-splunk-deployment-guide) and [Zscaler and Splunk Deployment Guide](/zscaler-technology-partners/zscaler-and-splunk-deployment-guide).
While the LSS is used to capture log data about App Connectors and users in ZPA using a log receiver, the Nanolog Streaming Service (NSS) resides in Zscaler Internet Access (ZIA) and allows streaming of traffic logs from the Zscaler Nanolog to your SIEM. To learn more, see [Understanding the Nanolog Streaming Service](/zia/understanding-nanolog-streaming-service).
![Log Streaming Service Deployment](/downloads/zpa/documentation-knowledgebase/log-streaming-service/about-log-streaming/ZPA-LSS-Diagram.png)
Your App Connectors must be deployed prior to [configuring a log receiver](/zpa/configuring-log-receiver). To learn more, see the [App Connector Deployment Guides for Supported Platforms](/zpa/documentation-knowledgebase/connectors-and-connector-groups/connector-deployment-guides-supported-platforms).
[]It is possible to use mutual TLS encryption between the log receiver and the App Connector, which you can enable when [configuring a log receiver](/zpa/configuring-log-receiver). LSS traffic only occurs between the App Connector and the log receiver after mutual authentication is established. This requires them to exchange certificates. The App Connector trusts a certificate signed by a public root certificate authority (CA) in addition to certificates signed privately by a custom CA, which it gets automatically when the App Connector is [deployed](/zpa/app-connector-management/app-connector-deployment-guides-supported-platforms). The log receiver must have a certificate signed by a public root certificate authority (CA).
To use TLS encryption, you must meet the requirements to ensure successful communication:
- Log receiver:
- Supports TLS communication.
- Has a client certificate for mutual TLS encryption that uses a public root CA.
App Connectors trust certificates that are signed by a public or custom root CA.
- Validates the chain of trust to the App Connector’s [enrollment certificate](/zpa/about-enrollment-ca-certificates). One way to enable the log receiver to validate the chain of trust is to add the App Connector’s enrollment certificate in the log receiver’s certificate trust store.
- App Connector: Automatically receives a root certificate during deployment. The App Connector is designed to trust log receiver certificates that are either signed by the global public root CAs, or signed by custom root CAs that are used as the App Connector's enrollment certificate.
A log receiver can capture the following log types:
- AppProtection: Information related to AppProtection policy activity in your organization. To learn more, see [Understanding AppProtection Log Fields](/zpa/understanding-appprotection-log-fields).
- Audit Logs: Session information for all admins accessing the ZPA Admin Portal. To learn more, see [Understanding Audit Log Fields](/zpa/understanding-audit-log-fields) and [About Audit Logs](/zpa/about-audit-logs).
- App Connector Metrics: Information related to an App Connector's metrics. To learn more, see [Understanding App Connector Metrics Log Fields](/zpa/understanding-app-connector-metrics-log-fields).
- App Connector Status: Information related to an App Connector's availability and connection to ZPA. To learn more, see [Understanding App Connector Status Log Fields](/zpa/understanding-connector-status-log-fields).
- Browser Access Logs: HTTP log information related to Browser Access. To learn more, see [Understanding Browser Access Log Fields](/zpa/understanding-browser-access-log-fields) and [About Browser Access](/zpa/about-BrowserAccess).
- Private Cloud Controller Metrics: Information related to a Private Cloud Controller’s metrics. To learn more, see [Understanding Private Cloud Controller Metrics Log Fields](/zpa/understanding-private-cloud-controller-metrics-log-fields).
- Private Cloud Controller Status: Information related to a Private Cloud Controller’s availability and connection to ZPA. To learn more, see [Understanding Private Cloud Controller Status Log Field](/zpa/understanding-private-cloud-controller-status-log-fields)s.
- Private Service Edge Metrics: Information related to a ZPA Private Service Edge's metrics. To learn more, see [Understanding Private Service Edge Metrics Log Fields](/zpa/understanding-private-service-edge-metrics-log-fields).
- Private Service Edge Status: Information related to a ZPA Private Service Edge's availability and connection to ZPA. To learn more, see [Understanding Private Service Edge Status Log Fields](/zpa/understanding-private-service-edge-status-log-fields).
- User Activity: Information on end user requests to Applications. To learn more, see [Understanding User Activity Log Fields](/zpa/understanding-user-activity-log-fields).
- User Status: Information related to an end user's availability and connection to ZPA. To learn more, see [Understanding User Status Log Fields](/zpa/understanding-user-status-log-fields).
- Microsegmentation: Information related to Microsegmentation Flow activity. To learn more, see [Understanding Microsegmentation Flow Log Fields](/zpa/about-microsegmentation-flow-log-fields).
After you select which log type to capture, you can configure a streaming policy for the information.
The LSS does not transmit any log data generated during a connection loss between ZPA and the App Connectors. After the connection is restored, it can retransmit the last 15 minutes of the log data. However, the delivery of that log data is not guaranteed. With the exception of Audit Log data, the LSS does not transmit any log data generated during a connection loss between the App Connector and the SIEM.
About the Log Receivers Page
[]On the Log Receivers page (Configuration & Control > Private Infrastructure > Log Streaming Service > Log Receivers), you can do the following:
- View a list of applied filters available from the current and previous user sessions. Applied filters must be saved to the user session first before they can be viewed. Use the drop-down menu to select the applied filters to view. To learn more, see [Using Tables](/zpa/using-tables#filterData).
- Hide the filters on the page by clicking **Hide Filters**. Click **Show Filters** to display the filters.
- Refresh the Log Receivers page to reflect the most current information.
- Filter the information that appears in the table. By default, no filters are applied. You can also save applied filters to your preferences so that they're visible in future user sessions. To learn more, see [Using Tables](/zpa/using-tables#filterData).
- [Add a new log receiver](/zpa/configuring-log-receiver).
- [Expand all of the rows in the table](/zpa/using-tables#expand) to see more information about each log receiver.
- View a list of all log receivers that are configured for your organization. For each receiver, you can see:
- **Name**: The name of the receiver.
- **Domain Name or IP Address**: The domain name or IP address for the receiver.
- **TCP Port**: The TCP port number for the receiver.
- **TLS Encryption**: Indicates that TLS encryption is enabled or disabled for the receiver.
- **Log Type**: The log type the receiver is capturing (i.e., **User Activity**, **User Status**, **App Connector Status**, **Browser Access**).
- [Copy a log receiver's configuration](/zpa/configuring-log-receiver#CopyLRConfig) and use it to create a new configuration.
- [Edit an existing log receiver](/zpa/configuring-log-receiver#EditLRConfig).
-
Delete a log receiver.
If a log receiver is configured using Zscaler Deception, then the copy, edit, and delete options are unavailable.
- [Modify the columns displayed in the table.](/zpa/using-tables)
- Display more rows or a different page of the table.
- Open the [Zscaler Help Browser](/zpa/using-zscaler-help-browser) and view Help Portal articles without leaving the ZPA Admin Portal.
- Go to the [App Connector Groups](/zpa/about-connectorgroups) page to view and configure the App Connector groups that are specifically associated with your log receivers.
![Viewing and Managing Log Receivers in the ZPA Admin Portal](/downloads/zpa/log-streaming-service/about-log-streaming-service/zpa-log-receivers-page-react.png)