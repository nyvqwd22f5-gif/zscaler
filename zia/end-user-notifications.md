# End User Notifications
Source: https://help.zscaler.com/zia/end-user-notifications

API Reference Guide for the ZIA Cloud Service and Sandbox Submission APIs

**Base URL:** https://zsapi.[zscaler-cloud-name]/api/v1

## `GET /eun`

Retrieves browser-based end user notification (EUN) configuration details. To learn more, see [Understanding Browser-Based End User Notifications](/zia/understanding-browser-based-end-user-notifications).

**Tags:** End User Notifications
**Consumes:** application/json
**Produces:** application/json
No parameters.

| Code | Description | Schema |
| ---- | ----------- | ------ |
| 200 | Successful Operation | EndUserNotification |

## `PUT /eun`

Updates browser-based end user notification (EUN) configuration details. To learn more, see [Understanding Browser-Based End User Notifications](/zia/understanding-browser-based-end-user-notifications).

**Tags:** End User Notifications
**Consumes:** application/json
**Produces:** application/json

| Name | In | Type | Required | Description |
| ---- | --- | ---- | -------- | ----------- |
| body | body | EndUserNotification | No |  |

| Code | Description | Schema |
| ---- | ----------- | ------ |
| 200 | Successful Operation | EndUserNotification |

## Models
### EndUserNotification
| Field | Type | Required | Description |
| ----- | ---- | -------- | ----------- |
| aupCustomFrequency | integer (int32) | No | The custom frequency (in days) for showing the AUP to the end users. Valid range is 1 to 180. |
| aupDayOffset | integer (int32) | No | Specifies which day of the week or month the AUP is shown for users when **aupFrequency** is set. Valid range is 1 to 31. |
| aupFrequency | string | No | The frequency at which the Acceptable Use Policy (AUP) is shown to the end users |
| aupMessage | string | No | The acceptable use statement that is shown in the AUP |
| cautionAgainAfter | integer (int32) | No | The time interval at which the caution notification is shown when users continue browsing a restricted site.
**Note**: The recommended setting for complex websites, such as Social Networking sites, is at least 5 minutes. |
| cautionCustomText | string | No | The custom message that appears in the caution notification |
| cautionPerDomain | boolean | No | Specifies whether to display the caution notification at a specific time interval for URLs in the Miscellaneous or Unknown category. This option is applicable when a user browses a URL or a sub-domain of a URL in the Miscellaneous or Unknown category. |
| customText | string | No | The custom text shown in the EUN |
| displayCompLogo | boolean | No | A Boolean value indicating whether your organization's logo appears in the EUN or not |
| displayCompName | boolean | No | A Boolean value indicating whether the organization's name appears in the EUN or not |
| displayReason | boolean | No | A Boolean value indicating whether or not the reason for cautioning or blocking access to a site, file, or application is shown when the respective notification is triggered |
| idpProxyNotificationText | string | No | The message that appears in the IdP Proxy notification |
| notificationType | string | No | The type of EUN as default or custom |
| orgPolicyLink | string | No | The URL of the organization's policy page. This field is required for the default notification type. |
| quarantineCustomNotificationText | string | No | The message that appears in the quarantine notification |
| redirectUrl | string | No | The redirect URL for the external site hosting the EUN specified when the custom notification type is selected |
| securityReviewCustomLocation | string | No | A custom URL location where users' review requests for possible misclassified URLs are sent |
| securityReviewEnabled | boolean | No | A Boolean value indicating whether the Security Violation notification is enabled or disabled |
| securityReviewSubmitToSecurityCloud | boolean | No | A Boolean value indicating whether users' review requests for blocked URLs are submitted to the Zscaler service (i.e., Security Cloud) or a custom location. A true value indicates that the request is sent to the Security cloud, whereas a false value indicates that the request is sent to the specified custom location. |
| securityReviewText | string | No | The message that appears in the Security Violation notification |
| supportEmail | string | No | The email address for writing to IT Support |
| supportPhone | string | No | The phone number for contacting IT Support |
| urlCatReviewCustomLocation | string | No | A custom URL location where users' review requests for blocked URLs are sent |
| urlCatReviewEnabled | boolean | No | A Boolean value indicating whether the URL Categorization notification is enabled or disabled |
| urlCatReviewSubmitToSecurityCloud | boolean | No | A Boolean value indicating whether users' review requests for possibly misclassified URLs are submitted to the Zscaler service (i.e., Security Cloud) or a custom location. A true value indicates that the request is sent to the Security cloud, whereas a false value indicates that the request is sent to the specified custom location. |
| urlCatReviewText | string | No | The message that appears in the URL Categorization notification |
| webDlpReviewCustomLocation | string | No | A custom URL location where users' review requests for the web DLP policy violation are sent |
| webDlpReviewEnabled | boolean | No | A Boolean value indicating whether the Web DLP Violation notification is enabled or disabled |
| webDlpReviewSubmitToSecurityCloud | boolean | No | A Boolean value indicating whether users' review requests for web DLP policy violation are submitted to the Zscaler service (i.e., Security Cloud) or a custom location. A true value indicates that the request is sent to the Security cloud, whereas a false value indicates that the request is sent to the specified custom location. |
| webDlpReviewText | string | No | The message that appears in the Web DLP Violation notification |
