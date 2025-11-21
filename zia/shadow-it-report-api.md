# Shadow IT Report
Source: https://help.zscaler.com/zia/shadow-it-report-api

API Reference Guide for the ZIA Cloud Service and Sandbox Submission APIs

**Base URL:** https://zsapi.[zscaler-cloud-name]/api/v1

## `PUT /cloudApplications/bulkUpdate`

Updates application status and tag information for predefined or custom cloud applications based on the IDs specified

**Tags:** Shadow IT Report
**Consumes:** application/json
**Produces:** application/json

| Name | In | Type | Required | Description |
| ---- | --- | ---- | -------- | ----------- |
| body | body | CloudApplication | Yes |  |

| Code | Description | Schema |
| ---- | ----------- | ------ |
| default | Successful Operation |  |

## `GET /cloudApplications/lite`

Gets the list of predefined and custom cloud applications

**Tags:** Shadow IT Report
**Consumes:** application/json
**Produces:** application/json

| Name | In | Type | Required | Description |
| ---- | --- | ---- | -------- | ----------- |
| pageNumber | query | integer | No | Specifies the page number. The numbering starts at 0. |
| limit | query | integer | No | Specifies the maximum number of cloud applications that must be retrieved in a page |

| Code | Description | Schema |
| ---- | ----------- | ------ |
| 200 | Successful Operation | array[NamedItem] |

## `GET /customTags`

Gets the list of custom tags available to assign to cloud applications

**Tags:** Shadow IT Report
**Consumes:** application/json
**Produces:** application/json
No parameters.

| Code | Description | Schema |
| ---- | ----------- | ------ |
| 200 | Successful Operation | array[CustomTag] |

## `POST /shadowIT/applications/export`

Export the Shadow IT Report (in CSV format) for the [cloud applications](/zia/about-cloud-applications) recognized by Zscaler based on their usage in your organization. This report lists cloud applications along with a number of parameters including the sanction status for each application, the risk index assigned for the application, application usage details, application hosting information, and application security-related information, such as SSL certificate validity, data encryption (in transit), security certifications, published CVE, involvement in data breaches, etc.
You can generate this report for specific applications by using the **application** parameter. If no value is specified for this parameter, the report is generated for all cloud applications. You can customize the report by using various filters to show only the cloud applications that match specific parameters. To learn more, see [About Shadow IT Report](/zia/about-shadow-it-report).

**Tags:** Shadow IT Report
**Consumes:** application/json
**Produces:** text/csv

| Name | In | Type | Required | Description |
| ---- | --- | ---- | -------- | ----------- |
| body | body | ShadowITApplicationRequest | Yes | Information used to generate the Shadow IT Report for the [cloud applications](/zia/about-cloud-applications) recognized by Zscaler based on their usage in your organization. |

| Code | Description | Schema |
| ---- | ----------- | ------ |
| default | Successful Operation |  |

## `POST /shadowIT/applications/{entity}/exportCsv`

Export the Shadow IT Report (in CSV format) for the list of users or known [locations](/zia/about-locations) identified with using the [cloud applications](/zia/about-cloud-applications) specified in the request. This report includes information about each user who has interacted with the application or the known location from where the application is accessed, application category, application usage details, the number of transactions made, last accessed time, etc.
You can customize the report per your requirements by using various filters. To learn more, see [About Application Information](/zia/about-application-information).

**Tags:** Shadow IT Report
**Consumes:** application/json
**Produces:** text/csv

| Name | In | Type | Required | Description |
| ---- | --- | ---- | -------- | ----------- |
| body | body | ShadowITRequest | Yes | Information used to generate the Shadow IT Report for the list of users that have interacted with a specific [cloud application](/zia/about-cloud-applications) or the known [locations](/zia/about-locations) where the cloud application is accessed. |
| entity | path | string | Yes | Indicates whether the Shadow IT Report must be generated to retrieve the list of users who have interacted with a cloud application or the known [locations](/zia/about-locations) where the cloud application is accessed |

| Code | Description | Schema |
| ---- | ----------- | ------ |
| default | Successful Operation |  |

## Models
### CloudApplication
Cloud application information
| Field | Type | Required | Description |
| ----- | ---- | -------- | ----------- |
| applicationIds | array[integer (int32)] | No | The list of cloud application IDs for which the status (sanctioned or unsanctioned) and tags have to be updated |
| customTags | array[CustomTag] | No | The list of custom tags that must be assigned to the cloud applications |
| sanctionedState | string | No | The cloud application status that indicates whether it is sanctioned or unsanctioned |

### CustomTag
Name-ID information of custom tags
| Field | Type | Required | Description |
| ----- | ---- | -------- | ----------- |
| id | integer (int32) | No | Unique identifier of the custom tag |
| name | string | No | The name of the custom tag |

### EntityIdName
| Field | Type | Required | Description |
| ----- | ---- | -------- | ----------- |
| deleted | boolean | No |  |
| description | string | No |  |
| getlId | integer (int64) | No |  |
| id | integer (int32) | No |  |
| name | string | No |  |
| pid | integer (int32) | No |  |

### IncludeExcludeMultiFilterOperationCertKeySize
| Field | Type | Required | Description |
| ----- | ---- | -------- | ----------- |
| operation | string | No |  |
| value | array[string] | No |  |

### IncludeExcludeMultiFilterOperationVendorComplianceID
| Field | Type | Required | Description |
| ----- | ---- | -------- | ----------- |
| operation | string | No |  |
| value | array[string] | No |  |

### NamedItem
| Field | Type | Required | Description |
| ----- | ---- | -------- | ----------- |
| id | integer (int32) | No | Unique identifier of the cloud application |
| name | string | No | The name of the cloud application |

### Order
| Field | Type | Required | Description |
| ----- | ---- | -------- | ----------- |
| by | string | No |  |
| on | string | No |  |

### RangeLong
| Field | Type | Required | Description |
| ----- | ---- | -------- | ----------- |
| max | integer (int64) | No |  |
| min | integer (int64) | No |  |

### ShadowITApplicationRequest
| Field | Type | Required | Description |
| ----- | ---- | -------- | ----------- |
| adminAuditLogs | array[string] | No | Filters the cloud applications based on whether they support admin audit logging. |
| appName | string | No | Filters the data based on the cloud application name that matches the specified string |
| application | array[string] | No | The list of cloud applications for which the Shadow IT Report must be generated. If no value is specified for this parameter, the report is generated for all cloud applications recognized by Zscaler based on their usage in your organization. |
| applicationCategory | array[string] | No | Filters the data based on the cloud application category. |
| certKeySize | IncludeExcludeMultiFilterOperationCertKeySize | No | Filters the data by the size of the SSL certificate public keys used by the cloud applications. The **operation** field indicates whether the specified security certifications are included or excluded, whereas the **value** field specifies the list of security certifications. |
| dataConsumed | array[RangeLong] | No | Filters the data by the cloud application usage in terms of the total amount of data uploaded and downloaded from the application. The min and max fields specify the minimum and maximum values in the range, respectively. |
| dataEncryptionInTransit | array[string] | No | Filters the cloud applications based on whether they support data encryption in transit. |
| dnsCAAPolicy | array[string] | No | Filters the cloud applications by the presence of DNS CAA policy. |
| domainBasedMessageAuthentication | array[string] | No | Filters the cloud applications based on whether they support Domain-based Message Authentication. |
| domainKeysIdentifiedMail | array[string] | No | Filters the cloud applications based on whether they support DomainKeys Identified Mail (DKIM). |
| duration | string | No | (Required) Filters the data by using predefined time frames. |
| employees | array[string] | No | Filters the data based on the employee count of the cloud application vendor. |
| evasive | array[string] | No | Checks if the application supports accessing data anonymously without expecting the user to create an account and log in. If there is no login option, anyone can access the application anonymously without providing their identity. For example, some applications allow users to share files without authenticating them. This can lead malicious users to spread malware and makes identifying the user difficult. |
| fileSharing | array[string] | No | Filters the cloud applications based on whether they include file-sharing provision. |
| hadBreachInLast3Years | array[string] | No | Filters the cloud applications based on whether they are involved in the data breaches reported in the last three years. |
| haveHTTPSecurityHeaderSupport | array[string] | No | Filters the cloud applications by the presence of security headers. |
| havePoorItemsOfService | array[string] | No | Filters the cloud applications based on whether they have questionable parameters in their terms of service. |
| haveWeakCipherSupport | array[string] | No | Filters the cloud applications based on the cryptographic keys used by the application and flags key sizes that are less than 128 bits. |
| malwareScanningContent | array[string] | No | Filters the cloud applications based on whether they include malware content. |
| mfaSupport | array[string] | No | Filters the cloud applications based on whether they support multi-factor authentication. |
| order | Order | No | Sorts the list in increasing or decreasing order based on the specified attribute. The on field specifies which attribute must be sorted, whereas the by field indicates the sorting order as increasing or decreasing. |
| passwordStrength | array[string] | No | Filters the cloud applications based on whether they require strong passwords. |
| remoteAccessScreenSharing | array[string] | No | Filters the cloud applications based on whether they support remote access and screen sharing. |
| riskIndex | array[number (double)] | No | Filters the data based on the risk index assigned to cloud applications. |
| sanctionedState | array[string] | No | Filters the data based on the status of the cloud applications. |
| senderPolicyFramework | array[string] | No | Filters the cloud applications based on whether they support Sender Policy Framework. |
| sourceIpRestriction | array[string] | No | Filters the cloud applications based on whether they have source IP restrictions. |
| sslCertKeyAlgo | array[string] | No | Filters the list of SaaS applications based on the cryptographic signature algorithms used in their SSL/TLS certificates. |
| sslCertificationValidity | array[string] | No | Filters the cloud applications based on whether they have a valid SSL certificate. |
| sslPinned | array[string] | No | Filters the cloud applications based on whether they use SSL Pinning. |
| supportedCertifications | IncludeExcludeMultiFilterOperationVendorComplianceID | No | Filters the cloud applications by security certifications. The **operation** field indicates whether the specified security certifications are included or excluded, whereas the **value** field specifies the list of security certifications. |
| validSSLCertificate | array[string] | No | Filters the cloud applications based on whether they have a valid SSL certificate. |
| vulnerability | array[string] | No | Filters the cloud applications based on whether they have published Common Vulnerabilities and Exposures (CVE). |
| vulnerableDisclosureProgram | array[string] | No | Filters the cloud applications based on whether they support Vulnerability Disclosure Policy. |
| vulnerableToHeartBleed | array[string] | No | Filters the cloud applications based on whether they are vulnerable to Heartbleed attack. |
| vulnerableToLogJam | array[string] | No | Filters the cloud applications based on whether they are vulnerable to Logjam attack. |
| vulnerableToPoodle | array[string] | No | Filters the cloud applications based on whether they are vulnerable to Poodle attack. |
| wafSupport | array[string] | No | Filters the cloud applications based on whether WAF is enabled for the applications. |

### ShadowITRequest
| Field | Type | Required | Description |
| ----- | ---- | -------- | ----------- |
| application | array[string] | No | (Required) The cloud application for which user or location data must be retrieved.
**Note**: Only one cloud application can be specified at a time in this field. |
| dataConsumed | array[RangeLong] | No | Filters the data by the cloud application usage in terms of the total amount of data uploaded and downloaded from the application. The min and max fields specify the minimum and maximum values in the range respectively. |
| departments | array[EntityIdName] | No | Filters the data by department. The id and name fields specify the department information. |
| downloadBytes | array[RangeLong] | No | Filters the data by the cloud application usage in terms of the amount of data (in bytes) downloaded from the application. The min and max fields specify the minimum and maximum values in the range respectively. |
| duration | string | No | (Required) Filters the data by using predefined timeframes. |
| locations | array[EntityIdName] | No | Filters the data by location. The id and name fields specify the location information. |
| order | Order | No | Sorts the list in increasing or decreasing order the specified attribute. The **on** field specifies which attribute must be sorted, whereas the **by** field indicates the sorting order as increasing or decreasing. |
| uploadBytes | array[RangeLong] | No | Filters the data by the cloud application usage in terms of the amount of data (in bytes) uploaded to the application. The min and max fields specify the minimum and maximum values in the range respectively. |
| users | array[EntityIdName] | No | Filters the data by user. The id and name fields specify the user information. |
