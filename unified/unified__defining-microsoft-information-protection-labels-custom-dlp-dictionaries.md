# Defining Microsoft Information Protection Labels for Custom DLP Dictionaries
Source: https://help.zscaler.com/unified/defining-microsoft-information-protection-labels-custom-dlp-dictionaries
PDF: https://help.zscaler.com/pdf/com/en/1493126.pdf

You can add Microsoft Information Protection (MIP) labels to custom DLP dictionaries. To learn more, see [Adding Custom DLP Dictionaries](/unified/adding-custom-dlp-dictionaries).
Before you can add MIP labels to a custom dictionary, you must add a MIP account in the Admin Portal and retrieve the MIP labels from Microsoft to the MIP account. To learn more, see [Adding a MIP Account](/unified/adding-mip-account) and [Retrieving MIP Labels from Microsoft to the MIP Account](/unified/retrieving-mip-labels-microsoft-mip-account).
To define MIP labels for custom DLP dictionaries:
- Go to **Policies > Data Protection > Common Resources > Dictionaries & Engines**.
- Click **Add DLP Dictionary** or click the **Edit** icon next to an existing Microsoft Information Protection type dictionary.
The **Add/Edit DLP Dictionary** window appears.
- In the **Add DLP Dictionary** window, in the **Dictionary Type** field, select **Microsoft Information Protection (MIP)**. In the **Edit DLP Dictionary** window, the **Dictionary Type** of **Microsoft Information Protection (MIP)** is displayed and cannot be changed.
- In the **Match On** table, select the labels you want to use for the dictionary. A maximum of 256 labels can be selected for each custom dictionary. You can't select deleted labels, which appear with a strikethrough line. Any labels that have been deleted on Azure will display with a strikethrough line in this window.
[See image.](#MIP_Labels_Selected)
- Click **Save** and activate the change.
[][![Selecting MIP Labels on the Add DLP Dictionary window in the ZIA Admin Portal](/downloads/zia/policies/data-loss-prevention/dlp-dictionaries-engines/defining-microsoft-information-protection-labels-custom-dlp-dictionaries-draft/ZIA-Add-DLP-Dictionary-MIP-Labels-Selected.png?1651247561)
]