# Adding DNS Search Domains
Source: https://help.zscaler.com/unified/adding-dns-search-domains
PDF: https://help.zscaler.com/pdf/com/en/1492136.pdf

As necessary, DNS search domains can be added as suffixes to application names to create fully qualified domain names (FQDNs). This is analogous to the DNS search suffixes in a DHCP scope for adding suffixes to non-FQDN (i.e., shortname) hosts. The DNS search domains are processed in sequence on the Zscaler Client Connector. For a complete list of ranges and limits for DNS suffixes, see [About Ranges & Limitations](/unified/ranges-limitations).
Defining DNS search domains for applications is not required. However, when you [configure an application segment](/unified/configuring-defined-application-segments), the FQDNs or wildcard discovery domains you enter must match your DNS search domains.
Zscaler recommends you are aware of the following when adding DNS search domains within [Microtenants](/unified/about-microtenants):
-
DNS search domains are unique per customer.
-
When configuring Microtenants, DNS search domains that are added in the default tenant are inherited across Microtenants.
To add DNS search domains:
- Go to **Application Segments** (Policies > Access Control > Private Applications > App Segments) or **Browser Access** (Policies > Access Control > Clientless > Browser Access) or **Segment Groups** (Policies > Access Control > Private Applications > Segment Groups).
- Click **DNS Search Domains**.
The **DNS Search Domains** window appears.
- In the **DNS Search Domains** window, enter the FQDN.
A trailing dot (.) is not supported when adding DNS search domains. For example, the domain `example.safemarch.com.` is not valid.
- (Optional) If you need Zscaler Client Connector to resolve invalid domains as NXDOMAIN (non-existent domain), select **Domain Validation in Zscaler Client Connector**.
This setting is only applied if your users are running Zscaler Client Connector 1.5.1 or later.
Click **Add More** to enter additional DNS search domains. If you need to remove a domain, hover over the field and click the **Remove** icon (![Remove icon within the ZPA Admin Portal](/downloads/zpa/documentation-knowledgebase/applications/application-segments/dnsDomains/zpa-removeicon-x.png)
).
![Add and Remove Buttons in DNS Search Domains Window within ZPA Admin Portal](/downloads/zpa/documentation-knowledgebase/applications/application-segments/dnsDomains/zpa-adddnssearchdomains.png)
- Click **Save**.