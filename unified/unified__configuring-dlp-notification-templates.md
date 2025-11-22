# Configuring DLP Notification Templates
Source: https://help.zscaler.com/unified/configuring-dlp-notification-templates
PDF: https://help.zscaler.com/pdf/com/en/1493311.pdf

You can create templates for the email notification, which can be referenced while configuring policy rules for inline web Data Loss Prevention (DLP), Data at Rest Scanning DLP, Outbound Email DLP, and Endpoint DLP. To learn more, see [Configuring DLP Policy Rules with Content Inspection](/unified/configuring-dlp-policy-rules-content-inspection), [Configuring DLP Policy Rules without Content Inspection](/unified/configuring-dlp-policy-rules-without-content-inspection), [Configuring DLP Policy Rules with Evaluate All Rules Mode Enabled](/unified/configuring-dlp-policy-rules-evaluate-all-rules-mode-enabled), [Configuring the Data at Rest Scanning DLP Policy](/unified/configuring-data-rest-scanning-dlp-policy), [Configuring Outbound Email Policy Rules](/unified/configuring-outbound-email-policy-rules), and [Configuring Endpoint DLP Policy Rules](/unified/configuring-endpoint-dlp-policy-rules).
[]To add a DLP notification template:
- Go to **Policies **> **Data Protection **>** Common Resources **>** Notification Templates**.
- On the **DLP** tab, click **Add DLP Notification Template**.
-
In the **Add DLP Notification Template** window:
- Enter a **Name** for the notification.
-
By default, the **Subject** line for the notification uses the text `DLP Violation:` with the `${TRANSACTION_ID}` and `${RULENAME}` macros. These macros list the ID of the transaction that triggered the DLP rule as well as the triggered DLP rule's name. However, you can modify this text. You can include the `${USER}` macro for all three notification template types, and include the `${URL}` macro for inline web DLP and Data at Rest Scanning DLP, as well.
You can use the following macros in the subject line:
- [Macros for Inline Web DLP](#web-dlp-subject-line)
- [Macros for Data at Rest Scanning DLP](#casb-dlp-subject-line)
- [Macros for Outbound Email DLP](#email-dlp-subject-line)
- [Macros for Endpoint DLP](#endpoint-dlp-subject-line)
- Enable **Attach Violating Content** if you want an attachment of the violating content added to the notifications emailed to auditors.
-
Enable **Use TLS** to use a TLS connection to send the notification email. If you enable this option, ensure that the email recipient's SMTP server supports TLS. Zscaler recommends that you use TLS because any email you send might contain sensitive content.
These attachments and the violating content contained in them are never stored on disk. The attachments, violating content, and body of the notification emails are placed in RAM, and the Zscaler service creates and sends an encrypted email through TLS. All data is then deleted from RAM and no sensitive information is stored.
-
In the **Message as Plain Text** or **Message as HTML** section, you can create a customized message detailing why the content triggered DLP rule. This message is delivered through email (Delivery Status Notification) to the auditor when a policy triggers and blocks content.
The following macros can be used in the message body:
- [Macros for Inline Web DLP](#web-dlp)
- [Macros for Data at Rest Scanning DLP](#casb-dlp)
- [Macros for Outbound Email DLP](#email-dlp)
- [Macros for Endpoint DLP](#endpoint-dlp)
For inline web DLP and Data at Rest Scanning DLP, the `${TRANSACTION_ID}`, `${USER}`, `${URL}`, `${TYPE}`, `${DLPMD5}`, `${ENGINES_IN_RULE}`, and `${DICTIONARIES}` macros are included in the notification by default.
[See image.](#AddDLPNotification_img)
- Click **Save** and [activate the change](/unified/saving-and-activating-changes-admin-portal).
[]To modify an existing DLP notification template:
- Go to **Policies **> **Data Protection **>** Common Resources **>** Notification Templates**.
- On the **DLP** tab, locate the notification template you want to modify in the table, and click the **Edit** icon.
-
You can edit the **Name**, **Subject**, **Message as Plain Text**, and **Message as HTML** fields. You can also enable or disable the **Attach Violating Content** and **Use TLS** settings.
[See image.](#EditDLPNotification_img)
The **Message as Plain Text** field and the **Message as HTML** field are independent of one another (i.e., if you make a change in one field, you must manually update the other field to reflect the same change).
- Click **Save** and [activate the change](/unified/saving-and-activating-changes-admin-portal).
- []`${ACTION}`: Specifies the action of the triggered DLP rule (i.e., whether the transaction was allowed or blocked).
- `${DEPARTMENT}`: Shows the department of the user who triggered the DLP rule.
- `${DLPMD5}`: Provides the MD5 hash of the file that triggered the DLP rule. You can use this number as a filter in the Web Logs to find the relevant transactions.
- `${ENGINE_EXPRESSION}`: Specifies the DLP engine expression associated with the triggered policy, which includes how the Boolean operators and DLP dictionaries are combined logically.
- `${ENGINES}`: Lists the DLP engines associated with the triggered policy.
- `${FILENAME}`: Specifies the name of the file that triggered the DLP rule.
- `${FILESIZE}`: Specifies the size of the file that triggered the DLP rule.
- `${REFERRER_URL}`: Shows the referrer URL of the user who triggered the DLP rule.
- `${RULENAME}`: Specifies the name of the triggered DLP rule.
- `${TIMESTAMP}`: Specifies the time the user attempted to send violating content.
- `${TOTAL_TRIGGERED_DICTIONARIES}`: Specifies the total number of DLP dictionaries triggered across all DLP rules.
- `${TOTAL_TRIGGERED_ENGINES}`: Specifies the total number of DLP engines triggered across all DLP rules.
- `${TRANSACTION_ID}`: Provides the transaction ID of the transaction that triggered a DLP rule. You can use this unique number as a filter in the Web Logs to find the relevant transactions.
- `${URL}`: Specifies the destination URL (i.e., the URL accessed).
- `${USER}`: Specifies the name of the user, if any. If the user's name is unavailable, "unknown" is used.
- []`${ACTION}`: Specifies the action of the triggered Data at Rest Scanning DLP rule (i.e., whether the transaction was allowed or blocked).
- `${DLPMD5}`: Provides the MD5 hash of the file that triggered the Data at Rest Scanning DLP rule. You can use this number as a filter in the Web Logs to find the relevant transactions.
- `${ENGINE_EXPRESSION}`: Specifies the DLP engine expression associated with the triggered policy, which includes how the Boolean operators and DLP dictionaries are combined logically.
- `${ENGINES}`: Lists the DLP engines associated with the triggered policy.
- `${FILENAME}`: Specifies the name of the file that triggered the Data at Rest Scanning DLP rule.
- `${RULENAME}`: Specifies the name of the triggered Data at Rest Scanning DLP rule.
- `${TIMESTAMP}`: Specifies the time the user attempted to send violating content.
- `${TOTAL_TRIGGERED_DICTIONARIES}`: Specifies the total number of DLP dictionaries triggered across all Data at Rest Scanning DLP rules.
- `${TOTAL_TRIGGERED_ENGINES}`: Specifies the total number of DLP engines triggered across all Data at Rest Scanning DLP rules.
- `${TRANSACTION_ID}`: Provides the transaction ID of the transaction that triggered a Data at Rest Scanning DLP rule. You can use this unique number as a filter in the Web Logs to find the relevant transactions.
- `${URL}`: Specifies the destination URL (i.e., the URL accessed).
- `${USER}`: Specifies the name of the user, if any. If the user's name is unavailable, "unknown" is used.
[]`${TRANSACTION_ID}`: Provides the transaction ID of the transaction that triggered an Outbound Email DLP rule. You can use this unique number as a filter in the Web Logs to find the relevant transactions.
The **Subject** field is automatically populated with the `${TRANSACTION_ID}` and `${RULENAME}` macros; however, the Zscaler service does not support the `${RULENAME}` macro for the subject line in Outbound Email DLP notification templates.
- []`${ACTION}`: Specifies the action of the triggered DLP rule (i.e., whether the transaction was allowed or blocked).
- `${DLPMD5}`: Provides the MD5 hash of the file that triggered the Endpoint DLP rule. You can use this number as a filter in the Endpoint Logs to find the relevant activities.
- `${ENGINE_EXPRESSION}`: Specifies the DLP engine expression associated with the triggered policy, which includes how the Boolean operators and DLP dictionaries are combined logically.
- `${ENGINES}`: Lists the DLP engines associated with the triggered policy.
- `${FILENAME}`: Specifies the name of the file that triggered the Endpoint DLP rule.
- `${RULENAME}`: Specifies the name of the triggered Endpoint DLP rule.
- `${TIMESTAMP}`: Specifies the time the user attempted an activity that used violating content.
- `${TOTAL_TRIGGERED_DICTIONARIES}`: Specifies the total number of DLP dictionaries triggered across all Endpoint DLP rules.
- `${TOTAL_TRIGGERED_ENGINES}`: Specifies the total number of DLP engines triggered across all Endpoint DLP rules.
- `${TRANSACTION_ID}`: Provides the transaction ID of the transaction that triggered an Endpoint DLP rule. You can use this unique number as a filter in the Endpoint Logs to find the relevant transactions.
- `${USER}`: Specifies the name of the user, if any. If the user's name is unavailable, "unknown" is used.
- []`${ACTION}`: Specifies the action of the triggered DLP rule (i.e., whether the transaction was allowed or blocked).
- `${CLIENT_IP}`: Specifies the user's IP address, if available.
- `${DICTIONARIES}`: Lists the DLP dictionaries associated with the triggered policy, which includes the match count (for dictionaries such as Credit Cards) or score (for machine learning dictionaries such as Financial Statements or Source Code), for each dictionary triggered due to a content match.
[See image.](#DictionariesMacro-web-dlp)
- `${DICTIONARIES_IN_RULE}`: Lists the DLP dictionaries associated with the triggered DLP rule.
- `${DICTIONARIES_NOT_IN_RULE}`: Lists the triggered DLP dictionaries that aren’t associated with the triggered DLP rule, but are associated with other DLP rules.
The `${DICTIONARIES_IN_RULE}` and `${DICTIONARIES_NOT_IN_RULE}` macros share a maximum limit and can only list up to 25 dictionaries combined. If more than 25 dictionaries are triggered, the `${DICTIONARIES_IN_RULE}` macro is prioritized.
For example, an uploaded document triggers a total of 35 dictionaries in your DLP policy. Of those 35 dictionaries:
- 15 dictionaries are associated with the triggered DLP rule and the `${DICTIONARIES_IN_RULE}` macro lists all 15 dictionaries.
- 20 dictionaries aren’t associated with the triggered DLP rule and the `${DICTIONARIES_NOT_IN_RULE}` macro only lists 10 of those dictionaries due to the maximum limit.
- `${DLPMD5}`: Provides the MD5 hash of the file that triggered the DLP rule. You can use this number as a filter in the Web Logs to find the relevant transactions.
- `${DLPTRIGGERS}`: Lists the content (up to 10 items) that matched a dictionary, as well as a 15-byte prefix and suffix around the DLP trigger to provide context about the DLP incident.
- `${ENGINE_EXPRESSION}`: Specifies the DLP engine expression associated with the triggered policy, which includes how the Boolean operators and DLP dictionaries are combined logically.
- `${ENGINES}`: Lists the DLP engines associated with the triggered policy.
- `${ENGINES_IN_RULE}`: Lists the DLP engines associated with the triggered DLP rule.
- `${ENGINES_NOT_IN_RULE}`: Lists the triggered DLP engines that aren’t associated with the triggered DLP rule, but are associated with other DLP rules.
The `${ENGINES_IN_RULE}` and `${ENGINES_NOT_IN_RULE}` macros share a maximum limit and can only list up to 25 engines combined. If more than 25 engines are triggered, the `${ENGINES_IN_RULE}` macro is prioritized.
For example, an uploaded document triggers a total of 35 engines in your DLP policy. Of those 35 engines:
- 15 engines are associated with the triggered DLP rule and the `${ENGINES_IN_RULE}` macro lists all 15 engines.
- 20 engines aren’t associated with the triggered DLP rule and the `${ENGINES_NOT_IN_RULE}` macro only lists 10 of those engines due to the maximum limit.
- `${FILENAME}`: Specifies the name of the file that triggered the DLP rule.
- `${FILETYPE}`: Specifies the file type of the file that triggered the DLP rule.
-
`${OTHER_MATCHED_RULES}`: Specifies up to 8 rules that were matched but not triggered for a violation.
The `${OTHER_MATCHED_RULES}` macro applies only to organizations with Evaluate All Rules mode enabled. If you do not have Evaluate All Rules mode enabled, this macro does not return a value. To learn more, see [Configuring DLP Policy Rules with Evaluate All Rules Mode Enabled](/unified/configuring-dlp-policy-rules-evaluate-all-rules-mode-enabled).
- `${RULENAME}`: Specifies the name of the triggered DLP rule.
- `${SEVERITY}`: Specifies the triggered DLP rule's severity (i.e., Information, Low, Medium, or High).
- `${TIMESTAMP}`: Specifies the time the user attempted to send violating content.
- `${TOTAL_TRIGGERED_DICTIONARIES}`: Specifies the total number of DLP dictionaries triggered across all DLP rules.
- `${TOTAL_TRIGGERED_ENGINES}`: Specifies the total number of DLP engines triggered across all DLP rules.
- `${TRANSACTION_ID}`: Provides the transaction ID of the transaction that triggered a DLP rule. You can use this unique number as a filter in the Web Logs to find the relevant transactions.
- `${TYPE}`: Specifies the [Cloud App category](/unified/understanding-cloud-app-categories) for the destination traffic. For example, "File Sharing" can be a type. If the destination does not match any Cloud App categories, the type is "Web Posting."
- `${URL}`: Specifies the destination URL (i.e., the URL accessed).
- `${USER}`: Specifies the name of the user, if any. If the user's name is unavailable, "unknown" is used.
- []`${CASB}`: Specifies the name of the SaaS application tenant, the file path of the file that triggered the Data at Rest Scanning DLP rule, collaborators, and collaboration scope.
- `${DICTIONARIES}`: Lists the DLP dictionaries associated with the triggered policy, which includes the match count (for dictionaries such as Credit Cards) or score (for machine learning dictionaries such as Financial Statements or Source Code), for each dictionary triggered due to a content match.
[See image.](#DictionariesMacro-casb-dlp)
- `${DLPMD5}`: Provides the MD5 hash of the file that triggered the Data at Rest Scanning DLP rule. You can use this number as a filter in the Web Logs to find the relevant transactions.
- `${DLPTRIGGERS}`: Lists the content (up to 10 items) that matched a dictionary.
- `${ENGINES}`: Lists the DLP engines associated with the triggered policy.
- `${FILENAME}`: Specifies the name of the file that triggered the Data at Rest Scanning DLP rule.
- `${RULENAME}`: Specifies the name of the triggered Data at Rest Scanning DLP rule.
- `${TIMESTAMP}`: Specifies the time the user attempted to send violating content.
- `${TRANSACTION_ID}`: Provides the transaction ID of the transaction that triggered a Data at Rest Scanning DLP rule. You can use this unique number as a filter in the Web Logs to find the relevant transactions.
- `${TYPE}`: Specifies the [Cloud App category](/unified/understanding-cloud-app-categories) for the destination traffic. For example, "File Sharing" can be a type. If the destination does not match any Cloud App categories, the type is "Web Posting."
- `${USER}`: Specifies the name of the user, if any. If the user's name is unavailable, "unknown" is used.
- []`${EMAIL_DETAILS}`: Returns a table that is common for all recipients and includes details about the email that triggered the DLP rule. The table includes the following columns:
- `TRANSACTION_ID`: Specifies the transaction ID of the email transaction that triggered the DLP rule.
- `USER`: Shows the email address of the user who sent the email that triggered the DLP rule.
- `RECIPIENTS`: Lists all recipients of the email that triggered the DLP rule, separated by commas.
- `SUBJECT`: Shows the original subject line of the email that triggered the DLP rule.
- `${EMAIL_TRIGGERED_RECIPIENTS}`: Returns a dynamic table that includes details about the recipients of the email that triggered the DLP rule. The table includes the following columns:
- `RECIPIENT`: Specifies the email address of the recipient.
- `MD5`: Specifies the MD5 hash of the content of the triggered DLP rule.
- `ACTION`: Specifies the action of the triggered DLP rule (i.e., Block, Allow, or Custom Header).
- `SEVERITY`: Specifies the triggered DLP rule's severity (i.e., Information, Low, Medium, or High).
- `RULE NAME`: Specifies the name of the triggered DLP rule.
- `${ENGINES_IN_RULE}`: Lists the DLP engines associated with the triggered DLP rule.
- `${DICTIONARIES}`: Lists the DLP dictionaries associated with the triggered policy, which includes the match count (for dictionaries such as Credit Cards) or score (for machine learning dictionaries such as Financial Statements or Source Code), for each dictionary triggered due to a content match.
- []`${ACTION}`: Specifies the action of the triggered Endpoint DLP rule (i.e., whether the activity was allowed, blocked, or required user confirmation).
- `${DICTIONARIES_IN_RULE}`: Lists the DLP dictionaries associated with the triggered Endpoint DLP rule.
- `${DLPMD5}`: Provides the MD5 hash of the file that triggered the Endpoint DLP rule. You can use this number as a filter in the Endpoint Logs to find the relevant transactions.
- `${DLPTRIGGERS}`: Lists the content (up to 10 items) that matched a dictionary.
- `${EPDLP_ACTTYPE}`: Specifies the type of activity performed by the user (i.e., printing, uploading to personal cloud, saving to removable storage, or saving to network share).
- `${EPDLP_CHANNEL}`: Specifies the channel used when the Endpoint DLP rule was triggered (i.e., Printing, Removable Storage, Network Share, or Personal Cloud Storage).
- `${EPDLP_CON_ACT}`: Specifies the confirmation action taken by the end user after the Endpoint DLP rule was triggered (i.e., justify or cancel). This macro applies only when the rule **Action** is **Confirm**.
- `${EPDLP_CON_JUS}`: Specifies the justification provided by the end user after the Endpoint DLP rule was triggered. This macro applies only when the rule **Action** is **Confirm**.
- `${EPDLP_DEVNAME}`: Specifies the hostname of the device used when the Endpoint DLP rule was triggered.
- `${EPDLP_DST_LOC}`: Specifies the destination location of the file that triggered the Endpoint DLP rule.
- `${EPDLP_DSTNAME}`: Specifies the name of the destination for the data associated with the activity (e.g., printer name, removable storage device name, network share, or personal cloud storage service).
- `${EPDLP_DSTTYPE}`: Specifies the destination type for the data associated with the activity (e.g., application, local drive, printer, etc.).
- `${EPDLP_SRC_LOC}`: Specifies the source location of the file that triggered the Endpoint DLP rule.
- `${EPDLP_SRCNAME}`: Specifies the name of the source for the data associated with the activity (i.e., hostname, application name, network share, etc.).
- `${EPDLP_SRCTYPE}`: Specifies the source type for the data associated with the activity (i.e., application, local drive, web, etc.).
- `${ENGINES_IN_RULE}`: Lists the DLP engines associated with the triggered Endpoint DLP rule.
- `${FILENAME}`: Specifies the name of the file that triggered the Endpoint DLP rule.
- `${FILETYPE}`: Specifies the file type of the file that triggered the Endpoint DLP rule.
- `${RULENAME}`: Specifies the name of the triggered Endpoint DLP rule.
- `${TIMESTAMP}`: Specifies the time the user attempted an activity that violated Endpoint DLP policy.
- `${TOTAL_TRIGGERED_DICTIONARIES}`: Specifies the total number of DLP dictionaries triggered across all Endpoint DLP rules.
- `${TOTAL_TRIGGERED_ENGINES}`: Specifies the total number of DLP engines triggered across all Endpoint DLP rules.
- `${TRANSACTION_ID}`: Provides the transaction ID of the activity that triggered an Endpoint DLP rule. You can use this unique number as a filter in the Endpoint Logs to find the relevant transactions.
- `${USER}`: Specifies the name of the user, if any. If the user's name is unavailable, "unknown" is used.
- [Sample Endpoint DLP message as plain text](#edlp-sample-plaintext)
- [Sample Endpoint DLP message as HTML](#edlp-sample-html)
[]
`
The attached content triggered an Endpoint DLP rule for your organization.
Rule Name: ${RULENAME}
Time: ${TIMESTAMP}
User: ${USER}
Device Name: ${EPDLP_DEVNAME}
Action: ${ACTION}
Confirm Action: ${EPDLP_CON_ACT}
User Justification: ${EPDLP_CON_JUS}
Channel: ${EPDLP_CHANNEL}
File Name: ${FILENAME}
File Type: ${FILETYPE}
Source Name: ${EPDLP_SRCNAME}
File Source Location: ${EPDLP_SRC_LOC}
Destination Name: ${EPDLP_DSTNAME}
File Destination Location: ${EPDLP_DST_LOC}
File MD5: ${DLPMD5}
Transaction ID: ${TRANSACTION_ID}
Triggered DLP Violation Engines (assigned to the hit rule): ${ENGINES}
Triggered DLP Violation Dictionaries (assigned to the hit rule): ${DICTIONARIES_IN_RULE}`
[]
`    <!DOCTYPE html>
<html>
<head>
<style>
.user {color: rgb(1, 81, 152);}
.url {color: rgb(1, 81, 152);}
.postingtype {color: rgb(1, 81, 152);}
.engines {color: rgb(1, 81, 152);}
.dictionaries {color: rgb(1, 81, 152);}
</style>
</head>
<body>
The attached content triggered an Endpoint DLP rule for your organization.
<br/><br/>
Rule Name: <span>${RULENAME}</span><br/>
Time: <span>${TIMESTAMP}</span><br/>
User: <span class="user">${USER}</span><br/>
Device Name: <span>${EPDLP_DEVNAME}</span><br/>
Action: <span>${ACTION}</span><br/>
Confirm Action: <span>${EPDLP_CON_ACT}</span><br/>
User Justification: <span>${EPDLP_CON_JUS}</span><br/>
Channel: <span>${EPDLP_CHANNEL}</span><br/>
File Name: <span>${FILENAME}</span><br/>
File Type: <span>${FILETYPE}</span><br/>
Source Name: <span>${EPDLP_SRCNAME}</span><br/>
File Source Location: <span>${EPDLP_SRC_LOC}</span><br/>
Destination Name: <span>${EPDLP_DSTNAME}</span><br/>
File Destination Location: <span>${EPDLP_DST_LOC}</span><br/>
File MD5: <span class="dlpmd5">${DLPMD5}</span><br/>
Transaction ID: <span class="transaction_id">${TRANSACTION_ID}</span><br/>
Triggered DLP Violation Engines (assigned to the hit rule): <span class="engines">${ENGINES_IN_RULE}</span><br/>
Triggered DLP Violation Dictionaries (assigned to the hit rule): <span class="dictionaries">${DICTIONARIES_IN_RULE}</span><br/>
<br/>
</body>
</html>`
[]`![Add DLP Notification Template page within the ZIA Admin Portal](/downloads/zia/policies/data-loss-prevention/dlp-notification-templates/configuring-dlp-notification-templates/ZIA-Add-DLP-Notification-Template-Window.png)
`
[]`![Edit DLP Notification Template page within the ZIA Admin Portal](/downloads/zia/policies/data-loss-prevention/dlp-notification-templates/configuring-dlp-notification-templates/ZIA-Edit-DLP-Notification-Template-Window.png)
`
[]`![Content including Dictionary Name and Match Count triggered by a Web DLP Rule](/downloads/zia/documentation-knowledgebase/creating-and-managing-policies/data-loss-prevention-dlp/configuring-dlp/configuring-dlp-notification-templates/zia-dlp-emailnotificationexample.png)
`
[]`![Screenshot of the email notification sent when a CASB DLP rule is triggered.](/downloads/zia/documentation-knowledgebase/creating-and-managing-policies/data-loss-prevention-dlp/configuring-dlp/configuring-dlp-notification-templates/zia-casb-dlp-emailnotificationexample.jpg)
`