# Best Practices for Zscaler Client Connector Deployment
Source: https://help.zscaler.com/unified/best-practices-zscaler-client-connector-deployment
PDF: https://help.zscaler.com/pdf/com/en/1492351.pdf

Following are best practices you can follow to ensure successful deployment of Zscaler Client Connector for your organization. You can also create a specific user group for testing the latest version of Zscaler Client Connector before deploying it to all your organization's user groups. For more information, see [Best Practices for Deploying Zscaler Client Connector Version Updates](/unified/best-practices-updating-latest-versions-zscaler-client-connector-application).
Platform Configuration
Gather as much information as possible about the computers being used by your organization. See below for some of the information you'll want to collect about your users' computers. Zscaler recommends you test Zscaler Client Connector on as many different computers as possible in each phase. This will allow you to discover and resolve any issues the app might encounter on different computer images and in different infrastructures, before it is fully deployed to all users.
For the Windows and macOS computers users will be on, gather the following information:
- **Versions**: What OS versions are being used?
- **Browsers**: What browsers are being used?
- **VPN**: What VPN clients are being used?
- **Antivirus**: What antivirus solutions are being used?
- **Firewall**: What firewalls are being used?
- **Management**: What computer management mechanisms are being used?
- **Key Applications**: What key applications are being used?
- **Application Distribution**: How are application packages distributed?
- **Other**: Take note of any other platform features that might impact Zscaler Client Connector functionality.
Deployment Phases
Zscaler recommends the following four-phase approach for deployment:
- [Phase 1: IT Test - 25-50 users](#Phase1)
- [Phase 2: Expanded IT Test - Another 100 to 150 users](#Phase2)
- [Phase 3: End User Group - Another 200 to 300 users](#Phase3)
- [Phase 4: Remaining Users - All remaining users, in groups of 1,000 users each](#Phase4)
[]Begin by deploying the app to about 25-50 users in your organization's IT group.
**Goal**: To discover different use cases for the app in your organization and ensure that it is properly configured for those use cases.
**Success Criteria**: No blockers exist for moving to the next phase.
Following are the recommended tests for IT group:
- [Test Interoperability with VPN Clients](#test-1)
- [Test Functionality On and Off Trusted Networks](#test-2)
- [Test Traffic Exemptions](#test-3)
- [Test SSL Inspection](#test-4)
- [Test Custom App Profiles](#test-5)
[]If your users will be running Zscaler Client Connector in conjunction with VPN clients or applications that function like VPNs (for example, Microsoft DirectAccess), take steps to ensure users don't face interoperability issues. Zscaler recommends selecting **Tunnel with Local Proxy** as the forwarding profile action in your forwarding profiles.
For a complete list of recommended steps, see [Best Practices for Zscaler Client Connector and VPN Client Interoperability](/unified/best-practices-zscaler-client-connector-and-vpn-client-interoperability).
Confirm that users can run Zscaler Client Connector with VPN clients together without any connectivity issues.
[]Take steps to ensure Zscaler Client Connector forwards traffic properly on and off trusted networks. The app must be able to detect trusted networks and untrusted networks and forward user traffic as configured in forwarding profiles. Try configuring your forwarding profiles so that the app disables its services when users are on trusted networks that have GRE or IPsec tunnels forwarding traffic to Zscaler. Then, test the configuration to ensure the app behaves as expected, and user traffic is sent to Zscaler through the GRE or IPsec tunnels rather than through the app.
To learn more, see [Configuring Forwarding Profiles for Zscaler Client Connector](/unified/configuring-forwarding-profiles-zscaler-client-connector).
Confirm that Zscaler Client Connector properly forwards traffic on and off trusted networks.
[]Some applications or websites your users access might be incompatible with proxy services enabled by Zscaler Client Connector. If so, create PAC files so you can exempt some user traffic from being forwarded with the app. You can specify the URL for this PAC file when [configuring Zscaler Client Connector app profiles](/unified/configuring-zscaler-client-connector-app-profiles) and [forwarding profiles](/unified/configuring-forwarding-profiles-zscaler-client-connector). If you have DNS resolve, add this function to the forwarding profile PAC file only, to avoid duplication of the DNS query.
Confirm that traffic to applications or websites specified as exempt from Zscaler Client Connector in the PAC file are not forwarded by the app, and ensure users can access them properly with the app running.
[]If you want Zscaler to perform SSL inspection on traffic forwarded by Zscaler Client Connector, you must:
- Turn on the** Install Zscaler SSL Certificate** option when [configuring app profiles](/unified/configuring-zscaler-client-connector-app-profiles). If you want to use your organization's custom SSL certificate, [upload the custom certificate](/unified/uploading-custom-ssl-certificate-zscaler-client-connector) on the **Advanced Configuration** page and Zscaler automatically uses this certificate for Zscaler Client Connector.
The Install Zscaler SSL Certificate feature is not supported on devices running macOS Big Sur (11) and later.
- For Internet & SaaS, in the **Policy for Zscaler Client Connector** section of the [SSL Inspection](/zia/deploying-ssl-inspection) page in the Admin Portal, enable to perform SSL inspection for Zscaler Client Connector users on each relevant platform.
- Ensure all applications that perform [certificate pinning](/unified/certificate-pinning-and-ssl-inspection) are specified under **Do Not Inspect these Applications** on the [SSL Inspection](/unified/deploying-ssl-inspection) page in the Admin Portal.
- Conduct the recommended tests described in [Best Practices for Testing and Rolling Out SSL Inspection](/unified/best-practices-testing-and-rolling-out-ssl-inspection).
Confirm that SSL inspection is being correctly performed on traffic forwarded by Zscaler Client Connector.
[]Try configuring custom app profiles to ensure Zscaler Client Connector functions as intended for your organization. In particular, Zscaler recommends selecting the following options when [configuring app profiles](/unified/configuring-zscaler-client-connector-app-profiles):
- If you want to enable SSL inspection of traffic forwarded by Zscaler Client Connector, select **Install Zscaler SSL Certificate**.
The **Install Zscaler SSL Certificate** feature is not supported on devices running macOS Big Sur (11) and later.
- For **Log Mode**, select **Debug** in Phase 1 and **Error** in Phase 4.
- If configuring app profiles for Windows users and if the app is running in **Tunnel with Local Proxy** mode:
- **Disable Loopback Restriction**: Required for **Tunnel with Local Proxy** mode
- **Override WPAD**: Unless the devices must utilize WPAD, Zscaler recommends selecting this option for fresh installations where WPAD is still present or received by DHCP.
- **Restart WinHTTP Service**: Zscaler recommends selecting this option to delete any cached WPAD settings.
Confirm that the custom app profiles allows the app to meet the needs of your organization.
Expand the group of users by deploying the app to another 100-150 users in your organization's IT group as a pilot.
[]**Goal**: To ensure Zscaler Client Connector functionality on a variety of platforms, with different applications and use cases.
**Success Criteria**: No blockers exist for moving to the next phase.
[]Deploy Zscaler Client Connector to 200-300 end users in your organization.
**Goal**: To ensure app functionality for a smaller group of end users before full deployment to all end users.
**Success Criteria**: No blockers exist for moving to the next phase.
[]Deploy Zscaler Client Connector to your organization's remaining end users, in batches of 1,000 users.
**Goal**: To ensure Zscaler Client Connector functionality for full deployment to all end users.
**Success Criteria**: No blockers exist.