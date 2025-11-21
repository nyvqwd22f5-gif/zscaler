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