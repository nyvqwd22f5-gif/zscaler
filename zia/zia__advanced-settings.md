# Advanced Settings
Source: https://help.zscaler.com/zia/advanced-settings

API Reference Guide for the ZIA Cloud Service and Sandbox Submission APIs

**Base URL:** https://zsapi.[zscaler-cloud-name]/api/v1

## `GET /advancedSettings`

Retrieves information about the advanced settings configured in the ZIA Admin Portal

**Tags:** Advanced Settings
**Consumes:** application/json
**Produces:** application/json
No parameters.

| Code | Description | Schema |
| ---- | ----------- | ------ |
| 200 | Successful Operation | AdvancedSettings |

## `PUT /advancedSettings`

Updates the advanced settings configuration in the ZIA Admin Portal. To learn more, see [Configuring Advanced Settings](/zia/configuring-advanced-settings).

**Tags:** Advanced Settings
**Consumes:** application/json
**Produces:** application/json

| Name | In | Type | Required | Description |
| ---- | --- | ---- | -------- | ----------- |
| body | body | AdvancedSettings | Yes | Advanced settings in the ZIA Admin Portal |

| Code | Description | Schema |
| ---- | ----------- | ------ |
| 200 | Successful Operation | AdvancedSettings |

## Models
### AdvancedSettings
Advanced settings available for configuration in the ZIA Admin Portal. To learn more, see [Configuring Advanced Settings](/zia/configuring-advanced-settings).
| Field | Type | Required | Description |
| ----- | ---- | -------- | ----------- |
| authBypassApps | array[PolicyWebApplication] | No | Cloud applications that are exempted from cookie authenticatio |
| authBypassUrlCategories | array[WebFilteringUrlCategory] | No | URL categories that are exempted from cookie authentication |
| authBypassUrls | array[string] | No | Custom URLs that are exempted from cookie authentication for users |
| basicBypassApps | array[PolicyWebApplication] | No | Cloud applications that are exempted from Basic authentication |
| basicBypassUrlCategories | array[WebFilteringUrlCategory] | No | URL categories that are exempted from Basic authentication |
| blockConnectHostSniMismatch | boolean | No | A Boolean value indicating whether CONNECT host and SNI mismatch (i.e., CONNECT host doesn't match the SSL/TLS client hello SNI) is blocked or not |
| blockDomainFrontingApps | array[PolicyWebApplication] | No | Applications that are exempted from domain fronting |
| blockDomainFrontingOnHostHeader | boolean | No | A Boolean value indicating whether to block HTTP and HTTPS transactions that have an FQDN mismatch between:
- The request URL and the request's host header. The service doesn't consider it a mismatch if either of the fields, host header, or FQDN URL is empty.
- The SNI and the inner request's host header. The service doesn't consider it a mismatch if either of the fields, host header, or SNI is empty. |
| blockHttpTunnelOnNonHttpPorts | boolean | No | A Boolean value indicating whether HTTP CONNECT method requests to non-standard ports are allowed or not (i.e., requests directed to ports other than the standard HTTP and HTTPS ports, 80 and 443) |
| blockNonCompliantHttpRequestOnHttpPorts | boolean | No | A Boolean value indicating whether to allow or block traffic that is not compliant with RFC HTTP protocol standards |
| blockNonHttpOnHttpPortEnabled | boolean | No | A Boolean value indicating whether non-HTTP Traffic on HTTP and HTTPS ports are allowed or blocked |
| cascadeUrlFiltering | boolean | No | A Boolean value indicating whether to apply the URL Filtering policy even when the Cloud App Control policy already allows a transaction explicitly |
| digestAuthBypassApps | array[PolicyWebApplication] | No | Cloud applications that are exempted from Digest authentication |
| digestAuthBypassUrlCategories | array[WebFilteringUrlCategory] | No | URL categories that are exempted from Digest authentication |
| digestAuthBypassUrls | array[string] | No | Custom URLs that are exempted from Digest authentication |
| dnsResolutionOnTransparentProxyApps | array[PolicyWebApplication] | No | Cloud applications to which DNS optimization on transparent proxy mode applies |
| dnsResolutionOnTransparentProxyExemptApps | array[PolicyWebApplication] | No | Cloud applications that are excluded from DNS optimization on transparent proxy mode |
| dnsResolutionOnTransparentProxyExemptUrlCategories | array[WebFilteringUrlCategory] | No | URL categories that are excluded from DNS optimization on transparent proxy mode |
| dnsResolutionOnTransparentProxyExemptUrls | array[string] | No | URLs that are excluded from DNS optimization on transparent proxy mode |
| dnsResolutionOnTransparentProxyIPv6Apps | array[PolicyWebApplication] | No | Cloud applications to which DNS optimization for IPv6 addresses on transparent proxy mode applies |
| dnsResolutionOnTransparentProxyIPv6ExemptApps | array[PolicyWebApplication] | No | Cloud applications that are excluded from DNS optimization for IPv6 addresses on transparent proxy mode |
| dnsResolutionOnTransparentProxyIPv6ExemptUrlCategories | array[WebFilteringUrlCategory] | No | IPv6 URL categories that are excluded from DNS optimization on transparent proxy mode |
| dnsResolutionOnTransparentProxyIPv6UrlCategories | array[WebFilteringUrlCategory] | No | IPv6 URL categories to which DNS optimization on transparent proxy mode applies |
| dnsResolutionOnTransparentProxyUrlCategories | array[WebFilteringUrlCategory] | No | URL categories to which DNS optimization on transparent proxy mode applies |
| dnsResolutionOnTransparentProxyUrls | array[string] | No | URLs to which DNS optimization on transparent proxy mode applies |
| domainFrontingBypassUrlCategories | array[WebFilteringUrlCategory] | No | URL categories that are exempted from domain fronting |
| dynamicUserRiskEnabled | boolean | No | A Boolean value indicating whether to dynamically update user risk score by tracking risky user activities in real time |
| ecsForAllEnabled | boolean | No | A Boolean value indicating whether or not to include the ECS option in all DNS queries, originating from all locations and remote users. |
| ecsObject | EntityReference | No | The ECS prefix that must be used in DNS queries when the ECS option is enabled |
| enableAdminRankAccess | boolean | No | A Boolean value indicating whether ranks are enabled for admins to allow admin ranks in policy configuration and management |
| enableDnsResolutionOnTransparentProxy | boolean | No | A Boolean value indicating whether DNS optimization is enabled or disabled for Z-Tunnel 2.0 and [transparent proxy](/zia/what-proxy-mode#transparent-mode) mode traffic (e.g., traffic via GRE or IPSec tunnels without a PAC file). This setting allows Zscaler to perform a DNS lookup and override the externally resolved IP addresses in the outbound HTTP and HTTPS connections to establish a connection to the destination server that is geographically closer to the ZIA Service Edge (Public, Private, or Virtual). |
| enableEvaluatePolicyOnGlobalSSLBypass | boolean | No | A Boolean value indicating whether policy evaluation for global SSL bypass traffic is enabled or not |
| enableIPv6DnsOptimizationOnAllTransparentProxy | boolean | No | A Boolean value indicating whether DNS optimization is enabled or disabled for all IPv6 transparent proxy traffic |
| enableIPv6DnsResolutionOnTransparentProxy | boolean | No | A Boolean value indicating whether DNS optimization is enabled or disabled for IPv6 traffic sent via Z-Tunnel 2.0 and [transparent proxy](/zia/what-proxy-mode#transparent-mode) mode traffic (e.g., traffic via GRE or IPSec tunnels without a PAC file). |
| enableOffice365 | boolean | No | A Boolean value indicating whether Microsoft Office 365 One Click Configuration is enabled or not |
| enablePolicyForUnauthenticatedTraffic | boolean | No | A Boolean value indicating whether policies that include user and department criteria can be configured and applied for unauthenticated traffic |
| enforceSurrogateIpForWindowsApp | boolean | No | Enforce Surrogate IP authentication for Windows app traffic |
| http2NonbrowserTrafficEnabled | boolean | No | A Boolean value indicating whether or not HTTP/2 should be the default web protocol for accessing various applications at your organizational level |
| httpRangeHeaderRemoveUrlCategories | array[WebFilteringUrlCategory] | No | URL categories for which HTTP range headers must be removed |
| kerberosBypassApps | array[PolicyWebApplication] | No | Cloud applications that are exempted from Kerberos authentication |
| kerberosBypassUrlCategories | array[WebFilteringUrlCategory] | No | URL categories that are exempted from Kerberos authentication |
| kerberosBypassUrls | array[string] | No | Custom URLs that are exempted from Kerberos authentication |
| logInternalIp | boolean | No | A Boolean value indicating whether to log internal IP address present in X-Forwarded-For (XFF) proxy header or not |
| preferSniOverConnHost | boolean | No | A Boolean value indicating whether or not to use the SSL/TLS client hello Server Name Indication (SNI) for DNS resolution instead of the CONNECT host for forward proxy connections |
| preferSniOverConnHostApps | array[PolicyWebApplication] | No | Applications that are exempted from the **preferSniOverConnHost** setting |
| sipaXffHeaderEnabled | boolean | No | A Boolean value indicating whether or not to insert XFF header to all traffic forwarded from ZIA to ZPA, including source IP-anchored and ZIA-inspected ZPA application traffic. |
| sniDnsOptimizationBypassUrlCategories | array[WebFilteringUrlCategory] | No | URL categories that are excluded from the preferSniOverConnHost setting (i.e., prefer SSL/TLS client hello SNI for DNS resolution instead of the CONNECT host for forward proxy connections) |
| trackHttpTunnelOnHttpPorts | boolean | No | A Boolean value indicating whether to apply configured policies on tunneled HTTP traffic sent via a CONNECT method request on port 80 |
| uiSessionTimeout | integer (int32) | No | Specifies the login session timeout for admins accessing the ZIA Admin Portal |
| zscalerClientConnector1AndPacRoadWarriorInFirewall | boolean | No | A Boolean value indicating whether to apply the Firewall rules configured without a specified location criteria (or with the Road Warrior location) to remote user traffic forwarded via Z-Tunnel 1.0 or PAC files |

### EntityReference
This is an immutable reference to an entity that mainly consists of id and name.
| Field | Type | Required | Description |
| ----- | ---- | -------- | ----------- |
| extensions | object | No | Additional information about the entity |
| externalId | string | No | An external identifier used for an entity that is managed outside of ZIA. Examples include `zpaServerGroup` and `zpaAppSegments`. This field is not applicable to ZIA-managed entities. |
| id | integer (int64) | No | A unique identifier for an entity |
| name | string | No | The configured name of the entity |

### PolicyWebApplication
| Field | Type | Required | Description |
| ----- | ---- | -------- | ----------- |
| appCatModified | boolean | No |  |
| appNotReady | boolean | No |  |
| backendName | string | No |  |
| deprecated | boolean | No |  |
| misc | boolean | No |  |
| name | string | No |  |
| originalName | string | No |  |
| underMigration | boolean | No |  |
| val | integer (int32) | No |  |
| webApplicationClass | string | No | The cloud application class selected from the available options |

### WebFilteringUrlCategory
| Field | Type | Required | Description |
| ----- | ---- | -------- | ----------- |
| backendName | string | No |  |
| comments | string | No |  |
| deprecated | boolean | No |  |
| mask | integer (int32) | No |  |
| name | string | No |  |
| urlSupercategory | string | No |  |
| userConfiguredName | string | No |  |
| val | integer (int32) | No |  |
