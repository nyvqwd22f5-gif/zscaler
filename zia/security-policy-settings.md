# Security Policy Settings
Source: https://help.zscaler.com/zia/security-policy-settings

API Reference Guide for the ZIA Cloud Service and Sandbox Submission APIs

**Base URL:** https://zsapi.[zscaler-cloud-name]/api/v1

## `GET /security`

Gets a list of URLs that are on the allowlist.

**Tags:** Security Policy Settings
**Consumes:** application/json
**Produces:** application/json
No parameters.

| Code | Description | Schema |
| ---- | ----------- | ------ |
| 200 | Successful Operation | SecurityPolicy |

## `PUT /security`

Updates the list of URLs on the allowlist. This overwrites a previously-generated allowlist. If you need to completely erase the allowlist, submit an empty list.

**Tags:** Security Policy Settings
**Consumes:** application/json
**Produces:** application/json

| Name | In | Type | Required | Description |
| ---- | --- | ---- | -------- | ----------- |
| policy | body | SecurityPolicy | No | Updates the security policy. |

| Code | Description | Schema |
| ---- | ----------- | ------ |
| 200 | Successful Operation | SecurityPolicy |

## `GET /security/advanced`

Gets a list of URLs that are on the denylist.

**Tags:** Security Policy Settings
**Consumes:** application/json
**Produces:** application/json
No parameters.

| Code | Description | Schema |
| ---- | ----------- | ------ |
| 200 | Successful Operation | AdvancedSecurityPolicy |

## `PUT /security/advanced`

Updates the list of URLs that are on the denylist. This overwrites a previously-generated denylist. If you need to completely erase the denylist, submit an empty list.

**Tags:** Security Policy Settings
**Consumes:** application/json
**Produces:** application/json

| Name | In | Type | Required | Description |
| ---- | --- | ---- | -------- | ----------- |
| advSettings | body | AdvancedSecurityPolicy | No | Updates the Advanced Threat Protection policy's denylist. |

| Code | Description | Schema |
| ---- | ----------- | ------ |
| 200 | Successful Operation | AdvancedSecurityPolicy |

## `POST /security/advanced/blacklistUrls`

Adds a URL to or removes a URL from the denylist. To add a URL to the denylist, set the action parameter to `ADD_TO_LIST`. To remove a URL, set action to `REMOVE_FROM_LIST`.

**Tags:** Security Policy Settings
**Consumes:** application/json
**Produces:** application/json

| Name | In | Type | Required | Description |
| ---- | --- | ---- | -------- | ----------- |
| action | query | string | Yes | The action applied to the Advanced Threat Protection policy’s denylist (i.e., adding a URL or removing a URL). |

| Code | Description | Schema |
| ---- | ----------- | ------ |
| 200 | Successful Operation | AdvancedSecurityPolicy |

## Models
### AdvancedSecurityPolicy
Advanced Security Policy
| Field | Type | Required | Description |
| ----- | ---- | -------- | ----------- |
| blacklistUrls | array[string] | No | URLs on the denylist for your organization. Allow up to 25000 URLs. |

### SecurityPolicy
Security Policy
| Field | Type | Required | Description |
| ----- | ---- | -------- | ----------- |
| whitelistUrls | array[string] | No | Allowlist URLs whose contents are not scanned. Allows up to 255 URLs. There may be trusted websites the content of which might be blocked due to anti-virus, anti-spyware, or anti-malware policies. Enter the URLs of sites you do not want scanned. The service allows users to download content from these URLs without inspecting the traffic. The allowlist applies to the Malware Protection, Advanced Threats Protection, and Sandbox policies. |
