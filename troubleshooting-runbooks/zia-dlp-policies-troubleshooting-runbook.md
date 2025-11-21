# ZIA DLP Policies Troubleshooting Runbook
Source: https://help.zscaler.com/troubleshooting-runbooks/zia-dlp-policies-troubleshooting-runbook
PDF: https://help.zscaler.com/pdf/com/en/1532308.pdf

The Data Loss Prevention (DLP) Policies Troubleshooting Runbook serves as a comprehensive guide for configuring, fine-tuning, and troubleshooting Zscaler's DLP solutions across various scopes. It provides step-by-step methodologies to address common challenges encountered during DLP deployment and operation. The troubleshooting framework outlined in the runbook emphasizes a systematic approach by leveraging internal tools such as Web Insights logs and detailed configuration checks. By adhering to these systematic troubleshooting steps, the DLP Policy Runbook enables organizations to enhance the accuracy, effectiveness, and resilience of their data protection strategies.
Require DLP Feature Configuration Assistance or DLP Policy Fine-Tuning
Zscaler DLP offers various enhancement features that are enabled on-demand or require an additional subscription. The following examples are a few enhancements DLP policies provide.
- [Support for Correlated View of App Users and DLP File Access](/zia/release-upgrade-summary-2025?applicable_category=zscaler.net&deployment_date=2025-05-16&id=1525346): To view the information on the Files tab, you must have a license for SaaS Security Data at Rest Scanning DLP, and you must configure the DLP scan. To upgrade your license, contact your Zscaler Account team.
- [Support for SaaS Security API Data at Rest Scanning DLP Policy Rules without Content Inspection](/zia/release-upgrade-summary-2025): To enable this feature for your organization, contact [Zscaler Support](/contact-support).
- [New Predefined DLP Engines](/zia/release-upgrade-summary-2025): These engines are available by default for users with tenants enabled on April 4, 2025, or later. For enablement on existing tenants, contact [Zscaler Support](/contact-support).
Look for the following information in the [Zscaler’s Help Portal](/zia) or [Release Notes](/zia/release-notes):
- Contact your Zscaler Account team: The feature might require an additional subscription or an additional SKU, depending on your current Zscaler’s subscription. Contact your Zscaler Account team for more information.
- Contact [Zscaler Support](/contact-support): The feature is not enabled automatically for all users. Raise a Provisioning support case with Zscaler Support with the feature details and reference link from Zscaler’s Help Portal or Release Notes.
If users have configured the DLP policy but want to fine-tune the policy, consider the following policy option, if applicable:
- Configure the **Minimum Data Size (KB)**. Zscaler DLP engines support files up to 400 MB and can scan the first 100 MB of the extracted text. The maximum size also applies to files extracted from archive files. If files exceed defined thresholds for size or format compatibility, DLP inspection could fail or skip triggering policies for those files.
Review the DLP false positive events to determine a feasible value for **Minimum Data Size (KB)**. For example, if there is a lot of telemetry data smaller than 10 KB that contributes to a large volume of false positives, you can configure the **Minimum Data Size (KB)** as 10 KB and monitor again.
- Create a **DLP Allowlist** rule for HTTP Form Data based on the **Custom Allowlist URL** category. This category includes file type fallback decisions by Zscaler.
- For single-part non-URL-encoded requests, the default is **HTTP non-file text data**.
- For multipart requests and single-part URL-encoded requests, the default is **HTTP Form data**.
- Avoid configuring a catch-all DLP policy rule with ANY file type. Due to the file type fallback decisions by Zscaler, you can drop HTTP Form data from the file type list of the last catch-all rule.
- Use a combination of a **Predefined Dictionary** with a **Low **or **Medium Confidence Score Threshold **and a **Custom Dictionary** for **Pattern/Phrase**.
For example, you can create a Custom Dictionary to include keywords using patterns and phrases:
[See image.](#patterns-phrases)
- Leverage the Predefined dictionary **NRIC Numbers (Singapore)**.
- Create a new DLP Engine by using the Predefined dictionary **NRIC Numbers (Singapore) and Custom Dictionary**.
Use the Expression Preview: ((NRIC Numbers (Singapore) > 5) AND ((Identity Card Number (Phrases 1) > 0) OR (Identity Card Number (Phrases 2) > 0)))
[See image.](#dlp-engine)
Web DLP Policy (Inline DLP, OCR, EDM, and IDM) Not Working as Expected
When handling DLP policy issues, look at two areas: the DLP policy configuration on Zscaler and the input data.
The DLP policy is configured to match the DLP Engine or other criteria (with or without content matching), but the access is not triggered. You must look at the Web Insights logs for the **Blocked Policy Type** value and the **Allowed DLP Rule Name** for the reported transaction.
By default, the Zscaler service evaluates inline DLP policy rules according to rule order, with the evaluation stopping at the first match. However, if [Evaluate All Rules mode](/zia/configuring-dlp-policy-rules-evaluate-all-rules-mode) is enabled for your organization, you can instead have the Zscaler service evaluate all rules, and enforce the rule with the most restrictive action. [Evaluate All Rules mode](/zia/configuring-dlp-policy-rules-evaluate-all-rules-mode) uses rule order only when multiple rules with the same action are matched. In that case, the rule order determines which policy rule is triggered.
[Sample Web Insights Logs](#sample-web-insights-logs)
[]
The following are important Web insights fields for DLP issues.
Keep in mind that policy action depends on the [Evaluate All Rules mode](/zia/configuring-dlp-policy-rules-evaluate-all-rules-mode) setting:
[See image.](#inline-dlp-rule-eval)
- By Rule Order: Zscaler service evaluates inline DLP policy rules according to rule order, with evaluation stopping at the first match.
- Evaluate All Rules: Zscaler service evaluates all rules, enforcing the rules with the most restrictive action. Evaluate All Rules mode uses rule order only when multiple rules with the same action are matched. In that case, the rule order determines which policy rule is triggered.
| URL | DLP Engine | DLP Dictionaries | Blocked Policy Name | Blocked Policy Type | Allowed DLP Rule Name |
| --- | ---------- | ---------------- | ------------------- | ------------------- | --------------------- |
| dlptest.com/wp-admin/admin-ajax.php | SSN | SSN Regex 2 (4) | DLP_Block_SSN | Data Loss Prevention | DLP_Pre724_otherDoc |
| dlptest.com/http-post/ | Hash Engine | test (2) | DLP_Rule_Phrase | Data Loss Prevention | DLP_Pre724_otherDoc |
| lastpass.com/login_check.php | External | None | None | None | DLP_Pre724_otherDoc |
| lastpass.com/login_check.php | External | None | None | None | DLP_Pre724_otherDoc |
| storage.prod.us-east-1.w1.dataprotection.zscaler.net/browser-extensions/ | External | None | DLP_Password | Data Loss Prevention | None |
| endpoints.prod.us-east-1.w1.dataprotection.zscaler.net/api/ | 26-Thailand National Identity Card Number | 26-Thailand National Identity Card Number (Patterns) (1);26-Thailand National Identity Card Number (Phrases) (1) | DLP_NRIC_SEA | Data Loss Prevention | None |
[Troubleshooting](#troubleshoot-1)
[]
If the** Blocked Policy Type** and **Allowed DLP Rule Name** isn't **None**, this means the request matched the DLP policy. Check the following in the full web insights logs and ZIA configuration:
- Ensure the reported traffic is seen on the Web Insights logs. If the web transaction is not visible in the ZIA Web Insights logs, it is possible that the transaction is not reaching Zscaler.
- Ensure SSL inspection is enabled if the traffic is HTTPS.
- Go to **Admin UI** > **Administration **> **Resources **> **Data Loss Prevention** > **DLP Advanced Settings** and verify the following configuration:
- Check that the request traffic is included in any of the **Cloud App & URL Exceptions for DLP** configuration. These configurations are a global setting. Do not change them without fully understanding the change and impact.
- **Exempted Cloud Applications**: Add the respective cloud app if you want to bypass DLP policy.
- **Exempted URLs**: Add the respective domains if you want to bypass DLP policy.
- **Exempted User-Defined URL Categories**: Add the respective **Custom URL** category if you want to bypass DLP policy.
- **Exempt URL Encoded Data**: Enable this setting to bypass scanning the content type as `application/x-www-form-urlencoded` from DLP evaluation.
- Go to **Inline DLP Rule Evaluation** > **Evaluate All Rules**: If **Evaluate All Rules** mode is enabled for your organization, you can have the Zscaler service evaluate all rules, enforcing all rules with the most restrictive action. **Evaluate All Rules** mode uses rule order only when multiple rules with the same action are matched. In that case, the rule order determines which policy rule is triggered.
- Go to **Exact Data Match **> **Check for Popular Formats:** Enabling this reduces false positives on non-standard formats. Exact Data Match (EDM) and Indexed Document Match (IDM) require the Advanced DLP suite.
- Go to **Optical Character Recognition (OCR)** > **Inspect Images via OCR**: Ensure this setting is enabled if you want to apply DLP policy on image files.
- Review and take notes on the specific triggered DLP rule (in the Web Insights **Blocked Policy Type** or **Allowed DLP Rule Name**).
- Check if the transaction matches all the criteria configured within a DLP rule:
- **Source-related criteria**: These include Users, Groups, Departments, User Risk Profile, Locations, Location Groups, Source IP Groups.
- **Destination-related criteria**: These include URL Categories, Cloud Applications, Cloud Application Instances, Zscaler Private Access (ZPA) Application Segment.
The DLP policy applies AND logic to the URL Categories and Cloud Applications fields when inspecting your organization's traffic. In order for a DLP rule to trigger, the Zscaler service must detect the rule’s selected URL categories and cloud applications in a transaction.
- **Other criteria**: This includes Time, Protocols, File Type, and Data Size (KB).
Notes: [WebSocket Protocol](/zia/release-upgrade-summary-2025?applicable_category=zscaler.net&deployment_date=2025-05-09&id=1524391) is now supported in DLP rule.
- If **Content Matching** is enabled, record which DLP Engines are selected. Based on the DLP Engines in use, go to **Administration** > **Resources** > **Data Loss Prevention** > **DLP Dictionaries & Engines** to learn more details:
- First, check the respective DLP Engines to learn which DLP Dictionaries are involved and their **Expression**.
- View the respective DLP Engine and take a screenshot or record the **Expression Preview.**
[See image.](#expression-preview)
- When you know the DLP Dictionaries used, view the respective **DLP Dictionary** and take a screenshot.
[See image.](#patterns-phrases-edm-idm)
- Check the settings and values configured in each related DLP Dictionary:
- **Predefined Type**: Note the **Confidence Score Threshold **and **Proximity Length**.
- Special configurations like **Custom High Confidence Phrases** and **Social Security Numbers** in **Social Security Numbers (US)**.
- **Patterns & Phrases**
- **EDM**
- **IDM**
- If you have the DLP violation alert, cross-check the DLP violation criteria with the earlier steps. If your current DLP Notification Template does not include `"${DLPTRIGGERS}"`, you can create a new DLP Notification Template using the following example:
[See image.](#dlp-rule-with-without-content-match)
If your current DLP Notification Template does not include `"${DLPTRIGGERS}"`. You can create a new DLP Notification Template using the following example in the **Message as HTML** section.
`<!DOCTYPE html>
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
The attached content triggered a Web DLP rule for your organization.
<br/><br/>
Transaction Timestamp: <span class="timestamp">${TIMESTAMP}</span>
<br/>
Transaction ID: <span class="transaction_id">${TRANSACTION_ID}</span>
<br/>
Client IP Accessing the URL: <span class="client_ip">${CLIENT_IP}</span>
<br/>
User Accessing the URL: <span class="user">${USER}</span>
<br/>
Action for the access: <span class="action">${ACTION}</span>
<br/>
Rulename of DLP policy: <span class="rulename">${RULENAME}</span>
<br/>
Severity of Violation: <span class="severity">${SEVERITY}</span>
<br/>
URL Accessed: <span class="url">${URL}</span>
<br/>
Posting Type: <span class="postingtype">${TYPE}</span>
<br/>
DLP MD5: <span class="dlpmd5">${DLPMD5}</span>
<br/>
File Name: <span class="filename">${FILENAME}</span>
<br/>
File Type: <span class="filetype">${FILETYPE}</span>
<br/>
Triggered DLP Violation Engines (assigned to the hit rule): <span class="engines">${ENGINES_IN_RULE}</span>
<br/>
Triggered DLP Violation Dictionaries (assigned to the hit rule): <span class="dictionaries">${DICTIONARIES}</span>
<br/><br/>
DLP Triggers match: <span class="triggers">${DLPTRIGGERS}</span>
<br/>
No action is required on your part.
<br/><br/>
</body>
</html>`
- If no issue is found in the DLP Engines or DLP Dictionaries, check if the content is **POST **using single or multipart form submission. There is a possibility that part of a multipart/form-data payload submission hits the DLP rule.
How to Check Multipart Form Submission
A user can submit a POST request to Zscaler using a single or multipart payload submission. This affects the way the Zscaler’s DLP engine processes the data.
For example, when a user selects a single file or multiple files in one single upload, one or more files are uploaded to a website like http://dlptest.com/http-post/ using the multipart/form-data option. In a multipart payload upload, the data is divided into multiple parts with its own headers and boundaries. Each of the parts is evaluated against the Zscaler's DLP rules.
The following Chrome Browser Header indicates a multipart payload upload.
[See image.](#request-headers)
[Further Consideration](#further-consider-1)
[]
At this point, you should have verified most of the DLP-related configuration on the ZIA Admin Portal and nothing is out of the norm. You might have to create an issue summary with the compiled data and open a support case with [Zscaler Support](/contact-support).
Here is a quick checklist of the data collection:
- HTTP Header HAR file
- [Capturing HTTP Headers on Microsoft Edge](/zia/capturing-http-headers-microsoft-edge).
- [Capturing HTTP Headers on Google Chrome](/zia/capturing-http-headers-google-chrome).
- [Capturing HTTP Headers on Mozilla Firefox](/zia/capturing-http-headers-mozilla-firefox).
- [Capturing HTTP Headers on Safari](/zia/capturing-http-headers-safari).
- Wireshark capture
- For Zscaler Client Connector, use the [Packet Capture option](/zscaler-client-connector/enabling-packet-capture-zscaler-client-connector).
- Without Zscaler Client Connector, use the [Wireshark capture method](https://www.wireshark.org/docs/wsug_html_chunked/ChapterCapture.html).
- Web Insights logs with all fields selected.
- Violation content notification email or JSON file.
You can remove or obfuscate the highly sensitive data while it is still able to trigger the DLP issue.
- Sample test data. (You can skip this if the same data was provided earlier.)
- Temporarily enable [Remote Assistance](/zia/enabling-remote-assistance).
Web DLP Email or ICAP Notification Issue
Zscaler supports sending DLP violation notification delivery using email, Internet Content Adaptation Protocol (ICAP). You can integrate the ICAP option (subscription required) with a third party ICAP server or Zscaler Incident. To learn more, see [ICAP server](/zia/about-icap-communication-between-zscaler-and-dlp-servers) or [Zscaler Incident Receiver](/zia/policies/data-loss-prevention/dlp-incident-receiver).
Troubleshooting
The following sections describe troubleshooting for web DLP.
[Email Notification Issue](#email-notification)
[]
For Email Notification:
- Zscaler supports a 25 MB limit for DLP email notification attachments by default. The admin still receives the DLP email notification but without the violation content attachment. The DLP email shows a message like this:
`	Posting Type: General Browsing Post (NRIC-Large.xlsx not attached - its size 51530124 bytes exceeds archive size limit of 25MB)`
[See image.](#posting-type)
Further Steps
- What is the use case and investigate why you want to send large violation content using email.
- Use other options such as leveraging the ICAP method (integration with a third-party ICAP server, Zscaler Incident Receiver, or Zscaler Workflow Automation).
- If you have a strong, valid use case to send large violation content using email, then raise a Provisioning support case with [Zscaler Support](/contact-support) with the details.
[SMTP Delivery Issue](#smtp-delivery-issue)
[]
If the DLP policy is triggered as per Zscaler logs, and you are not getting email notifications to the configured auditor email address, then use the following sections.
SMTP Codes Reference
Zscaler Support can check the Simple Mail Transfer Protocol (SMTP) code for a particular email delivery using the DLP Identifier field from Web Insights logs. SMTP codes are three-digit numbers, such as 250, 421, or 550. The first digit indicates the general category of the response:
- 2.x.x: Positive completion reply (success).
- 3.x.x: Positive intermediate reply (command accepted, more information needed).
- 4.x.x: Transient negative completion reply (temporary error).
- 5.x.x: Permanent negative completion reply (permanent error).
Common examples:
- 220: Service ready (SMTP server is ready to accept connections).
- 250: Requested mail action okay (message delivered successfully).
- 421: Service not available, closing transmission channel (temporary issue with the server).
- 450: Requested mail action not taken: mailbox unavailable (temporary issue with the recipient's mailbox).
- 451: Requested action aborted: local error in processing (temporary error on the server).
- 500: Syntax error, command unrecognized (invalid command).
- 550: Requested action not taken: mailbox unavailable or not found (permanent error).
- 554: Transaction failed (general error during message transmission).
Troubleshooting
- Check the auditor's email address. From the ZIA Admin Portal, find the external auditor's email address by editing the relevant DLP rule. Ensure the auditor email address is correct. You can test it using a different email address (with a different email domain (e.g., gmail.com or yahoo.com).
[See image.](#auditor-email-address)
This step is not a workaround or solution but a problem isolation step. Since DLP violation might involve sensitive data, you must get the necessary internal approval before performing this test.
- Check the Web Insights logs. You can filter the Web Insights logs to display the DLP transactions. Look for the **Policy Action** column, ensure the notification for DLP was triggered as either **Violates Compliance Category, archived to mailbox**, or **Allowed and archived to mailbox**.
[See image.](#insights-logs)
Further Steps
At this point, you can compile the issue summary with the data and open a support case with [Zscaler Support](/contact-support). Here is a quick checklist of the data collection:
- Relevant configuration screenshots:
- DLP rule name
- Auditor Email address
- Web Insights logs with all fields selected.
- Temporarily enable **Remote Assistance**. To learn more, see [Enabling Remote Assistance](/zia/enabling-remote-assistance).
[ICAP Notification Issue](#icap-notification-issue)
[]
Zscaler supports secure or unencrypted ICAP receivers on the DLP notification. Zscaler recommends sending transaction information via secure ICAP.
Secure ICAP is required to set up stunnel application.
To learn more, see [About ICAP Communication Between Zscaler and DLP Servers](/zia/about-icap-communication-between-zscaler-and-dlp-servers).
[See image.](#dlp-icap-icaps-flow)
Troubleshooting
- Ensure the necessary Firewall configuration according to Zscaler's Config page.
- **DLP ICAP Requirements**. Use the following URL format: `https://config.zscaler.com/``<zscaler cloud>``/icap`, where you should replace <zscaler cloud> with your Zscaler cloud URL (e.g., https://config.zscaler.com/zscaler.net/icap).
- **DLP Incident Receiver**. Use the following URL format: `https://config.zscaler.com/``<zscaler cloud>``/dlp-incident-receiver`, where you should replace <zscaler cloud> with your Zscaler cloud URL (e.g., https://config.zscaler.com/zscaler.net/dlp-incident-receiver).
- **ZIA Advanced DLP (Private Service Edge)**. Use the following URL format: `https://config.zscaler.com/``<zscaler cloud>``/zia-private-dlp`, where you should replace <zscaler cloud> with your Zscaler cloud URL (e.g., https://config.zscaler.com/zscaler.net/zia-private-dlp).
- **ZIA Private Service Edge Access Requirements**. Use the following URL format: `https://config.zscaler.com/``<zscaler cloud>``/zia-sedge`, where you should replace <zscaler cloud> with your Zscaler cloud URL (e.g., https://config.zscaler.com/zscaler.net/zia-sedge).
- Perform a telnet to the external ICAP server IP address and port (e.g., 1344) behind an allowed network.
- If it is ICAPS, check the stunnel configuration according to the tunnel application guide. Change the configuration to an unencrypted ICAP URL and test again.
Further Steps
At this point, you can compile the issue summary with the data and open a support case with [Zscaler Support](/contact-support). Here is a quick checklist of the data collection:
- Relevant configuration screenshots:
- DLP rule name
- DLP rule’s DLP Incident Receiver setting
- DLP Incident Receiver’s configuration
- Web Insights logs with all fields selected.
- Temporarily enable **Remote Assistance**. To learn more, see [Enabling Remote Assistance](/zia/enabling-remote-assistance).
[]![Pattern](/downloads/troubleshooting-runbooks/zia-dlp-policies-troubleshooting-runbook/Pattern.png)
![Phrase](/downloads/troubleshooting-runbooks/zia-dlp-policies-troubleshooting-runbook/Phrase.png)
[]![DLP Engine](/downloads/troubleshooting-runbooks/zia-dlp-policies-troubleshooting-runbook/DLP-Engine.png)
[]![Inline DLP Rule Evaluation](/downloads/troubleshooting-runbooks/zia-dlp-policies-troubleshooting-runbook/Inline-DLP-Rule-Evaluation.png)
[]![Expression Preview](/downloads/troubleshooting-runbooks/zia-dlp-policies-troubleshooting-runbook/Expression-Preview.png)
[]![Patterns and Phrases](/downloads/troubleshooting-runbooks/zia-dlp-policies-troubleshooting-runbook/Patterns-n-Phrases.png)
![Exact Data Match (EDM)](/downloads/troubleshooting-runbooks/zia-dlp-policies-troubleshooting-runbook/Exact-Data-Match.png)
![Indexed Document Match (IDM)](/downloads/troubleshooting-runbooks/zia-dlp-policies-troubleshooting-runbook/Indexed-Document-Match.png)
[]![DLP with Content Matching](/downloads/troubleshooting-runbooks/zia-dlp-policies-troubleshooting-runbook/DLP-rule-with-Content-Matching.png)
![DLP rule without content matching](/downloads/troubleshooting-runbooks/zia-dlp-policies-troubleshooting-runbook/DLP-rule-without-Content-Matching.png)
[]![Request headers](/downloads/troubleshooting-runbooks/zia-dlp-policies-troubleshooting-runbook/Request-Headers.png)
![Payload](/downloads/troubleshooting-runbooks/zia-dlp-policies-troubleshooting-runbook/Payload.png)
[]![Posting type](/downloads/troubleshooting-runbooks/zia-dlp-policies-troubleshooting-runbook/Posting-Type.png)
[]![Auditor Email Address](/downloads/troubleshooting-runbooks/zia-dlp-policies-troubleshooting-runbook/Auditor-Email-Address.png)
[]![Web Insights Logs](/downloads/troubleshooting-runbooks/zia-dlp-policies-troubleshooting-runbook/Web-Insights-Logs.png)
[]![DLP ICAP / ICAPS Flow](/downloads/troubleshooting-runbooks/zia-dlp-policies-troubleshooting-runbook/DLP-ICAP-and-ICAPS-Flow.png)