# Configuring Advanced Policy Settings
Source: https://help.zscaler.com/unified/configuring-advanced-policy-settings
PDF: https://help.zscaler.com/pdf/com/en/1493971.pdf

To configure the advanced policy settings:
- Go to **Policies **>** Access Control **>** Internet & SaaS** >** Advanced Settings**.
-
Configure the following:
- [Enable CIPA Compliance](#Enable-CIPA)
- [Enable Suspicious New Domains Lookup](#DomainLookup)
- [Enable 3rd-Party URL Category Lookup](#3rd-party-url-cat-lookup)
- [Enable AI-/ML-Based Content Categorization](#Dynamic)
- [Enable Embedded Sites Categorization](#Embedded)
- [Enforce SafeSearch](#Safe)
- [Enable Creative Commons Search Results](#CC-search)
- [Enable Identity-Based Block Override](#Enable-block-override)
- [Enable Microsoft-Recommended One Click Office 365 Configuration](#MicrosoftOneClick)
- [Skype](#Skype)
- [Unified Communications as a Service (UCaaS)](#ucaas)
- [Gen AI Prompt Configuration](#gen-AI-prompt)
[See image.](#adv-policy-settings)
- Click **Save** and [activate the change](/unified/saving-and-activating-changes-admin-portal).
[]Enable this option to activate the predefined CIPA Compliance Rule. To learn more, see [About CIPA Compliance](/unified/about-cipa-compliance).
If you have exceeded the [URL filtering policy rules limit](/unified/ranges-limitations#Rules), the following warning message appears:
`You cannot enable CIPA compliance because you have reached the maximum number of URL filtering rules and the CIPA compliance rule cannot be auto-enabled for you. To enable CIPA compliance, you have to delete one of your URL filtering rules, and then enable CIPA compliance.`
[]Enable this option to provide advanced protection to users against the newly registered and observed domains that are identified within hours of going live. This feature also identifies newly revived domains. These domains are often considered potentially malicious until they are well-known or categorized. Identifying them improves the overall security posture. This feature is a prerequisite for using the Newly Registered and Observed Domains and Newly Revived Domains [URL categories](/unified/about-url-categories) in a policy rule.
Zscaler recommends enabling SSL Inspection for these URL categories.
[]Enable this option if you want the service to perform URL category lookups for uncategorized URLs using a third-party database.
![ZIA Advanced Policy Settings Page](/downloads/zia/policies/url-filtering/configuring-advanced-policy-settings/ZIA-Advanced-Policy-Settings-3rd-Party-URL-Category-Lookup.png)
[]Enable this option if you want the service to analyze the content of uncategorized websites using AI/ML tools to identify whether they belong to one of the predefined URL categories.
If the service determines that a site belongs to a category, then it categorizes the site to that category and applies the corresponding policies. When AI-/ML-based content categorization is enabled, the handling of transactions depends on the HTTP response codes received from the website server.
For example:
- **Redirect responses (3xx)**: If the policy is set to block a category (e.g., Gambling), but the server responds with a redirect (3xx response code), then Zscaler allows the transaction to proceed and follows the redirect.
- **Server error responses (5xx)**: If the server returns a response code indicating a server error (5xx), then Zscaler logs the transaction as allowed.
- **Other response codes**: For all other response codes, Zscaler blocks or allows the site based on your configured policy for the identified category.
[]Enable this option to allow the service to enforce the [URL filtering policy](/unified/about-url-filtering) for sites that are translated using translation service websites. For example, when this feature is enabled, if you have a policy that blocks www.gambling.com, and a user translates the page to another language using Google Translate, the service blocks the translated page.
[]Enable this option if you want the service to return only safe content from searches. When SafeSearch is enabled, the following field appears:
**SafeSearch Applications**: Choose any of the following applications to which you want to apply SafeSearch:
- AOL
- Bing Search
- Dailymotion
- DuckDuckGo
- Flickr
- Google
- Yahoo
- YouTube
[SSL Inspection](/unified/about-ssl-inspection) must be enabled for this option.
[]Enable this option if you want the service to return only Creative Commons search content from the following search engines:
- Bing
- Google
- Yahoo
This option is disabled by default.
[]Enable this option to allow authorized users to provide temporary access to the blocked pages by using the company-provided credentials such as the single sign-on credentials.
In companies that have SAML authentication and the Enable Identity-Based Block Override option activated:
- Unauthorized users (e.g., students) are temporarily allowed to access the blocked pages if authorized users (e.g., teachers) reauthenticate for them in the SAML reauthentication prompt.
- Authorized users (e.g., teachers) are temporarily allowed to access the blocked pages if they reauthenticate in the SAML reauthentication prompt.
Ensure that SAML Identity Provider (IdP) force reauthentication is enabled on the IdP side for the SAML reauthentication prompt to appear when you override the blocked pages. All other IdPs either don't support force reauthentication or support force reauthentication without any additional configuration.
If your company uses Okta IdP, ensure to clear the **Disable Force Authentication** option under the **Sign On** tab in the Okta SAML 2.0 application to enable forced reauthentication.
[See image.](#okta-sign-on)
If you disable this option, the default block override behavior (hosted database) is applied. To learn more, see [Configuring the URL Filtering Policy](/unified/configuring-url-filtering-policy#block-override).
[]Enabling this option allows Zscaler to enable local breakout for Microsoft 365 traffic automatically without any manual configuration needed by customers. Enabling this option turns off SSL Interception for all Microsoft 365 destinations as per Microsoft's recommendation. If you want to continue using existing granular controls for Microsoft 365, disable this option and enable the pre-existing configuration. To learn more, see [About Microsoft One Click Options](/unified/about-microsoft-one-click-options).
[]While VoIP might be encouraged for its telephone cost savings, it might also be discouraged because of the high bandwidth utilization associated with it. The Zscaler service can block access to Skype, a popular P2P VoIP application.
[]UCaaS is a cloud delivery model that offers communications and audio/video-based collaboration services. It's rapidly being adopted by enterprises of all sizes. Zscaler enables direct-to-cloud access for UCaaS applications like Zoom, GoTo, RingCentral, Webex, and Talkdesk by enabling organizations to send traffic directly to application servers over the internet, instead of backhauling traffic over costly Multiprotocol Label Switching (MPLS) circuits.
Zscaler simplifies your UCaaS deployment by taking advantage of our global direct-to-cloud network, which improves user experience and application performance for your organization. If your organization uses any of the UCaaS applications, you can send all traffic from all your locations, including remote user traffic, through the Zscaler service. The Zscaler service provides a One-Click Configuration option for UCaaS apps which allows Zscaler to identify and map all IP ranges and domains, including ports and protocols for secure connectivity and better user experience. Zscaler partnered with all major UCaaS vendors (Zoom, GoTo, RingCentral, Webex, and Talkdesk) and leverages the REST-based web services to keep this mapping up to date dynamically.
Enabling the **Zoom,** **GoTo**, **RingCentral**, **Webex**, or **Talkdesk** option allows Zscaler to permit secure local breakout for their traffic automatically, without any manual configuration needed. When either option is enabled, it turns off SSL interception for all Zoom, GoTo, RingCentral, Webex, or Talkdesk destinations. To continue using existing granular controls for Zoom, GoTo, RingCentral, Webex, or Talkdesk, disable the respective option, and enable cloud application and firewall network application policies accordingly.
Also, when either option is enabled, a **UCaaS One Click Rule **is automatically created in the following policies:
- [Firewall Control Policy](/unified/about-firewall-filtering) and [DNS Control Policy](/unified/about-dns-control): The rule is created to allow traffic from firewall.
- [Cloud App Control Policy](/unified/about-cloud-app-control): The rule is created under the Collaboration & Online Meetings category to allow traffic destined to the Zoom, GoTo, RingCentral, Webex, or Talkdesk UCaaS applications.
The Webex Connect application is not part of the Webex option.
[]Generative AI (Gen AI) prompts are a series of instructions that are provided as input to Gen AI applications to get the desired response from them. The Zscaler service categorizes and stores prompts for Gen AI applications. Enabling the following options allows Zscaler to categorize and store the prompts for the respective applications:
- **ChatGPT**
- **Microsoft Copilot**
- **Gemini**
- **Perplexity**
- **Poe**
- **Meta AI**
- **Writer**
- **Deepseek**
- **Grok AI**
The prompts for these applications are logged on the [Web Insights Logs](/zia/about-insights-logs) page.
The Zscaler service stores prompts up to a maximum of 2 KB in size for these applications. Prompts for the Microsoft Copilot application are stored only if the user is not authenticated to it.
To apply DLP WebSocket policies and capture prompts for Microsoft Copilot, Zscaler recommends users to:
- Create a custom URL category for substrate.office.com and copilot.microsoft.com for SSL Inspection. To learn more, see [Configuring Custom URL Categories](https://help.zscaler.com/zia/configuring-custom-url-categories).
- Create a new SSL Inspection policy for the custom category above the OneClick SSL Inspection policy. To learn more see, [Configuring SSL Inspection Policy](https://help.zscaler.com/zia/configuring-ssl-inspection-policy).
Zscaler's DLP inspection and prompt capture capabilities are currently limited to Microsoft Copilot Chat. Support for Microsoft Copilot embedded within Microsoft Office applications is currently unavailable.
[]![Sign On tab allows you to sign into an application](/downloads/zia/documentation-knowledgebase/creating-and-managing-policies/url-filtering/configuring-url-filtering/how-do-i-configure-advanced-url-policy-settings/ZIA-Sign-On-Okta-SAML.png)
[]![Advanced Policy Settings Tab allows you to configure advanced settings for policies](/downloads/zia/policies/url-filtering/configuring-advanced-policy-settings/Advanced_Policy_Settings_CoPilot.png)