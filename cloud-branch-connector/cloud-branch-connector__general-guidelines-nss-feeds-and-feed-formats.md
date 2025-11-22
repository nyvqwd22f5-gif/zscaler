# General Guidelines for NSS Feeds and Feed Formats
Source: https://help.zscaler.com/cloud-branch-connector/general-guidelines-nss-feeds-and-feed-formats
PDF: https://help.zscaler.com/pdf/com/en/1420831.pdf

This article provides guidelines and information about the different feeds and fields that you can include in the NSS output for the logs.
In the Zscaler Cloud & Branch Connector Admin Portal, enter the desired fields in the Feed Output Format** **text box (Administration > Nanolog Streaming Service** **> NSS Feeds > Add NSS Feed).
Guidelines
The following guidelines are intended to help you create useful NSS outputs for your logs. These recommendations vary based on the capabilities of your security information and event management (SIEM) solution.
- Zscaler recommends not including more than 50 fields in the NSS feed to accommodate for syslog message size limits. However, if your SIEM is able to ingest larger message sizes, you can configure more than 50.
- The fields must be in the order you want them to appear in the output. Consider using name-value pairs, if your SIEM can support it. Some SIEMs, such as Splunk, can automatically parse name-value formats and auto-detect field names, regardless of the order.
- The Zscaler service hex encodes all non-printable ASCII characters that are in URLs when it sends logs to the NSS. Any URL character that is less than or equal to 0x20, or equal to and above 0x7F, is encoded as `%HH`. This ensures that your SIEM parses the URLs in case they contain control characters. For example, a `\n` character in a URL is encoded as `0A`, and a space is encoded as `%20`.
- Use tabs as field delimiters. Avoid using commas and spaces because they could be in some output values. For example, department names might contain spaces or URLs might contain commas. If you must use commas or other characters as delimiters, enter those characters in the Feed Escape Character** **field when you define an NSS feed. The service encodes the characters that you enter in this field. For example, if you enter a comma, the service encodes it as `%2C`.
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
- `"%s{time}"`,`"%s{login}"`,`"%s{proto}"\n` results in a log entry that looks like: `"Mon Sep 10 10:50:46 2012","jdoe@example.com", "HTTP"`
- `%s{time}\t%s{login}\t%s{proto}\n` results in a log entry that looks like:
`Mon Sep 10 10:50:46 2012jdoe@example.comHTTP`
- Field names are case-sensitive.
- Escape special characters with `\`, `{`, `}` or `%`. For example: `%s{login}: \{%s{hostname}\}` generates a log entry similar to the following: `user@example.com: {www.zscaler.com}`
- You can optionally include static text strings in the output. For example: `%s{time} GMT` produces: `Mon Sep 10 10:50:46 2012 GMT`
- You can also specify the padding if you want constant width strings. For example:
- `%d{hh}:%d{mm}:%d{ss}` produces `21:5:0`
- `%02d{hh}:%02d{mm}:%02d{ss}` produces `21:05:00`
- You must escape `%` with another `%`
- You can break up a long output format into multiple lines for readability. For example, the following format string:
%s{time}\t%s{proto}\t%s{url}\t%s{login}\t%s{dept}\t%s{urlcat}\t%s{urlsupercat}\t%s{urlclass}\t%s{location}\t%s{ua}\n
can be specified as:
%s{time}\t%s{proto}\t%s{url}\t
%s{login}\t%s{dept}\t
%s{urlcat}\t%s{urlsupercat}\t%s{urlclass}\t
%s{location}\t%s{ua}\n
- NSS can buffer logs for at least one hour. If a SIEM goes offline for maintenance or if the connection between the NSS and the SIEM is disrupted, the NSS buffers the logs and sends them when the connection is re-established. There can be a difference between the time the SIEM becomes unavailable and the time that the NSS detects that the SIEM is unavailable. When you configure an NSS feed, you can use the Duplicate Logs option to control the period of time from before the NSS detects the SIEM for which it resends logs. You configure up to 16 NSS feeds for each NSS.
For example, the SIEM went offline at 6:29:00 PM, the NSS detected the lost connection at 6:30:00 PM, and the connection was restored at 6:40:00 PM.
- If Duplicate Logs is set to 5 minutes, the NSS resends the logs from 6:25:00 onwards, after the connection is restored. It sends 5 minutes of duplicate logs.
- If Duplicate Logs is disabled, the NSS resends the logs from 6:30:01 onwards, after the connection is restored.
Each log record has a unique ID stored in the recorded field that is used to discover duplicate logs.