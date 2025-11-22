# Configuring VPN Credentials for IPSec Tunnels Using API
Source: https://help.zscaler.com/zia/configuring-vpn-credentials-ipsec-tunnels-using-api
PDF: https://help.zscaler.com/pdf/com/en/1400436.pdf

The Zscaler service inspects internal traffic within an organization's corporate network using ZIA Public Service Edges or secure web gateways. Traffic forwarding can be enabled through IPSec VPN tunneling, and requires that the proper user credentials are configured. To learn more, see [About VPN Credentials](/zia/about-vpn-credentials). For detailed information about the API endpoints used for configuring and managing VPN credentials, see [API Reference](/zia/traffic-forwarding-0).
Getting VPN Credentials for a Location
To retrieve the VPN credentials for a location, send a GET request to `/vpnCredentials`. You can use the following parameters within the request:
- `locationId`: Specify a location ID number, the request returns credentials for a specific location.
- `search`: Specify a string, the request returns any VPN credentials with matching `commonName`, `fqdn`, `ipAddress`, `comments`, or `locationName` fields, including partial matches.
- `type`: Specify a string, the request gets the credentials with the specified type.
- `includeOnlyWithoutLocation`: When the Boolean for this parameter is set to `true`, the request gets VPN credentials that are not associated with any location.
- `page`: Specify a page offset.
- `pageSize`: Specify the page length, up to a limit of 1000.
Zscaler recommends changing the `pageSize` query parameter to more than 100, or iterating through all results using the `page` query parameter, until the last page has less than 100 results.
If you send a GET request to `/vpnCredentials`, the pre-shared key (PSK) is not included in the response for security reasons.
Getting Credentials for a Specific VPN ID
To get the credentials for a specific VPN ID, send a GET request to `/vpnCredentials/{vpnId}`.
Updating Credentials for a Specific VPN ID
To update the credentials for a specific VPN ID:
- Send a PUT request to `/vpnCredentials/{vpnId}`, and specify the following VPN parameters in the Body:
- `id`: Specify the VPN ID as an integer (e.g., "`72532`").
- `type`: Specify the authentication type as a string (e.g., "`UFQDN`").
- `fqdn`: This parameter is only required if you are using the `UFQDN` or `XAUTH` authentication type. Specify the fully qualified domain name as a string (e.g., "`testvpn.antest.com`").
You cannot update the `fqdn` by sending a PUT request to `/vpnCredentials/{vpnId}`. If the `fqdn` is modified in the request, the change is ignored.
- `comments`: Add comments as a string (e.g., "`created automatically`").
- `pre-shared key`: This key is only required if you are using the `UFQDN` or `IP` authentication type (e.g., "`newPassword123!`").
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