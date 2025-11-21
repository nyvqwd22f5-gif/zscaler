# Configuring Dedicated Proxy Ports
Source: https://help.zscaler.com/unified/configuring-dedicated-proxy-ports-0
PDF: https://help.zscaler.com/pdf/com/en/1496346.pdf

You can use and manage dedicated proxy ports in the Admin Portal. To learn more about dedicated proxy ports for the Zscaler service, see [Configuring Dedicated Proxy Ports](/unified/configuring-dedicated-proxy-ports).
- In the Admin Portal, go to **Infrastructure > Connectors > Client > Dedicated Proxy Port**.
- Enable **Dedicated Proxy Port**.
- Select an available port from the **Select Dedicated Proxy Port** drop-down menu. Zscaler Client Connector attempts connections with this port before using the following ports in this order: 443, 80, or 8080.
![Enable the dedicated proxy port setting and select a port](/downloads/z-app/policy-administration-settings/about-dedicated-proxy-ports/dpp-config_0.png)
- Click **Save**.