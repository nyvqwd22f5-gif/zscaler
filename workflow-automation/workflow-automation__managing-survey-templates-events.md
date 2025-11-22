# Managing Survey Templates for Events
Source: https://help.zscaler.com/workflow-automation/managing-survey-templates-events
PDF: https://help.zscaler.com/pdf/com/en/1500266.pdf

Adding survey templates in Workflow Automation is one of the tasks in configuring Workflow Automation. Admins with access to Workflow Automation can add and map survey templates. A survey template provides the format for the survey that an end user must complete when responding to an event notification from Workflow Automation. The survey includes questions that, when answered, provide the justification for the event.
When an admin configures a notification template, they can choose to format a link in the notification template that enables the user to view the event details and the survey. When a user receives the notification, they can click the link, which opens the events page and the survey that they must complete. The template settings on the [Template Mappings](/workflow-automation/managing-template-mappings-events) page determine the notification template and the survey template that Workflow Automation uses for the different event types and notification types.
Workflow Automation provides the system default **End-user Justification - Questionnaire Template** survey template. You can create only one template in each language. You cannot create two templates of the same language for a single template family.
Admins cannot edit the system default survey template. They can only view and clone the default survey template.
On the Survey Templates page, admins can:
- [View Survey Templates](#view-survey-templates)
- [Add Survey Templates](#add-survey-templates)
- [Preview Survey Templates](#preview-survey-templates)
- [Edit Survey Templates](#edit-survey-templates)
- [Translate Survey Templates](#translate-survey-template)
- [Clone Survey Templates](#clone-survey-templates)
[]To view existing survey templates:
- Go to **Setup** > **Survey Templates**. The **Survey Templates** page appears.
- (Optional) Filter the templates by status, type, template family, or language. You can also search for specific templates that you want to view.
- (Optional) Reset all the applied filters.
-
View a list of survey templates configured for your organization. For each survey template, you can see:
- **Template Name**: The name of the template.
- **Template Family**: The family of the template.
- **Type**: The type of template. The type of template is always **Questionnaire**.
- **Language**: The language of the template.
- **Last Modified**: The date and time the template was last modified.
- **Status**: The status of the template. Statuses are **Draft**, **Published**, or **System Default**.
[See image.](#Survey-Templates-Page-View)
[]To add a survey template:
- Go to **Setup** > **Survey Templates**. The **Survey Templates** page appears.
-
Click **Add More**.
[See image.](#Survey-Templates-Page-Add_1)
-
On the new page that appears:
- **Template Name**: Enter a name for the template.
- **Template Family**: From the drop-down menu, select a family for the template.
- **Type**: From the drop-down menu, select **Questionnaire**.
- **Source Language**: Select the language for the template.
After you select the template type, the survey creator section appears below the row. Workflow Automation uses the Survey Creator component from Survey. Using this drag-and-drop survey builder, you can create a survey template, change the content, include pictures, and link to files. Furthermore, you can change the template's structure and style.
[See image.](#Survey-Templates-Page-Add_2)
- In the survey creator, configure the survey template using one or more of the questions and panel types in the toolbox:
- **Single Input**: Adds a single-line text editor to the template design. Use this type for open-ended questions that require short answers.
- **Checkbox**: Adds a checkbox to the template design. Use this type for questions that accept multiple answers.
- **Radiogroup**: Adds a radiogroup to the template design. Use this type for questions that can have multiple options but accept only one answer.
- **Dropdown**: Adds a drop-down menu to the template design. Use this type for questions that can have multiple options but accept only one answer. With this type, you can display more options while occupying less screen space.
- **Comment**: Adds a resizeable multiline text area to the design. Use this type for open-ended questions that accept multiline answers.
- **Rating**: Adds a rating selection to the design. Use this type if you want respondents to enter a rating.
- **Ranking**: Adds a ranking list to the design. Use this type for questions in which respondents must set the order of items.
- **Image Picker**: Adds an image picker to the design. Use this type to have respondents select one or several images or videos from a series.
- **Boolean**: Adds a Boolean editor to the design. Use this type to have respondents switch the Boolean editor to Yes or No.
- **Image**: Adds an image or video to the design. This type is used for presentation only.
- **HTML**: Adds HTML to the design. Use this type to format text as needed, include links, and insert media or other custom elements. This type is used for presentation only.
- **Signature Pad**: Adds a signature area to the design. Use this type to obtain the respondent's signature or any hand-drawn input.
- **Expression**: Adds an expression to the design. Use this type to calculate values and present them to respondents.
- **File**: Adds a file upload area to the design. Use this type to allow respondents to upload files.
- **Single-Choice Matrix**: Adds a single-choice matrix to the design. Use this type to display radio buttons in rows and columns. Respondents can select only one radio button in each row.
-
**Multiple-Choice Matrix**: Adds a multichoice matrix to the design. Use this type to display rows and columns. At their intersections, the matrix can display the following editors:
- Dropdown
- Checkbox
- Radiogroup
- Single Input
- Comment
- Boolean
- Expression
- Ratings
Respondents use these editors to select a desired value in each cell.
- **Dynamic Matrix**: Adds a dynamic matrix to the design. This type is similar to the Multiple-Choice Matrix, but respondents can add and remove matrix rows.
- **Multiple Text**: Adds multiple single-line text editors to the design. Use this type for open-ended questions that require more than one short answer.
- **Panel**: Adds a panel container for other questions and panels to the design. Use this type to group several questions or panels and control them all together.
- **Dynamic Panel**: Adds a dynamic panel that can contain multiple questions. Respondents can add and remove panels based on the template.
- (Optional) Click **Save as Draft**. The template is saved with the status as **Draft**. You can come back later and continue to work on the template design.
- (Optional) Click **Translate** to translate the newly created template to a different language. The **Translate **window appears.
- In the **Translate** window, from the **Translate To** drop-down menu, select a language to which you want to translate the template.
- Click **Preview** to view the translated template. The template displays in the selected language.
- (Optional) To revert the template to the original language and also to revert any changes made after translation, click **Reset**.
- Click **Publish Template**. The template is published, and the status is **Published**. Workflow Automation only uses published templates for its surveys.
[]To preview a survey template:
- Go to **Setup** > **Survey Templates**. The **Survey Templates** page appears.
- In the **Action** column next to an existing template, click the **View** icon. The Survey Template page appears, displaying the survey template in the **Designer** tab.
- On the **Survey Template** page, click the **Preview** tab to view the survey template in its rendered format.
[See image.](#Survey-Templates-Page-Preview-Designer-Tab)
-
(Optional) Click **Edit Template**. You are redirected to a page where you can modify and publish the survey template.
[See image.](#Survey-Templates-Page-Preview-Preview-Tab)
- Click **Close**.
[]To edit a survey template:
- Go to **Setup** > **Survey Templates**. The **Survey Templates** page appears.
-
In the** Action** column next to an existing published or draft template, click the **Edit** icon. You cannot edit a system default template. The **Survey Template** page appears, displaying the survey template under the **Designer** tab.
[See image.](#Survey-Templates-Page-Edit)
- On the **Survey Template** page, edit the survey template details or the survey template design using one or more of the question and panel types in the toolbox.
- (Optional) Click **Save as Draft**. You can come back later and continue to work on the template design.
- Click **Publish Template**. The template is published. Workflow Automation only uses published templates for its surveys.
To delete a survey template, in the **Action** column next to an existing template, click the **Delete** icon. You cannot delete a system default template.
[]To translate a survey template into a different language:
- Go to **Setup** > **Survey Templates**. The **Survey Templates** page appears.
-
In the** Action** column next to a published, system default, or draft template, click the **Translate** icon. The **Translate **window appears.
[See image.](#translate-template-icon-image)
- In the **Translate** window, from the **Translate To** drop-down menu, select a language to which you want to translate the template.
-
To view the translated template, click **Preview**. The template displays in the selected language.
[See image.](#translate-window-image)
- (Optional) To revert the template to the original language and also to revert any changes made after translation, click **Reset**.
- (Optional) Click **Save as Draft**. You can come back later and continue to work on the template.
- Click **Publish Template**. The template is published. Workflow Automation only uses published templates for its surveys.
[]To clone a survey template:
- Go to **Setup** > **Survey Templates**. The **Survey** **Templates** page appears.
-
In the **Action** column next to a draft, published, or system default template, click the **Clone** icon. The **Survey Template** page appears. In the **Template Name** field, "Clone of" appears in front of the name of the survey template that you cloned.
[See image.](#clone-template-window)
- (Optional) In the **Template Name** field, change the template name.
- Edit the template details or the survey template design using one or more of the question and panel types in the toolbox.
-
(Optional) Click **Save as Draft**. You can come back later and continue to work on the template design.
[See image.](#view-clone-template)
- (Optional) Click **Translate** to translate the newly created template to a different language. The **Translate **window appears.
- In the **Translate** window, from the **Translate To** drop-down menu, select a language to which you want to translate the template.
- Click **Preview** to view the translated template. The template displays in the selected language.
- (Optional) To revert the template to the original language and also to revert any changes made after translation, click **Reset**.
- Click **Publish Template**. The template is published. Workflow Automation only uses published templates for its surveys.
You can only update the [template mappings](/workflow-automation/managing-template-mappings-events) with templates that are in a published status. You also receive notifications from Workflow Automation to update the template mappings to use this template.
[]![Viewing all the templates on the Survey Templates page. The survey templates are listed in a table that has columns for Template Name, Template Family, Type, Language, Last Modified, Status, and Action.](/downloads/workflow-automation/business-insights/setup/managing-survey-templates-events/WA-BI-Survey-Templates-PG-Main-Page.png)
[]![Viewing the Add More button on the Survey Templates page](/downloads/workflow-automation/business-insights/setup/managing-survey-templates-events/WA-BI-Survey-Templates-PG-Add-More-Button.png)
![Adding a template using the survey creator section on the Survey Template page. The survey creator section is initially empty and displays the toolbox that contains the questions and panel types that you can use to create the template.](/downloads/workflow-automation/business-insights/setup/managing-survey-templates-events/WA-BI-Survey-Templates-PG-Adding-Template-Page.png)
[]
[]![Previewing a template on the Survey Template page](/downloads/workflow-automation/business-insights/setup/managing-survey-templates-events/WA-BI-Survey-Templates-PG-Preview-Tab.png)
![Survey Templates Page - Previewing a Template](/downloads/workflow-automation/business-insights/setup/managing-survey-templates-events/WA-BI-Survey-Templates-PG-Edit-Template-Button.png)
[]
![Editing a survey template on the Survey Template page](/downloads/workflow-automation/business-insights/setup/managing-survey-templates-events/WA-BI-Survey-Templates-PG-Edit-Template-Page.png)
[]
[]![Viewing a cloned template on the Survey Template page](/downloads/workflow-automation/business-insights/setup/managing-survey-templates-events/WA-BI-Survey-Templates-PG-Clone-Template-Change-Name.png)
[]![Viewing a cloned template with a draft status on the Survey Templates page](/downloads/workflow-automation/business-insights/setup/managing-survey-templates-events/WA-BI-Survey-Templates-PG-Draft-Status.png)
![Viewing the Translate icon for a template on the Survey Templates page](/downloads/workflow-automation/business-insights/setup/managing-survey-templates-events/WA-BI-Survey-Templates-PG-Translate-Icon.png)
[]
![Viewing the language drop-down menu in the Translate window](/downloads/workflow-automation/business-insights/setup/managing-survey-templates-events/WA-BI-Survey-Templates-PG-Translate-Preview-Button.png)
[]