# Cloning Predefined DLP Dictionaries
Source: https://help.zscaler.com/unified/cloning-predefined-dlp-dictionaries
PDF: https://help.zscaler.com/pdf/com/en/1493101.pdf

Cloning a predefined DLP dictionary allows you to easily leverage an existing dictionary for a different purpose when [configuring DLP policy rules](/unified/configuring-dlp-policy-rules-content-inspection). You can use clones of the same dictionary with different Confidence Score Thresholds, as well as with different dictionary-specific parameters. For example, suppose you want to use one dictionary to look more aggressively for [Bank Identification Numbers (BIN)](#bin-number), and another dictionary to look less aggressively for other credit card data. In that scenario, you can clone the predefined Credit Card dictionary, and then add BIN numbers to the clone, with a Confidence Score Threshold of Medium. In the existing predefined Credit Card dictionary, you can leave out BIN numbers and set the Confidence Score Threshold to High.
The Zscaler service supports cloning identification-based predefined dictionaries (e.g., Credit Cards, Social Security Numbers, National Identification Numbers, etc.). You can create up to 4 clones from a predefined dictionary.
To clone a predefined DLP dictionary:
- Go to **Policies > Data Protection > Common Resources > Dictionaries & Engines**.
-
Locate the predefined dictionary and click the **Clone **icon.
The **Clone DLP Dictionary** window appears.
[See image.](#cloning-dlp-dictionaries)
- In the **Clone DLP Dictionary** window:
- **Name**: Enter a name for the cloned dictionary.
- **Confidence Score Threshold**: Choose a value of **Low**, **Medium**, or **High**. To learn about configuring the Confidence Score Threshold for a specific dictionary, see [Understanding Predefined DLP Dictionaries](/unified/understanding-predefined-dlp-dictionaries).
-
**Proximity Length**: This field appears only when the dictionary’s **Confidence Score Threshold** is **High**, if applicable. The proximity length defines how close a high confidence phrase must be to an instance of the pattern (that the dictionary detects) to count as a match. The phrase can be located in any direction from the pattern within the document. Enter a value from 0-10,000 bytes. A proximity length of 0 disables this option (i.e., the phrase can be any distance from the pattern).
For example, you configure a proximity length of 50 bytes for the Credit Cards dictionary. With this dictionary, the DLP policy detects a document containing the phrase “Amex” within 30 bytes right of a credit card number and counts this transaction as a match.
- **High Confidence Phrases**: This field only appears when the dictionary’s **Confidence Score Threshold** is **High**, if applicable. This field displays all of Zscaler’s default high confidence phrases that the dictionary matches when scanning content.
- **Custom High Confidence Phrases**: This field only appears when the dictionary’s **Confidence Score Threshold** is **High**, if applicable. Enter up to 256 custom phrases you want the dictionary to match in addition to its default phrases when scanning content. You must enter phrases one at a time (i.e., one phrase per line).
- [General Guidelines for Phrases](#phrases-guidelines)
- []**BIN Number**: This field appears only for the predefined credit card dictionary or its clones. Specify whether to include or exclude specific BIN numbers, then enter up to 512 BIN values. You must enter numbers one at a time (i.e., one number per line).
[See image.](#bin-number-image)
- **Social Security Numbers**: This field appears only for the predefined Social Security Numbers (US) dictionary or its clones. Specify whether to include or exclude specific Social Security numbers, then enter up to 512 values. You must enter numbers one at a time (i.e., one number per line).
[See image.](#ssn-include-exclude-image)
- (Optional) For **Description**, enter any additional notes or information. The description cannot exceed 255 characters.
- Click **Save** and activate the change.
Any combination of cloned, predefined, and custom dictionaries can be added to a DLP engine, which is what you must reference when creating DLP policies. To learn more, see [Adding Custom DLP Dictionaries](/unified/adding-custom-dlp-dictionaries) and [About DLP Engines](/unified/about-dlp-engines).
[]![Editing a predefined Data Loss Prevention (DLP) dictionary for Zscaler Internet Access (ZIA)](/downloads/zia/policies/data-loss-prevention/cloning-predefined-dlp-dictionaries/ZIA-DLP-Clone-BIN-number-Include-Exclude.png)
[]![Editing a predefined Data Loss Prevention (DLP) dictionary for Zscaler Internet Access (ZIA)](/downloads/zia/policies/data-loss-prevention/cloning-predefined-dlp-dictionaries/ZIA-DLP-Clone-SSN-US-Dictionary-Include-Exclude.png)
[]![Creating a clone of a predefined Data Loss Prevention (DLP) dictionary for Zscaler Internet Access (ZIA)](/downloads/zia/policies/data-loss-prevention/dlp-dictionaries-engines/cloning-predefined-dlp-dictionaries/ZIA-Clone-Icon-Open-Clone-Window.png)
- []Each phrase can contain a minimum of 3 bytes and a maximum of 128 bytes.
- Dictionary phrase-matching is not case-sensitive and ignores punctuation.
-
You can place quotes around phrases to specify that the dictionary only detects phrases that exactly match the phrase in the order given within the quotes.
The Zscaler service uses fuzzy matching techniques to ensure that phrases do not go undetected by dictionaries because of capitalization or spacing discrepancies and the existence of noise words (such as spurious words or HTML tags) between words. For example, the configured phrase “security service” would match the text “security <b>service</b>”.
Sometimes this fuzzy matching results in matching phrases from an irrelevant context and can cause false positives. In such cases, quotes or double quotes can be placed around the words of a phrase to disable fuzzy matching and match only the phrase within the quotes. Zscaler then ignores the different types of whitespace between the words. For example, “security service” matches “security-service,” “security,service,” and other such unrelated phrases.