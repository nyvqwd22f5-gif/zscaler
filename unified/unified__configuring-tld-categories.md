# Configuring TLD Categories
Source: https://help.zscaler.com/unified/configuring-tld-categories
PDF: https://help.zscaler.com/pdf/com/en/1493961.pdf

Create TLD Categories to control top-level domains (TLDs). You can select TLD categories in the following policies:
- [DNS Control](/unified/configuring-dns-control-policy)
- [File Type Control](/unified/configuring-file-type-control-policy)
- [Firewall Filtering](/unified/configuring-firewall-filtering-policy)
- [IPS Control](/unified/configuring-ips-control-policy)
- [Sandbox](/unified/configuring-sandbox-policy)
- [DLP Policy with Content Inspection](/unified/configuring-dlp-policy-rules-content-inspection)
- [DLP Policy without Content Inspection](/unified/configuring-dlp-policy-rules-without-content-inspection)
- [Forwarding Control](/unified/configuring-forwarding-policy)
- [SSL Inspection](/unified/configuring-ssl-inspection-policy)
- [URL Filtering](/unified/about-url-filtering)
To add a TLD Category:
- Go to **Policies** > **Access Control** > **Internet & SaaS** > **URL Categories**.
- Click the **TLD Categories** tab.
- In the upper left corner, click **Add TLD Category**.
- Complete the following:
- **Name**: Type in a name for the new category. Category names can only contain alphanumeric characters, underscores, hyphens, dots, parenthesis, and spaces.
- **URL Super Category**: This is always User-Defined. Because TLDs are capable of controlling a wide variety of websites, TLD categories do not fit neatly into the other pre-defined URL categories.
-
**Administrator Operational Scope**: Choose the operational scope for this category. You can select multiple operational scopes and when there is more than one scope, OR logic is used to find a match. Select from the following scopes:
- **Any**: Any admin can manage. If your organization does not have granular access requirements for custom URL categories, select Any as the scope. You can then control which admins are able to manage custom categories through admin roles.
- **Organization**: Admins whose scope is Organization can manage.
- **Location Group**: Admins with one or more of the selected location groups in their scope can manage.
- **Location**: Admins with one or more of the selected locations in their scope can manage.
Admins that have an operational scope over location groups that include one or more of the selected locations can also manage. However, they cannot change the operational scope of the category.
- **Department**: Admins with one or more of the selected departments in their operational scope can manage.
If there are any operational scopes that you don't see, they are not part of your administrative operational scope.
You can only delete a custom category that belongs to the User-Defined super category if your administrator scope exactly matches the scope of the custom category.
- **Top Level Domains**: Enter the TLDs for this category (For example, .edu, .us, .coffee) and click **Add Items**. You can enter multiple entries. Hit **Enter** after each entry. You can add up to two levels of domains (For example, .co.uk, .gov.in). For item lists, you can view up to 500 items on a page; filter the list by searching for a word, phrase, or number contained in an item; and remove the first 25,000 items from the list (**Remove 25K Items**) or only items from a specific page (**Remove Page**). If you select **Remove 25K Items** or **Remove Page**, a confirmation window will appear.
- **Description**: (Optional) Enter additional notes or information. The description cannot exceed 256 characters.
- Click **Save** and activate the change.