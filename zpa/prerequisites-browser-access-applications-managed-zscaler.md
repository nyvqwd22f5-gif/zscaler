# Prerequisites for Browser Access Applications Managed by Zscaler
Source: https://help.zscaler.com/zpa/prerequisites-browser-access-applications-managed-zscaler
PDF: https://help.zscaler.com/pdf/com/en/1528948.pdf

This article provides the requirements to use a [Browser Access application](/zpa/configuring-defined-application-segments#BAsteps) with a Zscaler-managed certificate. If you are defining a Browser Access application with custom certificates and configuring an FQDN, see [Defining a Browser Access Application with Different External vs. Internal Domains](/zpa/defining-browser-access-application-different-external-vs-internal-domains).
Prerequisites
When using a Zscaler-managed certificate, the following prerequisites apply:
- Your internal fully qualified domain name (FQDN) for the application must be properly named (e.g., internalweb.example1.com), and your App Connectors must resolve to that host name via your internal DNS. The domain must be owned by the tenant.
- Internal web servers must serve pages with objects linked as relative URLs (e.g., HREF=”/filename.ext”). Absolute URLs are not supported (e.g., HREF=”http://foo.example2.com/file.ext” or HREF=”http://172.16.1.1/file.ext”).
- Internal web servers must be single tenant with a single hostname only.
- Wildcard cookies are not supported.
- Wildcard Browser Access applications aren't supported (e.g., *.example1.com).
- Applications with IP addresses aren't supported.
- Domains that aren't registered by your account aren't supported (e.g., testing.com).
- Internal applications sending CORS requests to other internal applications managed by Browser Access aren't supported (e.g., internalweb.example1.com CORS request to the Browser Access application images.example1.com). Browser Access applications must be modified to add absolute external URLs.
- If an application uses the HTTP header `Content-Security-Policy`, then the application has to accept an external FQDN in the host/origin header.
ZPA Access for Managed Applications
Zscaler modifies HTTP headers for Browser Access applications in the following ways:
- **Host header:** Modified with port configured `<host>:<port>`.
- **Set-Cookie header:** The domain attribute is removed to only allow strict cookies.
- **Origin header**: Modified to add `<scheme>://<host>:<port>`.