# Adding Email Notification Templates
Source: https://help.zscaler.com/workflow-automation/adding-email-notification-templates
PDF: https://help.zscaler.com/pdf/com/en/1495191.pdf

[]Workflow Automation allows you to create various email notification templates using the email template builder to send notifications to the DLP admins, managers, approvers, and end users. The email template builder ensures that the email notification template displays properly to all email clients.
To add an email notification template:
-
On the **Notification Template **page:
- **Template Name**: Enter a name for the template.
- **Template Family**: From the drop-down menu, select an existing template family or add a new template family.
- **Type**: From the drop-down menu, select **Email**.
- **Digest**: Enable this option to make this template a digest notification template. This option identifies whether the template is for a digest type of notification (user digest and DLP admin digest) or a non-digest type of notification (user notification and escalation).
- **Source Language**: From the drop-down menu, select a language in which you want to create the notification template. The default language is **English**.
- **Subject Line**: Enter a subject or a short description for the template. This field only supports the default language, English, and has a character limitation of 100.
After you select the template type, the email template builder appears, displaying the following:
- The template design area, which is blank except for a single row with one column. You use this area to create and design the email notification template.
- The Rich Text Editor, which contains all the tools (**Columns**, **Button**, **Divider**, **Heading**, **Text**, **Image**, **Menu**, and **HTML**) that you can use to create the email notification template.
- The Button toolbar, which contains the **Content**,** Blocks**, **Body**, and **Images **buttons. You can use these buttons to navigate within the email template builder.
Using the drag-and-drop capability of these tools, you can configure or modify an email notification template. You can also change the template's structure and style.
[See image.](#add-edit-template-page-adding-template_2)
- In the email template builder, configure the email notification template using one or more of the tools and buttons.
- [Configuring the General Details for the Template Body](#configure-general-details-for-template-body)
- [Adding Rows with Columns](#add-rows-with-columns)
- [Adding Buttons](#add-buttons)
- [Adding Dividers](#add-dividers)
- [Adding Headings](#add-headings)
- [Adding Text](#add-text)
- [Adding Images](#add-images)
- [Adding Menus](#add-menus)
- [Adding HTMLs](#add-htmls)
- [Moving Rows and Column Content](#moving-rows-content)
- [Deleting Rows and Column Content](#delete-rows-content)
- [Duplicating Rows and Column Content](#duplicate-rows-content)
- (Optional) Click **Save as Draft**. You can come back later and continue to work on the template design. The status of the template is **Draft**.
- (Optional) Click **Translate** to translate the newly created template into a different language. The **Translate **window appears.
- In the **Translate** window, from the **Translate To** drop-down menu, select a language to which you want to translate the template.
- Click **Preview** to view the translated template. The template displays in the selected language.
- (Optional) To revert the template to the original language, click **Reset**. Doing so also reverts any changes made after translation.
- Click **Publish Template**. The template is published, and the status of the template is **Published**. Workflow Automation only uses published templates for its notifications.
[![Viewing the Notification Template page with an empty email template builder. The email template builder displays a template design area, the Rich Text Editor with all the tools, and the button toolbar.](/downloads/workflow-automation/setup/adding-email-notification-templates/WA-Not-Template-PG-Initial-Email-Display-page.png)
][]
[]To configure the general details for the template body:
-
On the email template builder, in the Button toolbar, click **Body**. The Rich Text Editor appears, displaying fields which you can use to configure the general details for the template.
[See image.](#email-builder-body-tab)
-
In the Rich Text Editor, in the **General** section:
- **Text Color**: Select the text color for the template. To select the text color:
- Click the **Text Color** box. The color palette appears.
- In the color palette, select the default text color for the template. By default, when you add text to the template design area using the **Heading**, **Text**,** **or** HTML **tools, the text appears in this color.
- **Background Color**: Select the background color for the template. To select the background color:
- Click the **Background Color** box. The color palette appears.
- In the color palette, select the background color for the template. In the template design area, this background color appears for the template.
- **Content Width**: Enter the width in pixels for all rows in the template. In the template design area, all the template rows appear in this width for the template.
- **Content Alignment**: Select the content alignment for the rows in the template. You can left align or center align the content in a row. In the template design area, the content appears in this alignment for the template.
- **Font Family**: From the drop-down menu, select the font family for the template. Font families include **Arial**, **Helvetica**, and several others. By default, when you add text to the template design area of the page using the **Heading**, **Text**,** **or** HTML **tools, the text appears in this font family. By default, when you add a button or menu using the **Button** or **Menu** tools, the text for these items appears in this font family.
- **Font Weight**: From the drop-down menu, select the font weight for the template. Font weights are **Regular** and **Bold**. By default, when you add text to the template design area of the page using the **Heading**, **Text**,** **or** HTML **tools, the text appears in this font weight. By default, when you add a button or menu using the **Button** or **Menu** tools, the text for these items appears in this font weight.
[See image.](#email-builder-body-tab-general-sect)
-
(Optional) In the **Email Settings** section, enter text in the **Preheader Text** field for the notification email. This text follows the subject line in an email notification that was created using this template.
[See image.](#email-builder-body-email-settings-section)
-
In the **Links** section:
- **Color**: Select the color for the links in the template. To select the color for the links:
- Click the **Color** box. The color palette appears.
- In the color palette, select the default color for the links in the template. By default, when you add a link to the template design area of the page using the **Heading** or **Text** tools, the link appears in this color.
- **Underline**: If you want the links to be underlined in the template, enable this setting. Otherwise, the links are not underlined. By default, when you add a link to the template design area of the page using the **Heading** or **Text** tools, the link appears either underlined or not underlined.
[See image.](#email-builder-body-links-section)
[]![Configuring the general details for the body of an email notification template using the various fields in the General section of the Rich Text Editor](/downloads/workflow-automation/setup/adding-email-notification-templates/WA-Not-Template-PG-Body-Button.png)
[]![ Viewing the General section in the Rich Text Editor. This section contains fields that are used for configuring the body of the email notification template.](/downloads/workflow-automation/setup/adding-email-notification-templates/WA-Email-Template-Builder-Body-Button-General.png)
[]![Viewing the Email Settings section in the Rich Text Editor. This section contains a Preheader Text field that is used for the email notification template.](/downloads/workflow-automation/setup/managing-notification-templates/WA-Not-Template-Page-Body-Button-Email-Settings.png)
[]![Viewing the Links section in the Rich Text Editor. This section contains fields (Color and Underline) that are used for configuring the links within the body of the email notification template.](/downloads/workflow-automation/setup/managing-notification-templates/WA-Not-Template-Page-Body-Button-Links.png)
[]To add rows with columns:
-
On the email template builder, add a row with columns to the template using one of these methods:
- In the Button toolbar, click **Content**. In the Rich Text Editor, click the **Columns** tool, then drag and drop it to the template design area of the email template builder. By default, in the template design area, a row appears with one column.
- In the Button toolbar, click **Blocks**. In the Rich Text Editor, click on a row with one or more columns, then drag and drop it to the template design area of the email template builder. Depending on your selection, in the template design area, a row appears with one or more columns.
- In the template design area, click the **Add Row** icon at the bottom of any row. By default, in the template design area, a row appears with one column.
[See image.](#email-builder-columns-add)
On the right side of the email template builder, the Rich Text Editor for the row also appears. The Rich Text Editor displays the **Desktop** tab for the row, and it also displays a column tab for each column in the row in the **Column Properties** section.
[See image.](#email-builder-row-dialog-window-columns-sect)
- Configure the desktop version of the row for the template:
-
In the Rich Text Editor, in the **Columns** section, you can change the number and format of the columns that appear for the row in the template design area. Select one of the number and format options for the column. For example, if you select the three-box column option, then in the template design area three columns appear for the row.
[See image.](#email-builder-columns-columns-section)
-
In the Rich Text Editor, in the **Column Properties** section for each column:
A separate column tab appears for each column in the row. You must add the column properties for each column.
-
**Background Color**: Select the background color for the column. A red slash across the box indicates that a color has not been selected. By default, if you do not select a color, then the column appears in the background color that you defined for the template body. To select the background color:
- Click the **Background Color** box. The color palette appears.
- In the color palette, select the background color for the column in the template. In the template design area, this background color appears for the column.
To learn more, see [Configuring the General Details for the Template Body](#configure-general-details-for-template-body).
-
**Padding**: Set the padding in one of the following ways:
- In the **All Sides** field, enter the number of pixels to pad the column with on all sides.
- Enable **More Options** and enter the number of pixels to pad the **Top**, **Right**, **Left**, and **Bottom** of the column.
In the template design area, this padding appears for the column.
-
**Border**: Configure the border for the column. by doing one of the following:
- To create the same border for all sides:
- In the **All Sides** fields, from the drop-down menu, select the type of border for all sides of the column. Border types are **Solid**, **Dotted**, and **Dashed**.
- Enter the width of the border in pixels for all sides of the column.
- Select the border color for all sides of the column. To select the border color:
- Click the color box. The color palette appears.
- In the color palette, select the border color.
- To create a different border for each side:
- Enable **More Options**. The **Top**, **Right**, **Left**, and **Bottom** fields appear.
- In the **Top**, **Right**, **Left**, and **Bottom** fields, from the drop-down menu, select the type of border for the different sides of the column. Border types are **Solid**, **Dotted**, and **Dashed**.
- Enter the width of the border in pixels for the different sides of the column.
- Select the border color for the different sides of the column. To select the border color:
- Click the color box. The color palette appears.
- In the color palette, select the border color.
In the template design area, this border appears for the column.
[See image.](#email-builder-columns-column-properties-sect)
-
In the Rich Text Editor, in the **Row Properties** section:
-
**Background Color**: Select the background color for the entire row in the template. A red slash across the box indicates that a color has not been selected. By default, if you do not select a color, then the row appears in the background color that you defined for the template body. To select the background color:
- Click the **Background Color** box. The color palette appears.
- In the color palette, select the background color for the entire row in the template. In the template design area, this background color appears for the row.
To learn more, see [Configuring the General Details for the Template Body](#configure-general-details-for-template-body).
-
**Content Background Color**: Select the background color for all the content in the row. A red slash across the box indicates that a color has not been selected. By default, if you do not select a color, then the content appears in the background color that you defined for the template body. To select the content background color:
- Click the **Content Background Color** box. The color palette appears.
- In the color palette, select the background color for all the content in the row. In the template design area, this background color appears for the content in the row.
To learn more, see [Configuring the General Details for the Template Body](#configure-general-details-for-template-body).
- **Background Image**:
- Select the background image for the row by doing one of the following:
- Click **Upload Image** and upload an image. The image you upload appears in the box under the **Background Image** field along with an **Edit Image** button. In the template design area, this image also appears for the row.
- Drop a new image or select a file to upload to the empty box that is displayed under the **Background Image** field. The image you upload appears in the box along with an **Edit Image** button. In the template design area, this image also appears for the row.
- From the **More Images** drop-down menu, select **Stock Photos** and then select an image. The image you select appears in the box under the **Background Image** field along with an **Edit Image** button. In the template design area, this image also appears for the row.
- (Optional) Edit the image. To edit the image, click **Edit Image**. When you click this button, a new edit image window appears, where you can edit the image. By clicking the various buttons on this window, you can apply effects to the image, such as shapes, stickers, filters, and text.
- **Image URL**: Displays the URL for the image you upload or select.
-
**Image Options**:
If you apply a background image to the row, these fields appear.
- **Container Width**: Select the width for the background image in the row. Select **Content**, if you want the image to appear only within the entire content area of the row in the template design area. Select **Full Width**, if you** **want** **the image to appear across the full width of the row in the template design area.
-
**Repeat**: Select whether you want to repeat the image in the row. The following are the repeat options:
- **None**:** **Select** **if you do not want to repeat the image.
- **Repeat**: Select if you want to repeat the image in a grid format.
- **Horizontal**:** **Select if you want to repeat the image horizontally.
- **Vertical**:** **Select if you want to repeat the image vertically.
In the template design area, the repeated images appear in the row.
- **Position**: Select the position of the image in the row. Click the left, right, top, or bottom arrows to position the image in the row or select the **Left** and **Top** percentages from the center for the image position. In the template design area, the image appears in this position.
-
**Padding**: Set the padding in one of the following ways:
- In the **All Sides** field, enter the number of pixels to pad the background image with on all sides.
- Enable **More Options** and enter the number of pixels to pad the **Top**, **Right**, **Left**, and **Bottom** of the image.
In the template design area, this padding appears for the image.
[See image.](#email-builder-columns-row-properties-sect)
-
In the Rich Text Editor, in the **Responsive Design **section, if you want to hide a row design from the desktop version, enable **Hide on Desktop**. In the desktop version of this notification template, this row is hidden.
[See image.](#email-builder-columns-responsive-design-sect)
-
Configure the mobile version of the row for the template:
- In the Rich Text Editor, select the **Mobile** tab. All the settings that you added to the row in the desktop version appear on the mobile version.
- Review all the row settings for the mobile version. The mobile version template size is different from the desktop version template size. So, the mobile version might require some changes from the desktop version.
- (Optional) If necessary, change any of the settings for the mobile version.
[See image.](#email-builder-columns-mobile-tab)
![Video showing how use the email template builder to configure rows with columns for an email notification template](/downloads/workflow-automation/setup/adding-email-notification-templates/WA-Notification-Template-Page-Add-Column-Methods.gif)
[]
[]![Viewing the email template builder with rows and columns added for an email notification template. A row with two columns is highlighted in the design section. In addition, the Desktop tab and Column tab are highlighted in the Rich Text Editor for that row.](/downloads/workflow-automation/setup/adding-email-notification-templates/WA-Not-Template-PG-Add-Column-RichTextEditor.png)
[]![Video showing how use the email template builder to configure rows with one or more columns for an email notification template](/downloads/workflow-automation/setup/adding-email-notification-templates/WA-Notification-Template-Page-Changing-Columns.gif)
[]![Viewing the Column Properties section in the Rich Text Editor for a row with two columns. Tabs are highlighted at the top of the section for each column in the row. The Column Properties section contains fields for Background Color, Padding, and Border.](/downloads/workflow-automation/setup/adding-email-notification-templates/WA-Not-Template-PG-Add-Column-RichTextEditor-Column-Properties.png)
[]![Viewing the Row Properties section in the Rich Text Editor for a row. The Row properties section contains fields for Background Color and Content Background Color. In addition, there are buttons and fields to upload an image for a row.](/downloads/workflow-automation/setup/managing-notification-templates/WA-Not-Template-Page-Add-Column-RichTextEditor-Row-Properties.png)
[]![Viewing the Responsive Design section in the Rich Text Editor for a row. The Responsive Design section contains an option to hide this row on the Desktop version of the email notification template.](/downloads/workflow-automation/setup/managing-notification-templates/WA-Not-Template-Page-Add-Column-RichTextEditor-Resp-Des.png)
[]![Viewing the mobile version of an email notification template that contains a row with multiple columns in the email template builder. The Mobile tab is highlighted on the Rich Text Editor.](/downloads/workflow-automation/setup/adding-email-notification-templates/WA-Not-Template-PG-Add-Column-RichTextEditor-Mobile.png)
[]To add buttons
- On the email template builder, in the Button toolbar, click **Content**. In the Rich Text Editor, click the **Button** tool, then drag and drop it to a column in a row in the template design area of the email template builder. In the template design area, a button placeholder appears with `Button Text`.
- Enter the button text:
- In the template design area, click the button placeholder in the column and row where you dropped the button. In the template design area, a Button toolbar appears. Plus, on the right side of the email template builder, the Rich Text Editor for the button also appears, displaying the **Desktop** tab for the button.
- In the template design area:
- Enter new text to replace `Button Text`.
-
Modify the button text using one or more of the following Button toolbar options:
- Format it using one or more of the format options. Format options are **Bold**, **Italic**, **Underline**, and **Strikethrough**.
- Add merge tags to the button text. From the **Merge Tags** drop-down menu, select a merge tag. Merge tags are:
- **All Incidents Waiting for Feedback Count**
- **Client IP**
- **Current Time**
- **Customer ID**
- **Date**
- **Destination URL**
- **Document Name**
- **High Priority Incidents Waiting for Feedback Count**
- **Hostname or Application**
- **Incident ID**
- **New Incidents Count**
- **Note to the User**
- **Open Incidents Count**
- **Operation**
- **Priority**
- **Severity**
- **State Changes Count**
- **Time**
- **User Name**
- **Violated Policy**
[See image.](#email-builder-button-3)
- Configure the desktop version of the button for the template:
-
(Optional) In the Rich Text Editor, in the **Smart Buttons** section, click **Try it now!** to enhance the quality of your button text using AI.
[See image.](#email-builder-button-content-window-smart-buttons-section)
- In the Rich Text Editor, in the **Action **section, configure one of the following actions for the button:
- Open Website
- **Action Type**: From the drop-down menu, select **Open Website**. The **URL**, **Target**, and **Special Links** fields appear.
- **URL**: Enter the URL for the website.
- **Target**: From the drop-down menu, select where the website opens when the button is clicked. The targets are **New Tab** and **Same Tab**.
-
**Special Links**: (Optional) From the drop-down menu, select a special link. The following are special links:
- **Incident Justification Magic Link**: Redirects the user to the Incident page, where they can view and enter justification details for an incident.
- **Incident Escalation Magic Link**: Redirects the manager or approver to the Incident page, where they can view and enter justification details for an incident.
- **Incident List Page Magic Link**: Redirects the user or DLP admin to the Incident page, where they can view the incidents that require their attention.
After you select a special link, the special link appears in the **URL** field. It replaces the value in the **URL** field.
[See image.](#email-builder-button-content-window-action-section)
- Send Email
- **Action Type**: From the drop-down menu, select **Send Email**. The **Mail To**, **Subject**, and **Body** fields appear.
- **Mail To**: Enter the email address of the recipient who receives the email.
- **Subject**: Enter the subject line for the email.
- **Body**: Enter the body for the email.
- Call Phone Number
- **Action Type**: From the drop-down menu, select **Call Phone Number**. The **Phone** field appears in this section.
- **Phone**: Enter the phone number to call.
-
In the Rich Text Editor, in the **Button Options **section:
- **Background Color**: Select the background color for the button. To select the background color:
- Click the **Background Color** box. The color palette appears.
- In the color palette, select the background color for the button. In the template design area, the background color for the button appears in this color.
- **Text Color**: Select the color for the button text. To select the color:
- Click the **Text Color** box. The color palette appears.
- In the color palette, select the color for the button text. In the template design area, the button text appears in this color.
- **Width**: If you want the button to match the width and height of the column in the row in the template design area, enable **Auto On**.** **If you do not enable auto width, a percentage line toggle appears, and you can adjust the width of the button by percentage. In the template design area, the button appears in this width.
- **Font Family**: From the drop-down menu, select the font family for the button text. Font families include **Arial**, **Helvetica**, and several others. In the template design area, the button text appears in this font family.
- **Font Weight**: From the drop-down menu, select the font weight for the button text. Font weights are **Regular** and **Bold**. In the template design area, the button text appears in this font weight.
- **Font Size**: Enter the font size in pixels for the button text. In the template design area, the button text appears in this font size.
- **Line Height**: Enter the line height percentage for the button text. In the template design area, the button appears in this line height.
- **Letter Spacing**: Enter the letter spacing in pixels for the button text. In the template design area, the button text appears with this letter spacing.
[See image.](#email-builder-button-content-window-button-options-section)
-
In the Rich Text Editor, in the **Spacing **section:
- **Alignment**: Select the alignment for the button in the column. Button alignments are left-aligned, center-aligned, right-aligned, and equal alignment across rows. In the template design area, the button appears in this alignment.
-
**Padding**: Set the padding in one of the following ways:
- In the **All Sides** field, enter the number of pixels to pad the button with on all sides.
- Enable **More Options **and enter the number of pixels to pad the **Top**, **Right**, **Left**, and **Bottom** of the button.
In the template design area, this padding appears for the button.
-
**Border**: Configure the border for the button by doing one of the following;
- To create the same border for all sides:
- In the **All Sides** field, from the drop-down menu, select the type of border for all sides of the button. Border types are **Solid**, **Dotted**, and **Dashed.**
- Enter the width of the border in pixels for all sides of the button.
- Select the border color for all sides of the button. To select the border color:
- Click the color box. The color palette appears.
- In the color palette, select the border color.
- To create a different border for each side:
- Enable **More Options**. The **Top**, **Right**, **Left**, and **Bottom** fields appear.
- In the **Top**, **Right**, **Left**, and **Bottom** fields, from the drop-down menu, select the type of border for the different sides of the button. Border types are **Solid**, **Dotted**, and **Dashed.**
- Enter the width of the border for the different sides of the button.
- Select the color border for the different sides of the button. To select the border color:
- Click the color box. The color palette appears.
- In the color palette, select the border color.
In the template design area, this border appears for the button.
-
**Rounded Border**: Set the rounded border in one of the following ways:
- In the **All Sides** field, enter the number of pixels to round the button border with on all sides for the button.
- Enable **More Options **and enter the number of pixels to round the button border with for the **Top**, **Right**, **Left**, and **Bottom** of the button.
In the template design area, a rounded border appears for the button.
[See image.](#email-builder-button-content-window-spacing-section)
-
In the Rich Text Editor, in the **General **section, set the container padding in one of the following ways:
- In the **All Sides** field, enter the number of pixels to pad the button with on all sides.
- Enable **More Options **and enter the number of pixels to pad the **Top**, **Right**, **Left**, and **Bottom** of the button.
In the template design area, this padding appears for the button.
[See image.](#email-builder-button-content-window-gen-section)
-
In the Rich Text Editor, in the **Responsive Design **section, if you want to hide the button from the desktop version, enable **Hide on Desktop**. In the desktop version of this notification template, the button is hidden.
[See image.](#email-builder-button-content-window-res-des-section)
-
Configure the mobile version of the button for the template:
- In the Rich Text Editor, select the **Mobile** tab. Most of the settings that you added for the button in the desktop version appear for the mobile version.
- Review all the button settings for the mobile version. The mobile version template size is different from the desktop version template size. So, the mobile version might require some changes from the desktop version.
- (Optional) If necessary, change any of the settings for the mobile version.
[See image.](#email-builder-button-content-window-mobile-tab)
[]![Video showing how to use the email template builder to add a button to an email notification template](/downloads/workflow-automation/setup/adding-email-notification-templates/WA-Notification-Template-Page-Add-Button.gif)
[]![Viewing the Smart Buttons section in the Rich Text Editor for a button. The Smart Buttons section contains a Try it Now! button. When you click this button you can get AI based suggestions for your buttons in any tone you want.](/downloads/tech-pubs-drafts/adding-email-notification-templates-doc-55797/WA-Not-Template-PG-Add-Button-RichTextEditor-Smart-Buttons.png)
[]![Viewing the Action section in the Rich Text Editor for a button. The Action section contains fields where you can define the action for the button. You can select to have a button open a website, send an email, or call a phone number.](/downloads/workflow-automation/setup/managing-notification-templates/WA-Not-Template-Page-Add-Button-Rich-Text-Editor-Action.png)
[]![Viewing the Button Options section in the Rich Text Editor for a button. The Button Option section contains multiple fields, such as Background Color, Text Color, Width, Font Family, Font Weight, and Font Size.](/downloads/workflow-automation/setup/adding-email-notification-templates/WA-Not-Template-PG-Add-Button-RichTextEditor-Button-Options.png)
[]![Viewing the Spacing section in the Rich Text Editor for a button. The Spacing section contains fields for Alignment, Padding, Border, and Rounded Border.](/downloads/workflow-automation/setup/adding-email-notification-templates/WA-Not-Template-PG-Add-Button-RichTextEditor-Spacing.png)
[]![Viewing the General section in the Rich Text Editor for a button. The General section contains the Container Padding field.](/downloads/workflow-automation/setup/managing-notification-templates/WA-Not-Template-Page-Add-Button-Rich-Text-Editor-General.png)
[]![Viewing the Responsive Design section in the Rich Text Editor for a button. The Responsive Design section contains an option to hide this button on the Desktop version of the email notification template.](/downloads/workflow-automation/setup/managing-notification-templates/WA-Not-Template-Page-Add-Button-Rich-Text-Editor-Resp-Des.png)
[]![Viewing the mobile version of an email notification template that contains a button in the email template builder. The Mobile tab is highlighted on the Rich Text Editor.](/downloads/workflow-automation/setup/adding-email-notification-templates/WA-Not-Template-PG-Add-Button-RichTextEditor-Mobile.png)
[]To add dividers:
-
On the email template builder, in the Button toolbar, click **Content**. In the Rich Text Editor, click the **Divider** tool, then drag and drop it to a column in a row in the template design area of the email template builder. In the template design area, a divider line appears in the column for the row.
[See image.](#email-builder-divider)
- Configure the desktop version of the divider for the template:
- In the template design area, click the divider in the column and row where you dropped the divider. On the right side of the email template builder, the Rich Text Editor for the divider appears, displaying the **Desktop** tab.
-
In the** **Rich Text Editor, in the **Line **section:
- **Width**: Use the width selection toggle to select the width of the divider across the column.
-
**Line**: Configure the line for the divider using the **Line** fields. To configure the line:
- From the drop-down menu, select the line type for the divider. Line types are **Solid**, **Dashed**, and **Dotted**.
- Select the size of the divider in pixels.
- Select the color for the line. To select the line color:
- Click the color box. The color palette appears.
- In the color palette, select the color for the divider.
In the template design area, the divider appears with this line configuration.
- **Align**: Select the alignment for the divider in the column. Divider alignments are left-aligned, center-aligned, right-aligned, and equal alignment across rows. In the template design area, the divider appears in this alignment.
[See image.](#email-builder-divider-content-window-line-section)
-
In the** **Rich Text Editor, in the **General **section, set the container padding in one of the following ways:
- In the **All Sides** field, enter the number of pixels to pad the divider with on all sides.
- Enable **More Options **and enter the number of pixels to pad the **Top**, **Right**, **Left**, and **Bottom** of the divider.
In the template design area, this padding appears for the divider.
[See image.](#email-builder-divider-content-window-gen-section)
-
In the** **Rich Text Editor, in the **Responsive Design **section, if you want to hide the divider from the desktop version, enable **Hide on Desktop**. In the desktop version of this notification template, this divider is hidden.
[See image.](#email-builder-divider-content-window-res-des-section)
-
Configure the mobile version of the divider for the template:
- In the** **Rich Text Editor, select the **Mobile** tab. A couple of the settings that you added for the divider in the desktop version appear for the mobile version.
- Review all the divider settings for the mobile version. The mobile version template size is different from the desktop version template size. So, the mobile version might require some changes from the desktop version.
- (Optional) If necessary, change any of the settings for the mobile version.
[See image.](#email-builder-divider-content-window-mobile-tab)
[]![Video showing how to use the email template builder to add a divider to an email notification template](/downloads/workflow-automation/setup/adding-email-notification-templates/WA-Notification-Template-Page-Add-Dividers.gif)
[]![Video showing how to use the email template builder to configure a divider for an email notification template](/downloads/workflow-automation/setup/adding-email-notification-templates/WA-Notification-Template-Page-Change-Divider.gif)
[]![Viewing the General section in the Rich Text Editor for a divider. The General section contains the Container Padding field.](/downloads/workflow-automation/setup/adding-email-notification-templates/WA-Not-Template-PG-Add-Divider-RichTextEditor-General.png)
[]![Viewing the Responsive Design section in the Rich Text Editor for a divider. The Responsive Design section contains an option to hide this divider on the Desktop version of the email notification template.](/downloads/workflow-automation/setup/managing-notification-templates/WA-Not-Template-Page-Add-Divider-Rich-Text-Editor-Resp-Des-Section.png)
[]![Viewing the mobile version of an email notification template that contains a divider in the email template builder. The Mobile tab is highlighted on the Rich Text Editor.](/downloads/workflow-automation/setup/adding-email-notification-templates/WA-Not-Template-PG-Add-Divider-RichTextEditor-Mobile.png)
[]To add headings:
- On the email template builder, in the Button toolbar, click **Content**. In the Rich Text Editor, click the **Heading** tool, then drag and drop it to a column in a row in the template design area of the email template builder. In the template design area, the text `Heading` appears in the column for the row. By default, the heading type is an H1.
- Enter the text or value for the heading:
- In the template design area, click the `Heading` text in the column and row where you dropped the heading. In the template design area, a heading toolbar appears. Plus, on the right side of the email template builder, the Rich Text Editor for the heading also appears, displaying the **Desktop** tab for the heading.
- In the template design area:
- Enter new text to replace `Heading`.
-
Modify the new heading using one or more of the following heading toolbar options:
- Format it using one or more of the format options. Format options are **Bold**, **Italic**, **Underline**, **Strikethrough**, **Superscript**, and **Subscript**.
- Enter a link in the heading using the **Insert Link** option. When you click the **Insert Link** option, the **Insert/Edit Link** dialog window appears. In the **Insert/Edit Link** dialog window, configure the link using one of the following options:
- Open Website
- **Action Type**: From the drop-down menu, Select **Open Website**. The **URL**, **Target**, and **Special Links** fields appear.
- **URL**: Enter the URL for the website.
- **Target**: From the drop-down menu, select where the website opens when the link is selected. The targets are **New Tab** and **Same Tab**.
-
(Optional) **Special Links**: From the drop-down menu, select a special link. The following are special links:
- **Incident Justification Magic Link**: Redirects the user to the Incident page, where they can view and enter justification details for an incident.
- **Incident Escalation Magic Link**: Redirects the manager or approver to the Incident page, where they can view and enter justification details for an incident.
- **Incident List Page Magic Link**: Redirects the user or DLP admin to the Incident page, where they can view the incidents that require their attention.
After you select a special link, the special link appears in the **URL** field.
- Click **Save**.
- Send Email
- **Action Type**: From the drop-down menu, select **Send Email**. The **Mail To**, **Subject**, and **Body** fields appear.
- **Mail To**: Enter the email address of the recipient who receives the email.
- **Subject**: Enter the subject line for the email.
- **Body**: Enter the body for the email.
- Click **Save**.
- Call Phone Number
- **Action Type**: From the drop-down menu, select **Call Phone Number**. The **Phone** field appears.
- **Phone**: Enter the phone number to call.
- Click **Save**.
- Add emojis to the heading using the **Emoticons** option.
- Add merge tags to the heading. From the **Merge Tags** drop-down menu, select a merge tag. Merge tags are:
- **All Incidents Waiting for Feedback Count**
- **Client IP**
- **Current Time**
- **Customer ID**
- **Date**
- **Destination URL**
- **Document Name**
- **High Priority Incidents Waiting for Feedback Count**
- **Hostname or Application**
- **Incident ID**
- **New Incidents Count**
- **Note to the User**
- **Open Incidents Count**
- **Operation**
- **Priority**
- **Severity**
- **State Changes Count**
- **Time**
- **User Name**
- **Violated Policy**
[See image.](#email-builder-change-heading)
- Configure the desktop version of the heading for the template:
-
(Optional) In the Rich Text Editor, in the **Smart Headings** section, click **Try it now!** to get AI-based suggestions for your heading in any tone that you want.
[See image.](#email-builder-heading-content-window-smart-head-section)
-
In the Rich Text Editor, in the **Text **section:
- **Heading Type**: Select the type of heading for the heading. The types are **H1**, **H2**, **H3**, and **H4**. In the template design area, the heading appears in this type.
- **Font Family**: From the drop-down menu, select the font family for the heading. Font families include **Arial**, **Helvetica**, and several others. In the template design area, the heading appears in this font family.
- **Font Weight**: From the drop-down menu, select the font weight for the heading. Font weights are **Regular** and **Bold**. In the template design area, the heading appears in this font weight.
- **Font Size**: Enter the font size in pixels for the heading. In the template design area, the heading appears in this font size.
-
**Color**: Select the color for the heading. A red slash across the box indicates that a color has not been selected. By default, if you do not select a color, then the heading appears in the text color that you defined for the template body. To select the color:
- Click the **Color** box. The color palette appears.
- In the color palette, select the color for the heading. In the template design area, the heading appears in this color.
To learn more, see [Configuring the General Details for the Template Body](#configure-general-details-for-template-body).
- **Text Align**: Select the text alignment for the heading in the column. Text alignments are left-aligned, center-aligned, right-aligned, and equal alignment across rows. In the template design area, the heading appears in this alignment.
- **Line Height**: Enter the line height percentage for the heading in the column. In the template design area, the heading appears in this line height.
- **Letter Spacing**: Enter the letter spacing in pixels for the heading text. In the template design area, the heading text appears with this letter spacing.
[See image.](#email-builder-heading-content-window-text-section)
-
In the Rich Text Editor, in the **Links **section:
- **Inherit Body Styles**: If you want the heading links to inherit the link styles you defined for the template body, enable this setting. If you do not enable inherit body styles, the **Color** and **Underline** fields appear in this section. To learn more, see [Configuring the General Details for the Template Body](#configure-general-details-for-template-body).
- **Color**: Select the color for the links. To select the color:
- Click the **Color** box. The color palette appears.
- In the color palette, select the link color for the heading links. In the template design area, the heading links appear in this color.
- **Underline**: If you want the links in the heading to be underlined, enable this setting. Otherwise, the links are not underlined. In the template design area, the heading links appear with this setting.
[See image.](#email-builder-heading-content-window-links-section)
-
In the Rich Text Editor, in the **General** section, set the container padding in one of the following ways:
- In the **All Sides** field, enter the number of pixels to pad the heading with on all sides.
- Enable **More Options **and enter the number of pixels to pad the **Top**, **Right**, **Left**, and **Bottom** of the heading.
In the template design area, this padding appears for the heading.
[See image.](#email-builder-heading-content-window-general-section)
-
In the Rich Text Editor, in the **Responsive Design **section, if you want to hide the heading from the desktop version, enable **Hide on Desktop**. In the desktop version of this notification template, this heading is hidden.
[See image.](#email-builder-heading-content-window-resp-des-section)
-
Configure the mobile version of the heading for the template:
- In the Rich Text Editor, select the **Mobile** tab. Most of the settings that you added for the heading in the desktop version appear for the mobile version.
- Review all the heading settings for the mobile version. The mobile version template size is different from the desktop version template size. So, the mobile version might require some changes from the desktop version.
- (Optional) If necessary, change any of the settings for the mobile version.
[See Image.](#email-builder-heading-content-window-mobile-tab)
[]![Video showing how to use the email template builder to add a heading to an email notification template](/downloads/workflow-automation/setup/adding-email-notification-templates/WA-Notification-Template-Page-Adding-Heading.gif)
[]![Viewing the Smart Headings section in the Rich Text Editor for a heading. The Smart Headings section contains a Try it Now! button. When you click this button you can get AI based suggestions for your heading in any tone you want.](/downloads/workflow-automation/setup/adding-email-notification-templates/WA-Not-Template-PG-Add-Heading-RichTextEditor-Smart-Headings.png)
[]![Viewing the Text section in the Rich Text Editor for a heading. The text section contains multiple fields, such as Heading Type, Font Family, Font Weight, Font Size, Color, and Text Align.](/downloads/workflow-automation/setup/adding-email-notification-templates/WA-Not-Template-PG-Add-Heading-RichTextEditor-Text.png)
[]![Viewing the Links section in the Rich Text Editor. This section contains fields (Inherit Body Styles, Color, and Underline) that are used for configuring the links within the heading for the email notification template.](/downloads/workflow-automation/setup/managing-notification-templates/WA-Not-Template-Page-Add-Heading-Rich-Text-Editor-Link-Section.png)
[]![Viewing the General section in the Rich Text Editor for a heading. The General section contains the Container Padding field.](/downloads/workflow-automation/setup/adding-email-notification-templates/WA-Not-Template-PG-Add-Heading-RichTextEditor-General.png)
[]![Viewing the Responsive Design section in the Rich Text Editor for a heading. The Responsive Design section contains an option to hide this heading on the Desktop version of the email notification template.](/downloads/workflow-automation/setup/managing-notification-templates/WA-Not-Template-Page-Add-Heading-Rich-Text-Editor-Resp-Des-Section.png)
[]![Viewing the mobile version of an email notification template that contains a heading in the email template builder. The Mobile tab is highlighted on the Rich Text Editor.](/downloads/workflow-automation/setup/adding-email-notification-templates/WA-Not-Template-PG-Add-Heading-RichTextEditor-Mobile.png)
[]To add text:
- On the email template builder, in the Button toolbar, click **Content**. In the Rich Text Editor, click the **Text** tool, then drag and drop it to a column in a row in the template design area of the email template builder. In the template design area, the text `This is a new Text block. Change the text.` appears in the column for the row.
- Enter the text:
- In the template design area, click the `This is a new Text block. Change the text.` text in the column and row where you dropped the text. In the template design area, a text toolbar appears. Plus, on the right side of the email template builder, the Rich Text Editor for the text also appears, displaying the **Desktop** tab for the text.
- In the template design area:
- Enter new text to replace `This is a new Text block. Change the text.`
-
Modify the new text using one or more of the following text toolbar options:
- Format it using one or more of the format options. Format options are **Bold**, **Italic**, **Underline**, **Strikethrough**, **Text Color**, **Background Color**, **Superscript**, **Subscript, Bullet List**, and** Number List**.
- Enter a link in the text using the **Insert Link** option. When you click the **Insert Link** option, the **Insert/Edit** **Link** dialog window appears. In the **Insert/Edit Link** dialog window, configure the link using one of the following options:
- Open Website
- **Action Type**: From the drop-down menu, select **Open Website**. The **URL**, **Target**, and **Special Links** fields appear.
- **URL**: Enter the URL for the website.
- **Target**: From the drop-down menu, select where the website opens when the link is selected. The targets are **New Tab** and **Same Tab**.
-
**Special Links**: (Optional) From the drop-down menu, select a special link. The following are special links:
- **Incident Justification Magic Link**: Redirects the user to the Incident page, where they can view and enter justification details for an incident.
- **Incident Escalation Magic Link**: Redirects the manager or approver to the Incident page, where they can view and enter justification details for an incident.
- **Incident List Page Magic Link**: Redirects the user or DLP admin to the Incident page, where they can view the incidents that require their attention.
After you select a special link, the special link appears in the **URL** field. It replaces the value in the **URL** field.
- Click **Save**.
- Send Email
- **Action Type**: From the drop-down menu, select **Send Email**. The **Mail To**, **Subject**, and **Body** fields appear.
- **Mail To**: Enter the email address of the recipient who receives the email.
- **Subject**: Enter the subject line for the email.
- **Body**: Enter the body for the email.
- Click **Save**.
- Call Phone Number
- **Action Type**: From the drop-down menu, select **Call Phone Number**. The **Phone** field appears in this section.
- **Phone**: Enter the phone number to call.
- Click **Save**.
- Add emojis to the text using the **Emoticons** option.
- Add merge tags to the text. From the **Merge Tags** drop-down menu, select a merge tag. Merge tags are:
- **All Incidents Waiting for Feedback Count**
- **Client IP**
- **Current Time**
- **Customer ID**
- **Date**
- **Destination URL**
- **Document Name**
- **High Priority Incidents Waiting for Feedback Count**
- **Hostname or Application**
- **Incident ID**
- **New Incidents Count**
- **Note to the User**
- **Open Incidents Count**
- **Operation**
- **Priority**
- **Severity**
- **State Changes Count**
- **Time**
- **User Name**
- **Violated Policy**
- (Optional) Enhance the quality of your text using the AI-based **Smart Text** options.
[See image.](#email-builder-text-change-text)
- Configure the desktop version of the text for the template:
-
In the Rich Text Editor, in the **Text **section:
- **Font Family**: From the drop-down menu, select the font family for the text. Font families include **Arial**, **Helvetica**, and several others. In the template design area, the text appears in this font family.
- **Font Weight**: From the drop-down menu, select the font weight for the text. Font weights are **Regular** and **Bold**. In the template design area, the text appears in this font weight.
- **Font Size**: Enter the font size in pixels for the text. In the template design area, the text appears in this font size.
-
**Color**: Select the color for the text. A red slash across the box indicates that a color has not been selected. By default, if you do not select a color, then the text appears in the text color that you defined for the template body. To select the color:
- Click the **Color** box. The color palette appears.
- In the color palette, select the color for the text. In the template design area, the text appears in this color.
To learn more, see [Configuring the General Details for the Template Body](#configure-general-details-for-template-body).
- **Text Align**: Select the text alignment for the text in the column. Text alignments are left-aligned, center-aligned, right-aligned, and equal alignment across rows. In the template design area, the text appears in this alignment.
- **Line Height**: Enter the line height percentage for the text in the column. In the template design area, the text appears in this line height.
- **Letter Spacing**: Enter the letter spacing in pixels for the text. In the template design area, the text appears with this letter spacing.
[See image.](#email-builder-text-content-window-text-section)
-
In the Rich Text Editor, in the **Links **section:
- **Inherit Body Styles**: If you want the text links to inherit the link styles you defined for the template body, enable this setting. If you do not enable inherit body styles, the **Color** and **Underline** fields appear in this section. To learn more, see [Configuring the General Details for the Template Body](#configure-general-details-for-template-body).
- **Color**: Select the color for the links. To select a color:
- Click the **Color** box. The color palette appears.
- In the color palette, select the color for the text links. In the template design area, the text links appear in this color.
- **Underline**: If you want the links in the text to be underlined, enable this setting. Otherwise, the links are not underlined. In the template design area, the text links appear with this setting.
[See image.](#email-builder-text-content-window-links-section)
-
In the** **Rich Text Editor, in the **General** section, set the container padding in one of the following ways:
- In the **All Sides** field, enter the number of pixels to pad the text with on all sides.
- Enable **More Options** and enter the number of pixels to pad the **Top**, **Right**, **Left**, and **Bottom** of the text.
In the template design area, the text appears with this padding.
[See image.](#email-builder-text-content-window-general-section)
-
In the** **Rich Text Editor, in the **Responsive Design **section, if you want to hide the text from the desktop version, enable **Hide on Desktop**. In the desktop version of this notification template, this text is hidden.
[See image.](#email-builder-text-content-window-resp-des-section)
-
Configure the mobile version of the text for the template:
- In the** **Rich Text Editor, select the **Mobile** tab. Most of the settings that you added for the text in the desktop version appear for the mobile version.
- Review all the text settings for the mobile version. The mobile version template size is different from the desktop version template size. So, the mobile version might require some changes from the desktop version.
- (Optional) If necessary, change any of the settings for the mobile version.
[See image.](#email-builder-text-content-window-mobile-tab)
[]![Video showing how to use the email template builder to add text to an email notification template](/downloads/workflow-automation/setup/adding-email-notification-templates/WA-Notification-Template-Page-Add-Text.gif)
[]![Viewing the Text section in the Rich Text Editor for text.  The text section contains multiple fields, such as Font Family, Font Weight, Font Size, Color, and Text Align.](/downloads/workflow-automation/setup/adding-email-notification-templates/WA-Not-Template-PG-Add-Text-RichTextEditor-Text.png)
[]![Viewing the Links section on the Rich Text Editor for text on the email notification template](/downloads/workflow-automation/setup/managing-notification-templates/WA-Not-Template-Page-Add-Text-Rich-Text-Editor-Link-Section.png)
[]![Viewing the General section in the Rich Text Editor for text. The General section contains the Container Padding field.](/downloads/workflow-automation/setup/adding-email-notification-templates/WA-Not-Template-PG-Add-Text-RichTextEditor-General.png)
[]![Viewing the Responsive Design section in the Rich Text Editor for text. The Responsive Design section contains an option to hide this text on the Desktop version of the email notification template.](/downloads/workflow-automation/setup/managing-notification-templates/WA-Not-Template-Page-Add-Text-Rich-Text-Editor-Resp-Des-Section.png)
[]![Viewing the mobile version of an email notification template that contains text in the email template builder. The Mobile tab is highlighted on the Rich Text Editor.](/downloads/workflow-automation/setup/adding-email-notification-templates/WA-Not-Template-PG-Add-Text-RichTextEditor-Mobile.png)
[]You can add images to the template design area using a couple of different methods. You can select an image in the Rich Text Editor accessed from the **Images** button on the Button toolbar or select the **Image** tool in the Rich Text Editor accessed from the **Content** button in the Button toolbar.
To add images:
-
On the email template builder, drag and drop an image to the template using one of the following methods:
- In the email template builder, in the Button toolbar, click **Content**. In the Rich Text Editor, click the **Image** tool, then drag and drop it to a column in a row in the template design area of the email template builder. In the template design area, an image placeholder appears in the column for the row.
- In the email template builder, in the Button toolbar, click **Images**. In the Rich Text Editor, select an image, then drag and drop it to a column in a row in the template design area of the email template builder. In the template design area, the image appears in the column for the row.
[See image.](#email-builder-image)
- Configure the desktop version of the image for the template:
-
In the template design area, click the image or the image placeholder in the column and row where you dropped the image. On the right side of the email template builder, the Rich Text Editor for the image appears, displaying the **Desktop** tab.
[See image.](#email-builder-image-2)
-
(Optional) In the Rich Text Editor, in the **Magic Image** section, click **Generate Images** and let AI create a unique and custom image for your design.
[See image.](#email-builder-image-content-window-magic-image-section)
-
In the Rich Text Editor, in the **Image **section:
- Select the image for the image placeholder:
-
**Image**: Select the image for the image placeholder by performing one of the following options:
If you dragged and dropped an image from the **Images** button, you do not need to perform this step. In this case, the **Image** and **Image URL** fields are already populated with the information for the image.
- Click **Upload Image** and upload an image. The image you upload appears in the box under the **Image** field along with an **Edit Image** button. In the template design area, the image appears.
- Drop a new image or select a file to upload to the empty box that is displayed under the **Image** field. The image you upload appears in the box along with an **Edit Image** button. In the template design area, the image also appears.
- From the **More Images** drop-down menu, select **Stock Photos**. The Rich Text Editor appears, displaying different images. In the Rich Text Editor, select an image. The image you select appears in the box under the **Image** field along with an **Edit Image** button. In the template design area, the image also appears.
[See image.](#email-builder-image-content-window-upload-image)
-
**Edit Image**: (Optional) Click this button to edit the image. When you click this button, a new edit image window appears, where you can edit the image. By clicking the various buttons on this window, you can apply effects to the image, such as shapes, stickers, filters, and text.
[See image.](#email-builder-image-content-window-apply-effects)
- **Image URL**: Displays the URL for the image you upload or select.
- Configure the other image settings:
- **Width**: If you want the image to match the width and height of the column in the row in the template design area, enable **Auto On**.** **If you do not enable auto on, a percentage line toggle appears, and you can adjust the width of the image by percentage. In the template design area, the image appears in this width.
- **Align**: Select the alignment for the image in the column. Image alignments are left-aligned, center-aligned, right-aligned, and equal alignment across rows. In the template design area, the image appears in this alignment.
- **Alternate Text**: Enter the text that appears as a tooltip for the image on the email notification created from this template. When you hover over the image on the email notification, this text appears. It also appears if the image is not loaded in the browser.
[See image.](#email-builder-image-content-window-image-section-2)
-
(Optional) In the Rich Text Editor, in the **Action **section, configure one of the following actions for the image:
- Open Website
- **Image Link**: From the drop-down menu, select **Open Website**. The **URL**, **Target**, and **Special Links** fields appear.
- **URL**: Enter the URL for the website.
- **Target**: From the drop-down menu, select where the website opens when the image is selected. The targets are **New Tab** and **Same Tab**.
-
**Special Links**: (Optional) From the drop-down menu, select a special link. The following are special links:
- **Incident Justification Magic Link**: Redirects the user to the Incident page, where they can view and enter justification details for an incident.
- **Incident Escalation Magic Link**: Redirects the manager or approver to the Incident page, where they can view and enter justification details for an incident.
- **Incident List Page Magic Link**: Redirects the user or DLP admin to the Incident page, where they can view the incidents that require their attention.
After you select a special link, the special link appears in the **URL** field. It replaces the value in the **URL** field.
- Send Email
- **Image Link**: From the drop-down menu, select **Send Email**. The **Mail To**, **Subject**, and **Body** fields appear.
- **Mail To**: Enter the email address of the recipient who receives the email.
- **Subject**: Enter the subject line for the email.
- **Body**: Enter the body for the email.
- Call Phone Number
- **Image Link**: From the drop-down menu, select **Call Phone Number**. The **Phone** field appears.
- **Phone**: Enter the phone number to call.
[See image.](#email-builder-image-content-window-action-section)
-
In the Rich Text Editor, in the **General **section, set the container padding in one of the following ways:
- In the **All Sides** field,** **enter the number of pixels to pad the image with on all sides.
- Enable **More Options **and enter the number of pixels to pad the **Top**, **Right**, **Left**, and **Bottom** of the image.
In the template design area, this padding appears for the image.
[See image.](#email-builder-image-content-window-general-section)
-
On the Rich Text Editor, in the **Responsive Design **section, if you want to hide the image from the desktop version, enable **Hide on Desktop**. In the desktop version of this notification template, the image is hidden.
[See image.](#email-builder-image-content-window-resp-des-section)
- Configure the mobile version of the image for the template:
- In the Rich Text Editor, select the **Mobile** tab. Most of the settings that you added for the image in the desktop version appear for the mobile version.
- Review all the image settings for the mobile version. The mobile version template size is different from the desktop version template size. So, the mobile version might require some changes from the desktop version.
- (Optional) If necessary, change any of the settings for the mobile version.
[See image.](#email-builder-image-content-window-mobile-tab)
[]![Video showing how to use the email template builder to add an image to an email notification template](/downloads/workflow-automation/setup/adding-email-notification-templates/WA-Notification-Template-Page-Add-Images.gif)
[]![Viewing the email template builder with an image placeholder on an email notification template. A row with an image placeholder is highlighted in the design section. In addition, the Rich Text Editor is highlighted for the image.](/downloads/workflow-automation/setup/adding-email-notification-templates/WA-Notification-Template-PG-Add-Image-RichTextEditor.png)
[]![Viewing the Magic Image section in the Rich Text Editor for a image. The Magic Image section contains a Generate Images button. When you click this button you can get unique and custom images for your design with AI.](/downloads/workflow-automation/setup/adding-email-notification-templates/WA-Notification-Template-PG-Add-Image-RichTextEditor-Magic-Image.png)
[]![Viewing the email template builder with an image on the email notification template. A row with an image is highlighted in the design section. In addition, the Image section on the Rich Text Editor is highlighted for the image. The Image section contains buttons to upload an image and fields such as, Width, Align, and Alternate Text.](/downloads/workflow-automation/setup/adding-email-notification-templates/WA-Notification-Template-PG-Add-Image-RichTextEditor-Upload-Image.png)
[]![Viewing the edit image window for an image in the email template builder. This window contains several buttons that you can use to apply different affects to the image. Buttons are Filter, Resize, Crop, Draw, Text, Shapes, Stickers, Frame, Corners, and Merge.](/downloads/workflow-automation/setup/adding-email-notification-templates/WA-Not-Template-PG-Add-Image-RichTextEditor-Edit-Image.png)
[]![Viewing the Image section in the Rich Text Editor for an image. The Image section contains buttons to upload an image and additional fields (Width, Align, and Alternate Text) for the image. ](/downloads/workflow-automation/setup/adding-email-notification-templates/WA-Not-Template-PG-Add-Image-RichTextEditor-Image_0.png)
[]![Viewing the Action section in the Rich Text Editor for an image. The Action section contains fields where you can define the action for the image. You can select to have an image open a website, send an email, or call a phone number.](/downloads/workflow-automation/setup/managing-notification-templates/WA-Not-Template-Page-Add-Image-Rich-Text-Editor-Action-Section.png)
[]![Viewing the General section in the Rich Text Editor for an image. The General section contains the Container Padding field.](/downloads/workflow-automation/setup/adding-email-notification-templates/WA-Not-Template-PG-Add-Image-RichTextEditor-General.png)
[]![Viewing the Responsive Design section in the Rich Text Editor for an image. The Responsive Design section contains an option to hide this image on the Desktop version of the email notification template.](/downloads/workflow-automation/setup/managing-notification-templates/WA-Not-Template-Page-Add-Image-Rich-Text-Editor-Resp-Des-Section.png)
[]![Viewing the mobile version of an email notification template that contains an image in the email template builder. The Mobile tab is highlighted on the Rich Text Editor.](/downloads/workflow-automation/setup/adding-email-notification-templates/WA-Notification-Template-PG-Add-Image-RichTextEditor-Mobile-Tab.png)
[]To add menus:
-
In the email template builder, in the Button toolbar, click **Content**. In the Rich Text Editor, click the **Menu** tool, then drag and drop it to a column in a row in the template design area of the email template builder. In the template design area, the menu placeholder appears in the column for the row.
[See image.](#email-builder-menu)
- Configure the desktop version of the menu for the template:
-
In the template design area, click the menu placeholder in the column and row where you dropped the menu. On the right side of the email template builder, the Rich Text Editor for the menu appears, displaying the **Desktop** tab.
[See image.](#email-builder-menu-2)
-
In the Rich Text Editor, in the **Menu Items **section:
- Click the **Add** **New Item** icon. Additional fields appear for the menu item.
- Configure the menu item with one of the following actions:
- Open Website
- **Action Type**: From the drop-down menu, select **Open Website**. The **Label**, **URL**, **Target**, and **Special Links** fields appear in this section.
- **Label**: Enter the label for the menu item. In the template design area, this text appears for the menu item.
- **URL**: Enter the URL for the website.
- **Target**: From the drop-down menu, select where the website opens when the menu item is clicked. The targets are **New Tab** and **Same Tab**.
-
**Special Links**: (Optional) From the drop-down menu, select a special link. The following are special links:
- **Incident Justification Magic Link**: Redirects the user to the Incident page, where they can view and enter justification details for an incident.
- **Incident Escalation Magic Link**: Redirects the manager or approver to the Incident page, where they can view and enter justification details for an incident.
- **Incident List Page Magic Link**: Redirects the user or DLP admin to the Incident page, where they can view the incidents that require their attention.
After you select a special link, the special link appears in the **URL** field. It replaces the value in the **URL** field.
- Send Email
- **Action Type**: From the drop-down menu, select **Send Email**. The **Label**, **Mail To**, **Subject**, and **Body** fields appear in this section.
- **Label**: Enter the label for the menu item. In the template design area, this text appears for the menu item.
- **Mail To**: Enter the email address of the recipient who receives the email.
- **Subject**: Enter the subject line for the email.
- **Body**: Enter the body for the email.
- Call Phone Number
- **Action Type**: From the drop-down menu, select **Call Phone Number**. The **Label** and **Phone** fields appear in this section.
- **Label**: Enter the label for the menu item. In the template design area, this text appears for the menu item.
- **Phone**: Enter the phone number to call.
- (Optional) Add additional menu items to the menu, as required. Repeat the previous steps.
[See image.](#email-builder-menu-content-menu-items-section)
-
In the Rich Text Editor, in the **Styles **section:
- **Font Family**: From the drop-down menu, select the font family for the menu items. Font families include **Arial**, **Helvetica**, and several others. In the template design area, the menu items appear in this font family.
- **Font Weight**: From the drop-down menu, select the font weight for the menu items. Font weights are **Regular** and **Bold**. In the template design area, the menu items appear in this font weight.
- **Font Size**: Enter the font size in pixels for the menu items. In the template design area, the menu items appear in this font size.
- **Letter Spacing**: Enter the letter spacing in pixels for the menu items. In the template design area, the menu items appear in this letter spacing.
- **Text Color**: Select the text color for the menu items. To select the text color:
- Click the **Text Color** box. The color palette appears.
- In the color palette, select the text color for the menu items. In the template design area, the menu items appear in this color.
- **Link Color**: Select the color for the menu item links. To select the link color:
- Click the **Link Color** box. The color palette appears.
- In the color palette, select the link color for the menu items. In the template design area, the menu item links appear in this color.
- **Align**: Select the menu item alignment for the menu in the column. Menu item alignments are left-aligned, center-aligned, right-aligned, and equal alignment across rows. In the template design area, the menu items appear in this alignment.
- **Layout**: From the drop-down menu, select the layout for the menu items. Layouts are **Horizontal** and **Vertical**. In the template design area, the menu items appear in this layout.
- **Separator**: If you select **Horizontal** as the layout, enter the separator for the menu items. In the template design area, the menu items appear with this separator.
-
**Padding**: Set the padding in one of the following ways:
- In the **All Sides** field, enter the number of pixels to pad the menu items with on all sides.
- Enable **More Options** and enter the number of pixels to pad the **Top**, **Right**, **Left**, and **Bottom** of the menu items.
In the template design area, this padding appears for the menu items.
[See image.](#email-builder-menu-content-styles-section)
-
In the Rich Text Editor, in the **General **section, set the container padding in one of the following ways:
- In the **All Sides** field,** **enter the number of pixels to pad the menu with on all sides.
- Enable **More Options **and enter the number of pixels to pad the **Top**, **Right**, **Left**, and **Bottom** of the menu.
In the template design area, this padding appears for the menu.
[See image.](#email-builder-menu-content-gen-section)
-
In the Rich Text Editor, in the **Responsive Design **section, if you want to hide the menu from the desktop version, enable **Hide on Desktop**. In the desktop version of this notification template, the menu is hidden.
[See image.](#email-builder-menu-content-res-des-section)
-
Configure the mobile version of the menu for the template:
- In the Rich Text Editor, select the **Mobile** tab. Most of the settings that you added for the menu in the desktop version appear for the mobile version.
- Review all the menu settings for the mobile version. The mobile version template size is different from the desktop version template size. So, the mobile version might require some changes from the desktop version.
- (Optional) If necessary, change any of the settings for the mobile version.
[See image.](#email-builder-menu-content-mobile-tab)
[]![Video showing how to use the email template builder to add a menu to an email notification template](/downloads/workflow-automation/setup/adding-email-notification-templates/WA-Notification-Template-Page-Add-Menu.gif)
[]![Viewing the email template builder with a menu placeholder on an email notification template. A row with a menu placeholder is highlighted in the design section. In addition, the Rich Text Editor is highlighted for the menu.](/downloads/workflow-automation/setup/adding-email-notification-templates/WA-Not-Template-PG-Add-Menu-RichTextEditor.png)
[]![Viewing the email template builder with a menu configured for an email notification template. The menu items are highlighted in the design section. In addition, the Label fields for the action items are highlighted in the Menu Items section in the Rich Text Editor for the menu.](/downloads/workflow-automation/setup/adding-email-notification-templates/WA-Not-Template-PG-Add-Menu-RichTextEditor-Add-Menu-Items.png)
[]![Viewing the Styles section in the Rich Text Editor for a menu. The Styles section contains fields, such as Font Family, Font Weight, Font Size, Text Color, Link Color, Align, Layout, Separator, and Padding.](/downloads/workflow-automation/setup/adding-email-notification-templates/WA-Notification-Template-PG-Add-Menu-RichTextEditor-Styles.png)
[]![Viewing the General section on the Rich Text Editor for a menu on the email notification template](/downloads/workflow-automation/setup/adding-email-notification-templates/WA-Not-Template-PG-Add-Menu-RichTextEditor-General.png)
[]![Viewing the Responsive Design section in the Rich Text Editor for a menu. The Responsive Design section contains an option to hide this menu on the Desktop version of the email notification template.](/downloads/workflow-automation/setup/managing-notification-templates/WA-Not-Template-Page-Add-Menu-Rich-Text-Editor-Resp-Des-Section.png)
[]![Viewing the mobile version of an email notification template that contains a menu in the email template builder. The Mobile tab is highlighted on the Rich Text Editor.](/downloads/workflow-automation/setup/adding-email-notification-templates/WA-Not-Template-PG-Add-Menu-RichTextEditor-Mobile.png)
[]To add HTMLs:
-
On the email template builder, in the Button toolbar, click **Content**. In the Rich Text Editor, click the **HTML** tool, then drag and drop it to a column in a row in the template design area of the email template builder. In the template design area, the HTML placeholder (`Hello, World!`) appears in the column for the row.
[See image.](#email-builder-html)
- Configure the desktop version of the HTML for the template:
-
In the template design area, click the HTML placeholder in the column and row where you dropped the HTML. On the right side of the email template builder, the Rich Text Editor for the HTML appears, displaying the **Desktop** tab.
[See image.](#email-builder-html-2)
-
In the Rich Text Editor, in the **HTML **section, enter the HTML that you want to have appear in the template. In the template design area, this HTML appears.
[See image.](#email-builder-html-content-html-section)
-
In the Rich Text Editor, in the **General **section, set the container padding in one of the following ways:
- In the **All Sides** field, enter the number of pixels to pad the HTML with on all sides.
- Enable **More Options **and enter the number of pixels to pad the **Top**, **Right**, **Left**, and **Bottom** of the HTML.
In the template design area, this padding appears for the HTML.
[See image.](#email-builder-html-content-gen-section)
-
In the Rich Text Editor, in the **Responsive Design **section, if you want to hide the HTML from the desktop version, enable **Hide on Desktop**. In the desktop version of this notification template, the HTML is hidden.
[See image.](#email-builder-html-content-res-des-section)
-
Configure the mobile version of HTML for the template:
- In the Rich Text Editor, select the **Mobile** tab. A couple of the settings that you added for the HTML in the desktop version appear for the mobile version.
- Review all the HTML settings for the mobile version. The mobile version template size is different from the desktop version template size. So, the mobile version might require some changes from the desktop version.
- (Optional) If necessary, change any of the settings for the mobile version.
[See image.](#email-builder-html-content-mobile-tab)
[]![Video showing how to use the email template builder to add HTML content to an email notification template](/downloads/workflow-automation/setup/adding-email-notification-templates/WA-Notification-Template-Page-Add-HTML.gif)
[]![Viewing the email template builder with the default HTML content (Hello, world!) on an email notification template. The default HTML content is highlighted in the design section. In addition, the HTML section is highlighted in the Rich Text Editor for the HTML.](/downloads/workflow-automation/setup/adding-email-notification-templates/WA-Not-Template-PG-Add-HTML-RichTextEditor.png)
[]![Viewing the HTML section in the Rich Text Editor for HTML content. The HTML section contains an area where you can add the HTML content you want to display on the email notification template. The HTML content section is highlighted in the Rich Text Editor and the HTML content is highlighted in the design area for the email notification template.](/downloads/workflow-automation/setup/adding-email-notification-templates/WA-Not-Template-PG-Add-HTML-RichTextEditor-HTML-Section.png)
[]![Viewing the General section in the Rich Text Editor for HTML content. The General section contains the Container Padding field.](/downloads/workflow-automation/setup/adding-email-notification-templates/WA-Not-Template-PG-Add-HTML-RichTextEditor-General.png)
[]![Viewing the Responsive Design section in the Rich Text Editor for HTML content. The Responsive Design section contains an option to hide this HTML content on the Desktop version of the email notification template.](/downloads/workflow-automation/setup/managing-notification-templates/WA-Not-Template-Page-Add-HTML-Rich-Text-Editor-Resp-Des-Section.png)
[]![Viewing the mobile version of an email notification template that contains HTML content in the email template builder. The Mobile tab is highlighted on the Rich Text Editor.](/downloads/workflow-automation/setup/adding-email-notification-templates/WA-Not-Template-PG-Add-HTML-RichTextEditor-Mobile.png)
[]When configuring the email notification template, you can move rows, and you can also move the content within a column in the template.
- [Moving Rows](#move-rows)
- [Moving Column Content](#move-column-content)
[]To move rows:
-
On the email template builder, in the template design area for a template, click the row that you want to move. A directional icon appears at the end of the row.
[See image.](#email-builder-move-rows)
- Click the directional icon and then drag and drop the row to the new location in the template.
[]![Viewing the email template builder with a row selected in the Design area and the directional icon highlighted at the end of the row. When a row is selected in the Design area, the directional icon appears at the end of the row. Click the directional icon and then drag and drop the row to the new location in the template. ](/downloads/workflow-automation/setup/adding-email-notification-templates/WA-Email-Template-Builder-Move-Rows.png)
[]To move column content:
-
On the email builder, in the template design area for a template, click the column of a row that contains content that you want to move. A directional icon appears at the end of the column.
[See image.](#email-builder-move-col-content)
- Click the directional icon and then drag and drop the content to the new column location in the template. You can move content within the same column in a row, within different columns of the same row, or from one row to another row.
[]![Viewing the email template builder with the content of a column selected in the Design area and the directional icon highlighted next to the content. When the content in a column is selected in the Design area, the directional icon appears next to the content. Select the directional icon and then drag and drop the content to the new column location in the template. You can move content within the same column in a row, within different columns of the same row, or from one row to another row. ](/downloads/workflow-automation/setup/adding-email-notification-templates/WA-Email-Template-Builder-Move-Content.png)
[]When configuring the email notification template, you can delete rows and delete column content in a template.
- [Deleting Rows](#delete-rows)
- [Deleting Column Content](#delete-column-content)
[]To delete rows:
-
In the email template builder, in the template design area, click the row that you want to delete. A **Delete** icon and a **Duplicate** icon appear under the row. On the right side of the email template builder, the Rich Text Editor for the row appears.
[See image.](#email-builder-delete-rows)
- Delete the row using one of the following options:
- In the template design area, click the **Delete** icon under the row.
- In the Rich Text Editor, click the **Delete** icon in the top-right corner.
[]![Viewing the email template builder with a row selected in the Design area to display the Delete icon under the selected row. The Delete icon is highlighted in the Design area and the Delete icon is highlighted on the Rich Text Editor for the row. Click the Delete icon in either location to delete the row.](/downloads/workflow-automation/setup/managing-notification-templates/WA-Email-Template-Builder-Delete-Row.png)
[]To delete column content:
-
In the email builder, in the template design area, click the column of a row that contains content that you want to delete. A **Delete** icon and a **Duplicate** icon appear under the content in the column. On the right side of the email template builder, the Rich Text Editor appears for the content in the column.
[See image.](#email-builder-delete-col-content)
- Delete the content using one of the following options:
- In the template design area, click the **Delete** icon under the content in the column.
- In the Rich Text Editor, click the **Delete** icon in the top-right corner.
[]![Viewing the email template builder with the content for a column selected in the Design area to display the Delete icon under the column content. The Delete icon is highlighted in the Design area and the Delete icon is highlighted on the Rich Text Editor for the content. Click the Delete icon in either location to delete the column content.](/downloads/workflow-automation/setup/adding-email-notification-templates/WA-Email-Template-Builder-Delete-Column-Content.png)
[]When configuring the email notification template, you can duplicate rows and duplicate column content in a template.
- [Duplicating Rows](#duplicate-rows)
- [Duplicating Column Content](#duplicate-column-content)
[]To duplicate rows:
-
On the email template builder, in the template design area, click the row that you want to duplicate. A **Delete** icon and a **Duplicate** icon appear under the row. On the right side of the email template builder, the Rich Text Editor for the row appears.
[See image.](#email-builder-duplicate-rows)
-
Duplicate the row using one of the following options:
- In the template design area, click the **Duplicate** icon under the row.
- In the Rich Text Editor, click the **Duplicate** icon in the top-right corner.
In the template design area, a duplicate row appears under the row that was duplicated.
[]![Viewing the email template builder with a row selected in the Design area to display the Duplicate icon under the selected row. The Duplicate icon is highlighted in the Design area and the Duplicate icon is highlighted on the Rich Text Editor for the row. Click the Duplicate icon in either location to duplicate the row.](/downloads/workflow-automation/setup/adding-email-notification-templates/WA-Email-Template-Builder-Duplicate-Rows.png)
[]To duplicate column content.
-
In the email template builder, in the template design area, click the column of a row that contains content that you want to duplicate. A **Delete** icon and a **Duplicate** icon appear under the content in the column. On the right side of the email template builder, the Rich Text Editor appears for the content in the column.
[See image.](#email-builder-duplicate-col-content)
-
Duplicate the content using one of the following options:
- In the template design area, click the **Duplicate** icon under the content in the column.
- In the Rich Text Editor, click the **Duplicate** icon in the top-right corner.
In the template design area, the duplicate content appears in the column under the content that was duplicated.
[]![Viewing the email template builder with the content for a column selected in the Design area to display the Duplicate icon under the column content. The Duplicate icon is highlighted in the Design area and the Duplicate icon is highlighted on the Rich Text Editor for the content. Click the Duplicate icon in either location to delete the column content.](/downloads/workflow-automation/setup/adding-email-notification-templates/WA-Email-Template-Builder-Duplicate-Column-Content.png)