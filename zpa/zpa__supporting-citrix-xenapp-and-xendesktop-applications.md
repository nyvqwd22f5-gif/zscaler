# Supporting Citrix XenApp and XenDesktop Applications
Source: https://help.zscaler.com/zpa/supporting-citrix-xenapp-and-xendesktop-applications
PDF: https://help.zscaler.com/pdf/com/en/1484136.pdf

Citrix XenApp and XenDesktop applications are not accessible via ZPA when a wildcard (e.g., *.domain.com) or fully qualified domain name (FQDN) application (e.g., citrix.domain.com) is defined within an application segment. This is due to Citrix's default ICA file returning the IP address of the Citrix server in their data center that services the application request. Although it's possible for ZPA to access these applications using an IP address, this is not an ideal solution and is counter to our zero-trust solution.
Instead, you should configure Citrix to return the FQDN for the servers in their data center. This enables XenApp to establish a new connection to the FQDN, which ZPA then uses to pass the service through.
To learn more about how to configure Citrix, see [How to Enable DNS Address Resolution in XenApp 6.x](https://support.citrix.com/article/CTX128436) and [Controlling the Type of Address Returned by the XenApp XML Broker](https://support.citrix.com/article/CTX200103) on the Citrix Support Knowledge Center, for your XenApp version.
To learn more about application access and discovery within ZPA, see [About Application Access](/zpa/about-application-access).