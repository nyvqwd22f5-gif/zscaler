# Browser Control Policy
Source: https://help.zscaler.com/zia/browser-control-policy

API Reference Guide for the ZIA Cloud Service and Sandbox Submission APIs

**Base URL:** https://zsapi.[zscaler-cloud-name]/api/v1

## `GET /browserControlSettings`

Retrieves the Browser Control status and the list of configured browsers in the Browser Control policy

**Tags:** Browser Control Policy
**Consumes:** application/json
**Produces:** application/json
No parameters.

| Code | Description | Schema |
| ---- | ----------- | ------ |
| 200 | Successful Operation | BrowserControlSettings |

## `PUT /browserControlSettings`

Updates the Browser Control settings. To learn more, see [Configuring the Browser Control Policy](/zia/configuring-browser-control-policy).

**Tags:** Browser Control Policy
**Consumes:** application/json
**Produces:** application/json
No parameters.

| Code | Description | Schema |
| ---- | ----------- | ------ |
| 200 | Successful Operation | BrowserControlSettings |

## Models
### BrowserControlSettings
Browser Control Settings
| Field | Type | Required | Description |
| ----- | ---- | -------- | ----------- |
| allowAllBrowsers | boolean | No | A Boolean value that specifies whether or not to allow all the browsers and their respective versions access to the internet |
| blockedChromeVersions | array[string] | No | Versions of Google Chrome browser that need to be blocked. If not set, all Google Chrome versions are allowed. |
| blockedFirefoxVersions | array[string] | No | Versions of Mozilla Firefox browser that need to be blocked. If not set, all Mozilla Firefox versions are allowed. |
| blockedInternetExplorerVersions | array[string] | No | Versions of Microsoft browser that need to be blocked. If not set, all Microsoft browser versions are allowed. |
| blockedOperaVersions | array[string] | No | Versions of Opera browser that need to be blocked. If not set, all Opera versions are allowed. |
| blockedSafariVersions | array[string] | No | Versions of Apple Safari browser that need to be blocked. If not set, all Apple Safari versions are allowed. |
| bypassAllBrowsers | boolean | No | If set to true, all the browsers are bypassed for warnings. If not set, all vulnerable browsers are warned. This attribute has effect only if the 'enableWarnings' is set to true. |
| bypassApplications | array[string] | No | List of applications that need to be bypassed for warnings. This attribute has effect only if the 'enableWarnings' attribute is set to true. If not set, all vulnerable applications are warned. |
| bypassPlugins | array[string] | No | List of plugins that need to be bypassed for warnings. This attribute has effect only if the 'enableWarnings' attribute is set to true. If not set, all vulnerable plugins are warned. |
| enableSmartBrowserIsolation | boolean | No | A Boolean value that specifies if Smart Browser Isolation is enabled |
| enableWarnings | boolean | No | A Boolean value that specifies if the warnings are enabled |
| pluginCheckFrequency | string | No | Specifies how frequently the service checks browsers and relevant applications to warn users regarding outdated or vulnerable browsers, plugins, and applications. If not set, the warnings are disabled |
| smartIsolationGroups | array[EntityReference] | No | Name-ID pairs of groups for which the rule is applied |
| smartIsolationProfile | BrowserIsolationProfile | No | The isolation profile. To learn more, see [Creating Isolation Profiles for ZIA](/zia/creating-isolation-profiles-zia). |
| smartIsolationProfileId | integer (int32) | No | The isolation profile ID |
| smartIsolationUsers | array[EntityReference] | No | Name-ID pairs of users for which the rule is applied |

### BrowserIsolationProfile
Information about browser isolation profile. To learn more, see [What Is Isolation?](/isolation/what-isolation) and [Creating Isolation Profiles for ZIA](/isolation/creating-zia-isolation-profile-isolation).
| Field | Type | Required | Description |
| ----- | ---- | -------- | ----------- |
| defaultProfile | boolean | No | (Optional) Indicates whether this is a default browser isolation profile. Zscaler sets this field. |
| id | string | No | The universally unique identifier (UUID) for the browser isolation profile |
| name | string | No | Name of the browser isolation profile |
| url | string | No | The browser isolation profile URL |

### EntityReference
This is an immutable reference to an entity that mainly consists of id and name
| Field | Type | Required | Description |
| ----- | ---- | -------- | ----------- |
| extensions | object | No | Additional information about the entity |
| externalId | string | No | An external identifier used for an entity that is managed outside of ZIA. Examples include `zpaServerGroup` and `zpaAppSegments`. This field is not applicable to ZIA-managed entities. |
| id | integer (int64) | No | A unique identifier for an entity |
| name | string | No | The configured name of the entity |
