# Configuring Source IP Anchoring
Source: https://help.zscaler.com/zia/configuring-source-ip-anchoring
PDF: https://help.zscaler.com/pdf/com/en/1401551.pdf

[Watch a video about configuring Source IP Anchoring.](https://fast.wistia.net/embed/iframe/qya3lmmz5t)
Source IP Anchoring uses ZIA forwarding policies and Zscaler Private Access (ZPA) App Connectors to selectively forward the application traffic to the appropriate destination servers. You can configure forwarding rules in the ZIA Admin Portal to forward Source IP Anchored traffic to ZPA through ZIA threat and data protection engines. To learn more, see [Understanding Source IP Anchoring](/zia/understanding-source-ip-anchoring).
To enable and configure Source IP Anchoring:
- Complete the following steps to do the initial setup on the ZPA Admin Portal if you are using ZPA solely for Source IP Anchoring. You can skip this step if you have already done the initial setup on the ZPA Admin Portal.
- [Update your company and administrator information](/zpa/step-step-configuration-guide-zpa#UpdateCompanyAdminInfo).
- [Configure the enrollment certificates for the App Connectors](/zpa/step-step-configuration-guide-zpa#ConfigureCertificates). For Source IP Anchoring, it is sufficient if you configure the enrollment certificates only for the App Connectors.
- [(Optional) Configure Single Sign-On Authentication](/zpa/step-step-configuration-guide-zpa#ConfigureSSO).
- [Configure your App Connectors](/zpa/step-step-configuration-guide-zpa#ConfigureConnectors).
- Configure the following items in the ZPA Admin Portal:
-
[Create and configure an application segment for which you need Source IP Anchoring.](/zpa/configuring-application-segments)
Ensure that you enable the **Source IP Anchor** option and select **Use Client Forwarding Policy** under the Bypass field while configuring the application segment.
-
[Configure a client forwarding policy for the application segment.](/zpa/configuring-client-forwarding-policies) You should create separate client forwarding policy rules for IP address-based and domain-based applications.
For IP address-based applications, select the** Only Forward Allowed Applications** rule action for Source IP Anchoring application segments.
For domain-based applications, configure the following rules:
- Rule 1: Select the **Bypass ZPA** rule action for Source IP Anchoring **Segment Groups** and **Client Types** >** Client Connector**.
- Rule 2: Select the **Forward to ZPA** rule action for Source IP Anchoring** Segment Groups** and **Client Types** > **ZIA Service Edge**.
-
[Create and configure an access policy for the application segment.](/zpa/configuring-access-policies) You should create separate access policy rules for IP address-based and domain-based applications.
For IP address-based applications, configure the following rules:
- Rule 1: Select the **Block Access** rule action and add all the client types, except the **ZIA Service Edge** client type for the application segments. This rule prevents application download on the Zscaler Client Connector.
- Rule 2: Select the **Allow Access** rule action and add only the **ZIA Service Edge** client type for the application segments.
For domain-based applications, ensure that you allow the Source IP Anchoring client (ZIA Service Edge client type) to access the applications.
- Configure the following items in the ZIA Admin Portal:
To support Source IP Anchoring for Zscaler Tunnel (Z-Tunnel) 1.0 traffic, you must enable the **Enable Firewall for Z-Tunnel 1.0 and PAC Road Warriors** option under **Administration** > **Advanced Settings**.
- [Configure the ZPA gateway.](/zia/configuring-zpa-gateway)
- [Configure the forwarding policies for ZPA.](/zia/configuring-forwarding-policies#source-ip-anchoring) You can also configure rules for source IP-anchored traffic in these [ZIA policies](#zia-policies).
-
To configure Source IP Anchoring for all traffic forwarded to the ZIA Admin Portal, enable the appropriate pre-configured DNS filtering rule from the **Policy** > **DNS Control** page:
-
For remote users, enable the **ZPA Resolver for Road Warrior** rule.
Zscaler does not recommend disabling the** ZPA Resolver for Road Warrior** rule. If disabled, the road warrior traffic falls under the **ZPA Resolver for Locations** rule instead of blocking the traffic. This leads to the source IP-anchored traffic being resolved by the **ZPA Resolver for Locations** IP pools and the traffic is not routed as intended.
- For location users, enable the **ZPA Resolver for Locations** rule.
Zscaler recommends the following best practices for forwarding source IP-anchored traffic to ZIA:
- The DNS rule order for the **ZPA Resolver for Road Warrior** rule should be a higher rule than the **ZPA Resolver for Locations** rule to configure Source IP Anchoring. For example, if **ZPA Resolver for Road Warrior** is at rule 4, then the **ZPA Resolver for Locations** should be at rule 5 and later.
- The DNS rules are associated with the respective preconfigured [IP pools](/zia/about-ip-pool). Any change in the IP pool is reflected in the **Action** column of the respective DNS rule when the rule is enabled.
- Configure open firewall rules for the Source IP Anchoring pools while sending DNS traffic to the Zscaler service for the Source IP Anchoring domains (i.e., the **Action** column on the Firewall Filtering policy should be set to **Allow** for the Source IP Anchoring pools).
- The client's DNS requests for domain-based non-web traffic should be forwarded to Zscaler service so the predefined ZPA DNS Resolver policies take effect.
- [][DLP Policy](/zia/about-data-loss-prevention)
- [DLP Policy with Content Inspection](/zia/configuring-dlp-policy-rules-content-inspection)
- [DLP Policy without Content Inspection](/zia/configuring-dlp-policy-rules-without-content-inspection)
- [File Type Control](/zia/configuring-file-type-control-policy)
- [Firewall Filtering](/zia/configuring-firewall-filtering-policy)
- [IPS Control](/zia/configuring-ips-control-policy)
- [Sandbox](/zia/about-sandbox)
- [SSL Inspection](/zia/configuring-ssl-inspection-policy)