# Configuring the Patient 0 Alert
Source: https://help.zscaler.com/zia/configuring-patient-0-alert
PDF: https://help.zscaler.com/pdf/com/en/1400816.pdf

You must have Advanced Sandbox to configure patient 0 alerts.
If you've configured the [first-time action](/zia/how-do-i-add-rules-sandbox-policy#first-time-action) of a [Sandbox rule](/zia/how-do-i-add-rules-sandbox-policy) to allow and scan unknown files, the Zscaler service:
- Allows users to download files that match the rule criteria.
- Sends the files to the Sandbox for behavioral analysis.
A patient 0 event occurs when a user downloads an unknown file that is scanned and found to be malicious. On the [Alerts page](/zia/about-alerts), you can add the patient 0 alert and receive emails about these events within approximately two hours.
[]Configuring the Patient 0 Alert
[Watch a video about Alerts, including how to configure them.](https://fast.wistia.net/embed/iframe/9to9j2rhzn)
To configure the patient 0 alert:
- [1. Add the Patient 0 Alert](#add-the-patient-0-alert)
- [2. Subscribe to the Patient 0 Alert](#subscribe-to-patient-0-alerts)
[]About the Sandbox Patient 0 Events Widget
On the [Security dashboard](/zia/about-dashboards#security), the **Sandbox Patient 0 Events** widget displays the patient 0 events that occurred in your organization.
On the **Sandbox Patient 0 Events** widget, you can see the following information:
[See image.](#seeimage4)
- **Alert Time**: Displays the time the patient 0 alert is sent.
- **MD5**: The MD5 hash of the malicious file. Click to view the following reports:
- [Sandbox Detail Report](/zia/viewing-sandbox-reports-data#about-sandbox-detail-report)
- [CrowdStrike Endpoint Hits report](/zia/viewing-crowdstrike-endpoint-hits-report) (requires a [CrowdStrike integration](/zia/configuring-crowdstrike-integration))
- **Threat**: The threat name of the malicious file. You can enter this name in the [Zscaler Threat Library](https://threatlibrary.zscaler.com/) to learn more about it.
- **Allowed Transactions**: The total number of allowed transactions that occurred with the malicious file. Click to view the transaction logs on the [Web Insights Logs](/zia/about-insights-logs) page.
If you hover over an event, you can see the following information:
[See image.](#seeimage5)
- **File Information**: Displays the following information of the malicious file.
- **File Type**: The type of file (EXE, DLL, PDF, etc.).
- **File Size**: The total bytes of the file.
- **MD5**: The MD5 hash of the file.
- **Users Affected**: Lists the users affected by the malicious file and their location.
[]To add the Patient 0 alert:
- Go to **Administration **>** Alerts**.
- On the **Define Alerts** tab, click **Add Alert Definition**.
[See image.](#seeimage1)
The **Add Alert Definition** window appears.
- In the **Add Alert Definition **window, do the following:
[See image.](#seeimage2)
- **Status**: Ensure it's **Enabled**.
- **Alert Name**: Choose **Patient 0**.
- **Comments**: (Optional) Enter any comments about the event. The comments cannot exceed 10,240 characters.
The ZIA Admin Portal automatically populates the following fields for the Patient 0 alert. You can't modify any of these fields.
- **Alert ID**: This field is blank. The service automatically assigns an ID after you create the alert.
- **Alert Class**: Set to **Patient 0**. The patient 0 alert class includes an unknown file that’s been permitted to download, but found to be malicious through behavioral analysis.
- **Minimum Occurrences**: Set to **1**. The service sends you an alert if one or more patient 0 events occur.
- **Within Time Interval**: Set to **1 hour**. The service scans for patient 0 events every hour.
- **Applies To**: Set to **Organization**. The service sends you an alert if a patient 0 event affects any user in your organization.
- **Severity**: Set to **Critical**. All patient 0 events are classified as critical because a malicious file download has been allowed.
- Click **Save**.
[]After adding the patient 0 alert, you must add a patient 0 alert subscription to receive emails about the events.
To subscribe to patient 0 alerts:
- On the Alerts page, click the **Publish Alerts** tab.
- Click **Add Alert Subscription** to add a new email recipient. If your email is already listed, click the **Edit** icon.
The **Add**/**Edit Alert Subscription** window appears.
- Under **Patient 0 Alerts**, enable **Critical**.
[See image.](#seeimage3)
- Click **Save** and [activate the change](/zia/saving-and-activating-changes-admin-portal).
[]![Screenshot of the Add Alert Definition button on the Define Alerts tab](/downloads/zia/documentation-knowledgebase/creating-and-managing-policies/sandbox/configuring-sandbox/configuring-patient-0-alerts/zia-add-alert-definition.png)
[]![Screenshot of the configured Patient 0 alert in the Add Alert Definition window ](/downloads/zia/documentation-knowledgebase/creating-and-managing-policies/sandbox/configuring-sandbox/configuring-patient-0-alert/zia-add-alert-definition-window.png)
[]![Screenshot highlighting the Critical option for Patient 0 Alerts in the Add Alert Subscription window](/downloads/zia/documentation-knowledgebase/creating-and-managing-policies/sandbox/configuring-sandbox/configuring-patient-0-alert/zia-patient-0-alerts-critical-option.png)
[]![Screenshot of the Sandbox Patient 0 Events widget.](/downloads/zia/documentation-knowledgebase/creating-and-managing-policies/sandbox/configuring-patient-0-alert/ZIA-Sandbox-Patient-0-Events-Widget.png)
[]![Screenshot of the File Information and Users Affected for a Sandbox patient 0 event.](/downloads/zia/documentation-knowledgebase/creating-and-managing-policies/sandbox/configuring-patient-0-alert/ZIA-Patient-0-Events-File-Information-Users.png)