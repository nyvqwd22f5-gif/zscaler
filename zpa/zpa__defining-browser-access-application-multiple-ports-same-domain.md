# Defining a Browser Access Application with Multiple Ports on the Same Domain
Source: https://help.zscaler.com/zpa/defining-browser-access-application-multiple-ports-same-domain
PDF: https://help.zscaler.com/pdf/com/en/1484161.pdf

In many cases the applications you want to make available via Browser Access are running on a single web server. Because it’s not necessary for the externally advertised DNS hostnames to match the internal ones, unmatched hostnames can be used to handle scenarios where one host is serving web applications on multiple ports.
For Browser Access enabled applications, Service Edges only listen on ports 80 and 443 for inbound connections from web browsers. So, a port 80 connection is automatically redirected to port 443, while a port 443 connection does domain virtualization through the provided Server Name Indication (SNI).
As a consequence, ZPA only receives one domain name and one port, and mapping that domain with port combination to multiple ports is not possible. However, you can map ports through multiple domain names using one of the following methods:
- **Method 1**: Use unique hostnames per application by using your internal DNS or by explicitly defining static servers in ZPA. This allows the advertising of a unique external hostname, that matches an internal hostname and port combination. For example, you could configure:
- The hostname web.corp.com (advertised externally), and map to web.corp.com:80 (configured internally)
- The hostname crm.corp.com (advertised externally), and map to crm.corp.com:443 (configured internally)
- The hostname webadmin.corp.com (advertised externally), and map to webadmin.corp.com:1000 (configured internally)
Using this method, as long as an internal DNS for these three hostnames is configured, then [dynamic server discovery](/zpa/how-do-i-enable-dynamic-server-discovery) for all three applications works. However, if an internal DNS doesn't exist for these three hostnames, then dynamic server discovery doesn't work and you must explicitly define static servers within the ZPA Admin Portal for them.
- [Learn more about configuring ZPA using Method 1 above](#Method1)
- **Method 2**: You can define the applications within an application segment internally to point to a specific hostname or IP address. For example, you could configure:
- The hostname web.corp.com (advertised externally), and map to linux.corp.com:80 (configured internally)
- The hostname crm.corp.com (advertised externally), and map to linux.corp.com:443 (configured internally)
- The hostname webadmin.corp.com (advertised externally), and map to linux.corp.com:1000 (configured internally)
However, this causes certificate validation problems because the hostname check fails. So users see web server certificate errors when connecting to any of the three applications in the example above.
Zscaler recommends using Method 1 above, as this method does not provide a satisfactory usability experience for your end users.
Like Method 1 above, as long as the internal DNS for these hostnames are configured, then [dynamic server discovery](/zpa/how-do-i-enable-dynamic-server-discovery) for all applications works. If an internal DNS doesn't exist for these hostnames, then dynamic server discovery doesn't work and you must explicitly define a static server within the ZPA Admin Portal and map it to the appropriate server group. In this example, server group linux.corp.com maps to server linux.corp.com. However, the server can be also specified by IP address, if necessary (i.e., server group linux.corp.com maps to server 172.31.23.203). You can then have all three applications use the same server group, but you would not be able to verify web server certificates.
- [Learn more about configuring ZPA using Method 2 above](#Method2)
To learn more, see [Explicitly Defining Servers](/zpa/about-server/new) and [Configuring Application Segments](/zpa/about-application/onboard#tab1).
[]To configure ZPA using Method 1, let’s assume that you have an application that has an FQDN of example.corp.com, which uses ports 80, 443, and 1000:
- If your internal DNS can resolve the hostnames, then proceed to step 3 and specify a server group that has **Dynamic Server Discovery** set to **On**. Make sure that you specify a server group that includes the proper App Connector groups for your servers. To learn more, see [Enabling Dynamic Server Discovery](/zpa/how-do-i-enable-dynamic-server-discovery).
If your internal DNS cannot resolve the hostnames, then you must:
- [Explicitly define the static servers.](/zpa/about-server/new) In this example, you would need to explicitly define the web.corp.com, crm.corp.com, and webadmin.corp.com servers.
- Add the defined servers to a server group that has **Dynamic Server Discovery** set to **Off**.
- Configure an application segment using the fully qualified domain names (FQDNs) you associated to the main application on your internal DNS:
- Go to **Resource Management **>** Application Management **>** Application Segments **>** Defined Application Segments**.
- Click **Add Application Segment**.
- Define the application (i.e., example.corp.com) using the FQDNs you associated to it on your internal DNS, with the proper port numbers applied. For example, for:
- web.corp.com:80 - Select **HTTP **and **80**
- crm.corp.com:443 - Select **HTTPS** and **443**
- webadmin.corp.com:1000 - Select **HTTPS** and **1000**
FQDNs that are defined in an application segment must map to the Browser Access (web server) certificate selected for ZPA to maintain the chain trust. In this example, crm.corp.com and webadmin.corp.com don't match with the web server certificate, so we must select **Use Untrusted Certificates** for both.
- Complete the configuration on the [**1 Define Applications**](/zpa/about-application/onboard#tab1) tab, then click **Next**.
- Complete the configuration on the [**2 Segment Group**](/zpa/about-application/onboard#tab2) tab, then click **Next**.
- On the [**3 Server Groups**](/zpa/about-application/onboard#selectservergroup) tab:
- If your internal DNS can resolve the hostnames, you can use an existing server group that has **Dynamic Server Discovery** set to **On**.
- If your internal DNS cannot resolve the hostnames, make sure that you select the server group you created in step 1.
- Review your application segment configuration settings on the [**5 Review**](/zpa/about-application/onboard#tab5) tab and review and edit any policies, as needed, on the [**6 Policies**](/zpa/about-application/onboard#tab6) tab.
- [Publish the CNAMEs for the FQDNs you defined in step 2c above.](/zpa/about-application/onboard#Publish_CNAME)
[]To configure ZPA using Method 2, let’s assume that you have an application that has an FQDN of linux.corp.com, which uses ports 80, 443, and 1000:
- If your internal DNS can resolve the hostnames, then proceed to step 3 and specify a server group that has **Dynamic Server Discovery** set to **On**. Make sure that you specify a server group that includes the proper App Connector groups for your server. To learn more, see [Enabling Dynamic Server Discovery](/zpa/how-do-i-enable-dynamic-server-discovery).
If your internal DNS cannot resolve the hostnames, then you must:
- [Explicitly define the static servers.](/zpa/about-server/new) In this example, you would need to explicitly define the linux.corp.com server.
- Add the defined server to a server group that has **Dynamic Server Discovery** set to **Off**.
- Configure an application segment using the fully qualified domain names (FQDNs) you associated to the application on your internal DNS:
- Go to **Resource Management** > **Application Management** > **Application Segments** > **Defined Application Segments**.
- Click **Add Application Segment**.
- Define the application (i.e., linux.corp.com) using the FQDNs you associated to it on your internal DNS, with the proper port numbers applied. For example, for:
- web.corp.com:80 - Select **HTTP **and **80**
- crm.corp.com:443 - Select **HTTPS** and **443**
- webadmin.corp.com:1000 - Select **HTTPS** and **1000**
- Complete the configuration on the [**1 Define Applications**](/zpa/about-application/onboard#tab1) tab, then click **Next**.
- Complete the configuration on the [**2 Segment Group**](/zpa/about-application/onboard#tab2) tab, then click **Next**.
- On the [**3 Server Groups**](/zpa/about-application/onboard#selectservergroup) tab:
- If your internal DNS can resolve the hostnames, you can use an existing server group that has **Dynamic Server Discovery** set to **On**.
- If your internal DNS cannot resolve the hostnames, make sure that you select the server group you created in step 1.
- Review your application segment configuration settings on the [**5 Review**](/zpa/about-application/onboard#tab5) tab and review and edit any policies, as needed, on the [**6 Policies**](/zpa/about-application/onboard#tab6) tab.
- [Publish the CNAMEs for the FQDNs you defined in step 2c above.](/zpa/about-application/onboard#Publish_CNAME)