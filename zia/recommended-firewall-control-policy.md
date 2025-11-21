# Recommended Firewall Control Policy
Source: https://help.zscaler.com/zia/recommended-firewall-control-policy
PDF: https://help.zscaler.com/pdf/com/en/1399901.pdf

The Zscaler service provides a default firewall filtering rule that blocks all traffic from your network to the internet. The default rule always maintains the lowest precedence (i.e. lowest rule order) and cannot be deleted. However, certain attributes of the rule, such as the rule action and logging option can be modified by admins with the [super admin](/zia/what-super-admin-role) role.
[See image.](#default-rule)
With the default firewall filtering rule set to block all traffic, you can create higher-order rules with granularity to allow traffic that matches specific conditions. Zscaler recommends that you configure the following firewall filtering rule:
- **Rule Order**: Select Rule Order **1 **or the highest order for admin-defined rules (as opposed to system-defined rules like Office 365 One Click Rule, Zscaler Proxy Traffic, etc.). Rules are evaluated in ascending numerical order.
- **Rule Status**: Select **Enabled**. Enabled rules are actively enforced.
- **Device Groups**: Select **Cloud Browser isolation**, **No Client Connector**, and the necessary device groups. To learn more, see [About Device Groups](/zia/about-device-groups).
- []
**Device Trust Level**: Select the device trust level values (**High Trust**, **Medium Trust**, **Low Trust**, or **Unknown**) to which the rule applies. While the High Trust, Medium Trust, or Low Trust evaluation is applicable only to Zscaler Client Connector traffic, Unknown evaluation applies to all traffic. Selecting no value ignores the criterion in the policy evaluation.
The trust levels assigned to the devices are based on your [posture configurations](/client-connector/adding-zia-posture-profiles) in the Zscaler Client Connector Portal.
- **Network Services**: Select the HTTP, HTTPS, and DNS network services. These services must be allowed through the firewall for the [DNS Control](/zia/about-dns-control) and [Web](/zia/about-public-service-edges) (secure web gateway) modules to evaluate the traffic.
- By default, the HTTP network service uses port 80, HTTPS uses 443, and DNS uses 53. You can also define custom network services with custom ports and configure them in the recommended firewall filtering rule. Additionally, to send the custom network services to the DNS Control and Web modules for evaluation, you must configure the services in the [Advanced Settings](/zia/configuring-advanced-settings) using the **Services Forwarded to HTTP Web Proxy** and **Services Applicable to DNS Transaction Policies** options. To learn more, see [Configuring Network Services](/zia/configuring-network-service).
- Zscaler recommends against changing the default ports for HTTP, HTTPS, and DNS network services. If you are using custom ports with network services, exercise caution when configuring those network services in the recommended firewall filtering rule.
- **Action**: Select **Allow**. This allows packets that match your criteria to pass through the firewall.
[See image.](#recommended-rule)
To learn more about the rule attributes, see [Configuring the Firewall Control Policy](/zia/configuring-firewall-filtering-policy).
[]![A screenshot of the default firewall filtering rule](/downloads/tech-pubs-drafts/zia-draft-articles/recommended-firewall-control-policy-doc-47250/default-firewall-filtering-rule.png)
[]![A screenshot of the firewall filtering rule recommended by Zscaler](/downloads/tech-pubs-drafts/zia-draft-articles/recommended-firewall-control-policy-doc-47250/recommended-firewall-filtering-rule.png)