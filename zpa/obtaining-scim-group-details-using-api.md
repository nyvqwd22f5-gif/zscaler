# Obtaining SCIM Group Details Using API
Source: https://help.zscaler.com/zpa/obtaining-scim-group-details-using-api
PDF: https://help.zscaler.com/pdf/com/en/1484846.pdf

This article provides information on managing Zscaler Private Access (ZPA) SCIM group use cases using APIs. All APIs are rate limited. To learn more, see [Understanding Rate Limiting](/zpa/understanding-rate-limiting).
Getting Details of All SCIM Groups
To get details of all SCIM groups for the specified IdP ID:
- Send a `GET` request to the following endpoint: `/userconfig/v1/customers/{customerId}/scimgroup/idpId/{idpId}`.
- Provide the following values in the request endpoint:
- `customerId`: The ZPA tenant ID of the customer.
- `idpId`: The ID of a particular IdP. To learn more, see [Obtaining IdP Configuration Details Using API](/zpa/obtaining-idp-configuration-details-using-api).
For example: `/userconfig/v1/customers/72057615512764416/scimgroup/idpId/73196561382768893`.
- [View an example response](#Viewanexampleresponse)
[]{
"totalPages": "1",
"totalCount": "2",
"list": [
{
"id": "20464",
"modifiedTime": "1610781818",
"creationTime": "1610626185",
"name": "group 2 public api",
"idpId": "73196561382768893",
"idpGroupId": null
},
{
"id": "20463",
"modifiedTime": "1610781110",
"creationTime": "1610626168",
"name": "group 1 public api",
"idpId": "73196561382768893",
"idpGroupId": null
}
]
}
A successful response returns code 200. To learn more, see [API Response Codes and Error Messages](/zpa/api-response-codes-and-error-messages).
This API supports pagination and sort capabilities. To get a paginated response and sort:
- Send a `GET` request to the following endpoint: `/userconfig/v1/customers/{customerId}/scimgroup/idpId/{idpId}?page=1&pagesize=5&sortBy=name&sortOrder=DSC`.
- Provide the following in the request endpoint:
- `customerId`: The ZPA tenant ID of the customer, in the request endpoint.
- `idpId`: The ID of a particular IdP.
- Valid values for page and page size parameters.
- Valid `sortBy` string values (e.g., `name`).
For example: `/userconfig/v1/customers/145254298228359168/scimgroup/idpId/145254298228359525?page=1&pagesize=5&sortBy=name&sortOrder=DSC`.
- [View an example response](#GetAllScimPagResponse)
[]{
"totalPages": 70000,
"totalCount": 350000,
"list": [
{
"id": 1981044,
"modifiedTime": 1666936258,
"creationTime": 1666073884,
"name": "grp99999",
"idpId": 145254298228359520,
"idpGroupId": "grp99999",
"internalId": "1981044"
},
{
"id": 1981043,
"modifiedTime": 1666936258,
"creationTime": 1666073884,
"name": "grp99998",
"idpId": 145254298228359520,
"idpGroupId": "grp99998",
"internalId": "1981043"
},
{
"id": 1981042,
"modifiedTime": 1666936258,
"creationTime": 1666073884,
"name": "grp99997",
"idpId": 145254298228359520,
"idpGroupId": "grp99997",
"internalId": "1981042"
},
{
"id": 1981041,
"modifiedTime": 1666936258,
"creationTime": 1666073884,
"name": "grp99996",
"idpId": 145254298228359520,
"idpGroupId": "grp99996",
"internalId": "1981041"
},
{
"id": 1981040,
"modifiedTime": 1666936258,
"creationTime": 1666073884,
"name": "grp99995",
"idpId": 145254298228359520,
"idpGroupId": "grp99995",
"internalId": "1981040"
}
]
}
If not provided, the default page size is 20. The maximum page size is 500.
A successful response returns code 200. To learn more, see [API Response Codes and Error Messages](/zpa/api-response-codes-and-error-messages).
Getting Details for a Particular SCIM Group
To get details of a particular SCIM group:
- Send a `GET` request to the following endpoint: `/userconfig/v1/customers/{customerId}/scimgroup/{scimGroupId}`.
- Use the following values in the request endpoint:
- `customerId`: The ZPA tenant ID of the customer.
- `scimGroupId`: The ID of a particular SCIM group.
For example: `/userconfig/v1/customers/72057615512764416/scimgroup/20464`.
- [View an example response](#Viewanexampleresponse2)
[]{
"id": "20464",
"modifiedTime": "1610781818",
"creationTime": "1610626185",
"name": "group 2 public api",
"idpId": "73196561382768893",
"idpGroupId": null
}
A successful response returns code 200. To learn more, see [API Response Codes and Error Messages](/zpa/api-response-codes-and-error-messages).
Field Descriptions
The following table includes descriptions of available fields for the SCIM group use cases:
-
-
-
-
| Field | Description | Required | Value |
| ----- | ----------- | -------- | ----- |
| page | Indicates the page. If not provided, the default value is `1`. | No | Integer |
| pageSize | Indicates the page size. If not provided, the default page size is `20`. The max page size is `500`. | No | Integer |
| sortBy | Indicates the `sortBy` field name that is used to sort the results. If not provided, the results are sorted by `modifiedTime`. | No | Supported values:`id``name``creationTime``modifiedTime` |