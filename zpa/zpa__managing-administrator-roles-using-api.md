# Managing Administrator Roles Using API
Source: https://help.zscaler.com/zpa/managing-administrator-roles-using-api
PDF: https://help.zscaler.com/pdf/com/en/1529292.pdf

This article provides information for managing Zscaler Private Access (ZPA) administrator roles using APIs. All APIs are rate limited. To learn more, see [Understanding Rate Limiting](/zpa/understanding-rate-limiting).
[]Getting All Default Permission Groups
To get the details of all default permission groups:
- Send a GET request to the following endpoint: `/mgmtconfig/v1/admin/customers/{customerId}/permissionGroups`.
- Proivde the `customerId`, the ZPA tenant ID of the customer, in the request endpoint. For example: `/mgmtconfig/v1/admin/customers/145256180497776640/permissionGroups`.
- [View an example response](#getPermissionResponse)
[]
`[
{
"id": "9",
"modifiedTime": "0",
"creationTime": "1516480235",
"name": "Administration",
"hidden": false,
"internal": false,
"localScopePermissionGroup": true,
"classPermissions": [
{
"permission": {
"mask": "15",
"type": "FULL",
"maxMask": "15"
},
"classType": {
"id": "5",
"modifiedTime": "0",
"creationTime": "1412894758",
"aclClass": "com.zscaler.zpath.model.User",
"friendlyName": "User",
"localScopeMask": "15"
}
},
{
"permission": {
"mask": "15",
"type": "FULL",
"maxMask": "1"
},
"classType": {
"id": "14",
"modifiedTime": "0",
"creationTime": "1412894758",
"aclClass": "com.zscaler.common.model.Role",
"friendlyName": "Role",
"localScopeMask": "15"
}
},
{
"permission": {
"mask": "15",
"type": "FULL",
"maxMask": "15"
},
"classType": {
"id": "22",
"modifiedTime": "0",
"creationTime": "1412894758",
"aclClass": "com.zscaler.common.model.Audit",
"friendlyName": "Audit",
"localScopeMask": "15"
}
},
{
"permission": {
"mask": "15",
"type": "FULL",
"maxMask": "15"
},
"classType": {
"id": "85",
"modifiedTime": "0",
"creationTime": "1558732428",
"aclClass": "com.zscaler.zpn.model.UserPortalAUP",
"friendlyName": "UserPortalAUP",
"localScopeMask": "15"
}
},
{
"permission": {
"mask": "15",
"type": "FULL",
"maxMask": "15"
},
"classType": {
"id": "158",
"modifiedTime": "0",
"creationTime": "1657523270",
"aclClass": "com.zscaler.zpn.model.DisasterRecovery",
"friendlyName": "Disaster Recovery",
"localScopeMask": "1"
}
},
{
"permission": {
"mask": "15",
"type": "FULL",
"maxMask": "15"
},
"classType": {
"id": "165",
"modifiedTime": "0",
"creationTime": "1664780102",
"aclClass": "com.zscaler.zpn.dto.ZiaCloudConfig",
"friendlyName": "Zscaler Cloud Sandbox",
"localScopeMask": "1"
}
},
{
"permission": {
"mask": "15",
"type": "FULL",
"maxMask": "15"
},
"classType": {
"id": "164",
"modifiedTime": "0",
"creationTime": "1663835534",
"aclClass": "com.zscaler.zpn.model.C2cIpRanges",
"friendlyName": "Client Connector IP Assignement",
"localScopeMask": "1"
}
},
{
"permission": {
"mask": "15",
"type": "FULL",
"maxMask": "15"
},
"classType": {
"id": "149",
"modifiedTime": "0",
"creationTime": "1650354549",
"aclClass": "com.zscaler.zpn.model.Scope",
"friendlyName": "Microtenant",
"localScopeMask": "0"
}
}
]
},
{
"id": "6",
"modifiedTime": "0",
"creationTime": "1516480235",
"name": "Authentication",
"hidden": false,
"internal": false,
"localScopePermissionGroup": true,
"classPermissions": [
{
"permission": {
"mask": "1",
"type": "VIEW_ONLY",
"maxMask": "15"
},
"classType": {
"id": "86",
"modifiedTime": "0",
"creationTime": "1560752143",
"aclClass": "com.zscaler.common.model.AuthenticationSetting",
"friendlyName": "AuthenticationSetting",
"localScopeMask": "1"
}
},
{
"permission": {
"mask": "15",
"type": "FULL",
"maxMask": "15"
},
"classType": {
"id": "133",
"modifiedTime": "0",
"creationTime": "1639394078",
"aclClass": "com.zscaler.zpn.master.model.ZPathConfigOverride",
"friendlyName": "ZPathConfigOverride",
"localScopeMask": "1"
}
},
{
"permission": {
"mask": "15",
"type": "FULL",
"maxMask": "15"
},
"classType": {
"id": "37",
"modifiedTime": "0",
"creationTime": "1429316165",
"aclClass": "com.zscaler.zpn.model.Idp",
"friendlyName": "Idp",
"localScopeMask": "1"
}
},
{
"permission": {
"mask": "15",
"type": "FULL",
"maxMask": "15"
},
"classType": {
"id": "41",
"modifiedTime": "0",
"creationTime": "1429316165",
"aclClass": "com.zscaler.zpn.model.SamlAttribute",
"friendlyName": "SamlAttribute",
"localScopeMask": "1"
}
},
{
"permission": {
"mask": "1",
"type": "VIEW_ONLY",
"maxMask": "15"
},
"classType": {
"id": "72",
"modifiedTime": "0",
"creationTime": "1518721867",
"aclClass": "com.zscaler.common.model.RemoteAssistance",
"friendlyName": "RemoteAssistance",
"localScopeMask": "1"
}
},
{
"permission": {
"mask": "15",
"type": "FULL",
"maxMask": "15"
},
"classType": {
"id": "181",
"modifiedTime": "0",
"creationTime": "1679041787",
"aclClass": "com.zscaler.zpn.model.EmergencyAccessConfig",
"friendlyName": "Emergency Access",
"localScopeMask": "1"
}
},
{
"permission": {
"mask": "15",
"type": "FULL",
"maxMask": "15"
},
"classType": {
"id": "182",
"modifiedTime": "0",
"creationTime": "1679041787",
"aclClass": "com.zscaler.zpn.dto.EmergencyAccessUserDTO",
"friendlyName": "Emergency Access Users",
"localScopeMask": "15"
}
}
]
}
]`
A successful response returns code 200. To learn more, see [API Response Codes and Error Messages](/zpa/api-response-codes-and-error-messages).
Getting Details of a Particular Role
To get details of a particular role:
- Send a `GET` request to the following endpoint: `/mgmtconfig/v1/admin/customers/{customerId}/roles/{roleId}`.
-
Provide the following in the request endpoint:
- `customerId`: The ZPA tenant ID of the customer.
- `roleId`: The unique identifier of the role.
For example: `/mgmtconfig/v1/admin/customers/145256180497776640/roles/145256180497776679`.
- [View an example response](#getRoleResponse)
[]
`{
"id": 145256180493676679,
"modifiedTime": 0,
"creationTime": 1426810977,
"modifiedBy": 0,
"name": "Administrator",
"microtenantId": 0,
"microtenantName": "example Microtenant",
"description": "Admin role",
"bypassAccestorAccessCheck": true,
"permissions": [
{
"id": 0,
"modifiedTime": 0,
"creationTime": 0,
"modifiedBy": 0,
"permissionMask": 0,
"classType": {
"id": 0,
"modifiedTime": 0,
"creationTime": 0,
"modifiedBy": 0,
"aclClass": "string",
"friendlyName": "string",
"localScopeMask": 0,
"customerId": 0
},
"role": "string",
"customerId": 0
}
],
"customRole": true,
"systemRole": true,
"restrictedRole": true,
"classPermissionGroups": [
{
"id": 0,
"modifiedTime": 0,
"creationTime": 0,
"modifiedBy": 0,
"name": "string",
"hidden": true,
"internal": true,
"localScopePermissionGroup": true,
"classPermissions": [
{
"modifiedTime": 0,
"creationTime": 0,
"modifiedBy": "string",
"id": "string",
"permission": {
"mask": 0,
"type": "FULL",
"maxMask": 0
},
"classType": {
"id": 0,
"modifiedTime": 0,
"creationTime": 0,
"modifiedBy": 0,
"aclClass": "string",
"friendlyName": "string",
"localScopeMask": 0,
"customerId": 0
}
}
]
}
],
"users": 0,
"apiKeys": 0,
"newAuditMessage": "string",
"oldAuditMessage": "string"
}`
A successful response returns code 200. To learn more, see [API Response Codes and Error Messages](/zpa/api-response-codes-and-error-messages).
Getting Details of All Configured Roles
To get details of all configured roles:
- Send a `GET` request to the following endpoint: `/mgmtconfig/v1/admin/customers/{customerId}/roles`.
- Proivde the `customerId`, the ZPA tenant ID of the customer, in the request endpoint. For example: `/mgmtconfig/v1/admin/customers/145256180497776640/roles`.
- [View an example response](#getAllRolesResponse)
[]
`[
{
"id": "145256180497776679",
"name": "Plant Manager",
"description": "Factory Plant Manager",
"bypassAccestorAccessCheck": false,
"customRole": true,
"systemRole": false,
"restrictedRole": false,
"classPermissionGroups": [
{
"id": "67",
"modifiedTime": "0",
"creationTime": "1633072041",
"name": "Privileged Remote Access",
"hidden": false,
"internal": false,
"localScopePermissionGroup": true,
"classPermissions": [
{
"permission": {
"mask": "1",
"type": "VIEW_ONLY",
"maxMask": "0"
},
"classType": {
"id": "198",
"modifiedTime": "0",
"creationTime": "1706108325",
"aclClass": "com.zscaler.zpn.model.CmdbClusterUpload",
"friendlyName": "CmdbClusterUpload",
"localScopeMask": "15"
}
},
{
"permission": {
"mask": "15",
"type": "FULL",
"maxMask": "0"
},
"classType": {
"id": "128",
"modifiedTime": "0",
"creationTime": "1632722165",
"aclClass": "com.zscaler.zpn.model.SRAPortal",
"friendlyName": "Privileged Portal",
"localScopeMask": "15"
}
},
{
"permission": {
"mask": "15",
"type": "FULL",
"maxMask": "0"
},
"classType": {
"id": "129",
"modifiedTime": "0",
"creationTime": "1632722165",
"aclClass": "com.zscaler.zpn.model.SRAConsole",
"friendlyName": "Privileged Console",
"localScopeMask": "15"
}
},
{
"permission": {
"mask": "15",
"type": "FULL",
"maxMask": "0"
},
"classType": {
"id": "26",
"modifiedTime": "0",
"creationTime": "1426810977",
"aclClass": "com.zscaler.zpn.model.Application",
"friendlyName": "Application",
"localScopeMask": "15"
}
},
{
"permission": {
"mask": "15",
"type": "FULL",
"maxMask": "0"
},
"classType": {
"id": "32",
"modifiedTime": "0",
"creationTime": "1426810977",
"aclClass": "com.zscaler.zpn.model.SigningCert",
"friendlyName": "SigningCert",
"localScopeMask": "15"
}
},
{
"permission": {
"mask": "15",
"type": "FULL",
"maxMask": "0"
},
"classType": {
"id": "144",
"modifiedTime": "0",
"creationTime": "1648565893",
"aclClass": "com.zscaler.zpn.model.JITApprovalView",
"friendlyName": "Privileged Approval",
"localScopeMask": "15"
}
},
{
"permission": {
"mask": "15",
"type": "FULL",
"maxMask": "0"
},
"classType": {
"id": "160",
"modifiedTime": "0",
"creationTime": "1660920636",
"aclClass": "com.zscaler.zpn.model.Credential",
"friendlyName": "Privileged Credential",
"localScopeMask": "15"
}
},
{
"permission": {
"mask": "15",
"type": "FULL",
"maxMask": "0"
},
"classType": {
"id": "268",
"modifiedTime": "0",
"creationTime": "1729268777",
"aclClass": "com.zscaler.zpn.model.CredentialPool",
"friendlyName": "Privileged Credential Pool",
"localScopeMask": "15"
}
}
]
}
],
"users": "0"
},
{
"id": "145256180497778051",
"name": "test-disable-ui",
"bypassAccestorAccessCheck": false,
"customRole": true,
"systemRole": false,
"restrictedRole": false,
"users": "0"
},
{
"id": "28",
"name": "API Full Access",
"description": "API Full Access user with full access to Public APIs",
"bypassAccestorAccessCheck": false,
"customRole": false,
"systemRole": false,
"restrictedRole": false,
"apiKeys": "7"
}
]`
A successful response returns code 200. To learn more, see [API Response Codes and Error Messages](/zpa/api-response-codes-and-error-messages).
Prerequisite API Calls
Before creating or updating a role, you must [get the default permission groups](#GetPermissionGroups).
Creating a New Role
To create a new role:
- Send a `POST` request to the following endpoint: `/mgmtconfig/v1/admin/customers/{customerId}/roles`.
- Provide the `customerId`, the ZPA tenant ID of the customer, in the request endpoint. For example: `/mgmtconfig/v1/admin/customers/145256180497776640/roles`.
- Include the request headers to provide information about the request context:
- Content-Type: `application/json`
- Authorization: `Bearer <access_token>`
- Use the following JSON payload and provide the following information:
- `name`: The name of the role.
- `mask`: The supported CRUD functions per permission. For multiple functions per permission, add the supported integer values together. For example, for read and delete access, the mask value is `9` (i.e., the sum of `1` and `8`). The supported values are:
- `1`: Denotes read-only access
- `2`: Denotes write-only access
- `4`: Denotes create-only access
- `8`: Denotes delete-only access
- `type`: The permission type. If the value is set to `permission.type` value is set to `VIEW_ONLY`, then the `permission.mask` value must be set to `1`. If the value is set to `permission.type` value is set to `FULL`, then the `permission.mask` value must be set to `15`. The supported values are:
- `VIEW_ONLY`: Denotes view-only permissions
- `FULL`: Denotes full access
- The default permission groups you want to pass that are captured in [Getting All Default Permission Groups](#GetPermissionGroups).
- [View the JSON payload](#postJsonPayload)
[]
` {
"id": 0,
"modifiedTime": 0,
"creationTime": 0,
"modifiedBy": 0,
"name": "string",
"microtenantId": 0,
"microtenantName": "string",
"description": "string",
"bypassRemoteAssistanceCheck": false,
"permissions": [
"#/components/schemas/ClassPermission"
],
"customRole": false,
"systemRole": false,
"restrictedRole": false,
"classPermissionGroups": [
{
"id": 0,
"modifiedTime": 0,
"creationTime": 0,
"modifiedBy": 0,
"name": "string",
"hidden": false,
"internal": false,
"localScopePermissionGroup": false,
"classPermissions": [
{
"modifiedTime": 0,
"creationTime": 0,
"modifiedBy": "string",
"id": "string",
"permission": {
"mask": 0,
"type": "FULL",
"maxMask": 0
},
"classType": {
"id": 0,
"modifiedTime": 0,
"creationTime": 0,
"modifiedBy": 0,
"aclClass": "string",
"friendlyName": "string",
"localScopeMask": 0,
"customerId": 0
}
}
]
}
],
"users": 0,
"apiKeys": 0,
"newAuditMessage": "string",
"oldAuditMessage": "string"
}`
- [View an example JSON payload](#examplePostJson)
[]
`{
"customRole":false,
"name":"test aneela apr30",
"description":"",
"classPermissionGroups":[
{
"id":"82",
"modifiedTime":"0",
"creationTime":"1670623256",
"name":"Browser Isolation",
"hidden":false,
"internal":false,
"localScopePermissionGroup":true,
"classPermissions":[
{
"permission":{
"mask":"15",
"type":"FULL",
"maxMask":"15"
},
"classType":{
"id":"172",
"modifiedTime":"0",
"creationTime":"1670623245",
"aclClass":"com.zscaler.cbi.zpa.model.CbiBanner",
"friendlyName":"CbiBanner",
"localScopeMask":"1"
},
"key":"BrowserIsolation-com.zscaler.cbi.zpa.model.CbiBanner-172"
},
{
"permission":{
"mask":"1",
"type":"VIEW_ONLY",
"maxMask":"15"
},
"classType":{
"id":"171",
"modifiedTime":"0",
"creationTime":"1670623245",
"aclClass":"com.zscaler.cbi.zpa.model.CbiCertificate",
"friendlyName":"CbiCertificate",
"localScopeMask":"1"
},
"key":"BrowserIsolation-com.zscaler.cbi.zpa.model.CbiCertificate-171"
},
{
"permission":{
"mask":"15",
"type":"FULL",
"maxMask":"15"
},
"classType":{
"id":"110",
"modifiedTime":"0",
"creationTime":"1610745057",
"aclClass":"com.zscaler.zpn.model.CbiProfile",
"friendlyName":"CbiProfile",
"localScopeMask":"15"
},
"key":"BrowserIsolation-com.zscaler.zpn.model.CbiProfile-110"
}
],
"enabled":true,
"customized":false
}
]
}`
- [View an example response](#postExampleResponse)
[]
` {
"id": "145256180497790172",
"modifiedTime": "1746053272",
"creationTime": "1746053272",
"modifiedBy": "145256180497790112",
"name": "test aneela apr30",
"bypassAccestorAccessCheck": false,
"customRole": true,
"systemRole": false,
"restrictedRole": false,
"classPermissionGroups": [
{
"id": "82",
"modifiedTime": "0",
"creationTime": "1670623256",
"name": "Browser Isolation",
"hidden": false,
"internal": false,
"localScopePermissionGroup": true,
"classPermissions": [
{
"permission": {
"mask": "15",
"type": "FULL",
"maxMask": "15"
},
"classType": {
"id": "172",
"modifiedTime": "0",
"creationTime": "1670623245",
"aclClass": "com.zscaler.cbi.zpa.model.CbiBanner",
"friendlyName": "CbiBanner",
"localScopeMask": "1"
}
},
{
"permission": {
"mask": "1",
"type": "VIEW_ONLY",
"maxMask": "15"
},
"classType": {
"id": "171",
"modifiedTime": "0",
"creationTime": "1670623245",
"aclClass": "com.zscaler.cbi.zpa.model.CbiCertificate",
"friendlyName": "CbiCertificate",
"localScopeMask": "1"
}
},
{
"permission": {
"mask": "15",
"type": "FULL",
"maxMask": "15"
},
"classType": {
"id": "110",
"modifiedTime": "0",
"creationTime": "1610745057",
"aclClass": "com.zscaler.zpn.model.CbiProfile",
"friendlyName": "CbiProfile",
"localScopeMask": "15"
}
}
]
},
{
"id": "1",
"modifiedTime": "0",
"creationTime": "1516480233",
"name": "CommonGroupWithReadAccess",
"hidden": true,
"internal": false,
"localScopePermissionGroup": false,
"classPermissions": [
{
"permission": {
"mask": "1",
"type": "VIEW_ONLY",
"maxMask": "1"
},
"classType": {
"id": "70",
"modifiedTime": "0",
"creationTime": "1517257732",
"aclClass": "com.zscaler.common.permission.CommonPermissionReadAccess",
"friendlyName": "CommonPermissionReadAccess",
"localScopeMask": "1"
}
},
{
"permission": {
"mask": "1",
"type": "VIEW_ONLY",
"maxMask": "1"
},
"classType": {
"id": "185",
"modifiedTime": "0",
"creationTime": "1684693390",
"aclClass": "com.zscaler.zpn.dto.MicrotenantInReadOnlyMode",
"friendlyName": "MicrotenantInReadOnlyMode",
"localScopeMask": "15"
}
},
{
"permission": {
"mask": "1",
"type": "VIEW_ONLY",
"maxMask": "1"
},
"classType": {
"id": "1",
"modifiedTime": "0",
"creationTime": "1412894758",
"aclClass": "com.zscaler.common.model.Customer",
"friendlyName": "Customer",
"localScopeMask": "1"
}
},
{
"permission": {
"mask": "1",
"type": "VIEW_ONLY",
"maxMask": "1"
},
"classType": {
"id": "50",
"modifiedTime": "0",
"creationTime": "1445388238",
"aclClass": "com.zscaler.common.service.Zendesk",
"friendlyName": "Zendesk",
"localScopeMask": "15"
}
},
{
"permission": {
"mask": "1",
"type": "VIEW_ONLY",
"maxMask": "1"
},
"classType": {
"id": "111",
"modifiedTime": "0",
"creationTime": "1610745057",
"aclClass": "com.zscaler.zpn.model.ZpnCbiMapping",
"friendlyName": "ZpnCbiMapping",
"localScopeMask": "1"
}
}
]
},
{
"id": "2",
"modifiedTime": "0",
"creationTime": "1516480234",
"name": "CommonGroupWithFullAccess",
"hidden": true,
"internal": false,
"localScopePermissionGroup": false,
"classPermissions": [
{
"permission": {
"mask": "15",
"type": "FULL",
"maxMask": "15"
},
"classType": {
"id": "61",
"modifiedTime": "0",
"creationTime": "1484012721",
"aclClass": "com.zscaler.zpn.model.AdminPreference",
"friendlyName": "AdminPreference",
"localScopeMask": "15"
}
}
]
},
{
"id": "99",
"modifiedTime": "0",
"creationTime": "1721110950",
"name": "ZSDK",
"hidden": true,
"internal": false,
"localScopePermissionGroup": false,
"classPermissions": [
{
"permission": {
"mask": "15",
"type": "FULL",
"maxMask": "15"
},
"classType": {
"id": "240",
"modifiedTime": "0",
"creationTime": "1721110895",
"aclClass": "com.zscaler.zsdk.entity.ZsdkIdentifier",
"friendlyName": "ZSDK Identifier",
"localScopeMask": "0"
}
},
{
"permission": {
"mask": "15",
"type": "FULL",
"maxMask": "15"
},
"classType": {
"id": "282",
"modifiedTime": "0",
"creationTime": "1742203028",
"aclClass": "com.zscaler.zsdk.entity.ZsdkDeviceProfile",
"friendlyName": "ZSDK Device Posture",
"localScopeMask": "0"
}
}
]
}
],
"newAuditMessage": "{\"name\":\"test aneela apr30\",\"bypassAccestorAccessCheck\":\"false\",\"customRole\":\"true\",\"description\":\"\",\"accessControlGroups\":[{\"id\":82,\"name\":\"Browser Isolation\"},{\"id\":1,\"name\":\"CommonGroupWithReadAccess\"},{\"id\":2,\"name\":\"CommonGroupWithFullAccess\"},{\"id\":99,\"name\":\"ZSDK\"}],\"permissions\":[{\"permissionMask\":15,\"accessType\":\"FULL\",\"classType\":{\"id\":\"240\",\"name\":\"ZSDK Identifier\"}},{\"permissionMask\":1,\"accessType\":\"VIEW_ONLY\",\"classType\":{\"id\":\"1\",\"name\":\"Customer\"}},{\"permissionMask\":1,\"accessType\":\"VIEW_ONLY\",\"classType\":{\"id\":\"50\",\"name\":\"Zendesk\"}},{\"permissionMask\":1,\"accessType\":\"VIEW_ONLY\",\"classType\":{\"id\":\"70\",\"name\":\"CommonPermissionReadAccess\"}},{\"permissionMask\":1,\"accessType\":\"VIEW_ONLY\",\"classType\":{\"id\":\"185\",\"name\":\"MicrotenantInReadOnlyMode\"}},{\"permissionMask\":15,\"accessType\":\"FULL\",\"classType\":{\"id\":\"282\",\"name\":\"ZSDK Device Posture\"}},{\"permissionMask\":1,\"accessType\":\"VIEW_ONLY\",\"classType\":{\"id\":\"171\",\"name\":\"CbiCertificate\"}},{\"permissionMask\":15,\"accessType\":\"FULL\",\"classType\":{\"id\":\"172\",\"name\":\"CbiBanner\"}},{\"permissionMask\":15,\"accessType\":\"FULL\",\"classType\":{\"id\":\"61\",\"name\":\"AdminPreference\"}},{\"permissionMask\":15,\"accessType\":\"FULL\",\"classType\":{\"id\":\"110\",\"name\":\"CbiProfile\"}},{\"permissionMask\":1,\"accessType\":\"VIEW_ONLY\",\"classType\":{\"id\":\"111\",\"name\":\"ZpnCbiMapping\"}}]}"
}`
A successful response returns code 201. To learn more, see [API Response Codes and Error Messages](/zpa/api-response-codes-and-error-messages).
Updating a Role
To update a role:
- Send a `PUT` request to the following endpoint: `/mgmtconfig/v1/admin/customers/{customerId}/roles/{roleId}`.
-
Provide the following in the request endpoint:
- `customerId`: The ZPA tenant ID of the customer.
- `roleId`: The unique identifier of the role.
For example: `/mgmtconfig/v1/admin/customers/145256180497776640/roles/145256180497776679`.
- Include the request headers to provide information about the request context:
- Content-Type: `application/json`
- Authorization: `Bearer <access_token>`
- Use the following JSON payload and provide the following information:
- `name`: The name of the role.
- `mask`: The supported CRUD functions per permission. For multiple functions per permission, add the supported integer values together. For example, for read and delete access, the mask value is `9` (i.e., the sum of `1` and `8`). The supported values are:
- `1`: Denotes read-only access
- `2`: Denotes write-only access
- `4`: Denotes create-only access
- `8`: Denotes delete-only access
- `type`: The permission type. If the value is set to `permission.type` value is set to `VIEW_ONLY`, then the `permission.mask` value must be set to `1`. If the value is set to `permission.type` value is set to `FULL`, then the `permission.mask` value must be set to `15`. The supported values are:
- `VIEW_ONLY`: Denotes view-only permissions
- `FULL`: Denotes full access
- The default permission groups you want to pass that are captured in [Getting All Default Permission Groups](#GetPermissionGroups).
- [View the JSON payload](#putJsonPayload)
[]
` {
"id": 0,
"modifiedTime": 0,
"creationTime": 0,
"modifiedBy": 0,
"name": "string",
"microtenantId": 0,
"microtenantName": "string",
"description": "string",
"bypassRemoteAssistanceCheck": false,
"permissions": [
"#/components/schemas/ClassPermission"
],
"customRole": false,
"systemRole": false,
"restrictedRole": false,
"classPermissionGroups": [
{
"id": 0,
"modifiedTime": 0,
"creationTime": 0,
"modifiedBy": 0,
"name": "string",
"hidden": false,
"internal": false,
"localScopePermissionGroup": false,
"classPermissions": [
{
"permission": {
"mask": 0,
"type": "FULL",
"maxMask": 0
},
"classType": {
"id": 0,
"modifiedTime": 0,
"creationTime": 0,
"modifiedBy": 0,
"aclClass": "string",
"friendlyName": "string",
"localScopeMask": 0,
"customerId": 0
}
}
]
}
],
"users": 0,
"apiKeys": 0,
"newAuditMessage": "string",
"oldAuditMessage": "string"
}`
- [View an example JSON payload](#examplePutPayload)
[]
`   "scopeId":0{
"customRole":false,
"id":"144118148382064895",
"objectType":"Role",
"action":"EDIT",
"name":"custom",
"bypassAccestorAccessCheck":false,
"systemRole":false,
"restrictedRole":false,
"classPermissionGroups":[
{
"id":"7",
"modifiedTime":"0",
"creationTime":"1521771356",
"name":"Authentication",
"localScopePermissionGroup":true,
"classPermissions":[
{
"permission":{
"mask":"15",
"type":"FULL",
"maxMask":"15"
},
"classType":{
"id":"132",
"modifiedTime":"0",
"creationTime":"1649831030",
"aclClass":"com.zscaler.zpn.master.model.ZPathConfigOverride",
"friendlyName":"ZPathConfigOverride",
"localScopeMask":"1"
},
"key":"Authentication-com.zscaler.zpn.master.model.ZPathConfigOverride-132"
},
{
"permission":{
"mask":"15",
"type":"FULL",
"maxMask":"15"
},
"classType":{
"id":"164",
"modifiedTime":"0",
"creationTime":"1683993607",
"aclClass":"com.zscaler.zpn.model.EmergencyAccessConfig",
"friendlyName":"Emergency Access",
"localScopeMask":"1"
},
"key":"Authentication-com.zscaler.zpn.model.EmergencyAccessConfig-164"
},
{
"permission":{
"mask":"15",
"type":"FULL",
"maxMask":"15"
},
"classType":{
"id":"165",
"modifiedTime":"0",
"creationTime":"1683993607",
"aclClass":"com.zscaler.zpn.dto.EmergencyAccessUserDTO",
"friendlyName":"Emergency Access Users",
"localScopeMask":"15"
},
"key":"Authentication-com.zscaler.zpn.dto.EmergencyAccessUserDTO-165"
},
{
"permission":{
"mask":"15",
"type":"FULL",
"maxMask":"15"
},
"classType":{
"id":"37",
"modifiedTime":"0",
"creationTime":"1429316165",
"aclClass":"com.zscaler.zpn.model.Idp",
"friendlyName":"Idp",
"localScopeMask":"1"
},
"key":"Authentication-com.zscaler.zpn.model.Idp-37"
},
{
"permission":{
"mask":"1",
"type":"VIEW_ONLY",
"maxMask":"15"
},
"classType":{
"id":"72",
"modifiedTime":"0",
"creationTime":"1521771356",
"aclClass":"com.zscaler.common.model.RemoteAssistance",
"friendlyName":"RemoteAssistance",
"localScopeMask":"1"
},
"key":"Authentication-com.zscaler.common.model.RemoteAssistance-72"
},
{
"permission":{
"mask":"15",
"type":"FULL",
"maxMask":"15"
},
"classType":{
"id":"41",
"modifiedTime":"0",
"creationTime":"1429316165",
"aclClass":"com.zscaler.zpn.model.SamlAttribute",
"friendlyName":"SamlAttribute",
"localScopeMask":"1"
},
"key":"Authentication-com.zscaler.zpn.model.SamlAttribute-41"
},
{
"permission":{
"mask":"1",
"type":"VIEW_ONLY",
"maxMask":"15"
},
"classType":{
"id":"78",
"modifiedTime":"0",
"creationTime":"1561880878",
"aclClass":"com.zscaler.common.model.AuthenticationSetting",
"friendlyName":"AuthenticationSetting",
"localScopeMask":"1"
},
"key":"Authentication-com.zscaler.common.model.AuthenticationSetting-78"
}
],
"enabled":true,
"customized":false,
"widgetId":"Authentication-7"
},
{
"id":"4",
"modifiedTime":"0",
"creationTime":"1521771356",
"name":"Diagnostics",
"localScopePermissionGroup":true,
"classPermissions":[
{
"permission":{
"mask":"1",
"type":"VIEW_ONLY",
"maxMask":"1"
},
"classType":{
"id":"69",
"modifiedTime":"0",
"creationTime":"1521771356",
"aclClass":"com.zscaler.zpn.model.Diagnostics",
"friendlyName":"Diagnostics",
"localScopeMask":"1"
},
"key":"\"Diagnostics-com.zscalerShow more"`
A successful response returns code 204, meaning the role is updated. To learn more, see [API Response Codes and Error Messages](/zpa/api-response-codes-and-error-messages).
Deleting a Role
To delete a role:
- Send a DELETE request to the following endpoint:
- Send a `PUT` request to the following endpoint: `/mgmtconfig/v1/admin/customers/{customerId}/roles/{roleId}`.
- Provide the following in the request endpoint:
- `customerId`: The ZPA tenant ID of the customer.
- `roleId`: The unique identifier of the role.
A successful response returns code 204, meaning the role is deleted. To learn more, see [API Response Codes and Error Messages](/zpa/api-response-codes-and-error-messages).
Adding Field Descriptions
The following table includes available fields you can use for the administrator role API use cases:
-
-
-
-
-
-
| Field | Description | Required | Value |
| ----- | ----------- | -------- | ----- |
| classType | The details of the permissions resource (e.g., permission name, mask, etc.) | Yes |  |
| aclClass | The name of the permission | Yes | String |
| permission.mask | The supported CRUD functions per permission. For multiple functions per permission, add the supported integer values together. For example, for read and delete access, the `mask` value is `9` (i.e., the sum of `1` and `8`). | Yes | IntegerThe supported values are:`1`: Denotes read-only access`2`: Denotes write-only access`4`: Denotes create-only access`8`: Denotes delete-only access |
| permission.type | The permission type. If the value is set to `permission.type` value is set to `VIEW_ONLY`, then the `permission.mask` value must be set to `1`. If the value is set to `permission.type` value is set to `FULL`, then the `permission.mask` value must be set to `15`. | Yes | StringThe supported values:`VIEW_ONLY`: Denotes view-only permissions`FULL`: Denotes full access |

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