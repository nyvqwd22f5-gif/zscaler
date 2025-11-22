# Managing Exception Settings
Source: https://help.zscaler.com/uvm/managing-exception-settings
PDF: https://help.zscaler.com/pdf/com/en/1527626.pdf

You can set up and manage exception requests within your Zscaler Unified Vulnerability Management (UVM) application. Users with access to exception settings can enable and customize the exception request process in the account. To learn more about exceptions, see [Understanding Exceptions Requests](/uvm/understanding-exception-requests).
For access to exceptions settings, your assigned role must include the Read and Edit permissions under the Vulnerabilities App > Exception Settings resource. To learn more, see [Creating Custom Roles](/uvm/creating-custom-roles) and [Assigning Roles to Users](/uvm/assigning-roles-users). To learn more about assigning exception reviewers, see [Reviewing Exception Requests](/uvm/reviewing-exception-requests).
The exception settings process involves the following steps:
- [Configuring the Exception Request Form](#configuring-request-form)
- [Assigning Reviewers](#assigning-reviewers)
- [Configuring Email Notifications](#configuring-email-notifications)
After customizing the settings, select **Enable to allow exception request submissions for UVM tickets **at the top of the page to activate the **Request Exception **button in the UVM tickets drawer.
[See image.](#enable-exception-request-submissions-uvm-tickets)
[]Configure the Exception Request form to capture the necessary information from requesters when they submit an exception request for an extended service level agreement (SLA). This form is displayed when the requester clicks the Exception Request button in the relevant ticket drawer.
The following fields are mandatory and cannot be removed from the form:
- **Requested SLA**: The requested SLA date extension for the ticket.
-
**Reason**: The reason the requester is submitting the request. The Reason field is populated by the values configured in the field's content validation on the Data Model page.
To customize the reason values:
- Go to **Configure **> **Data Model**.
-
Under **Exception**, select the **Reason **field.
The **Reason **drawer appears.
- In the **Reason **drawer, click the **Manual Updates **tab.
-
In the **Content Validation **section, adjust the values as needed.
[See image.](#reason-data-model-content-validation)
- Click **Save**.
You can add fields to the exception form to capture relevant information for your organization's exception request process.
If you integrate with a third-party exception management system, Zscaler recommends mirroring the required fields in the exception form to maintain consistency and avoid potential errors or misalignments.
To configure the exceptions form:
- In the **Vulnerabilities **app, go to **Settings **> **Exceptions**.
-
Click **Exceptions Settings**.
The **Exceptions **page appears.
-
In the **Request Form Fields **section, click **Add Field**.
A drop-down menu appears.
-
Select a field from the drop-down menu.
If the field you need is not listed in the drop-down menu, you can create a custom field on the Data Model page. If you don't have access to the Data Model page, contact your admin.
- (Optional) Hover over the field and select the **Required Field **checkbox. This ensures the field is populated during form submission.
- (Optional) Drag and drop fields using the **Drag **icon to reorder their appearance in the form.
- Save the settings in one of the following ways:
- Click **Save**. The exception settings will apply the next time data is ingested into your account.
- In the **Save **drop-down menu, click **Save & Run **to save the settings and immediately apply them in your account.
[]![exception reason data model content validation](/downloads/uvm/vulnerability-management/settings-uvm/managing-exception-settings/exception%20reason%20data%20model%20content%20validation.png)
[]Configure assignment rules to automatically assign new exception request submissions to designated reviewers based on shared attributes.
An assignment rule consists of two parts:
- IF Condition: Defines a filter that determines which requests the rule applies to. The IF condition can be configured as structured Conditions or as an Expression.
- Set Reviewer as: Specifies the value to populate the Reviewer field with when the request meets the IF conditions.
The reviewer assignment ruleset includes a default fallback rule with no conditional logic that applies when no other rule conditions are met. This ensures that there is always a default method for populating the Reviewer field. By default, no value is set in the default rule, which leaves the Reviewer field empty. You can edit this rule to adjust the default value, but it cannot be removed or deleted.
To create an assignment rule:
- In the **Vulnerabilities **app, go to **Settings **> **Exceptions**.
-
Click **Exceptions Settings**.
The **Exceptions **page appears.
-
In the **Reviewer Assignment Rules **section, click **Add Rule**.
The **Create Unification Rule** drawer appears.
- In the **Create Unification Rule **drawer:
- **Name**: Enter a name for the rule.
-
**IF**: Define the rule condition that determines which request the rule should apply to.
- Select a field that the condition should be based on. Available fields include Exception fields and all fields with a relation to Exceptions.
- Select an operator (e.g., **Equals**, **Contains**). Available operators vary depending on the field type, indicated to the left of the field name.
- Enter the value that the rule should apply to. Exception Reviewer conditions are not case sensitive.
- (Optional) Use **AND**/**OR** logic to define compound rules:
- **AND **populates the field only if the field meets all conditions in the rule.
- **OR **populates the field if the field meets any of the conditions in the rule.
For advanced filtering, click **Expression **in the top-right corner. Supported functions, operators, and references, along with examples, are displayed when clicking the Expression text box.
- **Set Reviewer as**: Select a method to set the value to populate the Reviewer field if the request meets the rule's conditions.
-
**By User**: Select a user from the drop-down menu.
The available users in the drop-down menu that you can set as exception reviewers are users assigned the **Audit **permission under the **Vulnerabilities **> **Exceptions Operational View** resource. To learn more, see [Creating Custom Roles](/uvm/creating-custom-roles).
- **Empty**: Select this method to prevent automatic reviewer assignment for requests that meet the rule's conditions, effectively leaving the **Reviewer **field unassigned.
- Click **Add **to save the rule.
- Save the settings in one of the following ways:
- Click **Save**. The exception settings will apply the next time data is ingested into your account.
- In the **Save **drop-down menu, click **Save & Run **to save the settings and immediately apply them in your account.
[]Configure email notifications to alert reviewers when new exception requests are submitted. This helps reviewers stay informed, enabling them to review and process exception requests efficiently and in a timely manner. Configuring email notifications ensures that exception requests are properly routed and processed through your organization's workflow.
To configure email notifications for new exception requests:
- In the **Vulnerabilities **app, go to **Settings **> **Exceptions**.
-
Click **Exceptions Settings**.
The **Exceptions **page appears.
- Enable **Email Notifications**.
- Select an option:
- **Notify assigned reviewer of new exception requests**: Select when you have assignment rules configured and you want to ensure that the designated reviewer is notified directly. An email is sent only to the reviewer assigned to review the request. If no reviewer is assigned to the exception, no email is sent.
- **Notify all reviewers of new exception requests**: Select if all reviewers are equally responsible for reviewing requests. An email is sent to all reviewers in the account.
- Save the settings in one of the following ways:
- Click **Save**. The exception settings will apply the next time data is ingested into your account.
- In the **Save **drop-down menu, click **Save & Run **to save the settings and immediately apply them in your account.
When the notification is sent for a single request submission, the email includes:
- **Ticket ID**: The unique identifier for the ticket associated with the exception request.
- **Ticket Title**: The title of the ticket associated with the exception request.
- **Requester**: The user who submitted the exception request.
- **Reason**: The reason for the exception request, as specified by the requester.
- **Current SLA**: The current SLA for the ticket.
- **Requested SLA**: The requested SLA extension for the ticket.
When the notification is sent for multiple request submissions, the email includes a link to the Exceptions drawer filtered by the new exception requests.
[]![enable exception request submissions for UVM tickets](/downloads/uvm/vulnerability-management/settings-uvm/managing-exception-settings/enable%20exception%20requests%20for%20uvm%20tickets%20toggle.png)