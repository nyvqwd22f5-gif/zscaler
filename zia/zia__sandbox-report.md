# Sandbox Report
Source: https://help.zscaler.com/zia/sandbox-report

API Reference Guide for the ZIA Cloud Service and Sandbox Submission APIs

**Base URL:** https://zsapi.[zscaler-cloud-name]/api/v1

## `GET /sandbox/report/quota`

The resource access quota for retrieving Sandbox Detail Reports is restricted to 3,000 requests per day, with a rate limit of 2/sec and 1,000/hour. Use GET `/sandbox/report/quota` to retrieve details regarding your organization's daily Sandbox API resource usage (i.e., used quota, unused quota).

**Tags:** Sandbox Report
**Consumes:** application/json
**Produces:** application/json
No parameters.

| Code | Description | Schema |
| ---- | ----------- | ------ |
| 200 | Successful Operation | array[RatingQuota] |

## `GET /sandbox/report/{md5Hash}`

Gets a full (i.e., complete) or summary detail report for an MD5 hash of a file that was analyzed by Sandbox. To view a full summary report response example, as well as possible enum values for various Sandbox Report attributes, see [Sandbox Report Use Cases](/zia/sandbox-report-use-cases).

**Tags:** Sandbox Report
**Consumes:** application/json
**Produces:** application/json

| Name | In | Type | Required | Description |
| ---- | --- | ---- | -------- | ----------- |
| md5Hash | path | string | Yes | MD5 hash of the file that was analyzed by Sandbox. |
| details | query | string | No | Type of report, full or summary. |

| Code | Description | Schema |
| ---- | ----------- | ------ |
| 200 | Successful Operation | object |

## Models
### RatingQuota
API usage quota details.
| Field | Type | Required | Description |
| ----- | ---- | -------- | ----------- |
| allowed | integer (int64) | No | Allowed daily quota |
| scale | string | No | Scale Unit (i.e., DAYS) |
| startTime | integer (int64) | No | Start time |
| unused | integer (int64) | No | Unused daily quota |
| used | integer (int64) | No | Used daily quota |
