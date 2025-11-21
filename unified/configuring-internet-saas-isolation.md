# Configuring Internet & SaaS for Isolation
Source: https://help.zscaler.com/unified/configuring-internet-saas-isolation
PDF: https://help.zscaler.com/pdf/com/en/1492751.pdf

Zscaler Isolation provides organizations with the capability to isolate web pages and categories of web pages, as well as isolate files downloaded from these web pages in a contained, temporary browser on the Zscaler cloud. Isolation offers complete integration with Zscaler Internet & SaaS, allowing admins to granularly define what web traffic from a user should be isolated and what policies need to be applied on the isolated traffic.
To learn about configuring Isolation for Private Applications, see [Signing in to the Admin Portal](/unified/signing-admin-portal) and [About Isolation Policy](/unified/about-isolation-policy).
Users must first be authenticated for any traffic and web requests to be redirected to Isolation.
In this configuration, you will create a new URL Filtering Policy Rule in Internet & SaaS to forward traffic to Isolation.
Prerequisites
- Isolation must be licensed for your organization.
- Admins must use the isolation profiles to configure policies in Internet & SaaS. To learn more, see [Creating Isolation Profiles for Internet & SaaS ](/unified/creating-isolation-profiles-internet-saas)and [Default Isolation Profiles in Isolation](/unified/default-isolation-profiles-isolation).
Creating a URL Filtering Policy Rule to Isolate Web Traffic
Users can only enable the Isolate action in a URL policy if:
- The protocol is HTTP, HTTPS, or both.
- The HTTP method is limited to CONNECT, GET, TRACE, or HEAD.
- The user agent is comprised of a minimum of one or more known browsers.
These parameters are automatically set after your organization has enabled Isolation.
To create this policy:
- Go to **Policies **> **Access Control** >** Internet & SaaS **> **URL Filtering**.
- Select **Add URL Filtering Rule**.
- In the **Add URL Filtering Rule **window:
- Choose a **URL Category** and any other rule **Criteria**.
[See image.](#Add-URL-filtering-rule)
- Select **Isolate** for **Web Traffic**.
The **Isolation Profile** drop-down menu appears.
- Choose the desired profile you want to isolate criteria-matching traffic for.
[See image.](#Select-Isolation-profile)
- Click **Save** to activate your changes.
Bandwidth Control is disabled for all traffic from the isolated browser destined to the Internet & SaaS Public Service Edges. To learn more, see [About Bandwidth Control](/unified/about-bandwidth-control).
![Choose the Isolate Action for Web traffic and then isolation profile from the dropdown](/downloads/zia/cloud-browser-isolation/configuring-browser-isolation/ZIA_URL-filtering-policy_action-isolate-dropdown-cropped-small.png)
[]
![Criteria field options](/downloads/zia/cloud-browser-isolation/configuring-browser-isolation/ZIA_URL-filtering-policy-criteria_URL-category.png)
[]