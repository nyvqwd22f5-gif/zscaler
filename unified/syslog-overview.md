# Syslog Overview
Source: https://help.zscaler.com/zia/syslog-overview
PDF: https://help.zscaler.com/pdf/com/en/1401366.pdf

This article provides an overview of the log messages that are being streamed through the Nanolog Streaming Service (NSS) to your security information and event management (SIEM) system. To learn more about syslog and syslog formatting, see the [syslog Wikipedia page](https://en.wikipedia.org/wiki/Syslog).
Syslog Formats
The RFC 5424 and RFC 3164 are two types of syslog formats, with RFC 5424 replacing the latter as the standard log message.
RFC 5424
RFC 5424 is now the standard BSD syslog format. The following is an example log message, which contains a header, structured data (SD), and message (MSG):
![Screenshot of a sample RFC 5424 syslog message](/downloads/zia/documentation-knowledgebase/analytics/nss/siem-integration-nss/nss-configuration-example-microsoft-sentinel/RFC%205424.png)
- The syslog header for this format contains:
- `<34>`:** **The priority number ([**Facility Number** x **8**] + **Severity**). In this example, the **Facility Number** is **4** (Auth), and the **Severity** is **2** (Critical).
- `1`: The version number.
- `2003-10-11T22:14:15.003Z`: The timestamp. It contains the year, the time zone, and sub-second information.
- `mymachine.example.com`: The hostname where the message was written.
- `su`: The application. Typically, this is the process name.
- In this example, the dashes are places for the PID, message ID, and other structured data you might have.
- Structured data is in key=value format within square brackets. It provides a mechanism to express information in a defined and interpretable data format that can be parsed.
- The MSG for this syslog format is everything after the header and structured data. In this example, the MSG is `'su root' failed for lonvick on /dev/pts/8.`
RFC 3164
RFC 3164 is considered the original standard BSD syslog format. The following is an example log message, which contains a header and MSG:
![Screenshot of a sample RFC 3164 syslog message](/downloads/zia/documentation-knowledgebase/analytics/nss/siem-integration-nss/nss-configuration-example-microsoft-sentinel/RFC%203164.png)
- The syslog header for this format contains:
- `<34>`:** **The priority number ([**Facility Number** x **8**] + **Severity**). In this example, the **Facility Number** is **4** (Auth), and the **Severity** is **2** (Critical).
- `Oct 11 22:14:15`:** **The timestamp. Unlike RFC 5424, this timestamp does not contain the year, the time zone, or sub-second information.
- `mymachine`: The hostname where the message was written.
- `su`: The tag. Typically, this is the process name, however, it sometimes contains a process ID (PID) (e.g.,` su[1234]:`).
- The MSG for this syslog format is everything after the tag. In this example, the MSG is `'su root' failed for lonvick on /dev/pts/8.`
Syslog Formats Used by SIEMs
Zscaler supports many syslog formats. This includes industry standard formats and the ability to create custom log strings. The Common Event Format (CEF) and Log Event Extended Format (LEEF) are two primary standards used by SIEMs.
Common Event Format (CEF)
CEF is an open log management standard that improves the interoperability of security-related information from different security and network devices and applications. The following is an example CEF message format:
CEF:Version|Device Vendor|Device Product|Device Version|Signature ID|Name|Severity|Extension
Log Event Extended Format (LEEF)
LEEF is a customized event format created by IBM QRadar. It's designed to describe network security events and uses encoding and transport similar to those used by CEF. However, the two formats differ in the number and types of fields. To learn more, see the [IBM product documentation](https://www.ibm.com/support/knowledgecenter/SS42VS_DSM/com.ibm.dsm.doc/c_LEEF_Format_Guide_intro.html). The following is an example LEEF message format:
LEEF:2.0|Vendor|Product|Version|EventID|(Delimiter Character, optional if
the Delimiter Character is tab)|Extension