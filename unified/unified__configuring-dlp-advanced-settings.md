# Configuring DLP Advanced Settings
Source: https://help.zscaler.com/unified/configuring-dlp-advanced-settings
PDF: https://help.zscaler.com/pdf/com/en/1493071.pdf

On the DLP Advanced Settings page, you can configure settings for a variety of Data Loss Prevention (DLP) features for the Zscaler service.
To configure DLP advanced settings:
- Go to **Policies** > **Data Protection** > **Common Resources** > **Advanced Settings**.
- Configure as needed:
- [Cloud App & URL Exceptions for DLP](#CloudAppURLExceptions)
- [Exact Data Match](#edmnew)
- [Optical Character Recognition (OCR)](#OCR)
- [Inline DLP Rule Evaluation](#RuleEvaluation)
- [Inspect HTTP Get Requests](#HTTPGetRequest)
- Click **Save** and activate the change.
[]The Zscaler [DLP policy](/unified/about-data-loss-prevention) allows you to create rules to monitor content for specific data being sent to cloud applications and websites.
You can stop the Zscaler service from inspecting specific cloud applications and websites by adding them to the Cloud Apps & URL Exceptions for DLP list.
The exemptions you configure on the DLP Advanced Settings page override the rules you create for the DLP policy. For example, one admin creates an exemption for a cloud application by adding it to the Cloud Apps & URL Exceptions for DLP list. Another admin creates a DLP policy rule to inspect the same application. When users send content to the application, the Zscaler service doesn’t inspect these transactions.
Under **Cloud Apps & URL Exceptions for DLP**, complete the following fields:
-
**Exempted Cloud Applications**: The cloud applications that you want to exempt from DLP evaluation. You can search for and select up to 256 applications.
By default, this field displays the first 100 cloud applications. The subsequent 100 cloud applications are displayed when you click the **Click to see more **link at the bottom of the list. You can repeat this process to view the remaining cloud applications.
[See image.](#cloud-app-field-with-click-see-more)
- **Exempted URLs**: Enter the URLs that you want to exempt from DLP evaluation and click **Add Items**. You can enter multiple entries. Press the **Enter** key after each entry. You can add up to 256 URLs. For guidance on entering URLs, see the [URL format guidelines](/unified/url-format-guidelines).
- **Exempted User-Defined URL Categories**: The [custom URL categories](/unified/configuring-custom-url-categories) you want to exempt from DLP evaluation. You can search for and select up to 256 custom URL categories.
- **Exempt URL Encoded Data**: Enable this option to exempt all URL encoded data from DLP evaluation.
[]![Zscaler DLP Advanced Settings with Click to See More in the Exempted Cloud Applications Field](/downloads/zia/policies/data-loss-prevention/configuring-dlp-advanced-settings/ZIA-DLP-Advanced-Settings-See-More.png)
[]Exact Data Match (EDM) uses index templates with primary and secondary fields by default. This can be changed in the DLP Advanced Settings so that EDM does not use primary or secondary keys or can be configured with EDM Check for Popular Formats.
- **With no primary keys:** If enabled, you select the fields from the template that must match, fields that are optional, and how many optional fields are required to match. Before enabling EDM with no primary keys, all existing EDM schema (templates, dictionaries, engines, and policies) must be deleted or unassigned. New schema with no primary keys functionality can be created after the feature is enabled.
- **Enable EDM Check for Popular Formats**: If enabled, the EDM scans SSN, SIN, and CCN dictionaries for a popular format, and the EDM match only succeeds if the entered format matches the popular data format type. To learn about which data types are supported, see [Creating an EDM template](/unified/creating-exact-data-match-template#data-types).
To configure EDM:
- Delete or unassign any existing EDM templates, dictionaries, engines, and policies.
- Go to **Administration **> **DLP Advanced Settings.**
- Enable EDM
- [Configure EDM with No Primary Keys](#no-primary-keys)
- [Configure EDM Check for Popular Formats](#edm-popular-format-check)
- Select **Save**.
[]
-
Enable **EDM with No Primary Keys**.
[See image.](#EDM-NPK-option)
-
[Create an EDM template](/unified/creating-exact-data-match-template). In the index tool, you do not need to specify primary or secondary fields.
[See image.](#EDM-NPK-Index-tool)
-
[Create a DLP dictionary](/unified/adding-custom-dlp-dictionaries) using the EDM template you created (or any other EDM template with no primary keys). When creating a DLP EDM dictionary with no primary keys enabled, specify **Fields that must Match On**, **Optional Fields to Match On**, and the **Match Type** for optional fields. You must make a selection in at least one of either **Fields that must Match On **or **Optional Fields to Match On**.
[See image.](#EDM-NPK-Dictionary-Settings)
- [Create a DLP engine](/unified/adding-custom-dlp-engines) using any EDM dictionaries with no primary keys.
- [Create policies with content inspection](/unified/configuring-dlp-policy-rules-content-inspection) using any EDM engines with no primary keys.
[]
-
Enable **Check for Popular Formats**.
[See image.](#enable-popular-format)
-
[Create an EDM template](/unified/creating-exact-data-match-template). In the index tool, specify the data type you are enabling.
[See image.](#EDM-NPK-Index-tool2)
-
[Create a DLP dictionary](/unified/adding-custom-dlp-dictionaries) using the EDM template you created. For **Fields that must Match On**, you must specify the **data type** (e.g., SSN, CCN, or CSIN) as the primary field and **Name **as the second field.
[See image.](#EDM-NPK-Dictionary-Settings2)
[]![Zscaler's DLP Advanced Settings window EDM with No Primary Keys option](/downloads/zia/policies/data-loss-prevention/dlp-exact-data-match/configuring-exact-data-match-no-primary-keys/ZIA-Enable-EDM-NPK.png)
[]![Zscaler's Index Tool for EDM with No Primary Keys](/downloads/zia/policies/data-loss-prevention/dlp-exact-data-match/configuring-exact-data-match-no-primary-keys/ZIA-Index-tool-NPK.png)
[]![Zscaler Add DLP Dictionary window with EDM dictionary settings with no primary keys enabled](/downloads/zia/policies/data-loss-prevention/dlp-exact-data-match/configuring-exact-data-match-no-primary-keys/ZIA-NPK-dictionary-settings.png)
[]The Zscaler service allows you to use optical character recognition (OCR) to scan images for sensitive text data as part of your [inline Data Loss Prevention (DLP)](/unified/about-data-loss-prevention), [SaaS Security API DLP](/unified/about-saas-security-api-dlp), and [Outbound Email DLP policies](/unified/what-zscaler-outbound-email-dlp). You configure OCR settings for your organization, and those settings apply to all DLP policies that you create. If OCR options are not enabled, DLP rules don't apply to image files.
DLP engines support OCR scanning of PNG, JPEG, TIFF, and BMP files.
Under **Optical Character Recognition (OCR)**, configure the following settings:
- **Inline DLP**: Enable this option to allow the Zscaler DLP engines to scan images for text content in data in transit. To learn more, see [About Data Loss Prevention](/unified/about-data-loss-prevention).
- **SaaS Security API**: Enable this option to allow the Zscaler DLP engines to scan images for text content in data at rest. To learn more, see [About SaaS Security API DLP](/unified/about-saas-security-api-dlp).
- **Outbound Email DLP**: Enable this option to allow the Zscaler DLP engines to scan images for text content in outbound emails sent to external domains. To learn more, see [What Is Zscaler Outbound Email DLP?](/unified/what-zscaler-outbound-email-dlp)
[]This setting appears only in organizations with Evaluate All Rules mode enabled. To access this feature, contact your Zscaler Account team. To learn more, see [Configuring DLP Policy Rules with Evaluate All Rules Mode Enabled](/unified/configuring-dlp-policy-rules-evaluate-all-rules-mode-enabled).
Under **Inline DLP Rule Evaluation**, specify how DLP engines evaluate the rules you configure:
- **By Rule Order**: Select this option if you want DLP engines to rely on rule order during evaluation. When the engine finds a matching rule, evaluation stops.
- **Evaluate All Rules**: Select this option if you want DLP engines to evaluate all rules. If multiple rules match, the rule engine selects the rule with the most restrictive action.
The evaluation method you select is applied to all inline DLP rules for your organization. If you want to change the evaluation method, you must first delete all existing inline DLP rules.
[]To access this feature, contact your Zscaler Account team.
To enable the User-Defined custom URL category in the policy, you must first go to the **DLP Advanced Settings **page and select which URL category to associate with Inspect HTTP GET Requests. To learn more, see [Configuring DLP Policy Rules with Content Inspection](/unified/configuring-dlp-policy-rules-content-inspection) and [Configuring DLP Policy Rules with Evaluate All Rules Mode Enabled.](/unified/configuring-dlp-policy-rules-evaluate-all-rules-mode-enabled)
To inspect HTTP GET Query Parameters for sensitive data:
-
On the **Custom URL** drop-down menu, select a URL category from the list. To create a custom URL category, see [Configuring Custom URL Categories](/unified/configuring-custom-url-categories).
[See image.](#http-get)
- Click **Save**.
[]
![Enable EDM Check for Popular Formats](/downloads/zia/policies/data-loss-prevention/configuring-dlp-advanced-settings/check-popular-formats.png)
[]![Zscaler's Index Tool for EDM with No Primary Keys](/downloads/zia/policies/data-loss-prevention/dlp-exact-data-match/configuring-exact-data-match-no-primary-keys/ZIA-Index-tool-NPK.png)
[]![Zscaler's Add DLP Dictionary Window with EDM dictionary settings](/downloads/zia/policies/data-loss-prevention/dlp-exact-data-match/configuring-exact-data-match-no-primary-keys/ZIA-NPK-dictionary-settings.png)
[]![Select Custom URL for HTTP GET Requests](/downloads/zia/policies/data-loss-prevention/configuring-dlp-advanced-settings/http-get-request.png)