# About AppProtection Log Fields
Source: https://help.zscaler.com/unified/about-appprotection-log-fields
PDF: https://help.zscaler.com/pdf/com/en/1496001.pdf

The Log Streaming Service can send AppProtection log information to any third-party log analytics tool. By default, the AppProtection log type includes the fields listed in the table below for each log template (i.e., CSV, JSON, TSV). While configuring your log receiver, you can edit the default log stream content to capture only specific fields, and create a Custom log template.
- [View an example AppProtection log](#AppProtectionExample)
The following table includes descriptions and supported field format specifications for each field within the template. To learn more about the format specifications listed for each field, including examples, see [Log Field Format Specifications](/unified/understanding-log-stream-content-format).
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
| LogTimestamp | Timestamp when the log was generated | %[OPT]s%[OPT]j |
| Customer | The customer name | %[OPT]s%[OPT]j |
| ConnectionID | The application connection ID | %[OPT]s%[OPT]j |
| UserID | The user ID | %[OPT]s%[OPT]j |
| AssistantID | The App Connector ID | %[OPT]s%[OPT]j |
| ExchangeSequenceIndex | HTTP exchange sequence index within the TCP connection | %[OPT]d |
| TimestampRequestReceiveStart | Timestamp in microseconds when the received request was started | %[OPT]d |
| TimestampRequestReceiveHeaderFinish | Timestamp in microseconds when the received request header was finished | %[OPT]d |
| TimestampRequestReceiveFinish | Timestamp in microseconds when the received request was finished | %[OPT]d |
| TimestampRequestTransmitStart | Timestamp in microseconds when the transmitted request was started | %[OPT]d |
| TimestampRequestTransmitFinish | Timestamp in microseconds when the transmitted request was finished | %[OPT]d |
| TimestampResponseReceiveStart | Timestamp in microseconds when the received response was started | %[OPT]d |
| TimestampResponseReceiveFinish | Timestamp in microseconds when the received response was finished | %[OPT]d |
| TimestampResponseTransmitStart | Timestamp in microseconds when the transmitted response was started | %[OPT]d |
| TimestampResponseTransmitFinish | Timestamp in microseconds when the transmitted response was finished | %[OPT]d |
| TotalTimeRequestReceive | Total time taken in microseconds for the request to be received | %[OPT]d |
| TotalTimeRequestTransmit | Total time taken in microseconds for the request to be transmitted | %[OPT]d |
| TotalTimeResponseReceive | Total time taken in microseconds for the response to be received | %[OPT]d |
| TotalTimeResponseTransmit | Total time taken in microseconds for the response to be transmitted | %[OPT]d |
| Domain | The domain or IP address | %[OPT]s%[OPT]j |
| Method | The HTTP request method | %[OPT]s%[OPT]j |
| Protocol | The protocol (i.e., 1.0 or 1.1) | %[OPT]s%[OPT]j |
| ProtocolVersion | The protocol version | %[OPT]s%[OPT]j |
| ContentType | The content type | %[OPT]s%[OPT]j |
| ContentEncoding | The value of the content encoding within the HTTP header | %[OPT]s%[OPT]j |
| TransferEncoding | The value of the transfer encoding within the HTTP header | %[OPT]s%[OPT]j |
| Host | The host domain or IP address | %[OPT]s%[OPT]j |
| OriginDomain | The value of the origin header in the cross-origin HTTP header | %[OPT]s%[OPT]j |
| URL | The URL field within the HTTP header | %[OPT]s%[OPT]j |
| UserAgent | The user agent string as specified in the HTTP host request header | %[OPT]s%[OPT]j |
| HTTPError | The HTTP error | %[OPT]s%[OPT]j |
| ClientPublicIp | The public IP of the client | %[OPT]s%[OPT]j |
| ClientPort | The port of the client | %[OPT]d |
| UpgradeHeaderPresent | If the upgrade header is present or not | %[OPT]d |
| StatusCode | HTTP status code of the response | %[OPT]d |
| RequestHdrSize | The size of the request header | %[OPT]d |
| ResponseHdrSize | The size of the response header | %[OPT]d |
| RequestBodySize | The size of the request body | %[OPT]d |
| ResponseBodySize | The size of the response body | %[OPT]d |
| Application | The application name | %[OPT]d |
| ApplicationGroup | The application group name | %[OPT]d |
| InspectionPolicy | The AppProtection policy | %[OPT]d |
| InspectionProfile | The AppProtection profile | %[OPT]d |
| ParanoiaLevel | The OWASP Predefined Paranoia Level | %[OPT]d |
| InspectionControlsHitCount | The number of AppProtection control hits | %[OPT]d |
| InspectionRuleProcessingTime | Time in microseconds taken for processing the AppProtection rule | %[OPT]d |
| InspectionReqHeadersProcessingTime | Time in microseconds taken for processing the AppProtection request headers | %[OPT]d |
| InspectionReqBodyProcessingTime | Time in microseconds taken for processing the AppProtection request body | %[OPT]d |
| InspectionRespHeadersProcessingTime | Time in microseconds taken for processing the AppProtection response headers | %[OPT]d |
| InspectionRespBodyProcessingTime | Time in microseconds taken for processing the AppProtection response body | %[OPT]d |
| CertificateId | The certificate ID | %[OPT]d |
| DoubleEncryption | The double encryption status. The expected values for this field are:OnOff | %[OPT]d |
| SSLInspection | If the HTTPS traffic inspected was terminated | %[OPT]d |
| TotalBytesProcessed | The total bytes processed | %[OPT]d |
[]{"LogTimestamp": "Fri Sep 16 16:34:18 2022","Customer": "SafemarchTestUser", "ConnectionID": "cg698XMrXoY9OfjUSURh,EUtFPDqC5AzvQpL+DjAV", "UserID": "testuser@safemarch.com", "AssistantID": "test-key-1650457413478", "ExchangeSequenceIndex": 0, "TimestampRequestReceiveStart": 1663346058860810, "TimestampRequestReceiveHeaderFinish": 1663346058860833, "TimestampRequestReceiveFinish": 1663346058861590, "TimestampRequestTransmitStart": 0, "TimestampRequestTransmitFinish": 0, "TimestampResponseReceiveFinish": 1663346058866909, "TimestampResponseTransmitStart": 0, "TimestampResponseTransmitFinish": 1663346058866941, "TotalTimeRequestReceive": 0, "TotalTimeRequestTransmit": 0, "TotalTimeResponseReceive": 58, "TotalTimeResponseTransmit": 0, "Domain": "safemarch.com", "Method": "GET", "Protocol": "1.1", "ProtocolVersion": "", "ContentType": "", "ContentEncoding": "", "TransferEncoding": "", "Host": "safemarch.com", "Destination": "safemarch.com", "OriginDomain": "", "URL": "/", "UserAgent": "curl/7.68.0", "HTTPError": "success", "ClientPublicIp": "199.168.150.161", "ClientPort": 0, "UpgradeHeaderPresent": 0, "StatusCode": 301, "RequestHdrSize": 42, "ResponseHdrSize": 210, "RequestBodySize", 0, "ResponseBodySize": 0, "Application": 145254438888544148, "ApplicationGroup": 145254438888544129, "InspectionPolicy": 145254438888543730, "InspectionProfile": 145254438888538683, "ParanoiaLevel": 4, "InspectionControlsHitCount": 0, "InspectionRuleProcessingTime": 0, "InspectionReqHeadersProcessingTime": 736, "InspectionReqBodyProcessingTime": 973, "InspectionRespHeadersProcessingTime": 29, "InspectionRespBodyProcessingTime": 2, "CertificateId": 145254438888538207, "DoubleEncryption": 1, "SSLInspection": 1, "TotalBytesProcessed": 0}