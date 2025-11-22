# About CIPA Compliance
Source: https://help.zscaler.com/unified/about-cipa-compliance
PDF: https://help.zscaler.com/pdf/com/en/1493986.pdf

The Children's Internet Protection Act (CIPA) is aimed to prevent children from accessing obscene or harmful content over the internet. To learn more, see [Children's Internet Protection Act (CIPA)](https://www.fcc.gov/sites/default/files/childrens_internet_protection_act_cipa.pdf). Schools or libraries are required to be CIPA compliant to receive discounts on internet access or internal connections through the E-rate program.
To aid schools and organizations to be compliant with the CIPA requirements, Zscaler provides a predefined URL filtering rule ([CIPA Compliance Rule](/unified/about-cipa-compliance#view-CIPA-comp-rule)) and a control ([Enable CIPA Compliance](/unified/about-cipa-compliance#Enable-CIPA-Compliance)) to enable the predefined rule. It also provides a [CIPA Compliance Report](/unified/cipa-compliance-report) which gives insights into the traffic and users that are blocked from accessing the prohibited content based on the CIPA Compliance Rule.
- [Enabling CIPA Compliance](#Enable-CIPA-Compliance)
- [Viewing CIPA Compliance Rule](#view-CIPA-comp-rule)
[]To activate the **CIPA Compliance Rule**, enable the **Enable CIPA Compliance** option from the **Advanced Policy Settings** tab (**Policies **> **Access Control** > **Internet & SaaS** > **Advanced Settings**). To learn more, see [Configuring Advanced URL Policy Settings](/unified/configuring-advanced-url-policy-settings).
- [Effects of Enabling CIPA Compliance](#Effects-Enable-CIPA)
- [Effects of Disabling CIPA Compliance](#Effect-Disable-CIPA)
You cannot enable the **Enable CIPA Compliance** option when:
- The number of URL filtering policy rules exceeds the [limit](/unified/ranges-limitations).
- A rule with rule order 1 exists with a higher admin rank.
[]When you enable CIPA Compliance:
- The **CIPA Compliance Rule** gets activated under the **URL Filtering Policy** tab (**Policies **> **Access Control** > **Internet & SaaS** > **URL Filtering**).
-
The following **Advanced URL Filtering** **Options** under the **Advanced Policy Settings **tab (**Policies **> **Access Control** > **Internet & SaaS** > **Advanced Settings**) get enabled. You cannot disable the following options:
- Enable Suspicious New Domains Lookup
- Enable AI/ML based Content Categorization
- Enable Embedded Sites Categorization
- Enforce SafeSearch
To learn more, see [Configuring Advanced URL Policy Settings](/unified/configuring-advanced-url-policy-settings).
-
The **CIPA Compliance Report** option gets enabled in the following places:
- **Analytics **> **Internet & SaaS** > **Analytics** > **Interactive Reports **> **Standard Reports** > **Liability Exposure** drop-down.
- **Analytics **> **Internet & SaaS** > **Analytics** > **Interactive Reports **> **Scheduled Reports** > **Add Scheduled Report** > **Report** drop-down.
[See image.](#reportimg)
To learn more, see [CIPA Compliance Report](/unified/cipa-compliance-report).
[]When you disable CIPA Compliance:
- The following warning message appears:
**If CIPA Compliance is disabled, then CIPA Compliance Rule will be disabled**.
- The **CIPA Compliance Rule** gets disabled under the **URL Filtering Policy** tab (**Policies **> **Access Control** > **Internet & SaaS** > **URL Filtering**). However, you can see the disabled rule.
- The **Advanced URL Filtering** **Options** under the **Advanced Policy Settings **tab (**Policies **> **Access Control** > **Internet & SaaS** > **Advanced Settings**) is set to the recommended policy settings. To learn more, see [Recommended URL & Cloud App Control Policy](/unified/recommended-url-cloud-app-control-policy).
[]You can see the **CIPA Compliance Rule** under the **URL Filtering Policy** tab (**Policies **> **Access Control** > **Internet & SaaS** > **URL Filtering**) if you select **Enable CIPA Compliance** option at least once. To learn more, see [Enabling CIPA Compliance](#Enable-CIPA-Compliance).
You can delete the CIPA Compliance Rule** **only** **when you disable the Enable CIPA Compliance** **option.
The attributes defined for the rule are as follows:
| Attributes | Value | Description |
| ---------- | ----- | ----------- |
| Rule Order | 1 | (Editable) Order of precedence of the rule.When the CIPA Compliance Rule is activated for the first time, it takes the highest precedence (rule order 1) by default. The rule order is automatically incremented by 1 for the other rules.You can edit the rule order based on your preference. |
| Admin Rank | 0 to 7 | (Editable) Admin rank of the logged-in user.If the logged-in user does not have an admin rank, then the rule is created with an admin rank 7. |
| Rule Name | CIPA Compliance Rule | (Non-editable) Name of the rule.You cannot create any custom URL filtering rule with the name CIPA Compliance Rule. |
| Rule Status | Disabled/Enabled | (Non-editable) Status of the rule. |
| URL Categories | Adult Sex Education, Adult Themes, Alcohol/Tobacco, Anonymizer, Computer Hacking, Copyright Infringement, Drugs, Gambling, K-12 Sex Education, Lingerie/Bikini, Mature Humor, Militancy/Hate and Extremism, Newly Registered and Observed Domains, Nudity, Other Adult Material, Other Illegal or Questionable, Pornography, Profanity, Questionable, Body Art, Social Networking Adult, Tasteless, Violence, Weapons/Bombs | (Non-editable) List of all the predefined categories under the URL super category, **Legal Liabilities** with predefined URLs and keywords.The custom categories under **Legal Liabilities **are excluded.You cannot add or delete URL categories from the predefined list.However, you can add or delete custom URLs and keywords (CIPA related) from any predefined category under **Legal Liabilities**. |
| HTTP Requests | OPTIONS, GET, HEAD, POST, PUT, DELETE, TRACE, CONNECT, OTHER, ALL | (Non-editable) List of predefined HTTP requests. |
| Users | --- | (Non-editable) Applicable to all the users in the organization. |
| Groups | --- | (Non-editable) Applicable to all the groups in the organization. |
| Departments | --- | (Non-editable) Applicable to all the departments in the organization. |
| Locations | --- | (Non-editable) Applicable to all the locations of the organization. |
| Location Groups | --- | (Non-editable) Applicable to all the location groups of the organization. |
| Time | --- | (Non-editable) Applicable at any time. |
| Protocols | Any | (Non-editable) Applicable to all protocols. |
| Web Traffic | Block | (Non-editable) Access is denied to all the sites that fall under the specified URL categories. |
| Allow Override | Disabled | (Non-editable) No exception is allowed for the blocked sites. |
| Redirect URL | --- | (Non-editable) No redirect URL is configured. |
| Description | --- | (Editable) Additional notes or information about the rule. |
[]![Screenshot of the CIPA Compliance Report in the ZIA Admin Portal](/downloads/zia/documentation-knowledgebase/policies/url-filtering/about-cipa-compliance/ZIA-5.7-CIPA-Compliance-Report.png)