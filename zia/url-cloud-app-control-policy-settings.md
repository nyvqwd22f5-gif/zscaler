# URL & Cloud App Control Policy Settings
Source: https://help.zscaler.com/zia/url-cloud-app-control-policy-settings

API Reference Guide for the ZIA Cloud Service and Sandbox Submission APIs

**Base URL:** https://zsapi.[zscaler-cloud-name]/api/v1

## `GET /advancedUrlFilterAndCloudAppSettings`

Retrieves information about URL and Cloud App Control advanced policy settings

**Tags:** URL & Cloud App Control Policy Settings
**Consumes:** application/json
**Produces:** application/json
No parameters.

| Code | Description | Schema |
| ---- | ----------- | ------ |
| 200 | Successful Operation | AdvancedUrlFilteringCloudAppOptions |

## `PUT /advancedUrlFilterAndCloudAppSettings`

Updates the URL and Cloud App Control advanced policy settings

**Tags:** URL & Cloud App Control Policy Settings
**Consumes:** application/json
**Produces:** application/json

| Name | In | Type | Required | Description |
| ---- | --- | ---- | -------- | ----------- |
| body | body | AdvancedUrlFilteringCloudAppOptions | No | URL and Cloud Control advanced policy settings |

| Code | Description | Schema |
| ---- | ----------- | ------ |
| 200 | Successful Operation | AdvancedUrlFilteringCloudAppOptions |

## Models
### AdvancedUrlFilteringCloudAppOptions
URL and Cloud App Control advanced policy settings
| Field | Type | Required | Description |
| ----- | ---- | -------- | ----------- |
| blockSkype | boolean | No | A Boolean value indicating whether access to Skype is blocked or not |
| considerEmbeddedSites | boolean | No | A Boolean value that indicates if URL filtering rules must be applied to sites that are translated using translation services or not. For example, when this feature is enabled, if you have a rule that blocks www.gambling.com, and a user translates the page to another language using Google Translate, the service blocks the translated page. |
| enableBlockOverrideForNonAuthUser | boolean | No | A Boolean value indicating if authorized users can temporarily override block action on websites by providing their authentication information |
| enableCIPACompliance | boolean | No | A Boolean value indicating if the predefined CIPA Compliance Rule is enabled or not. To learn more, see [About CIPA Compliance](/zia/about-cipa-compliance). |
| enableChatGptPrompt | boolean | No | A Boolean value indicating if the use of generative AI prompts with ChatGPT by users should be categorized and logged |
| enableClaudePrompt | boolean | No | A Boolean value indicating if the use of generative AI prompts with Claude by users should be categorized and logged |
| enableDeepSeekPrompt | boolean | No | A Boolean value indicating if the use of generative AI prompts with DeepSeek by users should be categorized and logged |
| enableDynamicContentCat | boolean | No | A Boolean value that indicates if dynamic categorization of URLs by analyzing content of uncategorized websites using AI/ML tools is enabled or not. |
| enableGeminiPrompt | boolean | No | A Boolean value indicating if the use of generative AI prompts with Google Gemini by users should be categorized and logged |
| enableGrokPrompt | boolean | No | A Boolean value indicating if the use of generative AI prompts with Grok by users should be categorized and logged |
| enableMetaPrompt | boolean | No | A Boolean value indicating if the use of generative AI prompts with Meta AI by users should be categorized and logged |
| enableMicrosoftCoPilotPrompt | boolean | No | A Boolean value indicating if the use of generative AI prompts with Microsoft Copilot by users should be categorized and logged |
| enableMistralAIPrompt | boolean | No | A Boolean value indicating if the use of generative AI prompts with Mistral by users should be categorized and logged |
| enableMsftO365 | boolean | No | A Boolean value indicating if the Zscaler service is allowed to permit secure local breakout for Office 365 traffic automatically without any manual configuration needed. Enabling this option turns off SSL Interception for all Office 365 destinations as per Microsoft's recommendation. If you want to continue using existing granular controls for Office 365, disable this option and enable preexisting configuration. To learn more, see [About Microsoft One Click Options](/zia/about-microsoft-one-click-options). |
| enableNewlyRegisteredDomains | boolean | No | A Boolean value indicating whether newly registered and observed domains that are identified within hours of going live are allowed or blocked |
| enableOffice365 | boolean | No | A Boolean value that enables or disables Microsoft Office 365 configuration. If you want to continue using existing granular controls for Office 365, then it is recommended to turn off the **enableMsftO365** option and enable this option instead. This is a legacy option used for backward compatibility. |
| enablePOEPrompt | boolean | No | A Boolean value indicating if the use of generative AI prompts with Poe by users should be categorized and logged |
| enablePerPlexityPrompt | boolean | No | A Boolean value indicating if the use of generative AI prompts with Perplexity by users should be categorized and logged |
| enableUcaasLogMeIn | boolean | No | A Boolean value indicating if the Zscaler service is allowed to automatically permit secure local breakout for GoTo traffic, without any manual configuration needed. When enabled, this option turns off SSL interception for all GoTo destinations. To continue using existing granular controls for GoTo traffic, disable this option and enable Cloud Application and Firewall Network Application policies accordingly. |
| enableUcaasRingCentral | boolean | No | A Boolean value indicating if the Zscaler service is allowed to automatically permit secure local breakout for RingCentral traffic, without any manual configuration needed. When enabled, this option turns off SSL interception for all RingCentral destinations. To continue using existing granular controls for RingCentral traffic, disable this option and enable Cloud Application and Firewall Network Application policies accordingly. |
| enableUcaasTalkdesk | boolean | No | A Boolean value indicating if the Zscaler service is allowed to automatically permit secure local breakout for Talkdesk traffic, with minimal or no manual configuration needed. When enabled, this option turns off SSL interception for all Talkdesk destinations. To continue using existing granular controls for Talkdesk traffic, disable this option and enable Cloud Application, DNS, and Firewall Network Application policies accordingly. |
| enableUcaasWebex | boolean | No | A Boolean value indicating if the Zscaler service is allowed to automatically permit secure local breakout for Webex traffic, without any manual configuration needed. When enabled, this option turns off SSL interception for all Webex destinations. To continue using existing granular controls for Webex traffic, disable this option and enable Cloud Application and Firewall Network Application policies accordingly. |
| enableUcaasZoom | boolean | No | A Boolean value indicating if the Zscaler service is allowed to automatically permit secure local breakout for Zoom traffic, without any manual configuration needed. When enabled, this option turns off SSL interception for all Zoom destinations. To continue using existing granular controls for Zoom traffic, disable this option and enable Cloud Application and Firewall Network Application policies accordingly. |
| enableWriterPrompt | boolean | No | A Boolean value indicating if the use of generative AI prompts with WRITER by users should be categorized and logged |
| enforceSafeSearch | boolean | No | A Boolean value that indicates whether only safe content must be returned for web, image, and video search. Safe search is supported for specific search engines and other platforms.
**Note**: [SSL Inspection](/zia/about-ssl-inspection) must be enabled for this option. To learn more, see [Configuring Advanced Policy Settings](/zia/configuring-advanced-policy-settings). |
| safeSearchApps | array[string] | No | A list of applications for which the SafeSearch enforcement applies. You cannot modify this field when the enforceSafeSearch field is disabled. |
