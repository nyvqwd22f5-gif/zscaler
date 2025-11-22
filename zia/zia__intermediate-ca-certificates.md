# Intermediate CA Certificates
Source: https://help.zscaler.com/zia/intermediate-ca-certificates

API Reference Guide for the ZIA Cloud Service and Sandbox Submission APIs

**Base URL:** https://zsapi.[zscaler-cloud-name]/api/v1

## `GET /intermediateCaCertificate`

Gets the list of intermediate CA certificates added for SSL  inspection.

**Tags:** Intermediate CA Certificates
**Consumes:** application/json
**Produces:** application/json

| Name | In | Type | Required | Description |
| ---- | --- | ---- | -------- | ----------- |
| page | query | integer | No | Specifies the page offset. |
| pageSize | query | integer | No | Specifies the page size. |

| Code | Description | Schema |
| ---- | ----------- | ------ |
| 200 | Successful Operation | array[IntermediateCaCertificate] |

## `POST /intermediateCaCertificate`

Adds a custom intermediate CA certificate that can be used for SSL  inspection. Custom intermediate certificates can be added with software protection or cloud HSM based on your subscriptions. In cloud HSM  protection, your certificate private keys are stored in a cloud hardware security module (HSM) located in a region of your choice.
With cloud HSM protection subscription, you can add up to eight custom intermediate certificates using either cloud HSM or software protection and only four certificates can be active at a time. With software protection subscription, you can add up to 2 intermediate certificates and only one certificate can be active at a time.
To learn more, see [Configuring Cloud HSM  Protection Intermediate CA Certificate](/zia/configuring-cloud-hsm-protection-intermediate-ca-certificate) and [ Configuring Software Protection Intermediate CA Certificate](/zia/configuring-software-protection-intermediate-ca-certificate).

**Tags:** Intermediate CA Certificates
**Consumes:** application/json
**Produces:** application/json

| Name | In | Type | Required | Description |
| ---- | --- | ---- | -------- | ----------- |
| body | body | IntermediateCaCertificate | No | Intermediate CA certificate information. |

| Code | Description | Schema |
| ---- | ----------- | ------ |
| 200 | Successful Operation | IntermediateCaCertificate |

## `GET /intermediateCaCertificate/downloadAttestation/{certId}`

Downloads the attestation bundle produced by the HSM solution for  the specified intermediate CA certificate ID. The attestation bundle  can be used to verify the HSM key attributes and the validity of the  certificate.

**Tags:** Intermediate CA Certificates
**Consumes:** application/json
**Produces:** application/json

| Name | In | Type | Required | Description |
| ---- | --- | ---- | -------- | ----------- |
| certId | path | integer | Yes | The unique identifier for the intermediate CA certificate. |

| Code | Description | Schema |
| ---- | ----------- | ------ |
| 200 | Successful Operation |  |

## `GET /intermediateCaCertificate/downloadCsr/{certId}`

Downloads a Certificate Signing Request (CSR) for the specified ID. To perform this operation, a CSR must have already been generated.

**Tags:** Intermediate CA Certificates
**Consumes:** application/json
**Produces:** application/json

| Name | In | Type | Required | Description |
| ---- | --- | ---- | -------- | ----------- |
| certId | path | integer | Yes | The unique identifier for the intermediate CA certificate. |

| Code | Description | Schema |
| ---- | ----------- | ------ |
| 200 | Successful Operation |  |

## `GET /intermediateCaCertificate/downloadPublicKey/{certId}`

Downloads the public key in the HSM key pair for the intermediate CA certificate with the specified ID. To perform this operation, a HSM key pair must have already been generated.

**Tags:** Intermediate CA Certificates
**Consumes:** application/json
**Produces:** application/json

| Name | In | Type | Required | Description |
| ---- | --- | ---- | -------- | ----------- |
| certId | path | integer | Yes | The unique identifier for the intermediate CA certificate. |

| Code | Description | Schema |
| ---- | ----------- | ------ |
| 200 | Successful Operation |  |

## `POST /intermediateCaCertificate/finalizeCert/{certId}`

Finalizes the intermediate CA certificate with the specified ID.

**Tags:** Intermediate CA Certificates
**Consumes:** application/json
**Produces:** application/json

| Name | In | Type | Required | Description |
| ---- | --- | ---- | -------- | ----------- |
| certId | path | integer | Yes | The unique identifier for the intermediate CA certificate. |

| Code | Description | Schema |
| ---- | ----------- | ------ |
| 200 | Successful Operation |  |

## `POST /intermediateCaCertificate/generateCsr/{certId}`

Generates a Certificate Signing Request (CSR) for the custom  intermediate CA certificate with the specified ID. You can send the generated CSR to your Certificate Authority (CA) to sign as a subordinate CA certificate or intermediate CA certificate. The  subordinate CA can be an intermediate or an issuing CA.

**Tags:** Intermediate CA Certificates
**Consumes:** application/json
**Produces:** application/json

| Name | In | Type | Required | Description |
| ---- | --- | ---- | -------- | ----------- |
| certId | path | integer | Yes | The unique identifier for the intermediate CA certificate. |
| csr | body | CertSigningRequest | Yes | Certificate Signing Request (CSR) information. |

| Code | Description | Schema |
| ---- | ----------- | ------ |
| 200 | Successful Operation | CertCSR |

## `POST /intermediateCaCertificate/keyPair/{certId}`

Generates a HSM key pair for the custom intermediate CA certificate with the specified ID.

**Tags:** Intermediate CA Certificates
**Consumes:** application/json
**Produces:** application/json

| Name | In | Type | Required | Description |
| ---- | --- | ---- | -------- | ----------- |
| certId | path | integer | Yes | The unique identifier for the intermediate CA certificate. |

| Code | Description | Schema |
| ---- | ----------- | ------ |
| 200 | Successful Operation | HsmKey |

## `GET /intermediateCaCertificate/lite`

Gets the list of intermediate CA certificates added for SSL inspection.

**Tags:** Intermediate CA Certificates
**Consumes:** application/json
**Produces:** application/json

| Name | In | Type | Required | Description |
| ---- | --- | ---- | -------- | ----------- |
| page | query | integer | No | Specifies the page offset. |
| pageSize | query | integer | No | Specifies the page size. |

| Code | Description | Schema |
| ---- | ----------- | ------ |
| 200 | Successful Operation | array[IntermediateCaCertificate] |

## `GET /intermediateCaCertificate/lite/{certId}`

Gets information about the intermediate CA certificate with the  specified ID.

**Tags:** Intermediate CA Certificates
**Consumes:** application/json
**Produces:** application/json

| Name | In | Type | Required | Description |
| ---- | --- | ---- | -------- | ----------- |
| certId | path | integer | Yes | The unique identifier for the intermediate CA certificate. |

| Code | Description | Schema |
| ---- | ----------- | ------ |
| 200 | Successful Operation | IntermediateCaCertificate |

## `PUT /intermediateCaCertificate/makeDefault/{certId}`

Updates the intermediate CA certificate information for the specified ID to mark it as the default intermediate certificate. Only one intermediate certificate can be marked as the default certificate at a time.

**Tags:** Intermediate CA Certificates
**Consumes:** application/json
**Produces:** application/json

| Name | In | Type | Required | Description |
| ---- | --- | ---- | -------- | ----------- |
| certId | path | integer | Yes | The unique identifier for the intermediate CA certificate. |

| Code | Description | Schema |
| ---- | ----------- | ------ |
| 200 | Successful Operation | IntermediateCaCertificate |

## `GET /intermediateCaCertificate/readyToUse`

Gets the list of intermediate CA certificates that are ready to use  for SSL inspection.

**Tags:** Intermediate CA Certificates
**Consumes:** application/json
**Produces:** application/json

| Name | In | Type | Required | Description |
| ---- | --- | ---- | -------- | ----------- |
| page | query | integer | No | Specifies the page offset. |
| pageSize | query | integer | No | Specifies the page size. |

| Code | Description | Schema |
| ---- | ----------- | ------ |
| 200 | Successful Operation | array[IntermediateCaCertificate] |

## `GET /intermediateCaCertificate/showCert/{certId}`

Shows information about the signed intermediate CA certificate with the specified ID.

**Tags:** Intermediate CA Certificates
**Consumes:** application/json
**Produces:** application/json

| Name | In | Type | Required | Description |
| ---- | --- | ---- | -------- | ----------- |
| certId | path | integer | Yes | The unique identifier for the intermediate CA certificate. |

| Code | Description | Schema |
| ---- | ----------- | ------ |
| 200 | Successful Operation | CertSigningRequest |

## `GET /intermediateCaCertificate/showCsr/{certId}`

Shows information about the Certificate Signing Request (CSR) for the specified ID.

**Tags:** Intermediate CA Certificates
**Consumes:** application/json
**Produces:** application/json

| Name | In | Type | Required | Description |
| ---- | --- | ---- | -------- | ----------- |
| certId | path | integer | Yes | The unique identifier for the intermediate CA certificate. |

| Code | Description | Schema |
| ---- | ----------- | ------ |
| 200 | Successful Operation | CertSigningRequest |

## `POST /intermediateCaCertificate/uploadCert/{certId}`

Uploads a custom intermediate CA certificate signed by your  Certificate Authority (CA) for SSL inspection. To enable users' browsers to trust this new intermediate certificate and any certificate signed by  it, install this certificate on users' browsers. If you also want to  upload a certificate chain, upload the signed intermediate certificate before uploading the certificate chain.

**Tags:** Intermediate CA Certificates
**Consumes:** multipart/form-data
**Produces:** application/json

| Name | In | Type | Required | Description |
| ---- | --- | ---- | -------- | ----------- |
| certId | path | integer | Yes | The unique identifier for the intermediate CA certificate. |
| fileInputStream | body | InputStream | No | Uploads the signed intermediate CA certificate. |

| Code | Description | Schema |
| ---- | ----------- | ------ |
| 200 | Successful Operation |  |

## `POST /intermediateCaCertificate/uploadCertChain/{certId}`

Uploads the intermediate certificate chain (PEM file). Upload the certificate chain that includes any other intermediate certificates that complete the chain to the intermediate root certificate you want to upload.
When you upload a certificate chain, the Zscaler service sends the  intermediate certificate along with this key chain and the signed server certificate to your users’ machines during SSL inspection. If you do not upload the certificate chain, the Zscaler service sends only your organization’s intermediate root certificate and its signed server certificate to your users' machines.

**Tags:** Intermediate CA Certificates
**Consumes:** multipart/form-data
**Produces:** application/json

| Name | In | Type | Required | Description |
| ---- | --- | ---- | -------- | ----------- |
| certId | path | integer | Yes | The unique identifier for the intermediate CA certificate. |
| body | body | InputStream | No | Uploads the intermediate certificate chain (PEM). |

| Code | Description | Schema |
| ---- | ----------- | ------ |
| 200 | Successful Operation |  |

## `POST /intermediateCaCertificate/verifyKeyAttestation/{certId}`

Verifies the attestation for the HSM keys generated for the  specified ID.

**Tags:** Intermediate CA Certificates
**Consumes:** application/json
**Produces:** application/json

| Name | In | Type | Required | Description |
| ---- | --- | ---- | -------- | ----------- |
| certId | path | integer | Yes | The unique identifier for the intermediate CA certificate. |

| Code | Description | Schema |
| ---- | ----------- | ------ |
| 200 | Successful Operation | HsmKeyAttestation |

## `DELETE /intermediateCaCertificate/{certId}`

Deletes the intermediate CA certificate with the specified ID.  The default intermediate certificate cannot be deleted.

**Tags:** Intermediate CA Certificates
**Consumes:** application/json
**Produces:** application/json

| Name | In | Type | Required | Description |
| ---- | --- | ---- | -------- | ----------- |
| certId | path | integer | Yes | The unique identifier for the intermediate CA certificate. |

| Code | Description | Schema |
| ---- | ----------- | ------ |
| default | Successful Operation |  |

## `GET /intermediateCaCertificate/{certId}`

Gets intermediate CA certificate information for the specified ID.

**Tags:** Intermediate CA Certificates
**Consumes:** application/json
**Produces:** application/json

| Name | In | Type | Required | Description |
| ---- | --- | ---- | -------- | ----------- |
| certId | path | integer | Yes | The unique identifier for the intermediate CA certificate. |

| Code | Description | Schema |
| ---- | ----------- | ------ |
| 200 | Successful Operation | IntermediateCaCertificate |

## `PUT /intermediateCaCertificate/{certId}`

Updates intermediate CA certificate information for the specified ID.

**Tags:** Intermediate CA Certificates
**Consumes:** application/json
**Produces:** application/json

| Name | In | Type | Required | Description |
| ---- | --- | ---- | -------- | ----------- |
| certId | path | integer | Yes | The unique identifier for the intermediate CA certificate. |
| body | body | IntermediateCaCertificate | No | Intermediate CA certificate information. |

| Code | Description | Schema |
| ---- | ----------- | ------ |
| 200 | Successful Operation | IntermediateCaCertificate |

## `DELETE /sslSettings/certchain`

Deletes the intermediate certificate chain.

**Tags:** Intermediate CA Certificates
**Consumes:** application/json
**Produces:** application/json
No parameters.

| Code | Description | Schema |
| ---- | ----------- | ------ |
| 200 | Successful Operation |  |

## `GET /sslSettings/downloadcsr`

Downloads a Certificate Signing Request (CSR). Before you can download the CSR, you must send a POST request to `/sslSettings/generatecsr` to create it.

**Tags:** Intermediate CA Certificates
**Consumes:** application/json
**Produces:** application/json
No parameters.

| Code | Description | Schema |
| ---- | ----------- | ------ |
| 200 | Successful Operation |  |

## `GET /sslSettings/exemptedUrls`

Gets a list of URLs that were exempted from SSL Inpection and policy evaluation.

**Tags:** Intermediate CA Certificates
**Consumes:** application/json
**Produces:** application/json
No parameters.

| Code | Description | Schema |
| ---- | ----------- | ------ |
| 200 | Successful Operation | Urls |

## `POST /sslSettings/exemptedUrls`

Adds URLs to the exempted from SSL Inspection and policy evaluation list or removes URLs from the list. To add a URL to the list, set the action parameter to `ADD_TO_LIST`. To remove a URL, set action to `REMOVE_FROM_LIST`.

**Tags:** Intermediate CA Certificates
**Consumes:** application/json
**Produces:** application/json

| Name | In | Type | Required | Description |
| ---- | --- | ---- | -------- | ----------- |
| action | query | string | Yes | The action applied to the exempted URLs list (i.e., adding a URL or removing a URL). |

| Code | Description | Schema |
| ---- | ----------- | ------ |
| 200 | Successful Operation | Urls |

## `POST /sslSettings/generatecsr`

Generates a Certificate Signing Request (CSR). If your organization uses a custom intermediate root certificate for SSL inspection, send a GET request to `/sslSettings/generatecsr` to generate a new CSR, then send the generated CSR to your Certificate Authority (CA) to sign as a subordinate CA certificate. The subordinate CA can be an intermediate or an issuing CA.

**Tags:** Intermediate CA Certificates
**Consumes:** application/json
**Produces:** application/json

| Name | In | Type | Required | Description |
| ---- | --- | ---- | -------- | ----------- |
| cert | body | CustomCertificate | Yes | Certificate information. |

| Code | Description | Schema |
| ---- | ----------- | ------ |
| 200 | Successful Operation |  |

## `GET /sslSettings/showcert`

Shows information about the signed intermediate root certificate.

**Tags:** Intermediate CA Certificates
**Consumes:** application/json
**Produces:** application/json
No parameters.

| Code | Description | Schema |
| ---- | ----------- | ------ |
| 200 | Successful Operation |  |

## `POST /sslSettings/uploadcert/text`

Uploads a signed intermediate root certificate for clients that use iframe-based uploads whose content type is text/plain. To enable users' browsers to trust this intermediate root certificate and any certificate signed by it, install this root certificate on users' browsers. If you also want to upload a certificate chain, upload the signed intermediate root certificate before uploading the certificate chain.

**Tags:** Intermediate CA Certificates
**Consumes:** multipart/form-data
**Produces:** text/plain

| Name | In | Type | Required | Description |
| ---- | --- | ---- | -------- | ----------- |
| fileInputStream | body | InputStream | No | The file input stream. |

| Code | Description | Schema |
| ---- | ----------- | ------ |
| 200 | Successful Operation |  |
| 400 | If the file upload fails, one of the following responses is displayed:
- Invalid request format
- Invalid file name
- No file selected
- Unsupported file format
- File size cannot exceed 64K
- Certificate has already expired
- Certificate not yet valid
- Invalid certificate contents, certificate and key do not match
- No CSR found
- Certificate cannot be parsed properly
- Not a valid root certificate
- Error in certificate format |  |

## `POST /sslSettings/uploadcertchain/text`

Uploads the Intermediate Certificate Chain (PEM) for clients that use iframe-based uploads whose content type is text/plain. Upload the certificate chain that includes any other intermediate certificates that complete the chain to the intermediate root certificate you want to upload.
When you upload a certificate chain, the Zscaler service sends the intermediate root certificate along with this key chain and the signed server certificate to your users' machines during SSL inspection. If you do not upload the certificate chain, the Zscaler service sends only your organization's intermediate root certificate and its signed server certificate to your users' machines.

**Tags:** Intermediate CA Certificates
**Consumes:** multipart/form-data
**Produces:** text/plain

| Name | In | Type | Required | Description |
| ---- | --- | ---- | -------- | ----------- |
| fileInputStream | body | InputStream | No | Upload the certificate change. |

| Code | Description | Schema |
| ---- | ----------- | ------ |
| 200 | Successful Operation |  |
| 400 | If the file upload fails, one of the following responses is displayed:
- Invalid request format
- Invalid file name
- No file selected
- Unsupported file format
- File name cannot be greater than 64 characters
- This certificate chain has n elements. Maximum number of chains allowed: 16
- Certificate chain has already expired
- Certificate chain not valid
- Certificate chain cannot be parsed properly
- Error in certificate chain format
- File size cannot exceed 64K
- Invalid certificate chain contents, certificate and chain do not match |  |

## Models
### CertCSR
Certificate Signing Request (CSR) information.
| Field | Type | Required | Description |
| ----- | ---- | -------- | ----------- |
| certId | integer (int32) | No | Unique identifier for the intermediate CA certificate |
| csrGenerationTime | integer (int32) | No | Timestamp when the CSR was generated |

### CertSigningRequest
Certificate Signing Request (CSR) information. Required if your  organization uses a custom intermediate root certificate for SSL inspection. After generating the CSR, download and send it to your trusted Certificate Authority (CA) to sign as a subordinate CA certificate or intermediate CA certificate.
| Field | Type | Required | Description |
| ----- | ---- | -------- | ----------- |
| certId | integer (int32) | No | Unique identifier for the intermediate CA certificate |
| city | string | Yes | Name of the city or town where your organization is located |
| commName | string | Yes | Common Name (CN) of your organization’s domain, such as zscaler.com |
| country | string | Yes | Country where your organization is located |
| csrFileName | string | Yes | Name of the CSR file |
| deptName | string | Yes | Name of your department or division |
| keySize | integer (int32) | No | Key size to be used in the encryption algorithm in bits.  Default size: 2048 bits |
| orgName | string | Yes | Name of your organization or company |
| pathLengthConstraint | integer (int32) | No | The path length constraint for the intermediate CA certificate.  Default values: 0 for cloud HSM, 1 for software protection |
| signatureAlgorithm | string | No | Signature algorithm to be used for generating intermediate CA  certificate. Default value: SHA256 |
| state | string | Yes | State, province, region, or county where your organization is located |

### CustomCertificate
If your organization uses a custom intermediate root certificate for SSL inspection. Click Generate New CSR to open the Generate Certificate Signing Request window. Fill in the CSR request, and click Save. Then click Download CSR. Send this CSR to your CA for signing, and ensure it is signed as a Subordinate Certification Authority or Intermediate Certification Authority.
| Field | Type | Required | Description |
| ----- | ---- | -------- | ----------- |
| certName | string | Yes | Certificate Name |
| city | string | Yes | City |
| commName | string | Yes | Common Name |
| country | string | Yes | Country |
| deptName | string | Yes | Department |
| keySize | integer (int32) | No | Key Size, by default set to 2048 |
| orgName | string | Yes | Organization |
| sha1fingerprint | string | No | Certificate SHA fingerprint, provided only in show cert |
| signatureAlgorithm | string | No | Signature Algorithm |
| state | string | Yes | State |
| validityInDays | integer (int32) | No | Number of days of certificate validity, provided only in show cert |

### HsmKey
HSM key information.
| Field | Type | Required | Description |
| ----- | ---- | -------- | ----------- |
| certId | integer (int32) | No | Unique identifier for the intermediate CA certificate |
| keyGenerationTime | integer (int32) | No | Timestamp when the HSM key was generated |
| publicKey | string | No | Public key in the HSM key pair generated for the intermediate CA certificate |

### HsmKeyAttestation
HSM key attestation verification information.
| Field | Type | Required | Description |
| ----- | ---- | -------- | ----------- |
| certId | integer (int32) | No | Unique identifier for the intermediate CA certificate |
| hsmAttestationVerifiedTime | integer (int32) | No | Timestamp when the attestation for the HSM key was verified |

### InputStream

### IntermediateCaCertificate
Intermediate CA certificate information.
| Field | Type | Required | Description |
| ----- | ---- | -------- | ----------- |
| certExpDate | integer (int64) | No | Expiration date of the intermediate CA certificate’s validity period |
| certStartDate | integer (int64) | No | Start date of the intermediate CA certificate’s validity period |
| csrFileName | string | No | Certificate Signing Request (CSR) file name |
| csrGenerationTime | integer (int32) | No | Timestamp when the Certificate Signing Request (CSR) was generated |
| currentState | string | No | Tracks the progress of the intermediate CA certificate in the configuration workflow |
| defaultCertificate | boolean | No | If set to true, the intermediate CA certificate is the default intermediate certificate. Only one certificate can be marked as the default intermediate certificate at a time. |
| description | string | No | Description for the intermediate CA certificate |
| hsmAttestationVerifiedTime | integer (int32) | No | Timestamp when the attestation for the HSM key was verified |
| id | integer (int32) | No | Unique identifier for the intermediate CA certificate |
| keyGenerationTime | integer (int32) | No | Timestamp when the HSM key was generated |
| name | string | Yes | Name of the intermediate CA certificate |
| publicKey | string | No | Public key in the HSM key pair generated for the intermediate CA certificate |
| region | string | No | Location of the HSM resources. Required for custom intermediate CA certificates with cloud HSM protection. |
| status | string | No | Determines whether the intermediate CA certificate is enabled or  disabled for SSL inspection. Subscription to cloud HSM protection allows a maximum of four active certificates for SSL inspection at a time,  whereas software protection subscription allows only one active certificate. |
| type | string | Yes | Type of the intermediate CA certificate. Available types: Zscaler’s intermediate CA certificate (provided by Zscaler), custom intermediate certificate with software protection, and custom intermediate certificate with cloud HSM protection. |

### Urls
| Field | Type | Required | Description |
| ----- | ---- | -------- | ----------- |
| urls | array[string] | No | Domains or URLs which are exempted from SSL Inspection |
