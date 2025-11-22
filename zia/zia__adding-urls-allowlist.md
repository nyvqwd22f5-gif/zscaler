# Adding URLs to the Allowlist
Source: https://help.zscaler.com/zia/adding-urls-allowlist
PDF: https://help.zscaler.com/pdf/com/en/1399311.pdf

There might be trusted websites of partners or vendors whose webmail or file downloads might otherwise be blocked due to anti-virus, anti-spyware, anti-malware, or URL filtering policies. You can exempt URLs from security scans, URL filtering, or both.
The allowlist applies to [Malware Protection](/zia/about-malware-protection), [Advanced Threat Protection](/zia/about-advanced-threat-protection), [Sandbox](/zia/about-sandbox), and [URL Filtering](/zia/about-url-filtering) policies. To learn more about how security exceptions impact policy enforcement, see [About Policy Enforcement](/zia/how-does-zscaler-service-enforce-policies).
You can allowlist URLs completely by exempting them from [security scans](#allowlist-security) and [URL filtering](#allowlist-urlfiltering).
[]Adding URLs to Allowlist for Security Scans
Adding URLs to the allowlist for security scans allows users to download content from these URLs without inspecting the traffic.
To add URLs to allowlist for security policies:
- Go to one of the following pages:
- **Policy **> **Malware Protection**
- **Policy **>** Advanced Threat Protection**
- Click the **Security Exceptions** tab.
- In **Do Not Scan Content from these URLs**, enter the URLs you want to allowlist and click **Add Items**. You can enter multiple entries by hitting **Enter** after each entry. You can add up to 1,024 URLs. To learn more, see [Ranges & Limitations](/zia/ranges-limitations). For guidance on entering URLs, see the [URL format guidelines](/zia/url-format-guidelines). For item lists, you can view up to 500 items on a page; filter the list by searching for a word, phrase, or number contained in an item; and remove all items from the list (**Remove All**) or only items from a specific page (**Remove Page**). If you select **Remove All** or **Remove Page**, a confirmation window will appear.
This allowlist also applies to the [Sandbox](/zia/about-sandbox) policy.
- Click **Save** and [activate the change](/zia/saving-and-activating-changes-admin-portal).
[]Adding URLs to Allowlist for URL Filtering
Adding URLs to the allowlist for URL filtering allows access to the content without being blocked by other URL Filtering policy rules.
To add URLs to allowlist for URL Filtering policy:
- Add the URLs you want to allowlist to a [custom URL category](/zia/adding-custom-url-categories).
- [Configure a URL Filtering rule](/zia/configuring-url-filtering-policy) to allow the custom URL category.
Ensure that the rule order of this rule is higher than the URL Filtering rule that blocks these URLs.