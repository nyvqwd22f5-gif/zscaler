# About Enrollment (CA) Certificates
Source: https://help.zscaler.com/zpa/about-enrollment-ca-certificates
PDF: https://help.zscaler.com/pdf/com/en/1483611.pdf

[Watch a video about Enrollment Certificates](https://fast.wistia.net/embed/iframe/gstgspmdcw)
App Connectors, ZPA Private Service Edges, Private Cloud Controllers, and Zscaler Client Connector are issued certificates that are sent by an enrollment certificate. The enrollment certificate must be capable of acting as a certificate authority (CA) for processing certificate signing requests (CSRs).
Enrollment certificates provide the following benefits and allow you to:
- Generate a new certificate by creating a CSR that is signed by your CA.
- Manage the certificates that are presented to your users by App Connectors, ZPA Private Service Edges, Private Cloud Controllers, and Zscaler Client Connector.
You can upload an enrollment certificate to ZPA using one of the following workflows:
- Use Zscaler-issued CA certificates
To use Zscaler-issued CA certificates for ZPA, generate certificates for Zscaler Client Connector, ZPA Private Service Edges, Private Cloud Controllers, and App Connectors using the ZPA Admin Portal, where the CA can be:
- A Zscaler-issued root CA
- An intermediate CA, where the root (i.e., parent) certificate is one of the preloaded ZPA CA certificates or another Zscaler-issued CA certificate
Make sure the same root certificate is used by the enrollment certificates for enrolling App Connectors, ZPA Private Service Edges, Private Cloud Controllers, and Zscaler Client Connector. If you are evaluating ZPA, Zscaler recommends that you use the [preloaded ZPA certificates](/zpa/about-usingDefaultZPACertificates) provided for expediency. When you deploy ZPA to your production environment, you can continue using these certificates or generate additional Zscaler-issued certificates as needed.
To learn more, see [Understanding Preloaded Enrollment (CA) Certificates](/zpa/understanding-preloaded-enrollment-ca-certificates) and [Generating Zscaler-issued Enrollment (CA) Certificates](/zpa/about-generateEnrollmentCertificate).
- Use your organization's CA certificates
To use your organization's CA certificates for ZPA:
- Create CSRs for Zscaler Client Connector, ZPA Private Service Edges, Private Cloud Controllers, and App Connectors using the ZPA Admin Portal.
- Sign the CSRs using your organization's signing CA, which can be a root or intermediate CA. This results in the CSRs becoming signed certificates.
- Upload the signed certificates using the ZPA Admin Portal.
ZPA must verify the chain of trust for the uploaded signed certificates. So, every certificate must be present in the chain of trust, starting from the signed certificates created in step 2 up to and including the root CA certificate.
You only need to upload the certificate chain of trust once.
You can upload the certificate chain using one of the following methods:
- Method 1: Prepend the certificate chain to each signed certificate prior to uploading them to ZPA.
- Method 2: Upload the signed certificates and the certificate chain corresponding to each, separately.
To learn more, see [Creating Certificate Signing Requests for Enrollment (CA) Certificates](/zpa/about-creatingEnrollmentCsr) and [Uploading Enrollment (CA) Certificates and the Certificate Chain](/zpa/uploadingEnrollmentCertificate#UploadNotPending).
About the Enrollment Certificates Page
[]On the Enrollment Certificates page (Configuration & Control > Certificate Management > Enrollment Certificates), you can do the following:
- View a list of applied filters available from the current and previous user sessions. Applied filters must be saved to the user session first before they can be viewed. Use the drop-down menu to select the applied filters to view. To learn more, see [Using Tables](/zpa/using-tables#filterData).
- Hide the filters on the page by clicking **Hide Filters**. Click **Show Filters** to display the filters.
- Refresh the Enrollment Certificates page to reflect the most current information.
- Filter the information that appears in the table. By default, no filters are applied. You can also save applied filters to your preferences so that they're visible in future user sessions. To learn more, see [Using Tables](/zpa/using-tables#filterData).
- [Generate a Zscaler-issued enrollment (CA) certificate.](/zpa/about-generateEnrollmentCertificate)
- Click **Actions** to select one of the following actions from the drop-down menu:
- **Create CSR**: [Creates a CSR for an enrollment (CA) certificate.](/zpa/about-creatingEnrollmentCsr)
- **Upload Certificate Chain**: [Uploads a certificate chain.](/zpa/uploadingEnrollmentCertificate)
- Expand all of the rows in the table to see more information about each enrollment (CA) certificate.
- View a list of all signing certificates used for enrollment that are configured for your organization, as well as the [preloaded enrollment (CA) certificates provided by Zscaler](/zpa/about-preloaded-enrollment-ca-certificates). For each certificate, you can see:
- **Name**: The name of the certificate. A **Zscaler Client Connector** icon (![Zscaler Client Connector Enrollment Certificate Icon](/downloads/zpa/documentation-knowledgebase/certificates/enrollment-certificates/about-enrollment-ca-certificates/zpa-certicon-clientconnector.png)
) is displayed next to the name if it is being used as a signing certificate for certificates issued to clients enrolling in Zscaler Client Connector. An **Isolation Client** icon (![Isolation Client Enrollment Certificate Icon](/downloads/zpa/documentation-knowledgebase/certificates/enrollment-certificates/about-enrollment-ca-certificates/zpa-certicon-isolationclient.png)
) is displayed next to the name if it is being used as a signing certificate for isolation clients.
- **Description**: The certificate's description, if available.
- **Parent Certificate**: The parent certificate for the signing certificate, if any.
- **Issued By**: The CA that issued the certificate.
- **Issued To**: The entity that the CA issued the certificate to.
- **Creation Date**: The creation date of the certificate.
- **Expiry Date**: The expiration date of the certificate.
- **Common Name**: The CN for the hostname associated with the certificate.
Depending on the **Expiry Date**, the following icons are displayed next to the **Name**:
- If the certificate has expired, a red **Warning** icon (![zpa-warning-icon.png](/downloads/zpa/documentation-knowledgebase/certificates/enrollment-certificates/about-enrollment-ca-certificates/zpa-warning-icon.png)
) is displayed.
- If the certificate has less than 7 days before expiration, a yellow **Caution** icon (![zpa-yellow-caution-icon.png](/downloads/zpa/documentation-knowledgebase/certificates/enrollment-certificates/about-enrollment-ca-certificates/zpa-yellow-caution-icon.png)
) is displayed.
- If the certificate has less than 30 days before expiration, an orange **Info** icon (![zpa-orange-info-icon.png](/downloads/zpa/documentation-knowledgebase/certificates/enrollment-certificates/about-enrollment-ca-certificates/zpa-orange-info-icon.png)
) is displayed.
- [Edit an existing enrollment (CA) certificate.](/zpa/about-signingcert/edit#EditEnrollCert)
- Download the CSR file for enrollment certificate.
- [Upload a signed certificate.](/zpa/uploading-enrollment-ca-certificates-and-certificate-chain#UploadNotPending)
- Delete an enrollment (CA) certificate.
- [Modify the columns displayed in the table.](/zpa/using-tables)
- Display more rows or a different page of the table.
- Open the [Zscaler Help Browser](/zpa/using-zscaler-help-browser) and view Help Portal articles without leaving the ZPA Admin Portal.
- Go to the [Certificates](/zpa/about-web-server-certificates) page to view and manage Browser Access (i.e., web server) certificates.
- Go to the [Root Certificates for Isolation](/isolation/about-root-certificates-isolation-zpa) page to view and manage root certificates associated with the isolation profiles.
![Viewing and Managing Enrollment Certificates](/downloads/zpa/documentation-knowledgebase/certificates/enrollment-certificates/about-enrollment-ca-certificates/zpa-enrollment-certificates-page-react.png)