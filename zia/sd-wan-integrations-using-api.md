# SD-WAN Integrations Using API
Source: https://help.zscaler.com/zia/sd-wan-integrations-using-api
PDF: https://help.zscaler.com/pdf/com/en/1400806.pdf

This article only includes information on how to:
- Enable Software-Defined Wide Area Networking (SD-WAN) partner API key access.
- Determine the best virtual IP addresses (VIPs) for an SD-WAN partner to use for your IPSec VPN tunnels.
- Use [Locations](/zia/location-management#/locations-get) and [VPN Credentials](/zia/traffic-forwarding-0#/vpnCredentials-get) API resources to set up IPSec VPN tunnels.
For details and SD-WAN deployment configuration guides for each partner (i.e., Riverbed SteelConnect, HPE Aruba, etc.), see the [SD-WAN partner site](https://www.zscaler.com/partners/technology/sd-wan?_ga=2.151531454.664659488.1542647815-1285048483.1515448871) or contact Zscaler Business Development.
If you have [enabled restricted access](/zia/configuring-restricted-access-admins) to the ZIA Admin Portal based on the source IP address, you need to include the SD-WAN device IP addresses in the allowlist for accessing the ZIA Admin Portal via API. To learn more, see [Configuring Restricted Access for Admins](/zia/configuring-restricted-access-admins).
Enabling SD-WAN API Access for Partners
An SD-WAN partner API key enables technology partner access to the [Locations](/zia/location-management#/locations-get) resources and a [VPN Credentials](/zia/traffic-forwarding-0#/vpnCredentials-get) resource within the cloud service API.
To enable SD-WAN partner API access:
- Log in to the ZIA Admin Portal.
- Configure a [SD-WAN partner API role](/zia/adding-sd-wan-partner-api-roles) with SD-WAN partner access enabled.
- Configure a [SD-WAN partner API client](/zia/adding-sd-wan-partner-api-clients) for the SD-WAN partner, and make sure the proper SD-WAN partner API role is applied.
-
[]When you have an SD-WAN partner API client and role properly configured, [add a partner key](/zia/configuring-sdwan-integration#AddNewKey).
You cannot use a cloud service API key configured under Administration > [Cloud Service API Key Management](/zia/about-cloud-service-api-key-management) to enable SD-WAN partner access. You must create an SD-WAN partner key under Administration > [Partner Integrations](/zia/about-partner-integration-management). Also, your organization can only have one key per SD-WAN partner.
- Send the D-WAN partner API client credentials and partner key to your SD-WAN partner.
If you [edit](/zia/configuring-sdwan-integration#EditNewKey), [regenerate](/zia/configuring-sdwan-integration#RegenerateKey), or [delete](/zia/configuring-sdwan-integration#DeleteKey) a partner key, make sure that you inform your SD-WAN partner of the change.
[]Determining Your Zscaler Data Center VIPs for SD-WAN Integrations
You need to select the best primary and secondary data center VIPs to which the SD-WAN partner establishes an IPSec VPN tunnel. To determine the best VIPs for your cloud, use one of the following methods:
-
Method 1 (Recommended): Use the `GET /vips` API endpoint to get a flat list of all VIPs for your cloud. Zscaler recommends including all VIPs in the request if you want to add your own intelligence to determine the best VIPs for your IPSec VPN tunnels, or if you want to provide a complete list to a user in order to enable them to override a selection. For example, in Python, the GET request to include all VIPs would appear as follows:
`conn.request("GET", "/api/v1/vips?include=all", headers=headers)`
To learn more about `GET /vips`, see Traffic Forwarding in the [API Reference](/zia/traffic-forwarding-0#/vips-get).
-
Method 2: Use the `GET https://pac.``<Zscaler cloud>``.net/getVpnEndpoints` API endpoint, where, `<Zscaler cloud>` is the cloud name provisioned for your organization by Zscaler (e.g., `zscalerbeta`). This endpoint returns your primary, secondary, and tertiary VIPs based on geolocation proximity to the source IP or location coordinates of the edge device. To learn more, see [What is my cloud name for ZIA?](/zia/what-my-cloud-name)
- Use `getVpnEndpoints`, with no attributes, to obtain the VIPs based on the source IP where the HTTP request originated from (e.g., `https://pac.zscalerbeta.net/getVpnEndpoints`).
- Use the `getVpnEndpoints?srcIp=``<source IP address>` query parameter to obtain the VIPs based on a specific source IP (e.g., `https://pac.zscalerbeta.net/getVpnEndpoints?srcIp=194.208.68.97`).
- Use the `getVpnEndpoints?lat=``<latitude coordinate>``&long=``<longitude coordinate>` query parameters to obtain the VIPs based on location coordinates (e.g., `https://pac.zscalerbeta.net/getVpnEndpoints?lat=47.1275&long=10.2637`).
- Use the `getVpnEndpoints?subcloud=``<subcloud>` query parameter to obtain the VIPs based on a specific subcloud. To learn more, see [Understanding Subclouds](/zia/understanding-subclouds) (e.g., `https://pac.zscalerbeta.net/getVpnEndpoints?subcloud=americas`).
- The `subcloud` query parameter can be used along with other parameters for the endpoint (e.g., `https://pac.zscalerbeta.net/getVpnEndpoints?lat=47.1275&long=10.2637&subcloud=americas`).
-
Use the `getVpnEndpoints?domesticPerf=``<true/false>` query parameter to obtain the VIPs based on domestic country. The default is `false`. When set to `true`, the three closest endpoints that are within the country of the requesting user are provided in the response, if available (e.g., `https://pac.zscalerbeta.net/getVpnEndpoints?domesticPref=true`).
The `domesticPref` query parameter can be used along with the source IP (`srcIP`) and location coordinates (`lat`/`long`) parameters for the endpoint (e.g., `https://pac.zscalerbeta.net/getVpnEndpoints?srcIp=194.208.68.97&lat=47.1275&long=10.2637&domesticPref=true`).
A successful API call returns a 200 OK status code. However, if an invalid query parameter is specified, a 400 status code is returned. To learn more, see [API Response Codes and Error Messages](/zia/api-response-codes-and-error-messages).
You should only pass integers to the `getVpnEndpoints` API endpoint.
A successful API call returns the following VIP information within the response. For example:
{
"primaryIp": "165.225.72.39",
"primaryMeta": {
"region": "Europe",
"country": "Germany",
"city": "Frankfurt",
"dcName": "FRA4",
"latitude": 50.000000,
"longitude": 9.000000
},
"secondaryIp": "104.129.194.39",
"secondaryMeta": {
"region": "NorthAmerica",
"country": "United States",
"city": "Washington, DC",
"dcName": "WAS1",
"latitude": 39.000000,
"longitude": -77.000000
},
"tertiaryIp": "199.168.148.132",
"tertiaryMeta": {
"region": "NorthAmerica",
"country": "United States",
"city": "Fremont, CA",
"dcName": "FMT1",
"latitude": 37.000000,
"longitude": -121.000000
}
}
- Method 3 (Not Recommended): See the [Zscaler Data Center VIPs JSON](/zia/zscaler-api/ips-json-api) for your cloud and find the two data centers closest to the organization's location. To learn more, see [Locating the Hostnames and IP Addresses for ZIA Public Service Edges](/zia/locating-the-hostnames-and-ip-addresses-your-zens).
After you have determined your VIPs, be sure to provide this information to your SD-WAN partner.
Using Locations and VPN Credentials API Resources for SD-WAN Integrations
Within the ZIA Admin Portal, review your configured [locations](/zia/about-locations) or [VPN credentials](/zia/about-vpn-credentials) and assign the proper SD-WAN partner to manage them by setting the Managed By field. In order for partners to retrieve location details using `GET /locations`, the Managed By field (i.e., `managedBy` attribute) must be set to one of the partners defined in our service (e.g., Riverbed SteelConnect, HPE Aruba, etc.). To learn more, see the [Understanding the managedBy Attribute](/zia/sd-wan-api-integration#UnderstandManagedBy) section.
The Locations resources, and the `POST /vpnCredentials `resources, are designed to support SD-WAN partner integration workflows. Therefore, some limitations apply if you are attempting to use them for workflows that are not partner-specific. Also, all the location features and functionality within the ZIA Admin Portal are not available via the API (i.e., sublocations, public IP addresses, proxy ports, and location groups).
[]Understanding the managedBy Attribute
The `managedBy` attribute is a unique identifier for an entity. In this case, the entity managing the location or VPN credential. In the ZIA Admin Portal, this is represented by the Managed By field within the [Locations](/zia/configuring-locations) and [VPN Credentials](/zia/adding-individual-vpn-credentials#fqdn) pages, which can be set to you (i.e., Self) or your partner (e.g., Riverbed SteelConnect).
[See image.](#ManagedBy)
For Locations and VPN Credentials resources, the API includes a `managedBy` attribute in the object models. Locations and VPN Credentials resources only return objects that are managed by the proper entity. So, the `managedBy` attribute must be set to one of the following partners as named in our service:
- Cisco Viptela
- Citrix SD-WAN
- CloudGenix
- HPE Aruba
- ngena
- Riverbed SteelConnect
- Silver Peak
- VMware VeloCloud
For example, if your partner is Riverbed SteelConnect and they make a call to perform a GET action, then they can only get Riverbed SteelConnect-tagged location and VPN credential objects in the response. They cannot get objects that are managed by you (i.e., Self). Also, if the partner makes a call to perform a POST, PUT, or DELETE action, then the `managedBy` attribute is automatically assigned to them.
When an API call is made using an SD-WAN [partner key](/zia/sd-wan-api-integration#partner_key), the call fails if the payload does not include the matching partner name in the `managedBy` attribute.
Getting a List of Locations
The Locations resources allow an SD-WAN partner to export all attributes of a Zscaler service-defined location as a request. So, for partners, calling `GET /locations` would retrieve a list of location objects managed by them. For example, in Python, a GET request by a Riverbed SteelConnect partner would appear as follows:
conn.request("GET", "/api/v1/locations", headers=headers)
So the response would be:
[
{
"name": "nyc-2",
"id": 4562809,
"managedBy": {
"id": 1,
"name": "Riverbed SteelConnect"
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
"name": "Riverbed SteelConnect"
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
If used, Zscaler recommends changing the `pageSize` query parameter to more than 100, or iterating through all results using the `page` query parameter, until the last page has less than 100 results.
If you send a GET request to `/locations`, the pre-shared key (PSK) for the associated VPN credential is not included in the response for security reasons.
To learn more, see the [Understanding the managedBy Attribute](/zia/sd-wan-api-integration#UnderstandManagedBy) section.
Adding, Updating, and Deleting Locations
SD-WAN partners cannot get objects that are managed by you (i.e., Self). If a partner makes a call to perform a POST, PUT, or DELETE action for a location, then they can only do so for locations that they manage. To learn more, see the [Understanding the managedBy Attribute](/zia/sd-wan-api-integration#UnderstandManagedBy) section.
You cannot update a location's fully qualified domain name (`fqdn`) by sending a PUT request to `/locations/{locationId}`. If the `fqdn` is modified in the request, the change is ignored.
Adding VPN Credentials
Using the `POST /vpnCredentials` resource allows an SD-WAN partner to configure IPSec VPN authentication. To learn more, see [Adding VPN Credentials](/zia/adding-individual-vpn-credentials#fqdn).
[]![The Managed By field in Add Location and Add VPN Credential windows](/downloads/zia/zia-api/api-developer-reference-guide/working-apis/sd-wan-integrations-using-api/Add-Location-VPN-Credential%20-%20ManagedBy.png)