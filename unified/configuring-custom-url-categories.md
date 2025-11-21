# Configuring Custom URL Categories
Source: https://help.zscaler.com/zia/configuring-custom-url-categories
PDF: https://help.zscaler.com/pdf/com/en/1399366.pdf

[Watch a video about configuring custom URL categories](https://fast.wistia.net/embed/iframe/xi70acd2at#)
Creating and configuring custom categories provides you with greater flexibility when creating [URL filtering policies](/zia/about-url-filtering), allowing specific websites, keywords, and IP ranges to be controlled as desired. You can create up to 64 custom categories and you can also choose whether the URLs, keywords, and IP ranges you add remain mapped to their parent URL category (the [predefined URL category](/zia/about-url-categories) to which they currently belong).
Custom categories can only be managed by super admins, admins with the Custom URL Management role, or admins with the Custom URL Management and Override Existing URLs role. To learn more, see [Adding Admin Roles](/zia/adding-admin-roles).
To add a custom URL category:
- Go to **Administration **>** URL Categories**.
- In the upper left corner, click **Add**.
or,
Next to the super category you want to add your custom category to, click the **Add** icon.
- Complete the following fields:
- **Name**: Type in a name for the new category. Category names can only contain alphanumeric characters, underscores, hyphens, dots, parenthesis, and spaces.
- **URL Super Category**: Choose the URL super category that you want the custom category to belong to.
-
**Administrator Operational Scope**: Choose the operational scope for this category. This option is only available for categories where the URL super category is User-Defined. You can select multiple operational scopes and when there is more than one scope, OR logic is used to find a match. For example, see [Scope Examples](#scope-examples).
Select from the following scopes:
- **Any**: Any admin can manage. If your organization does not have granular access requirements for custom URL categories, select **Any** as the scope. You can then control which admins are able to manage custom categories through admin roles.
- **Organization**: Admins whose scope is Organization can manage.
- **Location Group**: Admins with one or more of the selected location groups in their scope can manage.
- **Location**: Admins with one or more of the selected locations in their scope can manage.
Admins that have an operational scope over location groups that include one or more of the selected locations can also manage. However, they cannot change the operational scope of the category.
- **Department**: Admins with one or more of the selected departments in their operational scope can manage.
If there are any operational scopes that you don't see, they are not part of your administrative operational scope.
You can only delete a custom category that belongs to the User-Defined super category if your administrator scope matches the scope of the custom category exactly.
-
**Custom URLs**:** **Enter the URLs or IP addresses you want to add to this custom category and click **Add Items**.
The IP addresses entered can only match if you directly access the IP address in the URL (e.g., https://192.168.1.10). This field supports IPv6 addresses either in full or short form (e.g., 2041:0000:140f:0000:0000:0000:875b:131b or 2041:0000:140f::875b:131b).
Add URLs or IP addresses to this field if you want to override the category or to create your own denylist or allowlist of URLs or IP addresses.
URLs or IP addresses added to Custom URLs do not remain mapped to the category in the Zscaler URL database, also called the parent category. So these URLs or IP addresses are covered by policies that reference this specific custom category, but not by policies that reference their parent category. For example, if you enter www.amazon.com here, this site is no longer covered by policies that reference its parent URL category (Online Shopping).
To add multiple entries, press **Enter** after each entry. For item lists, you can view up to 500 items on a page; filter the list by searching for a word, phrase, or number contained in an item; and remove the first 25,000 items from the list (**Remove 25K Items**) or only items from a specific page (**Remove Page**). If you select **Remove 25K Items** or **Remove Page**, a confirmation window appears.
To learn how to find the parent category of a given URL, see [Looking up URLs in the ZIA Admin Portal](/zia/lookup-urls-admin-portal). For guidance on entering URLs, see the [URL format guidelines](/zia/url-format-guidelines).
-
**URLs Retaining Parent Category**: Enter the URLs or IP addresses you want to add to this custom category and click **Add Items**.
The IP addresses entered can only match if you directly access the IP address in the URL (e.g., https://192.168.1.10). This field supports IPv6 addresses either in full or short form (e.g., 2041:0000:140f:0000:0000:0000:875b:131b or 2041:0000:140f::875b:131b).
URLs retaining parent category remain mapped to their parent category. So these URLs or IP addresses are covered by policies that reference the parent category and this custom category. For example, if you enter www.amazon.com here, this site is covered by policies that reference this custom category and its parent URL category (Online Shopping).
To add multiple entries, press **Enter** after each entry. For item lists, you can view up to 500 items on a page; filter the list by searching for a word, phrase, or number contained in an item; and remove the first 25,000 items from the list (**Remove 25K Items**) or only items from a specific page (**Remove Page**). If you select **Remove 25K Items** or **Remove Page**, a confirmation window appears.
If you add already categorized URLs or IP addresses to the **Miscellaneous or Unknown** category in the **URLs retaining parent category** field, the system only categorizes URLs or IP addresses under the pre-existing URL category and not under the **Miscellaneous or Unknown** category. For example, if you add www.blogs.com belonging to the **Blogs** category to the **Miscellaneous or Unknown** category in the **URLs retaining parent category** field, and if you had a policy that blocked the **Miscellaneous or Unknown** category, then www.blogs.com is not blocked as it's categorized only under the **Blogs** category and not under the **Miscellaneous or Unknown** category.
-
**Review Matches**: Select this drop-down menu to see if either the URLs or wildcard domains added in this custom URL category match any other custom categories with either the corresponding wildcard or a specific match, respectively. Choose a matching category if you want to add the URLs or wildcard domains to it.
For example, if you add a specific URL (test.example.com) to the custom category CAT A, and the custom category CAT B contains a wildcard URL (.example.com), then the system recognizes that the specific URL also matches the wildcard in the category CAT B and gives you the option to add it to CAT B, and vice versa.
This drop-down menu appears when you add a URL or an IP address either to the **Custom URLs **or **URLs Retaining Parent Category **field.
-
**Custom Keywords**: Enter keywords that you want to add to this custom category and click **Add Items**.
To add multiple entries, press **Enter** after each entry. For item lists, you can view up to 500 items on a page; filter the list by searching for a word, phrase, or number contained in an item; and remove all items from the list (**Remove All**) or only items from a specific page (**Remove Page**). If you select **Remove All** or **Remove Page**, a confirmation window appears.
URLs that match the keywords are added to the custom category but are not retained under their original parent category. For example, if you create a custom URL category that includes "gambling" as a custom keyword, a site like www.gambling.com is only covered by policies that reference this custom category. It's not covered by policies that reference its parent URL category (Gambling).
Policies including custom keywords trigger if the keyword is a full or partial match of the URI. For example, if you had a policy that blocked a URL category that included "gambling", then www.gambling101.com and www.gambling.com would both be blocked. In addition, as custom keywords apply to the entire URI, if you went to www.google.com and searched for "gambling", the search results would also be blocked since the word gambling appears in the URI (https://www.google.com/search?q=*gambling*&oq=*gambling*&aqs=chrome..69i57j0l4.2767j0j8&sourceid=chrome&ie=UTF-8).
Custom keywords must be between 3 and 255 characters.
-
**Keywords Retaining Parent Category**: Enter the keywords you want to add to this custom category and click **Add Items**.
To add multiple entries, press **Enter** after each entry. For item lists, you can view up to 500 items on a page; filter the list by searching for a word, phrase, or number contained in an item; and remove all items from the list (**Remove All**) or only items from a specific page (**Remove Page**). If you select **Remove All** or **Remove Page**, a confirmation window appears.
URLs that match the keywords are added to the custom category and also retained under their original parent category. For example, if you create a custom URL category that includes "gambling" as a keyword retaining parent category, a site like www.gambling.com is covered by policies that reference this custom category as well as by policies that reference its parent URL category (Gambling).
Policies including keywords retaining parent category trigger if the keyword is a full or partial match of the URI.
Keywords retaining parent category must be between 3 and 255 characters.
Adding keywords in the URLs belonging to the **Miscellaneous or Unknown** category to the **Keywords retaining parent category** in a URL category only categorizes the URLs under the respective URL category and not under **Miscellaneous or Unknown**.
-
**Custom IP Ranges**:** **Enter the IP ranges you want to add to this custom category and click **Add Items**.
This field is not available by default. Contact Zscaler Support to enable it. Also, IPv6 ranges are not supported for this field.
Add IP ranges to this field if you want to override the category or to create your own denylist or allowlist of IP ranges.
IP ranges added to custom IP ranges do not remain mapped to the category in the Zscaler URL database, also called the parent category. So these IP ranges are covered by policies that reference this specific custom category, but not by policies that reference their parent category. For example, if you enter 13.107.6.152/31 used for Microsoft 365 here, this IP range is no longer covered by policies that reference its parent URL category (Professional Services).
To add multiple entries, press **Enter** after each entry. For item lists, you can view up to 500 items on a page; filter the list by searching for a word, phrase, or number contained in an item; and remove the first 25,000 items from the list (**Remove 25K Items**) or only items from a specific page (**Remove Page**). If you select **Remove 25K Items** or **Remove Page**, a confirmation window appears.
-
**IP Ranges Retaining Parent Category**: Enter the IP ranges you want to add to this custom category and click **Add Items**.
IPv6 ranges are not supported for this field.
IP ranges retaining parent category remain mapped to their parent category. So these IP ranges are covered by policies that reference the parent category and this custom category. For example, if you enter 13.107.6.152/31 used for Microsoft 365 here, this IP range is covered by policies that reference this custom category and its parent URL category (Professional Services).
To add multiple entries, press **Enter** after each entry. For item lists, you can view up to 500 items on a page; filter the list by searching for a word, phrase, or number contained in an item; and remove the first 25,000 items from the list (**Remove 25K Items**) or only items from a specific page (**Remove Page**). If you select **Remove 25K Items** or **Remove Page**, a confirmation window appears.
Adding IP ranges belonging to the **Miscellaneous or Unknown** category to the **IP Ranges Retaining Parent Category** in a URL category only categorizes the IP ranges under the respective URL category and not under **Miscellaneous or Unknown**.
- **Description**: (Optional) Enter additional notes or information. The description cannot exceed 256 characters.
- Click **Save** and [activate the change](/zia/saving-and-activating-changes-admin-portal).
[]Scope Examples
These examples highlight the importance of considering scope when creating categories that belong to the User-Defined super category.
Example One
Example Category has the following **Administrator Operational Scopes**:
- **Location**: Selected locations are San Jose, Bangalore, and Tokyo.
- **Department**: Selected departments are Sales and Marketing.
Admin A, who has a Location scope that only includes San Jose and Bangalore, can edit Example Category. Admin B, whose department scope is only over Sales, can also edit.
Example Two
Test Category has the following **Administrator Operational Scope**:
- **Location**: Selected locations are London and Paris.
Admin A has a Location Group scope of England. The England location group contains London and Manchester. Admin A can edit all of Test Category, with the exception of its operational scope.