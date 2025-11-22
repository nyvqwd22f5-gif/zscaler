# Modifying the Predefined DNS Control Rules
Source: https://help.zscaler.com/zia/modifying-predefined-dns-control-rules
PDF: https://help.zscaler.com/pdf/com/en/1399921.pdf

The DNS Control policy has predefined rules based on best practice recommendations to manage specific types of traffic. These rules can be used readily by an organization to protect its traffic against specific threats. Depending on the rule functionality and the severity of threats against which they offer protection, some rules are highly restrictive and do not support customization for rule conditions and actions, whereas others allow for greater flexibility including rule deletion. Similarly, certain rules contain system-defined Rule Order (i.e., default Rule Order), which cannot be modified by admins. These rules with default Rule Order always maintain the lowest precedence.
The following are the predefined DNS Control rules. To learn more about each predefined rule and its attributes, review the following sections:
- Predefined DNS rules can be enabled or disabled based on your organization’s requirements. However, these rules cannot be deleted unless specified otherwise.
- In the event of false positives triggered by predefined DNS rules, you can either create custom rules using higher ranks or disable the rule that's causing the false positives.
The following are the default DNS Control policy rules:
- [Unknown DNS Traffic](#unknown-dns)
- [Default Firewall DNS Rule](#firewall)
- [Fallback ZPA Resolver for Locations](#fallback-rule-locations)
- [Fallback ZPA Resolver for Road Warrior](#fallback-rule-road-warriors)
- [Critical Risk DNS Categories](#critical-risk-dns-categories)
- [Critical Risk DNS Tunnels](#critical-risk-dns-tunnels)
- [High-Risk DNS Categories](#high-risk-dns-categories)
- [High-Risk DNS Tunnels](#high-risk-dns-tunnels)
- [Risky DNS Categories](#risky-dns-categories)
- [Risky DNS Tunnels](#risky-dns-tunnels)
[]The Unknown DNS Traffic rule is preconfigured to take action on suspected malformed traffic, non-standard DNS traffic, or even non-DNS traffic attempting to conceal itself as DNS traffic (not otherwise identified as another application). Zscaler recommends blocking the traffic matching this rule.
To modify the Unknown DNS Traffic rule:
- Go to **Policy** > **DNS Control**.
- Click the **Edit** icon corresponding to the default rule. The **Edit DNS Filtering Rule** window appears.
- In the** Edit DNS Filtering Rule** window, you can do the following:
- Select a **Rule Label** for the rule.
-
Select an action for the **Network Traffic **field:
- **Allow**: Allows the DNS requests and responses.
- **Block**: Silently blocks all DNS requests and responses.
[See image.](#unknown-dns-traffic-image)
- Click **Save** and [activate the change.](/zia/saving-and-activating-changes-admin-portal)
[]The Default Firewall DNS Rule is preconfigured to manage all the DNS traffic that is not specifically defined and actioned in the higher-ranked, user-defined rules. Zscaler recommends blocking the traffic matching the rule, but only if the permitted DNS traffic is defined in a higher-ranked rule.
If a higher-ranked allow rule is not defined, then many applications fail as DNS is essential for their operation.
To modify the Default Firewall DNS rule:
- Go to **Policy** > **DNS Control**.
- Click the **Edit** icon corresponding to the default rule. The **Edit DNS Filtering Rule** window appears.
-
In the** Edit DNS Filtering Rule** window, you can do the following:
- Select a **Rule Label** for the rule.
- Select an action for the **Network Traffic **field:
- **Allow**: Allows the DNS requests and responses.
- **Block**: Silently blocks all DNS requests and responses.
[See image.](#default-filtering-dns-traffic-image)
- Click **Save** and [activate the change.](/zia/saving-and-activating-changes-admin-portal)
[]The Fallback ZPA Resolver for Locations rule is predefined to redirect source IP anchored traffic from location users to the preconfigured IP pools during control plane maintenance. You can edit the IP address range configured for the IP pools under **Administration** > **IP & FQDN Groups** > **IP Pool page**. This rule is disabled by default and cannot be deleted. It is only enabled during control plane maintenance to ensure the resiliency of the Source IP Anchoring feature. You can only modify the rule label for this rule.
To modify the Fallback ZPA Resolver for Locations rule:
- Go to **Policy** > **DNS Control**.
- Click the **Edit **icon corresponding to the default rule. The **Edit DNS Filtering Rule** window appears.
-
In the **Edit DNS Filtering Rule** window, choose the **Rule Label** for the rule.
[See image.](#fallback-zpa-resolver-locations-image)
- Click Save and [activate the change.](/zia/saving-and-activating-changes-admin-portal)
[]The Fallback ZPA Resolver for Road Warrior rule is predefined to redirect source IP anchored traffic of remote users to the preconfigured IP pools during control plane maintenance. You can edit the IP address range configured for the IP pools under** Administration** > **IP & FQDN Groups** > **IP Pool** page.** **This rule is disabled by default and cannot be deleted. It is only enabled during control plane maintenance to ensure the resiliency of the Source IP Anchoring feature. You can only modify the rule label for this rule.
To modify the Fallback ZPA Resolver for Road Warrior rule:
- Go to **Policy** > **DNS Control**.
- Click the **Edit **icon corresponding to the default rule. The **Edit DNS Filtering Rule** window appears.
-
In the **Edit DNS Filtering Rule** window, choose the **Rule Label** for the rule.
[See image.](#fallback-zpa-resolver-road-warriors-image)
- Click Save and [activate the change.](/zia/saving-and-activating-changes-admin-portal)
[]The predefined rule, Critical Risk DNS Categories, blocks DNS traffic with the highest security risks in DNS request and response categories that are encountered by every organization. This block rule is implemented by all organizations, unless they are exceptional and very permissive circumstances. It blocks traffic that matches known or suspected critical security threats in DNS requests and responses, such as malicious IP addresses and FQDNs, Domain Generation Algorithm (DGA) domains, and other advanced security threats. This rule is enabled by default and is created with a higher rule order.
The Critical Risk DNS Categories rule contains predefined values for specific rule attributes, conditions, and action. While the rule attributes, such as Rule Order and Rule Label, are modifiable by admins to suit their organization’s requirements, the rule conditions and action, are read-only fields and can only use default values.
To modify the Critical Risk DNS Categories rule:
- Go to **Policy** > **DNS Control**.
- Click the **Edit** icon corresponding to the predefined rule. The **Edit DNS Filtering Rule** window appears.
-
In the **Edit DNS Filtering Rule** window, you can do the following:
- Configure the rule attributes listed as follows:
- Modify the **Rule Order** as per your requirements. If [Admin Rank](/zia/about-admin-rank) is enabled, your assigned admin rank determines the Rule Order values you can select.
- Modify the **Rule Status** to enable or disable the rule.
- Configure the **Rule Label**.
-
View the rule criteria (read-only) information in the following bulleted list:
The rule is configured only with specific criteria in the **DNS Application** category.
- **Request Categories**: Botnet Callback, Domain Generation Algorithm (DGA) Domains, Malicious Content, Phishing, and Spyware/Adware are selected.
- **Response Categories**: Botnet Callback, Domain Generation Algorithm (DGA) Domains, Malicious Content, Phishing, and Spyware/Adware are selected.
- View the rule action details and configure the Traffic Capture option as follows:
- **Action**: (Non-modifiable) Action is set to **Block**.
- **Logging**: (Non-modifiable) **Full Logging** is configured.
- **Capture**: (Modifiable) If [Traffic Capture is enabled](/zia/configuring-traffic-capture), the Capture option appears. By enabling this option, you can capture blocked traffic and store it in PCAP files for later analysis. To learn more, see [About Traffic Capture Settings](/zia/about-traffic-capture).
[See image.](#critical-risk-dns-categories-rule-edit-window)
- Click **Save** and [activate the change](/zia/saving-and-activating-changes-admin-portal).
[]The predefined rule, Critical Risk DNS Tunnels, blocks DNS tunnels with the highest security risks (e.g., commonly blocked DNS tunnels) that are encountered by every organization. This block rule is implemented by all organizations, unless they are exceptional and very permissive circumstances. This rule is enabled by default and is created with a higher rule order.
The Critical Risk DNS Tunnels rule contains predefined values for specific rule attributes, conditions, and action. While the rule attributes, such as Rule Order and Rule Label, are modifiable by admins to suit their organization’s requirements, the rule conditions and action, are read-only fields and can only use default values.
To modify the Critical Risk DNS Tunnels rule:
- Go to **Policy** > **DNS Control**.
- Click the **Edit** icon corresponding to the predefined rule. The **Edit DNS Filtering Rule** window appears.
-
In the **Edit DNS Filtering Rule** window, you can do the following:
- Configure the rule attributes listed as follows:
- Change the **Rule Order** as per your requirements. If [Admin Rank](/zia/about-admin-rank) is enabled, your assigned admin rank determines the Rule Order values you can select.
- Change the **Rule Status** to enable or disable the rule.
- Configure the **Rule Label**.
-
View the rule criteria information (read-only) in the following bulleted list:
The rule is configured only with specific criteria in the **DNS Application** category.
- **DNS Tunnels & Network Apps**: All DNS tunnels that are classified under the **Commonly Blocked DNS Tunnels** category by Zscaler are selected.
- View the rule action details and configure the Traffic Capture option as follows:
- **Action**: (Non-modifiable) Action is set to **Block**.
- **Logging**: (Non-modifiable) **Full Logging** is configured.
- **Capture**: (Modifiable) If [Traffic Capture is enabled](/zia/configuring-traffic-capture), the Capture option appears. By enabling this option, you can capture blocked traffic and store it in PCAP files for later analysis. To learn more, see [About Traffic Capture Settings](/zia/about-traffic-capture).
[See image.](#critical-risk-dns-tunnels-rule-edit-window)
- Click **Save** and [activate the change](/zia/saving-and-activating-changes-admin-portal).
[]The predefined rule, High-Risk DNS Categories, blocks DNS traffic with high security risks to an organization’s network. It blocks DNS traffic that matches newly registered and observed domains, newly revived domains, and other similar security threats in DNS requests and responses. This rule warrants careful consideration by an organization and it is strongly recommended by Zscaler to implement this block rule. This rule is enabled by default and is created with a higher rule order.
The High-Risk DNS Categories rule contains predefined values for specific rule attributes, conditions, and action. While the rule attributes, such as Rule Order and Rule Label, are modifiable by admins to suit their organization’s requirements, the rule conditions and action, are read-only fields and can only use default values.
To modify the High-Risk DNS Categories rule:
- Go to **Policy** > **DNS Control**.
- Click the **Edit** icon corresponding to the predefined rule. The **Edit DNS Filtering Rule** window appears.
-
In the **Edit DNS Filtering Rule** window, you can do the following:
- Configure the rule attributes listed as follows:
- Change the **Rule Order** as per your requirements. If [Admin Rank](/zia/about-admin-rank) is enabled, your assigned admin rank determines the Rule Order values you can select.
- Change the **Rule Status** to enable or disable the rule.
- Configure the **Rule Label**.
-
View the rule criteria information (read-only) in the following bulleted list.
The rule is configured only with specific criteria in the DNS Application category.
- **Request Categories**: Newly Registered and Observed Domains, Newly Revived Domains, and Other Security are selected.
- **Response Categories**: Newly Registered and Observed Domains, Newly Revived Domains, and Other Security are selected.
- View the rule action details and configure the Traffic Capture option as follows:
- **Action**: (Non-modifiable) Action is set to **Block**.
- **Logging**: (Non-modifiable) **Full Logging** is configured.
- **Capture**: (Modifiable) If [Traffic Capture is enabled](/zia/configuring-traffic-capture), the Capture option appears. By enabling this option, you can capture blocked traffic and store it in PCAP files for later analysis. To learn more, see [About Traffic Capture Settings](/zia/about-traffic-capture).
[See image.](#high-risk-dns-categories-rule-edit-window)
- Click **Save** and [activate the change](/zia/saving-and-activating-changes-admin-portal).
[]The predefined rule, High-Risk DNS Tunnels, blocks DNS tunnels with high security risks (e.g., unknown DNS tunnels) to an organization’s network. This rule warrants careful consideration by an organization and it is strongly recommended by Zscaler to implement this block rule. This rule is enabled by default and is created with a higher rule order.
The High-Risk DNS Tunnels rule contains predefined values for specific rule attributes, conditions, and action. While the rule attributes, such as Rule Order and Rule Label, are modifiable by admins to suit their organization’s requirements, the rule conditions and action, are read-only fields and can only use default values.
To modify the High-Risk DNS Tunnels rule:
- Go to **Policy** > **DNS Control**.
- Click the **Edit** icon corresponding to the predefined rule. The **Edit DNS Filtering Rule** window appears.
-
In the **Edit DNS Filtering Rule** window, you can do the following:
- Configure the rule attributes listed as follows:
- Change the **Rule Order** as per your requirements. If [Admin Rank](/zia/about-admin-rank) is enabled, your assigned admin rank determines the Rule Order values you can select.
- Change the **Rule Status** to enable or disable the rule.
- Configure the **Rule Label**.
-
View the rule criteria information (read-only) in the following bulleted list.
The rule is configured only with specific criteria in the DNS Application category.
- **DNS Tunnels & Network Apps**: All DNS tunnels that are classified under the **Unknown DNS Tunnels** category by Zscaler are selected.
- View the rule action details and configure the Traffic Capture option as follows:
- **Action**: (Non-modifiable) Action is set to **Block**.
- **Logging**: (Non-modifiable) **Full Logging** is configured.
- **Capture**: (Modifiable) If [Traffic Capture is enabled](/zia/configuring-traffic-capture), the Capture option appears. By enabling this option, you can capture blocked traffic and store it in PCAP files for later analysis. To learn more, see [About Traffic Capture Settings](/zia/about-traffic-capture).
[See image.](#high-risk-dns-tunnels-rule-edit-window)
- Click **Save** and [activate the change](/zia/saving-and-activating-changes-admin-portal).
[]The predefined rule, Risky DNS Categories, is a recommended rule to block common DNS security threats to an organization’s network. It blocks traffic that matches risky categories in DNS requests and responses, including content representing abuse or exploitative behavior, adult material, militancy/hate and extremism, violence, malicious content, etc. Blocking these categories is recommended but the rule implementation might vary depending on your organization’s requirements and corporate policies.
The Risky DNS Categories rule is not enabled by default. Admins of sufficient rank can enable, fully customize, or delete this rule.
To modify the Risky DNS Categories rule:
- Go to **Policy** > **DNS Control**.
- Click the **Edit** icon corresponding to the predefined rule. The **Edit DNS Filtering Rule** window appears.
-
In the **Edit DNS Filtering Rule** window, you can customize all attributes of the rule, rule conditions, and action. To learn how to configure DNS Control rules, see [Configuring the DNS Control Policy](/zia/configuring-dns-control-policy).
The rule cannot have different sets of URL categories selected under **Request Categories** and **Response Categories**. However, you can have only one of the two conditions configured for the rule by clearing the selection for the other condition.
[See image.](#risky-dns-categories-rule-edit-window)
- Click **Save** and [activate the change](/zia/saving-and-activating-changes-admin-portal).
If you want to delete the rule, use the **Delete** button in the **Edit DNS Filtering Rule** window.
[]The predefined rule, Risky DNS Tunnels, is a recommended rule to block DNS tunnels that are common security threats to an organization's network. Blocking these tunnels is recommended but the rule implementation might vary depending on your organization’s requirements and corporate policies.
The Risky DNS Tunnels rule is not enabled by default. Admins of sufficient rank can enable, fully customize, or delete this rule.
To modify the Risky DNS Tunnels rule:
- Go to **Policy** > **DNS Control**.
- Click the **Edit** icon corresponding to the predefined rule. The **Edit DNS Filtering Rule** window appears.
-
In the **Edit DNS Filtering Rule** window, you can customize all attributes of the rule, rule conditions, and action. To learn how to configure DNS Control rules, see [Configuring the DNS Control Policy](/zia/configuring-dns-control-policy).
[See image.](#risky-dns-tunnels-rule-edit-window)
- Click **Save** and [activate the change](/zia/saving-and-activating-changes-admin-portal).
If you want to delete the rule, use the **Delete** button in the **Edit DNS Filtering Rule** window.
![Screenshot of Edit DNS Filtering Rule section with fields for the Unknown Traffic default rule](/downloads/zia/documentation-knowledgebase/creating-and-managing-policies/firewall/firewall-policies/how-do-i-modify-default-dns-control-rule/ZIA-Edit-DNS-Filtering-Rule-Window.png)
[]
![Screenshot of Edit DNS Filtering Rule section with fields for the Fallback ZPA Resolver for Locations rule](/downloads/zia/policies/firewall/dns-control/zia-modifying-default-dns-rules-edit-fallback-location-user.png)
[]
![Screenshot of Edit DNS Filtering Rule section with fields for the Fallback ZPA Resolver for Road Warriors rule](/downloads/zia/policies/firewall/dns-control/zia-modifying-default-dns-rules-edit-fallback-road-warrior.png)
[]
![Screenshot of Edit DNS Filtering Rule section with fields for the Default Filtering DNS Rule](/downloads/zia/policies/firewall/dns-control/zia-modifying-default-dns-rules-edit-default-firewall-dns-rule.png)
[]
[]![Critical Risk DNS Categories rule edit window](/downloads/zia/policies/firewall/dns-control/modifying-default-dns-control-rule/critical-risk-dns-categories-rule.png)
[]![Critical Risk DNS Tunnels rule edit window](/downloads/zia/policies/firewall/dns-control/modifying-default-dns-control-rule/critical-risk-dns-tunnels-rule.png)
[]![High-Risk DNS Categories rule edit window](/downloads/zia/policies/firewall/dns-control/modifying-default-dns-control-rule/high-risk-dns-categories-rule.png)
[]![High-Risk DNS Tunnels rule edit window](/downloads/zia/policies/firewall/dns-control/modifying-default-dns-control-rule/high-risk-dns-tunnels-rule.png)
[]![Risky DNS Categories rule edit window](/downloads/zia/policies/firewall/dns-control/modifying-default-dns-control-rule/risky-dns-categories-rule_0.png)
[]![Risky DNS Tunnels rule edit window](/downloads/zia/policies/firewall/dns-control/modifying-default-dns-control-rule/risky-dns-tunnels-rule_1.png)