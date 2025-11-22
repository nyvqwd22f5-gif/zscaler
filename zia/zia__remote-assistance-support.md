# Remote Assistance Support
Source: https://help.zscaler.com/zia/remote-assistance-support

API Reference Guide for the ZIA Cloud Service and Sandbox Submission APIs

**Base URL:** https://zsapi.[zscaler-cloud-name]/api/v1

## `GET /remoteAssistance`

Retrieves information about the Remote Assistance option configured in the ZIA Admin Portal. Using this option, you can allow Zscaler Support to access your organization’s ZIA Admin Portal for a specified time period to troubleshoot issues. To learn more, see [Enabling Remote Assistance](/zia/enabling-remote-assistance).

**Tags:** Remote Assistance Support
**Consumes:** application/json
**Produces:** application/json
No parameters.

| Code | Description | Schema |
| ---- | ----------- | ------ |
| 200 | Successful Operation | RemoteAssistance |

## `PUT /remoteAssistance`

Retrieves information about the Remote Assistance option configured in the ZIA Admin Portal. Using this option, you can allow Zscaler Support to access your organization’s ZIA Admin Portal for a specified time period to troubleshoot issues. To learn more, see [Enabling Remote Assistance](/zia/enabling-remote-assistance).

**Tags:** Remote Assistance Support
**Consumes:** application/json
**Produces:** application/json
No parameters.

| Code | Description | Schema |
| ---- | ----------- | ------ |
| default | Successful Operation |  |

## Models
### RemoteAssistance
Remote Assistance preferences
| Field | Type | Required | Description |
| ----- | ---- | -------- | ----------- |
| deviceInfoObfuscate | boolean | No | A Boolean value that indicates whether the device information (Device Hostname, Device Name, and Device Owner) should be obfuscated or visible on the Dashboard and Analytics pages |
| fullAccessUntil | integer (int64) | No | A Boolean value that indicates whether the user names for single sign-on users should be obfuscated or visible |
| usernameObfuscated | boolean | No | A Boolean value that indicates whether the user names for single sign-on users should be obfuscated or visible |
| viewOnlyUntil | integer (int64) | No | The time until when view-only access is granted. Unix time is used. |
