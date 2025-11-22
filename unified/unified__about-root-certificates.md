# About Root Certificates
Source: https://help.zscaler.com/unified/about-root-certificates
PDF: https://help.zscaler.com/pdf/com/en/1497746.pdf

If you are using a third-party proxy service or isolated browser, Zscaler provides administrators with the capability to upload root certificates of their choice to use for successful SSL inspection.
The Root Certificates page provides the following benefits and enables you to:
- Upload custom root certificates of the third-party proxy service to sign the MITM certificates.
- Upload and associate custom root certificates with the isolation profiles that are created in the Admin Portal. The isolation browser trusts all the well-known certificate authorities trusted by Chromium.
About the Root Certificates Page
On the Root Certificates page (Infrastructure > Internet SaaS > Network Policies > Root Certificates), you can do the following:
- View the list of all configured root certificates. For each root certificate, you can view the following details:
- **Certificate Name**: The name of the root certificate.
- **Uploaded on**: The uploaded date and time of the root certificate.
- **Expiration Date**: The expiration date and time of the root certificate.
- **Type**: The type of root certificate.
- Search for a root certificate.
- [Customize the columns for the list](/unified/using-tables).
- [Add a new root certificate](/unified/adding-root-certificates).
- [Edit](/unified/editing-root-certificates) or [delete](/unified/deleting-root-certificates) any root certificates that are not the default root certificate.
- Download any root certificates that are not the default root certificate.
- Click to view the full details for the default root certificate.
![Screenshot of the Root Certificates in the ZIA Admin Portal](/downloads/zia/authentication-administration/certificates/about-root-certificates/ZIA_about-root-certificates.png)