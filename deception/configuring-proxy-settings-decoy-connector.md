# Configuring Proxy Settings for a Decoy Connector
Source: https://help.zscaler.com/deception/configuring-proxy-settings-decoy-connector
PDF: https://help.zscaler.com/pdf/com/en/1531271.pdf

An HTTP proxy is required if the Decoy Connector cannot establish a direct connection with the following hosts via port 443:
- Zscaler Deception Admin Portal
- Aggregator
- ib.smokescreen.io
- rs.smokescreen.io
You must turn off all inspection features for the hosts in the preceding list and also ensure that the proxy provides unfiltered access to TCP port 443 for these destinations.
To configure proxy settings for a Decoy Connector:
- Log in to the Zscaler Deception Recovery Console via the virtual machine (VM) console or SSH.
-
On the recovery console main menu, enter `3` to connect the Decoy Connector to the Deception Admin Portal and then press `Enter`.
[See image.](#config-proxy-option)
- Enter `Yes` to enable proxy.
- Enter `Yes` to configure the Decoy Connector to use a proxy to connect to the Deception Admin Portal.
- Enter the IP address or FQDN for the proxy server.
- Enter the port number to be used to connect to the proxy server.
-
If the proxy server requires credentials, enter a **Proxy Username** and **Proxy Password**. Otherwise, leave these fields blank.
[See image.](#configure-proxy-settings)
- Press `Enter` to save the proxy configuration.
[]![Configure Proxy ](/downloads/deception/product-documentation/settings/topology/appliances/decoy-connector-deployment-guides-supported-platforms/configuring-proxy-settings-decoy-connector/zscaler-deception-config-proxy.png)
[]![Proxy settings](/downloads/deception/product-documentation/settings/topology/appliances/decoy-connector-deployment-guides-supported-platforms/configuring-proxy-settings-decoy-connector/zscaler-deception-config-proxy-details.png)