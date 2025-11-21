# Looking Up URLs in Site Review
Source: https://help.zscaler.com/zia/using-site-review-lookup-urls
PDF: https://help.zscaler.com/pdf/com/en/1400241.pdf

Site Review is a URL categorization lookup tool that can be accessed by users going through the Zscaler service. By searching for a URL or IP address, you can find out how the site is categorized in Zscaler's URL filtering database. Results might vary from those seen in your environment due to custom [categories](/zia/about-url-categories) that your admin has configured.
Since a single IP address is capable of running multiple hosts or applications, Zscaler does not typically place IP addresses into predefined URL categories. However, if a SaaS or cloud provider dedicates an IP address or IP range to an application, the Zscaler service categorizes it. For example, 13.107.6.152/31 is used for Microsoft 365 and is categorized as Professional Services and Microsoft 365.
If you think that a website is incorrectly categorized, you can also use Site Review to request reclassification. For each request, based on your email address, a support case is automatically created. Zscaler Support then reviews the request and takes the required action on the URL category. After the request is reviewed, you get an email notification.
The [Site Review](https://sitereview.zscaler.com/) website supports multiple languages (i.e., Chinese, Chinese Taiwan (Optional), English (United States), English (United Kingdom), French, German, Japanese, Russian, and Spanish). Ensure to set the browser language settings to one of the supported languages.
To use Site Review:
- Go to [https://sitereview.zscaler.com/](https://sitereview.zscaler.com/).
-
In the **Enter URL** field, add a URL or IP address. Press `Enter` on your keyboard or click **Add More** to add up to three sites.
The URL or IP address is automatically populated in the **Enter URL** field when you request a review of it from the blocked EUN page.
- Click **Look Up** after you have added your sites. The **Request Review** page appears.
- On the **Request Review** page, you can see:
- **URL**: URL or IP address of the site that was looked up.
-
**Cloud Applications**: Cloud application for the site that was looked up.
A cloud application is shown only if it's associated with the looked-up URL.
- **Current Categories**: Current category of the site that was looked up.
-
(Optional) You can request a change to a site's categorization:
The site review website doesn't allow recategorization of a URL to a specific cloud application (e.g., The URL, www.zscaler.com associated with the cloud application A can not be recategorized to cloud application B using site review.). To recategorize a URL to a specific cloud application, contact Zscaler Support.
- Select up to three categories that you think are appropriate for the website. You can use either of the following methods to select the categories:
-
Click the drop-down arrow to search and select categories.
[See image.](#seeimage1)
or
-
Click **Menu** to see a full list of categories and select by clicking the category name.
[See image.](#seeimage2)
- Click **Done** when your selection is complete. Your suggested categories appear in the **Suggested Categories** column.
- In the **Comments** box, provide a reason you want the URL category to be modified.
- In the **Email** field, add your email address to receive updates on your request.
- Click **Submit Request**.
You can also look up URLs directly from the ZIA Admin Portal. To learn more, see [Looking up URLs in the ZIA Admin Portal](/zia/lookup-urls-admin-portal).
[]![The Request Review section on the Zscaler Site Review page with the Suggested Categories drop-down](/downloads/tech-pubs-drafts/zia-draft-articles/looking-urls-site-review-doc-53929/ZIA_site-review-dropdown.png)
[]![The Request Review section on the Zscaler Site Review page with the Suggested Categories menu button](/downloads/tech-pubs-drafts/zia-draft-articles/looking-urls-site-review-doc-53929/ZIA_Site_Review-Full-List.png)