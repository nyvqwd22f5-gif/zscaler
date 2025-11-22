# Adding Custom DLP Dictionaries
Source: https://help.zscaler.com/zia/adding-custom-dlp-dictionary
PDF: https://help.zscaler.com/pdf/com/en/1400076.pdf

Adding a custom Data Loss Prevention (DLP) dictionary is one of the tasks you can complete when configuring DLP policy rules. To learn more, see [Configuring Policies Using Zscaler DLP Engines](/zia/how-do-i-configure-policy-using-zscaler-dlp-engines).
For standalone custom dictionaries, you can add Exact Data Match (EDM) index templates, Indexed Document Match (IDM) index templates, Microsoft Information Protection (MIP) labels, or custom phrases and alphanumeric patterns. These represent the content you want to protect, and which the dictionary is to detect.
You can also use Patterns and Phrases dictionaries to create parent dictionaries or sub-dictionaries that allow you to easily create groups of dictionaries for specific tasks or locales.
Parent dictionaries and sub-dictionaries are not supported for Endpoint DLP.
To learn more about the ranges and limitations for custom DLP dictionaries, see [Ranges & Limitations](/zia/ranges-limitations).
To add a custom DLP dictionary:
- Go to **Administration** > **DLP Dictionaries & Engines**.
- Add one of the following dictionary types:
- [Add a Standalone DLP Dictionary](#Standalone)
- [Add a Parent DLP Dictionary or Sub-Dictionary](#Parent-Sub-Dictionary)
- Click **Save** and [activate the change](/zia/saving-and-activating-changes-admin-portal).
You can also [edit](/zia/how-do-i-edit-predefined-dlp-dictionaries) or [clone](/zia/cloning-predefined-dlp-dictionaries) the predefined dictionaries Zscaler provides. Any combination of cloned, predefined, and custom dictionaries can be added to a DLP engine, which is what you must reference when creating DLP policies. To learn more, see [About DLP Engines](/zia/about-dlp-engines).
[]
- Click **Add DLP Dictionary**.
The **Add DLP Dictionary **window appears.
- In the **Add DLP Dictionary** window:
- **Name**: Enter a name for the dictionary.
- **Dictionary Type**: Select a type from the drop-down menu.
- **Exact Data Match**: If selected, the **Exact Data Match** section appears below, where you can select existing EDM templates and add data fields from those templates. To learn more, see [Creating an Exact Data Match Template](/zia/creating-exact-data-match-template) and [Defining Exact Data Match Fields for Custom DLP Dictionaries](/zia/defining-exact-data-match-fields-custom-dlp-dictionaries).
[See image.](#EDM)
- **Indexed Document Match**: If selected, the **Indexed Document Match** section appears below, where you can select existing IDM templates and choose match accuracy levels for those templates. To learn more, see [Creating an Indexed Document Match Template](/zia/creating-indexed-document-match-template) and [Defining IDM Match Accuracy for Custom DLP Dictionaries](/zia/defining-idm-match-accuracy-custom-dlp-dictionaries).
[See image.](#IDM)
- **Microsoft Information Protection (MIP)**: If selected, the MIP labels appear in the table below, where you can select the MIP labels. To learn more, see [Adding a MIP Account](/zia/adding-mip-account) and [Defining Microsoft Protection Labels for Custom DLP Dictionaries](/zia/defining-microsoft-information-protection-labels-custom-dlp-dictionaries).
[See image.](#MIPs)
- **Patterns & Phrases**: If selected, the **Patterns **and **Phrases **sections appear below, where you can add patterns, phrases, and apply actions to them. To enable Unicode phrases defined in the Phrases list to be matched if they are adjacent to other characters without any delimiter in between, select the **Non-delimited Unicode Phrase matching **checkbox. For example, the phrase “クレジットカード” matches “クレジットカードのコピーをください”. Matches happen even when no spaces are detected. To learn more, see [Defining Patterns for Custom DLP Dictionaries](/zia/how-do-i-define-patterns-custom-dictionaries) and [Defining Phrases for Custom DLP Dictionaries](/zia/how-do-i-define-phrases-custom-dictionaries).
[See image.](#PatternsPhrases)
- **Match On**: This is only applicable if you select **Microsoft Information Protection (MIP)** as the **Dictionary Type**. Enter a search term to find an MIP label to add to the custom dictionary.
-
**Match Type**: This is only applicable if you are configuring a Patterns & Phrases type dictionary. Select a **Match Type** from the drop-down menu to configure how the dictionary triggers when matching patterns and phrases.
- **Match Any**: This is the default setting. If selected, the dictionary triggers when a transaction matches any one of the dictionary’s patterns or phrases.
- **Match All**: If selected, the dictionary triggers when a transaction matches all of the dictionary’s patterns and phrases.
- **Match Any Patterns and Any Phrases**: If selected, the dictionary triggers when a transaction matches any one of the dictionary's patterns and any one of the dictionary's phrases. This option requires at least one phrase and one pattern to match.
For custom dictionaries that use patterns with lookaround constructs (also known as zero-length assertions), you must:
- Select **Match Any Patterns and Any Phrases** as the **Match Type**.
- Configure at least one phrase.
- **Description**: (Optional) Enter a description for the dictionary.
- **Enable Proximity**: This is only applicable if you select **Match Any Patterns and Any Phrases** as the **Match Type**. You can enable proximity to define how close a phrase must be to an instance of a pattern to count as a match.
- **Proximity Length**: Defines how close a phrase must be to an instance of the pattern (that the dictionary detects) to count as a match. The phrase can be located in any direction from the pattern within the document. Enter a value from 0–10,000 bytes. A proximity length of 0 disables this option (i.e., the phrase can be any distance from the pattern).
[]![Selecting the Exact Data Match dictionary type](/downloads/zia/policies/data-loss-prevention/dlp-dictionaries-engines/adding-custom-dlp-dictionary/ZIA-Add-DLP-Dictionary-EDM.png)
[]![Selecting the Indexed Document Match dictionary type](/downloads/zia/policies/data-loss-prevention/dlp-dictionaries-engines/adding-custom-dlp-dictionary/ZIA-Add-DLP-Dictionary-IDM-exclude-match.png)
[]![Selecting the Microsoft Information Protection Dictionary Type](/downloads/zia/policies/data-loss-prevention/dlp-dictionaries-engines/adding-custom-dlp-dictionary/ZIA-Add-DLP-Dictionary-MIP-Labels.png)
[]![Patterns & Phrases Dictionary Type](/downloads/zia/policies/data-loss-prevention/adding-custom-dlp-dictionaries/Patterns-Phrases-Checkbox.png)
[]You can use Patterns and Phrases dictionaries to create custom parent dictionaries and sub-dictionaries as a means of easily grouping similar types of dictionaries (i.e., dictionaries for a particular locale). For parent dictionaries, you can define patterns or phrases, or you can leave them blank so that they act simply as a container for sub-dictionaries. The Zscaler service supports only one level of nesting for sub-dictionaries (i.e., sub-dictionaries cannot also be parent dictionaries), and each parent dictionary can contain up to 63 sub-dictionaries. Additionally, parent dictionaries and sub-dictionaries cannot be cloned.
To add a parent dictionary or sub-dictionary:
-
Do one of the following:
- To add a parent dictionary, click **Add DLP Dictionary**.
The **Add DLP Dictionary **window appears.
- To add a sub-dictionary, locate an existing Patterns and Phrases dictionary in the list, then click **Add DLP Sub Dictionary**.
The **Add DLP Sub Dictionary **window appears.
- In the **Add DLP Dictionary** or **Add DLP Sub Dictionary **window:
- **Name**: Enter a name for the dictionary.
-
**Dictionary Type**: Select a type from the drop-down menu.
- **Patterns & Phrases**: If selected, the **Patterns **and **Phrases **sections appear below, where you can add patterns, phrases, and apply actions to them. To enable Unicode phrases defined in the Phrases list to be matched if they are adjacent to other characters without any delimiter in between, select the **Non-delimited Unicode Phrase matching **checkbox. For example, the phrase “クレジットカード” matches “クレジットカードのコピーをください”. Matches happen even when no spaces are detected. To learn more, see [Defining Patterns for Custom DLP Dictionaries](/zia/how-do-i-define-patterns-custom-dictionaries) and [Defining Phrases for Custom DLP Dictionaries](/zia/how-do-i-define-phrases-custom-dictionaries).
[See image.](#PatternsPhrases_parent-sub)
If you don't specify patterns or phrases for a parent dictionary, it acts simply as a container for sub-dictionaries. You must specify at least one pattern or phrase for each sub-dictionary.
-
**Match Type**: This is only applicable if you are configuring a Patterns & Phrases type dictionary. Select a **Match Type** from the drop-down menu to configure how the dictionary triggers when matching patterns and phrases.
- **Match Any**: This is the default setting. If selected, the dictionary triggers when a transaction matches any one of the dictionary’s patterns or phrases.
- **Match All**: If selected, the dictionary triggers when a transaction matches all of the dictionary’s patterns and phrases.
- **Match Any Patterns and Any Phrases**: If selected, the dictionary triggers when a transaction matches any one of the dictionary's patterns and any one of the dictionary's phrases. This option requires at least one phrase and one pattern to match.
For custom dictionaries that use patterns with lookaround constructs (also known as zero-length assertions), you must:
- Select **Match Any Patterns and Any Phrases** as the **Match Type**.
- Configure at least one phrase.
- **Description**: (Optional) Enter a description for the dictionary.
- **Enable Proximity**: This is only applicable if you select **Match Any Patterns and Any Phrases** as the **Match Type**. You can enable proximity to define how close a phrase must be to an instance of a pattern to count as a match.
- **Proximity Length**: Defines how close a phrase must be to an instance of the pattern (that the dictionary detects) to count as a match. The phrase can be located in any direction from the pattern within the document. Enter a value from 0–10,000 bytes. A proximity length of 0 disables this option (i.e., the phrase can be any distance from the pattern).
[]![Patterns & Phrases Dictionary Type](/downloads/zia/policies/data-loss-prevention/adding-custom-dlp-dictionaries/Patterns-Phrases-Checkbox.png)