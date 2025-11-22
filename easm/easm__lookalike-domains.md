# Lookalike Domains
Source: https://help.zscaler.com/easm/lookalike-domains

API Reference Guide for the Zscaler EASM API

**Base URL:** https://localhost:8080/easm-ui/v1

## `GET /organizations/:orgId/lookalike-domains`

Retrieves the list of lookalike domains for an organization based on the specified ID

**Tags:** Lookalike Domains
**Produces:** application/json

| Name | In | Type | Required | Description |
| ---- | --- | ---- | -------- | ----------- |
| Authorization | header | string | Yes | API authentication token |

| Code | Description | Schema |
| ---- | ----------- | ------ |
| 200 | OK | lookalikeDomains.GetLookalikeDomainsResponse |
| 400 | Bad Request |  |
| 401 | Unauthorized |  |
| 500 | Internal Server Error |  |

## `GET /organizations/:orgId/lookalike-domains/:lookalikeRaw/details`

Retrieves details for a lookalike domain based on the specified ID

**Tags:** Lookalike Domains
**Produces:** application/json

| Name | In | Type | Required | Description |
| ---- | --- | ---- | -------- | ----------- |
| Authorization | header | string | Yes | API authentication token |

| Code | Description | Schema |
| ---- | ----------- | ------ |
| 200 | OK | lookalikeDomains.GetLookalikeDomainsResponse |
| 400 | Bad Request |  |
| 401 | Unauthorized |  |
| 500 | Internal Server Error |  |

## Models
### lookalikeDomain.LookalikeDomainRiskCategory
The list of lookalike domain categories available

### lookalikeDomain.LookalikeDomainStatus
The list of available statuses for lookalike domains

### lookalikeDomains.DeceptionMethod
The list of deception methods used by lookalike domain names for impersonating legitimate domains

### lookalikeDomains.GetLookalikeDomainsResponse
| Field | Type | Required | Description |
| ----- | ---- | -------- | ----------- |
| results | array[lookalikeDomains.LookalikeDomainDetails] | No | The list of lookalike domains identified for the seed domains configured for an organization |
| total_results | integer | No | The total number of lookalike domains present in the response |

### lookalikeDomains.LookalikeDomainDetails
Information about lookalike domains
| Field | Type | Required | Description |
| ----- | ---- | -------- | ----------- |
| created_date | string | No | The timestamp when the lookalike domain was detected in a scan and added to EASM |
| deception_method | array[lookalikeDomains.DeceptionMethod] | No | One or more deception methods used in the lookalike domain name to impersonate a legitimate domain |
| description | string | No | A description of the lookalike domain, why it is suspicious, and the deception tactics used. |
| expiration_date | string | No | The domain registration expiration date, if available. |
| is_registered | boolean | No | Indicates whether the domain is registered with a registrar or not |
| lookalike_raw | string | No | The lookalike domain URL |
| original_domain | string | No | The legitimate domain mimicked by the lookalike domain |
| registered_by | string | No | An individual or entity that owns the registered domain, if available. |
| registrar | string | No | The internet company that was used to register the domain, if available. |
| remediation | string | No | Risk remediation recommendations for the lookalike domain |
| risk_category | lookalikeDomain.LookalikeDomainRiskCategory | No | The risk categorization of the lookalike domain |
| risk_score | integer | No | A risk score assigned to the lookalike domain |
| status | lookalikeDomain.LookalikeDomainStatus | No | The status assigned to the lookalike domain entry |
| updated_date | string | No | The timestamp when the lookalike domain's status was last updated |
