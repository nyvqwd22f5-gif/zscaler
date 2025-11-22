# Editing Predefined DLP Dictionaries
Source: https://help.zscaler.com/zia/editing-predefined-dlp-dictionaries
PDF: https://help.zscaler.com/pdf/com/en/1400071.pdf

Modifying a predefined Data Loss Prevention (DLP) dictionary is one of the tasks you can complete when configuring DLP policy rules. To learn more, see [Configuring DLP Policy Rules with Content Inspection](/zia/how-do-i-configure-policy-using-zscaler-dlp-engines).
You can use the predefined DLP dictionaries as is, or modify them to suit your needs. To learn more, see [Understanding Predefined DLP Dictionaries](/zia/understanding-predefined-dlp-dictionaries).
To edit a predefined DLP dictionary:
- Go to **Administration** > **DLP Dictionaries & Engines**.
- Locate the predefined dictionary and click the **Edit **icon.
The **Edit DLP Dictionary** window appears.
- In the **Edit DLP Dictionary** window:
- **Confidence Score Threshold**: Choose a value of **Low**, **Medium**, or **High**. To learn about configuring the [Confidence Score Threshold](#confidence) for a specific dictionary, see [Understanding Predefined DLP Dictionaires](/zia/understanding-predefined-dlp-dictionaries).
- **Proximity Length**: This field appears only when the dictionary’s **Confidence Score Threshold** is **High**, if applicable. The proximity length defines how close a high confidence phrase must be to an instance of the pattern (that the dictionary detects) to count as a match. The phrase can be located in any direction from the pattern within the document. Enter a value from 0-10,000 bytes. A proximity length of 0 disables this option (i.e., the phrase can be any distance from the pattern).
For example, you configure a proximity length of 50 bytes for the Credit Cards dictionary. With this dictionary, the DLP policy detects a document containing the phrase “Amex” within 30 bytes right of a credit card number and counts this transaction as a match.
- **Default High Confidence Phrases**: This field only appears when the dictionary’s **Confidence Score Threshold** is **High**, if applicable. This field displays all of Zscaler’s default high confidence phrases that the dictionary matches when scanning content.
- **Custom High Confidence Phrases**: This field only appears when the dictionary’s **Confidence Score Threshold** is **High**, if applicable. Enter up to 256 custom phrases you want the dictionary to match in addition to its default phrases when scanning content. You must enter phrases one at a time (i.e., one phrase per line).
- [General Guidelines for Phrases](#phrases-guidelines)
- **BIN Number**: This field appears only for the predefined credit card dictionary or its clones. Specify whether to include or exclude specific Bank Identification Numbers (BIN), then enter up to 512 BIN values. You must enter numbers one at a time (i.e., one number per line).
[See image.](#bin-number-image)
- **Social Security Numbers**: This field appears only for the predefined Social Security Numbers (US) dictionary or its clones. Specify whether to include or exclude specific Social Security numbers, then enter up to 512 values. You must enter numbers one at a time (i.e., one number per line).
[See image.](#ssn-include-exclude-image)
- Click **Save** and [activate the change](/zia/saving-and-activating-changes-admin-portal).
You can also add a custom dictionary. Any combination of predefined and custom dictionaries can be added to a DLP engine, which is what you must reference when creating DLP policies. To learn more, see [Adding Custom DLP Dictionaries](/zia/adding-custom-dlp-dictionary) and [About DLP Engines](/zia/about-dlp-engines).
Configuring the Confidence Score Threshold[]
Depending on the predefined DLP dictionary, you can edit the dictionary and modify the Confidence Score Threshold. For this setting, you can choose a value of Low, Medium, or High.
For dictionaries where you can specify the Confidence Score Threshold, a lower confidence score threshold means the dictionary is more aggressive in identifying violations and requires less matching content to be found before it triggers. Conversely, a higher confidence score threshold means that the dictionary needs more exact format and verification requirements to be met for matching content, and that it also might need more instances of matching content to be found before it triggers.
[]![Editing a predefined Data Loss Prevention (DLP) dictionary for Zscaler Internet Access (ZIA)](/downloads/zia/policies/data-loss-prevention/editing-predefined-dlp-dictionaries/ZIA-DLP-BIN-number-Include-Exclude.png)
[]![Editing a predefined Data Loss Prevention (DLP) dictionary for Zscaler Internet Access (ZIA)](/downloads/zia/policies/data-loss-prevention/editing-predefined-dlp-dictionaries/ZIA-DLP-SSN-US-Dictionary-Include-Exclude.png)
- []Each phrase can contain a minimum of 3 bytes and a maximum of 128 bytes.
- Dictionary phrase-matching is not case-sensitive and ignores punctuation.
- You can place quotes around phrases to specify that the dictionary only detects phrases that exactly match the phrase in the order given within the quotes.
The Zscaler service uses fuzzy matching techniques to ensure that phrases do not go undetected by dictionaries because of capitalization or spacing discrepancies and the existence of noise words (such as spurious words or HTML tags) between words. For example, the configured phrase “security service” would match the text “security <b>service</b>”.
Sometimes this fuzzy matching results in matching phrases from an irrelevant context and can cause false positives. In such cases, quotes or double quotes can be placed around the words of a phrase to disable fuzzy matching and match only the phrase within the quotes. Zscaler then ignores the different types of whitespace between the words. For example, “security service” matches “security-service,” “security,service,” and other such unrelated phrases.