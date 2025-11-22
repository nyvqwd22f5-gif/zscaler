# Recommended URL & Cloud App Control Policy
Source: https://help.zscaler.com/zia/recommended-url-cloud-app-control-policy
PDF: https://help.zscaler.com/pdf/com/en/1399416.pdf

This article contains the recommended policy for URL Filtering and Cloud App Control.
URL Filtering
Zscaler recommends that you [configure](/zia/configuring-url-filtering-policy) the following for [URL Filtering](/zia/about-url-filtering) policy:
- **Rule Order**: Select a Rule Order that is appropriate for your organization. Rules are evaluated in ascending numerical order (Rule 1 before Rule 2, and so on).
- **Rule Status**: Select **Enabled**. Enabled rules are actively enforced.
- **URL Categories**: Select all categories in the **Legal Liability** class. To see which URL categories are in the Legal Liability class, see [About URL Categories](/zia/about-url-categories).
- **HTTP Requests**: Select **All** so that the rule is applied to all HTTP requests.
- **Users**: Select **Any** to apply the rule to all users.
- **Groups**: Select **Any** to apply the rule to all groups.
- **Departments**: Select **Any** to apply the rule to all departments.
- **Locations**: Select **Any** to apply the rule to all locations.
- **Location Groups**: Select **Any** to apply the rule to all location groups.
- **Time**: Select **Always** to apply the rule to all time intervals.
- **Protocols**: Select **HTTP** and **HTTPS** to apply the rule to these two protocols.
- **Action**: Select **Block** to block access to all sites in the selected URL categories.
[]Advanced Policy Settings
Zscaler recommends that you configure the following in the [Advanced Policy Settings](/zia/configuring-advanced-policy-settings).
- **Enable Suspicious New Domains Lookup**:** **Select** Enable**.** **This enables you to use the Newly Registered and Observed Domains [URL category](/zia/about-url-categories) in your URL Filtering policy.
-
**Enable AI/ML based Content Categorization**: Select **Enable**. This enables the service to analyze the content of uncategorized websites using AI/ML tools to check if they belong to one of these URL categories:
| URL Categories | URL Super Categories |
| -------------- | -------------------- |
| Alcohol/Tobacco | Society and Lifestyle |
| Anonymizer | Illegal or Questionable |
| Art/Culture | Society and Lifestyle |
| Blogs | Internet Communication |
| Classifieds | Business and Economy |
| Continuing Education/College | Education |
| Dining/Restaurant | Society and Lifestyle |
| FileHost | Information Technology |
| Finance | Business and Economy |
| Gambling | Gambling |
| Government | Government and Politics |
| Health | Health |
| Job/Employment Search | Job/Employment Search |
| K-12 | Education |
| Online and Other Games | Games |
| Online Auctions | Shopping and Auctions |
| Online Shopping | Shopping and Auctions |
| Other Adult Material | Adult Material |
| Other Drugs | Drugs |
| Other Religion | Religion |
| Radio Stations | Entertainment/Recreation |
| Real Estate | Shopping and Auctions |
| Social Networking | Society and Lifestyle |
| Special Interests/Social Organizations | Special Interests/Social Organizations |
| Sports | Sports |
| Travel | Travel |
| Vehicles | Vehicles |
| Weapons/Bombs | Weapons/Bombs |
| Webmail | Internet Communication |
If the service determines the site belongs in one of those categories, it will categorize those sites and apply your policy accordingly.
- **Enable Embedded Sites Categorization**: Select** Disable**. With this disabled, the service won't enforce the URL Filtering policy for sites that are translated using translation service websites.
-
**Enforce SafeSearch**: Select **Enable**. The following drop-down field appears when this option is enabled:
**SafeSearch Applications**: Select **Any** to return safe content from searches on AOL, Bing Search, Dailymotion, DuckDuckGo, Flickr, Google, Yahoo, and YouTube. [SSL Inspection](/zia/about-ssl-inspection) must be enabled for this option.
- **Enable Creative Commons Search Results**: Select **Enable**. This enables the service to return only Creative Commons search content from certain search engines (e.g., Bing, Google, and Yahoo).
Generative AI Prompt Configuration
When using Amazon Q, be aware that Zscaler and AWS are technology partners. For more information on the Zscaler and Amazon Q integration, see the [Zscaler and AWS Deployment Guide](/zscaler-technology-partners/zscaler-and-aws-deployment-guide).
Zscaler recommends that you configure the following in the [Advanced Policy Settings](/zia/configuring-advanced-policy-settings).
- **ChatGPT**: Select** Enable**.** **This enables the service to categorize and store prompts entered on ChatGPT.
- **Microsoft Copilot**: Select **Enable**. This enables the service to categorize and store prompts entered on Microsoft Copilot.
- **Gemini**: Select** Enable**.** **This enables the service to categorize and store prompts entered on Gemini.
- **Perplexity**: Select** Enable**.** **This enables the service to categorize and store prompts entered on Perplexity.
- **Poe**: Select** Enable**.** **This enables the service to categorize and store prompts entered on Poe.
- **Meta AI**: Select** Enable**.** **This enables the service to categorize and store prompts entered on Meta AI.
- **Writer**: Select** Enable**.** **This enables the service to categorize and store prompts entered on Writer.
- **Deepseek**: Select** Enable**.** **This enables the service to categorize and store prompts entered on Deepseek.
- **Grok AI**: Select** Enable**.** **This enables the service to categorize and store prompts entered on Grok AI.
Cloud App Control
Configure your Cloud App Control policy based on your corporate policy.
[]