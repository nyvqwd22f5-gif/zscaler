# Adding Session Attributes
Source: https://help.zscaler.com/zidentity/adding-session-attributes
PDF: https://help.zscaler.com/pdf/com/en/1499291.pdf

You can add session attributes related to the user's session in the ZIdentity Admin Portal, so they can be made available to the subscribed Zscaler services. For example, Zscaler Private Access (ZPA) can use these session attributes and enforce policies based on the session context.
Add Session Attributes
To add a session attribute:
- Go to **Directory **> **Attributes**.
- On the **Attributes** page, select the **Session Attribute** tab.
-
Click **Add Attribute**.
[See image.](#zsl-addattribute)
-
In the **Add Session Attribute** window, add the following details:
- **Attribute Name**: Enter the session attribute name.
- **Display Name**: Enter the display name for the attribute.
- **Description**: Enter a description for the attribute.
- **Data Type**: Select the type of data (String, Integer, Boolean, Date, or Decimal) that must be entered for this attribute.
[See image.](#zsl-attributedetails)
- Click **Save**.
Import a CSV File
You can add multiple session attributes to ZIdentity by importing a CSV file.
To import a CSV file that contains a list of session attributes:
- Go to **Directory **> **Attributes**.
- On the **Attributes** page, select the **Session Attribute** tab.
-
Click **Import CSV**.
[See image.](#zsl-importcsv)
The **Import Attributes** window appears.
-
Click the **Download Sample** link to download the sample template.
[See image.](#zsl-importwin)
- Add the attributes to the CSV file and save it in your local folder.
-
Click **Browse** to locate the saved CSV file, then click **Open**.
The file is uploaded.
-
Click **Import**.
The records are displayed in the **Import Attributes** window.
[See image.](#zsl-importlist)
-
Review the list, then click **Close**.
The attributes are added to the existing list and displayed on the **Attributes** page.
[]![The Session Attribute page showing a list of attributes and annotation around Add Attribute button. ](/downloads/zslogin/administration/attributes/adding-session-attributes/zid-add-attribute-button.png)
[]![The Add Session Attribute window showing empty information fields.](/downloads/zslogin/administration/attributes/adding-session-attributes/zid-add-attribute.png)
[]![The Session Attribute page showing a list of attributes and annotation around Import CSV button. ](/downloads/zslogin/administration/attributes/adding-session-attributes/zid-import-csv-button.png)
[]![The Import Attributes window showing a CSV file and the Download Sample link next to it. ](/downloads/zslogin/administration/attributes/adding-session-attributes/zid-import-attributes.png)
[]![The Import Attributes window showing the results of an imported CSV file. ](/downloads/zidentity/administration/attributes/adding-session-attributes/import-session-attribute.png)