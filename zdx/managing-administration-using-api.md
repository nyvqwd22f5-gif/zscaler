# Managing Administration Using API
Source: https://help.zscaler.com/zdx/managing-administration-using-api
PDF: https://help.zscaler.com/pdf/com/en/1403101.pdf

This article provides information for managing Zscaler Digital Experience (ZDX) Administration using APIs. All APIs are rate limited. To learn more, see [Understanding Rate Limiting](/zdx/understanding-rate-limiting).
Getting Department Details
To get the details of all the configured departments, send a GET request to the endpoint `[/administration/departments]`. Provide the following in the request:
- `from`: The timestamp, in epoch, from when the data is displayed.
- `to`: The timestamp, in epoch, till when the data is displayed.
For example, in Python:
payload = {
"from":1493967600000,
"to":1496645999999
}
The request body can also include the `search` attribute to get the data for a specific department ID or name.
- [View an example response](#exampleResponse)
[]{
"id": 38745231567,
"name": "Engineering"
}
A successful response returns code 200. To learn more, see [Understanding Error Codes](/zdx/understanding-error-codes).
Getting Location Details
To get the details of all the configured Zscaler locations, send a GET request to the endpoint `[/administration/locations]`. Provide the following in the request:
- `from`: The timestamp, in epoch, from when the data is displayed.
- `to`: The timestamp, in epoch, till when the data is displayed.
For example, in Python:
payload = {
"from":1493967600000,
"to":1496645999999
}
The request body can also include the `search` attribute to get the data for a specific location ID or name.
- [View an example response](#exampleResponse2)
[]{
"id": 72840124,
"name": "US-BHE23-CBR - San Francisco"
}
A successful response returns code 200. To learn more, see [Understanding Error Codes](/zdx/understanding-error-codes).