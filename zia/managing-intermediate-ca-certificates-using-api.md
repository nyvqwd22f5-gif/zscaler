# Managing Intermediate CA Certificates Using API
Source: https://help.zscaler.com/zia/managing-intermediate-ca-certificates-using-api
PDF: https://help.zscaler.com/pdf/com/en/1400441.pdf

The Zscaler service performs SSL inspection by acting as a full SSL proxy or a trusted man-in-the-middle (MITM) proxy in order to intercept and inspect your encrypted network traffic. To perform SSL inspection, Zscaler needs to generate domain certificates (end-entity certificates) dynamically using either Zscaler issuing Certificate Authority (CA) or the issuing CA of your organization. If you want to use the issuing CA of your organization for SSL inspection, you must complete the intermediate CA certificate generation process on the ZIA Admin Portal using your root or intermediate CA. To learn more about how SSL Inspection is performed by Zscaler, see [About SSL Inspection](/zia/about-ssl-inspection).
The following sections provide information on how to create and manage custom intermediate CA certificates via API requests:
Creating a Custom Intermediate CA Certificate
The following table lists the series of operations required to create and use a custom intermediate CA certificate for SSL inspection along with the API endpoints used for each operation:
| Operation | API Endpoint |
| --------- | ------------ |
| 1. Create a Custom Intermediate CA Certificate | `POST /intermediateCaCertificate` |
| 2. Generate a Key Pair | `POST /intermediateCaCertificate/keyPair/certId` |
| 3. Generate a Certificate Signing Request (CSR) | `POST /intermediateCaCertificate/generateCsr/certid` |
| 4. Sign the CSR (performed outside Zscaler) | Not Applicable |
| 5. Upload the Signed Certificate | `POST /intermediateCaCertificate/uploadCert/certid` |
| 6. (Optional) Upload the Certificate Chain | `POST /intermediateCaCertificate/uploadCertChain/certid` |
| 7. Finalize the Certificate | `POST /intermediateCaCertificate/finalizeCert/certid` |
| 8. (Optional) Mark as Default | `PUT /intermediateCaCertificate/makeDefault/certid` |
For detailed information about each API endpoint, see [API Reference](/zia/ssl-inspection-settings).
The following sections describe the individual API operations involved in the process:
- [Step 1: Create a Custom Intermediate CA Certificate](#create-certificate)
- [Step 2: Generate a Key Pair](#generate-key-pair)
- [Step 3: Generate a Certificate Signing Request (CSR)](#generate-csr)
- [Step 4: Sign the CSR (performed outside Zscaler)](#sign-csr)
- [Step 5: Upload the Signed Certificate](#upload-signed-certificate)
- [Step 6: (Optional) Upload the Certificate Chain](#upload-certificate-chain)
- [Step 7: Finalize the Certificate](#finalize-certificate)
- [Step 8: (Optional) Mark Certificate as Default](#make-default)
Managing Custom Intermediate CA Certificates
You can modify or delete your custom intermediate CA certificates using the following API requests:
- To modify a custom intermediate CA certificate, send a PUT request to `/intermediateCaCertificate/{certId}`.
You cannot modify a certificate’s private key or region after the certificate is created. You can modify other attributes of the certificate while it is in draft mode (i.e., not finalized). To find the current state of a certificate, send a GET request to `/intermediateCaCertificate/{certId}`. The `CERT_READY` value for the `currentState` field in the response indicates that the certificate is finalized and hence no further changes can be made.
- To delete an intermediate certificate, send a DELETE request to `/intermediateCaCertificate/{certId}`.
The default intermediate certificate (i.e., `defaultCertificate` field set to true) cannot be deleted.
[]To create a custom intermediate CA certificate for SSL inspection, send a POST request to `/intermediateCaCertificate` with the following attributes:
- `name`: Specify the name of your custom intermediate CA certificate.
- `type`: Specify the type of protection for the custom intermediate CA certificate from the following options:
- `CUSTOM_SW`: Certificate is protected using the software.
- `CUSTOM_HSM`: Certificate is secured with Cloud HSM protection. Cloud HSM safeguards your certificates by storing the certificate’s private keys in a cloud-hosted Hardware Security Module (HSM).
A subscription to the software protection type supports up to two custom intermediate CA certificates, and only one certificate can be enabled at a time. Cloud HSM subscription allows you to create up to eight custom intermediate CA certificates with four active certificates at a time. You can create certificates with either Cloud HSM or software protection with Cloud HSM subscription.
- `region`: If you are creating a custom intermediate CA certificate with Cloud HSM protection, specify the region where the Cloud HSM used to store your certificates must reside. You can choose your region from `GLOBAL`, `ASIA`, `EUROPE`, and `US`. Certificates with software protection can be created only in the GLOBAL region.
- `status`: Set this field to `ENABLED` if you want to use the certificate in SSL inspection policies.
- `description`: Provide information about the custom intermediate CA certificate.
[]To generate a key pair for your custom intermediate CA certificate, send a POST request to `/intermediateCaCertificate/keyPair/{certId}`. The response includes the public key generated for the certificate among other attributes. To download the public key, send a GET request to `/intermediateCaCertificate/downloadPublicKey/{certId}`.
If your custom intermediate CA certificates are secured using Cloud HSM, you can verify the key attestation in one of the following ways to ensure that your private key is generated and protected inside Cloud HSM:
- (Recommended) Send an API request to Zscaler to verify the key attestation. For this method of verification, send a POST request to `/intermediateCaCertificate/verifyKeyAttestation/{certId}`.
- Manually verify the key attestation using the attestation statement produced by the Cloud HSM. You can download the attestation statement by sending a POST `/intermediateCaCertificate/downloadAttestation/{certId}` request.
[]To generate a Certificate Signing Request (CSR), send a POST request to `/intermediateCaCertificate/generateCsr/{certId}` with the necessary parameters. You can download the CSR by sending a GET request to `/intermediateCaCertificate/downloadCsr/{certId}`.
[]Send the generated CSR along with the certificate’s public key to your Certificate Authority (CA) to sign as an intermediate CA certificate or subordinate CA certificate. The subordinate CA can be an intermediate or an issuing CA.
[]To upload the signed intermediate CA certificate to the ZIA Admin Portal, send a POST request to `/intermediateCaCertificate/uploadCert/{certId}`.
[]To allow your clients to validate the chain of trust for the SSL certificates issued using your custom intermediate CA, you need to upload the intermediate CA certificate chain by sending a POST request to `/intermediateCaCertificate/uploadCertChain/{certId}`.
If you want to upload a certificate chain, you must upload the signed intermediate certificate first. If you do not upload a certificate chain, the Zscaler service only sends your organization's intermediate certificate and its signed server certificate to your users' devices.
[]To make a custom intermediate certificate ready to use for SSL inspection, send a POST request to `/intermediateCaCertificate/finalizeCert/{certId}`.
You can retrieve the list of certificates available for use by sending a GET request to `/intermediateCaCertificate/readyToUse`.
[]To begin using an intermediate CA certificate for SSL inspection, you need to make it the default certificate by sending a PUT request to `/intermediateCaCertificate/makeDefault/{certId}`. Once marked as default, the certificate is deployed on the ZIA Public Service Edges and used for SSL inspection.
Only one certificate can be set as default and used for SSL inspection at a time. Setting a new certificate as the default certificate automatically revokes the current default certificate from being used for SSL inspection.
Zscaler recommends performing this action during a lull period in the network traffic or maintenance windows.