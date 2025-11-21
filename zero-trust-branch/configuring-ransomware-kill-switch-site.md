# Configuring the Ransomware Kill Switch for a Site
Source: https://help.zscaler.com/zero-trust-branch/configuring-ransomware-kill-switch-site
PDF: https://help.zscaler.com/pdf/com/en/1532702.pdf

The Ransomware Kill Switch allows you to change a site's threat level color code to one of four preset severities with a single click to immediately shut down vulnerable protocols, disable access to critical networks, and minimize downtime.
To learn more about use cases and examples of use, see [Understanding the Ransomware Kill Switch](/zero-trust-branch/understanding-ransomware-kill-switch).
To configure the Ransomware Kill Switch for a site:
-
In the Zero Trust Branch Admin Portal, go to **Incident Response > Ransomware Kill Switch**.
[See image.](#rks-green)
- Select the site for which you want to change threat levels from the drop-down menu.
- Click the dial to change the threat level color code and apply the corresponding policies to the selected site.
- Green: Lowest threat level
- Yellow: Moderate risk
- Orange: High risk
- Red: Critical risk
-
Confirm the change by entering the name of the new threat level (e.g., `yellow`) in the pop-up window. Click **Confirm** to change the threat level immediately.
[See image.](#confirm-rks)
Click **Notification Settings** to optionally customize an email notification template that will be sent when the threat level is changed. Add one or more email addresses to receive the notification and edit the email text as needed.
[See image.](#rks-notify)
[]![Ransomware Kill Switch set to green](/downloads/zero-trust-branch/analytics-monitoring/configuring-ransomware-kill-switch-site/ransomware-kill-switch.png)
[]![Confirming the threat level from the Ransomware Kill Switch page.](/downloads/zero-trust-branch/analytics-monitoring/configuring-ransomware-kill-switch-site/rks-confirm.png)
[]![Email Notification Settings dialog from the Ransomware Kill Switch page.](/downloads/zero-trust-branch/analytics-monitoring/configuring-ransomware-kill-switch-site/rks-notify.png)