# Configuring Destination IP Groups for Internet & SaaS
Source: https://help.zscaler.com/unified/configuring-destination-ip-groups-internet-saas
PDF: https://help.zscaler.com/pdf/com/en/1494196.pdf

You can create custom destination groups by specifying IP addresses (IPv4 only), FQDNs, wildcard FQDNs, countries where servers are located, or [custom URL categories](/unified/about-url-categories).
Custom groups based on IPv6 addresses are not currently supported.
To create a custom destination group for IPv4 addresses:
- Go to **Policies** >** Access Control **>** Firewall **>** IP & FQDN Groups **> **Destination IPv4 Groups**.
- On the **Destination IPv4 Groups** tab, click **Add Destination IPv4 Group**, and fill out the following fields:
- **Name**:** **Enter a name for the destination address group. Only alphanumeric characters, underscores, hyphens, and periods are allowed.
- **Type**:
- **IP Address**: You can add IPv4 addresses in any of the following formats:
- An individual address (e.g., 192.0.2.1)
- A subnet (e.g., 192.0.2.0/240
- An address range (e.g., 192.0.2.1 – 192.0.2.5)
- **FQDN**: You can add FQDNs for applications with multiple IPv4 addresses or with IPv4 addresses that frequently change.
-
**Wildcard FQDN**: You can add wildcard FQDNs to extend the policy to the subdomains of the stated URL. For example, the wildcard FQDN `*.safemarch.com` would match the following URLs:
- `atlanta.safemarch.com`
- `serv3.serv2.serv1.atlanta.safemarch.com`
- `safemarch.com`
- `safemarch.com/company/webinars`
- `serv3.serv2.serv1.atlanta.safemarch.com/company/webinars`
[See guidelines for configuring wildcard FQDNs.](#fqdn-format-guidelines)
To evaluate wildcard FQDNs against non-web traffic, Zscaler requires the IP address to which the FQDN resolves. Hence, for non-web traffic, the Zscaler service should be aware of the preceding DNS request/response. To ensure this, forward all of your DNS traffic to the Zscaler service if you intend to configure wildcard FQDNs in policies. Additionally, a Zscaler subscription with DNS Control is required. This functionality is included in Advanced Firewall and DNS Control subscriptions.
Wildcard FQDN match against web traffic (HTTP and TLS/SNI) can function without meeting these conditions.
-
**Other**: You can select this option if you don't want to associate IPv4 addresses, FQDNs, or domains with the destination group. Enter the following information:
- **Countries**:** **You can identify destinations based on the location of a server. Select **Any **to include all countries in the group or select specific countries.
- **Categories**:** **You can identify destinations based on the URL category of the domain. Select** **any number of custom URL categories to include in the group.
The destination group **Other** is supported only in firewall policies.
You can enter multiple entries for IP Address, FQDN, and Wildcard FQDN types. Press `Enter` after each entry, then click **Add Items**. For item lists, you can view up to 500 items on a page; filter the list by searching for a word, phrase, or number contained in an item; and remove all items from the list (**Remove All**) or only items from a specific page (**Remove Page**). If you select **Remove All** or **Remove Page**, a confirmation window appears.
For **Other** type, you can select multiple countries and/or categories. Click the drop-down, select the required items on the window that pops up, and click **Done**. To remove the items selected, click **Clear Selection **on the respective window.
- **Description**:** **(Optional) Type in any additional notes or information about the group. The description cannot exceed 10,240 characters. To learn more, see [Ranges & Limitations](/unified/ranges-limitations#internet-saas).
- Click **Save** and [activate the change](/unified/saving-and-activating-changes-admin-portal).
- []The wildcard character (*) preceding the leading period is optional (i.e., `*.safemarch.com` and `.safemarch.com` are equivalent).
- The wildcard character is allowed only as the leftmost label in wildcard FQDN entries. In other words, a wildcard is only used for full-text matches and cannot be used for partial matches (i.e., `.*safemarch.com`, `.safe*.com`, or `.sa*march.com` is not a legitimate wildcard FQDN).
- Only wildcard FQDNs using a prefix search are supported (e.g., `*.safemarch.com` is supported but `sub1.*.safemarch.com` is not supported). A wildcard can be used only once in an entry (i.e., `*.*.safemarch.com` is not allowed).
To learn more, see [URL Format Guidelines](/unified/url-format-guidelines).