# Managing URL Allowlist and Denylist Using API
Source: https://help.zscaler.com/zia/managing-url-allowlist-and-denylist-using-api
PDF: https://help.zscaler.com/pdf/com/en/1400421.pdf

The endpoint for managing denylists is `/security/advanced`. You can use this endpoint to retrieve or replace the entire denylist. To add or remove individual URLs to or from the denylist, use the `security/advanced/blacklistUrls` endpoint. The endpoint for managing allowlists is `/security`. You can use this endpoint to retrieve or replace the entire allowlist. However, you cannot add or remove individual URLs to or from the allowlist.
You can add up to 25,000 custom URLs and IPs across all categories (custom and predefined) and your organization's custom denylist and allowlist. For additional information on policy enforcement and prioritization of denylists, see [About Policy Enforcement](/zia/about-policy-enforcement).
Managing a Denylist
To update your custom denylist:
- (Optional) Get the current denylist by sending a GET request to `/security/advanced`.
- Modify the denylist's information by sending a PUT request to `/security/advanced`, and including all of the proper URLs to denylist in the Body. This action completely replaces the previous denylist.
- [Activate the changes to your configuration.](/zia/api-getting-started#ActivateChangestoYourConfiguration)
To add or remove a URL from a denylist:
- (Optional) Get the current denylist by sending a GET request to `/security/advanced`.
- Modify the denylist's information by sending a POST request to `/security/advanced/blacklistUrls`, with the `action` parameter set to `ADD_TO_LIST` or `REMOVE_FROM_LIST`, including all of the proper URLs in the Body.
- [Activate the changes to your configuration.](/zia/api-getting-started#ActivateChangestoYourConfiguration)
To learn more about the endpoints, see Security Policy Settings in the [API Reference](/zia/security-policy-settings).
Managing an Allowlist
To update your custom allowlist:
- (Optional) Get the current allowlist by sending a GET request to `/security`.
- Modify the allowlist's information by sending a PUT request to `/security`, and including all of the proper URLs to allowlist in the Body. This action completely replaces the previous allowlist.
- [Activate the changes to your configuration.](/zia/api-getting-started#ActivateChangestoYourConfiguration)
To learn more about the endpoints, see Security Policy Settings in the [API Reference](/zia/security-policy-settings).
When adding URLs to a denylist or allowlist, if a single URL uses an invalid format, the request is rejected and an error code is produced. A valid URL must meet the following requirements:
- The URL must use a standard URI format.
- The URL length cannot exceed 1024 characters.
- The URL cannot contain non-ASCII characters.
- The domain name before the colon (:) cannot exceed 255 characters.
- The domain name between periods (.) cannot exceed 63 characters.

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