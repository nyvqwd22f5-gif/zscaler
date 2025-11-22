# Using Wildcard Certificates for Browser Access Applications
Source: https://help.zscaler.com/unified/using-wildcard-certificates-browser-access-applications
PDF: https://help.zscaler.com/pdf/com/en/1492371.pdf

Using wildcard certificates when defining Browser Access applications within an application segment is supposed. You can use a wildcard certificate for multiple fully qualified domain names (FQDNs) within a single application segment or within multiple application segments.
For example, you can create two application segments:
- App1 that contains app1.example.com
- App2 that contains app2.example.com
Where, for both application segments, you use the same wildcard certificate: *.example.com.
You can also use a wildcard certificate with a wildcard application. However, while the wildcard application includes subdomains, the wildcard certificate only matches against one level. For example:
- A *.example.com wildcard application matches against app1.example.com, app2.example.com, and app1.local.example.com
- A *.example.com wildcard certificate matches against app1.example.com and app2.example.com, but will not match against app1.local.example.com
So, in this example, the wildcard certificate is not valid for app1.local.example.com.
Therefore, if you need to enable Browser Access for a particular subdomain, you must define a separate wildcard application (i.e., *.local.example.com) within an application segment that includes the equivalent wildcard certificate.
To learn more, see [About (Web Server) Certificates](/unified/about-web-server-certificates), [About Browser Access](/unified/about-browser-access), and [Configuring Application Segments](/unified/configuring-defined-application-segments#tab1).