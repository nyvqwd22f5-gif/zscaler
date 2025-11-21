# Obtaining SCIM Attribute Details Using API
Source: https://help.zscaler.com/zpa/obtaining-scim-attribute-details-using-api
PDF: https://help.zscaler.com/pdf/com/en/1484851.pdf

This article provides information on managing Zscaler Private Access (ZPA) SCIM attribute use cases using APIs. All APIs are rate limited. To learn more, see [Understanding Rate Limiting](/zpa/understanding-rate-limiting).
Getting Details for All SCIM Attributes
To get details for all the SCIM attributes:
- Send a `GET` request to the endpoint `/mgmtconfig/v1/admin/customers/{customerId}/idp/{idpId}/scimattribute` in the scim-attribute-header-controller.
- Provide the following values in the request body:
- `customerId`: The ZPA tenant ID of the customer.
- `idpId`: The ID of the IdP corresponding to the SCIM attribute.
For example: `/mgmtconfig/v1/admin/customers/72057615512764416/idp/73196561382768893/scimattribute`.
- [View an example response](#Viewanexampleresponse)
[]{
"totalPages": "1",
"list": [
{
"id": "73196561382768901",
"creationTime": "1610625597",
"modifiedBy": "73196561382768641",
"name": "active",
"idpId": "73196561382768893",
"dataType": "Boolean",
"schemaURI": "urn:ietf:params:scim:schemas:core:2.0:User",
"multivalued": false,
"required": false,
"caseSensitive": false,
"mutability": "readWrite",
"returned": "default",
"uniqueness": false
},
{
"id": "73196561382768904",
"creationTime": "1610625597",
"modifiedBy": "73196561382768641",
"name": "costCenter",
"idpId": "73196561382768893",
"dataType": "String",
"schemaURI": "urn:ietf:params:scim:schemas:extension:enterprise:2.0:User",
"multivalued": false,
"required": false,
"caseSensitive": false,
"mutability": "readWrite",
"returned": "default",
"uniqueness": false
},
{
"id": "73196561382768903",
"creationTime": "1610625597",
"modifiedBy": "73196561382768641",
"name": "department",
"idpId": "73196561382768893",
"dataType": "String",
"schemaURI": "urn:ietf:params:scim:schemas:extension:enterprise:2.0:User",
"multivalued": false,
"required": false,
"caseSensitive": false,
"mutability": "readWrite",
"returned": "default",
"uniqueness": false
},
{
"id": "73196561382768899",
"creationTime": "1610625597",
"modifiedBy": "73196561382768641",
"name": "displayName",
"idpId": "73196561382768893",
"dataType": "String",
"schemaURI": "urn:ietf:params:scim:schemas:core:2.0:User",
"multivalued": false,
"required": false,
"caseSensitive": false,
"mutability": "readWrite",
"returned": "default",
"uniqueness": false
},
{
"id": "73196561382768906",
"creationTime": "1610625597",
"modifiedBy": "73196561382768641",
"name": "division",
"idpId": "73196561382768893",
"dataType": "String",
"schemaURI": "urn:ietf:params:scim:schemas:extension:enterprise:2.0:User",
"multivalued": false,
"required": false,
"caseSensitive": false,
"mutability": "readWrite",
"returned": "default",
"uniqueness": false
},
{
"id": "73196561382768902",
"creationTime": "1610625597",
"modifiedBy": "73196561382768641",
"name": "emails.value",
"idpId": "73196561382768893",
"dataType": "String",
"schemaURI": "urn:ietf:params:scim:schemas:core:2.0:User",
"multivalued": true,
"required": false,
"canonicalValues": [
"work"
],
"caseSensitive": false,
"mutability": "readWrite",
"returned": "default",
"uniqueness": false
},
{
"id": "73196561382768895",
"creationTime": "1610625597",
"modifiedBy": "73196561382768641",
"name": "name.familyName",
"idpId": "73196561382768893",
"dataType": "String",
"schemaURI": "urn:ietf:params:scim:schemas:core:2.0:User",
"multivalued": false,
"required": false,
"caseSensitive": false,
"mutability": "readWrite",
"returned": "default",
"uniqueness": false
},
{
"id": "73196561382768897",
"creationTime": "1610625597",
"modifiedBy": "73196561382768641",
"name": "name.formatted",
"idpId": "73196561382768893",
"dataType": "String",
"schemaURI": "urn:ietf:params:scim:schemas:core:2.0:User",
"multivalued": false,
"required": false,
"caseSensitive": false,
"mutability": "readWrite",
"returned": "default",
"uniqueness": false
},
{
"id": "73196561382768896",
"creationTime": "1610625597",
"modifiedBy": "73196561382768641",
"name": "name.givenName",
"idpId": "73196561382768893",
"dataType": "String",
"schemaURI": "urn:ietf:params:scim:schemas:core:2.0:User",
"multivalued": false,
"required": false,
"caseSensitive": false,
"mutability": "readWrite",
"returned": "default",
"uniqueness": false
},
{
"id": "73196561382768898",
"creationTime": "1610625597",
"modifiedBy": "73196561382768641",
"name": "nickName",
"idpId": "73196561382768893",
"dataType": "String",
"schemaURI": "urn:ietf:params:scim:schemas:core:2.0:User",
"multivalued": false,
"required": false,
"caseSensitive": false,
"mutability": "readWrite",
"returned": "default",
"uniqueness": false
},
{
"id": "73196561382768905",
"creationTime": "1610625597",
"modifiedBy": "73196561382768641",
"name": "organization",
"idpId": "73196561382768893",
"dataType": "String",
"schemaURI": "urn:ietf:params:scim:schemas:extension:enterprise:2.0:User",
"multivalued": false,
"required": false,
"caseSensitive": false,
"mutability": "readWrite",
"returned": "default",
"uniqueness": false
},
{
"id": "73196561382768894",
"creationTime": "1610625597",
"modifiedBy": "73196561382768641",
"name": "userName",
"idpId": "73196561382768893",
"dataType": "String",
"schemaURI": "urn:ietf:params:scim:schemas:core:2.0:User",
"multivalued": false,
"required": true,
"caseSensitive": false,
"mutability": "readWrite",
"returned": "default",
"uniqueness": true
},
{
"id": "73196561382768900",
"creationTime": "1610625597",
"modifiedBy": "73196561382768641",
"name": "userType",
"idpId": "73196561382768893",
"dataType": "String",
"schemaURI": "urn:ietf:params:scim:schemas:core:2.0:User",
"multivalued": false,
"required": false,
"caseSensitive": false,
"mutability": "readWrite",
"returned": "default",
"uniqueness": false
}
]
}
A successful response returns code 200. To learn more, see [About Error Codes](/zpa/about-error-codes).
This API supports pagination. To get a paginated response:
- Send a `GET` request to the endpoint `/mgmtconfig/v1/admin/customers/{customerId}/idp/{idpId}/scimattribute?page=1&pagesize=20`.
- Provide the following in the request endpoint:
- `customerId`: The ZPA tenant ID of the customer, in the request endpoint.
- `idpId`: The ID of the IdP corresponding to the SCIM attribute.
- Valid values for page and page size parameters.
For example: `/mgmtconfig/v1/admin/customers/144118148382064640/idp/144118148382065427/scimattribute?page=1&pagesize=2.`
- [View an example response](#paginatedResponse)
[]{
"totalPages": "7",
"list": [
{
"id": "144118148382065476",
"creationTime": "1621016226",
"modifiedBy": "144118148382065457",
"name": "active",
"idpId": "144118148382065427",
"dataType": "Boolean",
"schemaURI": "urn:ietf:params:scim:schemas:core:2.0:User",
"multivalued": false,
"required": false,
"caseSensitive": false,
"mutability": "readWrite",
"returned": "default",
"uniqueness": false
},
{
"id": "144118148382065479",
"creationTime": "1621016226",
"modifiedBy": "144118148382065457",
"name": "costCenter",
"idpId": "144118148382065427",
"dataType": "String",
"schemaURI": "urn:ietf:params:scim:schemas:extension:enterprise:2.0:User",
"multivalued": false,
"required": false,
"caseSensitive": false,
"mutability": "readWrite",
"returned": "default",
"uniqueness": false
}
]
}
If not provided, the default page size is 20. The maximum page size is 500.
A successful response returns code 200. To learn more, see [API Response Codes and Error Messages](/zpa/api-response-codes-and-error-messages).
Getting Details for a Particular SCIM Attribute
To get the name, or key, for a particular SCIM attribute:
- Send a `GET` request to the endpoint `/mgmtconfig/v1/admin/customers/{customerId}/idp/{idpId}/scimattribute/``{scimAttributeId}` in the scim-attribute-header-controller.
- Provide the following values in the request endpoint:
- `customerId`: The ZPA tenant ID of the customer.
- `idpId`: The ID of the Idp corresponding to the SCIM attribute.
- `scimAttributeId`: The ID of the SCIM attribute.
For example: `/mgmtconfig/v1/admin/customers/72057615512764416/idp/73196561382768893/scimattribute/73196561382768901`.
- [View an example response](#Viewanexampleresponse2)
[]{
"id": "73196561382768901",
"creationTime": "1610625597",
"modifiedBy": "73196561382768641",
"name": "active",
"idpId": "73196561382768893",
"dataType": "Boolean",
"schemaURI": "urn:ietf:params:scim:schemas:core:2.0:User",
"multivalued": false,
"required": false,
"caseSensitive": false,
"mutability": "readWrite",
"returned": "default",
"uniqueness": false
}
A successful response returns code 200. To learn more, see [API Response Codes and Error Messages](/zpa/api-response-codes-and-error-messages).
[]Getting Details for a SCIM Attribute Value
To get the value of the particular key for a SCIM attribute value:
- Send a `GET` request to the endpoint `/userconfig/v1/customers/{customerId}/scimattribute/idpId/{idpId}/attributeId/{attributeId}` in the scim-attribute-header-controller**. **
- Provide the following values in the request endpoint:
- `customerId`: The ZPA tenant ID of the customer.
- `idpId`: The ID of the IdP corresponding to the SCIM attribute.
- `attributeId`: The ID of the SCIM attribute.
For example: `/mgmtconfig/v1/admin/customers/72057615512764416/idp/73196561382768893/scimattribute/73196561382768901`.
- [View an example response](#Viewanexampleresponse3)
[]{
"totalPages": "1",
"totalCount": "1",
"list": [
"true"
]
}
A successful response returns code 200. To learn more, see [API Response Codes and Error Messages](/zpa/api-response-codes-and-error-messages).
This API supports pagination. To get a paginated response:
- Send a `GET` request to the endpoint `/userconfig/v1/customers/{customerId}/scimattribute/idpId/{idpId}/attributeId/{attributeId}?page=1&pagesize=20`.
- Provide the following in the request endpoint:
- `customerId`, the ZPA tenant ID of the customer, in the request endpoint.
- `idpId`: The ID of the IdP corresponding to the SCIM attribute.
- `attributeId`: The ID of the SCIM attribute.
- Valid values for page and page size parameters.
For example: `/mgmtconfig/v1/admin/customers/217246660302995456/idp/217246660303022670/scimattribute/217246660303023460?page=1&pagesize=2.`
- [View an example response](#paginatedResponse2)
[]{
"totalPages": 1,
"totalCount": 1,
"list": [
"true"
]
}
If not provided, the default page size is 20. The maximum page size is 500.
A successful response returns code 200. To learn more, see [API Response Codes and Error Messages](/zpa/api-response-codes-and-error-messages).