# Configuring Privileged Credentials Using API
Source: https://help.zscaler.com/zpa/configuring-privileged-credentials-using-api
PDF: https://help.zscaler.com/pdf/com/en/1485931.pdf

This article provides information on managing Zscaler Private Access (ZPA) privileged credentials using APIs. All APIs are rate limited. To learn more, see [Understanding Rate Limiting](/zpa/understanding-rate-limiting).
Creating a New Privileged Credential
To create a new privileged credential:
- Send a `POST` request to the following endpoint in the Privileged Credential Controller: `/mgmtconfig/v1/admin/customers/{customerId}/credential`.
- Provide the `customerId`, the ZPA tenant ID of the customer, in the request endpoint.
For example: `mgmtconfig/v1/admin/customers/145256180497776640/credential`.
- Include the request headers to specify the following parameters about the request context:
- Content-Type: `application/json`
- Authorization: `Bearer <access_token>`
- Use the following JSON payloads and provide the following information:
- `credentialType`: The privileged credential type. The following values are supported:
- `USERNAME_PASSWORD`: Indicates if you are using RDP, SSH, or VNC.
- `SSH_KEY`: Indicates if you are using an SSH protocol.
- `PASSWORD`: Indicates if you are using a VNC option.
- `name`: The name of the privileged credential.
- `password`: The password of the privileged credential.
- `userName`: The user name of the privileged credential.
If you are using `USERNAME_PASSWORD` as the `credentialType`, refer to the following JSON payloads and example response:
- [View the JSON payload](#postPayloadRdp)
[]{
"credentialType": "USERNAME_PASSWORD",
"name": "string",
"password": "string",
"userName": "string"
}
- [View an example JSON payload](#postExamplePayloadRdp)
[]{
"name": "test-credentials",
"credentialType": "USERNAME_PASSWORD",
"userName": "test",
"password": "test"
}
- [View an example response](#postResponseRdp)
[]{
"id": "11410",
"modifiedTime": "1684413013",
"creationTime": "1684413013",
"modifiedBy": "145256180497777000",
"name": "test-credentials",
"userName": "test",
"credentialType": "USERNAME_PASSWORD",
"lastCredentialResetTime": "1684413013"
}
If you are using `SSH_KEY` as the `credentialType`, refer to the following JSON payloads and example response:
- [View the JSON payload](#postPayloadSsh)
[]{
"credentialType": "SSH_KEY",
"name": "string",
"userName": "string"
"privateKey": "string"
}
- [View an example JSON payload](#postExamplePayloadSsh)
[]{
"name": "test-credential3",
"credentialType": "SSH_KEY",
"userName": "test",
"privateKey": "-----BEGIN PRIVATE KEY-----\nMIIEvQIBADANBgkqhkiG9w0BAQEFAASCBKcwggSjAgEAAoIBAQCiwdgEapnnlNMA\n0gDC3DGNljrp58H7G/pPkZDnQ0NawfuwNN2VuIRnn/MIQuKnKgt36eOIV0aC6V9a\nA1cVr7W9Jy/vU73b6NoQXH/dpxQBzHp3d/qyx1k619wJcacP/cx4gUCN3mrnoFaz\nvj0y21pPP+/54dEJw1JXsEcE/aNJJ2KmQsxQac8ckN0vYKQBAAlZPd7l99VC9nW2\niece8yPHT5UiingDtOW+WOyD7gUE/QZSiKzAcRTVYq9x8CJPo/Q/EvvbWJp0zt0X\nMBjzJ2u4Rz+aaI5LVo+ERbeoS8jiodQh+OK5tFnozl21PuVQpr6BcbTId9KNhK4D\nlpJN8R1HAgMBAAECggEAGRws9ql3qynjz+mWYnnUT1LRLgsqe1JasPH1WCiheJwa\n95mAYjwAeXhM54ZiL4YmFM8J4pwMbeARbPK8+cSNFmy4UYUq8oWfNwz+UTUYuhpQ\n/qONEw38bz6kXPSi4K24YRMX4YtiFPBA0CRWjsUWzsk/fd7gAFCZIJw6qMN08LEa\nknKCN993KbQWb0q7QPMmn9dUpPVD4qy7BcnC3l6GLEW153VCDaZD4ghIFx34OCYN\n6L4sePmU7Io+brzIR5iVmkfwyFuvnMgUBSPRnHTPwxVW9+ZwwgGK417WR4gWq3hp\nh4XTaB9cbUINsTGETk8LDIN4PBhMxb+GnD2tLYhvEQKBgQDhuc57NQZ7H8/6K4wz\nv/ZOxGjeX2J1Pu3kH4iXZYJuj8IYLmk7VF9I6TNLU7eZKtVWxyipjPQu9kVvqpi+\nmErbghz4bB74fGHKaen+qKCgsuvefvp+HyrjJyenFQQwO9y2QEJHHf8fF8jFhtv1\nYEPVb4qj0yPHJlpj8OdDH0FAjwKBgQC4lgno4m2oRRVY6m5DPrlGpWRLidoYPO9V\nV8oGBIBD63jfvnMUjoNTP4h4xOjI6/KDsncmCUehIKKuRWYmaM/jXoHso8z9YqWd\nfsRZbfzZjoHWZ2Bf0I8agN/w3dwpsIqA2us48QnoYzoIAkAPdyz41F1Jbjz0/pcg\nYOnCmzBDyQKBgQDBuMpJmS9vudSvOnJ/8057OTtbJXeFcjWOI7YBYN/47S3BvQsZ\nHQcNtv4LttSKAmXHrPLr2Im0SC09cabXZDJSgy9D0N8fmPgAVLe6k5QPdp7RfB6U\n4UDYZEE2tuW6U5XPYATBri/Gyo3HYD8kLrLo2WqdwNYi03qd7SE8zPUeZwKBgE0Z\nbn41xbPZVzdShEfWNTFK9/+NTul82kL9bkbhLmowOsbKF+toM3ZcPTakmM8DrsJP\nkvDyQ1cL+KduGWLFuL+xw/cB3CeiQqbsQjtQc6KzoYvaliivRna9icxj/wfy04dK\n6aFZHNhSSfT6a6OKFeDBY02+m/uBM8K0eC9u/tPxAoGAQ6Gx0fgst71dyYd9P5aK\nuTDIr36TpKdAVHdIj/7BnE5ZHf8g0vbhuSOs+mudQADd1Rypc/9n+o3+uUL/P93x\nRLCfjisejv/EgRhGTjmG+LdlaV6zyCa4fqDbzNT3fkvOiJFmbu4JbutMaaPie50O\nmwV0h3cHDxx/LL8LPLvSY4s=\n-----END PRIVATE KEY-----"
- [View an example response](#PostResponseSsh)
[]{
"id": "11414",
"modifiedTime": "1684413491",
"creationTime": "1684413491",
"modifiedBy": "145256180497777000",
"name": "test-credential3",
"userName": "test",
"credentialType": "SSH_KEY",
"lastCredentialResetTime": "1684413491"
}
If you are using `PASSWORD` as the `credentialType`, refer to the following JSON payloads and example response:
- [View the JSON payload](#PostPayloadPassword)
[]{
"credentialType": "PASSWORD",
"name": "string",
"password": "string"
}
- [View an example JSON payload](#PostExamplePayloadPassword)
[]{
"name": "test-credential4",
"credentialType": "PASSWORD",
"password": "test",
}
- [View an example response](#PostResponsePassword)
[]{
"id": "11416",
"creationTime": "1684413909",
"modifiedBy": "72057594038624153",
"name": "test-credential4",
"credentialType": "PASSWORD",
"lastCredentialResetTime": "1684413909"
}
A successful response returns code 201. To learn more, see [API Response Codes and Error Messages](/zpa/api-response-codes-and-error-messages).
Microtenant Support
To create a new privileged console within a Microtenant:
- Send a `POST` request to the endpoint `/mgmtconfig/v1/admin/customers/{customerId}/credential?microtenantId={microtenantId}` in the Privileged Credential Controller.
- Provide the following in the request endpoint:
- `customerId`: The ZPA tenant ID of the customer.
- `microtenantId`: The unique identifier of the Microtenant for the ZPA tenant. To learn more, see [Configuring Microtenants Using API](/zpa/configuring-microtenants-using-api).
For example: `/mgmtconfig/v1/admin/customers/145256180497776640/credential?microtenantId=145260601092866314`.
- Include the request headers to specify the following parameters about the request context:
- Content-Type: `application/json`
- Authorization: `Bearer <access_token>`
- Use the following JSON payloads and provide the following information:
- `credentialType`: The privileged credential type. The following values are supported:
- `USERNAME_PASSWORD`: Indicates if you are using RDP, SSH, or VNC.
- `SSH_KEY`: Indicates if you are using an SSH protocol.
- `PASSWORD`: Indicates if you are using a VNC option.
- `name`: The name of the privileged credential.
- `password`: The password of the privileged credential.
- `userName`: The user name of the privileged credential.
If you are using `USERNAME_PASSWORD` as the `credentialType`, refer to the following JSON payloads and example response:
- [View the JSON payload](#postPayloadRdpMicrotenant)
[]{
"credentialType": "USERNAME_PASSWORD",
"name": "string",
"password": "string",
"userName": "string"
}
- [View an example JSON payload](#postExamplePayloadRdpMicrotenant)
[]{
"name": "test-credentials",
"credentialType": "USERNAME_PASSWORD",
"userName": "test",
"password": "test"
}
- [View an example response](#postResponseRdpMicrotenant)
[]
`{
"id": "11410",
"modifiedTime": "1684413013",
"creationTime": "1684413013",
"modifiedBy": "145256180497777000",
"name": "test-credentials",
"userName": "test",
"credentialType": "USERNAME_PASSWORD",
"lastCredentialResetTime": "1684413013",
"microtenantId": "145260601092866314",
"microtenantName": "Scope C"
}
`
If you are using `SSH_KEY` as the `credentialType`, refer to the following JSON payloads and example response:
- [View the JSON payload](#postPayloadSshMicrotenant)
[]{
"credentialType": "SSH_KEY",
"name": "string",
"userName": "string"
"privateKey": "string"
}
- [View an example JSON payload](#postExamplePayloadSshMicrotenant)
[]{
"name": "test-credential3",
"credentialType": "SSH_KEY",
"userName": "test",
"privateKey": "-----BEGIN PRIVATE KEY-----\nMIIEvQIBADANBgkqhkiG9w0BAQEFAASCBKcwggSjAgEAAoIBAQCiwdgEapnnlNMA\n0gDC3DGNljrp58H7G/pPkZDnQ0NawfuwNN2VuIRnn/MIQuKnKgt36eOIV0aC6V9a\nA1cVr7W9Jy/vU73b6NoQXH/dpxQBzHp3d/qyx1k619wJcacP/cx4gUCN3mrnoFaz\nvj0y21pPP+/54dEJw1JXsEcE/aNJJ2KmQsxQac8ckN0vYKQBAAlZPd7l99VC9nW2\niece8yPHT5UiingDtOW+WOyD7gUE/QZSiKzAcRTVYq9x8CJPo/Q/EvvbWJp0zt0X\nMBjzJ2u4Rz+aaI5LVo+ERbeoS8jiodQh+OK5tFnozl21PuVQpr6BcbTId9KNhK4D\nlpJN8R1HAgMBAAECggEAGRws9ql3qynjz+mWYnnUT1LRLgsqe1JasPH1WCiheJwa\n95mAYjwAeXhM54ZiL4YmFM8J4pwMbeARbPK8+cSNFmy4UYUq8oWfNwz+UTUYuhpQ\n/qONEw38bz6kXPSi4K24YRMX4YtiFPBA0CRWjsUWzsk/fd7gAFCZIJw6qMN08LEa\nknKCN993KbQWb0q7QPMmn9dUpPVD4qy7BcnC3l6GLEW153VCDaZD4ghIFx34OCYN\n6L4sePmU7Io+brzIR5iVmkfwyFuvnMgUBSPRnHTPwxVW9+ZwwgGK417WR4gWq3hp\nh4XTaB9cbUINsTGETk8LDIN4PBhMxb+GnD2tLYhvEQKBgQDhuc57NQZ7H8/6K4wz\nv/ZOxGjeX2J1Pu3kH4iXZYJuj8IYLmk7VF9I6TNLU7eZKtVWxyipjPQu9kVvqpi+\nmErbghz4bB74fGHKaen+qKCgsuvefvp+HyrjJyenFQQwO9y2QEJHHf8fF8jFhtv1\nYEPVb4qj0yPHJlpj8OdDH0FAjwKBgQC4lgno4m2oRRVY6m5DPrlGpWRLidoYPO9V\nV8oGBIBD63jfvnMUjoNTP4h4xOjI6/KDsncmCUehIKKuRWYmaM/jXoHso8z9YqWd\nfsRZbfzZjoHWZ2Bf0I8agN/w3dwpsIqA2us48QnoYzoIAkAPdyz41F1Jbjz0/pcg\nYOnCmzBDyQKBgQDBuMpJmS9vudSvOnJ/8057OTtbJXeFcjWOI7YBYN/47S3BvQsZ\nHQcNtv4LttSKAmXHrPLr2Im0SC09cabXZDJSgy9D0N8fmPgAVLe6k5QPdp7RfB6U\n4UDYZEE2tuW6U5XPYATBri/Gyo3HYD8kLrLo2WqdwNYi03qd7SE8zPUeZwKBgE0Z\nbn41xbPZVzdShEfWNTFK9/+NTul82kL9bkbhLmowOsbKF+toM3ZcPTakmM8DrsJP\nkvDyQ1cL+KduGWLFuL+xw/cB3CeiQqbsQjtQc6KzoYvaliivRna9icxj/wfy04dK\n6aFZHNhSSfT6a6OKFeDBY02+m/uBM8K0eC9u/tPxAoGAQ6Gx0fgst71dyYd9P5aK\nuTDIr36TpKdAVHdIj/7BnE5ZHf8g0vbhuSOs+mudQADd1Rypc/9n+o3+uUL/P93x\nRLCfjisejv/EgRhGTjmG+LdlaV6zyCa4fqDbzNT3fkvOiJFmbu4JbutMaaPie50O\nmwV0h3cHDxx/LL8LPLvSY4s=\n-----END PRIVATE KEY-----"
- [View an example response](#PostResponseSshMicrotenant)
[]
`{
"id": "11414",
"modifiedTime": "1684413491",
"creationTime": "1684413491",
"modifiedBy": "145256180497777000",
"name": "test-credential3",
"userName": "test",
"credentialType": "SSH_KEY",
"lastCredentialResetTime": "1684413491",
"microtenantId": "145260601092866314",
"microtenantName": "Scope C"
}`
If you are using `PASSWORD` as the `credentialType`, refer to the following JSON payloads and example response:
- [View the JSON payload](#PostPayloadPasswordMicrotenant)
[]{
"credentialType": "PASSWORD",
"name": "string",
"password": "string"
}
- [View an example JSON payload](#PostExamplePayloadPasswordMicrotenant)
[]{
"name": "test-credential4",
"credentialType": "PASSWORD",
"password": "test",
}
- [View an example response](#PostResponsePasswordMicrotenant)
[]
`{
"id": "11416",
"creationTime": "1684413909",
"modifiedBy": "72057594038624153",
"name": "test-credential4",
"credentialType": "PASSWORD",
"lastCredentialResetTime": "1684413909",
"microtenantId": "145260601092866314",
"microtenantName": "Scope C"
}`
A successful response returns code 201. To learn more, see [API Response Codes and Error Messages](/zpa/api-response-codes-and-error-messages).
Getting Details of All Privileged Credentials
To get all privileged credentials:
- Send a `GET` request to the following endpoint in the Privileged Credential Controller: `/mgmtconfig/v1/admin/customers/{customerId}/credential`.
- Provide the `customerId`, the ZPA tenant ID of the customer, in the request endpoint.
For example: `mgmtconfig/v1/admin/customers/72057594037927936/credential`.
- [View an example response](#getCredentials)
[]{
"totalPages": "1",
"totalCount": "6",
"list": [
{
"id": "47",
"creationTime": "1668431272",
"modifiedBy": "72057594038052745",
"name": "test",
"userName": "test123",
"credentialType": "SSH_KEY",
"lastCredentialResetTime": "1668431272"
},
{
"id": "259",
"modifiedTime": "1681193539",
"creationTime": "1681193467",
"modifiedBy": "72057594038071302",
"name": "test43782389823",
"description": "8h5KXKVxFOi92gpwy0RUbNGqa",
"userDomain": "yaYDDsmnke7sclsshifGnfuua.com",
"userName": "admin@lE54dmi5ytV2JsPejpxTP6jzy.com",
"credentialType": "USERNAME_PASSWORD",
"lastCredentialResetTime": "1681193539"
},
{
"id": "80",
"modifiedTime": "1681112288",
"creationTime": "1671722598",
"modifiedBy": "72057594038071302",
"name": "test8&^%$",
"userName": "simha",
"credentialType": "SSH_KEY",
"lastCredentialResetTime": "1671722598"
},
{
"id": "20",
"modifiedTime": "1668433318",
"creationTime": "1664475368",
"modifiedBy": "72057594038052745",
"name": "testCred",
"userName": "test123",
"credentialType": "USERNAME_PASSWORD",
"lastCredentialResetTime": "1668433318"
},
{
"id": "113",
"creationTime": "1676338296",
"modifiedBy": "72057594038006701",
"name": "testCred22",
"userName": "test",
"credentialType": "SSH_KEY",
"lastCredentialResetTime": "1676338296"
},
{
"id": "57",
"creationTime": "1669048095",
"modifiedBy": "72057594038072642",
"name": "trial01",
"userName": "Zscaler",
"credentialType": "USERNAME_PASSWORD",
"lastCredentialResetTime": "1669048095"
}
]
}
A successful response returns code 200. To learn more, see [API Response Codes and Error Messages](/zpa/api-response-codes-and-error-messages).
This API supports pagination and Microtenants. To get a paginated response and search by Microtenant:
- Send a `GET` request to the endpoint `/mgmtconfig/v1/admin/customers/{customerId}/credential?page=1&pagesize=20&sortBy=status&sortdir=ASCµtenantId={microtenantId}&search={searchString}` in the Privileged Credential Controller.
- Provide the following in the request endpoint:
- `customerId`: The ZPA tenant ID of the customer.
- Valid page and page size values. If not provided, the default page size is 20, and the maximum page size is 500.
- `microtenantId`: The unique identifier of the Microtenant for the ZPA tenant. To learn more, see [Configuring Microtenants Using API](/zpa/configuring-microtenants-using-api).
- Valid search string values. The search string values are in the format `filter%20Operator%20filterValue`. The supported value for `filter` is `ownershipType`. The supported value for `Operator` is `EQ` (equals). The supported values for `filterValue` are:
- `INHERITED`: The privileged credential is inherited by the Microtenant.
- `MICROTENANT_SPECIFIC`: The privileged credential is Microtenant-specific.
For example: `/mgmtconfig/v1/admin/customers/{customerId}/credential?page=1&pagesize=20&sortBy=status&sortdir=ASCµtenantId=145260601092866314&search=ownershipType%20EQ%20MICROTENANT_SPECIFIC'`.
- [View an example response](#getPagCredentials)
[]{
"totalPages": "1",
"totalCount": "4",
"list": [
{
"id": "453",
"creationTime": "1667515573",
"modifiedBy": "72057594038067446",
"name": "key size test",
"microtenantId": "145260601092866314",
"microtenantName": "Scope C",
"userName": "testkey",
"credentialType": "SSH_KEY",
"lastCredentialResetTime": "1667515573"
},
{
"id": "128",
"modifiedTime": "1667932422",
"creationTime": "1663696264",
"modifiedBy": "72057594038006701",
"name": "Test Credentials",
"microtenantId": "145260601092866314",
"microtenantName": "Scope C",
"userName": "test",
"credentialType": "USERNAME_PASSWORD",
"lastCredentialResetTime": "1667932422"
},
{
"id": "455",
"creationTime": "1667515783",
"modifiedBy": "72057594038067446",
"name": "Test Key Size 1",
"microtenantId": "145260601092866314",
"microtenantName": "Scope C",
"userName": "test-key-1",
"credentialType": "SSH_KEY",
"lastCredentialResetTime": "1667515783"
},
{
"id": "11262",
"creationTime": "1683125378",
"modifiedBy": "72057594038624153",
"name": "test-test-test-1",
"microtenantId": "145260601092866314",
"microtenantName": "Scope C",
"description": "test-test-test-1",
"userDomain": "zscaler.com",
"userName": "krishna",
"credentialType": "USERNAME_PASSWORD",
"lastCredentialResetTime": "1683125378"
}
]
}
If you use the ZPA API Portal or the Reference Guide to make your API calls, the search field string does not require any characters. For example, the search string `ownershipType%20EQ%20MICROTENANT_SPECIFIC` is `ownershipType EQ MICROTENANT_SPECIFIC`.
A successful response returns code 200. To learn more, see [API Response Codes and Error Messages](/zpa/api-response-codes-and-error-messages).
Getting Details of a Particular Privileged Credential
To get details of a particular privileged credential:
- Send a `GET` request to the following endpoint in the Privileged Credential Controller: `/mgmtconfig/v1/admin/customers/{customerId}/credential/{id}`.
- Provide the following in the request endpoint:
- `customerId`: The ZPA tenant ID of the customer.
- `id`: The ID of the privileged credential.
For example: `/mgmtconfig/v1/admin/customers/customers/145256180497776640/credential/11262`.
- [View an example response](#getCredential)
[]{
"id": "11262",
"creationTime": "1683125378",
"modifiedBy": "72057594038624153",
"name": "test-test-test-1",
"description": "test-test-test-1",
"userDomain": "zscaler.com",
"userName": "krishna",
"credentialType": "USERNAME_PASSWORD",
"lastCredentialResetTime": "1683125378"
}
A successful response returns code 200. To learn more, see [API Response Codes and Error Messages](/zpa/api-response-codes-and-error-messages).
To get details of a particular privileged credential within a Microtenant:
- Send a `GET` request to the following endpoint in the Privileged Credential Controller: `/mgmtconfig/v1/admin/customers/customers/145256180497776640/credential/{id}?microtenantId={microtenantId}`.
- Provide the following in the request endpoint:
- `customerId`: The ZPA tenant ID of the customer.
- `id`: The ID of the privileged credential.
- `microtenantId`: The unique identifier of the Microtenant for the ZPA tenant. To learn more, see [Configuring Microtenants Using API](/zpa/configuring-microtenants-using-api).
For example: `/mgmtconfig/v1/admin/customers/customers/145256180497776640/credential/11262?microtenantId=145260601092866314`.
- [View an example response](#getCredentialMicrotenant)
[]
`{
"id": "11262",
"creationTime": "1683125378",
"modifiedBy": "72057594038624153",
"name": "test-test-test-1",
"microtenantId": "145260601092866314",
"microtenantName": "Scope C",
"description": "test-test-test-1",
"userDomain": "zscaler.com",
"userName": "krishna",
"credentialType": "USERNAME_PASSWORD",
"lastCredentialResetTime": "1683125378"
}
`
A successful response returns code 200. To learn more, see [API Response Codes and Error Messages](/zpa/api-response-codes-and-error-messages).
Updating a Privileged Credential
To update a privileged credential:
- Send a `PUT` request to the following endpoint in the Privileged Credential Controller: `/mgmtconfig/v1/admin/customers/{customerId}/credential/{id}`.
- Provide the following in the request endpoint:
- `customerId`: The ZPA tenant ID of the customer.
- `id`: The ID of the privileged credential.
For example: `mgmtconfig/v1/admin/customers/145256180497776640/credential/11262`.
- Include the request headers to specify the following parameters about the request context:
- Content-Type: `application/json`
- Authorization: `Bearer <access_token>`
- Use the following JSON payload and provide the following information:
- `credentialType`: The privileged credential type. The supported values are:
- `USERNAME_PASSWORD`: Indicates if you are using RDP, SSH, or VNC.
- `SSH_KEY`: Indicates if you are using an SSH protocol.
- `PASSWORD`: Indicates if you are using a VNC option.
- `name`: The name of the privileged credential.
- `password`: The password of the privileged credential.
- `userName`: The user name of the privileged credential.
- [View the JSON payload](#putPayload)
[]{
"credentialType": "USERNAME_PASSWORD",
"name": "string",
"password": "string",
"userName": "string"
}
- [View an example JSON payload](#putExamplePayload)
[]{
"name": "test-credential4",
"credentialType": "PASSWORD",
"password": "test"
}
A successful response returns code 204, meaning the privileged credential was updated. To learn more, see [API Response Codes and Error Messages](/zpa/api-response-codes-and-error-messages).
This API supports Microtenants. To update a privileged credential within a Microtenant:
- Send a `PUT` request to the following endpoint in the Privileged Credential Controller: `/mgmtconfig/v1/admin/customers/{customerId}/credential/{id}?microtenantId={microtenantId}`.
- Provide the following in the request endpoint:
- `customerId`: The ZPA tenant ID of the customer.
- `id`: The ID of the privileged credential.
- `microtenantId`: The unique identifier of the Microtenant for the ZPA tenant. To learn more, see [Configuring Microtenants Using API](/zpa/configuring-microtenants-using-api).
For example: `mgmtconfig/v1/admin/customers/145256180497776640/credential/11262?microtenantId=145260601092866314`.
- Include the request headers to specify the following parameters about the request context:
- Content-Type: `application/json`
- Authorization: `Bearer <access_token>`
- Use the following JSON payload and provide the following information:
- `credentialType`: The privileged credential type. The supported values are:
- `USERNAME_PASSWORD`: Indicates if you are using RDP, SSH, or VNC.
- `SSH_KEY`: Indicates if you are using an SSH protocol.
- `PASSWORD`: Indicates if you are using a VNC option.
- `name`: The name of the privileged credential.
- `password`: The password of the privileged credential.
- `userName`: The user name of the privileged credential.
- [View the JSON payload](#putPayloadMicrotenant)
[]{
"credentialType": "USERNAME_PASSWORD",
"name": "string",
"password": "string",
"userName": "string"
}
- [View an example JSON payload](#putExamplePayloadMicrotenant)
[]{
"name": "test-credential4",
"credentialType": "PASSWORD",
"password": "test"
}
A successful response returns code 204, meaning the privileged credential was updated. To learn more, see [API Response Codes and Error Messages](/zpa/api-response-codes-and-error-messages).
Deleting a Privileged Credential
To delete a privileged credential:
- Send a `DELETE` request to the following endpoint in the Privileged Credential Controller: `/mgmtconfig/v1/admin/customers/{customerId}/credential/{id}`.
- Provide the following in the request endpoint:
- `customerId`: The ZPA tenant ID of the customer.
- `id`: The ID of the privileged credential.
For example: `mgmtconfig/v1/admin/customers/145256180497776640/credential/11262`.
A successful response returns code 204, meaning the privileged credential was deleted. To learn more, see [API Response Codes and Error Messages](/zpa/api-response-codes-and-error-messages).
This API supports Microtenants. The delete a privileged credential within a Microtenant:
- Send a `DELETE` request to the following endpoint in the Privileged Credential Controller: `/mgmtconfig/v1/admin/customers/{customerId}/credential/{id}?microtenantId={microtenantId}`.
- Provide the following in the request endpoint:
- `customerId`: The ZPA tenant ID of the customer.
- `id`: The ID of the privileged credential.
- `microtenantId`: The unique identifier of the Microtenant for the ZPA tenant. To learn more, see [Configuring Microtenants Using API](/zpa/configuring-microtenants-using-api).
For example: `/mgmtconfig/v1/admin/customers/145256180497776640/credential/11262?microtenantId=145260601092866314`.
A successful response returns code 204, meaning the privileged credential was deleted. To learn more, see [API Response Codes and Error Messages](/zpa/api-response-codes-and-error-messages).
[]Moving a Privileged Credential
To move a privileged credential from one Microtenant to the Default Microtenant and vice-versa:
- Send a `POST` request to the following endpoint in the Privileged Credential Controller: `/mgmtconfig/v1/admin/customers/{customerId}/credential/{id}/move?microtenantId={microtenantId}&targetMicrotenantId={targetMicrotenantId}`.
- Provide the following in the request endpoint:
- `customerId`: The ZPA tenant ID of the customer.
- `id`: The ID of the privileged credential.
- `microtenantId`: The unique identifier of the Microtenant for the ZPA tenant. To learn more, see [Configuring Microtenants Using API](/zpa/configuring-microtenants-using-api).
- `targetMicrotenantId`: The unique identifier of the target Microtenant that the privileged credential is being moved to. This field is required if you want to move a privileged credential.
For example: `/mgmtconfig/v1/admin/customers/145256180497776640/credential/11262?microtenantId=145260601092866314&targetMicrotenantId=145260601092866315`.
A successful response returns code 204, meaning the privileged credential was moved. To learn more, see [API Response Codes and Error Messages](/zpa/api-response-codes-and-error-messages).
[]Adding Field Descriptions
The following table includes descriptions of available fields you can use for the privileged credential use cases:
[](/zpa/about-microtenants)[](/zpa/configuring-microtenants-using-api)
-
-
| Field | Description | Required | Value |
| ----- | ----------- | -------- | ----- |
| customerId | The ZPA tenant ID of the customer | Yes | Integer |
| id | The ID of the privileged credential. | Yes | Integer |
| microtenantId | The unique identifier of the Microtenant for the ZPA tenant. If you are within a Microtenant, you must pass the `microtenantId` field when making an API call to retrieve data from that `Microtenant`. The `microtenantId` can be obtained in the API Keys page, or can be obtained programmatically using the ZPA cloud service API. Access to certain operations are limited when you are within a Microtenant. If you are within the Default Microtenant, pass `microtenantId` as `0` when making requests to retrieve data from the Default Microtenant. Pass `microtenantId` as null to retrieve data from all customers associated with the tenant. If the `microtenantId` is not passed in the request endpoint when creating or updating a resource, then the resource is created or updated in the Default Microtenant. To learn more, see Configuring Microtenants Using API. | No | Integer |
| page | Specifies the page number | No | Integer |
| pageSize | Specifies the page size | No | Integer |
| search | Indicates the search string used to support search by features or fields | No | String |
| sortBy | Indicates the parameter to sort by | No | String |
| sortdir | Specifies the sort direction (i.e., ascending or descending order) | No | EnumSupported values:`ASC`: Ascending`DSC`: Descending |
| targetMicrotenantId | The unique identifier of the target Microtenant that the privileged credential is being moved to. This field is required if you want to move a privileged credential. | No | Integer |

## Contents
- **API Developer & Reference Guide**
  - [Getting Started](/zpa/getting-started-zpa-api)
  - [Configuring the Postman REST API Client](/zpa/configuring-postman-rest-api-client)
  - [Understanding Rate Limiting](/zpa/understanding-rate-limiting)
  - [API Response Codes and Error Messages](/zpa/api-response-codes-and-error-messages)
  - **Reference Guide**
    - [Admin Single Sign-On Management](/zpa/admin-single-sign-management)
    - [API Key Management](/zpa/api-key-management-zpa-api-reference)
    - [Application Segment Management](/zpa/application-segment-management)
    - [Segment Group Management](/zpa/segment-group-management)
    - [AppProtection Control Management](/zpa/appprotection-control-management)
    - [AppProtection Profile Management](/zpa/appprotection-profile-management)
    - [App Connector Management API](/zpa/app-connector-management-api)
    - [App Connector Group Management](/zpa/app-connector-group-management)
    - [Certificate Management](/zpa/certificate-management-api)
    - [Customers](/zpa/customers)
    - [Customer Domain Management](/zpa/customer-domain-management)
    - [Cloud Connector Groups](/zpa/cloud-connector-groups)
    - [Emergency Access User Management](/zpa/emergency-access-user-management)
    - [Enrollment Certificates](/zpa/enrollment-certificates)
    - [Feature Configuration Management](/zpa/feature-configuration-management)
    - [IdP Configurations](/zpa/idp-configurations)
    - [Isolation Profiles](/zpa/isolation-profiles)
    - [Log Streaming Service (LSS) Configuration](/zpa/log-streaming-service-lss-configuration)
    - [Machine Groups](/zpa/machine-groups)
    - [Delegated Tenant Administration](/zpa/delegated-tenant-administration)
    - [Policy Management](/zpa/policy-management)
    - [Posture Profiles](/zpa/posture-profiles)
    - [Private Service Edge Management](/zpa/private-service-edge-management-api)
    - [Private Service Edge Group Management](/zpa/private-service-edge-group-management)
    - [Private Cloud Controller Management](/zpa/private-cloud-controller-management-zpa-api-reference)
    - [Private Cloud Controller Group Management](/zpa/private-cloud-controller-group-management)
    - [Privileged Approval Management](/zpa/privileged-approval-management)
    - [Privileged Console Management](/zpa/privileged-console-management)
    - [Privileged Credential Management](/zpa/privileged-credential-management)
    - [Privileged Portal Management](/zpa/privileged-portal-management)
    - [Provisioning Key Management](/zpa/provisioning-key-management)
    - [SAML Attributes](/zpa/saml-attributes)
    - [SCIM Attributes](/zpa/scim-attributes)
    - [SCIM Groups](/zpa/scim-groups)
    - [Server Management](/zpa/server-management)
    - [Server Group Management](/zpa/server-group-management)
    - [Trusted Networks](/zpa/trusted-networks)
    - [User Portal Management](/zpa/user-portal-management)
    - [User Portal Link Management](/zpa/user-portal-link-management)
    - [Version Profiles](/zpa/version-profiles)
    - [VPN (for Legacy Apps) API](/zpa/vpn-legacy-apps-api)
    - [Zscaler Clouds ](/zpa/zscaler-clouds)
    - [Zscaler Virtual IP Address Range Management](/zpa/zscaler-virtual-ip-address-range-management)
  - **Working with APIs**
    - [Managing Administrators Using API](/zpa/managing-administrators-using-api)
    - [Managing Administrator Roles Using API](/zpa/managing-administrator-roles-using-api)
    - [Managing Admin Single Sign-On Login Configurations Using API](/zpa/managing-admin-single-sign-login-configurations-using-api)
    - [Managing Client Settings Using API](/zpa/managing-client-settings-using-api)
    - [Obtaining Alternative Cloud Domain Details Using API](/zpa/obtaining-alternative-cloud-domain-details-using-api)
    - [Configuring API Keys Using API](/zpa/configuring-api-keys-using-api)
    - [Managing Application Load Balancing and High Availability Using API](/zpa/managing-application-load-balancing-and-high-availability-using-api)
    - [Configuring Application Segments Using API](/zpa/configuring-application-segments-using-api)
    - [Configuring Application Segment Multimatch Using API](/zpa/configuring-application-segment-multimatch-using-api)
    - [Configuring Segment Groups Using API](/zpa/configuring-segment-groups-using-api)
    - [Managing App Connectors Using API](/zpa/managing-app-connectors-using-api)
    - [Configuring Auto Delete for Disconnected App Connectors Using API](/zpa/configuring-auto-delete-disconnected-app-connectors-using-api)
    - [Configuring App Connector Groups Using API](/zpa/configuring-app-connector-groups-using-api)
    - [Configuring Browser Access Application Segments Using API](/zpa/configuring-browser-access-application-segments-using-api)
    - [Configuring Certificates Using API](/zpa/configuring-certificates-using-api)
    - [Obtaining Cloud Connector Group Details Using API](/zpa/obtaining-cloud-connector-group-details-using-api)
    - [Obtaining Customer Details Using API](/zpa/obtaining-customer-details-using-api)
    - [Managing Customer Domains Using API](/zpa/managing-customer-domains-using-api)
    - [Configuring Emergency Access Users Using API](/zpa/configuring-emergency-access-users-using-api)
    - [Obtaining Enrollment Certificate Details Using API](/zpa/obtaining-enrollment-certificate-details-using-api)
    - [Managing Feature Configurations Using API](/zpa/managing-feature-configurations-using-api)
    - [Obtaining IdP Configuration Details Using API](/zpa/obtaining-idp-configuration-details-using-api)
    - [Configuring AppProtection Controls Using API](/zpa/configuring-appprotection-controls-using-api)
    - [Configuring AppProtection Profiles Using API](/zpa/configuring-appprotection-profiles-using-api)
    - [Obtaining Isolation Profile Details Using API](/zpa/obtaining-isolation-profile-details-using-api)
    - [Managing Log Streaming Service Configurations Using API](/zpa/managing-log-streaming-service-configurations-using-api)
    - [Configuring Access Policies Using API](/zpa/configuring-access-policies-using-api)
    - [Configuring AppProtection Policies Using API](/zpa/configuring-appprotection-policies-using-api)
    - [Configuring Client Forwarding Policies Using API](/zpa/configuring-client-forwarding-policies-using-api)
    - [Configuring Isolation Policies Using API](/zpa/configuring-isolation-policies-using-api)
    - [Configuring Privileged Policies Using API](/zpa/configuring-privileged-policies-using-api)
    - [Configuring Redirection Policies Using API](/zpa/configuring-redirection-policies-using-api)
    - [Configuring Timeout Policies Using API](/zpa/configuring-timeout-policies-using-api)
    - [Obtaining Machine Group Details Using API](/zpa/obtaining-machine-group-details-using-api)
    - [Configuring Microtenants Using API](/zpa/configuring-microtenants-using-api)
    - [Obtaining Posture Profile Details Using API](/zpa/obtaining-posture-profile-details-using-api)
    - [Configuring Privileged Approvals Using API](/zpa/configuring-privileged-approvals-using-api)
    - [Configuring Privileged Credentials Using API](/zpa/configuring-privileged-credentials-using-api)
    - [Configuring Privileged Consoles Using API](/zpa/configuring-privileged-consoles-using-api)
    - [Configuring Privileged Portals Using API](/zpa/configuring-privileged-portals-using-api)
    - [Configuring Provisioning Keys Using API](/zpa/configuring-provisioning-keys-using-api)
    - [Obtaining SAML Attribute Details Using API](/zpa/obtaining-saml-attribute-details-using-api)
    - [Obtaining SCIM Attribute Details Using API](/zpa/obtaining-scim-attribute-details-using-api)
    - [Obtaining SCIM Group Details Using API](/zpa/obtaining-scim-group-details-using-api)
    - [Configuring Servers Using API](/zpa/configuring-servers-using-api)
    - [Configuring Server Groups Using API](/zpa/configuring-server-groups-using-api)
    - [Managing ZPA Private Service Edges Using API](/zpa/managing-zpa-private-service-edges-using-api)
    - [Configuring ZPA Private Service Edge Groups Using API](/zpa/configuring-zpa-private-service-edge-groups-using-api)
    - [Managing Private Cloud Controllers Using API](/zpa/managing-private-cloud-controllers-using-api)
    - [Managing Private Cloud Controller Groups Using API](/zpa/managing-private-cloud-controller-groups-using-api)
    - [Obtaining VPN (for Legacy Apps) Resources Using API](/zpa/obtaining-vpn-legacy-apps-resources-using-api)
    - [Obtaining Trusted Network Details Using API](/zpa/obtaining-trusted-network-details-using-api)
    - [Obtaining Version Profile Details Using API](/zpa/obtaining-version-profile-details-using-api)
    - [Configuring User Portals Using API](/zpa/configuring-user-portals-using-api)
    - [Configuring User Portal Links Using API](/zpa/configuring-user-portal-links-using-api)
    - [Configuring Zscaler Virtual IP Address Ranges Using API](/zpa/configuring-zscaler-virtual-ip-address-ranges-using-api)