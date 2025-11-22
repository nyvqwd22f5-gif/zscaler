# Organizations
Source: https://help.zscaler.com/easm/organizations

API Reference Guide for the Zscaler EASM API

**Base URL:** https://localhost:8080/easm-ui/v1

## `GET /organizations`

Retrieves all organizations configured for a tenant in the EASM Admin Portal

**Tags:** Organizations
**Produces:** application/json

| Name | In | Type | Required | Description |
| ---- | --- | ---- | -------- | ----------- |
| Authorization | header | string | Yes | API authentication token |

| Code | Description | Schema |
| ---- | ----------- | ------ |
| 200 | OK | organizations.GetOrganizationsResponse |
| 401 | Unauthorized |  |
| 500 | Internal Server Error |  |

## Models
### administration.Organization
Information about an organization configured in EASM
| Field | Type | Required | Description |
| ----- | ---- | -------- | ----------- |
| id | string | No | The unique identifier of an organization |
| name | string | No | The name of an organization |

### organizations.GetOrganizationsResponse
| Field | Type | Required | Description |
| ----- | ---- | -------- | ----------- |
| next_page | integer | No |  |
| prev_page | integer | No |  |
| results | array[administration.Organization] | No | Details obtained for the organizations |
| total_results | integer | No | The total number of organizations present in the response |
