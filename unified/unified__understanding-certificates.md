# Understanding Certificates
Source: https://help.zscaler.com/unified/understanding-certificates
PDF: https://help.zscaler.com/pdf/com/en/1492591.pdf

Within Private Applications, you must provide certificates for enrollment and for web servers, typically for Browser Access:
- [Enrollment Certificates](/unified/about-enrollment-ca-certificates): App Connectors, Private Applications Private Service Edges, Private Cloud Controllers, and the Zscaler Client Connector are issued certificates that are sent by an enrollment certificate. The enrollment certificate must be capable of acting as a certificate authority (CA).
To learn more, see [About Enrollment Certificates](/unified/about-enrollment-ca-certificates).
- [Certificates](/unified/about-web-server-certificates): A web server certificate that is used by Private Applications to provide access to a web application, typically for Browser Access. If the web server certificate is signed by a public certificate authority (CA), then Private Applications encrypts traffic using HTTPS. If the web server certificate is self-signed, or Private Applications is unable to verify the chain of trust to the public CA, then HTTP is used.
To learn more, see [About (Web Server) Certificates](/unified/about-web-server-certificates).
Enrollment and other certificates uploaded to Private Applications must be encoded in PEM format.