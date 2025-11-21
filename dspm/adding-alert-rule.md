# Adding an Alert Rule
Source: https://help.zscaler.com/dspm/adding-alert-rule
PDF: https://help.zscaler.com/pdf/com/en/1487201.pdf

You can add [alert rules](/dspm/about-alert-notifications) to export alert notifications to [third-party tools](/dspm/about-third-party-integrations) for further investigation.
Prerequisite
You need to integrate DSPM with the third-party tools before configuring alert rules.
Adding an Alert Rule
To add an alert rule:
- Go to **Alerts **> **Alert Settings** > **Alert Notification**.
-
Click **Create Alert Rule**.
[See image.](#create-rule)
-
On the **General Information** page:
- **Alert Rule Name**: Enter a unique name for the alert rule.
- (Optional)** Alert Rule Description**: Enter a description for the alert rule.
[See image.](#generalinfo)
- Click **Next**.
-
In the **Notification Scope** page, select at least one of the following filters:
- [Policies](#policies)
- [Cloud Accounts](#cloudaccounts)
- [Tags](#tags)
- [Resources](#resources)
- [DLP Engines](#dlp-engines)
[See image.](#notification-scope)
-
(Optional) In the **Notifications** page, select the third-party tools to which the alert notifications must be sent:
- [ITSM/Ticketing](#itsm-jira)
- [Cloud Storage](#cloud-storage)
- [ChatOps](#slack)
[See image.](#itsm/ticketing)
If you do not select the third-party tools and proceed to the next step, the alert rule is disabled, and an exclamation mark is displayed indicating the rule is invalid. [See image.](#notification-saved) You can add third-party tools later by [editing the alert notification](/dspm/editing-or-deleting-alert-notification).
- Click **Next**.
-
Review the alert rule configuration and edit the details if required, then click **Finish**.
[See image.](#notifi-summary)
The alert rule is displayed on the [Alert Notifications page](/dspm/about-alert-notifications) and is enabled by default.
[]Select the policy, category, or severity. Depending on your selection, one of the following additional fields is displayed:
- **Category**: Select the [threat category](/dspm/threat-categories) (**Public Exposure**, **External Users**, **Risky Credentials**, **Malicious Access**, **Data Loss**, **Data Governance**) from the drop-down menu.
- **Severity**: Select the policy severity (**Critical**, **High**, **Medium**, and **Low**) from the drop-down menu.
-
**Select Policies**: Select to view the** Select Existing Policies** page, and select the required [policies](/dspm/about-data-posture-policies) (**Custom** and **Predefined**) from the table.
[See image.](#select-existing-policies)
[See image.](#select-policies)
By default, the **All Policies** option is selected.
[]Select the cloud accounts, business units, or cloud provider. Depending on your selection, one of the following additional fields is displayed:
- **Select Accounts**: Select the [cloud accounts](/dspm/viewing-cloud-accounts-and-organizations) from the drop-down menu.
- **Business Units**: Select the [business units](/dspm/about-business-units) from the drop-down menu.
- **Cloud Provider**: Select the cloud provider (**AWS**, **Azure**, or **GCP**) from the drop-down menu.
[See image.](#select-cloud-accounts)
By default, the **All Account** option is selected.
[]Click the **Tags** drop-down menu and choose **Select Tags**. Click the **Add Tags** icon that appears to include the required tags.
[See image.](#select-tags)
By default, the **All Tags** option is selected.
[]Click the **Resources** drop-down menu and choose **Resource Type**. Select the required data stores from the drop-down menu.
[See image.](#select-resources)
By default, the **All Resources** option is selected.
[]Configure the following details:
- Select **ServiceNow** or **JIRA** or both.
- **Include in Alert payload**: Select the **Remediation **checkbox to include remediation steps in the alert payload.
- **Assignee**: Enter the recipient's email ID.
- **Send notifications for closed alerts**: Select the checkbox to send notifications for closed alerts.
- **Send notifications for resolved alerts**: Select the checkbox to send notifications for resolved alerts.
[See image.](#itsm-ticketing)
[]Configure the following details:
- Select the checkbox for the required Cloud Storage service, then select the integration account from the drop-down menu.
- **Include in Alert payload**: Select the **Remediation **checkbox to include remediation steps in alert payload.
[See image.](#cloudstorage)
[]Select **Slack** and then select the required Slack channels.
[See image.](#chatops)
[]Click the **DLP Engines** drop-down menu and choose **Specific** **DLP Engines**. Select the required DLP engines.
[See image.](#dlpengine-filter)
By default, the **All DLP Engines** option is selected.
[]![Add a notification rule](/downloads/dspm/alerts/alert-notification-rules/adding-alert-notification-rule/dspm-create-rule-button.png)
[]![Add notification name and description](/downloads/dspm/alerts/alert-notification-rules/adding-alert-rule/dspm-add-alert-rule-gi.png)
[]![Select the alert notification scope](/downloads/dspm/alerts/alert-notification-rules/adding-alert-rule/dspm-notification-scope-page.png)
[]![Select existing policies](/downloads/dspm/alerts/alert-notification-rules/adding-alert-rule/dspm-select-existing-policies.png)
[]![Select the policy scope](/downloads/dspm/alerts/alert-notification-rules/adding-alert-notification-rule/dspm-notification-policies.png)
[]![Select cloud accounts scope](/downloads/dspm/alerts/alert-notification-rules/adding-alert-notification-rule/dspm-cloud-accounts.png)
[]![Select notification tags](/downloads/dspm/alerts/alert-notification-rules/adding-alert-notification-rule/dspm-notification-tags.png)
[]![Select resources scope](/downloads/dspm/alerts/alert-notification-rules/adding-alert-notification-rule/dspm-notification-resources.png)
[]![Alert Notification Saved Status](/downloads/dspm/alerts/alert-notification-rules/adding-alert-notification-rule/dspm-invalid-alert-rule.png)
[]![View the alert notification summary](/downloads/dspm/alerts/alert-notification-rules/adding-alert-notification-rule/dspm-add-rule-summary.png)
[]![Configure the ITSM fields](/downloads/dspm/alerts/alert-notification-rules/adding-alert-rule/dspm-notifications-page.png)
[]![Configure the cloud storage fields](/downloads/dspm/alerts/alert-notification-rules/adding-alert-notification-rule/dspm-cloud-storage.png)
[]![Configure the ChatOps fields](/downloads/dspm/alerts/alert-notification-rules/adding-alert-rule/dspm-create-rule-slack.png)
[]![Select the filter scope](/downloads/dspm/alerts/alert-notification-rules/adding-alert-rule/dspm-dlp-engines.png)
[]![Configure the ITSM/Ticketing ](/downloads/dspm/alerts/alert-notification-rules/adding-alert-notification-rule/dspm-itsm-ticketing.png)