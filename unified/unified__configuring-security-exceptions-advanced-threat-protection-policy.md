# Configuring Security Exceptions for the Advanced Threat Protection Policy
Source: https://help.zscaler.com/unified/configuring-security-exceptions-advanced-threat-protection-policy
PDF: https://help.zscaler.com/pdf/com/en/1494251.pdf

[]To configure security exceptions for the Advanced Threat Protection policy:
- Go to **Policies** >** Cybersecurity **>** Inline Security **>** Advanced Threat Protection**.
- Click the **Security Exceptions** tab.
-
In **Do Not Scan Content from these URLs**, enter URLs you want to allowlist for ATP, or URLs you don't want to inspect for ATP, and click **Add Items**. You can enter multiple entries by hitting **Enter** after each entry. You can add up to 1,024 URLs. To learn more, see [Ranges & Limitations](/unified/ranges-limitations#internet-saas). For guidance on entering URLs, see the [URL format guidelines](/unified/url-format-guidelines). For item lists, you can view up to 500 items on a page; filter the list by searching for a word, phrase, or number contained in an item; and remove the first 25K items from the list (**Remove 25K Items**) or only items from a specific page (**Remove Page**). If you select **Remove 25K Items **or **Remove Page**, a confirmation window will appear.
This allowlist also applies to the [Malware Protection](/unified/configuring-malware-protection-policy) and [Sandbox](/unified/about-sandbox) policies. If you want to allowlist URLs and files completely, you must also configure the [URL Filtering](/unified/about-url-filtering), [File Type Control](/unified/about-file-type-control), and [IPS Control](/unified/about-ips-control) policies. To learn more, see [Adding URLs to the Allowlist](/unified/adding-urls-allowlist).
[See image.](#seeimage)
- Click **Add Items**.
- Click **Save** and activate the change.
[]![Screenshot of the Do Not Scan Content from these URLs field in the Security Exceptions tab for Advanced Threat Protection.](/downloads/zia/policies/advanced-threat-protection/configuring-security-exceptions-advanced-threat-protection-policy/ZIA-Advanced-Threat-Protection-Security-Exceptions.png)