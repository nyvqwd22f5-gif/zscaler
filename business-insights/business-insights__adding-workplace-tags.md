# Adding Workplace Tags
Source: https://help.zscaler.com/business-insights/adding-workplace-tags
PDF: https://help.zscaler.com/pdf/com/en/1510611.pdf

You can add tag categories and tags in each category, which can be used to link to workplaces. You can add a maximum of 8 tag categories, and each category can consist of 8 tags.
To add a tag category and tags:
- Go to **Workplaces **> **Offices and Locations **> click the drop-down menu under the Tags column for any office >** Manage All Tags**,** **or** Workplace Settings **> **Configured Offices **> click the Tags filter** **> **Manage All Tags**.
-
Click **Create Tag Category**.
The **Create New Tag Category** drawer appears.
- In the **Create New Tag Category **drawer:
- **Name**: Enter a name for the tag category.
- **Color**: Select a color to represent the tag category.
- **Type**: Select **Manual **or **Dynamic**. Manual tagging is individual linking of workplaces to a tag. Dynamic tagging allows you to configure criteria-based automatic tagging of workplaces.
- [Manual](#manual)
- [Dynamic](#dynamic)
-
Click **Save**.
The tag category is successfully added. You can view the tag category and its tags on the [Tag Management](/business-insights/about-tags) page.
- []**Name**: Enter the tag name.
- **Offices**: Select the offices that you want to link to this tag.
-
Click **Add Tag **to add more tags to the category. Note that only one tag in a category can be linked to an office.
[See image.](#manual-tag)
- []**Criteria**: Select one of the following criteria based on which the offices are automatically linked to a tag:
- Assigned Headcounts
- Capacity
- Hotel Desks
- Lease End Date
- Lease Status
- Permanent Desks
- **Name**: Enter the tag name.
- **Operator**: Select an operator to set the threshold to satisfy the criteria as greater than (**>**), greater than or equal to (**>=**), less than (**<**), less than or equal to (**<=**), equal to (**=**), **Contains**, or **Not Contains**.
- **Value**: Enter the value for the selected criteria.
For example, the following GIF shows how to configure a dynamic tag for linking offices that have a capacity of 500 or less to the High Cap tag and more than 500 to the Low Cap tag.
[See image.](#dynamic-gif)
[]![Dynamic Tags GIF](/downloads/business-insights/workplace-insights/workplace-settings/adding-tag-category/Business-Insights-Dynamic-Tag-example.gif)
[]![Manual Tag fields in the Add NewTag Category drawer](/downloads/business-insights/workplace-insights/workplace-settings/adding-tag-categories/Business-Inisghts-Tag-Management-Manual.png)