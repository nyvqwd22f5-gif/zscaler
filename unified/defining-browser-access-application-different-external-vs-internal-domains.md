# Defining a Browser Access Application with Different External vs. Internal Domains
Source: https://help.zscaler.com/zpa/defining-browser-access-application-different-external-vs-internal-domains
PDF: https://help.zscaler.com/pdf/com/en/1484231.pdf

The following guide provides the methods and requirements to define a Browser Access application that utilizes different external and internal domains.
Prerequisites
Regardless of the method used, the following prerequisites apply:
- Your internal fully qualified domain name (FQDN) for the application must be properly named, e.g., internalweb.example1.com, and your App Connectors must resolve to that hostname via your internal DNS.
- Your desired external FQDN for the application must be properly named, e.g., externalweb.example2.com. Ideally, the internal and external FQDNs for the application should use similar names. However, the following will also function:
- Split-DNS, where the domain and top-level domain are the same but the hostname varies.
- Separate DNS, where the domain and top-level domain differ.
- You must create an SSL certificate for the external FQDN (e.g., webapp.external.example.com or *.external.example.com if you want to use a wildcard certificate). The SSL certificate must contain the following:
- CN=[external FQDN]
- SAN=[internal FQDN]
To learn more, see [About Browser Access (Web Server) Certificates](/zpa/about-BrowserAccessCertificates) and [Using Wildcard Certificates for Browser Access Applications](/zpa/using-wildcard-certificates-browser-access-applications).
- If your web server is multihomed and is expecting a Host header matching the internal FQDN, ZPA will not transform the external FQDN. So, if your web server is configured for Host headers, you must add the external FQDN as an additional header.
- Internal web servers must serve pages with objects linked as relative URLs (e.g. HREF=”/filename.ext”). Absolute URLs are not supported (e.g. HREF=”http://foo.example2.com/file.ext” or HREF=”http://172.16.1.1/file.ext”).
- Internal web servers must be single-tenant.
Methods to Define a Browser Access Application
To define an application for Browser Access when it uses a different externally advertised DNS hostname than its internal hostname, you must use one of the following methods.
- **Method 1**: Disable dynamic server discovery and manually define the target servers - This method supports multiple web servers and no external load balancing is required.
- [Learn more about configuring ZPA using Method 1 above](#Method1)
- **Method 2**: Enable dynamic server discovery and manually define an A record in your internal DNS for the external FQDN - This method supports only one web server, unless third-party load balancing is used to place multiple web servers behind a single IP address referenced by the A record.
- [Learn more about configuring ZPA using Method 2 above](#Method2)
[]To configure ZPA using Method 1, you must disable [dynamic server discovery](/zpa/how-do-i-enable-dynamic-server-discovery) and then manually define your servers:
- Go to **Configuration & Control** > **Private Infrastructure** > **App Connector Management** > **Server**.
- Click **Add Server**.
- In the **Add Server** window:
- **Status**: Select **Enabled**.
- **Domain and IP Address**: Enter the FQDN for the internal hostname (e.g., webapp.internal.example.com)
If you have multiple web servers supporting the same application (e.g., webapp1, webapp2, etc.), then you must add a server in the ZPA Admin Portal for each internal FQDN.
- Click **Save**.
- Go to **Configuration & Control** > **Private Infrastructure** > **App Connector Management** > **Server Groups**.
- Click **Add Server Group**.
- In the **Add Server Group** window:
- **Status**: Select **Enabled**.
- **Dynamic Server Discovery**: Select **Off**.
- **Servers**: Choose the new server you added previously in step 3 above. If you added multiple servers (e.g., webapp1, webapp2, etc.), be sure to include all of them in the group.
- **App Connector Groups**: Choose the App Connector groups that can access your internal web servers.
- Click **Save**.
- Go to **Resource Management** > **Application Management** > **Application Segments**.
- Click **Add Application Segment** and define your web application for Browser Access using the external FQDN you associated to it on your internal DNS, with the proper port numbers applied.
- Under **Applications**, enter the external FQDN associated to the web application (e.g., webapp.external.example.com)
- Select the **Browser Access** checkbox, then complete the following steps:
- Select the proper SSL certificate from the drop-down menu. The certificate must match the external FQDN (i.e., webapp.external.example.com or *.external.example.com).To learn more, see [About Browser Access (Web Server) Certificates](/zpa/about-BrowserAccessCertificates) and [Using Wildcard Certificates for Browser Access Applications](/zpa/using-wildcard-certificates-browser-access-applications).
- Select **HTTPS **for the protocol. By default, port **443 **is applied for HTTPS. If this does not apply, be sure to change the port number to the proper one your internal web application is served on.
- Make sure that **Use Untrusted Certificates** is selected.
If you need to define multiple web applications for Browser Access (e.g., webapp1.external.example.com, webapp2.external.example.com, etc.), click **Add More** and repeat steps i through iii above.
- Under **TCP Port Ranges**, make sure that the proper port ranges are specified.
- Complete the configuration on the [**1 Define Applications**](/zpa/about-application/onboard#tab1) tab, then click **Next**.
- Complete the configuration on the [**2 Segment Group**](/zpa/about-application/onboard#tab2) tab, then click **Next**.
- On the [**3 Server Groups**](/zpa/about-application/onboard#selectservergroup) tab, for **Select Server Group**, choose the server group your created in step 7 above from the drop-down menu, and click **Next**.
- Review your application segment configuration settings on the [**5 Review**](/zpa/about-application/onboard#tab5) tab and review and edit any policies, as needed, on the [**6 Policies**](/zpa/about-application/onboard#tab6) tab.
- [Publish the CNAMEs for the FQDNs you defined in step 10a above.](/zpa/about-application/onboard#Publish_CNAME)
Your users should now be able to access the [applications you defined](/zpa/about-application/onboard#tab1) within the application segment, based upon the [policies](/zpa/about-application/onboard#tab6) applied. So make sure that you add or updated your access policies accordingly for your users.
[]To configure ZPA using Method 2, you must enable [dynamic server discovery](/zpa/how-do-i-enable-dynamic-server-discovery) and create an internal A record for your external FQDN on your DNS:
- In your internal DNS, create an A record for the internal application hostname (e.g., webapp.external.example.com) that points to the IP address, or load balancer virtual IP address (VIP), of the internal web server that is hosting the application.
- In the ZPA Admin Portal, go to **Configuration & Control** > **Private Infrastructure** > **App Connector Management** > **Server Groups**.
- Click **Add Server Group**.
- In the **Add Server Group** window:
- **Status**: Select **Enabled**.
- **Dynamic Server Discovery**: Select **On**.
- **App Connector Groups**: Choose the App Connector groups that can access your internal web servers or load balancer VIP.
- Click **Save**.
- Go to **Resource Management** > **Application Management** > **Application Segments**.
- Click **Add Application Segment** and define your web application for Browser Access using the external FQDN you associated to it on your internal DNS, with the proper port numbers applied.
- Under **Applications**, enter the external FQDN associated to the web application (e.g., webapp.external.example.com)
- Select the **Browser Access** checkbox, then complete the following steps:
- Select the proper SSL certificate from the drop-down menu. The certificate must match the external FQDN (i.e., webapp.external.example.com or *.external.example.com). To learn more, see [About Browser Access (Web Server) Certificates](/zpa/about-BrowserAccessCertificates) and [Using Wildcard Certificates for Browser Access Applications](/zpa/using-wildcard-certificates-browser-access-applications).
- Select **HTTPS **for the protocol. By default, port **443 **is applied for HTTPS. If this does not apply, be sure to change the port number to the proper one your internal web application is served on.
- Make sure that **Use Untrusted Certificates** is selected.
If you need to define multiple web applications for Browser Access (e.g., webapp1.external.example.com, webapp2.external.example.com, etc.), click **Add More** and repeat steps i through iii above.
- Under **TCP Port Ranges**, make sure that the proper port ranges are specified.
- Complete the configuration on the [**1 Define Applications**](/zpa/about-application/onboard#tab1) tab, then click **Next**.
- Complete the configuration on the [**2 Segment Group**](/zpa/about-application/onboard#tab2) tab, then click **Next**.
- On the [**3 Server Groups**](/zpa/about-application/onboard#selectservergroup) tab, for **Select Server Group**, choose the server group your created in step 4 above from the drop-down menu, and click **Next**.
- Review your application segment configuration settings on the [**5 Review**](/zpa/about-application/onboard#tab5) tab and review and edit any policies, as needed, on the [**6 Policies**](/zpa/about-application/onboard#tab6) tab.
- [Publish the CNAMEs for the FQDNs you defined in step 7a above.](/zpa/about-application/onboard#Publish_CNAME)
Your users should now be able to access the [applications you defined](/zpa/about-application/onboard#tab1) within the application segment, based upon the [policies](/zpa/about-application/onboard#tab6) applied. So make sure that you add or updated your access policies accordingly for your users.