# Cloud Applications
Source: https://help.zscaler.com/zia/cloud-applications

API Reference Guide for the ZIA Cloud Service and Sandbox Submission APIs

**Base URL:** https://zsapi.[zscaler-cloud-name]/api/v1

## `GET /cloudApplications/policy`

Retrieves a list of Predefined and User Defined Cloud Applications associated with the DLP rules, Cloud App Control rules, Advanced Settings, Bandwidth Classes, and File Type Control rules.
Retrieves AppInfo when groupResults is set to false and  retrieves the application count grouped by application category when groupResults is set to true.

**Tags:** Cloud Applications
**Consumes:** application/json
**Produces:** application/json

| Name | In | Type | Required | Description |
| ---- | --- | ---- | -------- | ----------- |
| search | query | string | No | Filter application by name |
| pageSize | query | integer | No | Set the size of response |
| page | query | integer | No | Set the page number of response |
| appClass | query | array | No | Filter application by application category |
| groupResults | query | boolean | No | Show count of applications grouped by application category |

| Code | Description | Schema |
| ---- | ----------- | ------ |
| 200 | Successful Operation | AppInfo |

## `GET /cloudApplications/sslPolicy`

Retrieves a list of Predefined and User Defined Cloud Applications associated with the SSL Inspection rules.
Retrives AppInfo when groupResults is set to false and retrieves the application count grouped by application category when groupResults is set to true.

**Tags:** Cloud Applications
**Consumes:** application/json
**Produces:** application/json

| Name | In | Type | Required | Description |
| ---- | --- | ---- | -------- | ----------- |
| search | query | string | No | Filter application by name |
| pageSize | query | integer | No | Set the size of response |
| page | query | integer | No | Set the page number of response |
| appClass | query | array | No | Filter application by application category |
| groupResults | query | boolean | No | Show count of applications grouped by application category |

| Code | Description | Schema |
| ---- | ----------- | ------ |
| 200 | Successful Operation | AppInfo |

## `GET /riskProfiles`

Retrieves the cloud application risk profile. To learn more, see [About Cloud Application Risk Profile](/zia/about-cloud-application-risk-profile).

**Tags:** Cloud Applications
**Consumes:** application/json
**Produces:** application/json
No parameters.

| Code | Description | Schema |
| ---- | ----------- | ------ |
| 200 | Successful Operation | RiskProfile |

## `POST /riskProfiles`

Adds a new cloud application risk profile. To learn more, see [Adding a Cloud Application Risk Profile](/zia/adding-cloud-application-risk-profile).

**Tags:** Cloud Applications
**Consumes:** application/json
**Produces:** application/json

| Name | In | Type | Required | Description |
| ---- | --- | ---- | -------- | ----------- |
| body | body | RiskProfile | No | Information about the cloud application risk profile |

| Code | Description | Schema |
| ---- | ----------- | ------ |
| 200 | Successful Operation | RiskProfile |

## `GET /riskProfiles/lite`

Retrieves the cloud application risk profile

**Tags:** Cloud Applications
**Consumes:** application/json
**Produces:** application/json
No parameters.

| Code | Description | Schema |
| ---- | ----------- | ------ |
| 200 | Successful Operation | RiskProfile |

## `DELETE /riskProfiles/{profileId}`

Deletes the cloud application risk profile based on the specified ID

**Tags:** Cloud Applications
**Consumes:** application/json
**Produces:** application/json

| Name | In | Type | Required | Description |
| ---- | --- | ---- | -------- | ----------- |
| profileId | path | integer | Yes | The risk profile ID |

| Code | Description | Schema |
| ---- | ----------- | ------ |
| default | Successful Operation |  |

## `GET /riskProfiles/{profileId}`

Retrieves the cloud application risk profile based on the specified ID

**Tags:** Cloud Applications
**Consumes:** application/json
**Produces:** application/json

| Name | In | Type | Required | Description |
| ---- | --- | ---- | -------- | ----------- |
| profileId | path | integer | Yes | The risk profile ID |

| Code | Description | Schema |
| ---- | ----------- | ------ |
| 200 | Successful Operation | RiskProfile |

## `PUT /riskProfiles/{profileId}`

Updates the cloud application risk profile based on the specified ID

**Tags:** Cloud Applications
**Consumes:** application/json
**Produces:** application/json

| Name | In | Type | Required | Description |
| ---- | --- | ---- | -------- | ----------- |
| body | body | RiskProfile | No | Information about the cloud application risk profile |
| profileId | path | integer | Yes | The risk profile ID |

| Code | Description | Schema |
| ---- | ----------- | ------ |
| 200 | Successful Operation | RiskProfile |

## Models
### AppInfo
Detailed list of application information comprising the application name and the parent application category it belongs to.
| Field | Type | Required | Description |
| ----- | ---- | -------- | ----------- |
| app | string | No | Application enum constant |
| appName | string | No | Cloud application name |
| parent | string | No | Application category enum constant |
| parentName | string | No | Name of the cloud application category |

### CustomTag
Name-ID information of custom tags
| Field | Type | Required | Description |
| ----- | ---- | -------- | ----------- |
| id | integer (int32) | No | Unique identifier of the custom tag |
| name | string | No | The name of the custom tag |

### EntityReference
This is an immutable reference to an entity that mainly consists of id and name
| Field | Type | Required | Description |
| ----- | ---- | -------- | ----------- |
| extensions | object | No | Additional information about the entity |
| externalId | string | No | An external identifier used for an entity that is managed outside of ZIA. Examples include `zpaServerGroup` and `zpaAppSegments`. This field is not applicable to ZIA-managed entities. |
| id | integer (int64) | No | A unique identifier for an entity |
| name | string | No | The configured name of the entity |

### RiskProfile
| Field | Type | Required | Description |
| ----- | ---- | -------- | ----------- |
| adminAuditLogs | string | No | Filters applications based on their support for logging and tracking all administrative activities to identify potential security threats. This field is not applicable to the Lite API. |
| certifications | array[string] | No | List of certifications to be included or excluded for the profile. This field is not applicable to the Lite API. |
| createTime | integer (int32) | No | Timestamp of when the profile was created. This field is not applicable to the Lite API. |
| customTags | array[CustomTag] | No | List of custom tags to be included or excluded for the profile. This field is not applicable to the Lite API. |
| dataBreach | string | No | Filters applications based on their history of reported data breaches in the last three years. This field is not applicable to the Lite API. |
| dataEncryptionInTransit | array[string] | No | Filters applications based on their support for encrypting data in transit. This field is not applicable to the Lite API. |
| dnsCaaPolicy | string | No | Filters applications based on their implementation of the DNS Certification Authority Authorization (CAA) policy that helps prevent unauthorized SSL certificates. This field is not applicable to the Lite API. |
| domainBasedMessageAuth | string | No | Filters applications based on their support for Domain-Based Message Authentication, Reporting, and Conformance (DMARC), which helps prevent email spoofing and phishing attacks. This field is not applicable to the Lite API. |
| domainKeysIdentifiedMail | string | No | Filters applications based on their support for DomainKeys Identified Mail (DKIM) authentication, which helps prevent email tampering. This field is not applicable to the Lite API. |
| evasive | string | No | Filters applications based on their support for anonymous access without requiring user authentication that can increase the risk of malicious activity. This field is not applicable to the Lite API. |
| excludeCertificates | integer (int32) | No | Indicates if the certificates are included or not. This field is not applicable to the Lite API. |
| fileSharing | string | No | Filters applications based on their support for file sharing features that can increase the risk of data exfiltration. This field is not applicable to the Lite API. |
| httpSecurityHeaders | string | No | Filters applications based on their implementation of all security headers (X-XSS-Protection, X-Frame-Options, Strict-Transport-Security, Content-Security-Policy, and X-Content-Type-Options) to protect against common web attacks. This field is not applicable to the Lite API. |
| id | integer (int32) | No | System-generated identifier for the cloud application risk profile |
| lastModTime | integer (int32) | No | Timestamp of when the profile was last modified. This field is not applicable to the Lite API. |
| malwareScanningForContent | string | No | Filters applications based on their support for content malware scanning. This field is not applicable to the Lite API. |
| mfaSupport | string | No | Filters applications based on their support for multi-factor authentication to enhance user account security. This field is not applicable to the Lite API. |
| modifiedBy | EntityReference | No | User that last modified the profile. This field is not applicable to the Lite API. |
| passwordStrength | string | No | Filters applications based on their password strength requirements under Hosting Info. This field is not applicable to the Lite API. |
| poorItemsOfService | string | No | Filters applications based on the presence of questionable terms and conditions in their legal agreements, such as sharing customer data with third-party applications. This field is not applicable to the Lite API. |
| profileName | string | No | Cloud application risk profile name |
| profileType | string | No | Risk profile type. The default profile type is CLOUD_APPLICATIONS. This field is not applicable to the Lite API. |
| remoteScreenSharing | string | No | Filters applications based on their support for remote access screen sharing, which can increase the risk of data exfiltration if not properly secured. This field is not applicable to the Lite API. |
| riskIndex | array[integer (int32)] | No | The risk index number of the cloud applications. It represents the risk score assigned to each cloud application based on the risk attribute values. This field is not applicable to the Lite API. |
| senderPolicyFramework | string | No | Filters applications based on their support for sender policy framework (SPF) authentication, which helps prevent email spoofing. This field is not applicable to the Lite API. |
| sourceIpRestrictions | string | No | Filters applications based on their ability to restrict access to specific IP addresses, reducing the attack surface. This field is not applicable to the Lite API. |
| sslCertKeySize | string | No | Filters applications based on the key size of their SSL certificates. This field is not applicable to the Lite API. |
| sslCertValidity | string | No | Filters applications based on the validity period of their SSL certificates. This field is not applicable to the Lite API. |
| sslPinned | string | No | Filters applications based on their use of pinned SSL certificates, making it difficult for attackers to decrypt and validate traffic. This field is not applicable to the Lite API. |
| status | string | No | Status of the applications. You can select the application status for cloud applications while adding a cloud application risk profile, and select the risk profile as a criterion in the Cloud App Control Policy rule. This field is not applicable to the Lite API. |
| supportForWaf | string | No | Filters applications based on their support for web application firewalls (WAFs) to protect against common web attacks. This field is not applicable to the Lite API. |
| vulnerability | string | No | Filters applications based on their published CVE vulnerabilities. This field is not applicable to the Lite API. |
| vulnerabilityDisclosure | string | No | Filters applications based on their policy for disclosing known vulnerabilities, allowing ethical hackers to report potential security threats. This field is not applicable to the Lite API. |
| vulnerableToHeartBleed | string | No | Filters applications based on their vulnerability to the Heartbleed attack. This field is not applicable to the Lite API. |
| vulnerableToLogJam | string | No | Filters applications based on their vulnerability to the Logjam attack. This field is not applicable to the Lite API. |
| vulnerableToPoodle | string | No | Filters applications based on their vulnerability to the POODLE attack. This field is not applicable to the Lite API. |
| weakCipherSupport | string | No | Filters applications based on their support for weak ciphers with key sizes less than 128 bits that can compromise SSL connections. This field is not applicable to the Lite API. |
