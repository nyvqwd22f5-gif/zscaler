# NSS Feed Output Format: Admin Audit Logs
Source: https://help.zscaler.com/unified/nss-feed-output-format-admin-audit-logs
PDF: https://help.zscaler.com/pdf/com/en/1497831.pdf

The Admin Audit Nanolog Streaming Service (NSS) feed specifies the data from the Admin Audit logs that the NSS sends to the security information and event management (SIEM) system. You can configure an NSS feed by including one or more fields. The fields and their values display in the NSS feed output.
- [View a sample Admin Audit log.](#sample-logs)
The following tables display information about the Admin Audit log fields and possible values for those fields.
Date/Time
| Field | Description | Example |
| ----- | ----------- | ------- |
| %s{time} | The time and date of the transaction. This excludes the time zone. | Mon Oct 16 22:55:48 2023 |
| %s{tz} | The time zone. This is the same as the time zone you specified when you configured the NSS feed. | GMT |
| %02d{ss} | Seconds (0–59) | 48 |
| %02d{mm} | Minutes (0–59) | 55 |
| %02d{hh} | Hours (0–23) | 22 |
| %02d{dd} | The day of the month (1–31) | 16 |
| %02d{mth} | The month of the year | 10 |
| %04d{yyyy} | Year | 2023 |
| %s{mon} | The name of the month | Oct |
| %s{day} | The day of the week | Mon |
Audit Logs
-
-
-
-
-
-
-
-
-
-
-
| Field | Description | Example |
| ----- | ----------- | ------- |
| %d{recordid} | The unique record identifier for each log |  |
| %s{action} | The action performed by the admin in the Admin Portal | ActivateCreateDelete |
| %s{category} | The location in the Admin Portal where the action was performed | Data Loss Prevention Resource |
| %s{subcategory} | The sub-location in the Admin Portal where the action was performed | DLP Dictionary |
| %s{resource} | The specific location within a sub-category | SSL Rule NameUser Object Name |
| %s{interface} | The means by which the user performs their actions | The interface will either be the Admin UI or an API |
| %s{adminid} | The admin's login ID | example@zscaler.com |
| %s{clientip} | The source IP address for the admin |  |
| %s{result} | The outcome of an action |  |
| %s{errorcode} | An optional field that exists only if the result is a failure | AUTHENTICATION_FAILEDINVALID_INPUT_ARGUMENT |
| %s{auditlogtype} | The Admin Audit log type | ZIA Portal Audit LogBranch Connector Portal Audit LogZDX Portal Audit LogClient Connector Portal Audit Log |
| %s{preaction} | Data before any policy or configuration changes |  |
| %s{postaction} | Data after any policy or configuration changes |  |
Hex-Encoded Fields
The Zscaler service hex encodes all non-printable ASCII characters that are in URLs when it sends logs to the NSS. Any URL character that is less than or equal to 0x20, or greater than or equal to 0x7F, is encoded as `%HH`. This ensures that your SIEM can parse the URLs that contain control characters. For example, a `\n` character in a URL is encoded as `%0A`, and a space is encoded as `%20`.
The following fields have been added as hex-encoded fields:
- epreaction
- epostaction
- eresource
[]"Tue Jun 7 07:50:48 2022","7536","ACTIVATE","ACTIVATION","ACTIVATION","com.zscaler.zdx.service.ActivationService$ActivationStatus","UI","zdx-admin@92713.zscalertwo.net","10.36.112.101","SUCCESS","Unknown","ZDX","{"status":"pending"}","{"status":"active"}"