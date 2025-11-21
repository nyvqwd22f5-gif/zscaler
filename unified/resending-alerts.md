# Resending Alerts
Source: https://help.zscaler.com/zia/resending-alerts
PDF: https://help.zscaler.com/pdf/com/en/1399141.pdf

[Watch a video about Alerts, including how to resend them](https://fast.wistia.net/embed/iframe/tuy0r93wba)
You can choose to send additional alerts every time the event's threshold is reached.
To resend alerts:
- Go to **Administration **>** ****Alerts**.
- Click the **Global Configuration** tab.
- Under **Resend Active Alerts Every**, choose the interval at which the Zscaler service sends an alert after the first alert is sent, if the event continues to occur. You can choose to send alerts every:
- **30 Minutes**
- **1 Hour**
- **6 Hours**
- **12 Hours**
- **24 Hours**
[See image.](#Image)
For example, choosing **30 Minutes** means that the service will send the next "5 viruses in 5 minutes" alert 30 minutes after the first alert. Choosing **1 Hour** means that the service will send a second alert an hour after the first.
[![Screenshot of drop-down menu with time interval options for when to resend active alerts](/downloads/zia/documentation-knowledgebase/managing-admins/admin-alerts-and-audit-logs/admin-alerts/how-do-i-resend-alerts/active_alerts_time_intervals_screenshot.png)
]