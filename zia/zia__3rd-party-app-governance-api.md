# 3rd-Party App Governance API
Source: https://help.zscaler.com/zia/3rd-party-app-governance-api

3rd-Party App Governance API
**Constraints:**
-  For query parameters, ensure that the provided characters adhere to the specifications outlined in RFC 7230 and RFC 3986.
-  Special characters and encoding must follow the standards defined in RFC 3986.

## `GET /app_views/list`

https://api.apptotal.zscaler.com/v1/app_views/list
Retrieves the list of [custom views](https://help.zscaler.com/zia/custom-views\) that you have configured in the 3rd-Party App Governance Admin Portal and includes all configurations that define the custom view.

**Tags:** App Views
No parameters.

| Code | Description | Schema |
| ---- | ----------- | ------ |
| 200 | Successful Operation |  |
| 400 | Invalid Request Body |  |
| 401 | Not Authenticated |  |
| 403 | Access Forbidden |  |
| 409 | Rate Limit Exceeded |  |
| 500 | Internal Server Error Occurred |  |

## `GET /app_views/{appViewId}/apps`

https://api.apptotal.zscaler.com/v1/app_views/{appViewId}/apps
Retrieves all assets (i.e., apps) that are related to a specified argument (i.e., [custom view](https://help.zscaler.com/zia/custom-views\)). Uses the value of `id` from `GET /app_views/list` to return the app IDs of the apps related to the custom view.

**Tags:** App Views

| Name | In | Type | Required | Description |
| ---- | --- | ---- | -------- | ----------- |
| appViewId | path | string | Yes | The custom view identifier |

| Code | Description | Schema |
| ---- | ----------- | ------ |
| 200 | Successful Operation |  |
| 400 | Invalid Request Body |  |
| 401 | Not Authenticated |  |
| 403 | Access Forbidden |  |
| 409 | Rate Limit Exceeded |  |
| 500 | Internal Server Error Occurred |  |

## `GET /app_views/{appViewId}/apps_extended`

https://api.apptotal.zscaler.com/v1/app_views/{appViewId}/apps_extended
Retrieves all assets (apps) attributes which are part of a specified argument app view, with extended information.

**Tags:** App views extended

| Name | In | Type | Required | Description |
| ---- | --- | ---- | -------- | ----------- |
| appViewId | path | string | Yes | The custom view identifier |
| limit | query | integer | No | Limit the number of results |
| page | query | integer | No | Page number |
| verbose | query | boolean | No | Return a verbose report including potentially heavy artifacts (e.g., extracted URLs and a list of vulnerabilities) |

| Code | Description | Schema |
| ---- | ----------- | ------ |
| 200 | Successful Operation |  |
| 400 | Bad Input Parameter |  |
| 401 | Not Authenticated |  |
| 403 | Access Forbidden |  |
| 409 | Rate Limit Exceeded |  |
| 500 | Internal Server Error Occurred |  |

## `GET /apps/app`

https://api.apptotal.zscaler.com/v1/apps/app
**Constraints:**
-   For query parameters, ensure that the provided characters adhere to the specifications  outlined in RFC 7230 and RFC 3986.
-  Special characters and encoding must follow the standards defined in RFC 3986.
Searches the 3rd-Party App Governance App Catalog by either  app ID or URL (i.e., a valid consent or marketplace link). You must use one of the required parameters—`app_id ` or `url`—for your search. If you use both an app ID and a  URL for your search, an error is returned.
- If the app is found in the catalog, a `200` response is received and the app's information is returned.
- If the app is not initially found in the catalog, a `202` response is received and the app is submitted for analysis in the 3rd-Party App Governance Sandbox.
**Note**: After analysis is complete, a subsequent `GET` request is required to fetch the app's information. As a best practice, allow 24 hours for analysis and then resubmit the required `GET` request.
- If the app is not found in the catalog, a `404` response is received.
- If the URL is not valid, a `400` response is received.
**Note**: If you cannot find the app via the API, you can troubleshoot by [manually searching for the app](https://help.zscaler.com/zia/searching-apps\) in the 3rd-Party App Governance Admin Portal. If you cannot find the app through manual search, contact Zscaler Support.
To learn more, see the Responses in the right-side panel.

**Tags:** Applications

| Name | In | Type | Required | Description |
| ---- | --- | ---- | -------- | ----------- |
| app_id | query | string | No | The app identifier (e.g., OAuth client ID) |
| url | query | string | No | Valid consent link or marketplace link |
| verbose | query | boolean | No | Return a verbose report including potentially heavy artifacts (e.g., extracted URLs and a list of vulnerabilities) |

| Code | Description | Schema |
| ---- | ----------- | ------ |
| 200 | Successful Operation |  |
| 202 | Application Analysis Underway |  |
| 400 | Bad Input Parameter |  |
| 401 | Not Authenticated |  |
| 403 | Access Forbidden |  |
| 404 | Application Not Found |  |
| 409 | Rate Limit Exceeded |  |
| 500 | Internal Server Error Occurred |  |

## `POST /apps/app`

https://api.apptotal.zscaler.com/v1/apps/app
Submits an app for analysis in the 3rd-Party App Governance Sandbox. After analysis is complete, a subsequent `GET` request is required to fetch the app's information.

**Tags:** Applications
No parameters.

| Code | Description | Schema |
| ---- | ----------- | ------ |
| 200 | Successful Operation |  |
| 400 | Invalid Request Body |  |
| 401 | Not Authenticated |  |
| 403 | Access Forbidden |  |
| 409 | Rate Limit Exceeded |  |
| 500 | Internal Server Error Occurred |  |

## `GET /apps/search`

https://api.apptotal.zscaler.com/v1/apps/search
**Constraints:**
-  For query parameters, ensure that the provided characters adhere to the specifications outlined in RFC 7230 and RFC 3986.
-  Special characters and encoding must follow the standards defined in RFC 3986.
Searches for an app by name. Any app whose name contains the search term (`appName`) is returned.
**Note**: The maximum number of results that are returned is 200.

**Tags:** Applications

| Name | In | Type | Required | Description |
| ---- | --- | ---- | -------- | ----------- |
| appName | query | string | Yes | The app  name |
| limit | query | integer | No | Limit the number of results |
| page | query | integer | No | Page number |

| Code | Description | Schema |
| ---- | ----------- | ------ |
| 200 | Successful Operation |  |
| 400 | Invalid Request Body |  |
| 401 | Not Authenticated |  |
| 403 | Access Forbidden |  |
| 409 | Rate Limit Exceeded |  |
| 500 | Internal Server Error Occurred |  |

## `GET /posture/assets`

https://api.apptotal.zscaler.com/v1/posture/assets
Returns a paginated list of asset control instances for a specific control ID in the 3rd-Party App Governance Posture tab.

**Tags:** Posture

| Name | In | Type | Required | Description |
| ---- | --- | ---- | -------- | ----------- |
| controlId | query | string | Yes | The control ID to query |
| limit | query | integer | No | Maximum number of rows to return |
| page | query | integer | No | Zero-based results page to return |

| Code | Description | Schema |
| ---- | ----------- | ------ |
| 200 | Successful Operation |  |
| 401 | Not Authenticated |  |
| 403 | Access Forbidden |  |
| 500 | Internal Server Error Occurred |  |

## `PUT /posture/assets/status`

https://api.apptotal.zscaler.com/v1/posture/assets/status
Enables or disables multiple asset control instances simultaneously by their IDs in the 3rd-Party App Governance Posture tab.

**Tags:** Posture
No parameters.

| Code | Description | Schema |
| ---- | ----------- | ------ |
| 200 | Toggle Operation Completed |  |
| 400 | Invalid Request Body |  |
| 401 | Not Authenticated |  |
| 403 | Access Forbidden |  |
| 500 | Internal Server Error Occurred |  |

## `POST /posture/controls`

https://api.apptotal.zscaler.com/v1/posture/controls
Retrieves a paginated list of controls based on filter and sort criteria in the 3rd-Party App Governance Posture tab.

**Tags:** Posture

| Name | In | Type | Required | Description |
| ---- | --- | ---- | -------- | ----------- |
| limit | query | integer | No | Maximum number of results to return (pagination limit) |
| page | query | integer | No | Page number for pagination |

| Code | Description | Schema |
| ---- | ----------- | ------ |
| 200 | Successful Operation |  |
| 400 | Invalid Request |  |
| 401 | Not Authenticated |  |
| 403 | Access Forbidden |  |
| 409 | Rate Limit Exceeded |  |
| 500 | Internal Server Error Occurred |  |

## `GET /posture/controls/filters`

https://api.apptotal.zscaler.com/v1/posture/controls/filters
Returns a map of available filters and their display names in the 3rd-Party App Governance Posture tab.

**Tags:** Posture
No parameters.

| Code | Description | Schema |
| ---- | ----------- | ------ |
| 200 | Successful Operation |  |
| 401 | Not Authenticated |  |
| 403 | Access Forbidden |  |
| 409 | Rate Limit Exceeded |  |
| 500 | Internal Server Error Occurred |  |

## `PUT /posture/controls/status`

https://api.apptotal.zscaler.com/v1/posture/controls/status
Enables or disables multiple controls simultaneously by their IDs in the 3rd-Party App Governance Posture tab.

**Tags:** Posture
No parameters.

| Code | Description | Schema |
| ---- | ----------- | ------ |
| 200 | Toggle Operation Completed |  |
| 400 | Invalid Request Body |  |
| 401 | Not Authenticated |  |
| 403 | Access Forbidden |  |
| 500 | Internal Server Error Occurred |  |
