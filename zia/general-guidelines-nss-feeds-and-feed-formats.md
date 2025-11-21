# General Guidelines for NSS Feeds and Feed Formats
Source: https://help.zscaler.com/zia/general-guidelines-nss-feeds-and-feed-formats
PDF: https://help.zscaler.com/pdf/com/en/1400786.pdf

This article provides guidelines and information about the different feeds and fields that you can include in the NSS output for logs.
In the ZIA Admin Portal, enter the desired fields in the **Feed Output Format **text box (Administration > NSS Feeds > Add NSS Feed).
Guidelines
The following guidelines are intended to help you create useful NSS outputs for your logs. These recommendations vary based on the capabilities of your security information and event management (SIEM) system.
- It's recommended not to include more than 50 fields in the NSS feed to accommodate for syslog message size limits. However, if your SIEM is able to ingest larger message sizes, you can configure more than 50.
- The fields must be in the order you want them to appear in the output. Consider using name-value pairs, if your SIEM can support it. Some SIEMs, such as Splunk, can automatically parse name-value formats and auto-detect field names, regardless of the order.
- The Zscaler service hex encodes all non-printable ASCII characters that are in URLs when it sends logs to the NSS. Any URL character that is less than or equal to 0x20, or greater than or equal to 0x7F, is encoded as `%HH`. This ensures that your SIEM can parse the URLs that contain control characters. For example, a `\n` character in a URL is encoded as `%0A`, and a space is encoded as `%20`.
- Use tabs as field delimiters. Avoid using commas and spaces because they could be in some output values. For example, department names might contain spaces or URLs might contain commas. If you must use commas or other characters as delimiters, enter those characters in the **Feed Escape Character **field when you define an NSS feed. The service encodes the characters that you enter in this field. For example, if you enter a comma, the service encodes it as `%2C`.
- The following special characters generate control outputs:
- `\t` = Tab
- `\n` = New line
- `\r` = Carriage return
- You don't need to add `\n` after the last field to indicate that it's the last entry. Zscaler automatically adds a blank line (line feed) after the last field.
- The field names specified are substituted by the corresponding value when NSS sends logs to the SIEM.
- `%s{<fieldname>}` displays the string name.
Example: `%s{time}`
- `%d{<fieldname>}` prints a number in decimal format.
Example: `%d{yyyy}`
- `%x{<fieldname>}` prints a number in hexadecimal (base-16) format.
Example: `%x{recordid}`
- The following are examples:
- `"%s{time}"`,`"%s{login}"`,`"%s{proto}"\n` results in a log entry that looks like: `"Mon Sep 18 10:50:46 2023","jdoe@example.com", "HTTP"`
- `%s{time}\t%s{login}\t%s{proto}\n` results in a log entry that looks like:
`Mon Sep 18 10:50:46 2023jdoe@example.comHTTP`
- Field names are case-sensitive.
- Special characters must be escaped with `\`, `{`, `}` or `%`. For example: `%s{login}: \{%s{hostname}\}` generates a log entry similar to the following: `user@example.com: {www.zscaler.com}`
In Cloud NSS feeds, if you select **JSON** as the **Feed Output Type**, special characters such as `\` present in string fields may cause a parsing issue for your SIEM. To prevent the issue, enter `,\"` as the **Feed Escape Character** and use hex-encoded fields (e.g., `%s{elogin}`instead of `%s{login}`) in the **Feed Output Format**`.`
- You can optionally include static text strings in the output. For example: `%s{time} GMT` produces: `Mon Sep 18 10:50:46 2023 GMT`
- You can also specify the padding if you want constant width strings. For example:
- `%d{hh}:%d{mm}:%d{ss}` produces `21:5:0`
- `%02d{hh}:%02d{mm}:%02d{ss}` produces `21:05:00`
- You can use date and time format elements to form the date-time string per your downstream requirements. For example:
- `%d{yyyy}-%02d{mth}-%02d{dd} %02d{hh}:%02d{mm}:%02d{ss}`** **produces: `2023-09-18 21:05:00`
- `%` must be escaped with another `%`
- You can break up a long output format into multiple lines for readability. For example, the following format string:
%s{time}\t%s{proto}\t%s{url}\t%s{login}\t%s{dept}\t%s{urlcat}\t%s{urlsupercat}\t%s{urlclass}\t%s{location}\t%s{ua}\n
can be specified as:
%s{time}\t%s{proto}\t%s{url}\t
%s{login}\t%s{dept}\t
%s{urlcat}\t%s{urlsupercat}\t%s{urlclass}\t
%s{location}\t%s{ua}\n
- NSS can buffer logs in the VM memory to increase its resilience to transient network issues. If the connection between the NSS and the SIEM is lost, the NSS replays the logs from the buffer and sends them to the SIEM after the connection is restored. There can be a difference between the time that the SIEM becomes unavailable and the time that the NSS *detects* that the SIEM is unavailable. When you configure an NSS feed, you can use the Duplicate Logs setting to specify when the NSS starts replaying logs from the buffer (e.g., 5 minutes before the lost SIEM connection is detected.) [See example.](#duplicate-logs-example)
Feed Formats
The following feed formats provide fields you can include in the NSS output:
- [NSS Feed Output Format: Web Logs](/zia/nss-feed-output-format-web-logs)
- [NSS Feed Output Format: Firewall Logs](/zia/nss-feed-output-format-firewall-logs)
- [NSS Feed Output Format: DNS Logs](/zia/nss-feed-output-format-dns-logs)
- [NSS Feed Output Format: Tunnel Logs](/zia/nss-feed-output-format-tunnel-logs)
- [NSS Feed Output Format: SaaS Security Logs](/zia/nss-feed-output-format-saas-security-logs)
- [NSS Feed Output Format: SaaS Security Activity Logs](/zia/nss-feed-output-format-saas-security-activity-logs)
- [NSS Feed Output Format: Admin Audit Logs](/zia/nss-feed-output-format-admin-audit-logs)
- [NSS Feed Output Format: Endpoint DLP Logs](/zia/nss-feed-output-format-endpoint-dlp-logs)
- [NSS Feed Output Format: Email DLP Logs](/zia/nss-feed-output-format-email-dlp-logs)
[]The following is an example use case for the Duplicate Logs setting:
- The SIEM goes offline at 6:29:00 PM.
- The NSS detects the lost connection at 6:30:00 PM.
- The connection is restored at 6:40:00 PM.
Based on the use case, the following results are possible:
- **If Duplicate Logs is set to 5 minutes**: After the connection is restored, the NSS sends logs from 6:25:00 PM onwards. It sends 5 minutes of logs: It duplicates logs from 6:25:00 PM to 6:28:59 PM and recovers logs from 6:29:00 PM to 6:30:00 PM.
- **If Duplicate Logs is disabled**: After the connection is restored, the NSS sends logs from 6:30:00 PM onwards. It does not recover logs from 6:29:00 PM to 6:30:00 PM.
- **If Duplicate Logs is set to 60 minutes**: After the connection is restored, the NSS sends logs from 5:30:00 PM onwards. It sends one hour of logs: It duplicates logs from 5:30:00 PM to 6:28:59 PM and recovers logs from 6:29:00 PM to 6:30:00 PM. This setting is not recommended due to the high number of duplicates to be processed by the SIEM, introducing unnecessary delay.