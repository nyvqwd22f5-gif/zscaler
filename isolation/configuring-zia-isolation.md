# Configuring ZIA for Isolation
Source: https://help.zscaler.com/isolation/configuring-zia-isolation
PDF: https://help.zscaler.com/pdf/com/en/1447181.pdf

[Watch a video about configuring ZIA for Isolation.](https://fast.wistia.net/embed/iframe/6r6l3ej234)
Zscaler Isolation provides organizations with the capability to isolate web pages and categories of web pages, as well as isolate files downloaded from these web pages in a contained, temporary browser on the Zscaler Cloud. Isolation offers complete integration with Zscaler Secure Internet and SaaS Access (ZIA), allowing admins to granularly define what web traffic from a user should be isolated and what policies need to be applied on the isolated traffic. To learn more, see [What is Isolation?](/isolation/what-isolation)
To learn about configuring Isolation for Secure Private Access (ZPA), see [About the ZPA Admin Portal](/zpa/about-zpa-admin-portal) and [About Isolation Policy](/zpa/about-isolation-policy).
Users must first be authenticated for any traffic and web requests to be redirected to Isolation.
In this configuration, you will create a new URL Filtering Policy Rule in ZIA to forward traffic to Isolation.
Prerequisites
- Isolation must be licensed for your organization.
- Admins must use the isolation profiles to configure policies in ZIA. To learn more, see [Creating a ZIA Isolation Profile for Isolation](/isolation/creating-zia-isolation-profile-isolation) and [Default Isolation Profiles in Isolation](/isolation/default-isolation-profiles-isolation).
Creating a URL Filtering Policy Rule to Isolate Web Traffic
Users can only enable the Isolate action in a URL policy if:
- The protocol is HTTP, HTTPS, or both.
- The HTTP method is limited to CONNECT, GET, TRACE, or HEAD.
- The user agent is comprised of a minimum of one or more known browsers.
These parameters are automatically set after your organization has enabled Isolation.
To create this policy:
- Go to **Policy** > **URL & Cloud App Control**.
- Select **Add URL Filtering Rule**.
- In the **Add URL Filtering Rule **window:
- Choose a **URL Category** and any other rule **Criteria**.
[See image.](#Add-URL-filtering-rule)
- Select **Isolate** for **Web Traffic**.
The **Isolation Profile** drop-down menu appears.
- Choose the desired profile you want to isolate criteria-matching traffic for.
[See image.](#Select-Isolation-profile)
- Click **Save** to activate your changes.
Bandwidth Control is disabled for all traffic from the isolated browser destined to the ZIA Public Service Edges. To learn more, see [About Bandwidth Control](/zia/about-bandwidth-control).
![Choose the Isolate Action for Web traffic and then isolation profile from the dropdown](/downloads/zia/cloud-browser-isolation/configuring-browser-isolation/ZIA_URL-filtering-policy_action-isolate-dropdown-cropped-small.png)
[]
![Criteria field options](/downloads/zia/cloud-browser-isolation/configuring-browser-isolation/ZIA_URL-filtering-policy-criteria_URL-category.png)
[]