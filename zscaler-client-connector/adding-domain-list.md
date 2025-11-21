# Adding a Domain List
Source: https://help.zscaler.com/zscaler-client-connector/adding-domain-list
PDF: https://help.zscaler.com/pdf/com/en/1532879.pdf

You can add a list of domains to use when adding a ruleset for traffic steering to use with location-based policies. To learn more, see [About Location-Based Policies](/zscaler-client-connector/about-location-based-policies).
This feature is available only for Zscaler Client Connector version 4.8 and later for Windows. Contact Zscaler Support to enable this feature.
To add a domain list:
- Go to **Administration** > **Location-Based Policies**.
-
Select the **Domain Lists** tab and click **Add Domain List**.
[See image.](#domain-list-tab)
The **Add Domain List** window appears.
[See image.](#add-domain-list-window)
- In the **Add Domain List** window:
- **Name**: Enter a unique alphanumeric name for your list.
-
**Domains**: Enter the domains to use in a ruleset. You can click **Download CSV** to download a comma-separated value file with the entries in the list, and you can click **Upload CSV** to upload a comma-separated value file that replaces the existing entries.
You can enter specific domains (e.g., `google.com`) or enter a wildcard (e.g., `*` or `*.[internaldomain].com`) to include or exclude all or specific DNS domains. For specific domains, up to two levels of subdomains are automatically included or excluded (e.g., if you enter `safemarch.com`, Zscaler Client Connector includes `downloads.safemarch.com` but not `web.downloads.safemarch.com`). Press `Enter` after each entry. You can add multiple items at the same time by separating each item with a comma and then pressing `Enter` when finished. The maximum number of characters is 65,535 in each field.
- **List Description**: Enter any notes regarding the list.
- Click **Save**.
You can enter a maximum of 300 domain lists. After you create a list, you can select it in Domain Inclusion and Domain Exclusion when [adding a ruleset](/zscaler-client-connector/adding-ruleset). You must use the list in a ruleset, and you cannot use it directly in an app profile.
[]![Domain Lists tab](/downloads/zscaler-client-connector/location-based-policies/adding-traffic-steering-ip-list/zclient-connector-domain-lists-tab.png)
[]
![Add Domain List window](/downloads/zscaler-client-connector/location-based-policies/adding-traffic-steering-ip-list/zclient-connector-add-domain-list.png)