# Configuring Zscaler Virtual IP Address Ranges Using API
Source: https://help.zscaler.com/zpa/configuring-zscaler-virtual-ip-address-ranges-using-api
PDF: https://help.zscaler.com/pdf/com/en/1530861.pdf

This article provides information on managing Zscaler virtual IP address ranges using APIs. All APIs are rate limited. To learn more, see [Adding IP Ranges](/zpa/adding-ip-ranges) and [Understanding Rate Limiting](/zpa/understanding-rate-limiting).
Getting the IP Address Range by Page and Page Size
To get the IP address range details by page and page size:
- Send a `POST` request to the following endpoint: `/mgmtconfig/v1/admin/customers/{customerId}/v2/ipRanges/search`.
- Provide the `customerId`, the ZPA tenant ID of the customer, in the request endpoint. For example: `/mgmtconfig/v1/admin/customers/72057594037927936/v2/ipRanges/search`.
- Include the request headers to provide information about the request context:
- Content-Type: `application/json`
- Authorization: Bearer `<access_token>`
- Use the following JSON payload.
- [View the JSON payload](#getAddressByPagePayload)
[]
`{
"sortBy": {
"sortName": "string",
"sortOrder": "string"
},
"filterBy": [
{
"filterName": "string",
"operator": "string",
"values": [
"string"
],
"commaSepValues": "string"
}
],
"pageBy": {
"page": "string",
"pageSize": "string",
}
}`
- [View the sample JSON payload](#getAddressByPageSamplePayload)
[]
`{
"filterBy": [
{
"filterName": "IP address",
"operator": "LIKE",
"values": [
"10.0.0.0"
],
"commaSepValues": "string"
}
],
"pageBy": {
"page": "1",
"pageSize": "20",
"validPage": 0,
"validPageSize": 0
}
}`
- [View an example response](#getAddressByPageExampleResponse)
[]
` {
"totalPages": "2",
"totalCount": "21",
"list": [
{
"id": "72057594038636775",
"modifiedTime": "1675179304",
"creationTime": "1675178886",
"modifiedBy": "72057594037957297",
"isDeleted": "0",
"customerId": "72057594037927936",
"name": "TempDis",
"description": "s",
"ipRangeBegin": "10.1.1.1",
"ipRangeEnd": "10.1.1.40",
"latitudeInDb": "28.7040592",
"longitudeInDb": "77.10249019999999",
"location": "Delhi, India",
"countryCode": "IN",
"enabled": true,
"totalIps": "40",
"sccmFlag": false
},
{
"id": "72057594038642797",
"modifiedTime": "1679431340",
"creationTime": "1679330645",
"modifiedBy": "72057594038078999",
"isDeleted": "0",
"customerId": "72057594037927936",
"name": "test",
"ipRangeBegin": "172.16.255.1",
"ipRangeEnd": "172.16.255.30",
"latitudeInDb": "37.7749295",
"longitudeInDb": "-122.4194155",
"location": "San Francisco, CA, USA",
"countryCode": "US",
"enabled": true,
"totalIps": "30",
"sccmFlag": false
},
{
"id": "72057594038624863",
"modifiedTime": "1679432841",
"creationTime": "1669363443",
"modifiedBy": "72057594038078999",
"isDeleted": "0",
"customerId": "72057594037927936",
"name": "disabled ip range test",
"ipRangeBegin": "10.0.0.10",
"ipRangeEnd": "10.0.0.100",
"enabled": true,
"totalIps": "91",
"sccmFlag": false
}
]
}
`
A successful response returns code 200. To learn more, see [API Response Codes and Error Messages](/zpa/api-response-codes-and-error-messages).
Getting Details of All IP Address Ranges
To get details of all IP address ranges:
- Send a `GET` request to the following endpoint: `/mgmtconfig/v1/admin/customers/{customerId}/v2/ipRanges`.
- Provide the `customerId`, the ZPA tenant ID of the customer, in the request endpoint. For example: `/mgmtconfig/v1/admin/customers/72057594037927936/v2/ipRanges`.
- [View an example response](#getAllRangesExample)
[]
`[
{
"id": "72057594038636775",
"modifiedTime": "1675179304",
"creationTime": "1675178886",
"modifiedBy": "72057594037957297",
"isDeleted": "0",
"customerId": "72057594037927936",
"name": "Example IP Address Range",
"description": "s",
"ipRangeBegin": "10.1.1.1",
"ipRangeEnd": "10.1.1.40",
"latitudeInDb": "28.7040592",
"longitudeInDb": "77.10249019999999",
"location": "Delhi, India",
"countryCode": "IN",
"enabled": true,
"totalIps": "40",
"sccmFlag": false
},
{
"id": "72057594038642797",
"modifiedTime": "1679431340",
"creationTime": "1679330645",
"modifiedBy": "72057594038078999",
"isDeleted": "0",
"customerId": "72057594037927936",
"name": "Example IP Address Range 2",
"ipRangeBegin": "10.90.255.1",
"ipRangeEnd": "10.90.255.30",
"latitudeInDb": "37.7749295",
"longitudeInDb": "-122.4194155",
"location": "San Francisco, CA, USA",
"countryCode": "US",
"enabled": true,
"totalIps": "30",
"sccmFlag": false
}
]  `
A successful response returns code 200. To learn more, see [API Response Codes and Error Messages](/zpa/api-response-codes-and-error-messages).
Getting Details for a Particular IP Address Range
To get details for a particular IP address range:
- Send a `GET` request to the following endpoint: `/mgmtconfig/v1/admin/customers/{customerId}/v2/ipRanges/{ipRangeId}`.
-
Provide the following in the request endpoint:
- `customerId`: The ZPA tenant ID of the customer.
- `ipRangeId`: The unique identifier of the IP address range.
For example: `/mgmtconfig/v1/admin/customers/72057594037927936/v2/ipRanges/72057594038636775`.
- [View an example response](#getIpAddressExample)
[]
`{
"id": "72057594038636775",
"modifiedTime": "1675179304",
"creationTime": "1675178886",
"modifiedBy": "72057594037957297",
"isDeleted": "0",
"customerId": "72057594037927936",
"name": "Example IP Address Range",
"description": "s",
"ipRangeBegin": "10.1.1.1",
"ipRangeEnd": "10.1.1.40",
"latitudeInDb": "28.7040592",
"longitudeInDb": "77.10249019999999",
"location": "Delhi, India",
"countryCode": "IN",
"enabled": true,
"totalIps": "40",
"sccmFlag": false
}`
A successful response returns code 200. To learn more, see [API Response Codes and Error Messages](/zpa/api-response-codes-and-error-messages).
Adding a New IP Address Range
To add a new IP address range:
- Send a `POST` request to the following endpoint: `/mgmtconfig/v1/admin/customers/{customerId}/v2/ipRanges`.
- Provide the `customerId`, the ZPA tenant ID of the customer, in the request endpoint. For example: `/mgmtconfig/v1/admin/customers/72057594037927936/v2/ipRanges`.
- Include the request headers to provide information about the request context:
- Content-Type: `application/json`
- Authorization: Bearer `<access_token>`
- Use the following JSON payload and provide the following:
- `name`: The name of IP address range.
- `ipRangeBegin`: The beginning IP address range. The beginning IP address range must be less than the ending IP address range. The `subnetCidr` field is not required if `ipRangeBegin` or `ipRangeEnd` fields are passed.
- `ipRangeEnd`: The ending IP address range. The ending IP address range must be greater than the beginning IP address range. The `subnetCidr` field is not required if `ipRangeBegin` or `ipRangeEnd` fields are passed.
- `subnetCidr`: The IP address subnet in Classless Inter-Domain Routing (CIDR) notation used for server-to-client connectivity. The `ipRangeBegin` or `ipRangeEnd` fields are not required if `subnetCidr` is passed.
- `location`: The location of the IP address range.
- `latitudeInDb`: The latitude coordinate for the location of the IP address range.
- `longitudeInDb`: The longitude coordinate for the location of the IP address range.
- `sccmFlag`: Indicates if the location hint is sent along with a Zscaler IP address to Zscaler Client Connector if it is configured. If Zscaler Client Connector receives the location hint, Zscaler Client Connector creates a pseudo network adapter and applies the location hint to the name of the adapter for the System Center Configuration Manager (SCCM) location boundary.
- `enabled`: Indicates if the IP address range is enabled (`true`) or disabled (`false`).
- [View the JSON payload](#addIpRangeJsonPayload)
[]
` {
"name": "string",
"description": "string",
"ipRangeBegin": "string",
"ipRangeEnd": "string",
"subnetCidr": "string",
"latitudeInDb": "string",
"longitudeInDb": "string",
"location": "string",
"countryCode": "string",
"enabled": true,
"sccmFlag": true,
"locationHint": "string"
}`
- [View an example JSON payload](#addIpRangeExampleJson)
[]
` {
"name":"Example IP Address Range",
"enabled":true,
"ipRangeBegin":"194.158.10.0",
"ipRangeEnd":"194.158.15.0",
"description":"Example Description",
"sccmFlag":false,
"latitudeInDb":37.7749295,
"longitudeInDb":-122.4194155,
"countryCode":"US",
"location":"San Francisco, CA, USA"
}`
- [View an example response](#addIpRangeResponse)
[]
` {
"id": "72057594038900885",
"modifiedTime": "1752776656",
"creationTime": "1752776656",
"modifiedBy": "72057594038040687",
"isDeleted": "0",
"customerId": "72057594037927936",
"name": "Example IP Address Range",
"description": "Example Description",
"ipRangeBegin": "194.158.10.0",
"ipRangeEnd": "194.158.15.0",
"latitudeInDb": "37.7749295",
"longitudeInDb": "-122.4194155",
"location": "San Francisco, CA, USA",
"countryCode": "US",
"enabled": true,
"totalIps": "1281",
"sccmFlag": false
}`
A successful response returns code 200. To learn more, see [API Response Codes and Error Messages](/zpa/api-response-codes-and-error-messages).
Updating an IP Address Range
To update an existing IP address range:
- Send a `PUT` request to the following endpoint: `/mgmtconfig/v1/admin/customers/{customerId}/v2/ipRanges/{ipRangeId}`.
-
Provide the following in the request endpoint:
- `customerId`: The ZPA tenant ID of the customer.
- `ipRangeId`: The unique identifier of the IP address range.
For example: `/mgmtconfig/v1/admin/customers/72057594037927936/v2/ipRanges/72057594038636775`.
- Include the request headers to provide information about the request context:
- Content-Type: `application/json`
- Authorization: Bearer `<access_token>`
- Use the following JSON payload and provide the following:
- `name`: The name of IP address range.
- `ipRangeBegin`: The beginning IP address range. The beginning IP address range must be less than the ending IP address range. The `subnetCidr` field is not required if `ipRangeBegin` or `ipRangeEnd` fields are passed.
- `ipRangeEnd`: The ending IP address range. The ending IP address range must be greater than the beginning IP address range. The `subnetCidr` field is not required if `ipRangeBegin` or `ipRangeEnd` fields are passed.
- `subnetCidr`: The IP address subnet in Classless Inter-Domain Routing (CIDR) notation used for server-to-client connectivity. The `ipRangeBegin` or `ipRangeEnd` fields are not required if `subnetCidr` is passed.
- `location`: The location of the IP address range.
- `latitudeInDb`: The latitude coordinate for the location of the IP address range.
- `longitudeInDb`: The longitude coordinate for the location of the IP address range.
- `sccmFlag`: Indicates if the location hint is sent along with a Zscaler IP address to Zscaler Client Connector if it is configured. If Zscaler Client Connector receives the location hint, Zscaler Client Connector creates a pseudo network adapter and applies the location hint to the name of the adapter for the System Center Configuration Manager (SCCM) location boundary.
- `enabled`: Indicates if the IP address range is enabled (`true`) or disabled (`false`).
- [View the example JSON payload](#updateIpRangePayload)
[]
`  {
"name": "string",
"description": "string",
"ipRangeBegin": "string",
"ipRangeEnd": "string",
"subnetCidr": "string",
"latitudeInDb": "string",
"longitudeInDb": "string",
"location": "string",
"countryCode": "string",
"enabled": true,
"sccmFlag": true,
"locationHint": "string"
}`
A successful response returns code 204, meaning the IP address range is updated. To learn more, see [API Response Codes and Error Messages](/zpa/api-response-codes-and-error-messages).
Deleting an IP Address Range
To delete an existing IP address range:
- Send a `DELETE` request to the following endpoint: `/mgmtconfig/v1/admin/customers/{customerId}/v2/ipRanges/{ipRangeId}`.
-
Provide the following in the request endpoint:
- `customerId`: The ZPA tenant ID of the customer.
- `ipRangeId`: The unique identifier of the IP address range.
For example: `/mgmtconfig/v1/admin/customers/72057594037927936/v2/ipRanges/72057594038636775`.
A successful response returns code 200, meaning the IP address range is deleted. To learn more, see [API Response Codes and Error Messages](/zpa/api-response-codes-and-error-messages).
Adding Field Descriptions
The following table includes available fields you can use for the IP address range API use cases:
| Field | Description | Required | Value |
| ----- | ----------- | -------- | ----- |
| enabled | Indicates if the IP address range is enabled (`true`) or disabled (`false`) | Yes | Default: `true`Boolean: `true`, `false` |
| ipRangeBegin | The beginning IP address range. The beginning IP address range must be less than the ending IP address range. The `subnetCidr` field is not required if `ipRangeBegin` or `ipRangeEnd` fields are passed. | Yes | String |
| ipRangeEnd | The ending IP address range. The ending IP address range must be greater than the beginning IP address range. The `subnetCidr` field is not required if `ipRangeBegin` or `ipRangeEnd` fields are passed. | Yes | String |
| latitudeInDb | The latitude coordinate for the location of the IP address range | Yes | String |
| location | The location of the IP address range | Yes | String |
| locationHint | The location hint to be sent along with a Zscaler virtual IP address to Zscaler Client Connector if it is configured. This field is required if the `sccmFlag` field is set to `true`. | No | String |
| longitudeInDb | The longitude coordinate for the location of the IP address range | Yes | String |
| name | The name of the IP address range | Yes | String |
| sccmFlag | Indicates if the location hint is sent along with a Zscaler virtual IP address to Zscaler Client Connector if it is configured. If Zscaler Client Connector receives the location hint, Zscaler Client Connector creates a pseudo network adapter and applies the location hint to the name of the adapter for the System Center Configuration Manager (SCCM) location boundary. | Yes | Default: `false`Boolean: `true`, `false` |
| subnetCidr | The IP address subnet in Classless Inter-Domain Routing (CIDR) notation used for server-to-client connectivity. The `ipRangeBegin` or `ipRangeEnd` fields are not required if `subnetCidr` is passed. | Yes | String |