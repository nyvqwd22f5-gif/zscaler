# Adding & Editing Redaction Profiles
Source: https://help.zscaler.com/zia/adding-editing-redaction-profiles
PDF: https://help.zscaler.com/pdf/com/en/1529359.pdf

You can use redaction profiles as part of your SaaS Security Data at Rest Scanning Data Loss Prevention (DLP) policy to hide sensitive content that triggers policy rules. When sensitive content triggers a SaaS Security Data at Rest Scanning DLP rule, the Zscaler service uses the redaction profile associated with the policy rule to replace the content you want to protect with asterisk (`*`) or hash (`#`) characters. The Zscaler service supports redaction profiles for the following file types:
- [Supported File Types for Redaction Profiles](#Supported-Redaction-Filetypes)
Adding a Redaction Profile
- Go to **Administration **>** Rights Management > Redaction**.
- Click **Add Profile**.
The **Add Redaction Profile** window opens.
- In the **Add Redaction Profile** window, specify settings for the redaction profile:
- **Profile Name**: Enter a name of up to 128 characters for the redaction profile.
- **Use Asterisks to Redact**: Select this option to use asterisk characters (`*`) to hide sensitive data.
- **Use Hash Signs to Redact**: Select this option to use hash characters (`#`) to hide sensitive data.
[See image.](#add-redaction-profile-dialog)
- Click **Save** and [activate the change](/zia/saving-and-activating-changes-admin-portal).
[]Editing a Redaction Profile
- Go to **Administration **>** Rights Management > Redaction**.
- Locate the redaction profile in the list, then click the **Edit** icon.
The **Edit Redaction Profile** window opens.
- In the **Edit Redaction Profile** window, specify settings for the redaction profile:
- **Profile Name**: Enter a name of up to 128 characters for the redaction profile.
- **Use Asterisks to Redact**: Select this option to use asterisk characters (`*`) to hide sensitive data.
- **Use Hash Signs to Redact**: Select this option to use hash characters (`#`) to hide sensitive data.
[See image.](#edit-redaction-profile-dialog)
- Click **Save** and [activate the change](/zia/saving-and-activating-changes-admin-portal).
[]
- Archive (.tar, .zip)
- Comma-Separated Value (.csv)
- Microsoft Excel (.xls, .xlsm, .xltm, .xlsx, .xltx)
- Microsoft PowerPoint (.ppt, .pptm, .ppsm, .potm, .pptx, .ppsx, .potx)
- Microsoft Word (.doc, .docm, .dotm, .docx, .dotx)
- PDF (.pdf): Editable and read-only files
- Plain Text (.txt)
- Rich Text (.rtf)
[]![The Add Redaction Profile window in the ZIA Admin Portal](/downloads/zia/policies/saas-security-api/rights-management/ZIA-DLP-Rights-Management-Add-Redaction-Profile.png)
[]![The Edit Redaction Profile window in the ZIA Admin Portal](/downloads/zia/policies/saas-security-api/rights-management/ZIA-DLP-Rights-Management-Edit-Redaction-Profile.png)