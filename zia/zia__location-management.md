# Location Management
Source: https://help.zscaler.com/zia/location-management

API Reference Guide for the ZIA Cloud Service and Sandbox Submission APIs

**Base URL:** https://zsapi.[zscaler-cloud-name]/api/v1

## `GET /locations`

Gets locations only, not sub-locations. When a location matches the given search parameter criteria only its parent location is included in the result set, not its sub-locations. To learn more, see [About Locations](/zia/about-locations).

**Tags:** Location Management
**Consumes:** application/json
**Produces:** application/json

| Name | In | Type | Required | Description |
| ---- | --- | ---- | -------- | ----------- |
| search | query | string | No | The search string used to partially match against a location's name and port attributes. |
| sslScanEnabled | query | boolean | No | This parameter was deprecated and no longer has an effect on SSL policy. It remains supported in the API payload in order to maintain backwards compatibility with existing scripts, but it will be removed in future.
Filter based on whether the Enable SSL Scanning setting is enabled or disabled for a location. |
| xffEnabled | query | boolean | No | Filter based on whether the Enforce XFF Forwarding setting is enabled or disabled for a location. |
| authRequired | query | boolean | No | Filter based on whether the Enforce Authentication setting is enabled or disabled for a location. |
| bwEnforced | query | boolean | No | Filter based on whether Bandwith Control is being enforced for a location. |
| enableIOT | query | boolean | No | If set to true, the city field (containing IoT-enabled location IDs, names, latitudes, and longitudes) and the iotDiscoveryEnabled filter are included in the response. Otherwise, they are not included. |
| page | query | integer | No | Specifies the page offset. |
| pageSize | query | integer | No | Specifies the page size. The default size is 100, but the maximum size is 1000. |

| Code | Description | Schema |
| ---- | ----------- | ------ |
| 200 | Successful Operation | array[Location] |

## `POST /locations`

Adds new locations and sub-locations. When invoked with a partner API key, it automatically sets the `managedBy` attribute to the partner associated with the key.

**Tags:** Location Management
**Consumes:** application/json
**Produces:** application/json

| Name | In | Type | Required | Description |
| ---- | --- | ---- | -------- | ----------- |
| location | body | Location | No | Location information |

| Code | Description | Schema |
| ---- | ----------- | ------ |
| 200 | Successful Operation | Location |

## `POST /locations/bulkDelete`

Bulk delete locations up to a maximum of 100 users per request. The response returns the location IDs that were successfully deleted.

**Tags:** Location Management
**Consumes:** application/json
**Produces:** application/json

| Name | In | Type | Required | Description |
| ---- | --- | ---- | -------- | ----------- |
| LocationIds | body | IdListInteger | No | The location IDs to bulk delete. |

| Code | Description | Schema |
| ---- | ----------- | ------ |
| 204 | Successful Operation |  |
| 404 | If the payload includes location IDs that are invalid a ['Resource does not exist' error](/zia/about-error-handling) is returned, but information about the invalid IDs is not included. |  |

## `GET /locations/groups`

Gets information on location groups. To learn more, see [About Location Groups](/zia/about-location-groups).

**Tags:** Location Management
**Consumes:** application/json
**Produces:** application/json

| Name | In | Type | Required | Description |
| ---- | --- | ---- | -------- | ----------- |
| version | query | integer | No | The version parameter is for Zscaler internal use only. The version is used by the service for backup operations. |
| name | query | string | No | The location group's name |
| groupType | query | string | No | The location group's type (i.e., Static or Dynamic) |
| comments | query | string | No | Additional comments or information about the location group |
| locationId | query | integer | No | The unique identifier for a location within a location group |
| lastModUser | query | string | No | The admin that last modified the group |
| fetchLocations | query | boolean | No | Fetches locations associated with the group. Set the value to 'false' to avoid fetching associated locations, thereby optimizing the GET location groups endpoint. |
| page | query | integer | No | Specifies the page offset |
| pageSize | query | integer | No | Specifies the page size. The default size is 100, but the maximum size is 1000. |

| Code | Description | Schema |
| ---- | ----------- | ------ |
| 200 | Successful Operation | array[LocationGroup] |

## `GET /locations/groups/count`

Gets the list of location groups for your organization.

**Tags:** Location Management
**Consumes:** application/json
**Produces:** application/json

| Name | In | Type | Required | Description |
| ---- | --- | ---- | -------- | ----------- |
| lastModUser | query | string | No | The admin who modified the location group last. |
| version | query | integer | No | The version parameter is for Zscaler internal use only. The version is used by the service for backup operations. |
| name | query | string | No | The location group's name. |
| groupType | query | string | No | The location group's type (i.e., Static or Dynamic). |
| comments | query | string | No | Additional comments or information about the location group. |
| locationId | query | integer | No | The unique identifier for a location within a location group. |

| Code | Description | Schema |
| ---- | ----------- | ------ |
| 200 | Successful Operation | integer (int32) |

## `GET /locations/groups/lite`

Gets the name and ID dictionary of location groups.

**Tags:** Location Management
**Consumes:** application/json
**Produces:** application/json

| Name | In | Type | Required | Description |
| ---- | --- | ---- | -------- | ----------- |
| page | query | integer | No | Specifies the page offset. |
| pageSize | query | integer | No | Specifies the page size. The default size is 100, but the maximum size is 1000. |

| Code | Description | Schema |
| ---- | ----------- | ------ |
| 200 | Successful Operation | LocationGroup |

## `GET /locations/groups/lite/{id}`

Gets the name and ID dictionary for the specified location group ID. The response only provides `id`, `name`, and `deleted` information.

**Tags:** Location Management
**Consumes:** application/json
**Produces:** application/json

| Name | In | Type | Required | Description |
| ---- | --- | ---- | -------- | ----------- |
| id | path | integer | Yes | The unique identifier for the location group. |

| Code | Description | Schema |
| ---- | ----------- | ------ |
| 200 | Successful Operation | LocationGroup |

## `GET /locations/groups/{id}`

Gets the location group for the specified ID.

**Tags:** Location Management
**Consumes:** application/json
**Produces:** application/json

| Name | In | Type | Required | Description |
| ---- | --- | ---- | -------- | ----------- |
| id | path | integer | Yes | The unique identifier for the location group. |

| Code | Description | Schema |
| ---- | ----------- | ------ |
| 200 | Successful Operation | LocationGroup |

## `GET /locations/lite`

Gets a name and ID dictionary of locations.

**Tags:** Location Management
**Consumes:** application/json
**Produces:** application/json

| Name | In | Type | Required | Description |
| ---- | --- | ---- | -------- | ----------- |
| includeSubLocations | query | boolean | No | If set to true sub-locations are included in the response otherwise they are excluded |
| includeParentLocations | query | boolean | No | If set to true locations with sub locations are included in the response, otherwise only locations without sub-locations are included |
| sslScanEnabled | query | boolean | No | This parameter was deprecated and no longer has an effect on SSL policy. It remains supported in the API payload in order to maintain backwards compatibility with existing scripts, but it will be removed in future.
Filter based on whether the Enable SSL Scanning setting is enabled or disabled for a location. |
| search | query | string | No | The search string used to partially match against a location's name and port attributes. |
| enableIOT | query | boolean | No | If set to true, the city field (containing IoT-enabled location IDs, names, latitudes, and longitudes) and the iotDiscoveryEnabled filter are included in the response. Otherwise, they are not included. |
| page | query | integer | No | Specifies the page offset. |
| pageSize | query | integer | No | Specifies the page size. The default size is 100, but the maximum size is 1000. |

| Code | Description | Schema |
| ---- | ----------- | ------ |
| 200 | Successful Operation | LocationLite |

## `GET /locations/supportedCountries`

Retrieves the list of countries supported in location configuration
**Note**: The response shows the current list of supported values in an Enum list. However, this list might vary if new entries are added or existing values are modified and the request always returns the latest information available about the countries.

**Tags:** Location Management
**Consumes:** application/json
**Produces:** application/json
No parameters.

| Code | Description | Schema |
| ---- | ----------- | ------ |
| 200 | Successful Operation | array[string] |

## `DELETE /locations/{locationId}`

Deletes the location or sub-location for the specified ID.

**Tags:** Location Management
**Consumes:** application/json
**Produces:** application/json

| Name | In | Type | Required | Description |
| ---- | --- | ---- | -------- | ----------- |
| locationId | path | integer | Yes | The unique identifier for the location. |

| Code | Description | Schema |
| ---- | ----------- | ------ |
| 204 | Successful Operation |  |

## `GET /locations/{locationId}`

Gets the location information for the specified ID.

**Tags:** Location Management
**Consumes:** application/json
**Produces:** application/json

| Name | In | Type | Required | Description |
| ---- | --- | ---- | -------- | ----------- |
| locationId | path | integer | Yes | The unique identifier for the location. |

| Code | Description | Schema |
| ---- | ----------- | ------ |
| 200 | Successful Operation | Location |

## `PUT /locations/{locationId}`

Updates the location and sub-location information for the specified ID.

**Tags:** Location Management
**Consumes:** application/json
**Produces:** application/json

| Name | In | Type | Required | Description |
| ---- | --- | ---- | -------- | ----------- |
| locationId | path | integer | Yes | The unique identifier for the location. |
| location | body | Location | No | Location information. |

| Code | Description | Schema |
| ---- | ----------- | ------ |
| 200 | Successful Operation | Location |

## `GET /locations/{locationId}/sublocations`

Gets the sub-location information for the location with the specified ID. These are the sub-locations associated to the parent location.

**Tags:** Location Management
**Consumes:** application/json
**Produces:** application/json

| Name | In | Type | Required | Description |
| ---- | --- | ---- | -------- | ----------- |
| locationId | path | integer | Yes | The unique identifier for the location. The sub-location information given is based on the parent location's ID. |
| search | query | string | No | The search string used to partially match against a sub-location's name and port attributes. |
| sslScanEnabled | query | boolean | No | This parameter was deprecated and no longer has an effect on SSL policy. It remains supported in the API payload in order to maintain backwards compatibility with existing scripts, but it will be removed in future.
Filter based on whether the Enable SSL Scanning setting is enabled or disabled for a sub-location. |
| xffEnabled | query | boolean | No | Filter based on whether the Enforce XFF Forwarding setting is enabled or disabled for a sub-location. |
| authRequired | query | boolean | No | Filter based on whether the Enforce Authentication setting is enabled or disabled for a sub-location. |
| bwEnforced | query | boolean | No | Filter based on whether Bandwith Control is being enforced for a sub-location. |
| enforceAup | query | boolean | No | Filter based on whether Enforce AUP setting is enabled or disabled for a sub-location. |
| enableFirewall | query | boolean | No | Filter based on whether Enable Firewall setting is enabled or disabled for a sub-location. |
| enableIOT | query | boolean | No | If set to true, the city field (containing IoT-enabled location IDs, names, latitudes, and longitudes) and the iotDiscoveryEnabled filter are included in the response. Otherwise, they are not included. |

| Code | Description | Schema |
| ---- | ----------- | ------ |
| 200 | Successful Operation | array[Location] |

## Models
### DynamicLocationGroupCriteria
Dynamic location group information.
| Field | Type | Required | Description |
| ----- | ---- | -------- | ----------- |
| city | StringFilter | No | A sub-string to match city. Valid operators are starts with, ends with, contains, and exact match operators. |
| countries | array[string] | No | One or more countries from a predefined set |
| enableBandwidthControl | boolean | No | Enable Bandwidth Control. When set to true, Bandwidth Control is enabled for the location. |
| enableCaution | boolean | No | Enable Caution. When set to true, a caution notifcation is enabled for the location. |
| enableXffForwarding | boolean | No | Enable XFF Forwarding. When set to true, traffic is passed to Zscaler Cloud via the X-Forwarded-For (XFF) header. |
| enforceAup | boolean | No | Enable AUP. When set to true, AUP is enabled for the location. |
| enforceAuthentication | boolean | No | Enforce Authentication. Required when ports are enabled, IP Surrogate is enabled, or Kerberos Authentication is enabled. |
| enforceFirewallControl | boolean | No | Enable Firewall. When set to true, Firewall is enabled for the location. |
| managedBy | array[EntityReference] | No | One or more values from a predefined set of SD-WAN partner list to display  partner names. |
| name | StringFilter | No | A sub-string to match location name. Valid operators are contains, starts with, and ends with", |
| profiles | array[string] | No | One or more location profiles from a predefined set |

### EntityReference
This is an immutable reference to an entity that mainly consists of id and name
| Field | Type | Required | Description |
| ----- | ---- | -------- | ----------- |
| extensions | object | No | Additional information about the entity |
| externalId | string | No | An external identifier used for an entity that is managed outside of ZIA. Examples include `zpaServerGroup` and `zpaAppSegments`. This field is not applicable to ZIA-managed entities. |
| id | integer (int64) | No | A unique identifier for an entity |
| name | string | No | The configured name of the entity |

### IdListInteger
| Field | Type | Required | Description |
| ----- | ---- | -------- | ----------- |
| ids | array[integer (int32)] | No |  |

### Location
Location and sub-location information.
| Field | Type | Required | Description |
| ----- | ---- | -------- | ----------- |
| aupBlockInternetUntilAccepted | boolean | No | For First Time AUP Behavior, Block Internet Access. When set, all internet access (including non-HTTP traffic) is disabled until the user accepts the AUP. |
| aupEnabled | boolean | No | Enable AUP. When set to true, AUP is enabled for the location. To learn more, see [About End User Notifications](/zia/about-end-user-notifications) |
| aupForceSslInspection | boolean | No | For First Time AUP Behavior, Force SSL Inspection. When set, Zscaler forces SSL Inspection in order to enforce AUP for HTTPS traffic. |
| aupTimeoutInDays | integer (int32) | No | Custom AUP Frequency. Refresh time (in days) to re-validate the AUP. |
| authRequired | boolean | No | Enforce Authentication. Required when ports are enabled, IP Surrogate is enabled, or Kerberos Authentication is enabled. |
| cautionEnabled | boolean | No | Enable Caution. When set to true, a caution notifcation is enabled for the location. To learn more, see [Configuring the Caution Notification](/zia/configuring-caution-notification#caution-interval) |
| city | object | No | Geolocation of the IoT device. It displays the name-ID pair for the location ("city" : { "id":"0", "name":"string" }).
For example, "city" : { "id":"2077963", "name":"Albany, Western Australia, Australia"}. |
| cookiesAndProxy | boolean | No | If set to true, the **surrogateIPEnforcedForKnownBrowsers** option is enabled for all authentication methods including cookie-based, Kerberos, Basic, and Digest authentication to leverage the existing IP address-to-user mapping (acquired from surrogate IP) to authenticate users and prevent further authentication challenges for traffic originating from that source IP address. If set to false, surrogate IP for known browsers is only supported for cookie-based authentication and all other methods require authentication after each request. |
| country | string | No | Country |
| defaultExtranetDns | boolean | No | A Boolean value indicating that the DNS server configuration used in the extranet is the designated default DNS server |
| defaultExtranetTsPool | boolean | No | A Boolean value indicating that the traffic selector specified in the extranet is the designated default traffic selector |
| description | string | No | Additional notes or information regarding the location or sub-location. The description cannot exceed 1024 characters. |
| displayTimeUnit | string | No | Display Time Unit. The time unit to display for IP Surrogate idle time to disassociation. |
| dnBandwidth | integer (int32) | No | Download bandwidth in kbps. The value 0 implies no Bandwidth Control enforcement. |
| extranet | EntityReference | No | The ID of the extranet resource that must be assigned to the location |
| extranetDns | EntityReference | No | The ID of the DNS server configuration used in the extranet |
| extranetIpPool | EntityReference | No | The ID of the traffic selector specified in the extranet |
| geoOverride | boolean | No | If this field is set to true, the latitude and longitude values must be provided. By default, it's set to false. |
| id | integer (int32) | No | Location ID. |
| idleTimeInMinutes | integer (int32) | No | Idle Time to Disassociation. The user mapping idle time (in minutes) is required if a Surrogate IP is enabled. |
| iotDiscoveryEnabled | boolean | No | If this field  is  set to true, IoT discovery is enabled for this location. |
| ipAddresses | array[string] | No | For locations: IP addresses of the egress points that are provisioned in the Zscaler Cloud. Each entry is a single IP address (e.g., 238.10.33.9).
For sub-locations: Egress, internal, or GRE tunnel IP addresses. Each entry is either a single IP address, CIDR (e.g., 10.10.33.0/24), or range (e.g., 10.10.33.1-10.10.33.10)). |
| ipsControl | boolean | No | Enable IPS Control. When set to true, IPS Control is enabled for the location if Firewall is enabled. |
| ipv6Dns64Prefix | object | No | (Optional) Name-ID pair of the NAT64 prefix configured as the DNS64 prefix for the location. If specified, the DNS64 prefix is used for the IP addresses that reside in this location. If not specified, a prefix is selected from the set of supported prefixes. This field is applicable only if `ipv6Enabled` is set is `true`. To learn more, see [About the DNS64 Prefix](/zia/about-dns64-prefix).
Before you can configure a DNS64 prefix, you must send a GET request to `/ipv6config/nat64prefix` to retrieve the IDs of NAT64 prefixes, which can be configured as the DNS64 prefix. |
| ipv6Enabled | boolean | No | If set to true, IPv6 is enabled for the location and IPv6 traffic from  the location can be forwarded to the Zscaler service to enforce security policies. |
| latitude | number (double) | No | The value of latitude must be set to 7-digit precision after decimal point, ranging between -90 and 90 degrees.
**Note**: This field is mandatory if geoOverride is set to true. |
| longitude | number (double) | No | The value of longitude must be set to 7-digit precision after decimal point, ranging between -180 and 180 degrees.
**Note**: This field is mandatory if geoOverride is set to true. |
| managedBy | object | No | SD-WAN Partner that manages the location. If a partner does not manage the location, this is set to Self. |
| name | string | Yes | Location Name. |
| ofwEnabled | boolean | No | Enable Firewall. When set to true, Firewall is enabled for the location. |
| other6SubLocation | boolean | No | If set to true, indicates that this is a default sub-location created by the Zscaler service to accommodate IPv6 addresses that are not part of any user-defined sub-locations. The default sub-location is created with the name **Other6** and it can be renamed, if required. This field is applicable only if `ipv6Enabled` is set is `true`. |
| otherSubLocation | boolean | No | If set to true, indicates that this is a default sub-location created  by the Zscaler service to accommodate IPv4 addresses that are not part of any user-defined sub-locations. The default sub-location is created with the name **Other** and it can be renamed, if required. |
| parentId | integer (int32) | No | Parent Location ID. If this ID does not exist or is 0, it is implied that it is a parent location. Otherwise, it is a sub-location whose parent has this ID. x-applicableTo: SUB |
| ports | array[integer (int32)] | No | IP ports that are associated with the location. |
| profile | string | No | (Optional) Profile tag that specifies the location traffic type. If not specified, this tag is automatically set to best possible value using certain criteria.
The criteria used for setting best possible value is as follows:
- When invoked with a partner API key, it automatically sets the profile attribute to **CORPORATE**.
- When invoked using public API, it automatically sets the profile attribute based on the following criteria:
- If the location has authentication enabled, then it sets profile to **CORPORATE**.
- If the location has authentication disabled and name contains "guest", then it sets profile to **GUESTWIFI**.
- For all other locations with authentication disabled, it sets profile to **SERVER**. |
| sslScanEnabled | boolean | No | This parameter was deprecated and no longer has an effect on SSL policy. It remains supported in the API payload in order to maintain backwards compatibility with existing scripts, but it will be removed in future.
Enable SSL Inspection. Set to true in order to apply your SSL Inspection policy to HTTPS traffic in the location and inspect HTTPS transactions for data leakage, malicious content, and viruses. To learn more, see [Deploying SSL Inspection](/zia/deploying-ssl-inspection) |
| subLocAccIds | array[string] | No | Specifies one or more Amazon Web Services (AWS) account IDs. These AWS accounts are associated with the parent location of this sublocation created in the Zscaler Cloud & Branch Connector Admin Portal. |
| subLocScope | string | No | Defines a scope for the sublocation from the available types to segregate workload traffic from a single sublocation to apply different Cloud Connector and ZIA security policies. This field is only available for the **Workload** traffic type sublocations whose parent locations are associated with Amazon Web Services (AWS) Cloud Connector groups. To learn about the different scope types supported, see [Configuring Sublocations](/zia/configuring-sublocations). |
| subLocScopeEnabled | boolean | No | Indicates whether defining scopes is allowed for this sublocation. Sublocation scopes are available only for the **Workload** traffic type sublocations whose parent locations are associated with Amazon Web Services (AWS) Cloud Connector groups. This is a read-only field. To learn more, see [Configuring Sublocations](/zia/configuring-sublocations). |
| subLocScopeValues | array[string] | No | Specifies values for the selected sublocation scope type |
| surrogateIP | boolean | No | Enable Surrogate IP. When set to true, users are mapped to internal device IP addresses. To learn more, see [About Surrogate IP](/zia/about-surrogate-ip). |
| surrogateIPEnforcedForKnownBrowsers | boolean | No | Enforce Surrogate IP for Known Browsers. When set to true, IP Surrogate is enforced for all known browsers. To learn more, see [About Surrogate IP](/zia/about-surrogate-ip) |
| surrogateRefreshTimeInMinutes | integer (int32) | No | Refresh Time for re-validation of Surrogacy. The surrogate refresh time (in minutes) to re-validate the IP surrogates. |
| surrogateRefreshTimeUnit | string | No | Display Refresh Time Unit. The time unit to display for refresh time for re-validation of surrogacy. |
| tz | string | No | Timezone of the location. If not specified, it defaults to GMT. |
| upBandwidth | integer (int32) | No | Upload bandwidth in kbps. The value 0 implies no Bandwidth Control enforcement. |
| vpnCredentials | array[VPNCredential] | No | VPN User Credentials that are associated with the location. |
| xffForwardEnabled | boolean | No | Enable XFF Forwarding for a location. When set to true, traffic is passed to Zscaler Cloud via the X-Forwarded-For (XFF) header.
**Note:** For sub-locations, this attribute is a read-only field as the  value is inherited from the parent location. |
| zappSSLScanEnabled | boolean | No | This parameter was deprecated and no longer has an effect on SSL policy. It remains supported in the API payload in order to maintain backwards compatibility with existing scripts, but it will be removed in future.
Enable Zscaler App SSL Setting. When set to true, the Zscaler App SSL Scan Setting takes effect, irrespective of the SSL policy that is configured for the location. To learn more, see [Configuring SSL Inspection for Zscaler App](/z-app/configuring-ssl-inspection-zscaler-app#configure-SSL-Zscaler-App) |

### LocationGroup
Location group information.
| Field | Type | Required | Description |
| ----- | ---- | -------- | ----------- |
| comments | string | No | Additional information about the location group |
| deleted | boolean | No | Indicates the location group was deleted |
| dynamicLocationGroupCriteria | DynamicLocationGroupCriteria | No | A dynamic location group's criteria. This is ignored if the groupType is Static. |
| groupType | string | No | The location group's type (i.e., Static or Dynamic) |
| id | integer (int32) | No | Unique identifier for the location group |
| lastModTime | integer (int32) | No | Automatically populated with the current time, after a successful POST or PUT request. |
| lastModUser | EntityReference | No | Automatically populated with the current ZIA admin user, after a successful POST or PUT request. |
| locations | array[EntityReference] | No | The Name-ID pairs of the locations that are assigned to the static location group. This is ignored if the groupType is Dynamic. |
| name | string | Yes | Location group name |
| predefined | boolean | No |  |

### LocationLite
Location and sub-location information based on a limited number of fields.
| Field | Type | Required | Description |
| ----- | ---- | -------- | ----------- |
| aupBlockInternetUntilAccepted | boolean | No | For First Time AUP Behavior, Block Internet Access. When set, all internet access (including non-HTTP traffic) is disabled until the user accepts the AUP. |
| aupEnabled | boolean | No | Enable AUP. When set to true, AUP is enabled for the location. To learn more, see [About End User Notifications](/zia/about-end-user-notifications) |
| aupForceSslInspection | boolean | No | For First Time AUP Behavior, Force SSL Inspection. When set, Zscaler forces SSL Inspection in order to enforce AUP for HTTPS traffic. |
| cautionEnabled | boolean | No | Enable Caution. When set to true, a caution notifcation is enabled for the location. To learn more, see [Configuring the Caution Notification](/zia/configuring-caution-notification#caution-interval) |
| id | integer (int32) | No | Location ID |
| ipsControl | boolean | No | Enable IPS Control. When set to true, IPS Control is enabled for the location if Firewall is enabled. |
| ipv6Enabled | boolean | No | If set to true, IPv6 is enabled for the location and IPv6 traffic from the location can be forwarded to the Zscaler service to enforce security policies. |
| name | string | Yes | Location Name |
| ofwEnabled | boolean | No | Enable Firewall. When set to true, Firewall is enabled for the location. |
| other6SubLocation | boolean | No | If set to true, indicates that this is a default sub-location created by the Zscaler service to accommodate IPv6 addresses that are not part of any user-defined sub-locations. The default sub-location is created with the name **Other6** and it can be renamed, if required.  This field is applicable only if `ipv6Enabled` is set is  `true`. |
| otherSubLocation | boolean | No | If set to true, indicates that this is a default sub-location created  by the Zscaler service to accommodate IPv4 addresses that are not part of any user-defined sub-locations. The default sub-location is created with the name **Other** and it can be renamed, if required. |
| parentId | integer (int32) | No | Parent Location ID. If this ID does not exist or is 0, it is implied that it is a parent location. Otherwise, it is a sub-location whose parent has this ID. x-applicableTo: SUB |
| subLocAccIds | array[string] | No | Specifies one or more Amazon Web Services (AWS) account IDs. These AWS accounts are associated with the parent location of this sublocation created in the Zscaler Cloud & Branch Connector Admin Portal. |
| subLocScope | string | No | Defines a scope for the sublocation from the available types to segregate workload traffic from a single sublocation to apply different Cloud Connector and ZIA security policies. This field is only available for the **Workload** traffic type sublocations whose parent locations are associated with Amazon Web Services (AWS) Cloud Connector groups. To learn about the different scope types supported, see [Configuring Sublocations](/zia/configuring-sublocations). |
| subLocScopeEnabled | boolean | No | Indicates whether defining scopes is allowed for this sublocation. Sublocation scopes are available only for the **Workload** traffic type sublocations whose parent locations are associated with Amazon Web Services (AWS) Cloud Connector groups. This is a read-only field. To learn more, see [Configuring Sublocations](/zia/configuring-sublocations). |
| subLocScopeValues | array[string] | No | Specifies values for the selected sublocation scope type |
| surrogateIP | boolean | No | Enable Surrogate IP. When set to true, users are mapped to internal device IP addresses. To learn more, see [About Surrogate IP](/zia/about-surrogate-ip). |
| surrogateIPEnforcedForKnownBrowsers | boolean | No | Enforce Surrogate IP for Known Browsers. When set to true, IP Surrogate is enforced for all known browsers. To learn more, see [About Surrogate IP](/zia/about-surrogate-ip) |
| tz | string | No | Timezone of the location. If not specified, it defaults to GMT. |
| xffForwardEnabled | boolean | No | Enable XFF Forwarding for a location. When set to true, traffic is passed to Zscaler Cloud via the X-Forwarded-For (XFF) header.
**Note:** For sub-locations, this attribute is a read-only field as the  value is inherited from the parent location. |
| zappSslScanEnabled | boolean | No | This parameter was deprecated and no longer has an effect on SSL policy. It remains supported in the API payload in order to maintain backwards compatibility with existing scripts, but it will be removed in future.
Enable Zscaler App SSL Setting. When set to true, the Zscaler App SSL Scan Setting takes effect, irrespective of the SSL policy that is configured for the location. To learn more, see [Configuring SSL Inspection for Zscaler App](/z-app/configuring-ssl-inspection-zscaler-app#configure-SSL-Zscaler-App) |

### StringFilter
| Field | Type | Required | Description |
| ----- | ---- | -------- | ----------- |
| matchString | string | No | String value to be matched or partially matched |
| matchType | string | No | Operator that performs match action |

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
