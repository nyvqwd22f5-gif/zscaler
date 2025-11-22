# Generating Admin Audit Logs Using API
Source: https://help.zscaler.com/zia/generating-admin-audit-logs-using-api
PDF: https://help.zscaler.com/pdf/com/en/1400431.pdf

Admin audit logs are stored for the last 6 months and you can download reports for up to 31 days or a maximum of 1,000 records at a time.
To generate and export a CSV-formatted admin audit log report via the API:
- Generate an audit log report by sending a POST request to `/auditlogEntryReport`, where the request body specifies:
- `startTime`: The timestamp, in epoch, of the admin's last login.
- `endTime`: The timestamp, in epoch, of the admin's last logout.
For example, in Python:
payload = {
"startTime":1493967600000,
"endTime":1496645999999
}
The request body can also include the following attributes:
- `actionTypes`: The action performed by the admin in the ZIA Admin Portal (i.e., Admin UI) or API. [Possible values for actionTypes](/zia/about-audit-logs#action).
- `category`: The location in the ZIA Admin Portal (i.e., Admin UI) where the `actionType` was performed. [Possible values for category](/zia/about-audit-logs#category).
- `subcategories`: The area within a category where the `actionType` was performed. [Possible values for subcategories](/zia/about-audit-logs#sub).
- `actionResult`: The outcome (i.e., Failure or Success) of an `actionType`.
- `actionInterface`: The interface (i.e., Admin UI or API) where the `actionType` was performed.
- `clientIP`: The source IP address for the admin.
- `adminName`: The admin's login ID.
- `traceId`: A trace ID is generated and logged for transactions associated with ZIA API requests made via [Zscaler OneAPI](/oneapi/understanding-oneapi). The trace ID helps admins correlate API transactions with the OneAPI platform and you can use the trace ID for debugging purposes.
Generating a new report overwrites a previously-generated report.
- When the report has generated, you can export it by sending a GET request to `/auditlogEntryReport/download`.
The response is formatted according to the time zone configured under **Administration **> **My Profile** within the ZIA Admin Portal. To learn more, see [Customizing Your Admin Account Settings](/zia/customizing-your-admin-account-settings).
To check whether the report has finished generating, send a GET request to `/auditlogEntryReport`. You can also cancel a POST request to generate a report by sending a DELETE request to `/auditlogEntryReport`.
To learn more about each endpoint, see [API Reference](/zia/admin-audit-logs).

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