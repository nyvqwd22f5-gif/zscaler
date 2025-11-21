# Policy Export
Source: https://help.zscaler.com/zia/policy-export

API Reference Guide for the ZIA Cloud Service and Sandbox Submission APIs

**Base URL:** https://zsapi.[zscaler-cloud-name]/api/v1

## `POST /exportPolicies`

Exports the specified policies to a ZIP file. This API request supports exporting a wide range of policy types, and you can view the list of supported policy types in the Enum list included in the request's body parameter.
The API response is one ZIP file containing JSON representation of the exported policies. One JSON file is created for each policy type specified in the request input. For example, if the request body specifies three policy types, such as FIREWALL, BA, and URL_FILTERING, the API response is exported as one ZIP file containing three JSON files, one for each policy type, named firewall.json, ba.json, and url_filtering.json.

**Tags:** Policy Export
**Consumes:** application/json
**Produces:** application/json, application/octet-stream

| Name | In | Type | Required | Description |
| ---- | --- | ---- | -------- | ----------- |
| body | body | array[string] | Yes | Specifies the list of policy types for which the rules must be exported |

| Code | Description | Schema |
| ---- | ----------- | ------ |
| default | Successful Operation |  |
