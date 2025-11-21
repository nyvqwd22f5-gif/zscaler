# Zscaler Client Connector and Charles Proxy Interoperability
Source: https://help.zscaler.com/unified/zscaler-client-connector-and-charles-proxy-interoperability
PDF: https://help.zscaler.com/pdf/com/en/1495631.pdf

On macOS devices, Zscaler Client Connector is interoperable with the Charles Web Debugging Proxy application. If Charles Proxy is detected, Zscaler Client Connector creates a proxy chain. The app automatically configures external proxy settings in the Charles application so that the user's system routes all traffic through the Charles Proxy first, then sends the traffic on to the app.
Keep in mind that if you install the Charles Proxy after installing Zscaler Client Connector, users must restart the Charles Proxy twice after installation, so that Zscaler Client Connector can automatically modify the Charles Proxy configuration for proxy chaining.
If you installed Charles Proxy on a user's device before installing Zscaler Client Connector, Zscaler Client Connector works seamlessly and users do not need to restart the Charles Proxy.