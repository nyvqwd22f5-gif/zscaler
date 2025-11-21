# Configuring User Confirmation Notification Templates
Source: https://help.zscaler.com/zia/configuring-user-confirmation-notification-templates
PDF: https://help.zscaler.com/pdf/com/en/1492906.pdf

When user activity triggers a rule that uses a Confirm action, the Zscaler service sends the default confirmation message based on the channel assigned to the rule (i.e., Network Share, Personal Cloud Storage, Printing, Removable Storage, and Inline Web DLP). The default message for each channel provides users with a standardized set of options to justify the activity that triggered the rule. Those options cannot be configured, but you can customize the language that begins each user confirmation message. Additionally, you can configure the messages to use your company name and logo.
To learn more, see [Configuring Settings for User Confirmation Notification Templates](/zia/configuring-settings-user-confirmation-notification-templates), [Configuring Endpoint DLP Policy Rules](/zia/configuring-endpoint-dlp-policy-rules), [Configuring DLP Policy Rules with Content Inspection](/zia/configuring-dlp-policy-rules-content-inspection), [Configuring DLP Policy Rules without Content Inspection](/zia/configuring-dlp-policy-rules-without-content-inspection), and [Configuring DLP Policy Rules with Evaluate All Rules Mode Enabled](/zia/configuring-dlp-policy-rules-evaluate-all-rules-mode-enabled).
For rules that are configured with an action other than Confirm (i.e., Allow, Block, or Protect), the Zscaler service provides a set of EUN messages that are customized separately. To learn more, see [Configuring EUNs for Endpoint DLP](/zia/configuring-euns-endpoint-dlp) and [Configuring EUNs for Inline Web DLP](/zia/configuring-euns-inline-web-dlp).
- [Add a Custom User Confirmation Notification Template](#add-custom)
- [Customize the User Confirmation Message](#edit)
[]
- Go to **Administration** > **Notification Templates** > **User Confirmation**.
- Click **Add Custom Message**.
- In the **Notification Details** section:
- Enter a **Name**.
- Select a **Channel **from the dropdown menu.
-
In the **Message** section:
- Select a language from the drop-down menu to show the introductory text for the message in that language.
- [Supported languages](#supported-languages2)
-
Update the introductory text as needed. Only the introductory text can be edited.
You can embed links in the message content by using the following format: __url[Link text | example.com]. For example, __url[Learn more | https://acme.com/policy]. You can also introduce line breaks in the message content by using the //n character.
- Preview the confirmation message in the **Preview** section.
The introductory text appears in the selected language; the options remain in English in the **Preview **but appears in the correct language on endpoints.
If the endpoint OS is set to one of the supported languages, then the confirmation message appears in that language on the endpoint. If the endpoint OS is set to an unsupported language, then the confirmation message appears in English.
[See image.](#add-custom-message)
- Click **Save** and activate the change.
[]
- Go to **Administration** > **Notification Templates** > **User Confirmation**.
- Locate the user confirmation template in the table and click **Edit**.
- In the **Message** section:
- Select a language from the drop-down menu to show the introductory text for the message in that language.
- [Supported languages](#supported-languages)
-
Update the introductory text as needed. Only the introductory text can be edited.
You can embed links in the message content by using the following format: __url[Link text | example.com]. For example, __url[Learn more | https://acme.com/policy]. You can also introduce line breaks in the message content by using the //n character.
- Preview the confirmation message in the **Preview** section.
The introductory text appears in the selected language; the options remain in English in the **Preview **but appears in the correct language on endpoints.
If the endpoint OS is set to one of the supported languages, then the confirmation message appears in that language on the endpoint. If the endpoint OS is set to an unsupported language, then the confirmation message appears in English.
[See image.](#edit-custom-message-window)
- Click **Save** and activate the change.
[]
- English (Default)
- Chinese (Traditional)
- French
- German
- Japanese
- Spanish
[]
- English (Default)
- Chinese (Traditional)
- French
- German
- Japanese
- Spanish
[]![Add Custom Message to Endpoint DLP Rule](/downloads/zia/policies/about-user-confirmation-notification-templates/add-custom-message-window.png)
[]![Endpoint DLP Edit Custom Message Window](/downloads/zia/policies/endpoint-data-loss-prevention/configuring-user-confirmation-notification-templates/ZIA-EndpointDLP-Edit-Custom-Message-Window-L10N.png)