# Understanding Certificates
Source: https://help.zscaler.com/zpa/understanding-certificates
PDF: https://help.zscaler.com/pdf/com/en/1484066.pdf

[Watch a video about Certificates](https://fast.wistia.net/embed/iframe/k9inmwljuz)
Within ZPA, you must provide certificates for enrollment and for web servers, typically for Browser Access:
- [Enrollment Certificates](/zpa/about-enrollment-ca-certificates): App Connectors, ZPA Private Service Edges, Private Cloud Controllers, and Zscaler Client Connector are issued certificates that are sent by an enrollment certificate. The enrollment certificate must be capable of acting as a certificate authority (CA).
To learn more, see [About Enrollment Certificates](/zpa/about-enrollment-ca-certificates).
- [Certificates](/zpa/about-web-server-certificates): A web server certificate that is used by ZPA to provide access to a web application, typically for Browser Access. If the web server certificate is signed by a public certificate authority (CA), then ZPA encrypts traffic using HTTPS. If the web server certificate is self-signed, or ZPA is unable to verify the chain of trust to the public CA, then HTTP is used.
To learn more, see [About (Web Server) Certificates](/zpa/about-web-server-certificates).
Enrollment and other certificates uploaded to ZPA must be encoded in PEM format.