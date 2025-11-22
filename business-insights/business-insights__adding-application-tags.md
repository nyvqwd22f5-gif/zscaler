# Adding Application Tags
Source: https://help.zscaler.com/business-insights/adding-application-tags
PDF: https://help.zscaler.com/pdf/com/en/1526436.pdf

To use tags for applications, you must add tag categories and tags for each category. You can add a maximum of 8 tag categories, and each category can consist of 8 tags.
To add a tag category and tags:
- Go to **Applications **>** Application Settings **>** Tag Management **>** Application Tags**.
-
Click **Create Tag Category**.
The **Create New Tag Category** drawer appears.
- In the **Create New Tag Category **drawer:
- **Name**: Enter a name for the tag category.
- **Color**: Select a color to represent the tag category.
- **Type**: Select **Manual **or **Dynamic**. Manual tagging is individual linking of applications to a tag. Dynamic tagging allows you to configure criteria-based automatic tagging of applications.
- [Manual](#manual)
- [Dynamic](#dynamic)
-
Click **Save**.
The tag category is successfully added. You can view the tag category and its tags on the [Application Tags](/business-insights/about-application-tags) page.
- []**Name**: Enter the tag name.
- **Applications**: Select the applications that you want to link to this tag.
-
Click **Add Tag **to add more tags to the category. Note that only one tag in a category can be linked to an application.
[See image.](#manual-tag)
- []**Criteria**: Select one of the following criteria based on which the applications are automatically linked to a tag:
- Engagement Index
- Active Users
- ACV
- Growth Trend
- Capability
- Sanction Status
- **Name**: Enter the tag name.
- **Operator**: Select an operator to set the threshold to satisfy the criteria as greater than (**>**), greater than or equal to (**>=**), less than (**<**), less than or equal to (**<=**), equal to (**=**), **Is**, **Is not**, **Contains**, or **Not Contains**.
- **Value**: Enter the value for the selected criteria.
For example, the following GIF shows how to configure a dynamic tag category (Active Users 500) for linking applications that have less than 500 active users to the Low Users tag, and more than or equal to 500 active users to the High Users tag.
[See image.](#dynamic-gif)
[]![Dynamic Tags GIF](/downloads/Business-Insights-Dynamic-Application-Tag-example.gif)
[]![Manual Tag fields in the Add NewTag Category drawer](/downloads/Business-Insights-Application-Tags-Manual.png)