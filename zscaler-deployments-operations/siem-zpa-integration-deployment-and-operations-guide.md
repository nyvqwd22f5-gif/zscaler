# SIEM and ZPA Integration Deployment and Operations Guide
Source: https://help.zscaler.com/zscaler-deployments-operations/siem-zpa-integration-deployment-and-operations-guide
PDF: https://help.zscaler.com/pdf/com/en/1420081.pdf

This guide describes the benefits of integrating security information and event management (SIEM) with Zscaler Private Access (ZPA) and the steps necessary for configuring ZPA to add SIEM integration to your security posture.
By integrating a SIEM with ZPA, organizations can efficiently collect and analyze log data from ZPA in one place. The Zscaler Log Streaming Service (LSS) sends various data logs to a log receiver. By default, Zscaler retains User Activity, User Status, and App Connector log information for up to 14 days and audit log information for up to 6 months. Both are accessible via the ZPA Admin Portal.
You can access logs beyond these periods by using LSS integrated with a SIEM. To learn more, see [About the Log Streaming Service](/zpa/about-log-streaming-service). To learn how to integrate your SIEM with Zscaler Internet Access (ZIA), see [SIEM and ZIA Integration Deployment and Operations Guide](/zscaler-deployments-operations/siem-zia-integration-deployment-and-operations-guide).
Value of SIEM Integration
Integrating a SIEM with ZPA provides the following benefits:
- Retains logged data for longer than 14 days.
- Retains audit logs for longer than 6 months.
- Uses SIEM analysis capabilities.
Deployment Phase
The deployment phase initially sets up and integrates Zscaler solutions into an existing network infrastructure. During the deployment phase, you configure ZPA to integrate with your SIEM. The following sections discuss the steps to deploy ZPA and SIEM integration.
Prerequisites
For SIEM integration with ZPA, review the following prerequisites:
- Set up App Connectors for your LSS configuration:
- Using a single Connector Group for both user traffic and log streaming is only supported in proof of concept scenarios and should not be used for any production deployments. Zscaler recommends creating dedicated App Connectors for LSS log types.
- You can use the standard App Connector image. To learn more, see [App Connector Deployment Prerequisites](/zpa/connector-deployment-prerequisites).
- (Optional) Enable Transport Layer Security (TLS) encryption between the log receiver and the App Connector when [configuring a log receiver](/zpa/configuring-log-receiver). You should use TLS encryption when the App Connector sends logs across an untrusted network (e.g., when the log receiver is in a public cloud environment):
- It requires a client certificate for mutual TLS encryption that uses a public root Certificate Authority (CA).
- Validate the chain of trust to the App Connector’s enrollment certificate. One way is to add the App Connector’s enrollment certificate to the log receiver’s certificate trust store.
Deployment Steps
The following steps explain how to integrate ZPA and a SIEM system:
- [Create App Connectors](/zpa/connector-deployment-prerequisites) dedicated to log streaming.
- [Add a log receiver](/zpa/configuring-log-receiver) and assign the [App Connector Group](/zpa/about-connector-groups).
- (Optional) [Configure mutual TLS encryption](/zpa/configuring-log-receiver) between the log receiver and the App Connector.
- Select which [log type](/zpa/configuring-log-receiver#Step2) to forward.
- Add a new log receiver configuration for each log you want to forward.
- [Verify the configuration](/zpa/configuring-log-receiver#Step3Review) and check if logs are received.
Considerations
Review the following considerations:
- In production scenarios, dedicate different App Connector Groups for log streaming and user traffic.
- The LSS won’t transmit any log data generated during a connection loss between ZPA and the App Connectors. When the connection is restored, the LSS can retransmit the last 15 minutes of the log data, but delivery isn’t guaranteed. The LSS does not transmit any log data generated during a loss of connection between the App Connector and the SIEM, except for [Audit Log data](/zpa/about-audit-logs).
- Zscaler recommends deploying App Connectors in pairs to ensure continuous availability during software upgrades.
Operations Phase
This section describes common practices used to operate Zscaler solutions when integrated with your environment. You can monitor and tune the ZPA SIEM integration during the operations phase to meet your infrastructure needs.
Common Troubleshooting Items
The following list describes common issues related to ZPA and SIEM operation:
- App Connectors health status check: You can use the [App Connectors page and health dashboard](/zpa/monitoring-connector-performance) to verify the health status because the log collector acts as an App Connector.
- If the SIEM server is not receiving logs from LSS:
- Verify the configuration in the ZPA Admin Portal based on the steps in this guide.
- Verify if the LSS is sending the logs by checking the [diagnostic logs](/zpa/dashboard-diagnostics).
- Check if [LSS encryption in the log receiver settings](/zpa/configuring-log-receiver) uses TLS encryption on traffic between the log streaming service components. The receiving component might not trust the certificate presented for mutual TLS encryption. Disable TLS encryption temporarily and test whether you receive logs in SIEM to validate.
- Follow Zscaler's general [App Connector Troubleshooting](/zpa/troubleshooting-app-connectors) guidelines.
Deployment Checklist
Zscaler recommends downloading the [ZPA SIEM Integration Deployment and Operations Checklist](/downloads/zscaler-deployments-operations/zpa-deployments-operations/siem-zpa-integration-deployment-and-operations-guide/ZPA-SIEM-Integration-Deployment-Operations-Checklist.pdf) to help plan and implement ZPA and SIEM integration: [Download PDF](/downloads/zscaler-deployments-operations/zpa-deployments-operations/siem-zpa-integration-deployment-and-operations-guide/ZPA-SIEM-Integration-Deployment-Operations-Checklist.pdf)
Additional Information
For more SIEM integration information and troubleshooting instructions, see the [Zscaler Support Portal](https://zscaler.my.site.com/customers/s/) and the [Zscaler Zenith Community](http://community.zscaler.com/).