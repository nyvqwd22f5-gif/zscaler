# Understanding Geolocalization IP
Source: https://help.zscaler.com/zia/understanding-geolocalization-ip
PDF: https://help.zscaler.com/pdf/com/en/1499521.pdf

Organizations that are located across the globe often access destinations (local government websites or other restricted entities) that allow access only if the source IP address of the traffic is local to the country from where the traffic originates. When the users access these destinations through Zscaler, the client's source IP address reaching the destination is replaced with a Zscaler IP address. This leads to traffic being blocked if the Zscaler IP address is not native to the country.
When Zscaler does not host a data center in a country and a user from that country accesses a local destination with source IP address-based access restrictions, the traffic is routed to the geographically closest Zscaler data center outside the country. As the egress source IP address is not local to the country from where the traffic originates, the user is either denied access to the destination or the results displayed are not localized to the user's location.
To avoid bypassing security checks when traffic is routed to Zscaler data centers outside the country, Zscaler offers a cloud-based service that allows organizations to forward their traffic via the egress source IP address (GeoIP address) mapped to the country from where the traffic originates for countries that Zscaler does not host a data center in. This ensures that the user is able to access specific destinations which have source IP address-based restrictions, and localized content is displayed if the destination renders content based on the country of the originating request.
The following steps are the primary process of using a GeoIP address to forward traffic:
- If not already available on your ZIA tenant, [contact Zscaler Support](/contact-support) to enable Geolocalization IP (GeoIP) for your ZIA tenant.
- After the feature is enabled, Zscaler enables geo IP as a traffic forwarding method in the ZIA Admin Portal.
- Configure geo IP forwarding policies and specify all the criteria to be met before forwarding the traffic. The criteria include location, users, network service, applications, source IPs, destination, etc. If you choose no criteria, all the traffic egresses with geo IP addresses based on the source country.
- The forwarding gateway configuration is not required. Zscaler automatically forwards the traffic with a source IP address mapped to the country from where the traffic originates.
The geo IP feature leverages forwarding policies to steer traffic processed by ZIA to the destination servers, ensuring that the traffic is secure and that the egress source IP address is mapped to the source country. The Zscaler service determines the country that the user is in based on the user's source IP. You can configure granular policies in the ZIA Admin Portal to forward traffic using the geo IP addresses to destinations that require an IP address native to the country of traffic's origin for access. To learn more about forwarding traffic via geo IP, see [Configuring Forwarding Policy](/zia/configuring-forwarding-policy).
For example, a GeoIP forwarding rule is applied to the traffic of a user located in Czechia, so the traffic is forwarded towards the destination with a Czechian source IP address. If the user moves to Serbia, then the traffic will be forwarded to the destination with a Serbian local source IP address. The Zscaler service recognizes that the user is in Czechia or Serbia based on their source IP address. If the user is in a country which hosts a Zscaler data center, the traffic is serviced by the local data center and egresses with a country-local source IP address, and the GeoIP rule does not apply.
When the GeoIP forwarding rule is triggered, Zscaler egresses the traffic with a local source IP address. In some cases, destination websites might not honor the source IP to country mapping to determine the location of the user and provide access. In such scenarios, you could deploy [App Connectors](/zpa/about-connectors) in the region for [Source IP Anchoring](/zia/understanding-source-ip-anchoring) with local IP addresses or deploy the ZIA Virtual Service Edges or Private Service Edges in the region for local IP addresses.
Supported Countries
The following table lists the currently supported countries for the geo IP feature:
This table includes pagination. Use the Search function in the table to find your desired country.
| Country Name | Region |
| ------------ | ------ |
| Albania | Europe |
| Algeria | Africa |
| American Samoa | Americas |
| Armenia | Middle East |
| Aruba | Africa |
| Azerbaijan | Europe |
| Bahamas | Americas |
| Bahrain | Middle East |
| Bangladesh | APJ |
| Belarus | Europe |
| Benin | Africa |
| Bolivia | Americas |
| Bosnia and Herzegovina | Europe |
| Bulgaria | Europe |
| Burkina Faso | Africa |
| Cambodia | APJ |
| Cameroon | Africa |
| Costa Rica | Americas |
| Croatia | Europe |
| Cyprus | Europe |
| Czechia | Europe |
| Djibouti | Africa |
| Dominican Republic | Americas |
| Ecuador | Americas |
| Egypt | Africa |
| El Salvador | Americas |
| Equatorial Guinea | Africa |
| Estonia | Europe |
| Ethiopia | Africa |
| Fiji | APJ |
| French Guiana | Americas |
| French Polynesia | Oceania |
| Gabon | Africa |
| Georgia | Europe |
| Ghana | Africa |
| Greece | Europe |
| Guadeloupe | Americas |
| Guam | APJ |
| Guatemala | Americas |
| Guinea | Africa |
| Honduras | Americas |
| Hungary | Europe |
| Ireland | Europe |
| Jamaica | Americas |
| Jersey | Europe |
| Jordan | Middle East |
| Kazakhstan | APJ |
| Kenya | Africa |
| Kuwait | Middle East |
| Kyrgyzstan | Middle East |
| Laayoune | Africa |
| Latvia | Europe |
| Lebanon | Middle East |
| Liberia | Africa |
| Libya | Africa |
| Lithuania | Europe |
| Luxembourg | Europe |
| Madagascar | Africa |
| Malawi | Africa |
| Maldives | Africa |
| Mali | Africa |
| Malta | Europe |
| Mauritania | Africa |
| Mauritius | APJ |
| Moldova | Europe |
| Monaco | Europe |
| Mongolia | APJ |
| Montenegro | Africa |
| Morocco | Africa |
| Mozambique | Africa |
| Myanmar | APJ |
| Namibia | Africa |
| Nepal | APJ |
| New Caledonia | APJ |
| Nicaragua | Americas |
| Niger | Africa |
| Oman | Middle East |
| Pakistan | APJ |
| Panama | Americas |
| Papua New Guinea | Africa |
| Paraguay | Americas |
| Peru | Americas |
| Philippines | APJ |
| Puerto Rico | Americas |
| Qatar | Middle East |
| Romania | Europe |
| Russia | Europe |
| Rwanda | Africa |
| Saint Martin | Americas |
| Samoa | APJ |
| Senegal | Africa |
| Serbia | Europe |
| Sierra Leone | Africa |
| Slovakia | Europe |
| Slovenia | Europe |
| Somalia | Africa |
| South Sudan | Africa |
| Sri Lanka | APJ |
| Sudan | Africa |
| Suriname | Africa |
| Tajikistan | APJ |
| Tanzania | Africa |
| Thailand | APJ |
| Togo | Africa |
| Trinidad and Tobago | Americas |
| Tunisia | Africa |
| Turkey | Europe |
| Turkmenistan | APJ |
| Uganda | Africa |
| Ukraine | Europe |
| Uruguay | Americas |
| Uzbekistan | Europe |
| Venezuela | Americas |
| Vietnam | APJ |
| Yemen | Africa |
| Zambia | Africa |
| Zimbabwe | Africa |
Benefits of Geo IP Address
The following are a few benefits of using a geo IP address:
- Eliminates the need for organizations to maintain PAC files to bypass the Zscaler service to access certain destinations.
- Eliminates the need to deploy on-premises infrastructure (for Service Edges) to provide a local source IP address.
- Applies uniform Zscaler security policies throughout the organization's traffic irrespective of the user's location.
- Provides you with the ability to granularly control the egress source IP address based on specified forwarding policy criteria.