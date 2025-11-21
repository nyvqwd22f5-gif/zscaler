# Obtaining Cloud Connector Group Details Using API
Source: https://help.zscaler.com/zpa/obtaining-cloud-connector-group-details-using-api
PDF: https://help.zscaler.com/pdf/com/en/1484861.pdf

This article provides information on managing Zscaler Private Access (ZPA) Cloud Connector Group use cases using APIs. All APIs are rate limited. To learn more, see [About Rate Limiting](/zpa/about-rate-limiting).
Getting Details for All Cloud Connector Groups
To get details for all the Cloud Connector groups:
- Send a `GET` request to the endpoint `/mgmtconfig/v1/admin/customers/{customerId}/cloudConnectorGroup` in the cloud-connector-group-controller.
- Provide the `customerId`, the ZPA tenant ID of the customer, in the request endpoint. For example: `/mgmtconfig/v1/admin/customers/72057615512764416/cloudConnectorGroup`.
- [View an example response](#Viewanexampleresponse)
[]{
"totalPages": "1",
"list": [
{
"creationTime": "1569858419",
"modifiedBy": "72057594037927958",
"id": "217246660303023507",
"name": "TestZNF",
"enabled": true,
"cloudConnectors": [
{
"id": "217246660303023508",
"modifiedTime": "1601588754",
"creationTime": "1569876403",
"modifiedBy": "3",
"name": "TestZNF-1",
"fingerprint": "my_fingerprint",
"issuedCertId": "10230",
"enabled": true
},
{
"id": "217246660303023540",
"modifiedTime": "1571609955",
"creationTime": "1571609954",
"modifiedBy": "3",
"name": "TestZNF-2",
"fingerprint": "my-fingerprint",
"issuedCertId": "1480",
"enabled": true
},
{
"id": "217246660303023559",
"modifiedTime": "1572472297",
"creationTime": "1572472296",
"modifiedBy": "3",
"name": "TestZNF-3",
"fingerprint": "test1",
"issuedCertId": "1491",
"enabled": true
},
{
"id": "217246660303023565",
"modifiedTime": "1572896745",
"creationTime": "1572896744",
"modifiedBy": "3",
"name": "TestZNF-4",
"fingerprint": "my-fingerprint-haha",
"issuedCertId": "1497",
"enabled": true
},
{
"id": "217246660303023627",
"modifiedTime": "1576242337",
"creationTime": "1576242334",
"modifiedBy": "3",
"name": "TestZNF-5",
"fingerprint": "my-fingerprint-so-unique",
"issuedCertId": "1857",
"enabled": true
},
{
"id": "217246660303024153",
"modifiedTime": "1604707454",
"creationTime": "1604707454",
"modifiedBy": "3",
"name": "TestZNF-6",
"fingerprint": "my-fingerprint-hahahahah23",
"issuedCertId": "10548",
"enabled": true
}
]
},
{
"creationTime": "1579645656",
"modifiedBy": "72057594037928105",
"id": "217246660303023669",
"name": "Test ZNF group",
"enabled": true,
"cloudConnectors": [
{
"id": "217246660303023670",
"modifiedTime": "1579646496",
"creationTime": "1579646495",
"modifiedBy": "3",
"name": "Test ZNF group provisioning key-1",
"fingerprint": "Testy-fingerprint",
"issuedCertId": "1889",
"enabled": true
}
]
},
{
"creationTime": "1596498299",
"modifiedBy": "72057594037953048",
"id": "217246660303023942",
"name": "Test_znf_group",
"enabled": true,
"ziaCloud": "zscaler.net",
"ziaOrgId": "12345",
"cloudConnectors": [
{
"id": "217246660303023943",
"modifiedTime": "1596499647",
"creationTime": "1596499647",
"modifiedBy": "3",
"name": "TestZNF-1",
"fingerprint": "Testfingerprint_0001",
"issuedCertId": "2383",
"enabled": true
}
]
},
{
"creationTime": "1598635915",
"modifiedBy": "72057594037950342",
"id": "217246660303024004",
"name": "Tesst_ZNF",
"enabled": true,
"ziaCloud": "zscaler.net",
"ziaOrgId": "12345",
"cloudConnectors": [
{
"id": "217246660303024005",
"modifiedTime": "1598638787",
"creationTime": "1598638787",
"modifiedBy": "3",
"name": "Tesstt_ZNF-1",
"fingerprint": "test-fingerprint-1",
"issuedCertId": "10104",
"enabled": true
},
{
"id": "217246660303024724",
"modifiedTime": "1607900877",
"creationTime": "1607900877",
"modifiedBy": "3",
"name": "MP_ZNF-2",
"fingerprint": "test-fingerprint-2",
"issuedCertId": "10592",
"enabled": true
}
]
},
{
"creationTime": "1599259086",
"modifiedBy": "72057594037941168",
"id": "217246660303024029",
"name": "test-econnector-grp",
"enabled": true,
"ziaCloud": "zscaler.net",
"ziaOrgId": "12345"
},
{
"creationTime": "1599763819",
"modifiedBy": "72057594037941168",
"id": "217246660303024036",
"name": "test_example",
"enabled": true,
"ziaCloud": "zscaler.net",
"ziaOrgId": "12345",
"cloudConnectors": [
{
"id": "217246660303024037",
"modifiedTime": "1599764564",
"creationTime": "1599764563",
"modifiedBy": "3",
"name": "test_example_1-1",
"fingerprint": "test111121212121",
"issuedCertId": "10142",
"enabled": true
}
]
},
{
"creationTime": "1603994989",
"modifiedBy": "72057594037959758",
"id": "217246660303024130",
"name": "test2 edge connector group",
"enabled": true,
"ziaCloud": "zscaler.net",
"ziaOrgId": "111111",
"cloudConnectors": [
{
"id": "217246660303024131",
"modifiedTime": "1603996783",
"creationTime": "1603996782",
"modifiedBy": "3",
"name": "test nonce-1",
"fingerprint": "Test0001",
"issuedCertId": "10531",
"enabled": true
}
]
}
]
}
A successful response returns code 200. To learn more, see [About Error Codes](/zpa/about-error-codes).
This API supports pagination. To get a paginated response:
- Send a `GET` request to the endpoint `/mgmtconfig/v1/admin/customers/{customerId}/cloudConnectorGroup?page=1&pagesize=20`.
- Provide the following in the request endpoint:
- `customerId`: The ZPA tenant ID of the customer.
- Valid values for page and page size parameters.
For example: `/mgmtconfig/v1/admin/customers/217246660302995456/cloudConnectorGroup?page=1&pagesize=2.`
- [View an example response](#paginatedResponse)
[]{
"totalPages": "8",
"list": [
{
"creationTime": "1628119973",
"modifiedBy": "72057594038044466",
"id": "217246660303025287",
"name": "Test_cloud_connector_group",
"enabled": true,
"ziaCloud": "zscaler.net",
"ziaOrgId": "12345",
"cloudConnectors": [
{
"id": "217246660303025288",
"modifiedTime": "1628122567",
"creationTime": "1628122567",
"modifiedBy": "3",
"name": "Test nonce-1",
"fingerprint": "Test-fingerprint",
"issuedCertId": "10829",
"enabled": true
},
{
"id": "217246660303025478",
"modifiedTime": "1632766307",
"creationTime": "1632766306",
"modifiedBy": "3",
"name": "Test nonce-2",
"fingerprint": "Test-fingerprint002",
"issuedCertId": "10912",
"enabled": true
},
{
"id": "217246660303025510",
"modifiedTime": "1634187902",
"creationTime": "1634187902",
"modifiedBy": "3",
"name": "Test nonce-3",
"fingerprint": "Test-fingerprint003",
"issuedCertId": "10926",
"enabled": true
}
]
},
{
"creationTime": "1644974062",
"modifiedBy": "72057594037988394",
"id": "217246660303026090",
"name": "branch_connector",
"enabled": true,
"description": "branch connector poc",
"ziaCloud": "zscaler.net",
"ziaOrgId": "21400",
"cloudConnectors": [
{
"id": "217246660303026091",
"modifiedTime": "1644975292",
"creationTime": "1644975292",
"modifiedBy": "3",
"name": "branch_conn_poc-1644975292103",
"fingerprint": "branch_connector_poc-vp1",
"issuedCertId": "11409",
"enabled": true
}
]
}
]
}
If not provided, the default page size is 20. The maximum page size is 500.
A successful response returns code 200. To learn more, see [About Error Codes](/zpa/about-error-codes).
Getting Details for a Particular Cloud Connector Group
To get details of a particular Cloud Connector group:
- Send a `GET` request to the endpoint `mgmtconfig/v1/admin/customers/{customerId}/cloudConnectorGroup/{id}` in the cloud-connector-group-controller.
- Provide the following values pairs in the request endpoint:
- `customerId`: The ZPA tenant ID of the customer.
- `id`: The ID of the desired cloud connector group.
For example: `/mgmtconfig/v1/admin/customers/72057615512764416/cloudConnectorGroup/217246660303023507`.
- [View an example response](#Viewanexampleresponse2)
[]{
"creationTime": "1569858419",
"modifiedBy": "72057594037927958",
"id": "217246660303023507",
"name": "TestZNF",
"enabled": true,
"cloudConnectors": [
{
"id": "217246660303023508",
"modifiedTime": "1601588754",
"creationTime": "1569876403",
"modifiedBy": "3",
"name": "TestTestZNF-1",
"fingerprint": "my_fingerprint",
"issuedCertId": "10230",
"enabled": true
},
{
"id": "217246660303023540",
"modifiedTime": "1571609955",
"creationTime": "1571609954",
"modifiedBy": "3",
"name": "TestTestZNF-2",
"fingerprint": "my-fingerprint",
"issuedCertId": "1480",
"enabled": true
},
{
"id": "217246660303023559",
"modifiedTime": "1572472297",
"creationTime": "1572472296",
"modifiedBy": "3",
"name": "TestTestZNF-3",
"fingerprint": "Testprivatebroker1",
"issuedCertId": "1491",
"enabled": true
},
{
"id": "217246660303023565",
"modifiedTime": "1572896745",
"creationTime": "1572896744",
"modifiedBy": "3",
"name": "TestTestZNF-4",
"fingerprint": "my-fingerprint-haha",
"issuedCertId": "1497",
"enabled": true
},
{
"id": "217246660303023627",
"modifiedTime": "1576242337",
"creationTime": "1576242334",
"modifiedBy": "3",
"name": "TestTestZNF-5",
"fingerprint": "my-fingerprint-so-unique",
"issuedCertId": "1857",
"enabled": true
},
{
"id": "217246660303024153",
"modifiedTime": "1604707454",
"creationTime": "1604707454",
"modifiedBy": "3",
"name": "TestTestZNF-6",
"fingerprint": "my-fingerprint-hahahahah23",
"issuedCertId": "10548",
"enabled": true
}
]
}
A successful response returns code 200. To learn more, see [About Error Codes](/zpa/about-error-codes).