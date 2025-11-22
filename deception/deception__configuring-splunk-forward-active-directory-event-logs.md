# Configuring Splunk to Forward Active Directory Event Logs
Source: https://help.zscaler.com/deception/configuring-splunk-forward-active-directory-event-logs
PDF: https://help.zscaler.com/pdf/com/en/1531338.pdf

You can configure a Splunk server to filter event logs from the Active Directory (AD) domain controllers for decoy accounts or enumeration detection. You can forward these logs to the Zscaler Deception Admin Portal when adversary actions are detected.
Prerequisites
Make sure that the following prerequisites are met:
- Configure all of the AD servers to forward security logs to the Splunk server.
- If you have selected the Deception Admin Portal to receive logs, make sure that there is network connectivity between the Splunk server and the Deception Admin Portal on TCP port 443.
- If you have selected a Decoy Connector to receive logs, make sure that there is network connectivity between the Splunk server and the Decoy Connector’s management IP on TCP port 80.
Configuring a Splunk server to forward event logs to the Deception Admin Portal
To configure a Splunk server to forward event logs to the Deception Admin Portal:
- [Download the trigger script](/deception/configuring-and-downloading-trigger-script) from the Deception Admin Portal.
- Log in to a Splunk instance.
- Go to **Search & Reporting** > **Search**.
- Create a new search.
- Open the triggers script (.txt file) downloaded from the Zscaler Deception Admin Portal, and copy the query into the **Search** textbox.
-
Click the **Magnifying glass** icon.
[See image.](#deception-ad-logs-splunk-magnify-glass)
-
Click **Save As** > **Alert**.
[See image.](#deception-ad-log-splunk-alert)
-
In the **Save As Alert** window:
- **Title**: Enter an alert title.
- **Alert type**: Select **Real-Time**.
- **Trigger alert when**: Select **Per-Result** from the drop-down menu.
- **Expires**: Enter an expiry date for the alert. For example, enter `3650` and select **day(s)** from the drop-down menu.
- **Trigger Actions**: Click **Add Actions** and select **Webhook** from the drop-down menu, and then enter the URL to the Zscaler Deception API.
- Click **Save**.
[See image.](#deception-ad-logs-splunk-config-alert)
To test AD decoys, log in to a decoy AD user account. You can see events triggered on the Splunk server and Deception Admin Portal.
[]![Splunk search query](/downloads/deception/deceive/active-directory-decoys/configuring-splunk-forward-active-directory-event-logs/zscaler-deception-splunk-copy-query.png?1655967512)
[]![Create an alert in Splunk](/downloads/deception/deceive/active-directory-decoys/configuring-splunk-forward-active-directory-event-logs/zscaler-deception-splunk-save-alert.png)
[]![Alert configuration in Splunk](/downloads/deception/deceive/active-directory-decoys/configuring-splunk-forward-active-directory-event-logs/zscaler-deception-splunk-alert-configurations.png)