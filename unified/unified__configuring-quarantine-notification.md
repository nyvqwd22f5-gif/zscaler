# Configuring the Quarantine Notification
Source: https://help.zscaler.com/unified/configuring-quarantine-notification
PDF: https://help.zscaler.com/pdf/com/en/1493836.pdf

When a [Sandbox rule](/unified/configuring-sandbox-policy) is triggered to quarantine (First-Time Action set to Quarantine) unknown files that users attempt to download, the Zscaler service displays a notification to inform the user about the policy action taken. This end user notification (EUN) has a default template that you can view and customize per your requirements.
[See image.](#quarantine-notification)
The Sandbox analysis might take a few minutes, depending on the size and type of the file being analyzed. If the file is determined to be safe after the analysis, the download begins automatically. If the file is determined to be unsafe, the file download is blocked. To learn more, see [Configuring the Sandbox Policy](/unified/configuring-sandbox-policy).
To customize the quarantine notification:
- Go to **Policies **>** Common Configuration **>** Resources **>** End User Notifications **>** Browser **>** Global Configuration**.
- On the **End User Notifications** page:
- Under the **Configure Notifications **section,** **choose the **Default** **Notification Type **from the drop-down menu, and configure the following options:
- **Display Reason**: Enable this option to display why access to a file is restricted in the end user notification.
- **Display Company Name**: Enable this option to display the name of your organization in the end user notification.
- **Display Company Logo**: Enable this option to display the logo of your organization in the end user notification. The option to upload your company logo is available on the [Company Profile](/unified/about-company-profile) page.
[See image.](#settings)
- These settings within the **Configure Notifications **section are also applied to [block notifications](/unified/configuring-block-notifications) and [caution notifications](/unified/configuring-caution-notification).
- The custom notification type is not applicable to the Quarantine notification.
- Under the **Quarantine Notifications **section, enter the **Notification Text** that must appear in the quarantine notification. This text box contains the default message displayed by Zscaler in the quarantine notification, which you can view and customize. You can use HTML, CSS styles, and JavaScript to customize the text. To learn more, see [Customizing EUNs with CSS Styles](/unified/customizing-euns-css-styles).
When customizing the message, ensure that you provide information about the time taken for Sandbox analysis of a file to keep users informed about the wait time. This detail is part of the default message, and it is recommended to leave it as is or add a similar note.
[See image.](#customize-quarantine-notification-text)
In addition to the notification text configured here, the quarantine notification includes texts that are auto-generated when users visit sites that may violate your organization's usage policies. You cannot modify these auto-generated texts but you can [customize the appearance](/unified/customizing-euns-css-styles) of the texts or hide them with CSS styles.
- Under the **IT Support **section, enter one or more of the following contact details so users can seek additional information about the policy action taken:
- **Email**: Enter an email address to which your users reach out to learn and understand your company's IT security policies.
- **Phone**: Enter a phone number to allow users to contact you to learn and understand your company's IT security policies.
- **Policy Link**: Enter the URL of your organization's page that describes your current policy on using the corporate network and internet resources.
[See image.](#it-support)
The options within the **IT Support** section are also applied to [Acceptable Use Policy](/unified/configuring-acceptable-use-policy), [block notifications](/unified/configuring-block-notifications), and [caution notifications](/unified/configuring-caution-notification).
- Click **Save** and activate the change.
[]![Quarantine notification displayed when files are analyzed by Sandbox](/downloads/zia/authentication-administration/end-user-notifications/configuring-quarantine-notification/quarantine-eun.png)
[]![A screenshot of the end user notification settings](/downloads/zia/authentication-administration/end-user-notifications/configuring-quarantine-notification/configure-notifications.png)
[]![A screenshot of the quarantine notification text customization window](/downloads/zia/authentication-administration/end-user-notifications/configuring-quarantine-notification/quarantine-notification-text.png)
[]![A screenshot of the IT support fields in the end user notification](/downloads/zia/authentication-administration/end-user-notifications/configuring-quarantine-notification/IT-support-fields.png)