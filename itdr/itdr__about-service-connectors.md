# About Service Connectors
Source: https://help.zscaler.com/itdr/about-service-connectors
PDF: https://help.zscaler.com/pdf/com/en/1531714.pdf

Before integrating Zscaler ITDR with a Security Information and Event Management (SIEM) solution, a Service Connector must be configured. A Service Connector is an application that communicates with the Zscaler ITDR Admin Portal and sends events and audit logs to the SIEM solution. You can integrate a Service Connector with one or multiple SIEM solutions.
Service Connectors provide the following benefits and enable you to:
- Forward the events recorded by Zscaler ITDR to one or more SIEM solutions for real-time analysis of the log data in a centralized view.
- Leverage built-in Service Connectors or configure your own Service Connectors by using the executables provided in the ITDR Admin Portal .
By default, Service Connectors are automatically configured in the ITDR Admin Portal. These Service Connectors are always running and cannot be deleted.
You can configure a Service Connector externally within your organization by downloading the executables (Windows or Linux) from the ITDR Admin Portal.
About the Service Connectors Page
On the Service Connectors page (Orchestrate > Service Connectors), you can do the following:
- View a list of all configured Service Connectors. For each Service Connector, you can see:
- **Name**: The name of the Service Connector.
- **Version**: The current version of the Service Connector.
- **Syslog Receiver Source**: The name of the syslog receiver type that is configured.
- **Syslog Receiver Allowed IPs**: The IP addresses to allow inbound connections from a configured syslog receiver.
- [Configure a Service Connector](/itdr/configuring-service-connector).
- [Edit or delete a Service Connector](/itdr/editing-or-deleting-service-connector).
![About Service Connectors](/downloads/itdr/orchestrate/siem-integrations/about-service-connectors/itdr-about-siem-connector-1.png)