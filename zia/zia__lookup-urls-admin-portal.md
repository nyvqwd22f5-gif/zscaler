# Looking Up URLs in the ZIA Admin Portal
Source: https://help.zscaler.com/zia/lookup-urls-admin-portal
PDF: https://help.zscaler.com/pdf/com/en/1399321.pdf

In the ZIA Admin Portal, you have the ability to see how Zscaler categorizes a site according to its URL or IP address. Since a single IP address is capable of running multiple hosts or applications, Zscaler does not typically place IP addresses into the predefined URL categories. However, if a SaaS or cloud provider dedicates an IP address or IP range to an application, the Zscaler service categorizes it. For example, 13.107.6.152/31 is used for Microsoft 365 and is categorized as Professional Services and Microsoft 365. To learn more about URL categories, see [About URL Categories](/zia/about-url-categories).
You can also look up URLs from [Zscaler's Site Review](https://sitereview.zscaler.com) website. To learn more, see [Using Site Review to Lookup URLs](/zia/using-site-review-lookup-urls).
To look up URLs:
-
Go to **Help** >** URL Lookup**.
[See image.](#image-1)
- Enter the URL and click **Lookup URL**.
The service displays the following information:
- **URL**: The URL you are looking up.
- **URL Classifications**: The predefined [category or super category](/zia/about-url-categories) of the URL.
- **Security Alert**: The security alert associated with the URL.
- **Cloud Application**: The [cloud application category and cloud application](/zia/about-cloud-app-categories) with which the URL is associated.
[See image.](#image-2)
[]![Where to find The help icon and URL Lookup option hightlighted](/downloads/zia/policies/url-filtering/lookup-urls-admin-portal/ZIA-help-URL-Lookup.png)
[]![The URL Lookup page showing fields used to look for URL classifications](/downloads/zia/documentation-knowledgebase/creating-and-managing-policies/url-filtering/configuring-url-filtering/how-do-i-look-urls/ZIA-URL-Lookup-Window.png)