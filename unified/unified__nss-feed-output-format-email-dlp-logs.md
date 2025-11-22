# NSS Feed Output Format: Email DLP Logs
Source: https://help.zscaler.com/unified/nss-feed-output-format-email-dlp-logs
PDF: https://help.zscaler.com/pdf/com/en/1503451.pdf

The Email Data Loss Prevention (DLP) Nanolog Streaming Service (NSS) feed specifies the data from the Email DLP logs that the NSS sends to the security information and event management (SIEM) system. You can configure an NSS feed by including one or more fields. The fields and their values display in the NSS feed output.
- [View a sample Email DLP log.](#sample-logs)
The following tables display information about the Email DLP log fields and possible values for those fields.
Date/Time
| Field | Description | Example |
| ----- | ----------- | ------- |
| %s{time} | The log time (i.e., when a transaction is logged by the Zscaler Nanolog) | Mon Oct 14 22:55:48 2024 |
| %u{ss} | Seconds (0–59) | 48 |
| %u{mm} | Minutes (0–59) | 55 |
| %u{hh} | Hours (0–23) | 22 |
| %s{day} | The day of the week | Mon |
| %u{dd} | The day of the month (1–31) | 14 |
| %s{mon} | The name of the month | Oct |
| %u{mth} | The month of the year | 10 |
| %u{yyyy} | Year | 2024 |
| %s{rtime} | The feed time (i.e., when a transaction is received by the NSS from the Nanolog) | Mon Oct 14 22:55:48 2024 |
| %u{rss} | Seconds (0–59) as recorded in the feed time (`%s{rtime}`) | 48 |
| %u{rmm} | Minutes (0–59) as recorded in the feed time (`%s{rtime}`) | 55 |
| %u{rhh} | Hours (0–23) as recorded in the feed time (`%s{rtime}`) | 22 |
| %s{rday} | The day of the week as recorded in the feed time (`%s{rtime}`) | Mon |
| %u{rdd} | The day of the month (1–31) as recorded in the feed time (`%s{rtime}`) | 14 |
| %s{rmon} | The name of the month as recorded in the feed time (`%s{rtime}`) | Oct |
| %u{rmth} | The month of the year as recorded in the feed time (`%s{rtime}`) | 10 |
| %u{ryyyy} | Year as recorded in the feed time (`%s{rtime}`) | 2024 |
| %s{tz} | The time zone. This is the same as the time zone you specified when you configured the NSS feed. | GMT |
Data Center Information
| Field | Description | Example |
| ----- | ----------- | ------- |
| %s{datacenter} | The name of the data center | Georgia |
| %s{datacentercity} | The city where the data center is located | Atlanta |
| %s{datacentercountry} | The country where the data center is located | US |
User Information
| Field | Description | Example |
| ----- | ----------- | ------- |
| %s{company} | The name of the company | Company Name |
| %s{departmentname} | The name of the department | Finance |
| %s{username} | The user who sent the email and is provisioned to Internet & SaaS | name@company.com |
| %s{extusername} | The user who sent the email but is not provisioned to Internet & SaaS. The external user can be within your organization. For example, a new employee joins the company and their company email address is created, but their user account is not configured in the Admin Portal. In this case, the employee is treated as an external or "non-provisioned" user even though they are part of the company and can send email from their official company email address. | name@externalcompany.com |
| %s{owner} | The username or email address of the user who sent the email. This field is an aggregate of `%s{username}` and `%s{extusername}`. If the user is provisioned to Internet & SaaS, they populate in `%s{username}` and `%s{owner}`. If the user is not provisioned to Internet & SaaS, they populate in `%s{extusername}` and` %s{owner}`. The fields `%s{username}` and `%s{extusername}` are not populated at the same time. The field `%s{owner}` is always populated whether the user is provisioned to Internet & SaaS or not. | name@company.com |
| %s{sender} | The username or email address of the user who sent the email. This field is an aggregate of `%s{username}` and `%s{extusername}`. If the user is provisioned to Internet & SaaS, they populate in `%s{username}` and `%s{sender}`. If the user is not provisioned to Internet & SaaS, they populate in `%s{extusername}` and `%s{sender}`. The fields `%s{username}` and `%s{extusername}` are not populated at the same time. The field `%s{sender}` is always populated whether the user is provisioned to Internet & SaaS or not. | name@company.com |
Email Information
| Field | Description | Example |
| ----- | ----------- | ------- |
| %s{mail_sent_time} | The date and time at which the email was sent | Mon Oct 14 22:50:48 2024 |
| %s{epochmail_sent_time} | The date and time at which the email was sent in epoch format | 1728946548 |
| %s{tenant} | The name of the email tenant | zlsr.onmicrosoft.com |
| %s{appname} | The name of the email application | Exchange |
| %s{msgid} | The unique email message identifier | <MN6PR20MB64253CC1C> |
| %s{subject} | The subject of the email | Subject Example |
| %s{ac_md5s} | The MD5 hash of the email attachment | [938c2cc0dcc05f2b68c4287040cfcf71|154f149b1443fbfa8c121d13e5c019a1] |
| %s{ac_sizes} | The size of the email attachment in bytes | [1 KB|5 MB] |
| %s{ac_filetypes} | The file type of the email attachment | [doc|pdf] |
| %s{ac_doctypes} | The document type of the email attachment | [Corporate Finance|Invoice] |
| %s{ac_names} | The file name of the email attachment | [file_name_1.doc|file_name_2.pdf] |
| %s{trigg_rcpts} | The recipients of an email that triggered a DLP rule (i.e., an action was taken) | [admin@company.com|name@company.com] |
| %s{other_rcpts} | The recipients of an email that did not trigger a DLP rule (i.e., no action was taken) | [name@externalcompany.com] |
| %s{trigg_rcpt_doms} | The domain of the recipients of an email that triggered a DLP rule (i.e., an action was taken) | [company.com|company.com] |
| %s{other_rcpt_doms} | The domain of the recipients of an email that did not trigger a DLP rule (i.e., no action was taken) | [externalcompany.com] |
DLP Information
| Field | Description | Example |
| ----- | ----------- | ------- |
| %llu{scan_time} | The DLP engine scan time in milliseconds | 1210 |
| %llu{dlpidentifier} | The unique DLP identifier | 7353686383933915137 |
| %s{dlpdictnames} | The name of the DLP dictionary | [Technical Document|Tax Identification Number] |
| %s{dlpdictcnts} | The number of hits for each of the DLP dictionaries | [12|13] |
| %s{dlpengnames} | The name of the DLP engine | [HIPAA|PCI] |
| %llu{recordid} | The unique record identifier | 7353686396818817024 |
| %s{logtype} | The type of record (i.e., DLP Incident, Sensitive Activity, or Scan). A DLP incident means that a DLP rule violation was detected. A sensitive activity means that movement of sensitive data was detected. A scan is considered normal (i.e., no DLP rule violation or movement of sensitive data was detected). | DLP Incident |
| %s{severity} | The severity. A DLP incident violates a DLP rule and the severity (i.e., High, Medium, Low, Information) is based on the rule that was violated. A sensitive activity does not violate a rule but is reported for visibility (i.e., Information). A scan does not violate a rule and the field displays `NA`. | [High Severity|Info Severity] |
| %s{actions} | The action taken (i.e., Allow, Block, Custom Header Insertion). The Zscaler service either allows or blocks transactions. Other actions (e.g., quarantine) are taken by the email application (e.g., Microsoft Exchange) as defined by a custom header (e.g., X-Zscaler-Scan:Quarantine). | [Allow|Block] |
| %s{rulelabels} | The name of the DLP rule | [DLP_Rule_1|DLP_Rule_2] |
[]{ "sourcetype" : "zscalernss-emaildlp", "event" :{"mailsenttime":"Wed Apr  3 09:58:51 2024","scantime":"3731","recordid":"7353686396818817024","company":"casb","tenant":"zslronmicrosoft","user":"sec_name@zslr.onmicrosoft.com","dept":"Engineering","filenames":"credit_ssn14Dec.pdf","filemd5s":"8573f6c2a0c9ec7232026c246b5a9f84","doctypes":"Unknown","filesizes":"20858","filetypes":"pdf","dlpdictnames":"Credit Cards: Detect leakage of credit card information|Social Security Number (US): Detect leakage of United States Social Security Numbers|US Passport Number","dlpdictcnts":"7|7|6","dlpengnames":"Credit-Card-Engine|The Originlal Burrito|ccn and ssn|US PII Alert Only|Compliance - GLBA|Compliance - PIPEDA|Compliance - U.K. PIOCP|Social Security Number OCR","dlpidentifier":"7353686383933915137","triggeredrcpts":"name@zscaler.com|name@gmail.com","severity":"High Severity|High Severity","action":"None|None","rulename":"","otherrcpts":"None","subject":"test sensitive 1","msgid":"<MN6PR20MB64256686FB0324A8F413C70DB73D2@MN6PR20MB6425.namprd20.prod.outlook.com>"}}