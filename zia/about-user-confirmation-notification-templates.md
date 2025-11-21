# About User Confirmation Notification Templates
Source: https://help.zscaler.com/zia/about-user-confirmation-notification-templates
PDF: https://help.zscaler.com/pdf/com/en/1492901.pdf

You can use Endpoint Data Loss Prevention (DLP) and Inline Web DLP policies to identify and act on end user activities that involve sensitive data. If an activity is part of a necessary workflow, you can configure your Endpoint DLP and Inline Web DLP policy rules with a Confirm action that requires users to explain the activity and provide justification for why it requires sensitive data.
To learn more, see [Configuring Endpoint DLP Policy Rules](/zia/configuring-endpoint-dlp-policy-rules), [Configuring DLP Policy Rules with Content Inspection](/zia/configuring-dlp-policy-rules-content-inspection), [Configuring DLP Policy Rules without Content Inspection](/zia/configuring-dlp-policy-rules-without-content-inspection), and [Configuring DLP Policy Rules with Evaluate All Rules Mode Enabled](/zia/configuring-dlp-policy-rules-evaluate-all-rules-mode-enabled).
When user activity triggers a rule that uses a Confirm action, the Zscaler service sends the default confirmation message based on the channel assigned to the rule (i.e., Network Share, Personal Cloud Storage, Printing, Removable Storage, and Inline Web DLP). The default message for each channel provides users with a standardized set of options to justify the activity that triggered the rule. Those options cannot be configured, but you can customize the language that begins each user confirmation message. Additionally, you can configure the messages to use your company name and logo.
For rules that are configured with an action other than Confirm (i.e., Allow, Block, or Protect), the Zscaler service provides a set of EUN messages that are customized separately. To learn more, see [Configuring EUNs for Endpoint DLP](/zia/configuring-euns-endpoint-dlp) and [Configuring EUNs for Inline Web DLP](/zia/configuring-euns-inline-web-dlp).
User Confirmation notification templates provide the following benefits and allow you to:
- Configure the language that introduces the default confirmation messages users receive when the activity on an endpoint triggers an Endpoint DLP or Inline Web DLP policy rule.
- Customize the company name and logo used on confirmation messages.
About the User Confirmation Notification Templates Page
On the User Confirmation Notification Templates page (Administration > Notification Templates), you can do the following:
- View the [DLP Notification Templates](/zia/about-dlp-notification-templates) page.
- View the [Quarantine Tombstone File Templates](/zia/about-quarantine-tombstone-file-templates) page.
- View a list of the default user notification templates available for your organization. For user confirmation notification templates, you can see:
- **Channel**: The channel to which each default template is assigned. You can sort this column.
- **Name**: The default template name for each channel.
- Search for a user confirmation template.
- [Modify the table and its columns](/zia/how-do-i-use-tables-admin-portal).
- [Customize](/zia/configuring-user-confirmation-notification-templates) the introductory language for each user confirmation notification template.
- [Specify global settings](/zia/configuring-settings-user-confirmation-notification-templates) for user confirmation templates.
![Viewing and managing Endpoint DLP User Confirmation Notification Templates within the ZIA Admin Portal](/downloads/zia/policies/endpoint-data-loss-prevention/about-user-confirmation-notification-templates/ZIA-DLP-User-Confirmation-Notification-Templates-Page.png)