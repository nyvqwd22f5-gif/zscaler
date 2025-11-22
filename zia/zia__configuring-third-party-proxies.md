# Configuring Third-Party Proxies
Source: https://help.zscaler.com/zia/configuring-third-party-proxies
PDF: https://help.zscaler.com/pdf/com/en/1401501.pdf

You can configure proxy objects using the IP address or FQDN of a third-party proxy service to which you want to forward the traffic using the [Third-Party Proxy Chaining](/zia/about-third-party-proxy-chaining) feature.
To configure a proxy:
- Go to **Administration** >** Proxies & Gateways **page.
- Select the **Proxies** tab.
- Click **Add Proxy**. The **Add Proxy** window appears.
- In the **Add Proxy** window:
- **Proxy Name**:** **Enter a user-friendly name for the third-party proxy that you are defining.
- **IP/FQDN**:** **Enter the IP address or the FQDN of the third-party proxy service.
- **Port**: Enter the port number on which the third-party proxy service listens to the requests forwarded from Zscaler.
- **Root Certificate**: (Optional) Select the root certificate used by the third-party proxy to perform SSL inspection. This root certificate is used by Zscaler to validate the SSL leaf certificates signed by the upstream proxy. The required root certificate appears in this drop-down list only if it is uploaded from the **Administration **> **Root Certificates** page. To learn more, see [Adding Third-Party SSL Root Certificates](/zia/adding-third-party-ssl-root-certificates).
-
**Insert X-Authenticated-User**: Enable to automatically insert authenticated user ID to the HTTP header, X-Authenticated-User. This field is disabled by default.
This allows the upstream proxies to consume authenticated user ID information from the X-Authenticated-User header value, avoiding re-authentication of users.
For unauthenticated user traffic, the service inserts the value Unknown to the X-Authenticated-User header. Ensure that the third-party proxy servers are configured to re-authenticate the users if the user ID value is Unknown in the HTTP header request.
- **Enable Base64 Encoding for X-Authenticated-User Value**: If you enabled **Insert X-Authenticated-User**, select this option to encode the user ID using the base64 encoding method.
- **Description**: (Optional) Enter additional notes or information. The description cannot exceed 256 characters.
- Click **Save** and [activate the change](/zia/saving-and-activating-changes-admin-portal).
You can configure up to eight proxy objects.