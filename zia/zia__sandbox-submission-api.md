# Sandbox Submission API
Source: https://help.zscaler.com/zia/sandbox-submission-api

API Reference Guide for the ZIA Cloud Service and Sandbox Submission APIs

**Base URL:** https://zsapi.[zscaler-cloud-name]/api/v1

## `POST /zscsb/discan`

Submits raw or archive files (e.g., ZIP) to the Zscaler service for out-of-band file inspection to generate real-time verdicts for known and unknown files. It leverages capabilities such as Malware Prevention, Advanced Threat Prevention, Sandbox cloud effect, AI/ML-driven file analysis, and integrated third-party threat intelligence feeds to inspect files and classify them as benign or malicious instantaneously.
All file types supported by [Malware Protection](/zia/configuring-malware-protection-policy) and [Advanced Threat Protection](/zia/configuring-advanced-threat-protection-policy) policies can be inspected with a file size limit of up to 400 MB for AI/ML, Malware, and Advanced Threat Protection and 20 MB for Sandbox and in a large volume of files.
**Note**: Dynamic file analysis is not included in out-of-band file inspection.

**Tags:** Sandbox Submission API
**Produces:** application/json

| Name | In | Type | Required | Description |
| ---- | --- | ---- | -------- | ----------- |
| api_token | query | string | Yes | The Sandbox API token obtained from the ZIA Admin Portal to be used for authenticating the Sandbox Submission API. To learn more, see [Managing Sandbox API Token](/zia/about-sandbox-api-token). |

| Code | Description | Schema |
| ---- | ----------- | ------ |
| 200 | Successful Operation | DIScanSubmissionResponse |

## `POST /zscsb/submit`

Submits raw or archive files (e.g., ZIP) to Sandbox for analysis. You can submit up to 100 files per day and it supports all file types that are currently supported by Sandbox. To learn more, see [About Sandbox](/zia/about-sandbox). By default, files are scanned by Zscaler antivirus (AV) and submitted directly to the sandbox in order to obtain a verdict. However, if a verdict already exists for the file, you can use the 'force' parameter to make the sandbox to reanalyze it.
You must have a Sandbox policy rule configured within the ZIA Admin Portal in order to analyze files that aren't present in the default policy rule. Ensure that you have explicitly added Sandbox policy rules that include the appropriate file types within your request. If not, an 'Unknown' message is shown in the response.
To learn more, see [Configuring the Sandbox Policy](/zia/configuring-sandbox-policy) and [Configuring the Default Sandbox Rule](/zia/configuring-default-sandbox-rule).
After files are sent for analysis, you must use GET /sandbox/report/{md5Hash} in order to retrieve the verdict. You can get the Sandbox report 10 minutes after a file is sent for analysis.

**Tags:** Sandbox Submission API
**Produces:** application/json

| Name | In | Type | Required | Description |
| ---- | --- | ---- | -------- | ----------- |
| api_token | query | string | Yes | The Sandbox API token obtained from the ZIA Admin Portal to be used for authenticating the Sandbox Submission API. To learn more, see [Managing Sandbox API Token](/zia/about-sandbox-api-token). |
| force | query | string | No | Submit file to sandbox even if found malicious during AV scan and a verdict already exists. |

| Code | Description | Schema |
| ---- | ----------- | ------ |
| 200 | Successful Operation | SandboxSubmissionResponse |

## Models
### DIScanSubmissionResponse
Information about the file inspection results
| Field | Type | Required | Description |
| ----- | ---- | -------- | ----------- |
| code | string | No | The response code |
| fileType | string | No | The file type of the submitted file |
| md5 | string | No | The MD5 hash of the submitted file |
| message | string | No | The response message that indicates whether the file is malicious or not |
| virusName | string | No | The threat name associated to a malicious file |
| virusType | string | No | The threat category asscociated to a malicious file |

### SandboxSubmissionResponse
Sandbox submission response information.
| Field | Type | Required | Description |
| ----- | ---- | -------- | ----------- |
| code | string | No | The response code |
| fileType | string | No | The file type of the submitted file |
| md5 | string | No | The MD5 hash of the submitted file |
| message | string | No | The response message |
| sandboxSubmission | string | No | Sandbox status of the submitted file |
| virusName | string | No | The threat name associated to a malicious file |
| virusType | string | No | The threat category asscociated to a malicious file |
