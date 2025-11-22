# NSS Feed Output Format: SaaS Security Activity Logs
Source: https://help.zscaler.com/unified/nss-feed-output-format-saas-security-activity-logs
PDF: https://help.zscaler.com/pdf/com/en/1497821.pdf

The SaaS Security Activity Nanolog Streaming Service (NSS) feed specifies the data from the SaaS Security Activity logs that the NSS sends to the security information and event management (SIEM) system. You can configure an NSS feed by including one or more fields. The fields and their values display in the NSS feed output.
- [View a sample SaaS Security Activity log.](#nss-feed-output-saas-security-activity-example)
The following tables display information about the SaaS Security Activity log fields and possible values for those fields.
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
SaaS Security Activity Logs
-
-
| Field | Description | Example |
| ----- | ----------- | ------- |
| %s{username} | The user who performed the activity | pshah@zslr.onmicrosoft.com |
| %s{is_admin_act} | Indicates if the user who performed the activity is an administrator | 1 = Yes0 = No |
| %s{tenant} | The SaaS application tenant associated with the activity | od-test |
| %s{objtypename1} | The object type associated with the activity | File |
| %s{objtypename2} | The second object type associated with the activity, if applicable | Folder |
| %s{appname} | The SaaS application associated with the activity | ONEDRIVE |
| %s{objnames1} | The object name associated with the first object type | sanity2022-09-04 00-06.pdf |
| %s{objnames2} | The object name associated with the second object type, if applicable | Maverick |
| %d{act_cnt} | The activity count | 55 |
| %s{act_type_name} | The type of activity performed by the user | Download |
| %s{eventtime} | The event time of the activity | Tue Oct 18 10:24:53 2022 |
| %s{extownername} | The external owner of the SaaS application | app@sharepoint |
| %s{src_ip} | The IP address associated with the activity | 104.129.203.39 |
[]"unknown_saas_user$@65605.zscaler.net","od-test","2","ONEDRIVE","[sanity2022-08-18 03-18.pdf,]","None"