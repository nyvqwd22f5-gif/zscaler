# Getting Started
Source: https://help.zscaler.com/zpa/getting-started-zpa-api
PDF: https://help.zscaler.com/pdf/com/en/1484896.pdf

Your organization must meet the following prerequisites before you can access and use the ZPA API:
- [Add an API key](/zpa/about-api-keys). Only admins with full access to the [API Key Management role](/zpa/configuring-administrator-roles#APIkey) can create keys.
- Use an API management tool, or use the [Zscaler Help Portal](/zpa/zpa-api/api-developer-reference-guide/reference-guide). If you choose to use the API management tool Postman, Zscaler does not officially provide a Postman collection. However, the option to create the collection is still possible. To learn more, see [Configuring the Postman REST API Client](/zpa/configuring-postman-rest-api-client).
If you need to obtain API keys, authenticate into, and make calls using [Zscaler OneAPI](/oneapi) endpoints, see [API Client Authentication](/zslogin/authentication/api-client-authentication) in ZIdentity and [Getting Started](/oneapi/getting-started) with OneAPI.
The request URLs and references to `config.private.zscaler.com` within this article differ depending on your organization’s assigned cloud. To learn more, see [What Is My Cloud Name for ZPA?](/zpa/what-my-cloud-name-zpa)
After these prerequisites are met, you can:
- [Locate your base URI](#Locate)
- [Authenticate and create an API session](#Authenticate)
- [Make an API call](#Make)
- [Log out of the API](#LogOut)
[]The base URI for the API is `/mgmtconfig/v1` and `/mgmtconfig/v2`. The base URI is `/userconfig/v1` for the following:
- The endpoint to get all SCIM attribute values.
- The endpoints to get SCIM group details.
To learn more, see [ZPA API Reference](/zpa/app-server-controller).
[]Before making any API calls, you must retrieve your authorization token (`Bearer <access_token>`). The authorization token is passed onto subsequent calls for authentication.
To authenticate via the API, use the following Python script to sign in and get the `Bearer <access_token>`. The client ID and client secret are highlighted to indicate the client ID and secret that must be entered.
`import requests
url = "https://config.private.zscaler.com/signin"
payload={'client_id':{client_id},'client_secret':{client_secret}}
headers = {
'Content-Type': 'application/x-www-form-urlencoded'
}
response = requests.request("POST", url, headers=headers, data=payload)
print(response.text)`
Example `POST` request for sign in using a Python script:
import requests
url = "https://config.private.zscaler.com/signin"
payload={'client_id':NzIwNzY1NDAyMTI0MTI1NjAtZWQ2Mz,'client_secret':O2k:0vs#,x,0N9}
headers = {
'Content-Type': 'application/x-www-form-urlencoded'
}
response = requests.request("POST", url, headers=headers, data=payload)
print(response.text)
The client secret is only accessible in the ZPA Admin Portal when the [API key](/zpa/about-api-keys) is created for the first time. Make sure to copy your client secret to your clipboard when you first create your API key. The authentication token expiry time is set to 3,600 seconds (one hour) by default.
- [View an example response](#ExampleResponseAuth)
[]
{
"token_type" : "Bearer",
"access_token" : "eyJraWQiOiI0bzZFS1k4STFqS1kwN2tQdjlqWV9",
"expires_in" : "3600"
}
To authenticate via the API and create a new session using an API management tool, you must first create the sign in request. To learn more, see [Configuring the Postman REST API Client](/zpa/configuring-postman-rest-api-client).
[]After you have your authorization token, you can make an API call.
To get the list of all application segments, send a `GET` request to the endpoint `/mgmtconfig/v1/admin/customers/``{customerId}``/application?page=1&pagesize=20&search=` and include the `customerId` parameter, the ZPA tenant ID of the customer.
Use the following Python script to get a list of all application segments. The `customerId` parameter is highlighted to indicate where the ZPA tenant ID must be entered.
import requests
url = "https://config.private.zscaler.com/mgmtconfig/v1/admin/customers/{customerId}/application?page=1&pagesize=20&search="
payload={}
headers = {
'Authorization': 'Bearer eyJraWQiOiI0bzZFS1k4STFqS1kwN2tQdjlqWV9'
}
response = requests.request("GET", url, headers=headers, data=payload)
print(response.text)
Example `GET` request using a Python script:
import requests
url = "https://config.private.zscaler.com/mgmtconfig/v1/admin/customers/7207654021241/application?page=1&pagesize=20&search="
payload={}
headers = {
'Authorization': 'Bearer eyJraWQiOiI0bzZFS1k4STFqS1kwN2tQdjlqWV9'
}
response = requests.request("GET", url, headers=headers, data=payload)
print(response.text)
- [View an example response](#ExampleResponseMake)
[]{
"totalPages":"1",
"list":[
{
"creationTime":"1617135729",
"modifiedBy":"7207654021241",
"id":"7207654021241",
"domainNames":[
"example.com"
],
"name":"example",
"serverGroups":[
{
"id":"7207654021241",
"creationTime":"1617134731",
"modifiedBy":"7207654021241",
"name":"SIPA",
"enabled":true,
"configSpace":"DEFAULT",
"dynamicDiscovery":true
}
],
"enabled":true,
"passiveHealthEnabled":true,
"tcpPortRanges":[
"443",
"443"
],
"doubleEncrypt":false,
"configSpace":"DEFAULT",
"bypassType":"NEVER",
"healthCheckType":"DEFAULT",
"isCnameEnabled":true,
"ipAnchored":true,
"healthReporting":"ON_ACCESS",
"segmentGroupId":"7207654021241",
"segmentGroupName":"SIPA"
},
{
"modifiedTime":"1617135436",
"creationTime":"1613673797",
"modifiedBy":"7207654021241",
"id":"7207654021241",
"domainNames":[
"www.example.com"
],
"name":"example",
"serverGroups":[
{
"id":"7207654021241",
"creationTime":"1613673769",
"modifiedBy":"7207654021241",
"name":"ZPA",
"enabled":true,
"configSpace":"DEFAULT",
"dynamicDiscovery":true
}
],
"enabled":true,
"passiveHealthEnabled":true,
"tcpPortRanges":[
"80",
"80"
],
"doubleEncrypt":false,
"configSpace":"DEFAULT",
"bypassType":"NEVER",
"healthCheckType":"DEFAULT",
"isCnameEnabled":true,
"ipAnchored":false,
"healthReporting":"ON_ACCESS",
"segmentGroupId":"7207654021241",
"segmentGroupName":"ZPA"
},
{
"creationTime":"1617134731",
"modifiedBy":"7207654021241",
"id":"7207654021241",
"domainNames":[
"docs.example.com"
],
"name":"docs.example.com",
"serverGroups":[
{
"id":"7207654021241",
"creationTime":"1617134731",
"modifiedBy":"7207654021241",
"name":"SIPA",
"enabled":true,
"configSpace":"DEFAULT",
"dynamicDiscovery":true
}
],
"enabled":true,
"passiveHealthEnabled":true,
"tcpPortRanges":[
"54",
"65535"
],
"doubleEncrypt":false,
"configSpace":"DEFAULT",
"bypassType":"NEVER",
"healthCheckType":"DEFAULT",
"isCnameEnabled":true,
"ipAnchored":true,
"healthReporting":"ON_ACCESS",
"segmentGroupId":"7207654021241",
"segmentGroupName":"SIPA"
},
{
"creationTime":"1613762719",
"modifiedBy":"7207654021241",
"id":"7207654021241",
"domainNames":[
"www.example.com"
],
"name":"example",
"serverGroups":[
{
"id":"7207654021241",
"creationTime":"1613673769",
"modifiedBy":"7207654021241",
"name":"ZPA",
"enabled":true,
"configSpace":"DEFAULT",
"dynamicDiscovery":true
}
],
"enabled":true,
"passiveHealthEnabled":true,
"tcpPortRanges":[
"443",
"443"
],
"doubleEncrypt":false,
"configSpace":"DEFAULT",
"bypassType":"NEVER",
"healthCheckType":"DEFAULT",
"isCnameEnabled":true,
"ipAnchored":false,
"healthReporting":"ON_ACCESS",
"segmentGroupId":"7207654021241",
"segmentGroupName":"ZPA"
},
{
"creationTime":"1616516461",
"modifiedBy":"7207654021241",
"id":"7207654021241",
"domainNames":[
"*.example.com"
],
"name":"test-wildcard",
"description":"&#x2a;&#x2e;example&#x2e;com",
"serverGroups":[
{
"id":"7207654021241",
"creationTime":"1613673769",
"modifiedBy":"7207654021241",
"name":"ZPA",
"enabled":true,
"configSpace":"DEFAULT",
"dynamicDiscovery":true
}
],
"enabled":true,
"passiveHealthEnabled":true,
"tcpPortRanges":[
"443",
"443",
"80",
"80"
],
"doubleEncrypt":false,
"configSpace":"DEFAULT",
"bypassType":"NEVER",
"healthCheckType":"DEFAULT",
"isCnameEnabled":true,
"ipAnchored":false,
"healthReporting":"ON_ACCESS",
"segmentGroupId":"7207654021241",
"segmentGroupName":"ZPA"
}
]
}
The following conditions apply when passing `microtenantId`, the unique identifier of the Microtenant, in a request:
- If you are within a Microtenant, you must pass the `microtenantId` field when making an API call to retrieve data from that Microtenant. The `microtenantId` can be obtained in the [API Keys](/zpa/about-api-keys) page, or can be obtained programmatically using the ZPA cloud service API. Access to certain operations are limited when you are within a Microtenant.
- If you are within the Default Microtenant, pass `microtenantId` as `0` when making requests to retrieve data from the Default Microtenant.
- Pass `microtenantId` as null to retrieve data from all customers associated with the tenant.
To learn more, see [About Microtenants](/zpa/about-microtenants) and [Configuring Microtenants Using API](/zpa/configuring-microtenants-using-api).
To get a list of all application segments within a Microtenant, send a `GET` request to the endpoint `/mgmtconfig/v1/admin/customers/{customerId}/application?microtenantId={microtenantId}` and include the `customerId` and `microtenantId` parameters.
Use the following Python script to get a list of all application segments within a Microtenant. The `customerId` and `microtenantId` parameters are highlighted to indicate where the parameters must be entered.
`import requests
url = "https://config.private.zscaler.com/mgmtconfig/v1/admin/customers/{customerId}/application?microtenantId={microtenantId}"
payload={}
headers = {
'Authorization': 'Bearer eyJraWQiOiI0bzZFS1k4STFqS1kwN2tQdjlqWV9'
}
response = requests.request("GET", url, headers=headers, data=payload)
print(response.text)`
Example `GET` request using a Python script:
`import requests
url = "https://config.private.zscaler.com/mgmtconfig/v1/admin/customers/72057594037927936/application?microtenantId=72057594038647050"
payload={}
headers = {
'Authorization': 'Bearer eyJraWQiOiI0bzZFS1k4STFqS1kwN2tQdjlqWV9'
}
response = requests.request("GET", url, headers=headers, data=payload)
print(response.text)`
- [View an example response](#MicrotenantExampleGet)
[]
`{
"totalPages": "526",
"totalCount": "0",
"list": [
{
"modifiedTime": "1706698881",
"creationTime": "1679251696",
"modifiedBy": "72057594038640698",
"id": "72057594038642786",
"domainNames": [
"es10.com"
],
"name": "10002ADPDemo21",
"description": "example description",
"serverGroups": [
{
"id": "72057594037988579",
"modifiedTime": "1698311146",
"creationTime": "1612438082",
"modifiedBy": "72057594038620086",
"name": "123",
"enabled": true,
"description": "/><img src=x onerror=alert(document.cookie)>",
"configSpace": "DEFAULT",
"dynamicDiscovery": true
}
],
"enabled": true,
"passiveHealthEnabled": true,
"doubleEncrypt": false,
"configSpace": "DEFAULT",
"bypassType": "ALWAYS",
"healthCheckType": "NONE",
"icmpAccessType": "NONE",
"isCnameEnabled": false,
"ipAnchored": false,
"bypassOnReauth": false,
"inspectTrafficWithZia": false,
"healthReporting": "NONE",
"useInDrMode": false,
"tcpKeepAlive": "1",
"selectConnectorCloseToApp": false,
"isIncompleteDRConfig": false,
"adpEnabled": false,
"microtenantName": "Default",
"segmentGroupId": "72057594038634881",
"segmentGroupName": "1SEG-GRP"
}
]
}
`
To learn about making calls in the ZPA API Portal, follow the relevant use cases. To learn more, see the [ZPA API Developer & Reference Guide](/zpa/zpa-api).
[]To log out of the API, send a `POST` request to the endpoint `/signout` with the following parameters:
- Content-Type: `application/json`
- Authorization: `Bearer <access_token>`
In the following Python script to log out of the API, the <access_token> is highlighted to indicate the authorization token you must enter:
import requests
url = "https://config.private.zscaler.com/signout"
payload={}
headers = {
'Content-Type': 'application/json',
'Authorization': 'Bearer <access_token>'
}
response = requests.request("POST", url, headers=headers, data=payload)
print(response.text)
To log out of the ZPA API Portal, enter the following URL into your browser: [https://config.private.zscaler.com/logout](https://config.private.zscaler.com/logout).
To learn more about rate limiting and HTTP status codes, see [About Rate Limiting](/zpa/about-rate-limiting) and [About Error Codes](/zpa/about-error-codes). If you encounter any issues with the API, contact Zscaler Support.

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