# Browser Isolation
Source: https://help.zscaler.com/zia/browser-isolation

API Reference Guide for the ZIA Cloud Service and Sandbox Submission APIs

**Base URL:** https://zsapi.[zscaler-cloud-name]/api/v1

## `GET /browserIsolation/profiles`

Gets a list of all the cloud browser isolation profiles in the Isolation Profile field for [URL Filtering Policy](/zia/configuring-url-filtering-policy#Action) and [Cloud App Control Policy](/zia/adding-rules-cloud-app-control-policy) rules.

**Tags:** Browser Isolation
**Consumes:** application/json
**Produces:** application/json
No parameters.

| Code | Description | Schema |
| ---- | ----------- | ------ |
| 200 | Successful Operation | array[BrowserIsolationProfile] |

## Models
### BrowserIsolationProfile
Information about browser isolation profile. To learn more, see [What Is Isolation?](/isolation/what-isolation) and [Creating Isolation Profiles for ZIA](/isolation/creating-zia-isolation-profile-isolation).
| Field | Type | Required | Description |
| ----- | ---- | -------- | ----------- |
| defaultProfile | boolean | No | (Optional) Indicates whether this is a default browser isolation profile. Zscaler sets this field. |
| id | string | No | The universally unique identifier (UUID) for the browser isolation profile |
| name | string | No | Name of the browser isolation profile |
| url | string | No | The browser isolation profile URL |
