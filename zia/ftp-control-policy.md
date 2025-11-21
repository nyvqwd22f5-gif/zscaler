# FTP Control Policy
Source: https://help.zscaler.com/zia/ftp-control-policy

API Reference Guide for the ZIA Cloud Service and Sandbox Submission APIs

**Base URL:** https://zsapi.[zscaler-cloud-name]/api/v1

## `GET /ftpSettings`

Retrieves the FTP Control status and the list of URL categories for which FTP is allowed. To learn more, see [About FTP Control](/zia/about-ftp-control).

**Tags:** FTP Control Policy
**Consumes:** application/json
**Produces:** application/json
No parameters.

| Code | Description | Schema |
| ---- | ----------- | ------ |
| 200 | Successful Operation | FtpSettings |

## `PUT /ftpSettings`

Updates the FTP Control settings. To learn more, see [Configuring the FTP Control Policy](/zia/configuring-ftp-control-policy).

**Tags:** FTP Control Policy
**Consumes:** application/json
**Produces:** application/json

| Name | In | Type | Required | Description |
| ---- | --- | ---- | -------- | ----------- |
| body | body | FtpSettings | No | Information about FTP settings |

| Code | Description | Schema |
| ---- | ----------- | ------ |
| 200 | Successful Operation | FtpSettings |

## Models
### FtpSettings
FTP settings information
| Field | Type | Required | Description |
| ----- | ---- | -------- | ----------- |
| ftpEnabled | boolean | Yes | Indicates whether to enable native FTP. When enabled, users can connect to native FTP sites and download files. |
| ftpOverHttpEnabled | boolean | Yes | Indicates whether to enable FTP over HTTP. By default, the Zscaler service doesn't allow users from a location to upload or download files from FTP sites that use FTP over HTTP. Select this to enable browsers to connect to FTP over HTTP sites and download files. If a remote user uses a dedicated port, then the service supports FTP over HTTP for them. |
| urlCategories | array[WebFilteringUrlCategory] | No | List of URL categories that allow FTP traffic |
| urls | array[string] | No | Domains or URLs included for the FTP Control settings |

### WebFilteringUrlCategory
| Field | Type | Required | Description |
| ----- | ---- | -------- | ----------- |
| backendName | string | No | URL category back end name |
| comments | string | No | Additional information about the URL category |
| deprecated | boolean | No | List of deprecated URL categories |
| name | string | No | The name of the URL category listed under the respective super category |
| urlSupercategory | string | No | Super category of the URL category. This field is required when creating custom URL categories. |
| userConfiguredName | string | No | User-configured URL category name |
