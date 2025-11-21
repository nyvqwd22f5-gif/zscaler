# About Bandwidth Classes
Source: https://help.zscaler.com/zia/about-bandwidth-classes
PDF: https://help.zscaler.com/pdf/com/en/1398911.pdf

[Watch a video about Bandwidth Classes](https://fast.wistia.net/embed/iframe/jjpc536mhm).
Bandwidth classes identify the [URL categories](/zia/about-url-categories) and [cloud applications](/zia/about-cloud-app-control) to which the service allocates bandwidth. You must configure the bandwidth classes before you can reference them in [Bandwidth Control](/zia/about-bandwidth-control) policy rules. To configure bandwidth classes, you can edit the predefined bandwidth classes or add new bandwidth classes, by grouping URL categories, applications, or domains into it. For example, if you want to control bandwidth for service updates, you could create a custom Bandwidth class including the URLs for the App Store and apply your desired policy.
If you have created a custom bandwidth class that isn't being used in any policies for a location, then the custom class will be added to the location’s default Bandwidth Control rule. The default rule includes all internet traffic not covered by other rules. By default, it's not guaranteed any bandwidth, but it can consume up to 100% of the bandwidth when available. These bandwidth settings can be changed by editing the default rule.
The **Cloud Applications** tab lists predefined bandwidth classes to which you can add domains. The predefined bandwidth classes can't be deleted. You can also add your own custom domains.
Following are the predefined bandwidth classes:
- **File Share**: You can enter URLs that represent file sharing sites.
- **Finance:** You can enter URLs that represent business-oriented, financial web-based applications or tools, such as Smith Barney or eTrade.
- **General Surfing:** This class includes all URL categories and cloud apps that do not fall into one of the following categories (Webmail, Instant Messaging, Streaming Media/File Share, and Social Networks/Blogging). This class can't be edited.
- **Sales/Support Apps:** You can enter URLs that represent business-oriented, sales/support web-based applications or tools, such as Salesforce or NetSuite.
- **Streaming Media:** You can enter URLs that represent streaming sites.
To add domains to the predefined bandwidth classes:
- Go to **Administration **>** Bandwidth Classes **to manage bandwidth classes.
- Go to the **Cloud Applications** tab.
- [Edit](/zia/how-do-i-edit-delete-or-duplicate-items-admin-portal) a predefined bandwidth class.
The **Edit Bandwidth Class **window appears.
- In the **Edit Bandwidth Class **window:
- **Domains: **Enter the URLs you want to include in the bandwidth class, and** **click **Add Items**. Use the [URL Format Guidelines](/zia/url-format-guidelines) when adding domains.
Click **Save**.
- Click **Save** and [activate your changes](/zia/saving-and-activating-changes-admin-portal).
About the Bandwidth Classes Page
On the Bandwidth Classes page:
- You can add up to 25,000 custom URLs (across all categories), and up to 64 custom categories. For a complete list of ranges and limits per feature, see [Ranges & Limitations](/zia/ranges-limitations).
- [Add a bandwidth class for cloud applications](/zia/adding-bandwidth-classes).
- Click the **Large Files** tab to configure that bandwidth class. To learn more, see [Configuring the Large Files Bandwidth Class](/zia/configuring-large-files-bandwidth-class).
- Click the **Web Conferencing Applications **tab to configure that bandwidth class. To learn more, see [Configuring the Web Conferencing Applications Bandwidth Class](/zia/configuring-web-conferencing-applications-bandwidth-class).
- Click the **VoIP** **Applications **tab to configure that bandwidth class. To learn more, see [Configuring the VoIP Applications Bandwidth Class](/zia/configuring-voip-applications-bandwidth-class).
- View a list of all configured bandwidth classes:
- **Name**: The name of the bandwidth class. You can sort this column.
- **URL Categories**: Which URL categories are included in the URL categories. To learn more about URL categories, see [About URL Categories](/zia/about-url-categories).
- **Cloud Applications**: The cloud applications included in the bandwidth class. You can select [cloud application categories](/zia/cloud-app-categories) or individual cloud applications.
- **Domains**: The domains included in the bandwidth class. You can add domains for up to 8 individual bandwidth classes.
- Edit a bandwidth class. To learn more, see [Editing, Deleting, or Duplicating Items](/zia/editing-deleting-duplicating-items).
- View the General Surfing bandwidth class. This class includes all URL categories and cloud apps that do not fall into one of the following categories (Webmail, Instant Messaging, Streaming Media, File Share, and Social Networks/Blogging).
- Modify the table and its columns. To learn more, see [Using Tables](/zia/using-tables).
- Search for a configured bandwidth class.
![Screenshot of the Bandwidth Classes page with labeled parts](/downloads/zia/documentation-knowledgebase/creating-and-managing-policies/bandwidth-management/bandwidth-management-guide/about-bandwidth-classes/zia-bandwidth-classes-5.7.png)