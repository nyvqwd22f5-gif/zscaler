# Configuring Settings for Zscaler Client Connector-Based EUNs
Source: https://help.zscaler.com/unified/configuring-settings-zscaler-client-connector-based-euns
PDF: https://help.zscaler.com/pdf/com/en/1508021.pdf

The Zscaler Client Connector-based end user notifications (EUNs) utilize the Zscaler Notification Framework to notify users when a policy is triggered. In addition to notification messages, these Zscaler Notification Framework-based notifications include additional information common to all Client Connector-based EUNs such as company name, logo, support information, notification duration, and actions displayed on the notification, such as option to snooze the notification, request exemption for an activity, link to the Corporate policy, etc. The options to configure these additional components are grouped under Settings on the Client Connector EUN page (Policies > Common Configuration > Resources > End User Notifications > Client Connector). To learn more, see [About Zscaler Client Connector-Based End User Notifications](/unified/about-zscaler-client-connector-based-end-user-notifications).
To configure the shared settings for Client Connector-based EUNs:
-
Go to **Policies **>** Common Configuration** >** Resources** > **End User Notifications** > **Client Connector** and click **Settings** on the top-right corner of the page.
The **Settings** window appears.
- In the **Settings** window:
- Under **Notification Actions**, select the actions that must appear in the notification displayed for the end users:
- **Learn more**: Opens the Notifications tab in the Client Connector application. This option is enabled by default and is non-editable.
- **Do Not Disturb**: Opens the More tab in the Client Connector application where the user can control the notification settings. To learn more, see [Zscaler Endpoint Data Loss Prevention (DLP) Integration with Zscaler Client Connector](/unified/zscaler-endpoint-data-loss-prevention-dlp-integration-zscaler-client-connector).
- **Open Corporate Policy**: Opens the URL specified in the text field.
-
**Open Containing Folder**: Opens the folder where files that triggered the block rule are quarantined.
This field is applicable only for Endpoint DLP policies that quarantine the original file.
-
**Request Exemption**: Opens the Data Protection tab in the Client Connector application where users can request to be exempted from the block rule application.
This field is applicable only for Endpoint DLP rules with Block action.
-
Under **General Details**, provide the following information about your organization:
- **Company Name**: Enter the company name that appears at the top of the notification.
- **Company Logo**: Upload a company logo that appears at the top of the notification. The logo must be a PNG file with a size limit of 20x20 pixels. The **Reset **option allows you to restore the default Company Logo.
Any changes made within this section are mirrored in the [User Confirmation settings](/unified/configuring-settings-user-confirmation-notification-templates) as these configurations are shared by Client Connector-based EUNs and User Confirmation notifications.
- Under **Duration**, specify whether the notification must be closed automatically or manually by the user. If you choose the **Auto Close** option, you need to specify the duration after which the notification must be closed using the drop-down menu.
- Under **Support Info**, provide your organization's contact information:
- **Email Address**: Enter your organization's email address where end users can reach out for technical support.
- **Phone Number**: Enter your organization's phone number where end users can reach out for technical support.
- **Link Text**: Enter the text for the hyperlink where end users can open a support request with your organization.
-
**URL**: Enter the URL where end users can open a support request with your organization. The URL can contain a query string that uses one or more variables supported by Zscaler. These variables allow you to transmit values and populate them in the respective fields on the support request form opened by end users using the URL. For example, `https://support.example.com/path/to/CreateTicket?name=$zcc_user&url_accessed=$url` can take users to a web page for raising a ticket that's prepopulated with the user's name and the URL that triggered the policy.
[See the list of variables supported.](#query-string-variables)
- Click **Save** and activate the change.
To learn how to customize the fields specific to individual Client Connector-based EUNs, see the respective configuration articles.
- []$filename
- $destination
- $triggered_rule
- $action
- $url
- $url_category
- $app_activity
- $app_category
- $zcc_user