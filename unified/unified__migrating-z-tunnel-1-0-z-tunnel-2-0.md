# Migrating from Z-Tunnel 1.0 to Z-Tunnel 2.0
Source: https://help.zscaler.com/unified/migrating-z-tunnel-1-0-z-tunnel-2-0
PDF: https://help.zscaler.com/pdf/com/en/1495416.pdf

Complete the following steps to ensure a successful migration from Zscaler Tunnel (Z‑Tunnel) 1.0 to Z‑Tunnel 2.0 for your organization.
Your Zscaler Client Connector must be version 2.0.1 or later to use Z‑Tunnel 2.0.
- [Step 1: Identify group of users and configure Z‑Tunnel 2.0 settings](#phase1)
- [Step 2: Add VPN gateway bypasses to the Z‑Tunnel 2.0 app profile](#phase2)
- [Step 3: Add the network address and range bypasses to the Z‑Tunnel 2.0 app profile](#phase3)
- [Step 4: Add the URL and domain-based bypasses Z‑Tunnel 2.0 PAC files](#phase4)
- [Step 5: Test the Z‑Tunnel 2.0 configuration](#phase5)
- [Step 6: Roll out Zscaler Client Connector version 2.0.1 and Z‑Tunnel 2.0](#phase6)
[]
For initial testing, begin by identifying a group of users and configuring Z-Tunnel 2.0 settings.
- [Step 1: Create a Group](#step1)
- [Step 2: Create a Forwarding Profile Policy](#step2)
- [Step 3: Create an App Profile Policy](#step3)
- [Step 4: Assign Zscaler Client Connector 2.0.1 to the Group](#step4)
[]In the Admin Portal, identify and create a small group of users for testing Z-Tunnel 2.0. Groups you configure for Internet & SaaS are automatically available for selection within the Admin Portal. You can also manually sync the groups. To learn more, see [Syncing Directory Groups between Internet & SaaS and Zscaler Client Connector](/unified/syncing-directory-groups-between-internet-saas-and-zscaler-client-connector).
[]To prevent confusion, Zscaler recommends creating a new forwarding profile for your Z-Tunnel 2.0 test. The forwarding profile policy determines what traffic Zscaler Client Connector captures from users’ devices. You enable the forwarding mechanism for Z-Tunnel 2.0 in this policy.
To enable Z-Tunnel 2.0, you must configure the following settings in the forwarding profile:
- For **Tunnel Driver Type**: Select **Packet Filter Based**.
- For **On Trusted Network**, select **Tunnel**.
- For **Tunnel Version Selection**, select** Z-Tunnel 2.0**.
- For **VPN Trusted Network** and **Off Trusted Network**, select **Same as "On Trusted Network"**.
For testing purposes, Zscaler recommends that you don’t configure the **VPN Trusted Network** and** Off Trusted Network** forwarding profile actions. After initial testing, you can change the behavior for all network environments.
Leave all other settings as default. To learn more about forwarding profiles, see [Configuring Forwarding Profiles for Zscaler Client Connector](/unified/configuring-forwarding-profiles-zscaler-client-connector).
[]Create a new app profile policy and associate your test users and the Z-Tunnel 2.0 forwarding profile to it.
To configure Z-Tunnel 2.0, you must configure the following in the app profile:
- For **Rule Order**, select **1** to ensure that your users receive this app profile above other profiles.
- Select **Enable**.
- For **Groups**, select the group of your test users.
- Leave the **Logout Password**, **Disable Password**, and **Custom PAC URL** fields empty.
- For **Forwarding Profile**, select the forwarding profile you created for testing.
- Select **Install Zscaler SSL Certificate**.
Leave all other settings as default. To learn more app profiles, see [Configuring Zscaler Client Connector App Profiles](/unified/configuring-zscaler-client-connector-app-profiles).
[]You can configure a Zscaler Client Connector Store group policy to assign Zscaler Client Connector 2.0.1 to your test users. To learn more, see [Configuring an App Update in the Zscaler Client Connector App Store](/unified/configuring-app-update-zscaler-client-connector-app-store).
[]Add the VPN gateway bypasses from **Hostname or IP Address Bypass for VPN Gateway** in your original app profile to the Z‑Tunnel 2.0 app profile you created. To learn more, see [VPN Gateway Bypasses](/unified/best-practices-adding-bypasses-z-tunnel-2-0).
Leave all other settings as default. To learn more app profiles, see [Configuring Zscaler Client Connector App Profiles](/unified/configuring-zscaler-client-connector-app-profiles).
[]You must add your network address and range bypasses to the Z‑Tunnel 2.0 app profile. First, gather all the network address and range bypasses in the original app profile PAC file. Then, in the Z‑Tunnel 2.0 app profile, add the bypasses to the **Destination Exclusions** list. To learn more about destination exclusions, see [Destination Exclusions and Inclusions](/unified/best-practices-adding-bypasses-z-tunnel-2-0).
To learn more app profiles, see [Configuring Zscaler Client Connector App Profiles](/unified/configuring-zscaler-client-connector-app-profiles).
[]You must add the URL and domain-based bypasses from your original app profile PAC file to your Z‑Tunnel 2.0 configured forwarding and app profile PAC files.
To add the URL and domain-based bypasses:
- Gather the URL and domain-based bypasses from your original app profile PAC file.
-
Create a new forwarding profile PAC file to route these destinations to the Z‑Tunnel 2.0 bypass gateway. Use the following Z‑Tunnel 2.0 bypass return statement for your domains.
`function FindProxyForURL(url, host) {
/* Updates are directly accessible */
if (dnsDomainIs(host, "``<domain>``"))
return "PROXY ${ZAPP_TUNNEL2_BYPASS}";
/* Default Traffic Forwarding. Return DIRECT to tunnel using Tunnel2 */
return "DIRECT";
}          `
For <domain>, enter the URL and domain-based bypasses.
- Add the new PAC file to the forwarding profile that you created for Z‑Tunnel 2.0. To learn more, see [Configuring Forwarding Profiles for Zscaler Client Connector](/unified/configuring-forwarding-profiles-zscaler-client-connector).
-
Create a new app profile PAC file to send these bypasses directly. Use the following Z‑Tunnel 2.0 return statement for your domains.
function FindProxyForURL(url, host) {
var privateIP = /^(0|10|127|192\.168|172\.1[6789]|172\.2[0-9]|172\.3[01]|169\.254|192\.88\.99)\.[0-9.]+$/;
var resolved_ip = dnsResolve(host);
/* Updates are directly accessible */
if (dnsDomainIs(host, "<domain>"))
return "DIRECT";
/* Default Traffic Forwarding */
return "PROXY ${GATEWAY}:443";
}
For <domain>, enter the URL and domain-based bypasses.
[]Test to ensure that general user experience is unaffected by these changes.
To test your Z‑Tunnel 2.0 configuration:
- Identify the top business applications that your organization uses.
- Test access to these applications with the test user group.
- Get user feedback on any issues they experience.
[]Roll out Zscaler Client Connector version 2.0.1 and Z‑Tunnel 2.0 to the rest of your employees in batches of 100–200 users. Each time you roll out Zscaler Client Connector and Z‑Tunnel 2.0 to a group, you must ensure that your business applications are unaffected.