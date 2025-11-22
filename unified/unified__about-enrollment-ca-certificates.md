# About Enrollment (CA) Certificates
Source: https://help.zscaler.com/unified/about-enrollment-ca-certificates
PDF: https://help.zscaler.com/pdf/com/en/1496901.pdf

App Connectors, Private Service Edges, Private Cloud Controllers, and Zscaler Client Connector are issued certificates that are sent by an enrollment certificate. The enrollment certificate must be capable of acting as a certificate authority (CA) for processing certificate signing requests (CSRs).
Enrollment certificates provide the following benefits and allow you to:
- Generate a new certificate by creating a CSR that is signed by your CA.
- Manage the certificates that are presented to your users by App Connectors, Private Service Edges, Private Cloud Controllers, and Zscaler Client Connector.
You can upload an enrollment certificate using one of the following workflows:
- Use Zscaler-issued CA certificates
To use Zscaler-issued CA certificates for Private Applications, generate certificates for Zscaler Client Connector, Private Service Edges, Private Cloud Controllers, and App Connectors using the Admin Portal, where the CA can be:
- A Zscaler-issued root CA
- An intermediate CA, where the root (i.e., parent) certificate is one of the preloaded CA certificates or another Zscaler-issued CA certificate
Make sure the same root certificate is used by the enrollment certificates for enrolling App Connectors, Private Service Edges, Private Cloud Controllers, and Zscaler Client Connector. If you are evaluating Private Applications, Zscaler recommends that you use the [preloaded certificates](/unified/understanding-preloaded-enrollment-ca-certificates) provided for expediency. When you deploy Private Applications to your production environment, you can continue using these certificates or generate additional Zscaler-issued certificates as needed.
To learn more, see [Understanding Preloaded Enrollment (CA) Certificates](/unified/understanding-preloaded-enrollment-ca-certificates) and [Generating Zscaler-issued Enrollment (CA) Certificates](/unified/generating-zscaler-issued-enrollment-ca-certificates).
- Use your organization's CA certificates
To use your organization's CA certificates for ZPA:
- Create CSRs for Zscaler Client Connector, Private Service Edges, Private Cloud Controllers, and App Connectors using the Admin Portal.
- Sign the CSRs using your organization's signing CA, which can be a root or intermediate CA. This results in the CSRs becoming signed certificates.
- Upload the signed certificates using the Admin Portal.
Private Applications must verify the chain of trust for the uploaded signed certificates. So, every certificate must be present in the chain of trust, starting from the signed certificates created in step 2 up to and including the root CA certificate.
You only need to upload the certificate chain of trust once.
You can upload the certificate chain using one of the following methods:
- Method 1: Prepend the certificate chain to each signed certificate prior to uploading them.
- Method 2: Upload the signed certificates and the certificate chain corresponding to each, separately.
To learn more, see [Creating Certificate Signing Requests for Enrollment (CA) Certificates](/unified/creating-certificate-signing-requests-enrollment-ca-certificates) and [Uploading Enrollment (CA) Certificates and the Certificate Chain](/unified/uploading-enrollment-ca-certificates).
About the Enrollment Certificates Page
[]On the Enrollment Certificates page (Infrastructure > Private Access > Component > Enrollment Certificates), you can do the following:
- View a list of applied filters available from the current and previous user sessions. Applied filters must be saved to the user session first before they can be viewed. Use the drop-down menu to select the applied filters to view. To learn more, see [Using Tables](/unified/using-tables#filter).
- Hide the filters on the page by clicking **Hide Filters**. Click **Show Filters** to display the filters.
- Refresh the Enrollment Certificates page to reflect the most current information.
- Filter the information that appears in the table. By default, no filters are applied. You can also save applied filters to your preferences so that they're visible in future user sessions. To learn more, see [Using Tables](/unified/using-tables#filter).
- [Generate a Zscaler-issued enrollment (CA) certificate.](/unified/generating-zscaler-issued-enrollment-ca-certificates)
- Click **Actions** to select one of the following actions from the drop-down menu:
- [Upload a certificate chain.](/unified/uploading-enrollment-ca-certificates)
- [Create a CSR for an enrollment (CA) certificate.](/unified/creating-certificate-signing-requests-enrollment-ca-certificates)
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
- If the certificate has expired, a red warning icon (![Red Warning Icon](/downloads/zpa/documentation-knowledgebase/certificates/enrollment-certificates/about-enrollment-ca-certificates/zpa-warning-icon.png)
) is displayed.
- If the certificate has less than 7 days before expiration, a yellow caution icon (![Yellow Caution Icon](/downloads/zpa/documentation-knowledgebase/certificates/enrollment-certificates/about-enrollment-ca-certificates/zpa-yellow-caution-icon.png)
) is displayed.
- If the certificate has less than 30 days before expiration, an orange info icon (![Yellow Information Icon](/downloads/zpa/documentation-knowledgebase/certificates/enrollment-certificates/about-enrollment-ca-certificates/zpa-orange-info-icon.png)
) is displayed.
- [Edit an existing enrollment (CA) certificate.](/unified/editing-enrollment-ca-certificates)
- Download the CSR file for enrollment certificate.
- [Upload a signed certificate.](/unified/uploading-enrollment-ca-certificates#UploadNotPending)
- Delete an enrollment (CA) certificate.
- [Modify the columns displayed in the table.](/unified/using-tables)
- Display more rows or a different page of the table.
![Using the Enrollment Certificates page](/downloads/zpa/documentation-knowledgebase/certificates/enrollment-certificates/about-enrollment-ca-certificates/experience-center-enrollment-certs.png)