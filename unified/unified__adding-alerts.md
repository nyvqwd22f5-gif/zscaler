# Adding Alerts
Source: https://help.zscaler.com/unified/adding-alerts
PDF: https://help.zscaler.com/pdf/com/en/1495126.pdf

To add alerts:
- Go to **Administration **>** Alerts **> **Platform Alerts**.
- Click the **Define Alerts** tab.
-
Click **Add Alert Definition**.
The **Add Alert Definition** window appears.
- In the **Add Alert Definition **window:
- [Alert Name](#Name)
- [Alert Class](#Class)
- [Minimum Occurrences](#Minimum)
- [WIthin Time Interval](#Time)
- [Applies To](#Applies)
- [Severity](#Severity)
- [Status](#status)
- (Optional) Enter any **Comments** about the event. The comments cannot exceed 10,240 characters.
- Click **Save** and activate the change.
To subscribe to the alert, see [Adding Alert Subscriptions](/unified/adding-alert-subscriptions). You can also [disable alerts after you create them](/unified/disabling-alerts).
[]**Alert Name** lists all the trigger events for which the Zscaler service can generate an alert. Select the specific event for which you wish to be notified. The **Policy Violation** event sends an alert if the total number of events from all other classes and categories reach the configured threshold.
[]After you choose an alert, the class of the event appears in **Alert Class.** To learn more, see [About Alerts](/unified/about-alerts-0).
[]From **Minimum Occurrences**, choose the number of times that the event must occur before an alert is generated. You can choose from 1, 5, 10, 100, or 1,000 occurrences. This value is used together with the **Within Time Interval** value. An alert is triggered when the event occurs the **Minimum Occurrences **value in the **Within Time Interval** time period.
[]From **Within Time Interval**, choose the span of time within which an event's occurrence triggers an alert. You can choose from 5 minutes, 15 minutes, 30 minutes, 1 hour, or 1 day. The service generates an alert when the event occurs the **Minimum Occurrences** value in the **Within Time Interval **time period.
[]From the **Applies To** menu, specify whether the alert is triggered by events in the organization, a location, department or user, then choose the specific location, department, or user.
[]Assign a **Severity** level of **Critical**, **Major**, **Minor**, **Info**, or **Debug **to the event. This is useful if you want to create multiple alerts for the same kind of event (such as detection of outbound viruses or data leakage), but establish different thresholds for each.
For example, you can set the severity level of an event with 5 occurrences in 5 minutes to **Minor** and set the severity level of the same event with 500 occurrences in 5 minutes to **Critical**. Set the **Severity** of each alert to reflect its threshold’s deviation from the norm.
[]From **Status**, choose either **Enabled** or **Disabled** to enable or disable the alert, respectively.