# Managing Locations Using API
Source: https://help.zscaler.com/zia/managing-locations-using-api
PDF: https://help.zscaler.com/pdf/com/en/1401566.pdf

Locations identify the various networks from which your organization sends its internet traffic. When an organization forwards its traffic to the Zscaler service through a [GRE](/zia/configuring-gre-tunnels) or [IPSec](/zia/configuring-ipsec-vpn-tunnel) tunnel, Zscaler provisions your organization's IP addresses, which you then add as locations. Sublocations enable an organization to create new locations that reference IP addresses that are encapsulated within a GRE or IPSec tunnel, or that are passed to the Zscaler service through X-Forwarded-For (XFF) headers. You can add [locations](/zia/about-locations) and [sublocations](/zia/understanding-sublocations) using the cloud service API or the ZIA Admin Portal. To learn more about the API endpoints used for these configurations, see [API Reference](/zia/location-management).
If your locations and sublocations are managed by a Software-Defined Wide Area Networking (SD-WAN) partner, see [SD-WAN API Integration for IPSec VPN Tunnel Provisioning](/zia/sd-wan-api-integration). The following information only provides details on how to use [Location Management](/zia/location-management) resources to set up locations and sublocations if they are not managed by an SD-WAN partner.
Getting a List of Locations and Sublocations
[Location Management](/zia/location-management) resources allow you to export all attributes of a Zscaler service-defined location as a request. Calling `GET /locations` retrieves a list of location objects managed by you. For example, in Python, a GET request would appear as follows:
conn.request("GET", "/api/v1/locations", headers=headers)
So the response would be:
[
{
"name": "nyc-2",
"id": 4562809,
"managedBy": {
"id": 1,
"name": "Self"
},
"vpnCredentials": [
{
"id": 4562807,
"type": "UFQDN",
"fqdn": "nyc-1-37@yourcompany.com",
"comments": "created automatically"
}
]
},
{
"name": "sjc-1",
"id": 4562808,
"managedBy": {
"id": 1,
"name": "Self"
},
"vpnCredentials": [
{
"id": 4562805,
"type": "UFQDN",
"fqdn": "sjc-1-37@yourcompany.com",
"comments": "created automatically"
}
]
}
]
If you have locations and sublocations that you manage and others that an SD-WAN partner manages, then calling `GET /locations` retrieves a list of location objects managed by you (i.e., Self) and your specified SD-WAN partner. However, SD-WAN partners cannot retrieve objects that are managed by you (i.e., Self). To learn more, see [Understanding the managedBy Attribute](/zia/sd-wan-api-integration#UnderstandManagedBy).
Calling `GET /locations/{locationId}/sublocations` retrieves a list of sublocation objects for the specified `locationId`. For example, in Python, a GET request would appear as follows:
conn.request("GET ", "/api/v1/locations/6793981/sublocations", headers=headers)
So the response would be:
[
{
"id": 6793982,
"name": "guest-wifi",
"parentId": 6793981,
"ipAddresses": ["10.131.2.128-10.131.3.255"],
"surrogateRefreshTimeInMinutes": 0
},
{
"id": 6793983,
"name": "other",
"parentId": 6793981,
"otherSubLocation": true,
"surrogateRefreshTimeInMinutes": 0
}
]
If used, Zscaler recommends changing the `pageSize` query parameter to more than 100, or iterating through all results using the `page` query parameter, until the last page has less than 100 results.
Adding Locations and Sublocations
To add a location with VPN credentials or a static IP address, make sure that the following prerequisites are met:
- If you want to add a location with VPN credentials, you need the ID and other details of the VPN credentials. You can retrieve the list of VPN credentials available for associating with a location by sending a GET request to `/vpnCredentials` with the `includeOnlyWithoutLocation` query parameter set to `true`. If the VPN credentials don't already exist, you need to add them by sending a POST request to `/vpnCredentials`.
- If you want to add a location with a static IP address, ensure that you have a self-provisioned static IP address or one that has been provisioned for your organization by Zscaler.
To add a location:
- Send a POST request to `/locations` and use the following key-value pairs in the Body:
- `name`: A string (e.g., "`nyc-4`").
- `vpnCredentials`: If you are adding a location with VPN credentials, then this parameter and its key-value pairs are required in the request:
- `id`: Specify the VPN ID as an integer (e.g., "`4562873`").
- `type`: Specify the authentication type as a string (e.g., "`UFQDN`").
- `fqdn`: This parameter is only required if you are using the `UFQDN` or `XAUTH` authentication type. Specify the fully qualified domain name as a string (e.g., "`nyc-1-38@yourcompany.com`").
To learn more, see [Configuring VPN Credentials for IPSec Tunnels Using API](/zia/vpn-credentials-use-cases).
- `ipAddresses`: If you are adding a location with a static IP address, then this parameter is required in the request (e.g., ["`50.60.70.80`"]).
- [Activate the changes to your configuration.](/zia/api-getting-started#ActivateChangestoYourConfiguration)
To add a sublocation:
- Send a POST request to `/locations` and use the following key-value pairs in the Body:
- `parentId`: The parent location's ID. A string (e.g., "`6793981`").
- `name`: A string (e.g., "`guest-wifi`").
- `ipAddresses`: The IP address for the sublocation. You can also specify IP addresses in a range (e.g., ["`10.131.2.128-10.131.3.255`"]).
- [Activate the changes to your configuration.](/zia/api-getting-started#ActivateChangestoYourConfiguration)
Updating Locations and Sublocations
To update a location or sublocation based on a specified location ID:
- Get information about a specific location by sending a GET request to `/locations/{locationId}` or `/locations/{locationId}/sublocations`.
If you send a GET request to `/locations`, the pre-shared key (PSK) for the associated VPN credential is not included in the response for security reasons.
- Modify the location or sublocation's information by sending a PUT request to `/locations/{locationId}`, and including all the required key-value pairs in the Body.
You cannot update a location or sublocation's fully qualified domain name (`fqdn`) by sending a PUT request to `/locations/{locationId}`. If the `fqdn` is modified in the request, the change is ignored.
- [Activate the changes to your configuration.](/zia/api-getting-started#ActivateChangestoYourConfiguration)
Deleting Locations and Sublocations
If you delete a location, then any sublocations associated with it are also deleted.
To delete a location or sublocation based on a specified location ID:
- Send a DELETE request to `/locations/{locationId}`.
You can also bulk delete locations, up to a maximum of 100 locations per request, by calling `DELETE /locations/bulkDelete`.
- [Activate the changes to your configuration.](/zia/api-getting-started#ActivateChangestoYourConfiguration)

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