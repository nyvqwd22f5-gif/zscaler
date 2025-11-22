# Managing Admins and Roles Using API
Source: https://help.zscaler.com/zia/managing-admins-and-roles-using-api
PDF: https://help.zscaler.com/pdf/com/en/1461451.pdf

Admin & Role Management API resources within the cloud service API provide programmatic access to perform various operations relating to admins, auditors, and roles. You can use these resources to retrieve roles or create and manage admins for your organization.
The following steps provide an overview of how to configure role-based administration for the Zscaler service:
- Add a user, set up authentication, and assign the user to their department and group by using the POST `/users` request. To learn more, see [Managing Users Using API](/zia/managing-users-using-api).
- Configure the user with admin privileges and assign the admin role, scope, and other permissions by using the POST `/adminUsers` request. Ensure that you have the admin role configured per your requirements.
- Manage the admin user:
- To update admin user information, use PUT `/adminUsers/{userId}`.
- To delete an admin and remove them as a user from the ZIA Admin Portal, use DELETE `/adminUsers/{userId}`. To delete an admin and retain them as a user, use POST `/adminUsers/{userId}/convertToUser`.
This article covers Step 2 and Step 3 in detail with examples.
The Zscaler service supports role-based access for admins to provide granular access to the ZIA Admin Portal based on their roles and responsibilities. The service also supports different types of admins, including ZIA admins, SD-WAN partner API clients, Executive Insights App admins, and API admins. You can also create and manage auditors, who play a special role in the organization, enabling admins to view user names that are obfuscated. To learn more, see [About Auditors](/zia/about-auditors).
- Access to Admin & Role Management resources requires full Administrators Access permissions for the [API role](/zia/adding-api-roles#administrators-access) (when using OAuth 2.0) or [admin role](/zia/adding-admin-roles#administrators-access) (when using admin credentials and API key-based authentication). To learn more, see [Getting Started](/zia/getting-started-zia-api).
- Admins who have permission to manage other admins can only create, edit, or view admins that have an equal or lower rank. To learn more, see [About Admin Rank](/zia/about-admin-rank). So when you retrieve, create, update, or delete admin credentials via the API, it is only for admins of an equal or lower rank to yours.
- Admin rank and scope don't apply to SD-WAN partner API clients. To learn more, see [Adding SD-WAN Partner API Clients](/zia/adding-sd-wan-partner-api-clients).
- [API roles](/zia/adding-api-roles) are never associated with an admin. Instead, an API role is assigned to an API client application that accesses Zscaler's APIs using OAuth 2.0. To learn more, see [Securing ZIA APIs with OAuth 2.0](/zia/securing-zia-apis-oauth-2.0).
Before getting started with the operations listed in this article, ensure that you have provisioned a user who can be assigned the admin role. To learn more, see [Managing Users Using API](/zia/managing-users-using-api).
After making any configuration changes, you must activate them by sending a POST request to `/status/activate`. As a best practice, if you are making multiple configuration changes, Zscaler recommends grouping the changes and activating once. To learn more, see [Getting Started](/zia/getting-started-zia-api).
Getting a List of Admin Roles
To get a list of admin roles, send a GET request to `/adminRoles/lite`. You can use the following query parameters in the request:
- `includeAuditorRole`: Includes auditor role information in the list.
- `includePartnerRole`: Includes SD-WAN partner API role information in the list.
- `includeApiRole`: Includes API role information in the list.
For example, in Python:
conn.request("GET", "/api/v1/adminRoles/lite?page=1&pageSize=100", payload, headers)
conn.request("GET", "/api/v1/adminRoles/lite?includeAuditorRole=true&includePartnerRole=true&includeApiRole=true", payload, headers)
A successful request returns the list of admin roles along with the following information in a JSON object:
[
{
"id": 1254,
"rank": 7,
"name": "HR",
"roleType": "ORG_ADMIN",
"reportTimeDuration": -1
},
…
]
Getting a List of Admin Users
To get a list of admin users configured in the ZIA Admin Portal, send a GET request to `/adminUsers`. You can use the following query parameters in the request:
- `includeAuditorUsers`: Includes users with auditor privileges in the list.
- `includePartnerRole`: Includes SD-WAN partner API client information in the list.
You can also use the search query parameter to use keywords to match (partially or fully) against an admin's Login ID or Name. (e.g., "John").
For example, in Python:
conn.request("GET", "/api/v1/adminUsers?page=1&pageSize=100&search=john", payload, headers)
conn.request("GET", "/api/v1/adminUsers?includeAuditorUsers=true&includePartnerRole=true", payload, headers)
A successful request returns the list of admin users with the following information in JSON-formatted data:
[
{
"id": 3817674,
"loginName": "jdoe@safemarch.com",
"userName": "John Doe",
"email": "jdoe@safemarch.com",
"role": {
"id": 1255,
"name": "IT",
"isNameL10nTag": true,
"extensions": {
"adminRank": "7",
"roleType": "ORG_ADMIN"
}
},
"comments": "Password123!",
"adminScopescopeGroupMemberEntities": [],
"adminScopeType": "DEPARTMENT",
"adminScopeScopeEntities": [
{
"id": 3829304,
"name": "TP"
}
],
"disabled": false,
"isPasswordLoginAllowed": true,
"pwdLastModifiedTime": 1520496222,
"name": "John Doe"
}
]
Adding an Admin User
Before you can add an admin, you must send a GET request to `/adminRoles` to retrieve information about the role that must be assigned to the admin user.
To configure a user with admin privileges, send a POST request to `/adminUsers` along with the following necessary key-value pairs in the Body:
- `loginName`: The admin's login name. This field value is in email format and uses the domain name associated with the Zscaler account.
- `email`: The admin's business email address.
- `userName`: The admin's username.
- `role`: A JSON key-value pair containing the id and name of the role that must be assigned to the admin.
You can also include optional fields, such as `isPasswordLoginAllowed`, `execMobileAppEnabled`, etc. in the API request.
For example:
{
"email": "demouser@example.com",
"loginName": "demouser@example.com",
"role": {
"id": 695,
"name": "Demo Role"
},
"userName": "Demo User"
}
Sample request in Python:
import http.client
import json
conn = http.client.HTTPSConnection("10.65.31.120")
payload = json.dumps({
"email": "demouser@example.com",
"loginName": "demouser@example.com",
"role": {
"id": 695,
"name": "Demo Role"
},
"userName": "Demo User"
})
headers = {
'Content-Type': 'application/json',
'Cookie': 'JSESSIONID=D2A1CC35FCCC5769501D7FE230576F34'
}
conn.request("POST", "/api/v1/adminUsers", payload, headers)
res = conn.getresponse()
data = res.read()
print(data.decode("utf-8"))
A successful request returns the admin user information in a JSON object:
{
"id": 344325,
"loginName": "demouser@example.com",
"userName": "Demo User",
"email": "demouser@example.com",
"role": {
"id": 695,
"name": "Demo Role",
"isNameL10nTag": true,
"extensions": {
"adminRank": "7",
"roleType": "ORG_ADMIN"
}
},
"adminScopescopeGroupMemberEntities": [],
"adminScopeType": "ORGANIZATION",
"adminScopeScopeEntities": [],
"disabled": false,
"pwdLastModifiedTime": 0,
"name": "Demo User",
"execMobileAppEnabled": false
}
When a key-value pair is not explicitly specified in the API request, the default value is assigned to the respective fields. This includes password-based login (disabled by default if single sign-on is configured), admin scope (organization scope assigned by default), Executive Insights App access (disabled by default), etc. You can configure these fields using the appropriate attributes when adding the admin or by updating the admin user information.
If you want to create an auditor user, you need to send a POST request to `/adminUsers` along with the following key-value pairs in the Body:
{
"email": "demoauditor@example.com",
"loginName": "demoauditor@example.com",
"userName": "Demo Auditor",
"isAuditor": true,
"isPasswordLoginAllowed": true,
"password": "Admin@123"
}
Optionally, you can include the auditor user status and additional comments by using the appropriate fields in the API request.
Updating Information for an Admin User
To update an admin user information, obtain the admin user ID (userId) by sending a GET request to `/adminUsers`. Then, send a PUT request to `/adminUsers/{userId}` with all of the required fields as well as the fields that must be modified.
For example, to enable password-based login for an admin, you need to send the following key-value pairs in the request Body:
{
"email": "demouser@example.com",
"loginName": "demouser@example.com",
"role": {
"id": 695,
"name": "Demo Role"
},
"userName": "Demo User",
"isPasswordLoginAllowed": true,
"password": "xxxxxx"
}
A successful request returns the admin user information along with the new configurations in a JSON structure:
{
"id": 344325,
"loginName": "demouser@example.com",
"userName": "Demo User",
"email": "demouser@example.com",
"role": {
"id": 695,
"name": "Demo Role",
"isNameL10nTag": true,
"extensions": {
"adminRank": "7",
"roleType": "ORG_ADMIN"
}
},
"adminScopescopeGroupMemberEntities": [],
"adminScopeType": "ORGANIZATION",
"adminScopeScopeEntities": [],
"disabled": false,
"isPasswordLoginAllowed": true,
"pwdLastModifiedTime": 1689002233,
"name": "Demo User",
"execMobileAppEnabled": false
}
Deleting an Admin User
The default admin account cannot be deleted.
To delete an admin user, obtain the admin user ID (userId) by sending a GET request to `/adminUsers`. Then, send a DELETE request to `/adminUsers/{userId}` with the admin's user ID. For example, in Python:
conn.request("DELETE", "/api/v1/adminUsers/344325", payload, headers)
This request deletes the admin and removes them as a user from the ZIA Admin Portal. However, if you want to remove the admin privileges for a user while retaining the user in the ZIA Admin Portal, you need to send a POST request to `/adminUsers/{userId}/convertToUser` with the admin user's ID. Apart from the user's ID, group information is mandatory for this request. Optionally, you can include other field information to modify the values.
For example, to convert an admin user to a non-admin user, you need to send the following POST request (example in Python) along with the key-value pairs in the request Body:
conn.request("POST", "/api/v1/adminUsers/74611/convertToUser", payload, headers){
"groups": [ {
"id": 69782,
"name": "Service Admin"
}
]
}

## Contents
- **API Developer & Reference Guide**
  - [Getting Started](/zia/getting-started-zia-api)
  - [Configuring the Postman REST API Client](/zia/configuring-postman-rest-api-client)
  - [Understanding Rate Limiting](/zia/understanding-rate-limiting)
  - [API Response Codes and Error Messages](/zia/api-response-codes-and-error-messages)
  - **Reference Guide**
    - [3rd-Party App Governance API](/zia/3rd-party-app-governance-api)
    - [Sandbox Submission API](/zia/sandbox-submission-api)
    - [Activation](/zia/activation)
    - [Admin Audit Logs](/zia/admin-audit-logs)
    - [Admin & Role Management](/zia/admin-role-management)
    - [Advanced Settings](/zia/advanced-settings)
    - [Advanced Threat Protection Policy](/zia/advanced-threat-protection-policy)
    - [Alerts](/zia/alerts)
    - [API Authentication](/zia/api-authentication)
    - [Authentication Settings](/zia/authentication-settings)
    - [Bandwidth Control & Classes](/zia/bandwidth-control-classes)
    - [Browser Control Policy](/zia/browser-control-policy)
    - [Browser Isolation](/zia/browser-isolation)
    - [Cloud Applications](/zia/cloud-applications)
    - [Cloud App Control Policy](/zia/cloud-app-control-policy)
    - [Cloud Nanolog Streaming Service (NSS)](/zia/cloud-nanolog-streaming-service-nss)
    - [Data Loss Prevention](/zia/data-loss-prevention)
    - [Device Groups](/zia/device-groups)
    - [DNS Control Policy](/zia/dns-control-policy)
    - [End User Notifications](/zia/end-user-notifications)
    - [Event Logs](/zia/event-logs)
    - [File Type Control Policy](/zia/file-type-control-policy)
    - [Firewall Policies](/zia/firewall-policies)
    - [Forwarding Control Policy](/zia/forwarding-control-policy)
    - [FTP Control Policy](/zia/ftp-control-policy)
    - [Intermediate CA Certificates](/zia/intermediate-ca-certificates)
    - [IoT Report](/zia/iot-report)
    - [IPS Control Policy](/zia/ips-control-policy)
    - [Location Management](/zia/location-management)
    - [Malware Protection Policy](/zia/malware-protection-policy)
    - [Mobile Malware Protection Policy](/zia/mobile-malware-protection-policy)
    - [NAT Control Policy](/zia/nat-control-policy)
    - [Organization Details](/zia/organization-details)
    - [PAC Files](/zia/pac-files)
    - [Policy Export](/zia/policy-export)
    - [Remote Assistance Support](/zia/remote-assistance-support)
    - [Rule Labels](/zia/rule-labels)
    - [SaaS Security API](/zia/saas-security-api)
    - [Sandbox Policy & Settings](/zia/sandbox-policy-settings)
    - [Sandbox Report](/zia/sandbox-report)
    - [Security Policy Settings](/zia/security-policy-settings)
    - [Service Edges](/zia/service-edges)
    - [Shadow IT Report](/zia/shadow-it-report-api)
    - [SSL Inspection Policy](/zia/ssl-inspection-policy)
    - [System Audit Report](/zia/system-audit-report)
    - [Time Intervals](/zia/time-intervals)
    - [Traffic Capture Policy](/zia/traffic-capture-policy)
    - [Traffic Forwarding](/zia/traffic-forwarding-0)
    - [URL Categories](/zia/url-categories)
    - [URL Filtering Policy](/zia/url-filtering-policy)
    - [URL & Cloud App Control Policy Settings](/zia/url-cloud-app-control-policy-settings)
    - [User Authentication Settings](/zia/user-authentication-settings)
    - [User Management](/zia/user-management)
    - [Workload Groups](/zia/workload-groups)
    - [API Rate Limit Summary](/zia/api-rate-limit-summary)
  - **Working with APIs**
    - [Generating Admin Audit Logs Using API ](/zia/generating-admin-audit-logs-using-api)
    - [Managing Admins and Roles Using API ](/zia/managing-admins-and-roles-using-api)
    - [Managing Intermediate CA Certificates Using API](/zia/managing-intermediate-ca-certificates-using-api)
    - [Managing Locations Using API](/zia/managing-locations-using-api)
    - [Obtaining Sandbox Reports Using API](/zia/obtaining-sandbox-reports-using-api)
    - [SD-WAN Integrations Using API](/zia/sd-wan-integrations-using-api)
    - [Configuring VPN Credentials for IPSec Tunnels Using API](/zia/configuring-vpn-credentials-ipsec-tunnels-using-api)
    - [Managing URL Allowlist and Denylist Using API](/zia/managing-url-allowlist-and-denylist-using-api)
    - [Configuring URL Categories Using API](/zia/configuring-url-categories-using-api)
    - [Managing Users Using API](/zia/managing-users-using-api)