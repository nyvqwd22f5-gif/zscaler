# Findings
Source: https://help.zscaler.com/easm/findings

API Reference Guide for the Zscaler EASM API

**Base URL:** https://localhost:8080/easm-ui/v1

## `GET /organizations/:orgId/findings`
Retrieves the list of findings identified and tracked for an organization's internet-facing assets scanned by EASM

**Tags:** Findings
**Produces:** application/json

| Name | In | Type | Required | Description |
| ---- | --- | ---- | -------- | ----------- |
| Authorization | header | string | Yes | API authentication token |

| Code | Description | Schema |
| ---- | ----------- | ------ |
| 200 | OK | findings.GetFindingsResponse |
| 400 | Bad Request |  |
| 401 | Unauthorized |  |
| 500 | Internal Server Error |  |

## `GET /organizations/:orgId/findings/:findingId/details`

Retrieves details for a finding based on the specified ID

**Tags:** Findings
**Produces:** application/json

| Name | In | Type | Required | Description |
| ---- | --- | ---- | -------- | ----------- |
| Authorization | header | string | Yes | API authentication token |

| Code | Description | Schema |
| ---- | ----------- | ------ |
| 200 | OK | findings.GetFindingDetailsResponse |
| 401 | Unauthorized |  |
| 500 | Internal Server Error |  |

## `GET /organizations/:orgId/findings/:findingId/evidence`

Retrieves scan evidence details for a finding based on the specified ID. This is a subset of the scan output obtained for the associated asset that can be attributed to the finding.

**Tags:** Findings
**Produces:** application/json

| Name | In | Type | Required | Description |
| ---- | --- | ---- | -------- | ----------- |
| Authorization | header | string | Yes | API authentication token |

| Code | Description | Schema |
| ---- | ----------- | ------ |
| 200 | OK | findings.GetScanOutputResponse |
| 401 | Unauthorized |  |
| 500 | Internal Server Error |  |

## `GET /organizations/:orgId/findings/:findingId/scan-output`

Retrieves the complete scan output for a finding based on the specified ID

**Tags:** Findings
**Produces:** application/json

| Name | In | Type | Required | Description |
| ---- | --- | ---- | -------- | ----------- |
| Authorization | header | string | Yes | API authentication token |

| Code | Description | Schema |
| ---- | ----------- | ------ |
| 200 | OK | findings.GetScanOutputResponse |
| 401 | Unauthorized |  |
| 500 | Internal Server Error |  |

## Models
### bitbucket_corp_zscaler_com_easm_easm-ui_internal_controllers_publicApi_findings.Finding
Information about findings
| Field | Type | Required | Description |
| ----- | ---- | -------- | ----------- |
| category | string | No | The finding's classification such as Exposure, Vulnerability, or Misconfiguration. |
| cisa_likelihood | string | No | Indicates whether a vulnerability is listed in the [Known Exploited Vulnerabilities (KEV) catalog, if applicable.](https://www.cisa.gov/known-exploited-vulnerabilities-catalog) |
| country | string | No | The geographical location of the asset to which the finding is associated |
| description | string | No | A detailed description of the finding gathered from open-source intelligence, such as the [National Vulnerability Database (NVD)](https://nvd.nist.gov/), and Zscaler's research team. |
| epss_likelihood | string | No | The Exploit Prediction Scoring System (EPSS) likelihood indicates the probability of a vulnerability being exploited in the wild, if applicable. |
| first_seen | string | No | The timestamp when the finding was first detected in the associated asset |
| id | string | No | Finding ID |
| impacted_asset_id | string | No | The ID of the asset to which the finding is associated |
| impacted_asset_name | string | No | The name of the asset to which the finding is associated |
| is_stale | boolean | No | A Boolean value that indicates if the asset was not detected in a scan for over 30 days and is therefore marked as stale |
| last_seen | string | No | The timestamp when the finding was last detected during scanning |
| name | string | No | Finding name |
| profile_id | string | No | ID of the Discovery Profile through which this finding was detected |
| risk_level | string | No | The risk level assigned to the finding ranging from Low, Medium, High, and Critical. |
| risk_score | string | No | A risk score computed for the finding ranging from 1 to 100 |
| scan_type | string | No | The scanning service that was used to uncover the risk, such as Web, Network, Certificate, and DNS scans. |
| severity_score | number | No | The Common Vulnerability Scoring System (CVSS) score that indicates the qualitative measure of severity of a vulnerability using a numerical value ranging from 1 to 10, if applicable. |
| status | string | No | Indicates the finding's current status in its workflow tracked from discovery to closure |
| type | string | No | The finding's type which is a sub-classification within the assigned `category` |

### findings.GetFindingDetailsResponse
Information about findings
| Field | Type | Required | Description |
| ----- | ---- | -------- | ----------- |
| category | string | No | The finding's classification such as Exposure, Vulnerability, or Misconfiguration. |
| cisa_likelihood | string | No | Indicates whether a vulnerability is listed in the [Known Exploited Vulnerabilities (KEV) catalog, if applicable.](https://www.cisa.gov/known-exploited-vulnerabilities-catalog) |
| country | string | No | The geographical location of the asset to which the finding is associated |
| description | string | No | A detailed description of the finding gathered from open-source intelligence, such as the [National Vulnerability Database (NVD)](https://nvd.nist.gov/), and Zscaler's research team. |
| epss_likelihood | string | No | The Exploit Prediction Scoring System (EPSS) likelihood indicates the probability of a vulnerability being exploited in the wild, if applicable. |
| first_seen | string | No | The timestamp when the finding was first detected in the associated asset |
| id | string | No | Finding ID |
| impacted_asset_id | string | No | The ID of the asset to which the finding is associated |
| impacted_asset_name | string | No | The name of the asset to which the finding is associated |
| is_stale | boolean | No | A Boolean value that indicates if the asset was not detected in a scan for over 30 days and is therefore marked as stale |
| last_seen | string | No | The timestamp when the finding was last detected during scanning |
| name | string | No | Finding name |
| profile_id | string | No | ID of the Discovery Profile through which this finding was detected |
| risk_level | string | No | The risk level assigned to the finding ranging from Low, Medium, High, and Critical. |
| risk_score | string | No | A risk score computed for the finding ranging from 1 to 100 |
| scan_type | string | No | The scanning service that was used to uncover the risk, such as Web, Network, Certificate, and DNS scans. |
| severity_score | number | No | The Common Vulnerability Scoring System (CVSS) score that indicates the qualitative measure of severity of a vulnerability using a numerical value ranging from 1 to 10, if applicable. |
| status | string | No | Indicates the finding's current status in its workflow tracked from discovery to closure |
| type | string | No | The finding's type which is a sub-classification within the assigned `category` |

### findings.GetFindingsResponse
Information about findings
| Field | Type | Required | Description |
| ----- | ---- | -------- | ----------- |
| results | array[bitbucket_corp_zscaler_com_easm_easm-ui_internal_controllers_publicApi_findings.Finding] | No | The list of findings detected for an organization |
| total_results | integer | No | The total number of findings in the response |

### findings.GetScanOutputResponse
| Field | Type | Required | Description |
| ----- | ---- | -------- | ----------- |
| content | string | No | The scan output information |
| source_type | string | No | The scanning service used to detect the risk, such as Web, Network, Certificate, or DNS scans. |
