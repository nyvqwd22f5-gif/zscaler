# Configuring an Alert Rule for Internet & SaaS
Source: https://help.zscaler.com/unified/configuring-alert-rule-internet-saas
PDF: https://help.zscaler.com/pdf/com/en/1529988.pdf

You can configure alert rules to get high-level statistics of each event type and threat severity. You can view, manage, create, and adjust the alert rules based on your organization's traffic. To learn more, see [About Security & UEBA Alerts for Internet & SaaS](/unified/about-security-ueba-alerts-internet-saas).
Adding an Alert Rule
To add an alert rule:
- Go to **Administration **> **Alerts** > **Security & UEBA Alerts** > **Alert Rules**.
-
Click **Add Alert Rule**.
The **Add Alert Rule** window appears.
- In the **Add Alert Rule** window:
- Under the **Alert Definition** section, configure the appropriate parameters:
- **Alert Name**: Enter an alert name. The maximum length is 31 characters.
- **Alert Class**: Select the alert class for the rule. By default, the alert class is set to **Security**.
- **Status**: Select the status of the rule.
- Under the **Alert Trigger Criteria** section, configure the appropriate parameters:
- [For Security Alerts](#adding-alert-rule-security)
- [For UEBA Alerts](#adding-alert-rule-ueba)
- For Security alerts, under the **Evaluation Status **section, to trigger the alert rule, enable **Send Alert Update every ___ intervals** and add the number of times you want to trigger the alert in the **intervals** field.
- For UEBA alerts, under **Actions**, select **Trigger an Alert **or **Place user in group **to trigger the alert rule. Select a **User Group** and **Time Interval** under **Action **for **Place user in group**.
-
Under the **Recipients **section, configure the appropriate parameters:
- **Webhooks**: Select a webhook from the list.
- **Email Addresses**: Add the email address, addresses, or email alias to trigger the alert email notification for the Internet & SaaS alert.
[See image.](#SecurityAlerts-AddAlertRules)
- Click **Save** and [activate the change](/unified/saving-and-activating-changes-admin-portal).
- []**Event Type**: Select the event type for the rule. Select from a list of **Advanced Threat Protection**, **Malware Protection**, or **Sandbox**.
- **Within Time Interval**: Choose the span of time within which an event's occurrence triggers an alert. You can choose from 10 minutes, 15 minutes, 30 minutes, 45 minutes, or 1 hour.
- **Add Filters**: You can add filters to security alerts to make the rule more specific. You can apply the filters to **Location**, **Users**, **Department**, and **System Impacted**.
- []**Event Type**: Select the event type for the rule. Select **Access**, **Data**, or **Privilege **from the drop-down.
- **Alert Type**: Select the alert type of the rule. The alert types depend on the selected **Event Type**. Each channel type has different alert types to choose from. The list of alert types includes:
- [Inline](#alert-types-inline-table)
- [API](#alert-types-api-table)
- **Channel**: Choose between **Inline **and **API **to select the channel. By default, the channel gets set to API for alert rules that are applicable only to the API channel.
- **Within Time Interval**: Choose the span of time within which an event's occurrence triggers an alert.
- **No of Failed Logins**: Enter the number of failed login attempts for the alert rule to get triggered.
- **Tenants**: Select the tenants for which you want to apply the alert rule.
- **No of Files Greater Than**: Enter the number of files to set the trigger. The rule gets triggered if the number of files is greater than the set number, for bulk upload or download of data.
- **Doc Type**: Select the document type to apply the alert rule.
- **DLP Engines**: Select the DLP engine for the rule. You can select one or multiple engines.
- **Data Types**: Select the type of data for the rule. By default, the data type is set to **All Data Types**.
- **No of Activities Greater Than**: Enter the number of activities to set the trigger. The rule gets triggered if the the number of activities is greater than the set number, for bulk sharing of data.
- **Activity**: Select the type of activity for the rule to apply.
- **Countries**: Select the country for the rule to apply. You can select one, multiple, or all countries from the drop-down menu.
Editing an Alert Rule
To edit an existing alert rule:
- Go to **Administration **> **Alerts** > **Security & UEBA Alerts** > **Alert Rules**.
-
In the alerts table, click the **Edit** icon to edit a selected preconfigured alert rule.
The **Edit Alert Rule** window appears.
- In the **Edit Alert Rule** window:
- Under the **Alert Definition** section, configure the appropriate parameters:
- **Alert Name**: Enter an alert name. The maximum length is 31 characters.
- **Alert Class**: Select the alert class for the rule. By default, the alert class is set to **Security**.
- **Status**: Select the status of the rule.
- Under the **Alert Trigger Criteria** section, configure the appropriate parameters:
- [For Security Alerts](#editing-alert-rule-security)
- [For UEBA Alerts](#editing-alert-rule-ueba)
- For Security alerts, under the **Evaluation Status **section, to trigger the alert rule, enable **Send Alert Update every ___ intervals** and add the number of times you want to trigger the alert in the **intervals** field.
- For UEBA alerts, under **Actions**, select **Trigger an Alert **or **Place user in group **to trigger the alert rule. Select a **User Group** and **Time Interval** under **Action **for **Place user in group**.
-
Under the **Recipients **section, configure the appropriate parameters:
- **Webhooks**: Select a webhook from the list.
- **Email Addresses**: Add the email address, addresses, or email alias to trigger the alert email notification for the Internet & SaaS alert.
[See image.](#securityalerts-editalertrule)
- Click **Save** and [activate the changes](/unified/saving-and-activating-changes-admin-portal).
- []**Event Type**: Select the event type for the rule. Select from a list of **Advanced Threat Protection**, **Malware Protection**, or **Sandbox**.
- **Within Time Interval**: Choose the span of time within which an event's occurrence triggers an alert. You can choose from 10 minutes, 15 minutes, 30 minutes, 45 minutes, or 1 hour.
- **Add Filters**: You can add filters to security alerts to make the rule more specific. You can apply the filters to **Location**, **Users**, **Department**, and **System Impacted**.
- []**Event Type**: Select the event type for the rule. Select **Access**, **Data**, or **Privilege **from the drop-down.
- **Alert Type**: Select the alert types of the rule. The alert types depend on the selected **Event Type**.
- **Channel**: Choose between **Inline **and **API **to select the channel. By default, the channel gets set to API for alert rules that are applicable only to the API channel.
- **Within Time Interval**: Choose the span of time within which an event's occurrence triggers an alert.
- **No of Failed Logins**: Enter the number of failed login attempts for the alert rule to get triggered.
- **Tenants**: Select the tenants for which you want to apply the alert rule.
- **No of Files Greater Than**: Enter the number of files to set the trigger. The rule gets triggered if the number of files is greater than the set number, for bulk upload or download of data.
- **Doc Type**: Select the document type to apply the alert rule.
- **DLP Engines**: Select the DLP engine for the rule. You can select one or multiple engines.
- **Data Types**: Select the type of data for the rule. By default, the data type is set to **All Data Types**.
- **No of Activities Greater Than**: Enter the number of activities to set the trigger. The rule gets triggered if the the number of activities is greater than the set number, for bulk sharing of data.
- **Activity**: Select the type of activity for the rule to apply.
- **Countries**: Select the country for the rule to apply. You can select one, multiple, or all countries from the drop-down menu.
[]![The Add Alert Rule window helps to configure various rules for different events.](/downloads/zia/security-ueba-alerts/configuring-alert-rule/Add%20Alert%20Rule.png)
[]![The Edit Alert Rule window helps to edit various preconfigured alert rules for different events.](/downloads/tech-pubs-drafts/zia-draft-articles/configuring-alert-rule-draft-ueba/Edit-Security-Alerts_0.png)
Alert Rule Exceptions
The UEBA alert also provides the option to exempt multiple users from an alert rule. By retaining specific users in the exceptions list, the alert does not evaluate them against the traffic for the selected applications.
To edit the list of user exceptions:
-
Edit an existing alert from the Alert Rules table.
The **Edit Alert Rule** window is displayed.
-
Click **Exceptions**.
The list of users exempted from evaluation appears.
-
To delete a user from the list, click the **Remove **icon (**x** icon) next to their name.
[See image.](#ueba-exceptions)
- Click **Save** and [activate the changes](/unified/saving-and-activating-changes-admin-portal).
[]![The Exceptions page allows users to be added to the list of exception for evaluation of traffic.](/downloads/tech-pubs-drafts/zia-draft-articles/configuring-alert-rule-draft-ueba/Alerts-Exceptions-UEBA.png)
[]
| Alert Type | Description |
| ---------- | ----------- |
| Impossible Travel | Identify users accessing the organization’s applications from different locations in a short period of time. |
| Multiple Failed Logins | Identify users with multiple failed login attempts to the organization’s applications in a short period of time. |
| Bulk Download of Data | Identify users with large amounts of download activities in a short period of time. |
| Bulk Upload of Data | Identify users with large amounts of upload activities in a short period of time. |
| Code Repo Shared Externally | Identify external users accessing the organization’s code repositories. |
| Code Repo Made Public | Identify if the organization’s code repositories are made public. |
| Bulk Files Delete | Identify users with large amounts of delete activities in a short period of time. |
| Bulk Share of Data | Identify users with large amounts of share activities in a short period of time. |
| Excessive Admin Activities | Identify users performing high admin activities in a short period of time. |
[]
| Alert Type | Description |
| ---------- | ----------- |
| Upload of Invoice | Identify users who have uploaded invoices in a short period of time. |
| Upload of Tax documents | Identify users who have uploaded tax documents in a short period of time. |
| Upload of Resumes | Identify users who have uploaded resumes in a short period of time. |
| Upload of Medical documents | Identify users who have uploaded medical documents in a short period of time. |
| Upload of Real Estate documents | Identify users who have uploaded real estate documents in a short period of time. |
| Upload of Legal documents | Identify users who have uploaded legal documents in a short period of time. |
| Upload of Court Form documents | Identify users who have uploaded court form documents in a short period of time. |
| Upload of Technical documents | Identify users who have uploaded technical documents in a short period of time. |
| Upload of Transportation and Motor documents | Identify users who have uploaded documents related to transportation and motor in a short period of time. |
| Upload of Immigration documents | Identify users who have uploaded immigration documents in a short period of time. |
| Upload of Insurance documents | Identify users who have uploaded insurance documents in a short period of time. |
| Upload of Corporate Finance documents | Identify users who have uploaded corporate finance documents in a short period of time. |
| Upload of Corporate Legal documents | Identify users who have uploaded legal documents in a short period of time. |
| Data exfiltration by password protected or encrypted docs | Identify users who have shared data after applying encryption or passwords to avoid content inspection. |
| Upload to high risk countries | Identify users who have uploaded data to locations in suspicious countries. |
| Upload from high risk countries | Identify users who have uploaded data from locations in suspicious countries. |
| Bulk Activity Alert | Identify users who have performed a certain set of activities in a short period of time. Through this alert multiple activities for the SaaS Security API can be tracked for a user.Supported Activities: Upload, Share, Create, Edit, Delete, Comment, Download, Rename, Form Sharing, File Transfer, Chat, Post, Send email, Send Attachments, and Comment |
| Bulk upload of sensitive data | Identify users who have uploaded sensitive data in a short period of time. |
| Bulk download of sensitive data | Identify users who have downloaded sensitive data in a short period of time. |