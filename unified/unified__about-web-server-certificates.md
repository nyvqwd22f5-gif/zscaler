# About (Web Server) Certificates
Source: https://help.zscaler.com/unified/about-web-server-certificates
PDF: https://help.zscaler.com/pdf/com/en/1492611.pdf

Web server certificates are used to provide access to a web application, typically for Browser Access. A certificate is selected when [defining an application](/unified/configuring-defined-application-segments#tab1) within an application segment.
Web server certificates provide the following benefits and allow you to:
- Generate a new certificate by creating a certificate signing request (CSR) that is signed by your Certificate Authority (CA).
- Manage the certificates that are presented to your users by AppProtection, Browser Access, Browser Isolation, and Privileged Remote Access.
You can upload a web server certificate using one of the following workflows:
- [Upload an existing web server certificate](/unified/uploading-web-server-certificates).
*or,*
- [Create a certificate signing request (CSR) for a web server certificate](/unified/creating-certificate-signing-requests-web-server-certificates).
You cannot use [enrollment (CA) certificates](/unified/about-enrollment-ca-certificates) for Browser Access.
About the Certificates Page
[]On the Certificates page (Policies > Access Control > Clientless > Certificates), you can do the following:
- [Upload a certificate](/unified/uploading-web-server-certificates#UploadNotPending).
- [Create a CSR for a certificate](/unified/creating-certificate-signing-requests-web-server-certificates).
- Expand all of the rows in the table to see more information about each certificate.
- Filter the information that appears in the table. By default, no filters are applied.
- View a list of all web server certificates that are configured for your organization. For each certificate, you can see:
- **Name**: The name of the certificate.
- **Description**: The certificate's description, if available.
- **Issued By**: The certificate authority (CA) that issued the certificate.
- **Issued To**: The entity that the CA issued the certificate to.
- **Creation Date**: The creation date of the certificate.
- **Expiry Date**:** **The expiration date of the certificate.
- **Common Name**: The CN for the hostname associated with the certificate.
Depending on the **Expiry Date**, the following icons are displayed next to the **Name**:
- If the certificate has expired, a red warning icon is displayed.
[See image.](#ExpiredIcon)
- If the certificate has less than 7 days before expiration, a yellow caution icon is displayed.
[See image.](#7DayCautionIcon)
- If the certificate has less than 30 days before expiration, an orange info icon is displayed.
[See image.](#30DayCautionIcon)
- Download the CSR file for the certificate.
- [Upload a certificate](/unified/uploading-web-server-certificates).
- [Edit an existing certificate](/unified/editing-web-server-certificates).
- Delete a certificate.
![Viewing and managing web server certificates on the Certificates page](/downloads/certificate-management/certificates/about-web-server-certificates/unified-certificates-page.png)
[]![Certificates page](/downloads/zpa/documentation-knowledgebase/certificates/browser-access-certificates/about-BrowserAccessCertificates/zpa-expiredcerticon-bacert.png)
[]![Certificates page](/downloads/zpa/documentation-knowledgebase/certificates/browser-access-certificates/about-BrowserAccessCertificates/zpa-caution7daycerticon-bacert.png)
[]![Certificates page](/downloads/zpa/documentation-knowledgebase/certificates/browser-access-certificates/about-BrowserAccessCertificates/zpa-caution30daycerticon-bacert.png)