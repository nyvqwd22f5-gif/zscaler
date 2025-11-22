# Configuring Disaster Recovery
Source: https://help.zscaler.com/zia/configuring-disaster-recovery
PDF: https://help.zscaler.com/pdf/com/en/1420071.pdf

Enabling disaster recovery ensures business continuity in the event of a disaster scenario that impacts the global Zscaler cloud infrastructure. Disaster recovery is for organizations that depend on the Zscaler cloud to remain operational during disaster events by providing users with access to critical applications. Zscaler provides support for disaster recovery in both Zscaler Private Access (ZPA) and ZIA.
The ZIA Disaster Recovery mode is only available to enrolled users.
To enable disaster recovery for ZIA, you must configure the following settings in your [Zscaler Client Connector Profiles](/zscaler-client-connector/configuring-zscaler-client-connector-app-profiles):
- In the **ZIA Admin Portal**, go to **Policy** > **Zscaler Client Connector Portal**.
- Click the **App Profiles **menu.
-
On the **Windows** page, click **Add Windows Policy**. The **Add Windows Policy** window appears.
-
In the **General **section, under the **ZIA Disaster Recovery**, you can configure the following to provide users access even when the ZIA service is down.
- Select **Enable ZIA DR**.
- Select from the following traffic forwarding actions in the drop-down menu:
- **Direct Internet Access**: Traffic bypasses Zscaler Client Connector, giving the user access to all applications through direct internet access.
- **Disable Internet Access**: All traffic is dropped at the endpoint and users do not have access to the internet.
- **Policy Based Access**: You can either block or allow access to specific URLs using a custom PAC file. Insert the custom PAC file URL in the **Use Custom Destinations URL** field.
- **Use Zscaler Recommended Destination List**: When enabled, users can access only the URLs that are present in the [Zscaler-provided global database allowlist](https://dll7xpq8c5ev0.cloudfront.net/drdb.txt). The rest of the URLs are blocked.
-
**Use Custom DR PAC URL**: Select this option to insert a custom PAC file URL in the **Custom Destinations** field. You can configure a custom PAC URL (with the http:// or https:// prefix) that users can access when the ZIA service is down. When configured in conjunction with the global database URL, both URL lists are allowed. The custom destinations URL takes precedence when there are any conflicts. You can also forward the traffic to a proxy server.
You must configure the Custom DR PAC URL pointing to the private PAC server for private business continuity cloud (`https://<private pac domain>.pac.zsbcs.net/<``insert the rest of the PAC URL``>`. For example: `http://platform-pm.pac.zsbcs.net/platform-pm.zscalerbeta.net/DRPAC`. To learn more about private business continuity, see [Understanding Zscaler-Managed Business Continuity Cloud](/zia/understanding-zscaler-managed-business-continuity-cloud).
- When configuring the custom PAC file, ensure that you allow access to the ZPA IP range `100.64.0.0/16` and ZPA domains, `zpath.net` and `zpatwo.net`, to prevent blocking ZPA traffic.
- If you have enabled both the **Allow Zscaler Preselected Destinations** and **Allow Custom Destinations** fields, ensure that you remove the `return drop;` syntax from the custom PAC file statement because it blocks the URLs listed in the Zscaler-provided global database allowlist.
Use the following sample custom PAC file:
function FindProxyForURL(url, host) {
var drop = "BLOCK";
/* Return DIRECT to Allow access */
if ((localHostOrDomainIs(host, "google.com")) ||
(localHostOrDomainIs(host, "salesforce.com")) ||
(localHostOrDomainIs(host, "microsoft.com")) ||
(localHostOrDomainIs(host, "zscaler.com")) )
return "DIRECT";
/* Default Block Statement to block anything not allowed above */
return drop;
}
- Return DIRECT to allow destination access.
- Return BLOCK (or any other return statement other than DIRECT) to block destination access.
- Return PROXY to forward the selected internet traffic to a proxy server with or without a port. Applies to Zscaler Client Connector version 4.5 for Windows and macOS only.
Use the following sample custom PAC file for private business continuity users:
The private business continuity feature is in limited availability. To learn more, contact your Zscaler Account team.
`function FindProxyForURL(url, host) {
var drop = "BLOCK";
/* Return DIRECT to Allow access */
if ((localHostOrDomainIs(host, "google.com")) ||
(localHostOrDomainIs(host, "ebay.com")))
return "DIRECT";
if ((localHostOrDomainIs(host, "yahoo.com")) ||
(localHostOrDomainIs(host, "msn.com")))
return drop;
/* Default Block Statement to block anything not allowed above */
return "PROXY ${GATEWAY.platform-bcp.zscalerbeta.net}:80; PROXY ${SECONDARY.GATEWAY.platform-bcp.zscalerbeta.net}:80";
}`
- Replace `Platform-bcp` with the organization name.
- Replace `zscalerbeta.net` with the name of the cloud on which your organization is provisioned.
- Return DIRECT to allow destination access.
- Return BLOCK (or any other return statement other than DIRECT) to block destination access.
- Return PROXY to forward the selected internet traffic to a proxy server with or without a port. Applies to Zscaler Client Connector version 4.5 and later for Windows.
- Return PROXY to the Zscaler-managed business continuity subcloud to maintain your policies in the business continuity environment.
- **DNS Settings**:
-
**Precreate a DNS TXT record with the Zscaler DNS generator tool**: To create an Active Domain Name and Domain Public Key, see [Creating DNS TXT Records](/zpa/creating-dns-txt-records).
If you have ZIA only, you cannot download the DNS Record Generator.
- **ZIA Domain name**: Enter a valid domain name.
- **TXT Record Signing Public Key**: Click **Upload** to add a valid public key. You can only upload .pem files.
- **Activation: **Activate or test disaster recovery by updating the DNS TXT record value. To learn more, see [Creating DNS TXT Records](/zpa/creating-dns-txt-records).
- **Test Mode: **Enable **Activate Test Mode** if the selected users or groups for the app profile are part of a group to test disaster recovery. Zscaler recommends that disaster recovery be tested periodically with just a few users.
[See image.](#zia-disaster-recovery-image)
- Click **Save**.
[]![Screenshot of the ZIA Disaster Recovery configurations in Windows Policy profile](/downloads/zia/traffic-forwarding/configuring-disaster-recovery/zia-disaster-recovery.png)