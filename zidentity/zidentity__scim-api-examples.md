# SCIM API Examples
Source: https://help.zscaler.com/zidentity/scim-api-examples
PDF: https://help.zscaler.com/pdf/com/en/1499466.pdf

Using SCIM operations enables you to perform operations such as creating and deleting users and groups. To do this, you must enable SCIM-based provisioning and have your Base URL and Bearer Token. Most API calls to Zscaler SCIM servers require the Bearer Token for authentication. However, there are several API calls (e.g., `/Schemas`, `/ServiceProviderConfig`, and `/ResourceTypes`) that do not require authentication, as they are informational for the SCIM server and not particular to any organization.
Zscaler SCIM servers have a rate limit of 50 requests per second. To avoid retries, configure your application to comply with this.
Fetching All Users
To fetch all users, use the following operations:
**Request**
`GET <Base URL>/Users`
**Curl example**
`curl -v -k <Base URL>/Users -H "Authorization: Bearer <Bearer Token>"`
**Response example**
`{
"schemas": [
"urn:ietf:params:scim:api:messages:2.0:ListResponse"
],
"totalResults": 5,
"startIndex": 1,
"Resources": [
{
"emails": [
{
"type": "work",
"value": "user1@zslog.in",
"primary": true
}
],
"phoneNumbers": [],
"meta": {
"location": "https://<subdomain>.zslogin.net/scim/h1gkrvmic07od/Users/ihgkrqp5tg7o5",
"resourceType": "User"
},
"displayName": "zzzz yyyy",
"name": {
"givenName": "zzzz",
"familyName": "yyyy"
},
"preferredLanguage": "English (US)",
"active": true,
"groups": [
{
"display": "Zscaler Global Administrators",
"value": "i9gkrhr5m07mo",
"$ref": "https://<subdomain>.zslogin.net/scim/h1gkrvmic07od/Groups/i9gkrhr5m07mo"
},
{
"display": "Dynamic Group Registered Domains",
"value": "i9hahu4kq06h8",
"$ref": "https://<subdomain>.zslogin.net/scim/h1gkrvmic07od/Groups/i9hahu4kq06h8"
},
{
"display": "Dynamic Group Administrators",
"value": "i9hahu4kq06h9",
"$ref": "https://<subdomain>.zslogin.net/scim/h1gkrvmic07od/Groups/i9hahu4kq06h9"
}
],
"id": "ihgkrqp5tg7o5",
"userName": "admin@<subdomain>.zslogin.net"
},
{
"emails": [
{
"type": "work",
"value": "zzzzz@zslog.in",
"primary": true
}
],
"phoneNumbers": [],
"meta":
{
"location": "https://<subdomain>.zslogin.net/scim/h1gkrvmic07od/Users/ihgkrup2eg7oc",
"resourceType": "User"
},
"displayName": "yyyyy xxxxx",
"name":
{
"givenName": "yyyyy",
"familyName": "xxxxx"
},
"preferredLanguage": "English (US)",
"active": true,
"groups": [
{
"display": "Zscaler Global Administrators",
"value": "i9gkrhr5m07mo",
"$ref": "https://<subdomain>.zslogin.net/scim/h1gkrvmic07od/Groups/i9gkrhr5m07mo"
},
{
"display": "Dynamic Group Registered Domains",
"value": "i9hahu4kq06h8",
"$ref": "https://<subdomain>.zslogin.net/scim/h1gkrvmic07od/Groups/i9hahu4kq06h8"
},
{
"display": "Dynamic Group Administrators",
"value": "i9hahu4kq06h9",
"$ref": "https://<subdomain>.zslogin.net/scim/h1gkrvmic07od/Groups/i9hahu4kq06h9"
}
],
"id": "ihgkrup2eg7oc",
"userName": "yyyyy@<subdomain>.zslogin.net"
},
{
"emails": [
{
"type": "work",
"value": "__remote_assistance@<subdomain>.zslogin.net",
"primary": true
}
],
"phoneNumbers": [],
"meta":
{
"location": "https://<subdomain>.zslogin.net/scim/h1gkrvmic07od/Users/ihhahu4dag7tr",
"resourceType": "User"
},
"displayName": "Remote Assistance",
"name":
{
"givenName": "Remote",
"familyName": "Assistance"
},
"preferredLanguage": "English (US)",
"active": true,
"groups": [
{
"display": "Dynamic Group Registered Domains",
"value": "i9hahu4kq06h8",
"$ref": "https://<subdomain>.zslogin.net/scim/h1gkrvmic07od/Groups/i9hahu4kq06h8"
}
],
"id": "ihhahu4dag7tr",
"userName": "__remote_assistance@<subdomain>.zslogin.net"
},
{
"emails": [
{
"type": "work",
"value": "xyyy@zslog.in",
"primary": true
}
],
"phoneNumbers": [],
"meta":
{
"location": "https://<subdomain>.zslogin.net/scim/h1gkrvmic07od/Users/ihgms732n076b",
"resourceType": "User"
},
"displayName": "xxxx yyyy",
"name":
{
"givenName": "xxxx",
"familyName": "yyyy"
},
"preferredLanguage": "English (US)",
"active": true,
"groups": [
{
"display": "Zscaler Global Administrators",
"value": "i9gkrhr5m07mo",
"$ref": "https://<subdomain>.zslogin.net/scim/h1gkrvmic07od/Groups/i9gkrhr5m07mo"
},
{
"display": "Dynamic Group Registered Domains",
"value": "i9hahu4kq06h8",
"$ref": "https://<subdomain>.zslogin.net/scim/h1gkrvmic07od/Groups/i9hahu4kq06h8"
},
{
"display": "Dynamic Group Administrat*ors",
"value": "i9hahu4kq06h9",
"$ref": "https://<subdomain>.zslogin.net/scim/h1gkrvmic07od/Groups/i9hahu4kq06h9"
}
],
"id": "ihgms732n076b",
"userName": "xxxxx@<subdomain>.zslogin.net"
},
{
"emails": [
{
"type": "work",
"value": "user2@zslog1.<domain>.com",
"primary": true
}
],
"phoneNumbers": [],
"meta":
{
"location": "https://<subdomain>.zslogin.net/scim/h1gkrvmic07od/Users/ihgkt6bro03do",
"resourceType": "User"
},
"displayName": "user2",
"name":
{
"givenName": "user",
"familyName": "2"
},
"externalId": "user2",
"active": true,
"groups": [
{
"display": "ZSLogin - HSSGEEK - SAML2",
"value": "i9gkt6c6003dp",
"$ref": "https://<subdomain>.zslogin.net/scim/h1gkrvmic07od/Groups/i9gkt6c6003dp"
},
{
"display": "Dynamic Group Registered Domains",
"value": "i9hahu4kq06h8",
"$ref": "https://<subdomain>.zslogin.net/scim/h1gkrvmic07od/Groups/i9hahu4kq06h8"
}
],
"id": "ihgkt6bro03do",
"userName": "user2@zlog1.<domain>.com"
}
],
"itemsPerPage": 100
}`
Creating a User
To create a user, use the following operations:
**Request**
`POST <Base URL>/Users`
**Curl example**
`curl -v -k <Base URL>/Users -d @create_scim_user.json -H "Authorization: Bearer <Bearer Token>" -H "Content-Type: application/scim+json"`
Where `create_scim_user.json` is a file containing the following information about the user in the JSON format.
**New user file example**
`{
"schemas": [
"urn:ietf:params:scim:schemas:core:2.0:User",
"urn:ietf:params:scim:schemas:extension:enterprise:2.0:User"
],
"externalId": "0a21f0f2-8d2a-4f8e-bf98-7363c4aed4ef",
"userName": "test@zslog.in",
"displayName": "Test User",
"active": true,
"emails": [
{
"primary": true,
"type": "work",
"value": "test@zslog.in"
}
],
"meta": {
"resourceType": "User"
},
"name": {
"formatted": "givenName familyName",
"familyName": "Test",
"givenName": "User"
},
"roles": []
}`
**Response example**
`{
"schemas": [
"urn:ietf:params:scim:schemas:core:2.0:User",
"urn:ietf:params:scim:schemas:extension:enterprise:2.0:User"
],
"externalId": "0a21f0f2-8d2a-4f8e-bf98-7363c4aed4ef",
"userName": "test@zslog.in",
"displayName": "Test User",
"active": true,
"emails": [
{
"primary": true,
"type": "work",
"value": "test@zslog.in"
}
],
"meta": {
"resourceType": "User"
},
"name": {
"formatted": "givenName familyName",
"familyName": "Test",
"givenName": "User"
},
"roles": []
}`
Updating a User's Display Name, Email, and Department
To update user information, use the following operations:
**Request**
`PUT <Base URL>/Users/{UserID} `
or
`PATCH <Base URL>/Users/{UserID}`
**Curl example**
In this example, the PUT request is used.
`curl -X PUT -v -k <Base URL>/Users/{UserID} -d @updated_user_file_example.json -H "Authorization: Bearer <Bearer Token>"-H "Content-Type: application/scim+json"`
**Updated user file example**
`{
"schemas": [
"urn:ietf:params:scim:api:messages:2.0:PatchOp"
],
"Operations": [
{
"op": "Replace",
"path": "emails",
"value": [
{
"value": "user.4@authpm.net",
"type": "work",
"primary": true
},
{
"value": "user.4@authpm.net",
"type": "home"
}
]
},
{
"op": "Replace",
"path": "urn:ietf:params:scim:schemas:extension:enterprise:2.0:User:department",
"value": "departmentPM"
},
{
"op": "Replace",
"path": "displayName",
"value": "user.4"
}
]
}`
**Response example**
`{
“schemas”: [
“urn:ietf:params:scim:schemas:core:2.0:User”,
“urn:ietf:params:scim:schemas:extension:enterprise:2.0:User”,
“urn:ietf:params:scim:schemas:extension:zscaler:1.0:User”
],
“addresses”: [
{
“locality”: “Newyork”
}
],
“phoneNumbers”: [
{
“type”: “work”,
“value”: “555-555-5555”
},
{
“type”: “mobile”,
“value”: “555-555-4444”
}
],
“externalId”: “702284",
“active”: true,
“groups”: [
{
“display”: “Zscaler Registered Domains”,
“value”: “i9cdic4n0034r”,
“$ref”: “http://<subdomain>.zslogin.net:9001/scim/h1a3pk1s502n8/Groups/i9cdic4n0034r”
}
],
“title”: “Tour Guide”,
“urn:ietf:params:scim:schemas:extension:zscaler:1.0:User”:
{
“city”: “Newyork”
},
“emails”: [
{
“type”: “work”,
“value”: “user.4@authpm.net”,
“primary”: true
},
{
“type”: “home”,
“value”: “user.4@authpm.net”,
“primary”: false
}
],
“meta”:
{
“location”: “http://oidp-test.zslogin.net:9001/scim/h1a3pk1s502n8/Users/ihf681vk1g3ok”,
“resourceType”: “User”
},
“displayName”: “user.4”,
“name”:
{
“givenName”: “user60",
“familyName”: “test”
},
“preferredLanguage”: “en-us”,
“urn:ietf:params:scim:schemas:extension:enterprise:2.0:User”:
{
“manager”:
{
“value”: “managerThrasdfsd11111222222eeOnePatchasdffd”
},
“department”: “departmentPM”
},
“id”: “ihf681vk1g3ok”,
“userName”: “forestcamp18@<domain>.com”`
**Create a Group with Members**
`curl -v -k <Base URL>/Groups -d @create_scim_group.txt  -H "Authorization: Bearer <Bearer Token>" -H "Content-Type: application/scim+json"`
**Sample new group file**
`{ "schemas": [ "urn:ietf:params:scim:schemas:core:2.0:Group" ], "externalId": "abcde", "displayName":"SCIM GROUP", "members": [ { "value":"{UserID}" } ] }`
**Example response**
`{
"schemas": [
"urn:ietf:params:scim:schemas:core:2.0:Group"
],
"meta": {
"location": "<Base URL>/Groups/{GroupID}",
"resourceType": "Group"
},
"displayName": "SCIM GROUP",
"members": [
{
"display": "user1",
"value": "{UserID}",
"$ref": "<Base URL>/Users/{UserID}"
}
],
"externalId": "test",
"id": "{GroupID}"
}`
Updating a Group With a New Member
To update a group, use the following operations:
**Request**
`PUT /Groups/{GroupID} `
or
` PATCH /Groups/{GroupID}`
**Curl example**
In this example, the PUT request is used.
`curl -v -k  -X PATCH <Base URL>/Groups/{GroupID} -d @patch_scim_group_1.txt -H "Authorization: Bearer <Bearer Token>" -H "Content-Type: application/json-patch+json"`
**Sample updated group file**
`{
"schemas": [
"urn:ietf:params:scim:api:messages:2.0:PatchOp"
],
"Operations": [
{
"op": "Add",
"path": "members",
"value": [
{
"$ref": null,
"value": "{UserID}"
}
]
}
]
}`
**Response**
The server responds with `204 - No Content` upon successful operation.
Deleting a User
To delete a user, use the following operations:
**Request**
`DELETE /Users/{UserID}`
**Curl example**
`curl -X DELETE -v -k  -H "Authorization: Bearer <Bearer Token>" <Base URL>/Users/{UserID}`
**Response**
The server responds with `204 - No Content` upon successful operation.