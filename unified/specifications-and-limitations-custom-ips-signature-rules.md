# Specifications and Limitations for Custom IPS Signature Rules
Source: https://help.zscaler.com/unified/specifications-and-limitations-custom-ips-signature-rules
PDF: https://help.zscaler.com/pdf/com/en/1494331.pdf

The following sections provide information on Zscaler's support for Snort rules in [custom IPS signature rules](/unified/about-custom-ips-signature-rules), including the features supported and limitations:
- [Basic Differences from Snort](#differences-from-snort)
- [Supported Snort Options](#supported-snort-options)
- [Limitations](#limitations)
[]The following table outlines the key differences in Zscaler's rule evaluation methods from Snort:
-
-
| Category | Specifications | Example |
| -------- | -------------- | ------- |
| Scan size limit | **Default scan size limit**: 4,000 bytes per session (includes traffic originating from the server and the client)**Maximum scan size limit**: 32,000 bytes per session (specified using the `max_scan_size` option in a rule)The scan size limit applies to traffic in bidirectional flow unless the rule specifies either `flow:to_server` or `flow:from_server` option.Scanning of packets ends when the limit for scan size or the number of packets is reached. | alert tcp any any -> any 21 (msg:"DoS"; flow:to_server; content:”Test”; max_scan_size:100; classtype:DoS;)This rule applies the scan limit on the traffic sent to the server. |
| Packet limit | **Default packet limit**: 16 packets (includes traffic originating from the server and the client)Scanning of packets ends when the limit for scan size or the number of packets is reached. | alert tcp any any -> any 21 (msg:"DoS"; flow:to_server; content:”Test”; max_scan_size:100; max_count:10; classtype:DoS;)This rule stops the Zscaler service from scanning after 10 packets from both directions, or after 100 bytes of traffic from the client. |
[]Snort rules in custom IPS signatures support the following Snort options and event filters:
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
-
-
- [](#pcre-flags)[](#pcre-constructs)
| **Option/Event Filter** | **Description** | **Notes** |
| ----------------------- | --------------- | --------- |
| byte_extract | Allows writing rules against length-encoded protocols. It extracts a specified number of bytes from the payload and saves it to a variable, which can be referenced later in the same rule. | The dce option is not supported. |
| byte_jump | Allows rules to read the length of a portion of data, then skip that far into the packet. | The dce option is not supported. |
| byte_test | Tests a byte field against a specific value (with operator). | The dce option is not supported. |
| content | Allows you to configure rules that search for specific content in the packet payload and trigger response based on that data. | The content data must be at least 5 bytes long.If the content option is used more than once within a rule, the distance option must be specified between the content options. |
| depth | A modifier for content/PCRE that specifies how far into a packet Snort should search for the specified pattern. | By default, depth is applied on each packet. To match a pattern over a stream, use the flow:stream keyword.**Example**:alert tcp any any -> any 21 (content:”SMB”; flow:stream; offset:4; depth:5;)In this example, the rule searches for patterns that occur between 4 and 10 bytes in the entire stream irrespective of the number of packets scanned. If the first packet is 10 bytes long, then the search terminates in the first packet. |
| detection_filter | Defines a rate which must be exceeded by a source or destination host before a rule can generate an event. | The rate can be tracked using standard attributes supported by Snort, such as source IP and destination IP. In addition, the Zscaler service provides exclusive by_srcport and by_dstport options to track by source port and destination port respectively. The count is maintained for each unique entity.Zscaler recommends using detection filters in conjunction with event filters to effectively reduce the number of logged events for noisy rules. |
| distance | A modifier for content/PCRE that specifies how far into a packet Snort should ignore before starting to search for the specified pattern relative to the end of the previous pattern match. | N/A |
| dsize | Tests the packet payload size. |  |
| event_filter | Limits the number of times a particular event is logged during a specified time interval. | The rate can be tracked using standard attributes supported by Snort, such as source IP and destination IP. In addition, the Zscaler service provides exclusive by_srcport and by_dstport options to track by source port and destination port respectively. The count is maintained for each unique entity.The event_filter option must be specified within a rule and cannot be used as standalone configurations. |
| fast_pattern | A content modifier that sets a content option within a rule to be used with the fast pattern matcher. | If fast_pattern is not specified in a rule, the longest content within the rule becomes the fast pattern. A fast pattern can be automatically determined only for content unmodified with distance or within.The length of a fast pattern ranges from 3 bytes to 16 bytes. If a pattern is longer than 16 bytes, the string that occupies the first 16 bytes is selected as the fast pattern.Fast patterns do not support the negation (!) operator.Zscalerrecommends using the fast_pattern:only option to specify fast patterns that exceed 16 characters/bytes. It is also recommended to place the fast pattern in the right order within the rule if multiple content options are present. |
| flags | Checks if specific TCP flag bits are present. It also supports ignoring specific TCP flag bits. | N/A |
| flow | Applies rules to traffic flowing in specific directions. | **Options supported:**to_serverto_clientfrom_clientfrom_serverestablished (always enabled)no_stream |
| isdataat | Verifies that the payload has data at a specified location. | N/A |
| nocase | A modifier for content/PCRE that ignores letter cases during a pattern search. | N/A |
| offset | A modifier for content/PCRE that specifies where to start searching for a pattern within a packet. | By default, offset is applied on each packet. To match a pattern over a stream, use the flow:stream keyword.**Example**:alert tcp any any -> any 21 (content:”SMB”; flow:stream; offset:4; depth:5;)In this example, the rule searches for patterns that occur between 4 and 10 bytes in the entire stream irrespective of the number of packets scanned. If the first packet is 10 bytes long, then the search terminates in the first packet. |
| pcre | Allows rules to be written using Perl Compatible Regular Expressions (PCRE). | The `pcre` keyword requires at least one content keyword to be present in the rule.Only limited PCRE flags and constructs are supported. |
| stream_size | Allows a rule to match traffic based on the number of bytes observed, as determined by the TCP sequence numbers. | N/A |
| within | A modifier for content/PCRE that ensures that at most N bytes are between pattern matches which use the content keyword. | N/A |
[]The following sections discuss the current limitations of Snort rules supported in custom IPS signatures:
- [General Limitations](#general-limitations)
- [PCRE-Specific Limitations](#pcre-limitations)
[]The following table provides the general limitations of Snort rules in custom IPS signatures:
-
-
-
-
-
| **Category** | **Specifications** |
| ------------ | ------------------ |
| Rule header | Only the alert rule action is supported.Only TCP, UDP, and IP protocols are supported.IP addresses and port numbers do *not* support variables.Alerts for packets directed towards any destination (configured using any any combination) are limited to 5.The bidirectional (<>) operator is *not*** **supported. |
| Rule options | A rule can contain a maximum of 16 Payload Detection rule options, which can include one or more options from the following list: byte_extract, byte_jump, byte_test, content, isdataat, pcre, and stream_size. |
| Event filters | The detection_filter and event_filter options are each limited to 10. |
| Data buffer | The Zscaler service does *not*** **buffer traffic data internally. However, it does maintain state for streams and identifies pattern matches across a packet’s boundary. As data is not buffered, negative offsets for pattern modifiers (e.g., distance) are not supported. |
[]Snort rules in custom IPS signatures support limited PCRE flags and constructs.
[]Supported PCRE Flags
Custom signature rules support only limited PCRE flags, which are listed in the following table:
| **Flag** | **Description** | **Supported?** |
| -------- | --------------- | -------------- |
| G | Inverts the "greediness" of the quantifiers so that they are not greedy by default, but become greedy if followed by "?". | Always enabled |
| i | Treats upper and lower case letters in a pattern as equivalent. | Supported |
| m | By default, the "start of line" metacharacter (^) matches only at the start of the string, while the "end of line" metacharacter ($) matches only at the end of the string, or before a terminating newline. When this modifier is set, “^” and “$” constructs match immediately following or immediately before any newline in the subject string, respectively, as well as the very start and end. | Always enabled |
| R | Matches a pattern relative to the end of the last pattern matched. | Supported |
| s | Allows a dot metacharacter in a pattern to match newlines. | Always enabled |
Other PCRE flags are currently not** **supported.
[]Unsupported PCRE Constructs
Custom signature rules support limited PCRE constructs. The assertions listed in the following table are *not*** **supported:
| **PCRE Construct** | **Description** |
| ------------------ | --------------- |
| (?=...) | Positive lookahead zero length assertion |
| (?!...) | Negative lookahead zero length assertion |
| (?<=...) | Positive lookbehind zero length assertion |
| (?<!...) | Negative lookbehind zero length assertion |
| (?()|) | Conditional pattern |
| (...) | Capturing group |
Zscaler strongly recommends against using capturing groups.