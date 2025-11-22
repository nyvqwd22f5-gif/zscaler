# Understanding the Log Stream Content Format
Source: https://help.zscaler.com/zpa/understanding-log-stream-content-format
PDF: https://help.zscaler.com/pdf/com/en/1483966.pdf

The following information includes specifications and guidelines about the log field format that is used by these log types: App Connector
- [Audit Logs](/zpa/about-audit-log-fields)
- [App Connector Metrics](/zpa/about-app-connector-metrics-log-fields)
- [App Connector Status](/zpa/about-connector-status-log-fields)
- [Browser Access](/zpa/about-browser-access-log-fields)
- [Microsegmentation Flow](/zpa/about-microsegmentation-flow-log-fields)
- [Private Cloud Controller Metrics](/zpa/understanding-private-cloud-controller-metrics-log-fields)
- [Private Cloud Controller Status](/zpa/understanding-private-cloud-controller-status-log-fields)
- [Private Service Edge Metrics](/zpa/about-private-service-edge-metrics-log-fields)
- [Private Service Edge Status](/zpa/about-private-service-edge-status-log-fields)
- [User Activity](/zpa/about-user-activity-log-fields)
- [User Status](/zpa/about-user-status-log-fields)
- [Web Inspection](/zpa/about-web-inspection-log-fields)
While [configuring your log receiver](/zpa/configuring-log-receiver), you can edit the default Log Stream Content to include customized log fields. For example, when configuring your log receiver using the [App Connector Status](/zpa/about-connector-status-log-fields) log type, the `ConnectionLogType` field can be added as a custom log field to distinguish between AppProtection and event logs. The expected values for this field are `event_log` and `inspection_log`. The supported log field format specification must be included (i.e., %[OPT]s, %[OPT]j, %[OPT]J, %[OPT]d, %[OPT]x, %[OPT]f, %[OPT]o).
Log Field Format Specifications
The field format string contains arbitrary text with the following escape formats, where [OPT] is an optional field width/precision of the style, implemented by printf. You can also specify the padding if you want constant width strings. For example:
- `%d{LogTimestamp:hh}:%d{LogTimestamp:mm}:%d{LogTimestamp:ss}` would appear as `21:5:0`
- `%02d{LogTimestamp:hh}:%02d{LogTimestamp:mm}:%02d{LogTimestamp:ss}` would appear as `21:05:00`
The <field_name>, as shown below, is substituted by the corresponding value when the log receiver sends logs to the SIEM.
[][]
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
-
-
-
-
[][][][][][]
| Field Format Specification | Description |
| -------------------------- | ----------- |
| %[OPT]s{<field_name>} | Displays the field as a string. For example, `User is %s{user_id}, and time is %s{startrx_us:iso8601}` would appear as `User is john.doe, and time is 2017-09-05T09:44:06.363Z`. |
| %[OPT]s{LogTimestamp:<field_name>} | Displays the LogTimestamp field as a string. You can use the following special characters for timestamps (in epoch):us = microseconds (0 to 999999)ms = milliseconds (0 to 999)ss = seconds (0 to 59)mm = minutes (0 to 59)hh = hours (0 to 23)dd = day of month (1 to 31)mth = month of year (1 to 12)mon = name of month (3 characters)yyy = year (3 digits)day = day of week (3 characters)time = example: Thu Sep 6 22:55:48 2012iso8601 = example: 2017-09-05T09:44:06.363Zepoch = epoch in secondsepoch_ms = epoch in millisecondsepoch_us = epoch in microsecondsFor example, `%s{LogTimestamp:time}` would appear as `Mon Sep 10 10:50:46 2012` |
| %[OPT]j{<field_name>} | Displays the field as a JSON string with quotation marks |
| %[OPT]J{<field_name>} | Displays the field as a JSON string without quotation marks |
| %[OPT]d{<field_name>} | Displays the field in decimal integer format |
| %[OPT]x{<field_name>} | Displays the field as a number in hexadecimal (base-16) format |
| %[OPT]f{<field_name>} | Displays the field as a float |
| %[OPT]o{<field_name>} | Displays the field in a 256-bit (64 character) one-way hashed (obfuscated) form. If you want a smaller obfuscation string, you can use precision limiting. |
Log Field Format Guidelines
The applicability of the following log field format guidelines and recommendations might vary based on the capabilities of your SIEM:
- Fields must be in the order you want them to appear in the output. If your SIEM can support it, consider using name-value pairs. Some SIEMs, such as Splunk, can automatically parse name-value formats and auto-detect field names regardless of the order. To learn more about third-party SIEM integrations, see [ZPA and Splunk Deployment Guide](/zpa/zpa-and-splunk-deployment-guide) and the [Zscaler and Splunk Deployment Guide](/zscaler-technology-partners/zscaler-and-splunk-deployment-guide).
- Field names are case-sensitive.
- The following special characters can be used generate control outputs:
- \t = tab
- \n = newline
- \r = carriage return
- The default Log Stream Content automatically adds a newline (\n) character after the last field. If you have modified the content, you must append at least one newline character after the last field.
- Optionally, you can include static text strings in the output. For example, `User is %s{user_id}, and time is %s{LogTimestamp:time} GMT` would appear as `User is john.doe, and time is Mon Sep 10 10:50:46 2012 GMT`