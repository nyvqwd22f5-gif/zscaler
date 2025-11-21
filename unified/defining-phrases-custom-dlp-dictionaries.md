# Defining Phrases for Custom DLP Dictionaries
Source: https://help.zscaler.com/unified/defining-phrases-custom-dlp-dictionaries
PDF: https://help.zscaler.com/pdf/com/en/1493116.pdf

[]You can add phrases to your custom dictionaries that represent content you want to protect for your organization. To learn more, see [Adding Custom DLP Dictionaries](/unified/adding-custom-dlp-dictionaries).
General guidelines for phrases include the following:
- A dictionary can contain up to 512 phrases.
- Each phrase can contain a minimum of 3 bytes and a maximum of 256 bytes.
- Dictionary phrase-matching is not case-sensitive and ignores punctuation.
- You can place quotes around phrases to specify that the dictionary only detects phrases that exactly match the phrase in the order given within the quotes.
-
To enable matching of Unicode phrases when they are adjacent to other characters with no delimiters in between, check the Unicode checkbox. To learn more, see [Adding Custom DLP Dictionaries](/unified/adding-custom-dlp-dictionaries).
The Zscaler service uses fuzzy matching techniques to ensure that phrases do not go undetected by dictionaries because of capitalization or spacing discrepancies and the existence of noise words (e.g., spurious words or HTML tags) between words. For example, the configured phrase “security service” would match the text “security <b>service</b>”.
Sometimes this fuzzy matching results in matching phrases from an irrelevant context and can cause false positives. In such cases, quotes or double quotes can be placed around the words of a phrase to disable fuzzy matching and match only the phrase within the quotes. Zscaler then ignores the different types of whitespace between the words. For example, “security service” matches “security-service,” “security,service,” and other such unrelated phrases.
Adding Phrases
To add phrases:
- Go to** Policies > Data Protection > Common Resources > Dictionaries & Engines**.
-
Click** Add DLP Dictionary** or click the **Edit **icon for an existing dictionary.
The **Add/Edit DLP Dictionary** window appears.
- In the **Add/Edit DLP Dictionary** window:
- Enter a **Phrase **you want the dictionary to match when scanning content. You must enter phrases one at a time (i.e., one phrase per line). To learn more, see the preceding [general guidelines for phrases](#AboutPhrases).
- Choose the **Action** the dictionary takes upon detecting valid matches:
- **Count All**: The dictionary counts all matches of the phrase, including identical phrases, toward the match count. For example, you create a dictionary with the phrase “Confidential Information” and choose **Count All**. When the dictionary scans content containing three instances of the phrase “Confidential Information,” it counts all three instances as three matches.
- **Count Unique**: The dictionary counts each unique match of the phrase towards the match count only once, regardless of how many times it appears in the content. For example, you create a dictionary with the phrase “Confidential Information” and choose **Count Unique**. When the dictionary scans content containing three instances of the phrase “Confidential Information,” it counts all three instances as one match.
-
Click the **Add Phrase** icon to add additional lines and the **Delete** icon to remove them.
![Adding or deleting phrases for Zscaler custom DLP dictionaries](/downloads/zia/policies/data-loss-prevention/dlp-dictionaries-engines/defining-phrases-custom-dictionaries/ZIA-DLP-Add-Delete-Phrases.png)
- Click **Save** and activate the change.