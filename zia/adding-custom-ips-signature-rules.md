# Adding Custom IPS Signature Rules
Source: https://help.zscaler.com/zia/adding-custom-ips-signature-rules
PDF: https://help.zscaler.com/pdf/com/en/1403191.pdf

The Zscaler service supports [Snort rules](https://www.snort.org/) to create [custom IPS signature rules](/zia/about-custom-signature-rules). Each custom signature rule is assigned a [threat category](/zia/about-threat-categories). A custom signature rule can be used in an [IPS Control](/zia/about-ips-control) rule via the assigned threat category.
To enable Custom IPS Signature Rules for your organization, contact your Zscaler Account team. Only traffic that transits [ZIA Private Service Edge](/zia/about-service-edge) or [ZIA Virtual Service Edge](/zia/about-virtual-service-edges) can be inspected against custom IPS signature rules. To leverage custom IPS signature rules, your organization must have one of these ZIA Service Edge deployments.
Writing Snort rules requires specialized technical expertise. Misconfiguration may lead to unexpected behavior. Before creating custom signatures, we strongly recommend that you read the [Specifications and Limitations for Custom IPS Signature Rules](/zia/specifications-limitations-custom-signature-rules) to understand the Snort syntax and features supported by Zscaler.
To add a custom signature rule:
- Go to **Administration **>** Custom IPS**.
- Click the **Custom Signature Rules **tab.
-
Click** Add Signature Rule**.
The** Add Signature Rule** window appears.
- In the **Add Signature Rule** window:
- **Name**: Enter a unique name for the custom signature rule. The name can contain any characters, including spaces. It cannot exceed 255 characters.
- **Threat Category**: Select a threat category that must be assigned to the custom signature rule. The custom signature rule can be used in an IPS Control rule via the assigned threat category.
- **Description**: (Optional) Provide a description for your custom signature rule. The description cannot exceed 255 characters.
- **Signature Rule**: Enter the Snort rule that you have configured. The Snort rule cannot exceed 16,000 characters.
- Click **Validate Rule** to verify that the custom signature rule is valid. This step is optional but recommended.
- Use the toggle button to enable the custom signature rule. Only enabled custom signature rules can be used in IPS Control rules.
- Click **Save **and [activate the change](/zia/saving-and-activating-changes-admin-portal).
[See image.](#signature-rule)
You can add a maximum of 500 custom signature rules. For a complete list of ranges and limits per feature, see [Ranges & Limitations](/zia/ranges-limitations).
[]![Adding custom signature rule](/downloads/zia/documentation-knowledgebase/policies/firewall/firewall-policy-resources/adding-custom-signature-rules/adding-signature-rule.png)