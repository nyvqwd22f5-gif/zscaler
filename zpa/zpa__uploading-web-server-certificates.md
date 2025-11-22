# Uploading (Web Server) Certificates
Source: https://help.zscaler.com/zpa/uploading-web-server-certificates
PDF: https://help.zscaler.com/pdf/com/en/1484061.pdf

After a (web server) certificate is uploaded to ZPA, it can then be selected when [defining an application](/zpa/about-application/onboard#tab1) within an application segment. For defined applications with Browser Access enabled, if the web server certificate is signed by a public certificate authority (CA), then HTTPS should be selected as the protocol. If the web server certificate is self-signed, or ZPA is unable to verify the chain of trust to the public CA, select HTTP. ZPA supports HTTP and HTTPS protocols, and ZPA inserts a Via header in HTTP requests (e.g., Via: 1.1 Zscaler-p.zpa-auth.net). To learn more, see [Configuring Application Segments](/zpa/about-application/onboard#tab1).
The uploaded signed certificate must include the unencrypted private key.
You can upload up to 1000 (web server) certificates. For a complete list of ranges and limits per feature, see [Ranges & Limitations](/zpa/ranges-limitations).
To upload a certificate:
- Go to **Configuration & Control **>** Certificate Management** > **Certificates**.
-
In the **Certificates** page:
You must upload a single Base64 encoded ASCII .pem file, which includes the certificate and unencrypted private key. If your PKI provided you with separate files or a file in the wrong format, you can use the following OpenSSL commands to create a single .pem file that includes the certificate and key.
[See instructions.](#OpenSSL_cmds)
- [Upload a web server certificate](#UploadNotPending)
- [Upload a web server certificate for a pending CSR](#UploadPending)
- Click **Upload**.
[]The following command creates a combined certificate and unencrypted private key PKCS#12 file (.pfx):
openssl pkcs12 -export -in <certificate>.pem -inkey <unencrypted private key>.key -out <combined cert and key>.pfx
For example:
openssl pkcs12 -export -in cert.pem -inkey unencrypted.key -out combined.pfx
The following command converts the PKCS#12 file (.pfx) containing the combined certificate and unencrypted private key file to PEM format (.pem):
openssl pkcs12 -in <combined cert and key>.pfx -out <combined cert and key>.pem -nodes
For example:
openssl pkcs12 -in combined.pfx -out combined.pem -nodes
- []Click **Upload Server Certificate**.
The **Upload Server Certificate** window appears.
- In the **Upload Server Certificate** window:
- **Name**: Enter a name for the web server certificate. The name cannot contain special characters, with the exception of periods (.), hyphens (-), and underscores ( _ ).
- **Description**: (Optional) Enter a description.
- **Certificate**: Click **Select File** and navigate to the web server certificate that was signed using your PKI (i.e., a Base64 encoded ASCII PEM formatted file). Make sure that the .pem file also includes the unencrypted private key.
![Browser Access Certificates page with Upload Server Certificate window within ZPA Admin Portal](/downloads/zpa/documentation-knowledgebase/certificates/about-uploadingBrowserAccessCertificate/zpa-uploadbrowseraccesscert.png)
- []Within the table, locate the **Certificate Pending icon** (![Certificate Pending icon](/downloads/zpa/documentation-knowledgebase/certificates/browser-access-certificates/about-uploadingBrowserAccessCertificate/zpa-certificatependingicon.png)
) next to the certificate name and click the **Edit** icon.
The **Upload Server Certificate** window appears.
- In the **Upload Server Certificate** window:
- **Name**: Make sure that the correct name was entered.
- **Description**: (Optional) Enter a description.
- **Certificate Signing Request**: The CSR text is displayed here.
- Click **Download .CSR File**.
- Sign the downloaded .csr file using your public key infrastructure (PKI) to create a valid signed web server certificate.
- Save the certificate in Base64 encoded ASCII PEM format (.pem).
- **Certificate**: Click **Select File** and navigate to the signed web server certificate you created (i.e., the .pem file).
![Browser Access Certificates page with Upload Server Certificate window for pending CSR](/downloads/zpa/documentation-knowledgebase/certificates/about-uploadingBrowserAccessCertificate/zpa-uploadbrowseraccesscert-uploadsignedcert.png)