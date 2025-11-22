# Defining IDM Match Accuracy for Custom DLP Dictionaries
Source: https://help.zscaler.com/zia/defining-idm-match-accuracy-custom-dlp-dictionaries
PDF: https://help.zscaler.com/pdf/com/en/1402031.pdf

You can add Indexed Document Match (IDM) templates to custom Data Loss Prevention (DLP) dictionaries that represent critical documents that you want to protect in your organization. When adding an IDM template, you must also choose the match accuracy level for the template in the dictionary. To learn more, see [Creating an Indexed Document Match Template](/zia/creating-indexed-document-match-template) and [Adding Custom DLP Dictionaries](/zia/adding-custom-dlp-dictionary).
To add an IDM template:
- Go to **Administration** > **DLP Dictionaries & Engines**.
- On the **DLP Dictionaries** tab, click **Add DLP Dictionary** or click the **Edit** icon for an existing dictionary.
The **Add/Edit DLP Dictionary** window appears.
- In the **Add/Edit DLP Dictionary** window:
- From **Dictionary Type**, choose **Indexed Document Match**.
- Select **Yes** for the **Exclude 100% Match** option if you do not want Zscaler to trigger the dictionary for documents that are a 100% match of already-indexed documents.
- From the **Index Template**, select the IDM templates you want to use for the dictionary.
- Choose the **Match Accuracy** for the IDM templates you selected. This is the level of accuracy (i.e., the percentage of similarity) that a user-uploaded document must meet to count as a match for an indexed document.
- **Low**: Zscaler detects a low-accuracy match when one of the following occurs:
- A user-uploaded document matches at least 25% of an indexed document.
- An indexed document matches at least 50% of a user-uploaded document.
- **Medium**: Zscaler detects a medium-accuracy match when one of the following occurs:
- A user-uploaded document matches at least 50% of an indexed document.
- An indexed document matches at least 75% of a user-uploaded document.
- **High**: Zscaler detects a high-accuracy match when a user-uploaded document matches at least 75% of an indexed document.
![Defining the Match Accuracy for selected Indexed Document Match templates](/downloads/zia/policies/data-loss-prevention/dlp-indexed-document-match/defining-idm-match-accuracy-custom-dlp-dictionaries/ZIA-DLP-Dictionary-IDM-Match-Accuracy-exclude-100-match.png)
- Click **Save** and [activate the change](/zia/saving-and-activating-changes-admin-portal).