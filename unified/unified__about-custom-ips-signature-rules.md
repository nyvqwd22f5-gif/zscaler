# About Custom IPS Signature Rules
Source: https://help.zscaler.com/unified/about-custom-ips-signature-rules
PDF: https://help.zscaler.com/pdf/com/en/1494316.pdf

Zscaler's Intrusion Prevention System (IPS) uses signature-based detection to monitor your network for malicious activities and prevent attacks. Signature-based detection compares your traffic with predefined signatures (like fingerprints) of known network attack patterns and performs the specified action when there is a pattern match. Signatures uniquely identify the characteristics of specific types of network activities that indicate an intrusion or a threat of intrusion. The Zscaler service evaluates your network traffic against the signatures through the [IPS Control](/unified/about-ips-control) policy. When a threat is detected based on a signature pattern match, the IPS enforces a preconfigured policy action to allow or block the traffic.
The Zscaler service uses signatures built and updated by ThreatLabZ (Zscaler's security research team), as well as signatures from industry-leading vendors. In addition to the signatures managed by Zscaler, you can create and deploy custom IPS signatures that are specific to your organization's requirements. Custom IPS signatures can be created in the Admin Portal using the [Snort](https://www.snort.org/) syntax, which supports a lightweight rules description language.
The custom IPS signatures developed for an organization are encrypted and stored in the Zscaler Central Authority (CA). You can then define IPS Control rules using your custom signatures to detect and prevent network intrusion. Internet & SaaS Service Edge downloads your policies and custom signatures as part of your organization configurations from the CA and enforces matching policies inline on your user traffic.
Custom IPS signatures provide the following benefits and enable you to:
- Define custom IPS signatures in the Admin Portal using the well-known Snort syntax and define them in IPS Control policies to monitor your network traffic for malicious activities and identify specific threats.
- Enforce condition-based actions on your network traffic through IPS Control policies. You can configure policies to allow or block traffic and also allow specific types of traffic to bypass Zscaler's IPS.
- Control and maintain your custom IPS signatures as private configurations that are accessible only to your organization.
- Leverage Zscaler Firewall logs to analyze and investigate threats detected in your network. These logs can also serve for auditing purposes and help you ensure compliance with regulatory requirements. Optionally, you can export firewall logs to on-premises or cloud security information and event management (SIEM), extended detection and response (XDR), or similar event collection tools and threat intelligence platforms.
[Firewall Insights](/unified/about-insights) provides visibility into the logs recorded for IPS traffic that matches with your custom IPS signatures. You can also track this data using interactive charts in the [IPS Overview Dashboard](/unified/about-dashboards#ips). Using [Nanolog Streaming Service (NSS)](/unified/understanding-nanolog-streaming-service), you can stream your logs in real time from the Zscaler Nanolog to your security information and event management (SIEM) system.
- To enable Custom IPS Signature Rules for your organization, contact your Zscaler Account team. Only traffic that transits [Internet & SaaS Private Service Edge](/unified/understanding-internet-saas-private-service-edge) or [Internet & SaaS Virtual Service Edge](/unified/about-internet-saas-virtual-service-edges) can be inspected against custom IPS signature rules. To leverage custom IPS signature rules, your organization must have one of these Internet & SaaS Service Edge deployments.
- IPS Control based on custom IPS signatures protects only non-web traffic.
- You can define a maximum of 500 custom IPS signature rules. Before creating custom IPS signatures, we strongly recommend that you read the [Specifications and Limitations for Custom IPS Signature Rules](/unified/specifications-and-limitations-custom-ips-signature-rules) to understand the Snort syntax and features supported by Zscaler.
About the Custom Signature Rules Page
On the Custom Signature Rules page (Policies > Cybersecurity > Inline Security > Custom IPS Signatures), you can do the following:
- [Add a custom signature rule](/unified/adding-custom-ips-signature-rules).
- View the list of all custom signature rules. By default, the table displays the following information:
- **Name**: The name of the custom signature rule.
- **Description**: The description of the custom signature rule.
- **Signature Rule**: The custom signature rule in the Snort rule syntax.
- **Threat Category**: The threat category that is assigned to the custom signature rule. The custom signature rule can be used in an IPS Control rule via the assigned threat category.
- **Status**: Status indicates whether the custom signature rule is enabled or disabled.
- Edit a custom signature rule. This action also allows you to delete a custom signature rule.
- [Modify the table and its columns](/unified/using-tables).
- Search for a custom signature rule.
- [Filter the list of custom signature rules.](#apply-filters)
- Download a Sample Import CSV file, which can be used to import custom signature rules.
- [Export your custom signature rules to a CSV file](/unified/importing-and-exporting-custom-ips-signature-rules).
- [Import new custom signature rules or modify existing custom signature rules using a CSV file](/unified/importing-and-exporting-custom-ips-signature-rules).
- Go to the [Threat Categories](/unified/about-threat-categories) page to add and manage custom threat categories.
![Custom Signature Rules page in the ZIA Admin Portal](/downloads/zia/policies/firewall/ips-control/about-custom-ips-signature-rules/custom-ips-signature-rules-page.png)
- []Click the **Apply Filter** icon.
- Click **Add Filter** and select an attribute from the drop-down menu. Alternatively, you can search for an attribute and select it.
- Click the drop-down menu and select a value for the attribute selected in the previous step. Alternatively, you can search for an attribute value and select it. When you select the attribute value, the list automatically updates to display relevant items.
- You can add multiple attributes as filters to narrow down the list further.
- Click the **Remove **icon to remove a filter.
- After adding the necessary filters, click **Done**.