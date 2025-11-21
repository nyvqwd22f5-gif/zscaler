# Traffic Forwarding
Source: https://help.zscaler.com/zia/traffic-forwarding-0

API Reference Guide for the ZIA Cloud Service and Sandbox Submission APIs

**Base URL:** https://zsapi.[zscaler-cloud-name]/api/v1

## `GET /datacenters`

Retrieves the list of Zscaler data centers (DCs) that can be excluded from service to your organization

**Tags:** Traffic Forwarding
**Consumes:** application/json
**Produces:** application/json

| Name | In | Type | Required | Description |
| ---- | --- | ---- | -------- | ----------- |
| page | query | integer | No | Specifies the page offset |
| pageSize | query | integer | No | Specifies the page size. The default size is 250. |

| Code | Description | Schema |
| ---- | ----------- | ------ |
| 200 | Successful Operation | array[Datacenter] |

## `GET /dcExclusions`

Retrieves the list of Zscaler data centers (DCs) that are currently excluded from service to your organization based on configured exclusions in the ZIA Admin Portal

**Tags:** Traffic Forwarding
**Consumes:** application/json
**Produces:** application/json
No parameters.

| Code | Description | Schema |
| ---- | ----------- | ------ |
| 200 | Successful Operation | array[TenantDCExclusion] |

## `POST /dcExclusions`

Adds a data center (DC) exclusion to disable the tunnels terminating at a virtual IP address of a Zscaler DC, triggering a failover from primary to secondary tunnels in the event of service disruptions, [Zscaler Trust Portal](https://trust.zscaler.com) incidents, disasters, etc. You can configure to exclude a specific DC based on the traffic forwarding method for a designated time period.
**Note**: Currently, only the IPSec VPN tunnel forwarding method is supported for DC exclusion. To learn more, see [Excluding a Data Center Based on Traffic Forwarding Method](/zia/excluding-data-center-based-traffic-forwarding-method).

**Tags:** Traffic Forwarding
**Consumes:** application/json
**Produces:** application/json

| Name | In | Type | Required | Description |
| ---- | --- | ---- | -------- | ----------- |
| body | body | array[TenantDCExclusion] | No | Information about the DC exclusion configuration |

| Code | Description | Schema |
| ---- | ----------- | ------ |
| 200 | Successful Operation | array[TenantDCExclusion] |

## `PUT /dcExclusions`

Updates a Zscaler data center (DC) exclusion configuration based on the specified ID. To learn more about the DC exclusion configuration, see [Excluding a Data Center Based on Traffic Forwarding Method](/zia/excluding-data-center-based-traffic-forwarding-method).

**Tags:** Traffic Forwarding
**Consumes:** application/json
**Produces:** application/json

| Name | In | Type | Required | Description |
| ---- | --- | ---- | -------- | ----------- |
| body | body | array[TenantDCExclusion] | No | The unique identifier for the DC exclusion configuration |

| Code | Description | Schema |
| ---- | ----------- | ------ |
| 200 | Successful Operation | array[TenantDCExclusion] |

## `DELETE /dcExclusions/{dcId}`

Deletes a Zscaler data center (DC) exclusion configuration based on the specified ID. The DC exclusion configuration ID can be obtained by sending a GET request to `/dcExclusions`.

**Tags:** Traffic Forwarding
**Consumes:** application/json
**Produces:** application/json

| Name | In | Type | Required | Description |
| ---- | --- | ---- | -------- | ----------- |
| dcId | path | integer | Yes | The unique identifier for the DC exclusion configuration |

| Code | Description | Schema |
| ---- | ----------- | ------ |
| default | Successful Operation |  |

## `GET /extranet`

Retrieves the list of extranets configured for the organization. Extranets are configured as part of Zscaler Extranet Application Support which allows an organization to connect its internal network with another organization’s network (e.g., partners, third-party vendors, etc.) that does not use the Zscaler service. Extranet Application Support enables Zscaler-managed organization users to securely access extranet resources through an IPSec VPN tunnel established between the Zscaler data center and the external organization’s data center, without requiring additional hardware or software installations.
To learn more, see [Understanding Extranet Application Support](/zia/understanding-extranet-application-support) and [About Extranet](/zia/about-extranet).

**Tags:** Traffic Forwarding
**Consumes:** application/json
**Produces:** application/json

| Name | In | Type | Required | Description |
| ---- | --- | ---- | -------- | ----------- |
| pageSize | query | integer | No | Specifies the page size. The default size is 200. |
| page | query | integer | No | Specifies the page offset |
| orderBy | query | string | No | The field used to sort the list in a specific order |
| order | query | string | No | The arrangement of the list in ascending or descending order |
| search | query | string | No | The search string used to match against specific extranets |

| Code | Description | Schema |
| ---- | ----------- | ------ |
| 200 | Successful Operation | array[Extranet] |

## `POST /extranet`

Adds a new extranet for the organization. Extranets are configured as part of Zscaler Extranet Application Support which allows an organization to connect its internal network with another organization’s network (e.g., partners, third-party vendors, etc.) that does not use the Zscaler service. Extranet Application Support enables Zscaler-managed organization users to securely access extranet resources through an IPSec VPN tunnel established between the Zscaler data center and the external organization’s data center, without requiring additional hardware or software installations.
To learn more, see [Understanding Extranet Application Support](/zia/understanding-extranet-application-support) and [Configuring an Extranet](/zia/configuring-extranet).

**Tags:** Traffic Forwarding
**Consumes:** application/json
**Produces:** application/json

| Name | In | Type | Required | Description |
| ---- | --- | ---- | -------- | ----------- |
| body | body | Extranet | No | Information about the extranet |

| Code | Description | Schema |
| ---- | ----------- | ------ |
| 200 | Successful Operation | Extranet |

## `PUT /extranet`

Updates an extranet based on the specified ID

**Tags:** Traffic Forwarding
**Consumes:** application/json
**Produces:** application/json

| Name | In | Type | Required | Description |
| ---- | --- | ---- | -------- | ----------- |
| body | body | Extranet | No | Information about the extranet |

| Code | Description | Schema |
| ---- | ----------- | ------ |
| 200 | Successful Operation | Extranet |

## `GET /extranet/lite`

Retrieves the name-ID pairs of all extranets configured for an organization

**Tags:** Traffic Forwarding
**Consumes:** application/json
**Produces:** application/json
No parameters.

| Code | Description | Schema |
| ---- | ----------- | ------ |
| 200 | Successful Operation | array[EntityReference] |

## `DELETE /extranet/{id}`

Deletes an extranet based on the specified ID

**Tags:** Traffic Forwarding
**Consumes:** application/json
**Produces:** application/json

| Name | In | Type | Required | Description |
| ---- | --- | ---- | -------- | ----------- |
| id | path | string | Yes | The ID of the extranet that can be obtained by sending a GET request to `/extranet/lite` or `/extranet` |

| Code | Description | Schema |
| ---- | ----------- | ------ |
| default | Successful Operation |  |

## `GET /extranet/{id}`

Retrieves information about an extranet based on the specified ID

**Tags:** Traffic Forwarding
**Consumes:** application/json
**Produces:** application/json

| Name | In | Type | Required | Description |
| ---- | --- | ---- | -------- | ----------- |
| id | path | integer | Yes | The ID of the extranet that can be obtained by sending a GET request to `/extranet/lite` or `/extranet` |

| Code | Description | Schema |
| ---- | ----------- | ------ |
| 200 | Successful Operation | Extranet |

## `GET /greTunnels`

Gets all provisioned GRE tunnel information.

**Tags:** Traffic Forwarding
**Produces:** application/json

| Name | In | Type | Required | Description |
| ---- | --- | ---- | -------- | ----------- |
| page | query | integer | No | Specifies the page offset. |
| pageSize | query | integer | No | Specifies the page size. The default size is 100, but the maximum size is 1000. |

| Code | Description | Schema |
| ---- | ----------- | ------ |
| 200 | Successful Operation | array[GreTunnel] |

## `POST /greTunnels`

Adds a GRE tunnel configuration.
**Note:** Specifying  `withinCountryOnly` or `subcloud` parameter is  mandatory if this endpoint uses a virtual IP address (VIP) retrieved by  passing either of these parameters in `GET /vips/recommendedList`.

**Tags:** Traffic Forwarding
**Consumes:** application/json
**Produces:** application/json

| Name | In | Type | Required | Description |
| ---- | --- | ---- | -------- | ----------- |
| body | body | GreTunnel | Yes |  |

| Code | Description | Schema |
| ---- | ----------- | ------ |
| 200 | Successful Operation | GreTunnel |

## `GET /greTunnels/availableInternalIpRanges`

Gets the next available GRE tunnel internal IP address ranges.

**Tags:** Traffic Forwarding
**Produces:** application/json

| Name | In | Type | Required | Description |
| ---- | --- | ---- | -------- | ----------- |
| internalIpRange | query | string | No | Internal IP range information. |
| staticIp | query | string | No | Static IP information. |
| limit | query | integer | No | The maximum number of GRE tunnel IP ranges that can be added. |

| Code | Description | Schema |
| ---- | ----------- | ------ |
| 200 | Successful Operation | array[GreTunnelIPRange] |

## `DELETE /greTunnels/{Id}`

Deletes the GRE tunnel information for the specified ID.

**Tags:** Traffic Forwarding
**Consumes:** application/json
**Produces:** application/json

| Name | In | Type | Required | Description |
| ---- | --- | ---- | -------- | ----------- |
| Id | path | integer | Yes | The unique identifier for the GRE tunnel. |

| Code | Description | Schema |
| ---- | ----------- | ------ |
| 204 | Successful Operation |  |

## `GET /greTunnels/{Id}`

Gets the GRE tunnel information for the specified ID.

**Tags:** Traffic Forwarding
**Produces:** application/json

| Name | In | Type | Required | Description |
| ---- | --- | ---- | -------- | ----------- |
| Id | path | integer | Yes | The unique identifier for the GRE tunnel. |

| Code | Description | Schema |
| ---- | ----------- | ------ |
| 200 | Successful Operation | GreTunnel |

## `PUT /greTunnels/{Id}`

Updates the GRE tunnel information for the specified ID.

**Tags:** Traffic Forwarding
**Consumes:** application/json
**Produces:** application/json

| Name | In | Type | Required | Description |
| ---- | --- | ---- | -------- | ----------- |
| Id | path | integer | Yes | The unique identifier for the GRE tunnel. |
| body | body | GreTunnel | Yes | GRE tunnel information. |

| Code | Description | Schema |
| ---- | ----------- | ------ |
| 200 | Successful Operation | GreTunnel |

## `GET /ipv6config`

Gets the [IPv6 configuration](/zia/configuring-ipv6-settings) details for the organization. For information about IPv6 support, see [Understanding IPv6 Support](/zia/understanding-ipv6-support).

**Tags:** Traffic Forwarding
**Consumes:** application/json
**Produces:** application/json
No parameters.

| Code | Description | Schema |
| ---- | ----------- | ------ |
| 200 | Successful Operation | IPv6Configuration |

## `GET /ipv6config/dns64prefix`

Gets the list of NAT64 prefixes configured as the DNS64 prefix for the organization. To learn more, see [About the DNS64 Prefix](/zia/about-dns64-prefix).

**Tags:** Traffic Forwarding
**Consumes:** application/json
**Produces:** application/json

| Name | In | Type | Required | Description |
| ---- | --- | ---- | -------- | ----------- |
| search | query | string | No | The search string used to match against a DNS64 prefix’s `name`, `description`, or `prefixMask` attributes. |

| Code | Description | Schema |
| ---- | ----------- | ------ |
| 200 | Successful Operation | array[IPv6PrefixMask] |

## `GET /ipv6config/nat64prefix`

Gets the list of NAT64 prefixes configured for the organization. The  prefix which has the `dnsPrefix` field set to `true` is identified as the DNS64 prefix. To learn more, see [About NAT64 Prefixes](/zia/about-nat64-prefixes).

**Tags:** Traffic Forwarding
**Consumes:** application/json
**Produces:** application/json

| Name | In | Type | Required | Description |
| ---- | --- | ---- | -------- | ----------- |
| search | query | string | No | The search string used to match against a NAT64 prefix’s `name`, `description`, or `prefixMask` attributes. |
| page | query | integer | No | Specifies the page offset. |
| pageSize | query | integer | No | Specifies the page size. The default size is 100 and the maximum size  is 1000. |

| Code | Description | Schema |
| ---- | ----------- | ------ |
| 200 | Successful Operation | array[IPv6PrefixMask] |

## `GET /orgProvisioning/ipGreTunnelInfo`

Gets a list of IP addresses with GRE tunnel details.

**Tags:** Traffic Forwarding
**Consumes:** application/json
**Produces:** application/json

| Name | In | Type | Required | Description |
| ---- | --- | ---- | -------- | ----------- |
| ipAddresses | query | array | No | Filter based on an IP address range. |

| Code | Description | Schema |
| ---- | ----------- | ------ |
| 200 | Successful Operation | array[IpDetails] |

## `GET /region/byGeoCoordinates`

Retrieves the geographical data of the region or city that is located in the specified latitude and longitude coordinates. The geographical data includes the city name, state, country, geographical ID of the city and state, etc.

**Tags:** Traffic Forwarding
**Produces:** application/json

| Name | In | Type | Required | Description |
| ---- | --- | ---- | -------- | ----------- |
| latitude | query | number | Yes | The latitude coordinate of the city or region |
| longitude | query | number | Yes | The longitude coordinate of the city or region |

| Code | Description | Schema |
| ---- | ----------- | ------ |
| 200 | Successful Operation | RegionInfo |

## `GET /region/byIPAddress/{ip}`

Retrieves information about the geo-location of the specified IP address, including the city, state, and country of location, geographical ID of the city and state, postal code, etc.

**Tags:** Traffic Forwarding
**Produces:** application/json

| Name | In | Type | Required | Description |
| ---- | --- | ---- | -------- | ----------- |
| ip | path | string | Yes | The IP address for which you want to retrieve the geo-location and other geographical data. |

| Code | Description | Schema |
| ---- | ----------- | ------ |
| 200 | Successful Operation | RegionInfo |

## `GET /region/search`

Retrieves the list of cities (along with their geographical data) that match the prefix search. The geographical data includes the latitude and longitude coordinates of the city, geographical ID of the city and state, country, postal code, etc.

**Tags:** Traffic Forwarding
**Produces:** application/json

| Name | In | Type | Required | Description |
| ---- | --- | ---- | -------- | ----------- |
| prefix | query | string | No | The string used in the prefix search of the city or region. The prefix can contain names of city, state, country in the following format: `city name, state name, country name`. A phrase for city name is mandatory, whereas the state and country names can be optionally provided to narrow down the search results. |
| page | query | integer | No | Specifies the page offset |
| pageSize | query | integer | No | Specifies the page size. The default size is 100 and the maximum size is 1,000. |

| Code | Description | Schema |
| ---- | ----------- | ------ |
| 200 | Successful Operation | array[RegionInfo] |

## `GET /staticIP`

Gets all provisioned static IP addresses.

**Tags:** Traffic Forwarding
**Produces:** application/json

| Name | In | Type | Required | Description |
| ---- | --- | ---- | -------- | ----------- |
| availableForGreTunnel | query | boolean | No | Set to true to get only the static IP addresses that are not yet associated to a GRE tunnel. |
| ipAddress | query | string | No | Filter based on IP address |
| page | query | integer | No | Specifies the page offset. |
| pageSize | query | integer | No | Specifies the page size. The default size is 100, but the maximum size is 1000. |

| Code | Description | Schema |
| ---- | ----------- | ------ |
| 200 | Successful Operation | array[StaticIP] |

## `POST /staticIP`

Adds a static IP address.

**Tags:** Traffic Forwarding
**Produces:** application/json

| Name | In | Type | Required | Description |
| ---- | --- | ---- | -------- | ----------- |
| body | body | StaticIP | Yes | Static IP address information. |

| Code | Description | Schema |
| ---- | ----------- | ------ |
| 200 | Successful Operation | StaticIP |

## `POST /staticIP/validate`

Validates the static IP address.

**Tags:** Traffic Forwarding
**Produces:** application/json

| Name | In | Type | Required | Description |
| ---- | --- | ---- | -------- | ----------- |
| body | body | StaticIP | Yes | The static IP address information. |

| Code | Description | Schema |
| ---- | ----------- | ------ |
| 200 | Successful Operation | string |

## `DELETE /staticIP/{Id}`

Deletes the static IP address for the specified ID.

**Tags:** Traffic Forwarding
**Consumes:** application/json
**Produces:** application/json

| Name | In | Type | Required | Description |
| ---- | --- | ---- | -------- | ----------- |
| Id | path | integer | Yes | The unique identifier for the provisioned static IP address. |

| Code | Description | Schema |
| ---- | ----------- | ------ |
| 204 | Successful Operation |  |

## `GET /staticIP/{Id}`

Gets static IP address for the specified ID

**Tags:** Traffic Forwarding
**Produces:** application/json

| Name | In | Type | Required | Description |
| ---- | --- | ---- | -------- | ----------- |
| Id | path | integer | Yes | The unique identifier for the provisioned static IP address. |

| Code | Description | Schema |
| ---- | ----------- | ------ |
| 200 | Successful Operation | StaticIP |

## `PUT /staticIP/{Id}`

Updates the static IP address for the specified ID.

**Tags:** Traffic Forwarding
**Consumes:** application/json
**Produces:** application/json

| Name | In | Type | Required | Description |
| ---- | --- | ---- | -------- | ----------- |
| Id | path | integer | Yes | The unique identifier for the provisioned static IP address. |
| body | body | StaticIP | Yes | The static IP address information. |

| Code | Description | Schema |
| ---- | ----------- | ------ |
| 200 | Successful Operation | StaticIP |

## `GET /subclouds`

Retrieves all the subclouds and the excluded data centers that are associated with the subcloud

**Tags:** Traffic Forwarding
**Produces:** application/json

| Name | In | Type | Required | Description |
| ---- | --- | ---- | -------- | ----------- |
| page | query | integer | No | Page offset |
| pageSize | query | integer | No | Page size |

| Code | Description | Schema |
| ---- | ----------- | ------ |
| 200 | Successful Operation | array[TenantSubCloudSummary] |

## `GET /subclouds/isLastDcInCountry/{id}`

Retrieves the list of all the excluded data centers in a country

**Tags:** Traffic Forwarding
**Produces:** application/json

| Name | In | Type | Required | Description |
| ---- | --- | ---- | -------- | ----------- |
| id | path | integer | Yes | Unique identifier for the country |
| dcId | query | array | No | Data center ID |

| Code | Description | Schema |
| ---- | ----------- | ------ |
| 200 | Successful Operation | array[SubCloudCountryDCExclusionInfo] |

## `PUT /subclouds/{id}`

Updates the subcloud and excluded data centers based on the specified ID

**Tags:** Traffic Forwarding
**Consumes:** application/json
**Produces:** application/json

| Name | In | Type | Required | Description |
| ---- | --- | ---- | -------- | ----------- |
| id | path | integer | Yes | Unique identifier for the excluded data center |
| body | body | TenantSubCloudExclusions | Yes | Information about the excluded data center |

| Code | Description | Schema |
| ---- | ----------- | ------ |
| 200 | Successful Operationabout-tenant-profiles | TenantSubCloudExclusions |

## `GET /vips`

Gets a paginated list of the virtual IP addresses (VIPs) available in the Zscaler cloud, including region and data center information. By default, the request gets all public VIPs in the cloud, but you can also include private or all VIPs in the request, if necessary.

**Tags:** Traffic Forwarding
**Consumes:** application/json
**Produces:** application/json

| Name | In | Type | Required | Description |
| ---- | --- | ---- | -------- | ----------- |
| dc | query | string | No | Filter based on data center. |
| region | query | string | No | Filter based on region. |
| page | query | integer | No | Specifies the page offset. |
| pageSize | query | integer | No | Specifies the page size. The default size is 100, but the maximum size is 1000. |
| include | query | string | No | Include all, private, or public VIPs in the list. |
| subcloud | query | string | No | Filter based on the subcloud for the VIP. To learn more see, [About Subcloud](/zia/what-subcloud). |

| Code | Description | Schema |
| ---- | ----------- | ------ |
| 200 | Successful Operation | array[PublicNode] |

## `GET /vips/groupByDatacenter`

Gets a list of recommended GRE tunnel virtual IP addresses (VIPs), grouped by data center, based on source IP address or latitude/longitude coordinates.

**Tags:** Traffic Forwarding
**Consumes:** application/json
**Produces:** application/json

| Name | In | Type | Required | Description |
| ---- | --- | ---- | -------- | ----------- |
| routableIP | query | boolean | No | The routable IP address. |
| withinCountryOnly | query | boolean | No | Search within country only. |
| includePrivateServiceEdge | query | boolean | No | Include ZIA Private Service Edge VIPs. |
| includeCurrentVips | query | boolean | No | Include currently assigned VIPs. |
| sourceIp | query | string | No | The source IP address. |
| latitude | query | number | No | The latitude coordinate of the GRE tunnel source. |
| longitude | query | number | No | The longitude coordinate of the GRE tunnel source. |
| subcloud | query | string | No | The subcloud for the VIP. To learn more see, [About Subcloud](/zia/what-subcloud). |

| Code | Description | Schema |
| ---- | ----------- | ------ |
| 200 | Successful Operation | array[DatacenterVips] |

## `GET /vips/recommendedList`

Gets a list of recommended GRE tunnel virtual IP addresses (VIPs), based on source IP address or latitude/longitude coordinates.

**Tags:** Traffic Forwarding
**Consumes:** application/json
**Produces:** application/json

| Name | In | Type | Required | Description |
| ---- | --- | ---- | -------- | ----------- |
| routableIP | query | boolean | No | The routable IP address. |
| withinCountryOnly | query | boolean | No | Search within country only. |
| includePrivateServiceEdge | query | boolean | No | Include ZIA Private Service Edge VIPs. |
| includeCurrentVips | query | boolean | No | Include currently assigned VIPs. |
| sourceIp | query | string | No | The source IP address. |
| latitude | query | number | No | The latitude coordinate of the GRE tunnel source. |
| longitude | query | number | No | The longitude coordinate of the GRE tunnel source. |
| subcloud | query | string | No | The subcloud for the VIP. To learn more see, [About Subcloud](/zia/what-subcloud). |

| Code | Description | Schema |
| ---- | ----------- | ------ |
| 200 | Successful Operation | array[GreVirtualIp] |

## `GET /vpnCredentials`

Gets VPN credentials that can be associated to locations. To learn more, see [About VPN Credentials](/zia/about-vpn-credentials).

**Tags:** Traffic Forwarding
**Consumes:** application/json
**Produces:** application/json

| Name | In | Type | Required | Description |
| ---- | --- | ---- | -------- | ----------- |
| search | query | string | No | The search string used to match against a VPN credential's commonName, fqdn, ipAddress, comments, or locationName attributes. |
| type | query | string | No | Only gets VPN credentials for the specified type. This parameter is not supported for partner API keys. |
| includeOnlyWithoutLocation | query | boolean | No | Include VPN credential only if not associated to any location. |
| locationId | query | integer | No | Gets the VPN credentials for the specified location ID. |
| managedBy | query | integer | No | Gets the VPN credentials that are managed by the given partner. This filter is automatically applied when called with a partner API key, and it cannot be overridden. |
| page | query | integer | No | Specifies the page offset. |
| pageSize | query | integer | No | Specifies the page size. The default size is 100, but the maximum size is 1000. |

| Code | Description | Schema |
| ---- | ----------- | ------ |
| 200 | Successful Operation | array[VPNCredential] |

## `POST /vpnCredentials`

Adds VPN credentials that can be associated to locations. When invoked with a partner API key, it automatically sets the managedBy attribute to the partner associated with the key. To learn more, see [Adding VPN Credentials](/zia/adding-vpn-credentials).

**Tags:** Traffic Forwarding
**Consumes:** application/json
**Produces:** application/json

| Name | In | Type | Required | Description |
| ---- | --- | ---- | -------- | ----------- |
| vpnCred | body | VPNCredential | No | VPN credential information. |

| Code | Description | Schema |
| ---- | ----------- | ------ |
| 200 | Successful Operation | VPNCredential |

## `POST /vpnCredentials/bulkDelete`

Bulk delete VPN credentials up to a maximum of 100 credentials per request. The response returns the VPN IDs that were successfully deleted.

**Tags:** Traffic Forwarding
**Consumes:** application/json
**Produces:** application/json

| Name | In | Type | Required | Description |
| ---- | --- | ---- | -------- | ----------- |
| ids | body | IdListInteger | No | The VPN IDs to bulk delete |

| Code | Description | Schema |
| ---- | ----------- | ------ |
| 204 | Successful Operation |  |
| 404 | If the payload includes VPN IDs that are invalid a ['Resource does not exist' error](/zia/about-error-handling) is returned, but information about the invalid IDs is not included. |  |

## `DELETE /vpnCredentials/{vpnId}`

Deletes the VPN credentials for the specified ID.

**Tags:** Traffic Forwarding
**Consumes:** application/json
**Produces:** application/json

| Name | In | Type | Required | Description |
| ---- | --- | ---- | -------- | ----------- |
| vpnId | path | integer | Yes | The unique identifier for the VPN credential. |

| Code | Description | Schema |
| ---- | ----------- | ------ |
| 204 | Successful Operation. No Content Returned. |  |

## `GET /vpnCredentials/{vpnId}`

Gets the VPN credentials for the specified ID.

**Tags:** Traffic Forwarding
**Consumes:** application/json
**Produces:** application/json

| Name | In | Type | Required | Description |
| ---- | --- | ---- | -------- | ----------- |
| vpnId | path | integer | Yes | The unique identifier for the VPN credential. |

| Code | Description | Schema |
| ---- | ----------- | ------ |
| 200 | Successful Operation | VPNCredential |

## `PUT /vpnCredentials/{vpnId}`

Updates the VPN credentials for the specified ID.

**Tags:** Traffic Forwarding
**Consumes:** application/json
**Produces:** application/json

| Name | In | Type | Required | Description |
| ---- | --- | ---- | -------- | ----------- |
| vpnId | path | integer | Yes | The unique identifier for the VPN credential. |
| vpnCred | body | VPNCredential | No | VPN credential information. |

| Code | Description | Schema |
| ---- | ----------- | ------ |
| 200 | Successful Operation | VPNCredential |

## Models
### Datacenter
Zscaler data center information.
| Field | Type | Required | Description |
| ----- | ---- | -------- | ----------- |
| datacenter | string | No | Zscaler data center name. |

### DatacenterCountry
| Field | Type | Required | Description |
| ----- | ---- | -------- | ----------- |
| country | string | No | Country name |
| id | integer (int32) | No | Data center ID for the country |
| name | string | No | Data center name |

### DatacenterVips
GRE cluster virtual IP addresses (VIPs) that belong to a Zscaler data center.
| Field | Type | Required | Description |
| ----- | ---- | -------- | ----------- |
| datacenter | object | No | Zscaler data center details. |
| greVips | array[GreVirtualIp] | No | GRE cluster virtual IP addresses (VIPs). |

### EntityReference
This is an immutable reference to an entity that mainly consists of id and name
| Field | Type | Required | Description |
| ----- | ---- | -------- | ----------- |
| extensions | object | No | Additional information about the entity |
| externalId | string | No | An external identifier used for an entity that is managed outside of ZIA. Examples include `zpaServerGroup` and `zpaAppSegments`. This field is not applicable to ZIA-managed entities. |
| id | integer (int64) | No | A unique identifier for an entity |
| name | string | No | The configured name of the entity |

### Extranet
Information about the extranet
| Field | Type | Required | Description |
| ----- | ---- | -------- | ----------- |
| createdAt | integer (int32) | No | The Unix timestamp when the extranet was created |
| description | string | No | The description of the extranet |
| extranetDNSList | array[Extranet_DNS] | No | Information about the DNS servers specified for the extranet |
| extranetIpPoolList | object | No | Information about the traffic selectors specified for the extranet. Type: Array |
| id | integer (int32) | No | The unique identifier for the extranet |
| modifiedAt | integer (int32) | No | The Unix timestamp when the extranet was last modified |
| name | string | No | The name of the extranet |

### Extranet_DNS
Information about the DNS servers specified for the extranet
| Field | Type | Required | Description |
| ----- | ---- | -------- | ----------- |
| id | integer (int32) | No | The ID generated for the DNS server configuration |
| name | string | Yes | The name of the DNS server |
| primaryDNSServer | string | No | The IP address of the primary DNS server |
| secondaryDNSServer | string | No | The IP address of the secondary DNS server |
| useAsDefault | boolean | No | A Boolean value indicating that the DNS servers specified in the extranet are the designated default servers |

### GreTunnel
GRE tunnel information
| Field | Type | Required | Description |
| ----- | ---- | -------- | ----------- |
| comment | string | No | Additional information about this GRE tunnel |
| id | integer (int32) | No | Unique identifier of the static IP address that is associated to a GRE tunnel |
| internalIpRange | string | No | The start of the internal IP address in /29 CIDR range |
| ipUnnumbered | boolean | No | This is required to support the automated SD-WAN provisioning of GRE tunnels, when set to true gre_tun_ip and gre_tun_id are set to null |
| lastModificationTime | integer (int32) | No | When the GRE tunnel information was last modified |
| lastModifiedBy | object | No | Who modified the GRE tunnel information last |
| managedBy | object | No | SD-WAN Partner that manages the location. If a partner does not manage the location, this is set to Self. |
| primaryDestVip | object | No | The primary destination data center and virtual IP address (VIP) of the GRE tunnel |
| secondaryDestVip | object | No | The secondary destination data center and virtual IP address (VIP) of the GRE tunnel |
| sourceIp | string | No | The source IP address of the GRE tunnel. This is typically a static IP address in the organization or SD-WAN. This IP address must be provisioned within the Zscaler service using the /staticIP endpoint. |
| subcloud | string | No | Restrict the data center virtual IP addresses (VIPs) only to those part of the subcloud |
| withinCountry | boolean | No | Restrict the data center virtual IP addresses (VIPs) only to those within the same country as the source IP address |

### GreTunnelIPRange
| Field | Type | Required | Description |
| ----- | ---- | -------- | ----------- |
| endIPAddress | string | No | Ending IP address in the range |
| startIPAddress | string | No | Starting IP address in the range |

### GreVirtualIp
GRE cluster virtual IP address (VIP) and data center information
| Field | Type | Required | Description |
| ----- | ---- | -------- | ----------- |
| datacenter | string | No | Data center information |
| id | integer (int32) | No | Unique identifer of the GRE virtual IP address (VIP) |
| privateServiceEdge | boolean | No | Set to true if the virtual IP address (VIP) is a ZIA Private Service Edge |
| virtualIp | string | No | GRE cluster virtual IP address (VIP) |

### IPv6Configuration
IPv6 configuration details.
| Field | Type | Required | Description |
| ----- | ---- | -------- | ----------- |
| dnsPrefix | object | No | DNS64 prefix information. |
| ipV6Enabled | boolean | No | If set to true, IPv6 support is enabled for your organization. You can forward IPv6 traffic to the Zscaler service and enforce security  policies. If set to false, IPv6 support is disabled for your organization. |
| natPrefixes | array[IPv6PrefixMask] | No | NAT64 prefix information. |

### IPv6PrefixMask
NAT64/DNS64 prefix information.
| Field | Type | Required | Description |
| ----- | ---- | -------- | ----------- |
| description | string | No | The description of the NAT64 prefix. |
| dnsPrefix | boolean | No | Indicates whether or not this NAT64 prefix is the DNS64 prefix. |
| id | integer (int32) | No | A unique identifier for the NAT64 prefix. |
| name | string | No | The name of the NAT64 prefix. |
| nonEditable | boolean | No | Indicates whether or not this NAT64 prefix is editable. |
| prefixMask | string | No | The subnet mask for the NAT64 prefix. |

### IdListInteger
| Field | Type | Required | Description |
| ----- | ---- | -------- | ----------- |
| ids | array[integer (int32)] | No |  |

### IpDetails
| Field | Type | Required | Description |
| ----- | ---- | -------- | ----------- |
| greEnabled | boolean | No |  |
| greRangePrimary | string | No |  |
| greRangeSecondary | string | No |  |
| greTunnelIP | string | No |  |
| ipAddress | string | No |  |
| primaryGW | string | No |  |
| secondaryGW | string | No |  |
| tunID | integer (int32) | No |  |

### PublicNode
Public node details
| Field | Type | Required | Description |
| ----- | ---- | -------- | ----------- |
| city | string | No | The city. |
| cloudName | string | No | The Zscaler cloud name. |
| country | string | No | The country. |
| dataCenter | string | No | Data center name. |
| greDomainName | string | No | The proxy host name. |
| greIps | array[string] | No | The GRE IP addresses. |
| location | string | No | The location coordinates. |
| pacDomainName | string | No | The PAC server domain name. |
| pacIps | array[string] | No | The PAC IP addresses. |
| region | string | No | The region. |
| svpnDomainName | string | No | The PAC server domain name. |
| svpnIps | array[string] | No | The PAC IP addresses. |
| vpnDomainName | string | No | The VPN server domain name. |
| vpnIps | array[string] | No | The VPN IP addresses. |

### RegionInfo
Information about a region or a city
| Field | Type | Required | Description |
| ----- | ---- | -------- | ----------- |
| cityGeoId | integer (int32) | No | The geographical ID of the city |
| cityName | string | No | The name of the city |
| continentCode | string | No | The ISO standard two-letter continent code |
| countryCode | string | No | The ISO standard two-letter country code |
| countryName | string | No | The name of the country |
| latitude | number (double) | No | The latitude coordinate of the city |
| longitude | number (double) | No | The longitude coordinate of the city |
| postalCode | string | No | The postal code |
| stateGeoId | integer (int32) | No | The geographical ID of the state |
| stateName | string | No | The name of the state, province, or territory of a country |

### StaticIP
Static IP address information
| Field | Type | Required | Description |
| ----- | ---- | -------- | ----------- |
| comment | string | No | Additional information about this static IP address |
| geoOverride | boolean | No | If not set, geographic coordinates and city are automatically determined from the IP address. Otherwise, the latitude and longitude coordinates must be provided. |
| id | integer (int32) | No | The unique identifier for the static IP address |
| ipAddress | string | No | The static IP address |
| lastModificationTime | integer (int32) | No | When the static IP address was last modified |
| lastModifiedBy | EntityReference | No | Who modified the static IP address last |
| latitude | number (double) | Yes | Required only if the geoOverride attribute is set. Latitude with 7 digit precision after decimal point, ranges between -90 and 90 degrees. |
| longitude | number (double) | Yes | Required only if the geoOverride attribute is set. Longitude with 7 digit precision after decimal point, ranges between -180 and 180 degrees. |
| managedBy | EntityReference | No | SD-WAN Partner that manages the location. If a partner does not manage the location, this is set to Self. |
| routableIP | boolean | No | Indicates whether a non-RFC 1918 IP address is publicly routable. This attribute is ignored if there is no ZIA Private Service Edge associated to the organization. |

### SubCloudCountryDCExclusionInfo
Information about all the data centers excluded for a country
| Field | Type | Required | Description |
| ----- | ---- | -------- | ----------- |
| country | string | No | Country where the data center is located |
| dcIds | array[integer (int32)] | No | List of data centers IDs requested for exclusion from the subcloud |
| lastDCExclusion | boolean | No | If set to true, all the data centers of the given country are excluded |

### SubCloudDCExclusion
Information about data center excluded from the subcloud
| Field | Type | Required | Description |
| ----- | ---- | -------- | ----------- |
| country | string | No | Country where the data center is located |
| createTime | integer (int32) | No | Timestamp when the data center exclusion was created |
| datacenter | EntityReference | No | The data center associated with the subcloud |
| disabledByOps | boolean | No | If set to true, this data center exclusion is disabled by Zscaler CloudOps |
| endTime | integer (int32) | No | Timestamp when the data center exclusion was stopped |
| expired | boolean | No | The subcloud data center exclusion is disabled |
| lastModifiedTime | integer (int32) | No | Timestamp when the data center exclusion entry was last modified |
| lastModifiedUser | EntityReference | No | Last user that modified the data center |
| startTime | integer (int32) | No | Timestamp when the data center exclusion was started |

### TenantDCExclusion
Information about the Zscaler DC exclusion configuration
| Field | Type | Required | Description |
| ----- | ---- | -------- | ----------- |
| dcName | EntityReference | No | The name of the data center. The list of Zscaler DCs that can be excluded can be obtained using the `GET /datacenters` request. |
| dcid | integer (int32) | No | The unique identifier for the DC exclusion configuration |
| description | string | No | Additional information about the DC exclusion |
| endTime | integer (int32) | No | The timestamp (in epoch) when the DC exclusion is set to expire and tunnels are re-enabled for the data center. The expiration can be set to happen within 15 days from the start time and it must be at least 2 hours from the start time (e.g., if the startTime Time is 11:30 AM UTC, set the endTime to 1:30 PM UTC after converting it to Unix time.) |
| expired | boolean | No | A Boolean value indicating whether the DC exclusion has expired |
| startTime | integer (int32) | No | The timestamp (in epoch) when the DC exclusion is set to begin and tunnels are disabled for the data center. The exclusion can be set to begin within a month from the current date and it must be at least 5 minutes from the current time (e.g., if the current time is 11:30 AM UTC, set the startTime to 11:35 AM UTC after converting it to Unix time.) |

### TenantSubCloudExclusions
The organization's subcloud containing the list of excluded data centers
| Field | Type | Required | Description |
| ----- | ---- | -------- | ----------- |
| exclusions | array[SubCloudDCExclusion] | No | List of data centers that are excluded from subcloud |
| id | integer (int32) | No | Subcloud ID |
| name | string | No | Subcloud name |

### TenantSubCloudSummary
Summary of the subcloud associated with an organization. This also represents the data centers that are excluded and associated with the subcloud.
| Field | Type | Required | Description |
| ----- | ---- | -------- | ----------- |
| dcs | array[DatacenterCountry] | No | List of data centers |
| exclusions | array[SubCloudDCExclusion] | No | List of data centers that are excluded from the subcloud |
| id | integer (int32) | No | Unique identifier for the subcloud |
| name | string | No | Subcloud name |

### VPNCredential
VPN is one way to route traffic from customer locations to the cloud. Site-to-site IPSec VPN credentials can be identified by the cloud through one of the following methods:
1. Common Name (CN) of IPSec Certificate
2. VPN User FQDN - requires VPN_SITE_TO_SITE subscription
3. VPN IP Address - requires VPN_SITE_TO_SITE subscription
4. Extended Authentication (XAUTH) or hosted mobile UserID - requires VPN_MOBILE subscription
Notes:
IPs must be created in Static IP first
CN type (certificate) is created automatically, when a CN is provisioned by Zscaler.
The 'psk' field is not applicable for this VPN type.
The most common type is UFQDN.
| Field | Type | Required | Description |
| ----- | ---- | -------- | ----------- |
| comments | string | No | Additional information about this VPN credential. |
| fqdn | string | No | Fully Qualified Domain Name. Applicable only to UFQDN or XAUTH (or HOSTED_MOBILE_USERS) auth type. |
| id | integer (int32) | No | VPN credential id |
| ipAddress | string | No | Static IP address for VPN that is [self-provisioned](/zia/self-provisioning-static-ip-addresses) or provisioned by  Zscaler. This is a required field for IP auth type and is not applicable to other auth types.
**Note:** If you want Zscaler to provision static IP addresses for your organization, contact Zscaler Support. |
| location | object | No | Location that is associated to this VPN credential. Non-existence means not associated to any location. |
| managedBy | object | No | SD-WAN Partner that manages the location. If a partner does not manage the location, this is set to Self. |
| preSharedKey | string | No | Pre-shared key. This is a required field for UFQDN and IP auth type. |
| type | string | Yes | VPN authentication type (i.e., how the VPN credential is sent to the server). It is not modifiable after VpnCredential is created.
**Note:** Zscaler no longer supports adding a new XAUTH VPN  credential, but existing entries can be edited or deleted using the  respective endpoints. |
