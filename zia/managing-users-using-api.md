# Managing Users Using API
Source: https://help.zscaler.com/zia/managing-users-using-api
PDF: https://help.zscaler.com/pdf/com/en/1400426.pdf

Typically, organizations synchronize users from Microsoft Active Directory (AD) or some other identity provider (IdP). However, if you create a user by sending a POST request to `/users`, the user's information is stored in Zscaler's hosted user database, and is not synchronized back to the IdP (e.g., AD). So, sending a GET request to `/users` returns non-hosted users (e.g., users synchronized from AD) but you cannot perform an action (i.e., updating or deleting) on those user IDs. To learn more, see [About the Hosted User Database](/zia/about-hosted-user-database). For detailed information about the API endpoints involved in managing users, see User Management in the [API Reference](/zia/user-management).
Zscaler recommends adopting the following best practices when managing users:
- Periodically iterate through the list of users, resetting passwords to random values.
- Reassign inactive user accounts to new users via password reset to avoid continually creating new users. Constantly creating new users can degrade performance over time.
To learn more, see [Managing Users, Groups, and Departments](/zia/documentation-knowledgebase/authenticating-and-managing-users/managing-users-groups-and-departments).
Admins who have permission to manage other admins can only create, edit, or view admins that have an equal or lower rank. To learn more, see [About Admin Rank](/zia/about-admin-rank). So when you retrieve, create, update, or delete admin credentials via the API, it's only for admins of an equal or lower rank to yours.
Getting a List of Users
To get a list of users, send a GET request to `/users`. You can use the following parameters to:
- Specify a page offset (`page`).
- Specify the page length (`pageSize`), up to a limit of 10,000.
- Sort users alphabetically by `name`.
- Request users that belong to a specific `group`.
- Request users that belong to a specific `dept`.
For example, in Python:
conn.request("GET", "/api/v1/users?page=1&pageSize=100", headers=headers)
conn.request("GET", "/api/v1/users?name=auto", headers=headers)
conn.request("GET", "/api/v1/users?group=guest-wifi", headers=headers)
conn.request("GET", "/api/v1/users?dept=testdept", headers=headers)
Adding a User
To add a user:
- Send a POST request to /users and use the following key-value pairs in the Body:
-
`name`: A string (e.g., "`guest1234`").
The `name` field allows values containing UTF-8 characters up to a maximum of 127 characters.
-
`email`: A string (e.g., "`guest1234@antest.com`").
The `email` field allows values of alphanumeric characters and certain special characters up to a maximum of 127 characters. The use of the `@` symbol is mandatory. This field corresponds to the User ID (also referred to as Login ID) field in the UI. However, the data validation in the UI uses different constraints.
- `groups`: An array of key-value pairs containing the `id` and `name` of one or more groups to which the user belongs. For example:
"groups": [
{
"id": 75457,
"name": "guest-wifi"
}
],
- `department`: An array of name value pairs containing `id `and `name` of the unique department to which the user belongs.
- `comments`: A string (e.g., "`guest wi-fi user`").
- `adminUser`: A Boolean that enables (`true`) or disables (`false`) administrative privileges for the user.
- [Activate the changes to your configuration.](/zia/api-getting-started#ActivateChangestoYourConfiguration)
Updating Information for a Specific User
To update information for a specific user:
- Get information for a specific user by sending a GET request to `/users/{userId}`.
- Modify the user's information by sending a PUT request to `/users/{userId}` along with all of the required key-value pairs in the Body.
- [Activate the changes to your configuration.](/zia/api-getting-started#ActivateChangestoYourConfiguration)
Modifying Group Association for a User
You can modify group association for individual users by sending a PUT request to `/users/{userId}` and specifying the groups that must be associated with the user. However, you cannot change a group directly to modify the users that are associated with the group.
User group information sent in a PUT request to `/users/{userId}` essentially replaces the current group associations for the user. So when using this request to add or remove groups associated with a user, make sure to include all other existing group associations that you want to preserve. Consider a user associated with two groups, namely IT Security and Operations. A GET request to `/users/{userId}` would return the following information along with the user’s group association:
{
"id": 17073377,
"name": "guest user",
"email": "guestuser@safemarch.com",
"groups": [
{
"id": 3830452,
"name": "IT Security"
},
{
"id": 3830440,
"name": "Operations"
}
],
"department": {
"id": 7390365,
"name": "Engineering"
},
"adminUser": false,
"deleted": false
}
Let's say you want to add this user to one more group, Support. To do this, you need to send a PUT request to `/users/{userId}` by specifying all of the group associations that must be preserved for the user in the request Body, including Support, IT Security, and Operations. This request would be:
{
"name": "guest user",
"email": "guestuser@safemarch.com",
"groups": [
{
"id": 3830448,
"name": "Support"
},
{
"id": 3830452,
"name": "IT Security"
},
{
"id": 3830440,
"name": "Operations"
}
],
"department":
{
"id": 7390365,
"name": "Engineering"
}
}
In another scenario, if you want to associate only the Support group with the user and remove the existing groups associated, you can send a request with the following payload:
{
"name": "guest user",
"email": "guestuser@safemarch.com",
"groups": [
{
"id": 3830448,
"name": "Support"
}
],
"department":
{
"id": 7390365,
"name": "Engineering"
}
}
This request would associate the user with the Support group and remove the user's existing association with the IT Security and Operations groups.
Deleting a Specific User
To delete a specific user:
- Send a DELETE request to `/users/{userId}`.
Although you can retrieve all admins using the `/users` endpoint, you can only delete regular users (i.e., non-admins) when sending a DELETE request to `/users/{userId}`.
- [Activate the changes to your configuration.](/zia/api-getting-started#ActivateChangestoYourConfiguration)