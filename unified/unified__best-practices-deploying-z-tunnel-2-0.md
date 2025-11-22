# Best Practices for Deploying Z-Tunnel 2.0
Source: https://help.zscaler.com/unified/best-practices-deploying-z-tunnel-2-0
PDF: https://help.zscaler.com/pdf/com/en/1495036.pdf

Below are best practices you can follow to ensure successful deployment of Zscaler Tunnel (Z-Tunnel) 2.0 for your organization.
You must have Zscaler Client Connector 2.0.1 (and later) to use Z-Tunnel 2.0.
- [Phase 1: Identify group of users and configure Z-Tunnel 2.0 settings](#phase1)
- [Phase 2: Block ICMP traffic to perform initial testing](#phase2)
- [Phase 3: Exclude internal network ranges from Z-Tunnel 2.0](#phase3)
- [Phase 4: Continue to test the group for one to two weeks](#phase4)
- [Phase 5: Roll out Zscaler Client Connector 2.0.1 and Z-Tunnel 2.0](#phase5)
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
[]To perform initial testing, begin by ensuring that ICMP traffic is blocked.
To block ICMP traffic:
- Ping google.com.
- Verify that ICMP traffic is seen on file for all logs.
- Create a firewall rule to block ICMP traffic.
- Ping google.com to test this rule.
- Verify that ICMP traffic is blocked on all logs.
[]To exclude these ranges, you must add them to the **Destination Exclusions** list in the app profile you created for testing. To learn more, see [VPN Gateway Bypasses](/unified/best-practices-adding-bypasses-z-tunnel-2-0).
To learn more about app profiles, see [Configuring Zscaler Client Connector App Profiles](/unified/configuring-zscaler-client-connector-app-profiles).
[]Continue to test this group of test users for one to two weeks.
To test your Z-Tunnel 2.0 configuration:
- Identify the top business applications that your organization uses.
- Test access to these applications with the test user group.
- Get user feedback on any issues they experience.
[]Roll out Zscaler Client Connector 2.0.1 and Z-Tunnel 2.0 to the rest of your employees in batches of 100-200 users. Each time you roll out Zscaler Client Connector and Z-Tunnel 2.0 to a group, you must ensure that your business applications are unaffected.