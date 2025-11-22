# About Rules
Source: https://help.zscaler.com/unified/about-rules
PDF: https://help.zscaler.com/pdf/com/en/1491756.pdf

The Rules page provides an overview of details of all the configured rules, including each rule's status and alert delivery method. Rules allow you to configure metrics for alert throttling when a predetermined threshold is met.
Rules provide the following benefits and enable you to configure rules by:
- Grouping ZDX Scores based on Departments, Cities, Organization, Region, or Zscaler Locations (specified Rule Type as ZDX Score).
- Providing application details (e.g., ZDX Score, Page Fetch Time) that meet the pre-defined threshold (specified Rule Type as Application).
- Customizing alert triggering based on pre-defined throttling thresholds and In Group criteria (e.g., Organization, Cities).
The predetermined threshold is defined when you create a rule for alert throttling. To learn more, see [Triggering an Alert](/unified/triggering-alert).
If the rules are not muted, you can configure alerts to be sent via email or webhooks. If the rules are muted, you can view the alerts in the Admin Portal and no information is sent via email or webhooks.
In the Rules page, you can use the following filters:
- **All Applications & Probes**: You can filter for specific applications or probes.
- **All Severities**: You can filter for rules configured for High, Medium, or Low severity.
- **All Locations**: You can filter for specific locations.
Apply filters to further sort the data. By default, all filters are applied, and the values are set to **All**. Click **Reset** to reset the filters.
About the Rules page
On the Rules page, you can view the following for all the configured rules:
- **Rule Name**: The alert rule name entered at configuration.
- **Status**: This can be Enabled or Disabled.
- **Last Triggered**: The date and time that the rule last triggered an alert.
- **Type**: This can be for an Application, Device, or Network.
- **Application**: The application associated with this rule.
- **Probe**: The probe configured for this application.
- **Alert Delivery Method**: Email or webhook, if configured. If the rule is muted, or no alert delivery method has been configured, this field is empty.
On the Rules page, you can do the following:
- Apply filters to sort alert rules and view details.
- View criteria details of configured rules. Click the arrow to the left of the rule name to view details.
- Configure a new rule by clicking **Add Alert Rule**. To learn more, see [Configuring a Rule](/unified/configuring-alert-rule).
- Edit, mute, unmute, copy, or delete a rule. To learn more, see [Editing a Rule](/unified/editing-alert-rule).
The Edit icon opens the Edit window for the selected rule. The Copy icon opens the Copy window with editable fields and copied details of the selected rule.
![Overview of the Rules Page](/downloads/zdx/about-rules/ZDX-AboutRules-0.jpg)