# Configuring Certificates Using API
Source: https://help.zscaler.com/zpa/configuring-certificates-using-api
PDF: https://help.zscaler.com/pdf/com/en/1484831.pdf

This article provides information on managing Zscaler Private Access (ZPA) certificate use cases using APIs. All APIs are rate limited. To learn more, see [Understanding Rate Limiting](/zpa/understanding-rate-limiting).
Getting Details for All Issued Certificates
This API is deprecated and will not be supported after January 27, 2023. To learn more, see [Getting Details for All Issued Certificates V2](#V2).
To get details for all certificates:
- Send a `GET` request to the following endpoint: `/mgmtconfig/v2/admin/customers/{customerId}/clientlessCertificate/issued`.
- Provide the `customerId`, the ZPA tenant ID of the customer, in the request endpoint. For example: `/mgmtconfig/v2/admin/customers/217246660302995456/clientlessCertificate/issued`.
- [View an example response](#ViewExample3)
[]{
"totalPages": "6",
"list": [
{
"id": "217246660303022175",
"modifiedTime": "1524677325",
"creationTime": "1523662106",
"modifiedBy": "217246660302995849",
"name": "*.examplesl.com",
"description": "ff",
"cName": "*.examplesl.com",
"validFromInEpochSec": "1523661691",
"validToInEpochSec": "1555197691",
"certificate": "-----BEGIN CERTIFICATE-----\nMIIDdTCCAl2gAwIBAgIIJCvWdDisi4QwDQYJKoZIhvcNAQELBQAwYTELMAkGA1UE\nBhMCVVMxEzARBgNVBAgMCkNhbGlmb3JuaWExEDAOBgNVBAo\n-----END CERTIFICATE-----\n",
"issuedTo": "CN=*.examplesl.com,O=Zscaler,ST=California,C=US",
"issuedBy": "CN=Testing Intermediate Certificate 2,O=Zscaler,ST=California,C=US",
"serialNo": "2606412604019346308",
"publicKey": "-----BEGIN PUBLIC KEY-----\nMIIBIjANBgkqhkiG9w0BAQEFAAOCAQ8AMIIBCgKCAQEAw/Pqr3HUpwFPwqOc9/Md\nk++G2JLR9j5HqZVmkSOlUi5Q4ggHhZ8+r6AsMuLTmZUAP/62JD\n-----END PUBLIC KEY-----\n",
"certChain": "-----BEGIN CERTIFICATE-----\nMIIDkzCCAnugAwIBAgIJAKyRiWWvB6J6MA0GCSqGSIb3DQEBCwUAMF8xCzAJBgNV\nBAYTAlVTMRMwEQYDVQQIDApDYWxpZm9ybmlhMRAwDgYDVQQKD\n-----END CERTIFICATE-----\n"
},
{
"id": "217246660303022109",
"creationTime": "1520014170",
"modifiedBy": "217246660302995458",
"name": "CN=*.examples1.com,O=Zscaler,ST=California,C=US",
"cName": "*.chanak.com",
"validFromInEpochSec": "1519963049000",
"validToInEpochSec": "1551499049000",
"certificate": "-----BEGIN CERTIFICATE-----\nMIIDdjCCAl6gAwIBAgIJALEcnE//uGOvMA0GCSqGSIb3DQEBCwUAMGExCzAJBgNV\nBAYTAlVTMRMwEQYDVQQIDApDYWxpZm9ybmlhMRAwDgYDVQQ\n-----END CERTIFICATE-----\n",
"issuedTo": "CN=*.examples1.com,O=Zscaler,ST=California,C=US",
"issuedBy": "CN=Testing Intermediate Certificate 2,O=Zscaler,ST=California,C=US",
"serialNo": "12762247311467766703",
"publicKey": "-----BEGIN PUBLIC KEY-----\nMIIBIjANBgkqhkiG9w0BAQEFAAOCAQ8AMIIBCgKCAQEAxPNTlNYNr/3D3mRDhFyU\no4eYCAN3mVlxzG9lFfvOZgGWiFRzrdNNF2UnDJhjikCXSuTF/\n-----END PUBLIC KEY-----\n",
"certChain": "-----BEGIN CERTIFICATE-----\nMIIDkjCCAnqgAwIBAgIIR9bHk2qmqn8wDQYJKoZIhvcNAQELBQAwXzELMAkGA1UE\nBhMCVVMxEzARBgNVBAgMCkNhbGlmb3JuaWExEDAOBgNVBAoMB\n-----END CERTIFICATE-----\n"
}
]
}
A successful response returns code 200. To learn more, see [API Response Codes and Error Messages](/zpa/api-response-codes-and-error-messages).
This API supports pagination. To get a paginated response:
- Send a `GET` request to the following endpoint: `/mgmtconfig/v2/admin/customers/{customerId}/clientlessCertificate/issued?page=1&pagesize=20`.
- Provide the following in the request endpoint:
- `customerId`: The ZPA tenant ID of the customer.
- Valid values for page and page size parameters.
For example: `/mgmtconfig/v2/admin/customers/144118148382064931/clientlessCertificate/issued?page=1&pagesize=2`.
- [View an example response](#paginatedResponse)
[]{
"totalPages": "2",
"list": [
{
"id": "144118148382064931",
"modifiedTime": "1648916882",
"creationTime": "1532110078",
"modifiedBy": "72057594037929181",
"name": "ADMIN",
"description": "desc",
"cName": "ak",
"validFromInEpochSec": "1530614700",
"validToInEpochSec": "1846233900",
"certificate": "-----BEGIN CERTIFICATE-----\nMIIDsjCCApqgAwIBAgIBATANBgkqhkiG9w0BAQUFADBhMQswCQY\n-----END CERTIFICATE-----\n",
"issuedTo": "1.2.840.113549.1.9.1=#1602616b,CN=ak,OU=ak,O=ak,L=IN,ST=IN,C=IN",
"issuedBy": "1.2.840.113549.1.9.1=#1602616b,CN=ak,OU=ak,O=ak,L=IN,ST=IN,C=IN",
"serialNo": "1",
"publicKey": "-----BEGIN PUBLIC KEY-----\nMIIBIjANBgkqhkiG9w0BAQEFAAOCAQ8AMIIBCgKCAQEAxEhVOulm9\n-----END PUBLIC KEY-----\n"
},
{
"id": "144118148382065029",
"modifiedTime": "1648916882",
"creationTime": "1532636586",
"modifiedBy": "72057594037929181",
"name": "Bitnami CRM cert",
"cName": "www.example.com",
"validFromInEpochSec": "1532538688",
"validToInEpochSec": "1847898688",
"certificate": "-----BEGIN CERTIFICATE-----\nMIIDLjCCAhYCCQCSX0pPo6MXYDANBgkqhkiG9w0BA\n-----END CERTIFICATE-----\n",
"issuedTo": "CN=www.example.com,OU=Certificate generated at boot time,O=Bitnami",
"issuedBy": "CN=www.example.com,OU=Certificate generated at boot time,O=Bitnami",
"serialNo": "10547230558233237344",
"publicKey": "-----BEGIN PUBLIC KEY-----\nMIIBIjANBgkqhkiG9w0BAQEFAAOCAQ8AMIIBCgB\n-----END PUBLIC KEY-----\n"
}
]
}
If not provided, the default page size is 20. The maximum page size is 500.
A successful response returns code 200. To learn more, see [API Response Codes and Error Messages](/zpa/api-response-codes-and-error-messages).
[]Getting Details for All Issued Certificates V2
To get details for all certificates:
- Send a `GET` request to the following endpoint: `/mgmtconfig/v2/admin/customers/{customerId}/certificate/issued?microtenantId={microtenantId}`.
-
Provide the following in the request endpoint:
- `customerId`, the ZPA tenant ID of the customer, in the request endpoint.
- `microtenantId`: The unique identifier of the Microtenant. If you are within a Microtenant, you must pass the `microtenantId` field when making an API call to retrieve data from that Microtenant. The `microtenantId` can be obtained from the API Keys page, or can be obtained programmatically using the ZPA cloud service API. Access to certain operations is limited when you are within a Microtenant. If you are within the Default Microtenant, pass `microtenantId` as `0` when making requests to retrieve data from the Default Microtenant. If the `microtenantId` is not passed in the request when creating or updating a resource, then the resource is created or updated in the Default Microtenant. To learn more, see [Configuring Microtenants Using API](/zpa/configuring-microtenants-using-api).
For example: `/mgmtconfig/v2/admin/customers/217246660302995456/certificate/issued?microtenantId=0`.
- [View an example response](#v2example)
[]{
"totalPages":"4",
"list":[
{
"id":"144118148382064931",
"modifiedTime":"1648916882",
"creationTime":"1532110078",
"modifiedBy":"72057594037929181",
"name":"Test",
"microtenantName":"Default",
"description":"desc",
"cName":"ak",
"validFromInEpochSec":"1530614700",
"validToInEpochSec":"1846233900",
"certificate":"-----BEGIN CERTIFICATE-----\nMIIDsjCCApqgAwIBAgIBATANBgkqhkiG9w0BAQUFADBhMQswCQYDVQQG\n-----END CERTIFICATE-----\n",
"issuedTo":"1.2.840.113549.1.9.1=#1602616b,CN=ak,OU=ak,O=ak,L=IN,ST=IN,C=IN",
"issuedBy":"1.2.840.113549.1.9.1=#1602616b,CN=ak,OU=ak,O=ak,L=IN,ST=IN,C=IN",
"serialNo":"1",
"publicKey":"-----BEGIN PUBLIC KEY-----\nMIIBIjANBgkqhkiG9w0BAQEFAAOCAQ8AMIIBCgKCAQEA\nxQIDAQAB\n-----END PUBLIC KEY-----\n"
}
]
}
A successful response returns code 200. To learn more, see [API Response Codes and Error Messages](/zpa/api-response-codes-and-error-messages).
This API supports pagination. To get a paginated response:
- Send a GET request to the following endpoint: `/mgmtconfig/v2/admin/customers/{customerId}/certificate/issued?microtenantId={microtenantId}&page={page}&pagesize={pagesize}`.
- Provide the following in the request endpoint:
- `customerId`: The ZPA tenant ID of the customer.
- `microtenantId`: The unique identifier of the Microtenant. If you are within a Microtenant, you must pass the `microtenantId` field when making an API call to retrieve data from that Microtenant. The `microtenantId` can be obtained from the API Keys page, or can be obtained programmatically using the ZPA cloud service API. Access to certain operations is limited when you are within a Microtenant. If you are within the Default Microtenant, pass `microtenantId` as `0` when making requests to retrieve data from the Default Microtenant. If the `microtenantId` is not passed in the request when creating or updating a resource, then the resource is created or updated in the Default Microtenant. To learn more, see [Configuring Microtenants Using API](/zpa/configuring-microtenants-using-api).
- `page`: Specifies the page number.
- `pagesize`: Specifies the page size. If not provided, the default page size is 20. The maximum page size is 500.
For example: `/mgmtconfig/v2/admin/customers/144118148382064931/certificate/issued?microtenantId=0&page=1&pagesize=2`.
- [View an example response](#v2paginationExample)
[]{
"totalPages":"2",
"list":[
{
"id":"144118148382064931",
"modifiedTime":"1648916882",
"creationTime":"1532110078",
"modifiedBy":"72057594037929181",
"name":"Test",
"microtenantName":"Default",
"description":"desc",
"cName":"ak",
"validFromInEpochSec":"1530614700",
"validToInEpochSec":"1846233900",
"certificate":"-----BEGIN CERTIFICATE-----\nMIIDsjCCApqgAwIBAgIBATANBgkqhkiG9w0BAQUFADBhMQswCQYD\nMVaMj588I+mFwAiZR2YiMmvblVlPOqYlzU8M+2ACSpDu1qGZZyc=\n-----END CERTIFICATE-----\n",
"issuedTo":"1.2.840.113549.1.9.1=#1602616b,CN=ak,OU=ak,O=ak,L=IN,ST=IN,C=IN",
"issuedBy":"1.2.840.113549.1.9.1=#1602616b,CN=ak,OU=ak,O=ak,L=IN,ST=IN,C=IN",
"serialNo":"1",
"publicKey":"-----BEGIN PUBLIC KEY-----\nMIIBIjANBgkqhkiG9w0BAQEFAAOCAQ8AMIIBCgKCAQEAxEhVOulm9GV4dqoFNZz\nDIzzOjzsdWfgGGsPqU4TaranQX5Y1N+029IB2nSdQfnbHXDjcWDS5RG0ImDAPGay\nxQIDAQAB\n-----END PUBLIC KEY-----\n"
},
{
"id":"144118148382065029",
"modifiedTime":"1648916882",
"creationTime":"1532636586",
"modifiedBy":"72057594037929181",
"name":"Test2",
"microtenantName":"Default",
"cName":"www.example.com",
"validFromInEpochSec":"1532538688",
"validToInEpochSec":"1847898688",
"certificate":"-----BEGIN CERTIFICATE-----\nMIIDLjCCAhYCCQCSX0pPo6MXYDANBgkqhkiG9w0BAQsFADBZ/lagEnHJL0Ba6vMeHc0SG9m6rT2KXJfYYf/ejB0XgpZp5L\nR5U=\n-----END CERTIFICATE-----\n",
"issuedTo":"CN=www.example.com,OU=Certificate generated at boot time,O=Bitnami",
"issuedBy":"CN=www.example.com,OU=Certificate generated at boot time,O=Bitnami",
"serialNo":"10547230558233237344",
"publicKey":"-----BEGIN PUBLIC KEY-----\nMIIBIjANBgkqhkiG9w0BAQEFAAOCAQ8AMIIB\n1QIDAQAB\n-----END PUBLIC KEY-----\n"
}
]
}
A successful response returns code 200. To learn more, see [API Response Codes and Error Messages](/zpa/api-response-codes-and-error-messages).
Getting a List of All Certificates
To get a list of all certificates:
- Send a `GET` request to the following endpoint: `/mgmtconfig/v1/admin/customers/{customerId}/certificate?microtenantId={microtenantId}`.
-
Provide the following in the request endpoint:
- `customerId`, the ZPA tenant ID of the customer,
- `microtenantId`: The unique identifier of the Microtenant. If you are within a Microtenant, you must pass the `microtenantId` field when making an API call to retrieve data from that Microtenant. The `microtenantId` can be obtained from the API Keys page, or can be obtained programmatically using the ZPA cloud service API. Access to certain operations is limited when you are within a Microtenant. If you are within the Default Microtenant, pass `microtenantId` as `0` when making requests to retrieve data from the Default Microtenant. If the `microtenantId` is not passed in the request when creating or updating a resource, then the resource is created or updated in the Default Microtenant. To learn more, see [Configuring Microtenants Using API](/zpa/configuring-microtenants-using-api).
For example: `/mgmtconfig/v1/admin/customers/73194682334576640/certificate`.
- [View an example response](#allCertsExample)
[]{
"totalPages":"5",
"list":[
{
"id":"144118148382064931",
"modifiedTime":"1648916882",
"creationTime":"1532110078",
"modifiedBy":"72057594037929181",
"name":"Test",
"microtenantName":"Default",
"description":"desc",
"cName":"ak",
"validFromInEpochSec":"1530614700",
"validToInEpochSec":"1846233900",
"certificate":"-----BEGIN CERTIFICATE-----\nMIIDsjCCApqgAwIBAgIBATANBgkqhkiG9w0BAQUFADBhMQs\n-----END CERTIFICATE-----\n",
"issuedTo":"1.2.840.113549.1.9.1=#1602616b,CN=ak,OU=ak,O=ak,L=IN,ST=IN,C=IN",
"issuedBy":"1.2.840.113549.1.9.1=#1602616b,CN=ak,OU=ak,O=ak,L=IN,ST=IN,C=IN",
"serialNo":"1",
"publicKey":"-----BEGIN PUBLIC KEY-----\nMIIBIjANBgkqhkiG9w0BAQEFAAOCAQ8AMIIBCgKCAQEAxEhVOulm9GV\n-----END PUBLIC KEY-----\n"
}
]
}
A successful response returns code 200. To learn more, see [API Response Codes and Error Messages](/zpa/api-response-codes-and-error-messages).
This API supports pagination. To get a paginated response:
- Send a `GET` request to the endpoint: `/mgmtconfig/v1/admin/customers/{customerId}/certificate?microtenantId={microtenantId}&page={page}&pagesize={pagesize}`.
- Provide the following in the request endpoint:
- `customerId`: The ZPA tenant ID of the customer.
- `microtenantId`: The unique identifier of the Microtenant. If you are within a Microtenant, you must pass the `microtenantId` field when making an API call to retrieve data from that Microtenant. The `microtenantId` can be obtained from the API Keys page, or can be obtained programmatically using the ZPA cloud service API. Access to certain operations is limited when you are within a Microtenant. If you are within the Default Microtenant, pass `microtenantId` as `0` when making requests to retrieve data from the Default Microtenant. If the `microtenantId` is not passed in the request when creating or updating a resource, then the resource is created or updated in the Default Microtenant. To learn more, see [Configuring Microtenants Using API](/zpa/configuring-microtenants-using-api).
- `page`: Specifies the page number.
- `pagesize`: Specifies the page size. If not provided, the default page size is 20. The maximum page size is 500.
For example: `/mgmtconfig/v1/admin/customers/73194682334576640/certificate?microtenantId=0&page=1&pagesize=2`.
- [View an example response](#allCertsPaginationExample)
[]{
"totalPages":"3",
"list":[
{
"id":"144118148382064931",
"modifiedTime":"1648916882",
"creationTime":"1532110078",
"modifiedBy":"72057594037929181",
"name":"ADMIN",
"microtenantName":"Default",
"description":"desc",
"cName":"ak",
"validFromInEpochSec":"1530614700",
"validToInEpochSec":"1846233900",
"certificate":"-----BEGIN CERTIFICATE-----\nMIIDsjCCApqgAwIBAgIBATANBgkqhkiG9w0BAQUFADBhMQswCQYDVQQGEwJJT=\n-----END CERTIFICATE-----\n",
"issuedTo":"1.2.840.113549.1.9.1=#1602616b,CN=ak,OU=ak,O=ak,L=IN,ST=IN,C=IN",
"issuedBy":"1.2.840.113549.1.9.1=#1602616b,CN=ak,OU=ak,O=ak,L=IN,ST=IN,C=IN",
"serialNo":"1",
"publicKey":"-----BEGIN PUBLIC KEY-----\nMIIBIjANBgkqhkiG9w0BAQEFAAOCAQ8AMIIBCgKCAQEAxEhVOulm9GV4dqoFNZz7\nSl5hoNw\n-----END PUBLIC KEY-----\n"
},
{
"id":"144118148382065029",
"modifiedTime":"1648916882",
"creationTime":"1532636586",
"modifiedBy":"72057594037929181",
"name":"Bitnami CRM cert",
"microtenantName":"Default",
"cName":"www.example.com",
"validFromInEpochSec":"1532538688",
"validToInEpochSec":"1847898688",
"certificate":"-----BEGIN CERTIFICATE-----\nMIIDLjCCAhYCCQCSX0pPo6MXYDANBgkqhkiG9w0BAQsFADBZMRAwDgYDVQQKDAdC/ejB0XgpZp5L\nR5U=\n-----END CERTIFICATE-----\n",
"issuedTo":"CN=www.example.com,OU=Certificate generated at boot time,O=Bitnami",
"issuedBy":"CN=www.example.com,OU=Certificate generated at boot time,O=Bitnami",
"serialNo":"10547230558233237344",
"publicKey":"-----BEGIN PUBLIC KEY-----\nMIIBIjANBgkqhkiG9w0BAQEFAAOCAQ8AMIIBCgKCAQEA7+4Onc+MdbP8\n-----END PUBLIC KEY-----\n"
}
]
}
A successful response returns code 200. To learn more, see [API Response Codes and Error Messages](/zpa/api-response-codes-and-error-messages).
This API supports a search option to search by features and fields. To search by features and fields:
- Send a `GET` request to the following endpoint: `/mgmtconfig/v1/admin/customers/73186051597795328/certificate&search={searchString}`.
- Provide the following in the request endpoint:
- `customerId`: The ZPA tenant ID of the customer.
- Valid search string values. The search string values are in the format `fieldName operator fieldValue`. Only search string values that correspond to the values for valid fields and filters are supported. For example, the string `name%20LIKE%20client` is supported for the **Name **filter, using the **Contains **(`LIKE`) operator, for the `client` filter value.
For example: `/mgmtconfig/v1/admin/customers/73186051597795328/certificate&search=name%20LIKE%20client`.
- [View an example response](#gettingAllCertsSearch)
[]{
"totalPages": "1",
"totalCount": "1",
"list": [
{
"id": "73186051597797529",
"modifiedTime": "1642071991",
"creationTime": "1548345659",
"modifiedBy": "72057594037951057",
"name": "clientless",
"description": "clientless",
"cName": "ga.dummy.com",
"validFromInEpochSec": "1533108480",
"validToInEpochSec": "1848727680",
"certificate": "-----BEGIN CERTIFICATE-----\nMIIDoDCCAoigAwIBAgIBATANBgkqhkiG9w0BAQsFADBYMQswCQYDVQQGEwJJTjEL\nMAkGA1UECBMCSU4xCzAJBgNVBAcTAklOMQswCQYDVQQKEwJnYTELMAkGA1UECxMC\nZ2ExFTATBgNVBAMTDGdhLmR1bW15LmNvbTAeFw0xODA4MDEwNzI4MDBaFw0yODA4\nMDEwNzI4MDBaMFgxCzAJBgNVBAYTAklOMQswCQYDVQQIEwJJTjELMAkGA1UEBxMC\nSU4xCzAJBgNVBAoTAmdhMQswCQYDVQQLEwJnYTEVMBMGA1UEAxMMZ2EuZHVtbXku\nY29tMIIBIjANBgkqhkiG9w0BAQEFAAOCAQ8AMIIBCgKCAQEAxM772y77AFo1lYAJ\nX+rkA30JhWAXtky+hyxIJROJ3OTHZPiOTMEXpArsYf6JbgNjLcFStxf3FaU3TFDp\nfL1Se/Z4RWJh3mS7Pnpc6i5Uxw/nc+0x1Au1B/cuFxTmhPRsGH8i0XsQD7FlKQad\nF/Dv0mbOjqDcrcczbDAOBgNVHQ8BAf8EBAMCAZ4wEQYJYIZIAYb4QgEBBAQDAgAH\nMB4GCWCGSAGG+EIBDQQRFg94Y2EgY2VydGlmaWNhdGUwDQYJKoZIhvcNAQELBQAD\nggEBAKjfZICpOtQkafJ9BpRiKdM6IKYXXw62F4QQwyNSjVl7c85Ki1j2B6KVNPWl\nD5lF30XXl0am+rNyUgnr5cWFIyUiWu9IE8zZDWU1l3jSD4Cbg/3koEn1tDY1QKje\n5tg5nEZLEelecFC2IO5pcoopnq/SxbMhXax8T5REWG0UTtKoFESzD+htJ46z03Tt\nqrcfs1w3U72YZiFlxA8LJFThYXZI6YOozs889sNi96E727C5yiMR7F2ofwuSzQHL\nmwp8Pe9g6G4Hae+cNLJyfAwq401WcPR7YDDUr6IVI9h0umT5g0JZ0615wTY0fa3J\n9qfvSipVrCuD6GvsCzV8gIdZlB4=\n-----END CERTIFICATE-----\n",
"issuedTo": "CN=ga.dummy.com,OU=ga,O=ga,L=IN,ST=IN,C=IN",
"issuedBy": "CN=ga.dummy.com,OU=ga,O=ga,L=IN,ST=IN,C=IN",
"serialNo": "1",
"publicKey": "-----BEGIN PUBLIC KEY-----\nMIIBIjANBgkqhkiG9w0BAQEFAAOCAQ8AMIIBCgKCAQEAxM772y77AFo1lYAJX+rk\nA30JhWAXtky+hyxIJROJ3OTHZPiOTMEXpArsYf6JbgNjLcFStxf3FaU3TFDpfL1S\ne/Z4RWJh3mS7Pnpc6i5Uxw/nc+0x1Au1B/cuFxTmhPRsGH8i0XsQD7FlKQadA8sq\nHIZ5ionwXMsu01JXUVSrTcwBEFQyIpRnN/VuBF+cTbIWP3MIMuDOqp1q7daotRgZne9e0M7EU52TivlzPZNifzi3VkrdbyF+8bfzTP4aUBJ8VwpKUqPU+f39lC0zve/ds\nCwIDAQAB\n-----END PUBLIC KEY-----\n",
"microtenantName": "Default"
}
]
}
A successful response returns code 200. To learn more, see [API Response Codes and Error Messages](/zpa/api-response-codes-and-error-messages).
Getting Details for a Particular Browser Access Certificate
This API is deprecated and will not be supported after January 27, 2023. To learn more, see [Getting Details for a Particular Certificate](#getCert).
To get details of a certificate:
- Send a `GET` request to the following endpoint: `/mgmtconfig/v1/admin/customers/{customerId}/clientlessCertificate/{certificateId}`.
- Use the following values in the request endpoint:
- `customerId`: The ZPA tenant ID of the customer.
- `certificateId`: The ID of the desired certificate.
For example: `/mgmtconfig/v1/admin/customers/72057615512764416/clientlessCertificate/72057615512764448`.
- [View an example response](#Viewanexampleresponse2)
[]{
"id": "72057615512764448",
"modifiedTime": "1559710128",
"creationTime": "1559691154",
"modifiedBy": "72057615512764423",
"name": "Wild Card Cert",
"description": "Wild%20Card%20Cert",
"cName": "*.lanuk.com",
"validFromInEpochSec": "1559667671",
"validToInEpochSec": "1602867671",
"certificate": "-----BEGIN CERTIFICATE-----\nMIIEcDCCAlgCCQDLbbOJT3D49TANBgkqhkiG9w0BAQsFADCBhzELMAkGA1UEBhMC\nVVMxEzARBgNVBAgMCkNhbGlmb3JuaWExETAPBgNVBAcMCFNhbiBK\n-----END CERTIFICATE-----\n",
"issuedTo": "CN=*.lanuk.com,O=Lanuk Inc,ST=CA,C=USA,L=San Jose,OU=Lanuk Inc",
"issuedBy": "1.2.840.113549.1.9.1=#161063657274407a7363616c65722e636f6d,CN=Certgen,OU=QA,O=Zscaler,L=San Jose,ST=California,C=US",
"serialNo": "14658569764485527797",
"publicKey": "-----BEGIN PUBLIC KEY-----\nMIIBIjANBgkqhkiG9w0BAQEFAAOCAQ8AMIIBCgKCAQEAvuhylAGQ916SLxlEXt+n\nn2gsKuNTK6VO58utz8Qcz+nyrs9uLSWcJV+UUuePnOXIh/xNENKLrv\n-----END PUBLIC KEY-----\n",
"san": [
"mail.lanuk.com",
"hr.lanuk.com",
"rdp.lanuk.com"
]
}
A successful response returns code 200. To learn more, see [API Response Codes and Error Messages](/zpa/api-response-codes-and-error-messages).
[]Getting Details for a Particular Certificate
To get details of a certificate:
- Send a `GET` request to the following endpoint: `/mgmtconfig/v1/admin/customers/{customerId}/certificate/{certificateId}?microtenantId={microtenantId}`.
- Provide the following values in the request endpoint:
- `customerId`: The ZPA tenant ID of the customer.
- `certificateId`: The ID of the desired certificate.
- `microtenantId`: The unique identifier of the Microtenant. If you are within a Microtenant, you must pass the `microtenantId` field when making an API call to retrieve data from that Microtenant. The `microtenantId` can be obtained from the API Keys page, or can be obtained programmatically using the ZPA cloud service API. Access to certain operations is limited when you are within a Microtenant. If you are within the Default Microtenant, pass `microtenantId` as `0` when making requests to retrieve data from the Default Microtenant. If the `microtenantId` is not passed in the request when creating or updating a resource, then the resource is created or updated in the Default Microtenant. To learn more, see [Configuring Microtenants Using API](/zpa/configuring-microtenants-using-api).
For example: `/mgmtconfig/v1/admin/customers/144118148382064640/certificate/144118148382064931?microtenantId=0`.
- [View an example response](#getCertExample)
[]{
"id":"144118148382064931",
"modifiedTime":"1648916882",
"creationTime":"1532110078",
"modifiedBy":"72057594037929181",
"name":"ADMIN",
"description":"desc",
"cName":"ak",
"microtenantName":"Default",
"validFromInEpochSec":"1530614700",
"validToInEpochSec":"1846233900",
"certificate":"-----BEGIN CERTIFICATE-----\nMIIDsjCCApqgAwIBAgIBATANBgkqhkiG9w0BAQUFADBhMQswCQYDVQQGEwJJTjEL\nMAkGA1UECBMCSU4xCzAJBgNVBAcTAklOMQswCQYDVQQKEwJhazELMAkGA1UECxMC\nYWsxCzAJBgNVBAMTAmFrMREwDwYJKoZIhvcNAQkBFgJhazAeFw0xODA3MDMxMDQ1\nMDBaFw0yODA3MDMxMDQ1MDBaMGExCzAJBgNVBAYTAklOMQswCQYDVQQIEwJJTjEL\nMAkGA1UEBxMCSU4xCzAJBgNVBAoTAmFrMQswCQYDVQQLEwJhazELMAkGA1UEAxMC\nYWsxETAPBgkqhkiG9w0BCQEWAmFrMIIBIjANBgkqhkiG9w0BAQEFAAOCAQ8AMIIB\nCgKCAQEAxEhVOulm9GV4dqoFNZz7Sl5hoNw+QidywF2Dgmps/oXH4gsQLU66hYeY\ncqpWk3TDiDRY8l9tHWQI4m5wkbozrg20VJN2NR/R/iV233ckqd0DNOaxgQZsD2C0\nagB2ste7eRcrdB24pWndYVRYYvihZK46E2VutgSyoNy4z0ZMeaKTCZ413UeyRg3t\nXdHCwYlsSv+A+awST4TnKApoSZ9LFG2ptYkYerTtj9PVF/IB++S1EuhOK1Tm2SKA\ndkRLN43J2Usrc+9W+oGwgFTMRa7qDIzzOjzsdWfgGGsPqU4TaranQX5Y1N+029IB\n2nSdQfnbHXDjcWDS5RG0ImDAPGayxQIDAQABo3UwczAPBgNVHRMBAf8EBTADAQH/\nMB0GA1UdDgQWBBSdeL+k+Tf9A4gORX2HY0BXFepSyTAOBgNVHQ8BAf8EBAMCAZ4w\nEQYJYIZIAYb4QgEBBAQDAgAHMB4GCWCGSAGG+EIBDQQRFg94Y2EgY2VydGlmaWNh\ndGUwDQYJKoZIhvcNAQEFBQADggEBAHbEWY2KKd+eHlVQ6lCjI/vzl9c8+2ARNXPT\nI2vb4MKUjo7kaU8NLlJhatZH1cxNvcoElDwwc0kb0uSeqiKC+aE5CBdLHPErGSjK\nlt08RWOm47cJXSHIiopWfqDhmLGMMRUaup1HRUdCrLYJe3kbm2ossz3yJf074Zo2\n6yJkUijq+zKJjZD5438IS+dbZv7Zg+H/P2xusOAyJCeceVUOtpunZveEQyWbGVzm\ncDXZgQA+b7ds3Gtgfg724JHNGdGqITzaYCTgmEbTBnJhLyZ7SnH/8IetfPAxwKPi\nMVaMj588I+mFwAiZR2YiMmvblVlPOqYlzU8M+2ACSpDu1qGZZyc=\n-----END CERTIFICATE-----\n",
"issuedTo":"1.2.840.113549.1.9.1=#1602616b,CN=ak,OU=ak,O=ak,L=IN,ST=IN,C=IN",
"issuedBy":"1.2.840.113549.1.9.1=#1602616b,CN=ak,OU=ak,O=ak,L=IN,ST=IN,C=IN",
"serialNo":"1",
"publicKey":"-----BEGIN PUBLIC KEY-----\nMIIBIjANBgkqhkiG9w0BAQEFAAOCAQ8AMIIBCgKCAQEAxEhVOulm9GV4dqoFNZz7\nSl5hoNw+QidywF2Dgmps/oXH4gsQLU66hYeYcqpWk3TDiDRY8l9tHWQI4m5wkboz\nrg20VJN2NR/R/iV233ckqd0DNOaxgQZsD2C0agB2ste7eRcrdB24pWndYVRYYvih\nZK46E2VutgSyoNy4z0ZMeaKTCZ413UeyRg3tXdHCwYlsSv+A+awST4TnKApoSZ9L\nFG2ptYkYerTtj9PVF/IB++S1EuhOK1Tm2SKAdkRLN43J2Usrc+9W+oGwgFTMRa7q\nDIzzOjzsdWfgGGsPqU4TaranQX5Y1N+029IB2nSdQfnbHXDjcWDS5RG0ImDAPGay\nxQIDAQAB\n-----END PUBLIC KEY-----\n"
}
A successful response returns code 200. To learn more, see [API Response Codes and Error Messages](/zpa/api-response-codes-and-error-messages).
Creating a Certificate
To create a certificate:
- Send a `POST` request to the following endpoint: `/mgmtconfig/v1/admin/customers/{customerId}/certificate?microtenantId={microtenantId}`.
-
Provide the following values in the request endpoint:
- `customerId`: The ZPA tenant ID of the customer.
- `microtenantId`: The unique identifier of the Microtenant. If you are within a Microtenant, you must pass the `microtenantId` field when making an API call to retrieve data from that Microtenant. The `microtenantId` can be obtained from the API Keys page, or can be obtained programmatically using the ZPA cloud service API. Access to certain operations is limited when you are within a Microtenant. If you are within the Default Microtenant, pass `microtenantId` as `0` when making requests to retrieve data from the Default Microtenant. If the `microtenantId` is not passed in the request when creating or updating a resource, then the resource is created or updated in the Default Microtenant. To learn more, see [Configuring Microtenants Using API](/zpa/configuring-microtenants-using-api).
For example: `/mgmtconfig/v1/admin/customers/72057594038056531/certificate?microtenantId=0`.
- Include the request headers to provide information about the request context:
- Content-Type: `application/json`
- Authorization: `Bearer <access_token>`
- Use the entire JSON payload to create a certificate and provide the following:
- `certBlob`: The content of the certificate.
The `certBlob` field must be in string format and must include the certificate and the private key (in PEM format) in the JSON payload. The certificate must be in X.509 certificate format and the private key must be in PKCS #1 or PKCS #8 format.
- `name`: The name of the certificate.
- [View the entire JSON payload](#entireJson)
[]{
"certBlob": "string",
"description": "string",
"id": 0,
"name": "string"
}
- [View the minimum criteria JSON payload](#minimumCriteriaJson)
[]{
"certBlob": "string",
"name": "string"
}
- [View the sample JSON payload](#postSampleJson)
[]{
"certBlob": "-----BEGIN CERTIFICATE-----
MIICTjCCAbegAwIBAgIBADANBgkqhkiG9w0BAQ0FADBEMQswCQYDVQQGEwJ1czEL
MAkGA1UECAwCRkwxFTATBgNVBAoMDFRlc3RfWnNjYWxlcjERMA8GA1UEAwwIdGVz
dC5jb20wHhcNMjIwNzE1MTQxNjM0WhcNMjMwNzE1MTQxNjM0WjBEMQswCQYDVQQG
EwJ1czELMAkGA1UECAwCRkwxFTATBgNVBAoMDFRlc3RfWnNjYWxlcjERMA8GA1UE
AwwIdGVzdC5jb20wgZ8wDQYJKoZIhvcNAQEBBQADgY0AMIGJAoGBANCw2uSsu/+t
bkjNvXiTLBrrjLsLkdddwlbxSB3JUpHM5wjMA4huCx0fMVm+qEq1KuH6ae3NsDGL
2hbabXQ1Yq8z3xnjO3bLVkjrJpc1o1m7x59nRrNctoOi4UwCXR4AcHOg3WlDb0g7
ynaPaPS48k1GcYi9/31MkZP81flqAD3TAgMBAAGjUDBOMB0GA1UdDgQWBBRRHuE2
AX8wWGI3N+VV7wsoc7uATTAfBgNVHSMEGDAWgBRRHuE2AX8wWGI3N+VV7wsoc7uA
TTAMBgNVHRMEBTADAQH/MA0GCSqGSIb3DQEBDQUAA4GBAEBF6CI5uBCAfulyk39U
pMHqGg7sj8BBaTBIVXFkDGiaB9zKVKH68IExv1g9OI2Rh5VF4bVaK0XnwIuuF7AO
TV9G4cMbXWyG6Kk9lGSa+jTyz43PkRfiHkXqjpr9/ZSjgbnKSc9sTLdPfVf5XFJM
FCKdpw0TcbNhybAcuZIU48Nl
-----END CERTIFICATE---
----BEGIN RSA PRIVATE KEY----
MIICXQIBAAKBgQDQsNrkrLv/rW5Izb14kywa64y7C5HXXcJW8UgdyVKRzOcIzAOI
bgsdHzFZvqhKtSrh+mntzbAxi9oW2m10NWKvM98Z4zt2y1ZI6yaXNaNZu8efZ0az
XLaDouFMAl0eAHBzoN1pQ29IO8p2j2j0uPJNRnGIvf99TJGT/NX5agA90wIDAQAB
AoGAawjaLAEAJ2F/N+316LqrG1+GfYSwl2IqQ8daspRIOil6sYNZqIawQo52FE56
KF8FEIQMAoDFhpPxFlmPW9PpuX9QsksimcnKATaB5m0jxzi9yZqCTVd1VL47dIsN
sfKwPePLd0AcP2szuqSZ009CQE/UPFIkDAmLzNspoXWs1PkCQQDuDAkD1S2cIapT
e+eZUj/z59cc9pIYtIqmu1T/0o7O/A82KBrX5VdD4SqqO6BOS2txwzh5Te3GL6+h
KENLAoB3AkEA4G4Kk07SPaO++tXLKlUqOkKjAdi16yVBp0u6KyvcWVa3LFB93S64
Hk+BduCLfuA/+Qk32xnmXedv8kC2cEiAhQJBANHQQdHi/8Rx19Klj0iQOlYcrnmU
ysiDuQGkdBLX34+Ik0/EoYRRXE00FYrd6zmXOCiZTRl+GmlodoCxID7pAZkCQQC+
FfX3FoeTlaEoKvRNAp0lg1M1OSu74m5dGBKyhg+3y26Rpgs0z2E6qvRoj38XEzCb
6WbZuHIZjvCOKqlbKM1RAkB1BxmDgJWlubGuarb8v0zg8iolA0vt1vTGtTfyW47b
lF/rrs19yfY4N+VuvVeJejL8vSL30SU/iIwiYq5OgM9p
----END RSA PRIVATE KEY----",
"description": "Sample Public_API_Upload_Cert",
"name": "Sample Public_API_Upload_Cert"
}
- [View the example response](#postExampleResponse)
[]{
"id":"73194682334586516",
"creationTime":"1657908708",
"modifiedBy":"72057594038056530",
"name":"New Example Public_API_Upload_Cert",
"description":"New ExamplePublic_API_Upload_Cert",
"cName":"test.com",
"microtenantName":"Default",
"validFromInEpochSec":"1657894594",
"validToInEpochSec":"1689430594",
"certificate":"----BEGIN CERTIFICATE----\nMIICTjCCAbegAwI\n----END CERTIFICATE----\n",
"issuedTo":"CN=test.com,O=Test_Zscaler,ST=FL,C=us",
"issuedBy":"CN=test.com,O=Test_Zscaler,ST=FL,C=us",
"serialNo":"0",
"publicKey":"----BEGIN PUBLIC KEY----\nMIGfMA0GCB\n----END PUBLIC KEY----\n",
"san":[
"test.com"
]
}
A successful response returns code 200. To learn more, see [API Response Codes and Error Messages](/zpa/api-response-codes-and-error-messages).
Updating a Certificate
To update the name or description of a certificate:
- Send a `PUT` request to the following endpoint: `/mgmtconfig/v1/admin/customers/{customerId}/certificate/{certificateId}?microtenantId={microtenantId}`.
-
Provide the following in the request endpoint:
- `customerId`: The ZPA tenant ID of the customer.
- `microtenantId`: The unique identifier of the Microtenant. If you are within a Microtenant, you must pass the `microtenantId` field when making an API call to retrieve data from that Microtenant. The `microtenantId` can be obtained from the API Keys page, or can be obtained programmatically using the ZPA cloud service API. Access to certain operations is limited when you are within a Microtenant. If you are within the Default Microtenant, pass `microtenantId` as `0` when making requests to retrieve data from the Default Microtenant. If the `microtenantId` is not passed in the request when creating or updating a resource, then the resource is created or updated in the Default Microtenant. To learn more, see [Configuring Microtenants Using API](/zpa/configuring-microtenants-using-api).
For example: `/mgmtconfig/v1/admin/customers/72057594038056531/certificate/144118148382064931?microtenantId=0`.
- Include the request headers to provide information about the request context:
- Content-Type: `application/json`
- Authorization: `Bearer <access_token>`
- Use the entire JSON payload to create a certificate and provide the following:
- `name`: The name of the certificate.
- `description`: The description of the certificate.
- [View the JSON payload](#updateCertJson)
[]
`{
"name":"<example certificate name>",
"description":"<example certificate description>"
}`
- [View the sample JSON payload](#updateCertSampleJson)
[]
`{
"name":"test name updated",
"description":"updated description"
}`
A successful response returns code 204, meaning the certificate is deleted. To learn more, see [API Response Codes and Error Messages](/zpa/api-response-codes-and-error-messages).
Adding Field Descriptions
The following table includes descriptions of available fields you can use for the certificate use cases:
[](/zpa/about-api-keys)[](/zpa/configuring-microtenants-using-api)
| Field | Description | Required | Value |
| ----- | ----------- | -------- | ----- |
| certBlob | The content of the certificate | Yes | String |
| description | The description of the certificate | No | String |
| id | The unique identifier of the certificate | No | Integer |
| name | The name of the certificate | Yes | String |
| customerId | The unique identifier of the ZPA tenant | Yes | Integer |
| page | Specifies the page number | No | Integer |
| pagesize | Specifies the page size | No | Integer |
| search | The search string used to support search by features and fields for the API | No | String |
| microtenantId | The unique identifier of the Microtenant for the ZPA tenant. If you are within a Microtenant, you must pass the `microtenantId` field when making an API call to retrieve data from that Microtenant. The `microtenantId` can be obtained from the API Keys page, or can be obtained programmatically using the ZPA cloud service API. Access to certain operations is limited when you are within a Microtenant. If you are within the Default Microtenant, pass `microtenantId` as `0` when making requests to retrieve data from the Default Microtenant. Pass `microtenantId` as null to retrieve data from all Microtenants associated with the tenant. If the `microtenantId` is not passed in the request when creating or updating a resource, then the resource is created or updated in the Default Microtenant. To learn more, see Configuring Microtenants Using API. | No | Integer |
Deleting a Certificate
To delete a certificate:
- Send a `DELETE` request to the following endpoint: `/mgmtconfig/v1/admin/customers/{customerId}/certificate/{certificateId}?microtenantId={microtenantId}`.
- Provide the following in the request endpoint:
- `customerId`: The ZPA tenant ID of the customer.
- `certificateId`: The unique identifier of the certificate.
- `microtenantId`: The unique identifier of the Microtenant. If you are within a Microtenant, you must pass the `microtenantId` field when making an API call to retrieve data from that Microtenant. The `microtenantId` can be obtained from the API Keys page, or can be obtained programmatically using the ZPA cloud service API. Access to certain operations is limited when you are within a Microtenant. If you are within the Default Microtenant, pass `microtenantId` as `0` when making requests to retrieve data from the Default Microtenant. If the `microtenantId` is not passed in the request when creating or updating a resource, then the resource is created or updated in the Default Microtenant. To learn more, see [Configuring Microtenants Using API](/zpa/configuring-microtenants-using-api).
For example: `/mgmtconfig/v1/admin/customers/72057594038056531/certificate/73194682334586516?microtenantId=0`.
A successful response returns code 204, meaning the certificate is deleted. To learn more, see [API Response Codes and Error Messages](/zpa/api-response-codes-and-error-messages).