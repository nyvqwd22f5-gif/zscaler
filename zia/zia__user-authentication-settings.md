# User Authentication Settings
Source: https://help.zscaler.com/zia/user-authentication-settings

API Reference Guide for the ZIA Cloud Service and Sandbox Submission APIs

**Base URL:** https://zsapi.[zscaler-cloud-name]/api/v1

## `GET /authSettings/exemptedUrls`

Gets a list of URLs that were exempted from [cookie authentication](/zia/about-zscaler-cookies). To learn more, see [URL Format Guidelines](/zia/url-format-guidelines).

**Tags:** User Authentication Settings
**Consumes:** application/json
**Produces:** application/json
No parameters.

| Code | Description | Schema |
| ---- | ----------- | ------ |
| 200 | Successful Operation | Urls |

## `POST /authSettings/exemptedUrls`

Adds a URL to or removes a URL from the [cookie authentication](/zia/about-zscaler-cookies) exempt list. To add a URL to the list, set the action parameter to `ADD_TO_LIST`. To remove a URL, set action to `REMOVE_FROM_LIST`.

**Tags:** User Authentication Settings
**Consumes:** application/json
**Produces:** application/json

| Name | In | Type | Required | Description |
| ---- | --- | ---- | -------- | ----------- |
| action | query | string | Yes | The action applied to the exempted URLs list (i.e., adding a URL or removing a URL). |

| Code | Description | Schema |
| ---- | ----------- | ------ |
| 200 | Successful Operation | Urls |

## Models
### Urls
| Field | Type | Required | Description |
| ----- | ---- | -------- | ----------- |
| urls | array[string] | No | Domains or URLs which are exempted from SSL Inspection |
