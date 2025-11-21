# Obtaining SAML Attribute Details Using API
Source: https://help.zscaler.com/zpa/obtaining-saml-attribute-details-using-api
PDF: https://help.zscaler.com/pdf/com/en/1484826.pdf

This article provides information on managing Zscaler Private Access (ZPA) SAML attribute use cases using APIs. All APIs are rate limited. To learn more, see [Understanding Rate Limiting](/zpa/understanding-rate-limiting).
Getting Details for a Particular SAML Attribute
To get details by ID for a particular SAML attribute:
- Send a `GET` request to the following endpoint in the saml-attr-controller: `/mgmtconfig/v1/admin/customers/{customerId}/samlAttribute/{attrId}`.
- Use the following values in the request endpoint:
- `customerId`: The ZPA tenant ID of the customer.
- `attrId`: The ID of the desired SAML attribute.
For example: `/mgmtconfig/v1/admin/customers/72057615512764416/samlAttribute/72057615512764585`.
- [View an example response](#Viewanexampleresponse2)
[]{
"id": "72057615512764585",
"creationTime": "1611878400",
"modifiedBy": "72057615512764552",
"name": "Department",
"userAttribute": false,
"idpId": "72057615512764429",
"samlName": "Department",
"idpName": "Okta"
}
A successful response returns code 200. To learn more, see [API Response Codes and Error Messages](/zpa/api-response-codes-and-error-messages).
[]Getting Details of All SAML Attributes V2
To get all SAML attributes by page:
- Send a `GET` request to the following endpoint in the saml-attr-controller: `/mgmtconfig/v2/admin/customers/{customerId}/samlAttribute`.
- Provide the `customerId`, the ZPA tenant ID of the customer, in the request endpoint. For example: `/mgmtconfig/v2/admin/customers/72057594037927936/samlAttribute`.
- [View an example response](#ViewExample3)
[]{
"totalPages": "3",
"list": [
{
"id": "72057594038042068",
"creationTime": "1625606470",
"modifiedBy": "72057594038006701",
"name": "dssd",
"userAttribute": false,
"idpId": "72057594037961373",
"samlName": "ds",
"idpName": "test"
}
]
}
A successful response returns code 200. To learn more, see [API Response Codes and Error Messages](/zpa/api-response-codes-and-error-messages).
This API supports pagination. To get a paginated response:
- Send a `GET` request to the following endpoint: `/mgmtconfig/v2/admin/customers/{customerId}/samlAttribute?page=1&pagesize=20`.
- Provide the following in the request endpoint:
- `customerId`: The ZPA tenant ID of the customer.
- Valid values for page and page size parameters.
For example: `/mgmtconfig/v2/admin/customers/217246660302995456/samlAttribute?page=1&pagesize=2.`
- [View an example response](#paginatedResponse)
[]
"totalPages": "9",
"list": [
{
"id": "217246660303022132",
"creationTime": "1521664572",
"modifiedBy": "217246660302996239",
"name": "Department",
"userAttribute": false,
"idpId": "217246660303022502",
"samlName": "Dept",
"idpName": "IDP Configuration - User SSO"
},
{
"id": "217246660303022772",
"creationTime": "1549853479",
"modifiedBy": "217246660302995744",
"name": "Department my1",
"userAttribute": false,
"idpId": "217246660303022502",
"samlName": "departmentmy1",
"idpName": "IDP Configuration - User SSO"
}
]
}
If not provided, the default page size is 20. The maximum page size is 500.
A successful response returns code 200. To learn more, see [API Response Codes and Error Messages](/zpa/api-response-codes-and-error-messages).
Getting Details of All SAML Attributes by Given Customer
To get all SAML attributes by customer:
- Send a `GET` request to the following endpoint in the saml-attr-controller: `/mgmtconfig/v2/admin/customers/{customerId}/samlAttribute/idp/{idpId}`.
- Use the following values in the request endpoint:
- `customerId`: The ZPA tenant ID of the customer.
- `idpId`: The ID of the IdP corresponding to the SAML attribute.
For example: `/mgmtconfig/v2/admin/customers/217246660302995456/samlAttribute/idp/217246660303022670`.
- [View an example response](#ViewExample4)
[]{
"totalPages": "1",
"list": [
{
"id": "217246660303022795",
"creationTime": "1550435486",
"modifiedBy": "217246660302995986",
"name": "login_Custom entityId IDP configuration - User sso - do NOT delete",
"userAttribute": false,
"idpId": "217246660303022670",
"samlName": "login"
},
{
"id": "217246660303024892",
"creationTime": "1617867425",
"modifiedBy": "217246660303024869",
"name": "s",
"userAttribute": false,
"idpId": "217246660303022670",
"samlName": "as"
},
{
"id": "217246660303022796",
"creationTime": "1550435486",
"modifiedBy": "217246660302995986",
"name": "username_Custom entityId IDP configuration - User sso - do NOT delete",
"userAttribute": false,
"idpId": "217246660303022670",
"samlName": "username"
}
]
}
A successful response returns code 200. To learn more, see [API Response Codes and Error Messages](/zpa/api-response-codes-and-error-messages).
This API supports pagination. To get a paginated response:
- Send a `GET` request to the following endpoint: `/mgmtconfig/v2/admin/customers/{customerId}/samlAttribute/idp/{idpId}?page=1&pagesize=20`.
- Provide the following in the request endpoint:
- `customerId`: The ZPA tenant ID of the customer.
- `idpId`: The ID of the IdP corresponding to the SAML attribute.
- Valid values for page and page size parameters.
For example: `/mgmtconfig/v2/admin/customers/217246660302995456/samlAttribute/idp/217246660303022670?page=1&pagesize=2.`
- [View an example response](#paginatedResponse2)
[]{
"totalPages": "2",
"list": [
{
"id": "217246660303022795",
"creationTime": "1550435486",
"modifiedBy": "217246660302995986",
"name": "login_Custom entityId IDP configuration - User sso - do NOT delete",
"userAttribute": false,
"idpId": "217246660303022670",
"samlName": "login"
},
{
"id": "217246660303024892",
"creationTime": "1617867425",
"modifiedBy": "217246660303024869",
"name": "s",
"userAttribute": false,
"idpId": "217246660303022670",
"samlName": "as"
}
]
}
If not provided, the default page size is 20. The maximum page size is 500.
A successful response returns code 200. To learn more, see [API Response Codes and Error Messages](/zpa/api-response-codes-and-error-messages).