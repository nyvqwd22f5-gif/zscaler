# Configuring the Port for Zscaler Client Connector to Listen On
Source: https://help.zscaler.com/unified/configuring-port-zscaler-client-connector-listen
PDF: https://help.zscaler.com/pdf/com/en/1496276.pdf

By default, Zscaler Client Connector listens on port 9000 via a TCP protocol. Zscaler Client Connector automatically listens to the next port if another application is listening to port 9000. However, if Zscaler Client Connector starts before the other application and begins listening on port 9000, the other application can fail.
In order to avoid port conflicts with other applications, you can configure the port for Zscaler Client Connector to listen on.
You must configure any local proxy PAC file to point to the configured port.
To configure the port:
- In the Admin Portal, go to **Infrastructure > Connectors > Client > Endpoint Configuration**.
- In the **Zscaler Client Connector Listening Port **field, enter the number for any port ranging from 1024 to 65534.
![The Zscaler Client Connector Listening Port option](/downloads/z-app/configuring-policy-and-administration-settings/zscaler-app-support-settings/endpoint-integration/configuring-port-zscaler-app-listen/Zscaler-App-Endpoint-Integration-Listening-Port.png?1602138035)
- Click **Save**.
When a device enrolls and downloads the policy, the listening port is downloaded. Zscaler Client Connector listens to this port the next time Zscaler Client Connector, the Zscaler service, or the device itself restarts. Zscaler Client Connector does not switch ports while it is running.