# Configuring an Alert Rule for Risk360
Source: https://help.zscaler.com/unified/configuring-alert-rule-risk360
PDF: https://help.zscaler.com/pdf/com/en/1533798.pdf

You can configure alert rules for various criteria (i.e., financial loss or risk score changes at organization, category, factor group, or factor levels) that trigger an email or webhook notification to the recipients.
To configure an alert rule:
- Go to **Analytics** > **Risk360** > **Alerts** > **Rules**.
- Click **Add Alert Rule**.
-
Choose an existing rule template or start configuring from the beginning by clicking **Create New**.
[See image.](#templates)
The **Add Alert Rule** wizard appears.
-
In the **Add Alert Rule** wizard, complete the following steps:
- [a. Define Criteria & Throttling](#Criteria)
- [b. Configure Delivery Method](#Action)
The alert rule is successfully created.
[]If you've selected a rule template, the service skips to the [Configure Delivery Method](#step2) section. However, you can click **Back **to edit the predefined values in the **Define Criteria &** **Throttling** section. In this section:
- **Criteria**: Set the criteria for the alert rule to be triggered:
- Select **All** or **Any** from the drop-down menu.
- Select the item for which you want to trigger the alert from **Org**, **Category**, **Factor Group**, or** Factor**.
- Based on your selection, the next drop-down menus are auto-populated. Select the required options.
- Select the operator for the criteria, i.e., equal to (**=**), greater than (**>**), less than (**<**), greater than or equal to (**≥**), less than or equal to (**≤**), **increases by**, or **decreases by**.
- Enter the value for the operator.
-
Click **Add** to add another criterion to the rule.
For example, see the following GIF to understand how to set the criteria for an alert to be triggered when the risk score for the Data Loss category exceeds 55.
[See image.](#criteria-gif)
- **Expression Preview**: You can view a logical preview for the criteria set in the preceding fields. This field is uneditable.
- **Minimum Alert Throttling Criteria**: Enter the number of days the criteria must persist before triggering the alert notification.
- Click **Next**.
[See image.](#criteria-img)
[]In the **Configure Delivery Method **section:
- []**Rule Name**: Enter a name to identify the rule.
- **Severity**: Select the severity of the rule from **Critical**, **High**, **Medium**, or **Low**.
- **Status**: Select **Enabled** or **Disabled** for the rule.
- **Delivery Method**: Select the alert delivery methods from **Email **and** Webhook.**
- **Webhooks**: Select from the existing configured webhooks or configure a new webhook by clicking **Configure Webhooks** to receive alerts via webhooks. To learn more, see [Configuring Alert Webhooks](/unified/configuring-alert-webhooks-risk360).
- **Email Recipient**: Enter the email address to which you want the alerts to be sent. To learn more about the information sent, see [Understanding the Alert Email](/unified/understanding-alert-email-risk360).
- **Custom Message**: Enter a custom message that is displayed within the alert notification when this alert is triggered. This message is applicable for both email and webhooks.
- Click **Add**.
[See image.](#delivery-img)
[]![Risk360-Criteria-Creation.png](/downloads/risk360/administration-authentication/alerts/configuring-alert-rule/Risk360-Criteria-Creation.png)
[]![Alert Delivery](/downloads/risk360/administration-authentication/alerts/configuring-alert-rule/Risk360-Alerts-Delivery.png)
[]![Adding Criteria](/downloads/risk360/administration-authentication/alerts/configuring-alert-rule/Risk360-Alert-Rule-Criteria.gif)
[]![Alert Templates](/downloads/risk360/administration-authentication/alerts/configuring-alert-rule/Risk360-Alerts-Templates_0.png)