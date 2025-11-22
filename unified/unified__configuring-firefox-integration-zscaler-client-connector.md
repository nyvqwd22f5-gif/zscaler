# Configuring Firefox Integration for Zscaler Client Connector
Source: https://help.zscaler.com/unified/configuring-firefox-integration-zscaler-client-connector
PDF: https://help.zscaler.com/pdf/com/en/1496126.pdf

You can enable or disable Firefox integration for Zscaler Client Connector. If enabled, Zscaler Client Connector attempts to configure Firefox automatically to follow Zscaler settings for macOS and Windows devices by enabling the "Use system proxy settings" feature in Firefox. If disabled, Zscaler Client Connector ignores Firefox and does not overwrite or create any configurations.
When enabled, Zscaler Client Connector overrides the Firefox proxy settings and prevents the user from changing them. Firefox integration does not support Mozilla Developer Preview or Firefox downloaded from the Microsoft Store.
To configure Firefox integration:
- In the Admin Portal, go to **Infrastructure > Connectors > Client > Endpoint Configuration**.
- On the **Endpoint Integration **tab, select **Enable Firefox Integration**.
![The Enable Firefox Integration switch in the Zscaler Client Connector Portal](/downloads/z-app/configuring-policy-and-administration-settings/zscaler-app-support-settings/endpoint-integration/configuring-firefox-integration-zscaler-client-connector/zscaler-client-connector-endpoint-int-firefox.png)
If you disable **Enable Firefox Integration**, ensure to add Zscaler proxy settings to your Firefox configuration.
- Click **Save**.
If you choose not to use Firefox integration for Zscaler Client Connector, then you must manually install the appropriate signing certificates from Firefox.