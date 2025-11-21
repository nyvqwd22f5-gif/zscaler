# Domain Validation in Zscaler Client Connector for Private Applications
Source: https://help.zscaler.com/unified/domain-validation-zscaler-client-connector-private-applications
PDF: https://help.zscaler.com/pdf/com/en/1495591.pdf

This functionality is only available to users running Zscaler Client Connector 1.5.1 or later.
In the Admin Portal, when [configuring DNS search domains](/unified/adding-dns-search-domains), you can specify that Zscaler Client Connector can resolve invalid domains as NXDOMAINs (non-existent domains). When a DNS request reaches Zscaler Client Connector, the app checks if the domain matches against any of the Private Applications DNS search domains marked as Domain Validation in Zscaler Client Connector.
The match can be a full match or a subdomain match. For example, if the search domain is corp.zscaler.com:
- The match succeeds for internal.corp.zscaler.com
- The match fails for my-corp.zscaler.com and it.my-corp.zscaler.com
If the domain matches one within the Private Applications DNS search domain list, Zscaler Client Connector performs additional checks to determine if it needs to respond with NXDOMAIN. If the domain doesn’t match any DNS search domains, Zscaler Client Connector doesn’t respond to the DNS request.
For a matched domain, Zscaler Client Connector checks for its validity via the Private Applications service. If the Private Applications service verifies the domain is a valid internal domain, Zscaler Client Connector sends a synthetic IP in response to the DNS request or replies with NXDOMAIN.