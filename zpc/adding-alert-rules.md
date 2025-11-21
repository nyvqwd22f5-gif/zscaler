# Adding Alert Rules
Source: https://help.zscaler.com/zpc/adding-alert-rules
PDF: https://help.zscaler.com/pdf/com/en/1394356.pdf

You can configure custom alert rules and set up notifications for specific security policy violations that occur in your cloud resources and IaC templates. ZPC triggers alerts in the event of any security policy violations and sends email notifications to recipients to take the necessary action.
You can integrate ZPC with third-party tools (ITSM, cloud storage services, and ChatOps), and send alert notifications and alert data to these tools for incident management. To learn more, see [About Third-Party Integrations](/zpc/about-third-party-integrations).
Prerequisites
You must first [onboard your cloud accounts](/zpc/onboarding-cloud-accounts) or complete the [IaC integration](/zpc/about-iac-integrations) before adding cloud or IaC alert rules.
Adding an Alert Rule
To add an alert rule:
- In the left-side navigation, select **Alerts**.
- On the **Alerts** page, click the **Notifications** tab.
- Click **Create Rule**.
[See image.](#createrulebutton)
- Under **General Information**:
- **Alert Rule Name**: Enter a unique name for the alert rule.
- **Alert Type**: Select **Cloud **or **IaC**.
- **Alert Rule Status**: Click the toggle to enable the status. Email notifications are sent every time the alert is triggered.
[See image.](#alert-general)
- Click **Next**.
- Under **Scope**, configure the details for:
- [Cloud Alert](#Cloud-alert-rules)
- [IaC Alert](#IaC-alert-rules)
- Click **Next**.
- Under **Notifications**, configure the alert notification for any of the following:
- [Email](#configure-email)
- [ITSM](#configure-itsm)
- [Cloud Storage](#configure-cloudstorage)
- [ChatOps](#configure-slack)
- Click **Next**.
- Review the alert rule. Click the **Edit** icon if you want to change any value.
[See image.](#alert-rule-review)
- Click **Finish**.
The newly added alert rule is displayed on the **Notifications** tab.
**[]**Select any of the following scopes:
- **Scan Plugin**: Select the IaC plugins for which alert notifications must be sent.
- **Repository**: Select the IaC repositories for which the alert notifications must be sent.
- **Select Policy**: Select the security policies for which the alert notifications must be sent. Use the **Compliance**, **Severity**, or **Policy Type** filter to search for specific policies.
[See image.](#iacalert-scope)
[]Select any of the following scopes:
- **Business Units**: Select the business units that must be associated with this alert rule. To learn more, see [About Business Units](/zpc/about-business-units).
- **Clouds**: Select the cloud service provider (AWS, Azure, or GCP).
- **Accounts**: Select the cloud accounts that must be included in this alert rule.
- **Regions**: Select the regions that must be included in this alert rule.
- **Select Policy**: Select the [security policies](/zpc/about-security-policies) that must be included in this the alert rule. Use the **Compliance**, **Severity**, **Threat Category**, or **Policy Type** filter to search for policies.
[See image.](#zpc-rule-select-policies)
[]Configure the following details:
- **Frequency**: Select the frequency (**Daily** or **Weekly**) of the notification.
- **Send At**: Select the time when the email must be sent to the recipient.
- **Timezone**: Select the time zone for the notification.
- **Include detailed report**: Select the checkbox to send the alert report as an email attachment.
- **Recipients**: Enter the email addresses of recipients.
[See image.](#email-notification)
[]Configure the following details:
- Select **ServiceNow** or **JIRA**.
- **Include in alert payload**: Select the data that must be included in the alert payload.
- **Audit Procedure**: Steps to audit the policy violation.
- **Remediation**: Steps to remediate the policy violation.
- **Resource Metadata**: The metadata of the asset or identity.
- **Assignee**: Enter the recipient's email ID.
- **Send notifications for closed alerts**: Select the checkbox to send notifications for closed alerts.
- **Send notifications for resolved alerts**: Select the checkbox to send notifications for resolved alerts.
[See image.](#ITSM)
[]Configure the following details:
- Select the checkbox for the required cloud storage service, then select the integration account from the drop-down menu.
- **Include in alert payload**: Select the data that must be included in the alert payload.
- **Audit Procedure**: Steps to audit the policy violation.
- **Remediation**: Steps to remediate the policy violation.
- **Resource Metadata**: The metadata of the asset or identity.
[See image.](#cloud-storage-details)
[]Select **Slack**, then select the required channels to which the alert notifications must be sent.
[See image.](#chatops)
[![Add an alert rule](/downloads/zpc/alerts/alert-rules/adding-iac-alert-rules/zpc-createrule.png)
]
[![Configure the email notification](/downloads/zpc/alerts/alert-rules/adding-alert-rules/zpc-alertn-email.png)
]
[![Add ITSM details](/downloads/zpc/alerts/alert-rules/adding-alert-rules/zpc-alert-rules-ITSM.png)
]
[![Add Cloud Storage details](/downloads/zpc/alerts/alert-rules/adding-alert-rules/zpc-alertn-cloudstorage.png)
]
[![Enable ChatOps](/downloads/zpc/alerts/alert-rules/adding-cloud-alert-rules/zpc-chatops-integration.png)
]
[![Select the scope and policies](/downloads/zpc/alerts/iac-alerts/adding-iac-alert-rules/zpc-iacalerts-scope.jpg)
]
[![View the Scope page](/downloads/zpc/alerts/alert-rules/adding-alert-rules/zpc-scope-select-policies.png)
]
[![Add a name and select the type of alert](/downloads/zpc/alerts/alert-rules/adding-alert-rules/zpc-alert-generalinfo.png)
]
[]![View the Alert Rules Review page](/downloads/zpc/alerts/alert-rules/adding-alert-rules/zpv-alert-rule-review.png)