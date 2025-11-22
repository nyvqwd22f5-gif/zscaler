# Adding Bandwidth Classes
Source: https://help.zscaler.com/zia/adding-bandwidth-classes
PDF: https://help.zscaler.com/pdf/com/en/1399911.pdf

[Watch a video about Bandwidth Classes](https://fast.wistia.net/embed/iframe/jjpc536mhm)
Bandwidth classes identify the URL categories and applications to which the service allocates bandwidth. You must configure the bandwidth classes before you can reference them in the [Bandwidth Control](/zia/about-bandwidth-control) policy rules. To configure bandwidth classes, you can edit the predefined bandwidth classes or add new bandwidth classes, then group URL categories, applications, or domains into the bandwidth classes.
In the **Cloud Applications **tab:
- Add up to 245 custom bandwidth classes.
- You can have up to 8 bandwidth classes with custom domains.
- Add up to 25,000 domains across all bandwidth classes (including URL categories).
The tab also lists predefined bandwidth classes to which you can add domains. The predefined bandwidth classes cannot be deleted. You can also add your own custom domains. For more information about predefined bandwidth classes, see [About Bandwidth Classes](/zia/about-bandwidth-classes).
If you have created a custom bandwidth class that isn't being used in any policies for a location, then the custom class will be added to the location’s default Bandwidth Control rule. The default rule includes all internet traffic not covered by other rules. By default, it's not guaranteed any bandwidth, but it can consume up to 100% of the bandwidth when available. These bandwidth settings can be changed by editing the default rule.
To add a new bandwidth class:
- Go to **Administration **>** Bandwidth Classes **to manage bandwidth classes.
- Go to the **Cloud Applications** tab.
- Click **Add Bandwidth Class**.
The **Add Bandwidth Class** window appears.
- In the **Add Bandwidth Class** window:
- **Name: **Type a name for the class.
- **URL categories: **Select [URL categories](/zia/about-url-categories) to add to the bandwidth class.
- **Cloud Applications:** Select [cloud applications](/zia/cloud-app-categories) to add to the bandwidth class. You can select cloud application categories or individual cloud applications.
By default, this field displays the first 100 cloud applications. The subsequent 100 cloud applications are displayed when you click the **Click to see more **link at the bottom of the list. You can repeat this process to view the remaining cloud applications.
[See image.](#cloud-app-field-with-click-see-more)
- **Domains: **Enter the URLs that you want to include in the bandwidth class and click **Add Items**. You can enter multiple entries. Hit **Enter** after each entry. You can add domains for up to 8 individual bandwidth classes. For guidance on entering URLs, see the [URL format guidelines](/zia/url-format-guidelines). For item lists, you can view up to 500 items on a page; filter the list by searching for a word, phrase, or number contained in an item; and remove the first 25,000 items from the list (**Remove 25K Items**) or only items from a specific page (**Remove Page**). If you select **Remove 25K Items** or **Remove Page**, a confirmation window will appear.
Click **Save**.
- Click **Save **and [activate the change](/zia/saving-and-activating-changes-admin-portal).
[]![Screenshot of ZIA Add Add Bandwidth Class with Click to See More in the Cloud Applications Field](/downloads/zia/documentation-knowledgebase/policies/bandwidth-management/adding-bandwidth-classes/ZIA-Add-Bandwidth-Classes-See-More.png)