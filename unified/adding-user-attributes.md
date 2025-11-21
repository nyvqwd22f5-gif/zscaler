# Adding User Attributes
Source: https://help.zscaler.com/zidentity/adding-user-attributes
PDF: https://help.zscaler.com/pdf/com/en/1499451.pdf

You can add user attributes or import them using a CSV file. You can add up to 128 attributes.
To add a user attribute:
- Go to **Directory **>** Attributes**.
-
On the **Attributes** page, the **User Attribute** tab is displayed by default.
[See image.](#zsl-abutton)
- Click **Add Attribute**.
-
In the **Add Attribute **window:
- **Attribute Name**:** **Enter the name of the attribute that is required to be mapped to an external IdP (e.g., Manager or Organization).
- **Display Name**: Enter the display name for the attribute.
- **Description**: Enter a description for the attribute.
- **Data Type**: Select the type of data (String, Integer, Boolean, Date, or Decimal) the user needs to enter for this attribute.
- **Attribute Required**: Select to mandate the attribute information when [adding a user](/zidentity/adding-users).
[See image.](#add-attributes)
- Click **Save**.
Import a CSV File
You can add multiple user attributes to ZIdentity by importing a CSV file.
To import a CSV file that contains a list of user attributes:
- Go to **Directory **> **Attributes**.
- On the **Attributes** page, the **User Attribute** tab is displayed by default.
-
Click **Import CSV**.
[See image.](#zsl-csvbutton)
-
In the **Import Attributes** window, click the **Download Sample** link to download a sample CSV file.
[See image.](#zsl-importcsv)
- Add the user attributes to the CSV file and save it in your local folder.
- In the **Import Attributes** window, click **Browse File** to locate and upload the saved CSV file.
- If you want to replace the existing list of user attributes, select **Override Existing Entries** checkbox.
-
Click **Import**.
The records are displayed in the **Import Attributes** window.
-
Review the list, then click **Close**.
The attributes are displayed on the **User** **Attributes** tab.
[]![The Add Attribute window showing information fields. ](/downloads/zslogin/administration/attributes/adding-user-attributes/zid-add-attribute.png)
[]![The User Attribute page showing a list of attributes and annotation around Add Attribute button. ](/downloads/zidentity/administration/attributes/adding-user-attributes/add-user-attribute.png)
[]![The Import Attributes window showing a CSV file and the Download Sample link next to it.](/downloads/zslogin/administration/attributes/adding-user-attributes/zid-import-attributes.png)
[]![The User Attribute page showing a list of attributes and annotation around Import CSV button. ](/downloads/zidentity/administration/attributes/adding-user-attributes/import-user-attribute.png)