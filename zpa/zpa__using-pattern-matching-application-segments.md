# Using Pattern Matching for Application Segments
Source: https://help.zscaler.com/zpa/using-pattern-matching-application-segments
PDF: https://help.zscaler.com/pdf/com/en/1485996.pdf

Zscaler Private Access (ZPA) supports patterns within FQDN-based application segments. Configuring applications with pattern definition helps to build optimal configurations. It also future proofs the configuration in the case where new servers are brought online and match the existing patterns for applications. This means no configuration changes are required in the application segment definition. To learn more, see [Configuring Defined Application Segments](/zpa/configuring-application-segments).
Prerequisites
To configure pattern matching for application segments, ensure the following prerequisites are met:
- Multimatch must be enabled on the tenant. To learn more, see [Using Application Segment Multimatch.](/zpa/using-app-segment-multimatch)
- App Connectors are upgraded to version 24.298.1 or later. To learn more, see [About App Connector Groups](/zpa/about-connector-groups).
- Zscaler Client Connector is upgraded to the following versions per OS:
- Windows versions:
- 4.5.0.337 or later
- 4.4.0.379 or later
- 4.3.0.261 or later
- macOS versions:
- 4.3.1.59 or later
- 4.3.0.240 or later
Supported Patterns of Applications in Application Segments
The asterisk (*) and question mark (?) symbols are the supported characters for pattern configuration in application segments.
| **Pattern Type** | **Example** |
| ---------------- | ----------- |
| Pattern matching in the initial part of the FQDN | *.acme.com*nonprod.acme.com |
| Pattern matching in the middle part of the application | psl*.ms.acme.comwww.jira*.acme.com*w*.acme.com |
| Matching one character with “?” | w?w.jira.acme.comw??.jira.acme.com |
The maximum number of patterns an admin can configure is 500. To learn more, see [Ranges & Limitations](/zpa/ranges-limitations).
App Connector Selection
Pattern matching does not select the most specific application for App Connector selection. Therefore, ensure you have at least one App Connector group available for similar applications. To learn more, see [About App Connector Groups](/zpa/about-connector-groups).
When application access matches multiple application segments for pattern matching, the App Connector selection is based on the most specific application segments that are pattern matching, regardless of the application segment that matches the access policy rule.
The following table shows example application segment configurations:
| Application Segment Name | Domain or Pattern Match | Protocol & Port | Multimatch | Match | Server Group Name |
| ------------------------ | ----------------------- | --------------- | ---------- | ----- | ----------------- |
| AS1 | important-server*.eu.example.com | TCP/22 | Yes | Yes | SG1 |
| AS2 | important-server?.eu.example.com | TCP/22 | Yes | Yes | SG2 |
| AS3 | important-*.eu.example.com | TCP/22 | Yes | Yes | SG3 |
| AS4 | *-*.eu.example.com | All | Yes | Yes | SG4 |
| AS5 | *.eu.example.com | All | Yes | Yes | SG5 |
| AS6 | *.example.com | All | No | No | SG6 |
When a user accesses important-server1.eu.example.com on the TCP protocol for port 22, it matches AS1, AS2, AS3, AS4, and AS5 because these are the most specific application segments with pattern matching. However, since AS5 is the wildcard application segment and AS6 does not have Multimatch enabled, the App Connector selection only applies to SG1, SG2, SG3, and SG4.