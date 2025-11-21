# Obtaining VPN (for Legacy Apps) Resources Using API
Source: https://help.zscaler.com/zpa/obtaining-vpn-legacy-apps-resources-using-api
PDF: https://help.zscaler.com/pdf/com/en/1532173.pdf

This article provides information on obtaining VPN (for Legacy Apps) resources using APIs. All APIs are rate limited. To learn more, see [Understanding Rate Limiting](/zpa/understanding-rate-limiting) and [VPN (for Legacy Apps)](/zpa/vpn-legacy-apps).
Getting Details of All Users Connected to VPN Service Edges
To get details of all users that are connected to VPN Service Edges:
- Send a `GET` request to the following endpoint: `/mgmtconfig/v1/admin/customers/{customerId}/vpnConnectedUsers`.
- Provide the `customerId`, the ZPA tenant ID of the customer, in the request endpoint. For example: `/mgmtconfig/v1/admin/customers/73229488749543424/vpnConnectedUsers`.
- [View an example response](#getApplications)
[]
`{
"totalPages": "1",
"currentCount": "1",
"totalCount": "1",
"list": [
{
"id": "73229488749551415",
"creationTime": "1756977137",
"modifiedBy": "72057594038820580",
"deviceState": "1",
"clientIPAddress": "192.0.2.0",
"vpnServiceEdgeId": "73229488749551620",
"commonName": "dec1bb9059eb7f3392ad3630820f881939d6b3dd4b77795fddc@vishnu1.com",
"UserName": "exampleUser2@sample.com",
"vpnServiceEdgeName": "Sample VPN Service Edge Name"
}
]
}`
A successful response returns code 200. To learn more, see [API Response Codes and Error Messages](/zpa/api-response-codes-and-error-messages).