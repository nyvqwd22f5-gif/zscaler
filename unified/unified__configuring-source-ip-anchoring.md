# Configuring Source IP Anchoring
Source: https://help.zscaler.com/unified/configuring-source-ip-anchoring
PDF: https://help.zscaler.com/pdf/com/en/1497696.pdf

Source IP Anchoring uses the Internet & SaaS forwarding policies and Private Applications' App Connectors to selectively forward the application traffic to the appropriate destination servers. You can configure forwarding rules in the Admin Portal to forward Source IP Anchored traffic to the Private Applications through Internet & SaaS threat and data protection engines. To learn more, see [Understanding Source IP Anchoring](/unified/understanding-source-ip-anchoring).
To enable and configure Source IP Anchoring:
- Complete the following steps to do the initial setup on the Admin Portal if you are using Private Applications solely for Source IP Anchoring. You can skip this step if you have already done the initial setup in the Admin Portal.
- [Update your company and administrator information](/zpa/step-step-configuration-guide-zpa#UpdateCompanyAdminInfo).
- [Configure the enrollment certificates for the App Connectors](/zpa/step-step-configuration-guide-zpa#ConfigureCertificates). For Source IP Anchoring, it is sufficient if you configure the enrollment certificates only for the App Connectors.
- [(Optional) Configure Single Sign-On Authentication](/zpa/step-step-configuration-guide-zpa#ConfigureSSO).
- [Configure your App Connectors](/zpa/step-step-configuration-guide-zpa#ConfigureConnectors).
- Configure the following items in the Admin Portal:
-
[Create and configure an application segment for which you need Source IP Anchoring.](/unified/configuring-defined-application-segments)
Ensure that you enable the **Source IP Anchor** option and select **Use Client Forwarding Policy** under the Bypass field while configuring the application segment.
-
[Configure a client forwarding policy for the application segment.](/unified/configuring-client-forwarding-policies) You should create separate client forwarding policy rules for IP address-based and domain-based applications.
For IP address-based applications, select the** Only Forward Allowed Applications** rule action for Source IP Anchoring application segments.
For domain-based applications, configure the following rules:
- Rule 1: Select the **Bypass ZPA** rule action for Source IP Anchoring **Segment Groups** and **Client Types** >** Client Connector**.
- Rule 2: Select the **Forward to ZPA** rule action for Source IP Anchoring** Segment Groups** and **Client Types** > **ZIA Service Edge**.
-
[Create and configure an access policy for the application segment.](/unified/configuring-access-policies) You should create separate access policy rules for IP address-based and domain-based applications.
For IP address-based applications, configure the following rules:
- Rule 1: Select the **Block Access** rule action and add all the client types, except the **ZIA Service Edge** client type for the application segments. This rule prevents application download on the Zscaler Client Connector.
- Rule 2: Select the **Allow Access** rule action and add only the **ZIA Service Edge** client type for the application segments.
For domain-based applications, ensure that you allow the Source IP Anchoring client (ZIA Service Edge client type) to access the applications.
-
Configure the following items in the Admin Portal:
To support Source IP Anchoring for Zscaler Tunnel (Z-Tunnel) 1.0 traffic, you must enable the **Enable Firewall for Z-Tunnel 1.0 and PAC Road Warriors** option under **Policies** > **Common Configuration** > **Advanced** > **Advanced Settings**.
- [Configure the Private Applications gateway.](/unified/configuring-zpa-gateway)
- [Configure the forwarding policies for Private Applications.](/unified/configuring-forwarding-policy#source-ip-anchoring) You can also configure rules for source IP-anchored traffic in these [Internet & SaaS policies](#zia-policies).
-
To configure Source IP Anchoring for all traffic forwarded to the Admin Portal, enable the appropriate pre-configured DNS filtering rule from the **Policies** > **Access Control** > **Firewall** > **DNS Control** page:
- For location users, enable the **ZPA Resolver for Locations** rule.
-
For remote users, enable the **ZPA Resolver for Road Warrior** rule.
When the ZPA Resolver for Road Warrior rule is disabled, the road warrior traffic automatically falls under the ZPA Resolver for Locations rule instead of blocking the traffic. Therefore, Zscaler does not recommend disabling the** ZPA Resolver for Road Warrior** rule.
Ensure that these DNS rules are the top rules (i.e., Rule 1 and Rule 2) to configure Source IP Anchoring. The DNS rules are associated with the respective preconfigured IP pools under **Policies** > **Access Control** > **Firewall** >**IP & FQDN Groups** > **IP Pool**. You can edit the IP pools based on your needs. To learn more, see [About IP Pool](/unified/about-ip-pool). Any change in the IP pool is reflected in the **Action** column of the respective DNS rule when the rule is enabled.
Zscaler also recommends having open firewall rules for the Source IP Anchoring pools while sending DNS traffic to the Zscaler service for the Source IP Anchoring domains (i.e., the **Action** column on the Firewall Filtering policy should be set to **Allow** for the Source IP Anchoring pools).
Ensure that your client's DNS requests for domain-based non-web traffic are forwarded to Zscaler services so the predefined ZPA DNS Resolver policies take effect.
- [][DLP Policy](/unified/about-data-loss-prevention)
- [DLP Policy with Content Inspection](/unified/configuring-dlp-policy-rules-content-inspection)
- [DLP Policy without Content Inspection](/unified/configuring-dlp-policy-rules-without-content-inspection)
- [File Type Control](/unified/configuring-file-type-control-policy)
- [Firewall Filtering](/unified/configuring-firewall-filtering-policy)
- [IPS Control](/unified/configuring-ips-control-policy)
- [Sandbox](/unified/about-sandbox)
- [SSL Inspection](/unified/configuring-ssl-inspection-policy)