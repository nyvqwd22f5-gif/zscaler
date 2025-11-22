# Zscaler Traffic Bypasses
Source: https://help.zscaler.com/unified/zscaler-traffic-bypasses
PDF: https://help.zscaler.com/pdf/com/en/1495311.pdf

This article provides detailed information about the types of traffic bypasses available in the Zscaler cloud. The following sections illustrate how you can bypass certain application traffic or web traffic in the Zscaler cloud.
- [Zscaler Client Connector](#zscaler-client-connector)
- [SSL Inspection](#ssl-bypass-traffic-rule)
- [Firewall Control Policy](#firewall-control-bypass-rule)
[]The Zscaler Client Connector has an Application Bypass feature that allows you to automatically bypass specific applications from being tunneled through Z-Tunnel 2.0. You need to add the applications that you want to bypass in the **Application Bypass** field while configuring the App Profiles in Zscaler Client Connector. To learn more, see [Configuring Zscaler Client Connector App Profiles](/unified/configuring-zscaler-client-connector-app-profiles).
[See image.](#zcc-application-bypass-windows-macos)
This application bypass is only applicable for [Windows](/unified/configuring-zscaler-client-connector-app-profiles#windows) and [macOS](/unified/configuring-zscaler-client-connector-app-profiles#macOS) App Profiles and if you use Z-Tunnel 2.0 as your forwarding profile in Zscaler Client Connector. You can also view the details of the bypassed applications on the [Application Bypass Info](/unified/about-application-bypass) page.
Full visibility of the traffic bypassed by Zscaler Client Connector, such as bypassed session, bypassed session event time, and flow type is logged and displayed in the [Web](/unified/web-insights-logs-columns) and [Firewall](/unified/firewall-insights-logs-columns) Insights Logs in the Admin Portal.
[See sample Web Logs.](#zcc-web-logs-bypassed-traffic)
[See sample Firewall Logs.](#zcc-firewall-logs-bypassed-traffic)
Application-Based Bypass in Android
Zscaler recommends bypassing Android application traffic. While configuring the [Android App Profile](/unified/configuring-zscaler-client-connector-app-profiles#android), you can automatically bypass standard messaging applications on Android using the following steps:
- Enable the **Bypass Traffic for MMS Applications** field to ensure that Android does not interfere with MMS, which also uses mobile data.
- Add the app’s identifier to the **Bypass Traffic for Specific Applications** field to bypass specific Android application traffic. You can find the app's identifier after the ID parameter in the URL of the app's Play Store details. For custom applications (i.e., applications not available in the Play Store), add the package name instead of the app’s identifier in the field.
[See image.](#zcc-application-bypass-android)
If you are not aware of the package name of the application, use PAC file-based exclusion to bypass specific hostnames and IP addresses. To do that, configure a [custom PAC file](/unified/using-custom-pac-files-forward-traffic-internet-saas) on the Admin Portal to bypass the Google FQDNs, and add that PAC URL to the **Custom PAC URL** field while adding an Android App Profile.
[See image.](#zcc-pac-config-android)
[]The Zscaler exception list for SSL Inspection includes a few dozen known domains or destinations, such as Zscaler service IP addresses for Zscaler best practices, contactservice.zoom.us for UCaaS bypass, and self.events.data.microsoft.com for O365 bypass events, which cannot be SSL inspected for various reasons. These domains are not exposed as they are subject to change.
The predefined *Zscaler Recommended Exemptions* rule under the** Policies **>** Common Configuration** >** SSL Inspection **>** SSL Inspection Policy **page, automatically exempts known destinations that cannot be SSL inspected when it is enabled. If you want to SSL inspect certain domains from the exempted list, create an inspection rule with higher rule order. Disable the predefined rule for SSL inspecting all domains. To learn more, see [About SSL Inspection Policy](/unified/about-ssl-inspection-policy).
You can find transactions that are not SSL inspected or blocked after an inspection under the **SSL Policy Reason** filter in the [Web Insights Logs](/unified/web-insights-logs-columns). The percentage of traffic automatically SSL bypassed is relatively small (less than 1%).
[See sample Web Logs.](#ssl-bypassed-traffic)
SSL inspection also does not work on applications that use [certificate pinning](/unified/certificate-pinning-and-ssl-inspection) because the client application is hardcoded to accept only one specific client certificate. They should be included in the list of URL categories for which SSL transactions are not decrypted. To manage the certificate pinning exempted applications, Zscaler recommends referring to the [Certificate Pinning and SSL Inspection](/unified/certificate-pinning-and-ssl-inspection) article.
[]The Firewall Control policy has a predefined implicit **Zscaler Bypass Traffic **rule** **which applies only to self-traffic destined for the Zscaler cloud. This rule is logged and displayed under the **Rule Name** column in the [Firewall Insights Logs](/unified/firewall-insights-logs-columns) and [DNS Insights Logs](/unified/dns-insights-logs-columns).
- [Firewall Logs](#firewall-logs)
- [DNS Logs](#dns-logs)
Zscaler recommends keeping the predefined *Zscaler Proxy Traffic* rule enabled. When the recommended predefined rule is disabled, the *Zscaler Bypass Traffic* rule is triggered.
[]The Zscaler Bypass Traffic rule populates in the Firewall logs when:
- The web module does not accept control for the traffic evaluation from the firewall module because the handshake abruptly terminates during flow establishment.
- The traffic is forwarded from a firewall-enabled sublocation but not enabled to the parent location or another sublocation under the same parent location. This happens due to the latency in identifying these location differences, such as in the X-Forwarded-For (XFF) configuration.
[See sample Firewall Logs.](#firewall-zscaler-bypass-traffic-rule)
There is another implicit rule called **Blocked by Web Proxy Policy** in [Firewall Insights Logs](/unified/firewall-insights-logs-columns), which populates when a web policy blocks traffic while it is being evaluated by deep packet inspection to identify the network application to which the traffic belongs.
[]The Zscaler Bypass Traffic rule populates in the DNS logs when:
- When the domain name in the DNS request query matches a Zscaler cloud domain.
- When the DNS request query matches an Office 365 endpoint listed in the [Office 365 One Click predefined firewall filtering rules](/unified/understanding-predefined-firewall-filtering-rules#office-one-click) if enabled.
- When the DNS response does not contain a resolved IP or CNAME.
- When the DNS response is not completely analyzed because of its resource record type. DNS Control performs a detailed analysis of responses for A, AAAA, CNAME, and PTR record types.
[See sample DNS Logs.](#sample-dns-logs)
![Screenshot of Application Bypass section in Zscaler Client Connector App Profile page](/downloads/zia/traffic-forwarding/understanding-zscaler-traffic-bypasses/zia-understanding-zscaler-taffic-bypasses-Z-tunnel-2.0-config.png)
[]
![Screenshot of the Web Logs page in the ZIA Admin Portal displaying the bypassed traffic transaction and time](/downloads/zia/traffic-forwarding/understanding-zscaler-traffic-bypasses/zia-understanding-zscaler-taffic-bypasses-zcc-web-logs.png)
[]
[]![Screenshot of the Firewall Logs page in the ZIA Admin Portal displaying the bypassed traffic session and time](/downloads/zia/traffic-forwarding/understanding-zscaler-traffic-bypasses/zia-understanding-zscaler-taffic-bypasses-zcc-firewall-logs.png)
![Screenshot of Application Bypass section for Andriod in Zscaler Client Connector App Profile page](/downloads/zia/traffic-forwarding/understanding-zscaler-traffic-bypasses/zia-understanding-zscaler-taffic-bypasses-zcc-android.png)
[]
![Screenshot of PAC Configuration section for Andriod in Zscaler Client Connector App Profile page](/downloads/zia/traffic-forwarding/understanding-zscaler-traffic-bypasses/zia-understanding-zscaler-taffic-bypasses-Z-tunnel-pac-config.png)
[]
[]![Screenshot of the Web Logs page in the ZIA Admin Portal displaying the SSL bypassed traffic](/downloads/zia/traffic-forwarding/understanding-zscaler-traffic-bypasses/zia-understanding-zscaler-taffic-bypasses-ssl-bypass-web-logs.png)
[]![Screenshot if the Rule Name column displaying Zscaler Bypass Traffic in the DNS Logs](/downloads/zia/traffic-forwarding/understanding-zscaler-traffic-bypasses/zia-understanding-zscaler-taffic-bypasses-firewall-bypass-dns-logs.png)
[]![Screenshot of the Firewall Logs page in the ZIA Admin Portal displaying the Zscaler Bypass Traffic rule name](/downloads/zia/traffic-forwarding/understanding-zscaler-traffic-bypasses/zia-understanding-zscaler-taffic-bypasses-firewall-bypass-firewall-logs.png)