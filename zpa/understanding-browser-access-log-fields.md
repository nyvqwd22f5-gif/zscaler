# Understanding Browser Access Log Fields
Source: https://help.zscaler.com/zpa/understanding-browser-access-log-fields
PDF: https://help.zscaler.com/pdf/com/en/1484086.pdf

The Log Streaming Service (LSS) can send HTTP log information related to Browser Access to any third-party log analytics tool. By default, the log type, Browser Access, includes the fields listed in the table below for each log template (i.e., CSV, JSON, TSV). While configuring your log receiver, you can edit the default log stream content to capture only specific fields, and create a Custom log template.
- [View an example Browser Access log](#BrowserAccessExample)
The following table includes descriptions and supported field format specifications for each field within the template. To learn more about the format specifications listed for each field, including examples, see [Log Field Format Specifications](/zpa/understanding-log-stream-content-format).
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
| Field | Description | Supported Field Format Specifications |
| ----- | ----------- | ------------------------------------- |
| LogTimestamp | Timestamp when the log was generated | %[OPT]s%[OPT]j%[OPT]J |
| ConnectionID | The application connection ID | %[OPT]s%[OPT]j%[OPT]J%[OPT]o |
| Exporter | The Browser Access Service instance to ZPA Public Service Edge or ZPA Private Service Edge instance | %[OPT]s%[OPT]j%[OPT]J%[OPT]o |
| TimestampRequestReceiveStart | Timestamp in microseconds when Browser Access Service received the first byte of the HTTP request from web browser | %[OPT]s%[OPT]j%[OPT]J |
| TimestampRequestReceiveHeaderFinish | Timestamp in microseconds when Browser Access Service received the last byte of the HTTP header corresponding to the request from web browser | %[OPT]s%[OPT]j%[OPT]J |
| TimestampRequestReceiveFinish | Timestamp in microseconds when Browser Access Service received the last byte of the HTTP request from web browser | %[OPT]s%[OPT]j%[OPT]J |
| TimestampRequestTransmitStart | Timestamp in microseconds when Browser Access Service sent the first byte of the HTTP request to the web server | %[OPT]s%[OPT]j%[OPT]J |
| TimestampRequestTransmitFinish | Timestamp in microseconds when Browser Access Service sent the last byte of the HTTP request to the web server | %[OPT]s%[OPT]j%[OPT]J |
| TimestampResponseReceiveStart | Timestamp in microseconds when Browser Access Service received the first byte of the HTTP response from the web server | %[OPT]s%[OPT]j%[OPT]J |
| TimestampResponseReceiveFinish | Timestamp in microseconds when Browser Access Service received the last byte of the HTTP response from the web server | %[OPT]s%[OPT]j%[OPT]J |
| TimestampResponseTransmitStart | Timestamp in microseconds when Browser Access Service sent the first byte of the HTTP response to the web browser | %[OPT]s%[OPT]j%[OPT]J |
| TimestampResponseTransmitFinish | Timestamp in microseconds when Browser Access Service sent the last byte of the HTTP response to the web browser | %[OPT]s%[OPT]j%[OPT]J |
| TotalTimeRequestReceive | Time difference between reception of the first and last byte of the HTTP request from the web browser as seen by the Browser Access Service | %[OPT]d%[OPT]x%[OPT]f%[OPT]o |
| TotalTimeRequestTransmit | Time difference between transmission of the first and last byte of the HTTP request towards the web server as seen by the Browser Access Service | %[OPT]d%[OPT]x%[OPT]f%[OPT]o |
| TotalTimeResponseReceive | Time difference between reception of the first and last byte of the HTTP response from the web server as seen by the Browser Access Service | %[OPT]d%[OPT]x%[OPT]f%[OPT]o |
| TotalTimeResponseTransmit | Time difference between transmission of the first and last byte of the HTTP response towards the web browser as seen by the Browser Access Service | %[OPT]d%[OPT]x%[OPT]f%[OPT]o |
| TotalTimeConnectionSetup | Time difference between reception of the first byte of the HTTP request from web browser and transmission of the first byte towards the web server, as seen by the Browser Access Service | %[OPT]d%[OPT]x%[OPT]f%[OPT]o |
| TotalTimeServerResponse | Time difference between transmission of the the last byte of the HTTP request towards the web server and reception of the first byte of the HTTP response from web server, as seen by the Browser Access Service | %[OPT]d%[OPT]x%[OPT]f%[OPT]o |
| Method | The HTTP request method | %[OPT]s%[OPT]j%[OPT]J%[OPT]o |
| Protocol | The HTTP protocol | %[OPT]s%[OPT]j%[OPT]J%[OPT]o |
| Host | The Web application | %[OPT]s%[OPT]j%[OPT]J%[OPT]o |
| URL | The URL requested by the user | %[OPT]s%[OPT]j%[OPT]J%[OPT]o |
| UserAgent | The user agent string as specified in the HTTP host request header | %[OPT]s%[OPT]j%[OPT]J%[OPT]o |
| XFF | The X-Forwarded-For (XFF) HTTP header | %[OPT]s%[OPT]j%[OPT]J%[OPT]o |
| NameID | The NameID received by ZPA in the SAML assertion from the IdP | %[OPT]s%[OPT]j%[OPT]J%[OPT]o |
| StatusCode | The HTTP status code | %[OPT]d%[OPT]x%[OPT]f%[OPT]o |
| RequestSize | The size of the HTTP request | %[OPT]d%[OPT]x%[OPT]f%[OPT]o |
| ResponseSize | The size of the HTTP response | %[OPT]d%[OPT]x%[OPT]f%[OPT]o |
| ApplicationPort | The application port on the web server | %[OPT]d%[OPT]x%[OPT]f%[OPT]o |
| ClientPublicIp | The public IP address of the user's device | %[OPT]s%[OPT]j%[OPT]J%[OPT]o |
| ClientPublicPort | The source port used by the user's device | %[OPT]d%[OPT]x%[OPT]f%[OPT]o |
| ClientPrivateIp | The private IP address of the user's device | %[OPT]s%[OPT]j%[OPT]J%[OPT]o |
| Customer | The name of the customer | %[OPT]s%[OPT]j%[OPT]J%[OPT]o |
| ConnectionStatus | The status of the connection | %[OPT]s%[OPT]j%[OPT]J%[OPT]o |
| ConnectionReason | The internal reason | %[OPT]s%[OPT]j%[OPT]J%[OPT]o |
| CorsToken | The token from the CORS request | %[OPT]s |
| Origin | The Browser Access domain that led to the origination of the CORS request | %[OPT]s |
[]{"LogTimestamp":"Wed Jul 3 05:12:25 2019","ConnectionID":"","Exporter":"unset","TimestampRequestReceiveStart":"2019-07-03T05:12:25.723Z","TimestampRequestReceiveHeaderFinish":"2019-07-03T05:12:25.723Z","TimestampRequestReceiveFinish":"2019-07-03T05:12:25.723Z","TimestampRequestTransmitStart":"2019-07-03T05:12:25.790Z","TimestampRequestTransmitFinish":"2019-07-03T05:12:25.790Z","TimestampResponseReceiveStart":"2019-07-03T05:12:25.791Z","TimestampResponseReceiveFinish":"2019-07-03T05:12:25.791Z","TimestampResponseTransmitStart":"2019-07-03T05:12:25.791Z","TimestampResponseTransmitFinish":"2019-07-03T05:12:25.791Z","TotalTimeRequestReceive":127,"TotalTimeRequestTransmit":21,"TotalTimeResponseReceive":73,"TotalTimeResponseTransmit":13,"TotalTimeConnectionSetup":66995,"TotalTimeServerResponse":1349,"Method":"GET","Protocol":"HTTPS","Host":"portal.beta.zdemo.net","URL":"/speeddial-18.0.99-82-gd7ba322-dirty/media/HelveticaNeueLTStd-Regular.762cbf85.woff","UserAgent":"Mozilla/5.0 (Macintosh; Intel Mac OS X 10_14_5) AppleWebKit/605.1.15 (KHTML, like Gecko) Version/12.1.1 Safari/605.1.15","XFF":"","NameID":"admin@zdemo.net","StatusCode":304,"RequestSize":615,"ResponseSize":331,"ApplicationPort":443,"ClientPublicIp":"139.216.128.195","ClientPublicPort":50042,"ClientPrivateIp":"","Customer":"ANZ Team/zdemo in beta","ConnectionStatus":"","ConnectionReason":"",https://example.com,token_created}