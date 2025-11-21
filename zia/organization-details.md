# Organization Details
Source: https://help.zscaler.com/zia/organization-details

API Reference Guide for the ZIA Cloud Service and Sandbox Submission APIs

**Base URL:** https://zsapi.[zscaler-cloud-name]/api/v1

## `GET /orgInformation`

Retrieves detailed organization information, including headquarter location, geolocation, address, and contact details.

**Tags:** Organization Details
**Consumes:** application/json
**Produces:** application/json
No parameters.

| Code | Description | Schema |
| ---- | ----------- | ------ |
| 200 | Successful Operation | OrganizationInformation |

## `GET /orgInformation/lite`

Retrieves minimal organization information.

**Tags:** Organization Details
**Consumes:** application/json
**Produces:** application/json
No parameters.

| Code | Description | Schema |
| ---- | ----------- | ------ |
| 200 | Successful Operation | OrganizationInformationLite |

## `GET /subscriptions`

Retrieves information about the list of subscriptions enabled for your tenant. Subscriptions define the various features and levels of functionality that are available to your organization.

**Tags:** Organization Details
**Consumes:** application/json
**Produces:** application/json
No parameters.

| Code | Description | Schema |
| ---- | ----------- | ------ |
| 200 | Successful Operation | array[Subscription] |

## Models
### OrganizationInformation
Detailed organization information
| Field | Type | Required | Description |
| ----- | ---- | -------- | ----------- |
| addrLine1 | string | No | Address Line 1 |
| addrLine2 | string | No | Address Line 2 |
| alertTimer | string | No | Time after which the alert is resend if condition is not cleared. If not set, the default value of 30 minutes is considered. |
| city | string | No | City |
| cloudName | string | No | Cloud name |
| country | string | No | Country Code |
| customerContactInherit | boolean | No | Customer contact inherit flag |
| domains | array[string] | No | Domain names |
| employeeCount | string | No | Number of employees |
| execInsightsHref | string | No | Contains href to the most recent insights newsletter when available |
| externalEmailPortal | boolean | No | Email portal is an external application |
| geoLocation | string | No | Geographic Region Group |
| hqLocation | string | No | Headquarter location |
| industryVertical | string | No | Industry Vertical Group |
| internalCompany | boolean | No | Internal Company |
| language | string | No | Primary Language. If not set, set to NONE. |
| legacyInsightsReportWasEnabled | boolean | No | Enable the executive report |
| logoBase64Data | string | No | Organization logo data. Base64 encoded. Must use uploadLogo api to update the logo. |
| logoMimeType | string | No | Organization logo file MIME type |
| name | string | No | Name of the organization |
| orgId | integer (int32) | No | Organization identifier |
| pdomain | string | No | Organization pseudo domain |
| primaryBillingContactAltPhone | string | No | Primary billing contact alternate phone number |
| primaryBillingContactEmail | string | No | Primary billing contact email address |
| primaryBillingContactInsightsHref | string | No | Contains href to the most recent insights newsletter when available |
| primaryBillingContactName | string | No | Primary billing contact name |
| primaryBillingContactPhone | string | No | Primary billing contact phone number |
| primaryBillingContactTitle | string | No | Primary billing contact title |
| primaryBillingContactcontactType | string | No | Primary billing contact type |
| primaryBusinessContactAltPhone | string | No | Primary business contact alternate phone number |
| primaryBusinessContactEmail | string | No | Primary business contact email address |
| primaryBusinessContactInsightsHref | string | No | Contains href to the most recent insights newsletter when available |
| primaryBusinessContactName | string | No | Primary business contact name |
| primaryBusinessContactPhone | string | No | Primary business contact phone number |
| primaryBusinessContactTitle | string | No | Primary business contact title |
| primaryBusinessContactcontactType | string | No | Primary business contact type |
| primaryTechnicalContactAltPhone | string | No | Primary technical contact alternate phone number |
| primaryTechnicalContactEmail | string | No | Primary technical contact email address |
| primaryTechnicalContactInsightsHref | string | No | Contains href to the most recent insights newsletter when available |
| primaryTechnicalContactName | string | No | Primary technical contact name |
| primaryTechnicalContactPhone | string | No | Primary technical contact phone number |
| primaryTechnicalContactTitle | string | No | Primary technical contact title |
| primaryTechnicalContactcontactType | string | No | Primary technical contact type |
| secondaryBillingContactAltPhone | string | No | Secondary billing contact alternate phone number |
| secondaryBillingContactEmail | string | No | Secondary billing contact email address |
| secondaryBillingContactInsightsHref | string | No | Contains href to the most recent insights newsletter when available |
| secondaryBillingContactName | string | No | Secondary billing contact name |
| secondaryBillingContactPhone | string | No | Secondary billing contact phone number |
| secondaryBillingContactTitle | string | No | Secondary billing contact title |
| secondaryBillingContactcontactType | string | No | Secondary billing contact type |
| secondaryBusinessContactAltPhone | string | No | Secondary business contact alternate phone number |
| secondaryBusinessContactEmail | string | No | Secondary business contact email address |
| secondaryBusinessContactInsightsHref | string | No | Contains href to the most recent insights newsletter when available |
| secondaryBusinessContactName | string | No | Secondary business contact name |
| secondaryBusinessContactPhone | string | No | Secondary business contact phone number |
| secondaryBusinessContactTitle | string | No | Secondary business contact title |
| secondaryBusinessContactcontactType | string | No | Secondary business contact type |
| secondaryTechnicalContactAltPhone | string | No | Secondary technical contact alternate phone number |
| secondaryTechnicalContactEmail | string | No | Secondary technical contact email address |
| secondaryTechnicalContactInsightsHref | string | No | Contains href to the most recent insights newsletter when available |
| secondaryTechnicalContactName | string | No | Secondary technical contact name |
| secondaryTechnicalContactPhone | string | No | Secondary technical contact phone number |
| secondaryTechnicalContactTitle | string | No | Secondary technical contact title |
| secondaryTechnicalContactcontactType | string | No | Secondary technical contact type |
| state | string | No | State |
| timezone | string | No | Primary Time Zone. If not set, set to GMT. |
| zipcode | string | No | Zip Code |
| zpaTenantCloud | string | No | ZPA tenant cloud |
| zpaTenantId | integer (int64) | No | ZPA tenant Id |

### OrganizationInformationLite
Minimal organization information
| Field | Type | Required | Description |
| ----- | ---- | -------- | ----------- |
| cloudName | string | No | Cloud name |
| domains | array[string] | No | Domain names |
| language | string | No | Primary Language. If not set, set to NONE. |
| name | string | No | Name of the organization |
| orgDisabled | boolean | No | Specifies whether an organization's information is disabled. This field is disabled by default. |
| orgId | integer (int32) | No | Organization identifier |
| timezone | string | No | Primary Time Zone. If not set, set to GMT. |

### Subscription
Information about subscriptions
| Field | Type | Required | Description |
| ----- | ---- | -------- | ----------- |
| cellCount | string | No | Specifies the number of cells that can contain data when a template is uploaded to the Advanced Data Protection tool |
| endDate | integer (int32) | No | The subscription end time in Unix time format |
| id | string | No | The unique identifier of the subscription |
| licenses | integer (int32) | No | The number of licenses owned by the tenant under the subscription. The license could be for users, Virtual Service Edges, proxy ports, NSS feeds, etc. |
| sku | string | No | The ID of the service enabled through the subscription |
| startDate | integer (int32) | No | The subscription start time in Unix time format |
| state | string | No | The current state of the subscription indicating whether it is active, expired, disabled, or not started. |
| status | string | No | The status of the subscription indicating whether it is on trial, expired and disabled, not subscribed, subscribed, or temporarily extended. |
| strEndDate | string | No | The subscription end date in `MM/DD/YYYY` format |
| strStartDate | string | No | The subscription start date in `MM/DD/YYYY` format |
| subscribed | boolean | No | A Boolean value indicating that the subscription is active or is not started |
| updatedAtTimestamp | integer (int64) | No | The timestamp in Unix time format when the subscription was last updated |
