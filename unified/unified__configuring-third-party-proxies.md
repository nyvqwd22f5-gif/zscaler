# Configuring Third-Party Proxies
Source: https://help.zscaler.com/unified/configuring-third-party-proxies
PDF: https://help.zscaler.com/pdf/com/en/1497736.pdf

You can configure proxy objects using the IP address or FQDN of a third-party proxy service to which you want to forward the traffic using the [Third-Party Proxy Chaining](/unified/understanding-third-party-proxy-chaining) feature.
To configure a proxy:
- Go to **Infrastructure** >** Internet & SaaS > Network Policies > Proxies and Gateways **page.
- Select the **Proxies** tab.
- Click **Add Proxy**. The **Add Proxy** window appears.
- In the **Add Proxy** window:
- **Proxy Name**:** **Enter a user-friendly name for the third-party proxy that you are defining.
- **IP Address/FQDN**:** **Enter the IP address or the FQDN of the third-party proxy service.
- **Port**: Enter the port number on which the third-party proxy service listens to the requests forwarded from Zscaler.
- **Root Certificate**: (Optional) Select the root certificate used by the third-party proxy to perform SSL inspection. This root certificate is used by Zscaler to validate the SSL leaf certificates signed by the upstream proxy. The required root certificate appears in this drop-down list only if it is uploaded from the **Infrastructure** >** Internet & SaaS > Network Policies > Root Certificates** page. To learn more, see [Adding Third-Party SSL Root Certificates](/unified/about-root-certificates).
- **Description**: (Optional) Enter additional notes or information. The description cannot exceed 256 characters.
- Click **Save** and activate the change.
You can configure up to eight proxy objects.