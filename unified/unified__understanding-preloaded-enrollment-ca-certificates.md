# Understanding Preloaded Enrollment (CA) Certificates
Source: https://help.zscaler.com/unified/understanding-preloaded-enrollment-ca-certificates
PDF: https://help.zscaler.com/pdf/com/en/1496916.pdf

The following Zscaler-issued signing certificates can be used to enroll Zscaler Client Connector and App Connectors:
- Root: The root (i.e., parent) certificate for the Client and Connector signing certificates.
- Client: A signing certificate that can be used for enrollment certificates issued to Zscaler Client Connector. The certificate's trust is established by the Zscaler public key infrastructure (PKI).
Its parent certificate is the Zscaler Root certificate. Private Applications automatically use this to sign certificates issued to Zscaler Client Connector, unless you configure another Zscaler-issued certificate.
- Connector: A Private Application signing certificate that can be used for enrollment certificates issued to Zscaler Client Connectors. The certificate’s trust is also established by the Zscaler PKI.
![Enrollment Certificates page with preloaded Zscaler-issued CA certificates displayed](/downloads/zpa/documentation-knowledgebase/certificates/enrollment-certificates/about-usingDefaultZPACertificates/zpa-certificatespage-zscalersigningcerts_0.png)
These signing certificates are 2048-bit key RSA certificates, which support TLS 1.2 connections (with cipher suite ECDHE-RSA-AES128-GCM-SHA256).
The certificate used to enroll a Private Service Edge must have the same root certificate used by the enrollment certificate for enrolling App Connectors and Zscaler Client Connector. To learn more, see [About Enrollment (CA) Certificates](/unified/about-enrollment-ca-certificates), [Configuring Private Service Edges](/unified/configuring-private-service-edges-private-applications), and [Generating Zscaler-issued Enrollment (CA) Certificates](/unified/generating-zscaler-issued-enrollment-ca-certificates).