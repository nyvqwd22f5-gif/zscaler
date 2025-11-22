# About (Web Server) Certificates
Source: https://help.zscaler.com/zpa/about-web-server-certificates
PDF: https://help.zscaler.com/pdf/com/en/1484051.pdf

[Watch a video about Certificates](https://fast.wistia.net/embed/iframe/k9inmwljuz)
ZPA uses web server certificates to provide access to a web application, typically for Browser Access. A certificate is selected when [defining an application](/zpa/about-application/onboard#tab1) within an application segment.
Web server certificates provide the following benefits and allow you to:
- Generate a new certificate by creating a certificate signing request (CSR) that is signed by your Certificate Authority (CA).
- Manage the certificates that are presented to your users by AppProtection, Browser Access, Browser Isolation, and Privileged Remote Access.
You can upload a web server certificate to ZPA using one of the following workflows:
- [Upload an existing web server certificate](/zpa/about-uploadingBrowserAccessCertificate#UploadNotPending).
*or,*
- [Create a certificate signing request (CSR) for a web server certificate](/zpa/about-creatingBrowserAccessCsr).
You cannot use [enrollment (CA) certificates](/zpa/about-signingcerts) for Browser Access.
About the Certificates Page
[]On the Certificates page (Configuration & Control > Certificate Management > Certificates), you can do the following:
- View a list of applied filters available from the current and previous user sessions. Applied filters must be saved to the user session first before they can be viewed. Use the drop-down menu to select the applied filters to view. To learn more, see [Using Tables](/zpa/using-tables#filterData).
- Hide the filters on the page by clicking **Hide Filters**. Click **Show Filters** to show the filters.
- Refresh the Certificates page to reflect the most current information.
- Filter the information that appears in the table. By default, no filters are applied. You can also save applied filters to your preferences so that they're visible in future user sessions. To learn more, see [Using Tables](/zpa/using-tables#filterData).
- [Upload a certificate](/zpa/about-uploadingBrowserAccessCertificate#UploadNotPending).
- [Create a CSR for a certificate](/zpa/creating-browser-access-csr).
- Expand all of the rows in the table to see more information about each certificate.
- View a list of all web server certificates that are configured for your organization. For each certificate, you can see:
- **Name**: The name of the certificate.
- **Description**: The certificate's description, if available.
- **Subject Alternate Name**: The subject alternative name of the certificate, if available.
- **Issued By**: The certificate authority (CA) that issued the certificate.
- **Issued To**: The entity that the CA issued the certificate to.
- **Creation Date**: The creation date of the certificate.
- **Expiry Date**:** **The expiration date of the certificate.
- **Common Name**: The CN for the hostname associated with the certificate.
Depending on the **Expiry Date**, the following icons are displayed next to the **Name**:
- If the certificate has expired, a red **Warning** icon (![zpa-warning-icon.png](/downloads/zpa/certificate-management/certificates/about-web-server-certificates/zpa-warning-icon.png)
) is displayed.
- If the certificate has less than 7 days before expiration, a yellow **Caution** icon (![zpa-yellow-caution-icon.png](/downloads/zpa/certificate-management/certificates/about-web-server-certificates/zpa-yellow-caution-icon.png)
) is displayed.
- If the certificate has less than 30 days before expiration, an orange **Info** icon (![zpa-orange-info-icon.png](/downloads/zpa/certificate-management/certificates/about-web-server-certificates/zpa-orange-info-icon.png)
) is displayed.
- [Edit an existing certificate](/zpa/editing-web-server-certificates).
- Download the CSR file for the certificate.
- [Upload a certificate](/zpa/about-uploadingBrowserAccessCertificate#UploadNotPending).
- Delete a certificate.
- [Modify the columns displayed in the table.](/zpa/using-tables)
- Display more rows or a different page of the table.
- Open the [Zscaler Help Browser](/zpa/using-zscaler-help-browser) and view Help Portal articles without leaving the ZPA Admin Portal.
- Go to the [Enrollment Certificates](/zpa/about-signingcerts) page to view and manage CA certificates for App Connectors, ZPA Private Service Edges, and Zscaler Client Connector.
- Go to the [Root Certificates for Isolation](/isolation/about-root-certificates-isolation-zpa) page to view and manage root certificates associated with isolation profiles.
![Viewing and Managing Certificates in the Certificates page](/downloads/zpa/certificate-management/certificates/about-web-server-certificates/zpa-certificates-page-react1.png)