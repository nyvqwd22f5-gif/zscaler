# Defining Exact Data Match Fields for Custom DLP Dictionaries
Source: https://help.zscaler.com/unified/defining-exact-data-match-fields-custom-dlp-dictionaries
PDF: https://help.zscaler.com/pdf/com/en/1493241.pdf

You can add Exact Data Match (EDM) index templates and fields to custom DLP dictionaries that represent content you want to protect in your organization. To learn more, see [Adding Custom DLP Dictionaries](/unified/adding-custom-dlp-dictionaries).
Before you can add EDM fields to a custom dictionary, you must create and submit an EDM index template that defines your data. To learn more, see [Creating an Exact Data Match Template](/unified/creating-exact-data-match-template).
You can configure EDM to function without primary or secondary fields. To learn more, see [Configuring DLP Advanced Settings](/unified/configuring-dlp-advanced-settings).
To add Exact Data Match templates and fields:
- Go to **Policies > Data Protection > Common Resources > Dictionaries & Engines**.
- Click **Add DLP Dictionary** or click the **Edit **icon for an existing dictionary.
The **Add/Edit DLP Dictionary **window appears.
- In the **Add/Edit DLP Dictionary** window:
- From the **Data Template** drop-down menu select the EDM template you want to use for the dictionary.
[See image.](#EDM0)
- Select a **Primary Field** you want the dictionary to match against when scanning content.
[See image.](#EDM1)
- Select any **Secondary Fields** you want the dictionary to match against when scanning content, if the dictionary detects a valid match for the Primary Field.
[See image.](#EDM2)
The drop-down menu lists all of the other data fields that were defined for the EDM template. If more than one Primary Field was defined, but was not selected in the previous step, it will appear as a Secondary Field option.
[See image.](#EDM3)
- Select one of the following options for the **Secondary Match On** drop-down menu:
- **None**: The dictionary only needs to match against the Primary Field, no Secondary Fields will be validated
- **Match at Least 1 from Secondary Fields**: The dictionary needs to match against the Primary Field and at least one Secondary Field
- **Match at Least 2 from Secondary Fields**: The dictionary needs to match against the Primary Field and at least two Secondary Fields
- **All Fields**: The dictionary needs to match against the Primary Fields and all Secondary Fields
[See image.](#EDM4)
- (Optional) If you want to apply fields from another EDM template to this dictionary, click **Add Template** and repeat steps a through e.
- Click **Save** and activate the change.
[]![The Data Template field for Zscaler DLP dictionaries](/downloads/zia/policies/data-loss-prevention/dlp-exact-data-match/defining-exact-data-match-fields-custom-dlp-dictionaries/ZIA-EDM-Data-Template.png)
[]![The Primary Field for Zscaler DLP dictionaries](/downloads/zia/policies/data-loss-prevention/dlp-exact-data-match/defining-exact-data-match-fields-custom-dlp-dictionaries/ZIA-EDM-Selecting-Primary-Field.png)
[]![The Secondary Fields for Zscaler DLP dictionaries](/downloads/zia/policies/data-loss-prevention/dlp-exact-data-match/defining-exact-data-match-fields-custom-dlp-dictionaries/ZIA-EDM-Dictionary-Secondary-Fields.png)
[]![The Secondary Fields menu for Zscaler DLP dictionaries](/downloads/zia/policies/data-loss-prevention/dlp-exact-data-match/defining-exact-data-match-fields-custom-dlp-dictionaries/ZIA-EDM-Selecting-Secondary-Fields.png)
[]![The Secondary Match On menu for Zscaler DLP dictionaries](/downloads/zia/policies/data-loss-prevention/dlp-exact-data-match/defining-exact-data-match-fields-custom-dlp-dictionaries/ZIA-EDM-Selecting-Secondary-Match-On.png)