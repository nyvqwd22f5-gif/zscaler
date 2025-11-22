# Configuring Browser EUN Template
Source: https://help.zscaler.com/unified/configuring-browser-eun-template
PDF: https://help.zscaler.com/pdf/com/en/1507991.pdf

You can configure the browser end user notification (EUN) templates with custom block and caution messages. To display the EUN for a specific Cloud App Control Policy rule, URL Filtering rule, or File Type Control rule, select the respective [browser notification template](/unified/about-browser-eun-template) configured for that particular rule. To learn more, see [Configuring the URL Filtering Policy](/unified/configuring-url-filtering-policy), [Adding Rules to the Cloud App Control Policy](/unified/adding-rules-cloud-app-control-policy), and [Configuring the File Type Control Policy](/unified/configuring-file-type-control-policy).
Zscaler browser EUNs come with default notification messages for each policy type, which can be customized. You can customize various elements of the notification, including the notification message for different policy actions, company name, logo, information displayed on the notification, duration of the notification, and more.
To add a browser EUN template:
- Go to **Policies** > **Common Configuration** > **Resources** > **End User Notifications** > **Browser** > **Templates**.
-
On the [Browser EUN Templates](/unified/about-browser-eun-template) page, click **Add Custom Message**.
The **Add Custom Message** window appears.
- In the **Add Custom Message** window:
- Under **General**:
- **Name**: Enter a unique name for the custom message.
- **Channel**: Select the policy type (**Cloud App Control**, **URL Filtering**, or **File Type Control**) to which the notification message is added.
-
Under **Messages**, enter text to customize the **Block** and **Caution** notification messages that appear when an end user's activity triggers a Cloud App Control policy, URL Filtering rule, or File Type Control policy. The **Reset All** option allows you to restore the default notification messages provided by the service.
The browser EUN is supported for either the Block or Caution action in the [Adding Rules to the Cloud App Control Policy](/unified/adding-rules-cloud-app-control-policy), [Configuring the URL Filtering Policy](/unified/configuring-url-filtering-policy), or [File Type Control policy](/unified/configuring-file-type-control-policy).
- Under **Additional Information**, select the information that must be displayed in the notification for the following policy type:
- [Cloud App Control](#cloud-app-control)
- [URL Filtering](#url-filtering)
- [File Type Control](#file-type-control)
- Under **Preview**, you can get a full view of the notification message you configured. You can interact with the notification previews by clicking the **Show More** button to view the additional details configured. Use the **Next** and **Previous** buttons to navigate through the Block and Caution notification previews.
- Click **Save** and activate the change.
[]Select the additional information that must be displayed in the notification for Cloud App Control:
- **Cloud Application**: The application that triggered the rule in the notification. This information is selected by default and you cannot unselect it.
- **Cloud App Category**: The category of the cloud application that triggered the rule in the notification. This information is selected by default and you cannot unselect it.
- **Rule Name**: Select to include the name of the triggered rule in the notification.
- **Recommended Cloud Application**: Select to include the cloud application recommended by your organization as an alternative to the cloud application that triggered the rule in the notification.
- **App Activity**: Select to include the cloud application activity that triggered the rule in the notification.
[]Select the additional information that must be displayed in the notification for URL Filtering:
- **Website URL**: Select to include the URL that triggered the rule in the notification. This information is selected by default and you cannot unselect it.
- **URL Category**: The category of the website URL that triggered the rule in the notification. This information is selected by default and you cannot unselect it.
- **Rule Name**: Select to include the name of the triggered rule in the notification.
[]Select the additional information that must be displayed in the notification for File Type Control:
- **Cloud Application**: The application that triggered the rule in the notification.
- **Rule Name**: Select to include the name of the triggered rule in the notification.
- **Activity**: Select to include the cloud application activity that triggered the rule in the notification. This information is selected by default and you cannot unselect it.
- **File Name**: Select to include the file name that triggered the rule in the notification.
- **URL**: Select to include the URL that triggered the rule in the notification.
- **File Type**: Select to include the file type that triggered the rule in the notification. This information is selected by default and you cannot unselect it.
- **File Size**: Select to include the file size that triggered the rule in the notification.