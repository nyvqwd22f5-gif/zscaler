# Zscaler Traffic Bypasses
Source: https://help.zscaler.com/zia/zscaler-traffic-bypasses
PDF: https://help.zscaler.com/pdf/com/en/1440656.pdf

This article provides detailed information about the types of traffic bypasses available in the Zscaler cloud. The following sections illustrate how you can bypass certain application traffic or web traffic in the Zscaler cloud.
- [Zscaler Client Connector](#zscaler-client-connector)
- [SSL Inspection](#ssl-bypass-traffic-rule)
- [Firewall Control Policy](#firewall-control-policy)
[]The Zscaler Client Connector has an Application Bypass feature that allows you to automatically bypass specific applications from being tunneled through Zscaler Tunnel (Z-Tunnel) 2.0. You need to add the applications that you want to bypass in the **Application Bypass** field while configuring the App Profiles in the Zscaler Client Connector Portal. To learn more, see [Configuring Zscaler Client Connector App Profiles](/zscaler-client-connector/configuring-zscaler-client-connector-app-profiles).
[See image.](#zcc-application-bypass-windows-macos)
This application bypass is only applicable for [Windows](/zscaler-client-connector/configuring-zscaler-client-connector-app-profiles?referer=mobileadmin.zscalerbeta.net#windows) and [macOS](/zscaler-client-connector/configuring-zscaler-client-connector-app-profiles?referer=mobileadmin.zscalerbeta.net#macOS) App Profiles and if you use Z-Tunnel 2.0 as your forwarding profile in Zscaler Client Connector. You can also view the details of the bypassed applications on the [Application Bypass Info](/zscaler-client-connector/viewing-information-bypassed-applications-z-tunnel-2.0-configuration) page.
Full visibility of the traffic bypassed by Zscaler Client Connector, such as bypassed session, bypassed session event time, and flow type is logged and displayed in the [Web](/zia/web-insights-logs-columns) and [Firewall](/zia/firewall-insights-logs-columns) Insights Logs in ZIA Admin Portal.
[See sample Web Logs.](#zcc-web-logs-bypassed-traffic)
[See sample Firewall Logs.](#zcc-firewall-logs-bypassed-traffic)
Application-Based Bypass in Android
Zscaler recommends bypassing Android application traffic. While configuring the [Android App Profile](/zscaler-client-connector/configuring-zscaler-client-connector-app-profiles?referer=mobileadmin.zscalerbeta.net#android), you can automatically bypass standard messaging applications on Android using the following steps:
- Enable the **Bypass Traffic for MMS Applications** field to ensure that Android does not interfere with MMS, which also uses mobile data.
-
Add the app's identifier to the **Bypass Traffic for Specific Applications** field to bypass specific Android application traffic. You can find the app's identifier after the ID parameter in the URL of the app's Play Store details. For custom applications (i.e., applications not available in the Play Store), add the package name instead of the app’s identifier in the field.
[See image.](#zcc-application-bypass-android)
If you are not aware of the package name of the application, use PAC file-based exclusion to bypass specific hostnames and IP addresses. To do that, configure a [custom PAC file](/zia/using-custom-pac-file-forward-traffic-zia) in the ZIA Admin Portal to bypass the Google FQDNs, and add that PAC URL to the **Custom PAC URL** field while adding an Android App Profile.
[See image.](#zcc-pac-config-android)
[]The Zscaler exception list for SSL Inspection includes a few dozen known domains or destinations, such as Zscaler service IP addresses for Zscaler best practices, `contactservice.zoom.us` for UCaaS bypass, and `self.events.data.microsoft.com` for Microsoft 365 bypass events, which cannot be SSL inspected for various reasons. These domains are not exposed as they are subject to change.
The predefined **Zscaler Recommended Exemptions** rule under **Policy** > **SSL Inspection Policy **automatically exempts known destinations that cannot be SSL inspected when it is enabled. If you want to SSL inspect certain domains from the exempted list, create an inspection rule with a higher rule order. Disable the predefined rule for SSL inspecting all domains. To learn more, see [About SSL Inspection Policy](/zia/about-ssl-inspection-policy).
You can find transactions that are not SSL inspected or blocked after an inspection under the **SSL Policy Reason** filter in [Web Insights Logs](/zia/web-insights-logs-columns). The percentage of traffic automatically SSL bypassed is relatively small (less than 1%).
[See sample Web Logs.](#ssl-bypassed-traffic)
SSL inspection also does not work on applications that use [certificate pinning](/zia/public-key-pinning-and-zscaler) because the client application is hardcoded to accept only one specific client certificate. They should be included in the list of URL categories for which SSL transactions are not decrypted. To learn how to manage certificate pinning exempted applications, see [Certificate Pinning and SSL Inspection](/zia/certificate-pinning-and-ssl-inspection).
[]The following are some of the Firewall Control policy rules applied to traffic that is bypassing the Zscaler cloud:
- [Zscaler Bypass Traffic](#zscaler-bypass-traffic)
- [Blocked by Web Proxy Policy](#blocked-by-web-proxy-policy)
- [Other Implicit Rules for Traffic Bypasses](#other-implicit-rules-traffic-bypasses)
[]The Firewall Control policy has a predefined implicit **Zscaler Bypass Traffic **rule** **which applies to traffic that matches the following conditions. Transactions that match this rule are logged and displayed along with the rule name in [Firewall Insights Logs](/zia/firewall-insights-logs-columns) and [DNS Insights Logs](/zia/dns-insights-logs-columns).
- [Firewall Logs](#firewall-logs-zscaler-bypass-traffic)
- [DNS Logs](#dns-logs-zscaler-bypass-traffic)
Zscaler recommends keeping the predefined **Zscaler Proxy Traffic** rule enabled. When the recommended predefined rule is disabled, the **Zscaler Bypass Traffic** rule is triggered.
[]The **Zscaler Bypass Traffic** rule matches with traffic that meets the following criteria and populates in the Firewall Logs:
- The web module does not accept control for the traffic evaluation from the firewall module because the handshake abruptly terminates during flow establishment.
- The traffic is forwarded from a firewall-enabled sublocation but not enabled to the parent location or another sublocation under the same parent location. This happens due to the latency in identifying these location differences, such as in the X-Forwarded-For (XFF) configuration.
- Traffic is destined to a Zscaler-owned IP address. For HTTP CONNECT requests destined to a virtual IP address (VIP), this rule triggers the first policy match unless the inner traffic is destined elsewhere.
- Traffic forwarded using GRE tunnels matches this rule.
- Zscaler web proxy instructs the firewall that a connection should not pass through firewall policy enforcement.
- A sublocation has firewall disabled while other sublocations within the same parent location have it enabled, and there are policies applied to the sublocation (e.g., [Source IP Anchoring](/zia/configuring-source-ip-anchoring) or [Forwarding rules](/zia/configuring-forwarding-policy)). In this scenario, the ZIA Service Edge holds the session temporarily to evaluate all the sublocation's policies and apply the most suitable rule, logging the traffic with the Zscaler Bypass Traffic rule until evaluation is complete.
[See sample Firewall Logs.](#sample-firewall-logs-bypass-traffic-rule)
[]The Zscaler Bypass Traffic rule populates in the DNS logs when:
- The domain name in the DNS request query matches a Zscaler cloud domain.
- The DNS request query matches a Microsoft 365 endpoint listed in the [Microsoft 365 One Click predefined Firewall Filtering rules](/zia/about-predefined-firewall-filtering-rules#office-one-click) if enabled.
- The DNS response does not contain a resolved IP or CNAME.
- The DNS response is not completely analyzed because of its resource record type. DNS Control performs a detailed analysis of responses for A, AAAA, CNAME, and PTR record types.
[See sample DNS Logs.](#sample-dns-logs-traffic-bypass-rule)
[]This implicit rule is applied when a web policy blocks traffic while it is being evaluated by deep packet inspection to identify the network application to which the traffic belongs. You can view the transactions that match this rule in the [Firewall Insights Logs](/zia/firewall-insights-logs-columns).
[]The traffic flow from users might bypass firewall or DNS modules when the following scenarios occur:
-
When the ZIA Service Edge fails to establish a connection with the Zscaler Central Authority (CA), it results in the traffic flow passing through the firewall or DNS without policy application. This might occur when traffic flow from a specific user or location arrives at the Service Edge for the first time and a connection to the CA is required to apply policies. Firewall logs this transaction, and you can view this in [Firewall Logs](/zia/firewall-insights-logs-filters) by applying the **Action** > **Bypassed due to missing config** filter.
[See sample Firewall Logs.](#bypassed-due-to-missing-config-filter-logs)
-
If the Service Edge has established a connection with the CA but the requested configuration does not arrive from the CA within the expected time period (typically 5 seconds), it results in the traffic flow passing through the firewall without policy application. This might occur when traffic flow from a specific user or location arrives at the Service Edge for the first time and a connection to the CA is established, but there is no response from the CA within the expected timeframe. Firewall logs this transaction, and you can view this in [Firewall Logs](/zia/firewall-insights-logs-filters) by applying the **Action** > **Timed out while waiting for a config** filter.
[See sample Firewall Logs.](#timed-out-while-waiting-for-config-filter-logs)
![Application Bypass section for Windows and macOS](/downloads/zia/traffic-forwarding/zscaler-traffic-bypasses/zia-understanding-zscaler-taffic-bypasses-Z-tunnel-2.0-config.png)
[]
![Web Logs page](/downloads/zia/traffic-forwarding/zscaler-traffic-bypasses/zia-understanding-zscaler-taffic-bypasses-zcc-web-logs.png)
[]
[]![Firewall Logs page](/downloads/zia/traffic-forwarding/zscaler-traffic-bypasses/zia-understanding-zscaler-taffic-bypasses-zcc-firewall-logs.png)
![Application Bypass section for Andriod](/downloads/zia/traffic-forwarding/zscaler-traffic-bypasses/zia-understanding-zscaler-taffic-bypasses-zcc-android.png)
[]
![PAC Configuration section](/downloads/zia/traffic-forwarding/zscaler-traffic-bypasses/zia-understanding-zscaler-taffic-bypasses-Z-tunnel-pac-config_0.png)
[]
[]![Web Logs page for SSL bypassed traffic](/downloads/zia/traffic-forwarding/zscaler-traffic-bypasses/zia-understanding-zscaler-taffic-bypasses-ssl-bypass-web-logs.png)
[]![Zscaler Bypass Traffic in the DNS Logs](/downloads/zia/traffic-forwarding/zscaler-traffic-bypasses/zia-understanding-zscaler-taffic-bypasses-firewall-bypass-dns-logs.png)
[]![Firewall Logs page for Zscaler Bypass Traffic rule](/downloads/zia/traffic-forwarding/zscaler-traffic-bypasses/zia-understanding-zscaler-taffic-bypasses-firewall-bypass-firewall-logs.png)
[]![Bypassed due to missing config filter in Firewall Logs](/downloads/zia/traffic-forwarding/zscaler-traffic-bypasses/firewall-logs-bypassed-due-to-missing-config.png)
[]![ Timed out while waiting for config filter in Firewall Logs](/downloads/zia/traffic-forwarding/zscaler-traffic-bypasses/firewall-logs-timed-out-while-waiting-for-config.png)