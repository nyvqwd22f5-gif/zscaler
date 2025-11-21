# Configuring Settings for User Confirmation Notification Templates
Source: https://help.zscaler.com/zia/configuring-settings-user-confirmation-notification-templates
PDF: https://help.zscaler.com/pdf/com/en/1492911.pdf

When user activity triggers an Endpoint Data Loss Prevention (DLP) or Inline Web DLP rule that uses a Confirm action, the Zscaler service sends the default confirmation message based on the channel assigned to the rule (i.e., Network Share, Personal Cloud Storage, Printing, Removable Storage, and Inline Web DLP). To learn more, see [Configuring User Confirmation Notification Templates](/zia/configuring-user-confirmation-notification-templates).
Each default message uses different text and can be configured to use one of the languages supported by the Zscaler service. Additionally, you can configure global settings so that messages use your company name and logo and appear on screen for a specified amount of time.
For rules that are configured with an action other than Confirm (i.e., Allow, Block, or Protect), the Zscaler service provides a set of EUN messages that are customized separately. To learn more, see [Configuring EUNs for Endpoint DLP](/zia/configuring-euns-endpoint-dlp) and [Configuring EUNs for Inline Web DLP](/zia/configuring-euns-inline-web-dlp).
To learn more, see [Configuring Settings for User Confirmation Notification Templates](/zia/configuring-settings-user-confirmation-notification-templates), [Configuring Endpoint DLP Policy Rules](/zia/configuring-endpoint-dlp-policy-rules), [Configuring DLP Policy Rules with Content Inspection](/zia/configuring-dlp-policy-rules-content-inspection), [Configuring DLP Policy Rules without Content Inspection](/zia/configuring-dlp-policy-rules-without-content-inspection), and [Configuring DLP Policy Rules with Evaluate All Rules Mode Enabled](/zia/configuring-dlp-policy-rules-evaluate-all-rules-mode-enabled).
To configure global settings for user confirmation notification templates:
- Go to **Administration** > **Notification Templates** > **User Confirmation**.
- Click **Settings**.
The **Settings** window is displayed.
[See image.](#user-confirm-global-settings)
- Configure the following **General Details**:
- **Company Name**: Add a company name that appears on each user confirmation message. By default, the messages use Zscaler as the company name.
- **Company Logo**: Click **Upload** to upload a company logo that appears at the top of each user confirmation message. The logo must be a .png file that is 10 KB or smaller. By default, the messages use the Zscaler company logo.
- Configure the following **Duration** settings:
- **Endpoint DLP**: Select the amount of time messages remain on screen (**5 minutes**, **10 minutes**, or **30 minutes**).
- **Inline Web DLP**: Select the amount of time messages remain on screen (**15 seconds**, **30 seconds**, or **45 seconds**).
The **General Details** settings are shared with Zscaler Client Connector EUN **General Details** settings. To learn more, see [Configuring Settings for Zscaler Client Connector-Based EUNs](/zia/configuring-settings-zscaler-client-connector-based-euns).
- Click **Save** and activate the change.
[]![The User Confirmation Notification Templates Settings Window](/downloads/zia/policies/endpoint-data-loss-prevention/configuring-settings-user-confirmation-notification-templates/ZIA-DLP-User-Confirmation-Settings.png)