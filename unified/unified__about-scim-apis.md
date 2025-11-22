# About SCIM APIs
Source: https://help.zscaler.com/unified/about-scim-apis
PDF: https://help.zscaler.com/pdf/com/en/1491481.pdf

The SCIM APIs allow you to use custom SCIM clients to make REST API calls to Zscaler. To learn more, see [About SCIM](/unified/about-scim) and [SCIM API Examples](/unified/scim-api-examples).
All SCIM APIs are rate limited. To learn more, contact Zscaler Support.
[]Operations Supported by the Zscaler SCIM Servers
The following table includes the supported SCIM API operations:
| Operation | HTTP Request |
| --------- | ------------ |
| Endpoints/Users |  |
| Fetch All Users | `GET``https://{{hostname}}/scim/{{userdb}}/{{idpId}}/v2/Users` |
| Create User | `POST https://{{hostname}}/scim/{{userdb}}/{{idpId}}/v2/Users` |
| Fetch User by ID | `GET https://{{hostname}}/scim/{{userdb}}/{{idpId}}/v2/Users/``{{userId}}` |
| Update User | `PUT https://{{hostname}}/scim/{{userdb}}/{{idpId}}/v2/Users/``{{userId}}`or`PATCH https://{{hostname}}/scim/{{userdb}}/{{idpId}}/v2/Users/``{{userId}}` |
| Delete User | `DELETE https://{{hostname}}/scim/{{userdb}}/{{idpId}}/v2/Users/``{{userId}}` |
| Endpoints/Groups |  |
| ---------------- | --- |
| Fetch All Groups | `GET``https://{{hostname}}/scim/{{userdb}}/{{idpId}}/v2/Groups` |
| Create Group | `POST https://{{hostname}}/scim/{{userdb}}/{{idpId}}/v2/Groups` |
| Fetch Group by ID | `GET https://{{hostname}}/scim/{{userdb}}/{{idpId}}/v2/Groups/``{{groupId}}` |
| Fetch Groups with Pagination and Sort | `GET https://{{hostname}}/scim/{{userdb}}/{{idpId}}/v2/Groups?startIndex=1&count=10&sortBy=displayName&sortOrder=descending` |
| Update Group | `PUT``https://{{hostname}}/scim/{{userdb}}/{{idpId}}/v2/Groups/``{{groupId}}`or`PATCH https://{{hostname}}/scim/{{userdb}}/{{idpId}}/v2/Groups/``{{groupId}}` |
| Delete Group | `DELETE``https://{{hostname}}/scim/{{userdb}}/{{idpId}}/v2/Groups/{{groupId}}` |