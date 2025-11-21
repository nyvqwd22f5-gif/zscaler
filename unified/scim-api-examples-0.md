# SCIM API Examples
Source: https://help.zscaler.com/unified/scim-api-examples-0
PDF: https://help.zscaler.com/pdf/com/en/1491486.pdf

Using SCIM operations allows you to fetch, create, update, and delete users and groups. To perform these operations, you must enable SCIM-based provisioning and have your SCIM Service Provider Endpoint and Bearer Token. You must provide the Bearer Token to authenticate the SCIM API calls. To learn more, see [Enabling SCIM for Identity Management](/unified/enabling-scim-identity-management).
The SCIM Service Provider Endpoints and references to `scim1.private.zscaler.com` within the examples of this article might differ depending on your organization’s IdP configuration.
For a full list of operations supported by the Zscaler SCIM servers, as well as attribute mappings, see [About SCIM APIs](/unified/about-scim-apis).
All SCIM APIs are rate limited. To learn more, contact Zscaler Support.
Fetching All Users
To fetch all users, send a `GET` request to the following endpoint:
https://{{hostname}}/scim/{{userdb}}/{{idpId}}/v2/Users
- [Curl example](#Curl)
[]curl --location --request GET 'https://scim1.private.zscaler.com/scim/1/144118148382065427/v2/Users' \
--header 'Authorization: Bearer <Token>
- [Response example](#Response)
[]{
"schemas": [
"urn:ietf:params:scim:api:messages:2.0:ListResponse"
],
"startIndex": 1,
"totalResults": 1,
"itemsPerPage": 10,
"Resources": [
{
"schemas": [
"urn:ietf:params:scim:schemas:core:2.0:User",
"urn:ietf:params:scim:schemas:extension:enterprise:2.0:User"
],
"id": "290277",
"externalId": "u43xZ0EZ87qvorWfQLGA",
"nickName": "test1",
"name": {
"formatted": "John Doe kdPrvwZ0hupSS7HSU5yJ@exampletest21.com",
"givenName": "Doe jYdoC2hzU3kMHfxhKcJ5@exampletest21.com",
"familyName": "John 3qHArSw8z8wnXfBSmAcl@exampletest21.com"
},
"userType": "ZPA User",
"displayName": "IcgCl1uDbpjvi4GY8yf4@exampletest21.com",
"emails": [
{
"value": "rN0XKUhmy0@exampletest21.com}@exampletest21.com"
}
],
"active": "true",
"urn:ietf:params:scim:schemas:extension:enterprise:2.0:User": {
"costCenter": "Mohali",
"department": "Cloud and Reliability",
"division": "AFuEwsRyTBVed9RocKWg",
"organization": "BKyX4E@safemarch.com"
},
"userName": "olJSy0vLDb7Ir5fDV0wH@safemarch.com",
"meta": {
"created": "2021-05-03T08:39:01Z",
"lastModified": "2021-05-03T08:39:01Z",
"location": "https://scim1.private.zscaler.com/scim/1/144118148382065427/v2/Users/290277",
"resourceType": "User"
}
}
]
Fetching All Users with Pagination
To fetch all users with pagination, send a GET request to the following endpoint:
`https://{{host}}/scim/{{userdb}}/{{idpId}}/v2/Users?startIndex=1&count=10`
- [Curl example](#CurlfetchUsersPag)
[]curl --location --request GET 'https://scim.private.zscaler.com/scim/1/144118148382065427/v2/Users?startIndex=1&count=10
--header 'Content-Type: application/json' \
--header 'Authorization: Bearer <Token>' \
- [Response example](#fetchUsersPagExample)
[]{
"schemas": [
"urn:ietf:params:scim:api:messages:2.0:ListResponse"
],
"startIndex": 1,
"totalResults": 16,
"itemsPerPage": 10,
"Resources": [
{
"schemas": [
"urn:ietf:params:scim:schemas:core:2.0:User",
"urn:ietf:params:scim:schemas:extension:enterprise:2.0:User"
],
"id": "a7b667fd-6c0c-40c3-af3f-a85b0e20ae73",
"externalId": "00u6um6qj2mpTNu8z5d7",
"name": {
"givenName": "Secondary",
"familyName": "Aden"
},
"active": true,
"userName": "adenulti@adenultimate.skywalker.com",
"groups": [
{
"display": "scim_group",
"value": "c81895c6-6b00-412e-8a94-0b03d4f805e4",
"$ref": "https://scim.private.zscaler.com/scim/1/72058973796171869/v2/Groups/c81895c6-6b00-412e-8a94-0b03d4f805e4"
}
],
"meta": {
"created": "2023-04-21T00:57:37Z",
"lastModified": "2023-04-21T21:09:51Z",
"location": "https://scim.private.zscaler.com/scim/1/72058973796171869/v2/Users/a7b667fd-6c0c-40c3-af3f-a85b0e20ae73",
"resourceType": "User"
},
]
If not specified, the default number of users fetched is 10. The maximum number of users fetched for this call is limited to 100.
Creating a User
To create a new user, send a `POST` request to the following endpoint:
https://{{hostname}}/scim/{{userdb}}/{{idpId}}/v2/Users
- [Curl example](#Curl2)
[]curl --location --request POST 'https://scim1.private.zscaler.com/scim/1/144118148382065427/v2/Users' \
--header 'Content-Type: application/json' \
--header 'Authorization: Bearer <Token> \
--data-raw '{
"schemas": [
"urn:ietf:params:scim:schemas:core:2.0:User",
"urn:ietf:params:scim:schemas:extension:enterprise:2.0:User"
],
"division": "AFuEwsRyTBVed9RocKWg",
"nickName": "scim test",
"organization": "BKyX4E@exampletest21.com",
"userType": "ZPA User",
"costCenter": "Mohali",
"externalId": "u43xZ0EZ87qvorWfQLGA",
"userName": "scim-example@safemarch.com",
"active": "true",
"displayName": "scim example",
"urn:ietf:params:scim:schemas:extension:enterprise:2.0:User": {
"department": "Cloud and Reliability"
},
"name": {
"formatted": "John Doe kdPrvwZ0hupSS7HSU5yJ@exampletest21.com",
"familyName": "Doe 3qHArSw8z8wnXfBSmAcl@exampletest21.com",
"givenName": "John jYdoC2hzU3kMHfxhKcJ5@exampletest21.com"
},
"emails": [
{
"value": "scim-example@safemarch.com}@exampletest21.com"
}
],
}'
- [New user file example](#New)
[]{
"schemas": [
"urn:ietf:params:scim:schemas:core:2.0:User",
"urn:ietf:params:scim:schemas:extension:enterprise:2.0:User"
],
"id": "null",
"division": "AFuEwsRyTBVed9RocKWg",
"nickName": "scim test",
"organization": "BKyX4E@exampletest21.com",
"userType": "ZPA User",
"costCenter": "Mohali",
"externalId": "u43xZ0EZ87qvorWfQLGA",
"userName": "scim-example@safemarch.com",
"active": "true",
"displayName": "scim example",
"urn:ietf:params:scim:schemas:extension:enterprise:2.0:User": {
"department": "Cloud and Reliability"
},
"name": {
"formatted": "John Doe kdPrvwZ0hupSS7HSU5yJ@safemarch.com",
"familyName": "Doe 3qHArSw8z8wnXfBSmAcl@safemarch.com",
"givenName": "John jYdoC2hzU3kMHfxhKcJ5@safemarch.com"
},
"emails": [
{
"value": "scim-example@safemarch.com}@exampletest21.com"
}
],
"meta": {
"created": "2019-09-18T10:13:45Z",
"lastModified": "2019-09-18T10:13:45Z",
"location": "https://scim1.private.zscaler.com/scim/1/144118148382065427/v2/Users/467697ed-199e-4101-84cc-8dcf5e7a47bd",
"resourceType": "User"
}
}
- [Response example](#Response2)
[]{
"schemas": [
"urn:ietf:params:scim:schemas:core:2.0:User",
"urn:ietf:params:scim:schemas:extension:enterprise:2.0:User"
],
"id": "467697ed-199e-4101-84cc-8dcf5e7a47bd",
"externalId": "u43xZ0EZ87qvorWfQLGA",
"urn:ietf:params:scim:schemas:extension:enterprise:2.0:User": {
"division": "AFuEwsRyTBVed9RocKWg",
"organization": "BKyX4E@exampletest21.com",
"costCenter": "Mohali",
"department": "Cloud and Reliability"
},
"nickName": "scim test",
"userType": "ZPA User",
"userName": "scim-example@safemarch.com",
"active": "true",
"displayName": "IcgCl1uDbpjvi4GY8yf4@exampletest21.com",
"name": {
"formatted": "John Doe kdPrvwZ0hupSS7HSU5yJ@safemarch.com",
"familyName": "Doe 3qHArSw8z8wnXfBSmAcl@safemarch.com",
"givenName": "John jYdoC2hzU3kMHfxhKcJ5@safemarch.com"
},
"emails": [
{
"value": "scim-example@safemarch.com}@safemarch.com"
}
],
"meta": {
"created": "2021-05-03T08:39:01Z",
"lastModified": "2021-05-03T08:39:01Z",
"location": "https://scim1.private.zscaler.com/scim/1/144118148382065427/v2/Users/467697ed-199e-4101-84cc-8dcf5e7a47bd",
"resourceType": "User"
}
}
If group information is sent as part of the create, update, or partial update for a user request, then the group information is ignored. User-group memberships can only be updated using the create, update, or partial update for group requests.
Fetch a User by ID
To fetch a user by ID, send a `GET` request to the following endpoint:
https://{{hostname}}/scim/{{userdb}}/{{idpId}}/v2/Users/{{userId}}
Provide the `{{userId}}`, the Internal User ID found on the SCIM Users page in the Admin Portal, in the request endpoint.
- [Curl example](#Curl3)
[]curl --location --request GET 'https://scim1.private.zscaler.com/scim/1/144118148382065427/v2/Users/467697ed-199e-4101-84cc-8dcf5e7a47bd' \
--header 'Authorization: Bearer <Token>
- [Response example](#Response3)
[]{
"schemas": [
"urn:ietf:params:scim:schemas:core:2.0:User",
"urn:ietf:params:scim:schemas:extension:enterprise:2.0:User"
],
"id": "467697ed-199e-4101-84cc-8dcf5e7a47bd",
"externalId": "u43xZ0EZ87qvorWfQLGA",
"nickName": "Test",
"name": {
"formatted": "John Doe kdPrvwZ0hupSS7HSU5yJ@safemarch.com",
"givenName": "John jYdoC2hzU3kMHfxhKcJ5@safemarch.com",
"familyName": "Doe 3qHArSw8z8wnXfBSmAcl@safemarch.com"
},
"userType": "ZPA User",
"displayName": "IcgCl1uDbpjvi4GY8yf4@safemarch.com",
"emails": [
{
"value": "rN0XKUhmy0@safemarch.com}@safemarch.com"
}
],
"active": "true",
"urn:ietf:params:scim:schemas:extension:enterprise:2.0:User": {
"costCenter": "Mohali",
"department": "Cloud and Reliability",
"division": "AFuEwsRyTBVed9RocKWg",
"organization": "BKyX4E@safemarch.com"
},
"userName": "olJSy0vLDb7Ir5fDV0wH@safemarch.com",
"meta": {
"created": "2021-05-03T08:39:01Z",
"lastModified": "2021-05-03T08:39:01Z",
"location": "https://scim1.private.zscaler.com/scim/1/144118148382065427/v2/Users/467697ed-199e-4101-84cc-8dcf5e7a47bd",
"resourceType": "User"
}
}
Older SCIM users can still use a numerical value for the `userId` in the request (e.g., `290277`).
Update a User
To update a user, send a `PUT` request to the following endpoint:
https://{{hostname}}/scim/{{userdb}}/{{idpId}}/v2/Users/{{userId}}
Provide the `{{userId}}`, the Internal User ID found on the SCIM Users page in the Admin Portal, in the request endpoint.
- [Curl example](#Curl4)
[]curl --location -g --request PUT '{{protocol}}://{{hostname}}/scim/{{userdb}}/{{idpId}}/v2/Users/467697ed-199e-4101-84cc-8dcf5e7a47bd' \
--header 'Content-Type: application/json' \
--header 'Authorization: Bearer  <Token> \
--data-raw '{
"schemas": [
"urn:ietf:params:scim:schemas:core:2.0:User",
"urn:ietf:params:scim:schemas:extension:enterprise:2.0:User"
],
"id": "290277",
"externalId": "u43xZ0EZ87qvorWfQLGA",
"nickName": "Test",
"name": {
"formatted": "John Doe kdPrvwZ0hupSS7HSU5yJ@safemarch.com",
"givenName": "John jYdoC2hzU3kMHfxhKcJ5@safemarch.com",
"familyName": "Doe 3qHArSw8z8wnXfBSmAcl@safemarch.com"
},
"userType": "ZPA User",
"displayName": "IcgCl1uDbpjvwei4GY8yf4@safemarch.com",
"emails": [
{
"value": "rN0XKUhmy0@safemarch.com}@safemarch.com"
}
],
"active": "true",
"urn:ietf:params:scim:schemas:extension:enterprise:2.0:User": {
"costCenter": "Mohalisss",
"department": "Cloud and Reliabilityw",
"division": "AFuEwsRyTBVed9RocKWg",
"organization": "BKyX4E@safemarch.com"
},
"userName": "olJSy0vLDb7Ir5fDV0wH@safemarch.com",
}'
- [Update user file example](#Update)
[]{
"schemas": [
"urn:ietf:params:scim:schemas:core:2.0:User",
"urn:ietf:params:scim:schemas:extension:enterprise:2.0:User"
],
"id": "467697ed-199e-4101-84cc-8dcf5e7a47bd",
"externalId": "u43xZ0EZ87qvorWfQLGA",
"nickName": "Example Nickname",
"name": {
"formatted": "John Doe kdPrvwZ0hupSS7HSU5yJ@safemarch.com",
"givenName": "John jYdoC2hzU3kMHfxhKcJ5@safemarch.com",
"familyName": "Doe 3qHArSw8z8wnXfBSmAcl@rsafemarch.com"
},
"userType": "ZPA User",
"displayName": "IcgCl1uDbpjvwei4GY8yf4@safemarch.com",
"emails": [
{
"value": "rN0XKUhmy0@safemarch.com}@safemarch.com"
}
],
"active": "true",
"urn:ietf:params:scim:schemas:extension:enterprise:2.0:User": {
"costCenter": "Mohalisss",
"department": "Cloud and Reliabilityw",
"division": "AFuEwsRyTBVed9RocKWg",
"organization": "BKyX4E@safemarch.com"
},
"userName": "olJSy0vLDb7Ir5fDV0wH@safemarch.com",
"meta": {
"created": "2021-05-03T08:01:40Z",
"lastModified": "2021-05-03T08:01:40Z",
"location": "https://scim1.private.zscaler.com/scim/1/144118148382065427/v2/Users/467697ed-199e-4101-84cc-8dcf5e7a47bd",
"resourceType": "User"
}
}
- [Response example](#Response4)
[]{
"schemas": [
"urn:ietf:params:scim:schemas:core:2.0:User",
"urn:ietf:params:scim:schemas:extension:enterprise:2.0:User"
],
"id": "467697ed-199e-4101-84cc-8dcf5e7a47bd",
"externalId": "u43xZ0EZ87qvorWfQLGA",
"userName": "olJSy0vLDb7Ir5fDV0wH@safemarch.com",
"name": {
"givenName": "John jYdoC2hzU3kMHfxhKcJ5@safemarch.com",
"familyName": "Doe 3qHArSw8z8wnXfBSmAcl@safemarch.com",
"formatted": "John Doe kdPrvwZ0hupSS7HSU5yJ@safemarch.com"
},
"nickName": "Test",
"userType": "ZPA User",
"displayName": "IcgCl1uDbpjvwei4GY8yf4@safemarch.com",
"emails": [
{
"value": "rN0XKUhmy0@safemarch.com}@safemarch.com"
}
],
"active": "true",
"urn:ietf:params:scim:schemas:extension:enterprise:2.0:User": {
"costCenter": "Mohalisss",
"department": "Cloud and Reliabilityw",
"division": "AFuEwsRyTBVed9RocKWg",
"organization": "BKyX4E@safemarch.com"
},
"meta": {
"created": "2021-05-14T18:30:12Z",
"lastModified": "2021-05-17T16:37:40Z",
"location": "https://scim1.private.zscaler.com/scim/1/144118148382065427/v2/Users/467697ed-199e-4101-84cc-8dcf5e7a47bd",
"resourceType": "User"
}
}
If group information is sent as part of the create, update, or partial update for a user request, then the group information is ignored. User-group memberships can only be updated using the create, update, or partial update for group requests. In addition, older SCIM users can still use a numerical value for the `userId` in the request (e.g., `290277`).
Partially Update a User
Add
To partially update a user using the add operation, send a `PATCH` request to the following endpoint:
https://{{hostname}}/scim/{{userdb}}/{{idpId}}/v2/Users/{{userId}}
Provide the `{{userId}}`, the Internal User ID found on the SCIM Users page in the Admin Portal, in the request endpoint.
- [Curl example](#Curl5)
[]curl --location --request PATCH 'https://scim1.private.zscaler.com/scim/1/144118148382065427/v2/Users/467697ed-199e-4101-84cc-8dcf5e7a47bd' \
--header 'Content-Type: application/json' \
--header 'Authorization: Bearer <Token>' \
--data-raw '{
"schemas":
["urn:ietf:params:scim:api:messages:2.0:PatchOp"],
"Operations":[{
"op":"add",
"path":"emails[type eq \"work\"].value",
"value":"babs@work.org"
}]
}'
- [Partial update user file example](#Partial)
[]{
"schemas":
["urn:ietf:params:scim:api:messages:2.0:PatchOp"],
"Operations":[{
"op":"add",
"path":"emails[type eq \"work\"].value",
"value":"babs@work.org"
}]
}
- [Response example](#Response5)
[]{
"schemas": [
"urn:ietf:params:scim:schemas:core:2.0:User",
"urn:ietf:params:scim:schemas:extension:enterprise:2.0:User"
],
"id": "467697ed-199e-4101-84cc-8dcf5e7a47bd",
"externalId": "u43xZ0EZ87qvorWfQLGA",
"userName": "test@safemarch.com",
"name": {
"givenName": "John jYdoC2hzU3kMHfxhKcJ5@safemarch.com",
"familyName": "Doe 3qHArSw8z8wnXfBSmAcl@safemarch.com",
"formatted": "John Doe kdPrvwZ0hupSS7HSU5yJ@safemarch.com"
},
"nickName": "Test",
"userType": "ZPA User",
"displayName": "IcgCl1uDbpjvi4GY8yf4@safemarch.com",
"emails": [
{
"value": "babs@work.org"
},
{
"value": "rN0XKUhmy0@safemarch.com}@safemarch.com"
}
],
"active": "true",
"urn:ietf:params:scim:schemas:extension:enterprise:2.0:User": {
"costCenter": "Mohali",
"department": "Cloud and Reliability",
"division": "AFuEwsRyTBVed9RocKWg",
"organization": "BKyX4E@safemarch.com"
},
"meta": {
"created": "2021-05-14T18:31:27Z",
"lastModified": "2021-06-07T19:58:09Z",
"location": "https://scim1.private.zscaler.com/scim/1/144118148382065427/v2/Users/467697ed-199e-4101-84cc-8dcf5e7a47bd",
"resourceType": "User"
}
}
Older SCIM users can still use a numerical value for the `userId` in the request (e.g., `290277`).
Replace
To partially update a user using the replace operation, send a `PATCH` request to the following endpoint:
https://{{hostname}}/scim/{{userdb}}/{{idpId}}/v2/Users/{{userId}}
Provide the `{{userId}}`, the Internal User ID found on the SCIM Users page of the Admin Portal, in the request endpoint.
- [Curl example](#Curl6)
[]curl --location --request PATCH 'https://scim1.private.zscaler.com/scim/1/144118148382065427/v2/Users/467697ed-199e-4101-84cc-8dcf5e7a47bd' \
--header 'Content-Type: application/json' \
--header 'Authorization: Bearer <Token>' \
--data-raw '{
"schemas":
["urn:ietf:params:scim:api:messages:2.0:PatchOp"],
"Operations":[{
"op":"replace",
"path":"name.familyName",
"value": "Doe"
}]
}'
- [Partial update user file example](#Partial2)
[]{
"schemas":
["urn:ietf:params:scim:api:messages:2.0:PatchOp"],
"Operations":[{
"op":"replace",
"path":"name.familyName",
"value": "Doe"
}]
}
- [Response example](#Response6)
[]{
"schemas": [
"urn:ietf:params:scim:schemas:core:2.0:User",
"urn:ietf:params:scim:schemas:extension:enterprise:2.0:User"
],
"id": "467697ed-199e-4101-84cc-8dcf5e7a47bd",
"externalId": "u43xZ0EZ87qvorWfQLGA",
"userName": "test@zscaler.com",
"name": {
"givenName": "John jYdoC2hzU3kMHfxhKcJ5@safemarch.com",
"familyName": "Doe",
"formatted": "John Doe kdPrvwZ0hupSS7HSU5yJ@safemarch.com"
},
"nickName": "Test",
"userType": "ZPA User",
"displayName": "IcgCl1uDbpjvi4GY8yf4@safemarch.com",
"emails": [
{
"value": "babs@work.org"
},
{
"value": "rN0XKUhmy0@safemarch.com}@safemarch.com"
}
],
"active": "true",
"urn:ietf:params:scim:schemas:extension:enterprise:2.0:User": {
"costCenter": "Mohali",
"department": "Cloud and Reliability",
"division": "AFuEwsRyTBVed9RocKWg",
"organization": "BKyX4E@safemarch.com"
},
"meta": {
"created": "2021-05-14T18:31:27Z",
"lastModified": "2021-06-07T20:12:04Z",
"location": "https://scim1.private.zscaler.com/scim/1/144118148382065427/v2/Users/467697ed-199e-4101-84cc-8dcf5e7a47bd",
"resourceType": "User"
}
}
Older SCIM users can still use a numerical value for the `userId` in the request (e.g., `290277`).
Remove
To partially update a user using the remove operation, send a `PATCH` request to the following endpoint:
https://{{hostname}}/scim/{{userdb}}/{{idpId}}/v2/Users/{{userId}}
Provide the `{{userId}}`, the Internal User ID found on the SCIM Users page of the Admin Portal, in the request endpoint.
- [Curl example](#Curl7)
[]curl --location --request PATCH 'https://scim1.private.zscaler.com/scim/1/144118148382065427/v2/Users/467697ed-199e-4101-84cc-8dcf5e7a47bd' \
--header 'Content-Type: application/json' \
--header 'Authorization: Bearer <Token>' \
--data-raw '{
"schemas":
["urn:ietf:params:scim:api:messages:2.0:PatchOp"],
"Operations":[{
"op":"remove",
"path":"emails"
}]
}'
- [Partial update user example](#Partial3)
[]{
"schemas":
["urn:ietf:params:scim:api:messages:2.0:PatchOp"],
"Operations":[{
"op":"remove",
"path":"emails"
}]
}
- [Response example](#Response7)
[]{
"schemas": [
"urn:ietf:params:scim:schemas:core:2.0:User",
"urn:ietf:params:scim:schemas:extension:enterprise:2.0:User"
],
"id": "467697ed-199e-4101-84cc-8dcf5e7a47bd",
"externalId": "u43xZ0EZ87qvorWfQLGA",
"nickName": "Example nickname",
"name": {
"formatted": "John Doe kdPrvwZ0hupSS7HSU5yJ@safemarch.com",
"givenName": "John jYdoC2hzU3kMHfxhKcJ5@safemarch.com",
"familyName": "Doe"
},
"userType": "ZPA User",
"displayName": "IcgCl1uDbpjvi4GY8yf4@safemarch.com",
"active": "true",
"urn:ietf:params:scim:schemas:extension:enterprise:2.0:User": {
"costCenter": "Mohali",
"department": "Cloud and Reliability",
"division": "AFuEwsRyTBVed9RocKWg",
"organization": "BKyX4E@safemarch.com"
},
"userName": "test@safemarch.com",
"meta": {
"created": "2021-05-14T18:31:27Z",
"lastModified": "2021-06-07T20:39:18Z",
"location": "https://scim1.private.zscaler.com/scim/1/144118148382065427/v2/Users/467697ed-199e-4101-84cc-8dcf5e7a47bd",
"resourceType": "User"
}
}
If group information is sent as part of the create, update, or partial update for a user request, then the group information is ignored. User-group memberships can only be updated using the create, update, or partial update for group requests. In addition, older SCIM users can still use a numerical value for the `userId` in the request (e.g., `290277`).
Delete a User
To delete a user, send a `DELETE` request to the following endpoint:
https://{{hostname}}/scim/{{userdb}}/{{idpId}}/v2/Users/{{userId}}
Provide the `{{userId}}`, the Internal User ID found on the SCIM Users page of the Admin Portal, in the request endpoint.
- [Curl example](#Curl8)
[]curl --location --request DELETE 'https://scim1.private.zscaler.com/scim/1/144118148382065427/v2/Users/467697ed-199e-4101-84cc-8dcf5e7a47bd' \
--header 'Authorization: Bearer <Token>\
--data-raw ''
The server responds with `204 No Content` upon successful operation.
Older SCIM users can still use a numerical value for the `userId` in the request (e.g., `290277`).
Fetch All Groups
To fetch all groups, send a `GET` request to the following endpoint:
https://{{hostname}}/scim/{{userdb}}/{{idpId}}/v2/Groups
Users in a group are not sent by the endpoint to fetch all groups and are only allowed in the endpoint to fetch a group by ID. If present, the `excludeAttributes` query parameter is honored and the excluded attributes are not sent in the response body.
- [Curl example](#Curl9)
[]curl --location --request GET 'https://scim1.private.zscaler.com/scim/1/144118148382065427/v2/Groups' \
--header 'Authorization: Bearer <Token>'
- [Response example](#Response8)
[]{
"schemas": [
"urn:ietf:params:scim:api:messages:2.0:ListResponse"
],
"startIndex": 1,
"totalResults": 5,
"itemsPerPage": 10,
"Resources": [
{
"schemas": [
"urn:ietf:params:scim:schemas:core:2.0:Group"
],
"id": "67979",
"externalId": "ExampleTestGrp",
"displayName": "ExampleTestGrpName",
"meta": {
"created": "2022-02-08T09:37:44Z",
"lastModified": "2022-02-18T13:37:43Z",
"location": "http://scim1.private.zscaler.com/scim/1/144118148382065427/v2/Groups/67979",
"resourceType": "Group"
}
},
{
"schemas": [
"urn:ietf:params:scim:schemas:core:2.0:Group"
],
"id": "68647",
"externalId": "ExampleTestGrp2",
"displayName": "ExampleTestGrpName2",
"meta": {
"created": "2022-02-18T10:55:06Z",
"lastModified": "2022-02-18T14:57:54Z",
"http://scim1.private.zscaler.com/scim/1/144118148382065427/v2/Groups/68647",
"resourceType": "Group"
}
},
{
"schemas": [
"urn:ietf:params:scim:schemas:core:2.0:Group"
],
"id": "68857",
"externalId": "ExampleTestGrp",
"displayName": "ExampleTestGrp3",
"meta": {
"created": "2022-02-22T04:18:42Z",
"lastModified": "2022-02-23T09:29:50Z",
"http://scim1.private.zscaler.com/scim/1/144118148382065427/v2/Groups/68857",
"resourceType": "Group"
}
},
{
"schemas": [
"urn:ietf:params:scim:schemas:core:2.0:Group"
],
"id": "68889",
"externalId": "ExampleTestGrp",
"displayName": "ExampleTestGrp4",
"meta": {
"created": "2022-02-23T09:20:09Z",
"lastModified": "2022-02-24T14:21:21Z",
"http://scim1.private.zscaler.com/scim/1/144118148382065427/v2/Groups/68889",
"resourceType": "Group"
}
},
{
"schemas": [
"urn:ietf:params:scim:schemas:core:2.0:Group"
],
"id": "61877",
"externalId": "ExampleTestGrp3",
"displayName": "ExampleTestGrpName5",
"meta": {
"created": "2022-01-26T05:24:03Z",
"lastModified": "2022-02-02T15:02:54Z",
"http://scim1.private.zscaler.com/scim/1/144118148382065427/v2/Groups/61877",
"resourceType": "Group"
}
}
]
}
Create a Group
To create a group, send a `POST` request to the following endpoint:
https://{{hostname}}/scim/{{userdb}}/{{idpId}}/v2/Groups
- [Curl example](#Curl10)
[]curl --location --request POST 'https://scim1.private.zscaler.com/scim/1/144118148382065427/v2/Groups' \
--header 'Content-Type: application/json' \
--header 'Authorization: Bearer <Token>' \
--data-raw '{
"schemas": ["urn:ietf:params:scim:schemas:core:2.0:Group"],
"displayName": "Example Name",
"externalId":"grp100",
"members": [
{
"value": "2541841",
"$ref":
"https://example.com/v2/Groups/c3a26dd3-27a0-4dec-a2ac-ce211e105f97",
"type": "User"
}
]
}'
- [New group file example](#New2)
[]{
"schemas": ["urn:ietf:params:scim:schemas:core:2.0:Group"],
"displayName": "Example Name",
"externalId":"grp100",
"members": [
{
"value": "2541841",
"$ref":
"https://example.com/v2/Groups/c3a26dd3-27a0-4dec-a2ac-ce211e105f97",
"type": "User"
}
]
}
}
- [Response example](#Response9)
[]{
"schemas": [
"urn:ietf:params:scim:schemas:core:2.0:Group"
],
"id": "467697ed-199e-4101-84cc-8dcf5e7a47bd",
"externalId": "grp100",
"displayName": "Example Name",
"members": [
{
"value": "2541841"
}
],
"meta": {
"created": "2021-05-17T16:31:47Z",
"lastModified": "2021-05-17T16:31:47Z",
"location": "https://scim1.private.zscaler.com/scim/1/144118148382065427/v2/Groups/467697ed-199e-4101-84cc-8dcf5e7a47bd",
"resourceType": "Group"
}
}
Fetch a Group by ID
To fetch a group by ID, send a `GET` request to the following endpoint:
https://{{hostname}}/scim/{{userdb}}/{{idpId}}/v2/Groups/{{groupId}}
Provide the `{{groupId}}`, the Internal Group ID found on the SCIM Groups page of the Admin Portal, in the request endpoint.
- [Curl example](#Curl11)
[]curl --location --request GET 'https://scim1.private.zscaler.com/scim/1/144118148382065427/v2/Groups/467697ed-199e-4101-84cc-8dcf5e7a47bd' \
--header 'Authorization: Bearer <Token>'
- [Response example](#Response10)
[]{
"schemas": [
"urn:ietf:params:scim:schemas:core:2.0:Group"
],
"id": "467697ed-199e-4101-84cc-8dcf5e7a47bd",
"externalId": "grp100",
"displayName": "Example Name",
"meta": {
"created": "2021-05-17T16:31:47Z",
"lastModified": "2021-05-17T16:34:43Z",
"location": "https://scim1.private.zscaler.com/scim/1/144118148382065427/v2/Groups/467697ed-199e-4101-84cc-8dcf5e7a47bd",
"resourceType": "Group"
}
}
Older SCIM groups can still use a numerical value for the `groupId` in the request (e.g., `290277`).
Fetch Groups with Pagination and Sort
To fetch groups with pagination and sort, send a `GET` request to the following endpoint:
https://{{hostname}}/scim/{{userdb}}/{{idpId}}/v2/Groups?startIndex=1&count=10&sortBy=displayName&sortOrder=descending
- [Curl example](#Curl12)
[]curl --location --request GET 'https://scim1.private.zscaler.com/scim/1/144118148382065427/v2/Groups?startIndex=1&count=10&sortBy=displayName&sortOrder=descending' \
--header 'Authorization: Bearer <Token>'
- [Response example](#Response11)
[]{
"schemas": [
"urn:ietf:params:scim:api:messages:2.0:ListResponse"
],
"startIndex": 1,
"totalResults": 2,
"itemsPerPage": 10,
"Resources": [
{
"schemas": [
"urn:ietf:params:scim:schemas:core:2.0:Group"
],
"id": "205717",
"externalId": "grp100",
"displayName": "Exammple Name",
"meta": {
"created": "2021-05-14T20:59:04Z",
"lastModified": "2021-05-14T20:59:54Z",
"location": "https://scim1.private.zscaler.com/scim/1/144118148382065427/v2/Groups/205717",
"resourceType": "Group"
}
},
{
"schemas": [
"urn:ietf:params:scim:schemas:core:2.0:Group"
],
"id": "205808",
"externalId": "grp-3",
"displayName": "Example Name33",
"meta": {
"created": "2021-05-17T16:31:47Z",
"lastModified": "2021-06-03T20:31:02Z",
"location": "https://scim1.private.zscaler.com/scim/1/144118148382065427/v2/Groups/205808",
"resourceType": "Group"
}
}
]
}
Update a Group
To update a group, send a `PUT` request to the following endpoint:
https://{{hostname}}/scim/{{userdb}}/{{idpId}}/v2/Groups/{{groupId}}
Provide the `{{groupId}}`, the Internal Group ID found on the SCIM Groups page of the Admin Portal, in the request endpoint.
- [Curl example](#Curl13)
[]curl --location --request PUT 'https://scim1.private.zscaler.com/scim/1/144118148382065427/v2/Groups/467697ed-199e-4101-84cc-8dcf5e7a47bd' \
--header 'Content-Type: application/json' \
--header 'Authorization: Bearer <Token>' \
--data-raw '{
"schemas": ["urn:ietf:params:scim:schemas:core:2.0:Group"],
"externalId":"grp-3"
}'
- [Update group file example](#Update2)
[]{
"schemas": ["urn:ietf:params:scim:schemas:core:2.0:Group"],
"externalId":"grp-33"
}
- [Response example](#Response12)
[]{
"schemas": [
"urn:ietf:params:scim:schemas:core:2.0:Group"
],
"id": "467697ed-199e-4101-84cc-8dcf5e7a47bd",
"externalId": "grp-33",
"displayName": "Example Name10",
"members": [
{
"value": "2541841"
}
],
"meta": {
"created": "2021-06-07T20:50:42Z",
"lastModified": "2021-06-07T21:32:35Z",
"location": "https://scim1.private.zscaler.com/scim/1/144118148382065427/v2/Groups/467697ed-199e-4101-84cc-8dcf5e7a47bd",
"resourceType": "Group"
}
}
Older SCIM groups can still use a numerical value for the `groupId` in the request (e.g., `290277`).
Partially Update a Group
Add
To partially update a group using the add operation, send a `PATCH` request to the following endpoint:
https://{{hostname}}/scim/{{userdb}}/{{idpId}}/v2/Groups/{{groupId}}
Provide the `{{groupId}}`, the Internal Group ID found on the SCIM Groups page of the Admin Portal, in the request endpoint.
- [Curl example](#Curl14)
[]curl --location --request PATCH 'https://scim1.private.zscaler.com/scim/1/144118148382065427/v2/Groups/467697ed-199e-4101-84cc-8dcf5e7a47bd' \
--header 'Content-Type: application/json' \
--header 'Authorization: Bearer <Token>' \
--data-raw '{
"schemas":
["urn:ietf:params:scim:api:messages:2.0:PatchOp"],
"Operations":[{
"op":"add",
"path":"members",
"value": [
{
"value": "2541841",
"$ref":
""https://scim1.private.zscaler.com/scim/1/144118148382065427/v2/Users/2541841",
"type": "User"
}
]
}]
}'
- [Partial update file example](#Partial4)
[]{
"schemas":
["urn:ietf:params:scim:api:messages:2.0:PatchOp"],
"Operations":[{
"op":"add",
"path":"members",
"value": [
{
"value": "2541841",
"$ref":
""https://scim1.private.zscaler.com/scim/1/144118148382065427/v2/Users/2541841",
"type": "User"
}
]
}]
}
The server responds with `204 No Content` upon successful operation.
Older SCIM groups can still use a numerical value for the `groupId` in the request (e.g., `290277`).
Replace
To partially update a group using the replace operation, send a `PATCH` request to the following endpoint:
https://{{hostname}}/scim/{{userdb}}/{{idpId}}/v2/Groups/{{groupId}}
Provide the `{{groupId}}`, the Internal Group ID found on the SCIM Groups page of the Admin Portal, in the request endpoint.
- [Curl example](#Curl15)
[]curl --location --request PATCH 'https://scim1.private.zscaler.com/scim/1/144118148382065427/v2/Groups/467697ed-199e-4101-84cc-8dcf5e7a47bd' \
--header 'Content-Type: application/json' \
--header 'Authorization: Bearer <Token>' \
--data-raw '{
"schemas":
["urn:ietf:params:scim:api:messages:2.0:PatchOp"],
"Operations":[{
"op":"replace",
"path":"members",
"value":[
{
"value": "2541841",
"$ref":
""https://scim1.private.zscaler.com/scim/1/144118148382065427/v2/Users/2541841",
"type": "User"
}
]
}]
}'
- [Partial update file example](#Partial5)
[]{
"schemas":
["urn:ietf:params:scim:api:messages:2.0:PatchOp"],
"Operations":[{
"op":"replace",
"path":"members",
"value":[
{
"value": "2541841",
"$ref":
""https://scim1.private.zscaler.com/scim/1/144118148382065427/v2/Users/2541841",
"type": "User"
}
]
}]
}
The server responds with `204 No Content` upon successful operation.
Older SCIM groups can still use a numerical value for the `groupId` in the request (e.g., `290277`).
Remove
To partially update a group using the remove operation, send a `PATCH` request to the following endpoint:
https://{{hostname}}/scim/{{userdb}}/{{idpId}}/v2/Groups/{{groupId}}
Provide the `{{groupId}}`, the Internal Group ID found on the SCIM Groups page of the Admin Portal, in the request endpoint.
- [Curl example](#Curl16)
[]curl --location --request PATCH 'https://scim1.private.zscaler.com/scim/1/144118148382065427/v2/Groups/467697ed-199e-4101-84cc-8dcf5e7a47bd' \
--header 'Content-Type: application/json' \
--header 'Authorization: Bearer <Token>' \
--data-raw '{
"schemas":
["urn:ietf:params:scim:api:messages:2.0:PatchOp"],
"Operations":[{
"op":"remove",
"path":"members"
}]
}'
- [Partial update file example](#Partial6)
[]{
"schemas":
["urn:ietf:params:scim:api:messages:2.0:PatchOp"],
"Operations":[{
"op":"remove",
"path":"members"
}]
}
The server responds with `204 No Content` upon successful operation.
Older SCIM groups can still use a numerical value for the `groupId` in the request (e.g., `290277`).
Delete a Group
To delete a group, send a `DELETE` request to the following endpoint:
https://{{hostname}}/scim/{{userdb}}/{{idpId}}/v2/Groups/{{groupId}}
Provide the `{{groupId}}`, the Internal Group ID found on the SCIM Groups page of the Admin Portal, in the request endpoint.
- [Curl example](#Curl17)
[]curl --location --request DELETE 'https://scim1.private.zscaler.com/scim/1/144118148382065427/v2/Groups/467697ed-199e-4101-84cc-8dcf5e7a47bd' \
--header 'Authorization: Bearer <Token>' \
--data-raw ''
The server responds with `204 No Content` upon successful operation.
Older SCIM groups can still use a numerical value for the `groupId` in the request (e.g., `290277`).
Field Descriptions
The following table includes descriptions of available fields you can use for the SCIM API use cases:
| Attribute | Description | Required | Value |
| --------- | ----------- | -------- | ----- |
| startIndex | Indicates the beginning index and count for the resources on the page | No | Integer |
| count | Indicates the desired maximum number of query results per page | No | Integer |