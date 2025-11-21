# Adding Contract Tags
Source: https://help.zscaler.com/business-insights/adding-contract-tags
PDF: https://help.zscaler.com/pdf/com/en/1526441.pdf

To use tags for contracts, you must add tag categories and tags for each category. You can add a maximum of 8 tag categories, and each category can consist of 8 tags.
To add a tag category and tags:
- Go to **Applications **> **Application Settings **>** Tag Management **>** Contract Tags**.
-
Click **Create Tag Category**.
The **Create New Tag Category** drawer appears.
- In the **Create New Tag Category **drawer:
- **Name**: Enter a name for the tag category.
- **Color**: Select a color to represent the tag category.
- **Type**: Select **Manual **or **Dynamic**. Manual tagging is individual linking of contracts to a tag. Dynamic tagging allows you to configure criteria-based automatic tagging of contracts.
- [Manual](#manual)
- [Dynamic](#dynamic)
-
Click **Save**.
The tag category is successfully added. You can view the tag category and its tags on the [Contract Tags](/business-insights/about-contract-tags) page.
- []**Name**: Enter the tag name.
- **Contracts**: Select the contracts that you want to link to this tag.
-
Click **Add Tag **to add more tags to the category. Note that only one tag in a category can be linked to a contract.
[See image.](#manual-tag)
- []**Criteria**: Select one of the following criteria based on which the contracts are dynamically linked to a tag:
- TCV
- ACV
- Seller Name
- Application
- Vendor
- License
- **Name**: Enter the tag name.
- **Operator**: Select an operator to set the threshold to satisfy the criteria as greater than (**>**), greater than or equal to (**>=**), less than (**<**), less than or equal to (**<=**), equal to (**=**), **Is**, **Is not**, **Contains**, or **Not Contains**.
- **Value**: Enter the value for the selected criteria.
For example, the following GIF shows how to configure a dynamic tag for linking contracts that have an annual contract value (ACV) of $10K or less to the Low ACV tag, and more than $10K to the High ACV tag.
[See image.](#dynamic-gif)
[]![Create New Dynamic Tag Category for Contracts](/downloads/Business-Insights-Dynamic-Tag-example.gif)
[]![Create New Tag Category Drawer for Contract Tags](/downloads/Business-Inisghts-New-Contract-Tag-Drawer.png)