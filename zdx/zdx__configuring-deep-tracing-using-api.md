# Configuring Deep Tracing Using API
Source: https://help.zscaler.com/zdx/configuring-deep-tracing-using-api
PDF: https://help.zscaler.com/pdf/com/en/1444036.pdf

This article provides information for managing Zscaler Digital Experience (ZDX) troubleshooting by using APIs. All APIs are rate limited. To learn more, see [Understanding Rate Limiting](/zdx/understanding-rate-limiting).
Start a Deep Trace for a Device
To start a deep tracing session on a device, send a POST request to the endpoint `/devices/{deviceid}/deeptraces`. Provide the following in the request:
- `deviceid`: The device's ID.
For example, in Python:
payload = {
"deviceid":30989301
}
- [View example response.](#ExampleResponseStartDeepTrace)
[]{
"trace_id": 0,
"status": "not_started",
"expected_time": 0
}
A successful response returns code 200. To learn more, see [Understanding Error Codes](/zdx/understanding-error-codes).
Stop a Deep Trace for a Device
To stop a deep tracing session on a device, send a DELETE request to the endpoint `/devices/{deviceid}/deeptraces`. Provide the following in the request:
This deletes the deep tracing session and the associated data.
- `deviceid`: The device's ID.
- `trace_id`: The deep tracing ID that requires a stop.
For example, in Python:
payload = {
"deviceid":30989301,
"trace_id":0
}
- [View example response.](#ExampleResponseStopDeepTrace)
[]{
"trace_id": 0
}
A successful response returns code 200. To learn more, see [Understanding Error Codes](/zdx/understanding-error-codes).
Get a List of All Deep Traces for a Device
To get a list of all deep traces on a specific device, send a GET request to the endpoint `[/devices/{deviceid}/deeptraces]`. Provide the following in the request:
- `deviceid`: The device's ID.
For example, in Python:
payload = {
"deviceid":30989301
}
- [View example response.](#ExampleResponseDeepTraceList)
[]{
"trace_id": 0,
"trace_details": {
"session_name": "string",
"user_id": 0,
"username": "string",
"device_id": 30989301,
"device_name": "string",
"web_probe_id": 0,
"web_probe_name": "string",
"cloudpath_probe_id": 0,
"cloud_path_name": "string",
"session_length": 0,
"probe_device": true
},
"status": "not_started",
"created_at": 0,
"started_at": 0,
"ended_at": 0
}
A successful response returns code 200. To learn more, see [Understanding Error Codes](/zdx/understanding-error-codes).
Get the Deep Tracing Session Configuration
To get the configuration of a Deep Tracing session, send a GET request to the endpoint `[/devices/{deviceid}/deeptraces/{trace_id}]`. Provide the following in the request:
- `deviceid`: The device's ID.
- `trace_id`: The device's deep tracing ID.
For example, in Python:
payload = {
"deviceid":30989301,
"trace_id":0
}
- [View example response.](#ExampleResponseDeepTracingStatus)
[]{
"trace_id": 0,
"trace_details": {
"session_name": "string",
"user_id": 0,
"username": "string",
"device_id": 30989301,
"device_name": "string",
"web_probe_id": 0,
"web_probe_name": "string",
"cloudpath_probe_id": 0,
"cloud_path_name": "string",
"session_length": 0,
"probe_device": true
},
"status": "not_started",
"created_at": 0,
"started_at": 0,
"ended_at": 0
}
A successful response returns code 200. To learn more, see [Understanding Error Codes](/zdx/understanding-error-codes).

## Contents
- **API Developer & Reference Guide**
  - [Getting Started](/zdx/getting-started-zdx-api)
  - [Understanding Rate Limiting](/zdx/understanding-rate-limiting)
  - [Understanding Error Codes](/zdx/understanding-error-codes)
  - [Configuring the Postman REST API Client](/zdx/configuring-postman-rest-api-client)
  - **Reference Guide**
    - [API Authentication](/zdx/api-authentication)
    - [Administration](/zdx/administration-0)
    - [Alerts](/zdx/alerts-zdx-api)
    - [Inventory](/zdx/inventory)
    - [Reports](/zdx/reports)
    - [Troubleshooting](/zdx/troubleshooting)
    - [ZDX Snapshots](/zdx/zdx-snapshots)
  - **Working with APIs**
    - [Managing Administration Using API](/zdx/managing-administration-using-api)
    - [Configuring Deep Tracing Using API](/zdx/configuring-deep-tracing-using-api)