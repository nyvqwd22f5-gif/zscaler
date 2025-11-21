# Configuring Custom File Types
Source: https://help.zscaler.com/zia/configuring-custom-file-types
PDF: https://help.zscaler.com/pdf/com/en/1532304.pdf

Creating and configuring custom file types with simple extension-based detections provides you with greater flexibility when creating File Type Control policies. Zscaler-defined file types are detected before custom file types.
To enable this feature, contact Zscaler support.
To add a custom file type:
- Go to **Administration **>** Custom File Types**.
-
In the upper-left corner, click **Add File Type**.
The **Add File Type** window appears.
-
In the **Add File Type **window:
- **Name**: Enter a name for the new custom file type. File type names can only contain alphanumeric characters, underscores, hyphens, periods, parentheses, and spaces.
-
**Extension**: Enter the extension that you want the custom file type to belong to. The maximum extension length is 10 characters.
Existing Zscaler extensions cannot be added to custom file types.
- **Description**: (Optional) Enter additional notes or information.
[See image.](#add-file-type)
- Click **Save** and [activate the change](/zia/saving-and-activating-changes-admin-portal).
After you have created a custom file type, you can add it to your File Type Control policy. To learn more, see [Configuring the File Type Control Policy](/zia/configuring-file-type-control-policy).
[]![Create and add a custom file type in the ZIA Admin Portal](/downloads/tech-pubs-drafts/zia-draft-articles/configuring-custom-file-types-doc-56905/add-custom-file-type-populated.png)