# Managing Log Streaming Service Configurations Using API
Source: https://help.zscaler.com/zpa/managing-log-streaming-service-configurations-using-api
PDF: https://help.zscaler.com/pdf/com/en/1485036.pdf

This article provides information for managing Zscaler Private Access (ZPA) Log Streaming Service (LSS) configuration using APIs. All APIs are rate limited. To learn more, see [Understanding Rate Limiting](/zpa/understanding-rate-limiting).
Prerequisite API Calls
Before you create a new LSS configuration, you must get the required LSS configuration details.
Getting Details of All LSS Configurations
To get details of all LSS configurations for a given customer:
- Send a `GET` request to the following endpoint: `/mgmtconfig/v2/admin/customers/{customerId}/lssConfig`.
- Provide the `customerId`, the ZPA tenant ID of the customer, in the request endpoint. For example: `/mgmtconfig/v2/admin/customers/217246660302995456/lssConfig`.
- [View an example response](#ViewExample2)
[]{
"totalPages": "16",
"list": [
{
"id": "217246660303025321",
"config": {
"id": "217246660303025321",
"creationTime": "1628702175",
"modifiedBy": "72057594038008981",
"name": "Sample-log-receiver",
"description": "Log receiver for Sample desktop",
"enabled": true,
"sourceLogType": "zpn_ast_auth_log",
"lssHost": "10.66.62.101",
"lssPort": "49003",
"useTls": false,
"format": "{\"LogTimestamp\": %j{LogTimestamp:time},\"Customer\": %j{Customer},\"SessionID\": %j{SessionID},\"SessionType\": %j{SessionType},\"SessionStatus\": %j{SessionStatus},\"Version\": %j{Version},\"Platform\": %j{Platform},\"ZEN\": %j{ZEN},\"Connector\": %j{Connector},\"ConnectorGroup\": %j{ConnectorGroup},\"PrivateIP\": %j{PrivateIP},\"PublicIP\": %j{PublicIP},\"Latitude\": %f{Latitude},\"Longitude\": %f{Longitude},\"CountryCode\": %j{CountryCode},\"TimestampAuthentication\": %j{TimestampAuthentication:iso8601},\"TimestampUnAuthentication\": %j{TimestampUnAuthentication:iso8601},\"CPUUtilization\": %d{CPUUtilization},\"MemUtilization\": %d{MemUtilization},\"ServiceCount\": %d{ServiceCount},\"InterfaceDefRoute\": %j{InterfaceDefRoute},\"DefRouteGW\": %j{DefRouteGW},\"PrimaryDNSResolver\": %j{PrimaryDNSResolver},\"HostUpTime\": %j{HostUpTime},\"ConnectorUpTime\": %j{ConnectorUpTime},\"NumOfInterfaces\": %d{NumOfInterfaces},\"BytesRxInterface\": %d{BytesRxInterface},\"PacketsRxInterface\": %d{PacketsRxInterface},\"ErrorsRxInterface\": %d{ErrorsRxInterface},\"DiscardsRxInterface\": %d{DiscardsRxInterface},\"BytesTxInterface\": %d{BytesTxInterface},\"PacketsTxInterface\": %d{PacketsTxInterface},\"ErrorsTxInterface\": %d{ErrorsTxInterface},\"DiscardsTxInterface\": %d{DiscardsTxInterface},\"TotalBytesRx\": %d{TotalBytesRx},\"TotalBytesTx\": %d{TotalBytesTx}}\\n",
"auditMessage": "{\"logType\":\"Connector Status\",\"tcpPort\":\"49003\",\"appConnectorGroups\":[{\"name\":\"sample_connector_group\",\"id\":\"217246660303024864\"}],\"domainOrIpAddress\":\"10.66.62.101\",\"logStreamContent\":\"{\\\"LogTimestamp\\\": %j{LogTimestamp:time},\\\"Customer\\\": %j{Customer},\\\"SessionID\\\": %j{SessionID},\\\"SessionType\\\": %j{SessionType},\\\"SessionStatus\\\": %j{SessionStatus},\\\"Version\\\": %j{Version},\\\"Platform\\\": %j{Platform},\\\"ZEN\\\": %j{ZEN},\\\"Connector\\\": %j{Connector},\\\"ConnectorGroup\\\": %j{ConnectorGroup},\\\"PrivateIP\\\": %j{PrivateIP},\\\"PublicIP\\\": %j{PublicIP},\\\"Latitude\\\": %f{Latitude},\\\"Longitude\\\": %f{Longitude},\\\"CountryCode\\\": %j{CountryCode},\\\"TimestampAuthentication\\\": %j{TimestampAuthentication:iso8601},\\\"TimestampUnAuthentication\\\": %j{TimestampUnAuthentication:iso8601},\\\"CPUUtilization\\\": %d{CPUUtilization},\\\"MemUtilization\\\": %d{MemUtilization},\\\"ServiceCount\\\": %d{ServiceCount},\\\"InterfaceDefRoute\\\": %j{InterfaceDefRoute},\\\"DefRouteGW\\\": %j{DefRouteGW},\\\"PrimaryDNSResolver\\\": %j{PrimaryDNSResolver},\\\"HostUpTime\\\": %j{HostUpTime},\\\"ConnectorUpTime\\\": %j{ConnectorUpTime},\\\"NumOfInterfaces\\\": %d{NumOfInterfaces},\\\"BytesRxInterface\\\": %d{BytesRxInterface},\\\"PacketsRxInterface\\\": %d{PacketsRxInterface},\\\"ErrorsRxInterface\\\": %d{ErrorsRxInterface},\\\"DiscardsRxInterface\\\": %d{DiscardsRxInterface},\\\"BytesTxInterface\\\": %d{BytesTxInterface},\\\"PacketsTxInterface\\\": %d{PacketsTxInterface},\\\"ErrorsTxInterface\\\": %d{ErrorsTxInterface},\\\"DiscardsTxInterface\\\": %d{DiscardsTxInterface},\\\"TotalBytesRx\\\": %d{TotalBytesRx},\\\"TotalBytesTx\\\": %d{TotalBytesTx}}\\\\n\",\"name\":\"aanjali-log-receiver\",\"description\":\"Log receiver for Arun desktop\",\"sessionStatuses\":[],\"enabled\":true,\"useTls\":false,\"policy\":{\"policyType\":\"Log Receiver Policy\",\"name\":\"LSS selection rule for sample-log-receiver\"}}"
},
"connectorGroups": [
{
"id": "217246660303024864",
"modifiedTime": "1631303407",
"creationTime": "1617747326",
"modifiedBy": "72057594037978891",
"name": "Sample_connector_group",
"enabled": true,
"description": "Sample Connector Group",
"versionProfileId": "0",
"overrideVersionProfile": true,
"versionProfileName": "Default",
"versionProfileVisibilityScope": "ALL",
"connectors": [
{
"id": "217246660303024865",
"modifiedTime": "1617747782",
"creationTime": "1617747781",
"modifiedBy": "-2",
"name": "sample_provising_key-1",
"fingerprint": "ypAytG0R89+86b/HJEP3C86SJNiEjKLMXZGi7UzC070=",
"issuedCertId": "10718",
"enabled": true,
"nonceId": "6211",
"connectorVersion": {
"id": "217246660303024865",
"modifiedTime": "1617751582",
"creationTime": "1617748526",
"modifiedBy": "72057594037928167",
"currentVersion": "21.67.2-5-gc17a10071-dirty",
"systemStartTime": "1617750694",
"applicationStartTime": "1617750694",
"lastBrokerConnectTime": "1617750694139955",
"lastBrokerDisconnectTime": "1617751234138000",
"brokerId": "72057594038008982",
"connectorGroupId": "217246660303024864",
"platform": "osx20",
"ctrlChannelStatus": "ZPN_STATUS_DISCONNECTED",
"latitude": "53.7266683",
"longitude": "-127.647621",
"privateIp": "192.168.96.1",
"publicIp": "192.168.96.1",
"loneWarrior": false,
"mtunnelId": "fAb5sxXJ2f0oua9P1Km3",
"upgradeAttempt": "0"
},
"upgradeAttempt": "0"
},
{
"id": "217246660303024871",
"modifiedTime": "1617841545",
"creationTime": "1617841545",
"modifiedBy": "-2",
"name": "sample_provising_key-2",
"fingerprint": "TQ0iesqrg2CwSD/CyyP/Tdb4XpEid0o/c8v9yTiJZVE=",
"issuedCertId": "10723",
"enabled": true,
"nonceId": "6211",
"upgradeAttempt": "0"
},
{
"id": "217246660303025071",
"modifiedTime": "1622488661",
"creationTime": "1622488661",
"modifiedBy": "-2",
"name": "sample_provising_key-3",
"fingerprint": "bUULiQ4mu6FgMbtjqv4OdJdP02RABbHBdwUsLnUX5IY=",
"issuedCertId": "10765",
"enabled": true,
"nonceId": "6211",
"upgradeAttempt": "0"
},
{
"id": "217246660303025075",
"modifiedTime": "1622502016",
"creationTime": "1622502016",
"modifiedBy": "-2",
"name": "sample_provising_key-4",
"fingerprint": "TkL50KRJxbkaCEOLtkS/Exv9qeUoHcuMtTHfr/gS8FQ=",
"issuedCertId": "10766",
"enabled": true,
"nonceId": "6211",
"connectorVersion": {
"id": "217246660303025075",
"modifiedTime": "1628209140",
"creationTime": "1622586222",
"modifiedBy": "72057594037928167",
"currentVersion": "21.172.1-703-g4f9451e18",
"systemStartTime": "1628209103",
"applicationStartTime": "1628206943",
"lastBrokerConnectTime": "1628206943988515",
"lastBrokerDisconnectTime": "1628209139503006",
"brokerId": "72057594038008982",
"connectorGroupId": "217246660303024864",
"platform": "osx20",
"ctrlChannelStatus": "ZPN_STATUS_DISCONNECTED",
"latitude": "53.7266683",
"longitude": "-127.647621",
"privateIp": "192.168.96.1",
"publicIp": "192.168.96.1",
"loneWarrior": true,
"mtunnelId": "TAuFZjNWCttkr7QyOfuk",
"previousVersion": "21.172.1-703-g9cedf7b87-dirty",
"lastUpgradedTime": "1628190895",
"upgradeAttempt": "0"
},
"upgradeAttempt": "0"
},
{
"id": "217246660303025200",
"modifiedTime": "1626298081",
"creationTime": "1626298081",
"modifiedBy": "-2",
"name": "sample_provising_key-5",
"fingerprint": "4G3ZCxvitnhAaIJ8l5LE/YAPWNr21ii3KuFALz6boU0=",
"issuedCertId": "10806",
"enabled": true,
"nonceId": "6211",
"connectorVersion": {
"id": "217246660303025200",
"modifiedTime": "1626397193",
"creationTime": "1626396809",
"modifiedBy": "72057594037928167",
"expectedVersion": "21.40.0",
"currentVersion": "21.146.1-549-g8df016a-dirty",
"systemStartTime": "1626387757",
"applicationStartTime": "1626396594",
"lastBrokerConnectTime": "1626396594139006",
"lastBrokerDisconnectTime": "1626397192900656",
"brokerId": "72057594038009216",
"restartTimeInSec": "1626397614",
"connectorGroupId": "217246660303024864",
"platform": "el7",
"upgradeStatus": "IN_PROGRESS",
"ctrlChannelStatus": "ZPN_STATUS_DISCONNECTED",
"latitude": "53.7266683",
"longitude": "-127.647621",
"privateIp": "10.80.1.18",
"publicIp": "10.80.1.18",
"loneWarrior": true,
"mtunnelId": "eAAbfYNDhejuw2BQM4KS",
"upgradeAttempt": "1"
},
"upgradeAttempt": "0"
},
{
"id": "217246660303025465",
"modifiedTime": "1631824019",
"creationTime": "1631824019",
"modifiedBy": "-2",
"name": "sample_provising_key-6",
"fingerprint": "vM16x2nqj14fvEbwcpDlA8Eb3gNnM9AbsQDmn6Hz/v4=",
"issuedCertId": "10904",
"enabled": true,
"nonceId": "6211",
"upgradeAttempt": "0"
}
],
"upgradeTimeInSecs": "25200",
"upgradeDay": "MONDAY",
"location": "British Columbia, Canada",
"latitude": "53.7266683",
"longitude": "-127.6476206",
"dnsQueryType": "IPV4_IPV6",
"cityCountry": "Terrace, CA",
"countryCode": "CA",
"lssConnectorGroup": false
}
],
"policyRule": {
"id": "217246660303025327",
"modifiedTime": "1629109632",
"creationTime": "1628702176",
"modifiedBy": "72057594037987390",
"name": "LSS selection rule for sample-log-receiver",
"ruleOrder": "13",
"priority": "4",
"policyType": "3",
"operator": "AND",
"actionId": "217246660303025321",
"action": "LOG",
"policySetId": "217246660303020729",
"reauthDefaultRule": false,
"bypassDefaultRule": false,
"isolationDefaultRule": false,
"defaultRule": false,
"lssDefaultRule": false
}
}
]
}
A successful response returns code 200. To learn more, see [API Response Codes and Error Messages](/zpa/api-response-codes-and-error-messages).
This API supports pagination. To get a paginated response:
- Send a `GET` request to the following endpoint: `/mgmtconfig/v2/admin/customers/{customerId}/lssConfig?page=1&pagesize=20`.
- Provide the following in the request endpoint:
- `customerId`: The ZPA tenant ID of the customer.
- Valid values for page and page size parameters.
For example: `/mgmtconfig/v2/admin/customers/217246660302995456/lssConfig?page=1&pagesize=2.`
- [View an example response](#paginatedResponse)
[]{
"totalPages": "9",
"list": [
{
"id": "217246660303025321",
"config": {
"id": "217246660303025321",
"modifiedTime": "1645764372",
"creationTime": "1628702175",
"modifiedBy": "72057594038008981",
"name": "Test-log-receiver",
"description": "Log receiver for Test desktop",
"enabled": true,
"sourceLogType": "zpn_trans_log",
"useTls": false,
"format": "{\"LogTimestamp\": %j{LogTimestamp:time},\"Customer\": %j{Customer},\"SessionID\": %j{SessionID},\"ConnectionID\": %j{ConnectionID},\"InternalReason\": %j{InternalReason},\"ConnectionStatus\": %j{ConnectionStatus},\"IPProtocol\": %d{IPProtocol},\"DoubleEncryption\": %d{DoubleEncryption},\"Username\": %j{Username},\"ServicePort\": %d{ServicePort},\"ClientPublicIP\": %j{ClientPublicIP},\"ClientPrivateIP\": %j{ClientPrivateIP},\"ClientLatitude\": %f{ClientLatitude},\"ClientLongitude\": %f{ClientLongitude},\"ClientCountryCode\": %j{ClientCountryCode},\"ClientZEN\": %j{ClientZEN},\"Policy\": %j{Policy},\"Connector\": %j{Connector},\"ConnectorZEN\": %j{ConnectorZEN},\"ConnectorIP\": %j{ConnectorIP},\"ConnectorPort\": %d{ConnectorPort},\"Host\": %j{Host},\"Hostname\": %j{Hostname},\"Platform\": %j{Platform},\"Application\": %j{Application},\"AppGroup\": %j{AppGroup},\"Server\": %j{Server},\"ServerIP\": %j{ServerIP},\"ServerPort\": %d{ServerPort},\"PolicyProcessingTime\": %d{PolicyProcessingTime},\"ServerSetupTime\": %d{ServerSetupTime},\"TimestampConnectionStart\": %j{TimestampConnectionStart:iso8601},\"TimestampConnectionEnd\": %j{TimestampConnectionEnd:iso8601},\"TimestampCATx\": %j{TimestampCATx:iso8601},\"TimestampCARx\": %j{TimestampCARx:iso8601},\"TimestampAppLearnStart\": %j{TimestampAppLearnStart:iso8601},\"TimestampZENFirstRxClient\": %j{TimestampZENFirstRxClient:iso8601},\"TimestampZENFirstTxClient\": %j{TimestampZENFirstTxClient:iso8601},\"TimestampZENLastRxClient\": %j{TimestampZENLastRxClient:iso8601},\"TimestampZENLastTxClient\": %j{TimestampZENLastTxClient:iso8601},\"TimestampConnectorZENSetupComplete\": %j{TimestampConnectorZENSetupComplete:iso8601},\"TimestampZENFirstRxConnector\": %j{TimestampZENFirstRxConnector:iso8601},\"TimestampZENFirstTxConnector\": %j{TimestampZENFirstTxConnector:iso8601},\"TimestampZENLastRxConnector\": %j{TimestampZENLastRxConnector:iso8601},\"TimestampZENLastTxConnector\": %j{TimestampZENLastTxConnector:iso8601},\"ZENTotalBytesRxClient\": %d{ZENTotalBytesRxClient},\"ZENBytesRxClient\": %d{ZENBytesRxClient},\"ZENTotalBytesTxClient\": %d{ZENTotalBytesTxClient},\"ZENBytesTxClient\": %d{ZENBytesTxClient},\"ZENTotalBytesRxConnector\": %d{ZENTotalBytesRxConnector},\"ZENBytesRxConnector\": %d{ZENBytesRxConnector},\"ZENTotalBytesTxConnector\": %d{ZENTotalBytesTxConnector},\"ZENBytesTxConnector\": %d{ZENBytesTxConnector},\"Idp\": %j{Idp},\"ClientToClient\": %j{c2c}}\\n",
"auditMessage": "{\"logType\":\"User Activity\",\"tcpPort\":\"514\",\"appConnectorGroups\":[{\"name\":\"aanjali_connector_group\",\"id\":\"217246660303024864\"}],\"domainOrIpAddress\":\"10.80.1.21\",\"logStreamContent\":\"{\\\"LogTimestamp\\\": %j{LogTimestamp:time},\\\"Customer\\\": %j{Customer},\\\"SessionID\\\": %j{SessionID},\\\"ConnectionID\\\": %j{ConnectionID},\\\"InternalReason\\\": %j{InternalReason},\\\"ConnectionStatus\\\": %j{ConnectionStatus},\\\"IPProtocol\\\": %d{IPProtocol},\\\"DoubleEncryption\\\": %d{DoubleEncryption},\\\"Username\\\": %j{Username},\\\"ServicePort\\\": %d{ServicePort},\\\"ClientPublicIP\\\": %j{ClientPublicIP},\\\"ClientPrivateIP\\\": %j{ClientPrivateIP},\\\"ClientLatitude\\\": %f{ClientLatitude},\\\"ClientLongitude\\\": %f{ClientLongitude},\\\"ClientCountryCode\\\": %j{ClientCountryCode},\\\"ClientZEN\\\": %j{ClientZEN},\\\"Policy\\\": %j{Policy},\\\"Connector\\\": %j{Connector},\\\"ConnectorZEN\\\": %j{ConnectorZEN},\\\"ConnectorIP\\\": %j{ConnectorIP},\\\"ConnectorPort\\\": %d{ConnectorPort},\\\"Host\\\": %j{Host},\"Hostname\": %j{Hostname},\"Platform\": %j{Platform},\\\"Application\\\": %j{Application},\\\"AppGroup\\\": %j{AppGroup},\\\"Server\\\": %j{Server},\\\"ServerIP\\\": %j{ServerIP},\\\"ServerPort\\\": %d{ServerPort},\\\"PolicyProcessingTime\\\": %d{PolicyProcessingTime},\\\"ServerSetupTime\\\": %d{ServerSetupTime},\\\"TimestampConnectionStart\\\": %j{TimestampConnectionStart:iso8601},\\\"TimestampConnectionEnd\\\": %j{TimestampConnectionEnd:iso8601},\\\"TimestampCATx\\\": %j{TimestampCATx:iso8601},\\\"TimestampCARx\\\": %j{TimestampCARx:iso8601},\\\"TimestampAppLearnStart\\\": %j{TimestampAppLearnStart:iso8601},\\\"TimestampZENFirstRxClient\\\": %j{TimestampZENFirstRxClient:iso8601},\\\"TimestampZENFirstTxClient\\\": %j{TimestampZENFirstTxClient:iso8601},\\\"TimestampZENLastRxClient\\\": %j{TimestampZENLastRxClient:iso8601},\\\"TimestampZENLastTxClient\\\": %j{TimestampZENLastTxClient:iso8601},\\\"TimestampConnectorZENSetupComplete\\\": %j{TimestampConnectorZENSetupComplete:iso8601},\\\"TimestampZENFirstRxConnector\\\": %j{TimestampZENFirstRxConnector:iso8601},\\\"TimestampZENFirstTxConnector\\\": %j{TimestampZENFirstTxConnector:iso8601},\\\"TimestampZENLastRxConnector\\\": %j{TimestampZENLastRxConnector:iso8601},\\\"TimestampZENLastTxConnector\\\": %j{TimestampZENLastTxConnector:iso8601},\\\"ZENTotalBytesRxClient\\\": %d{ZENTotalBytesRxClient},\\\"ZENBytesRxClient\\\": %d{ZENBytesRxClient},\\\"ZENTotalBytesTxClient\\\": %d{ZENTotalBytesTxClient},\\\"ZENBytesTxClient\\\": %d{ZENBytesTxClient},\\\"ZENTotalBytesRxConnector\\\": %d{ZENTotalBytesRxConnector},\\\"ZENBytesRxConnector\\\": %d{ZENBytesRxConnector},\\\"ZENTotalBytesTxConnector\\\": %d{ZENTotalBytesTxConnector},\\\"ZENBytesTxConnector\\\": %d{ZENBytesTxConnector},\\\"Idp\\\": %j{Idp},\\\"ClientToClient\\\": %j{c2c}}\\\\n\",\"name\":\"aanjali-log-receiver\",\"description\":\"Log receiver for Arun desktop\",\"sessionStatuses\":[],\"enabled\":true,\"useTls\":false,\"policy\":{\"policyType\":\"Log Receiver Policy\",\"name\":\"SIEM selection rule for aanjali-log-receiver\",\"action\":\"LOG\",\"ruleOrder\":\"13\"}}",
"lssHost": "10.80.1.21",
"lssPort": "514"
},
"connectorGroups": [
{
"id": "217246660303024864",
"modifiedTime": "1648582135",
"creationTime": "1617747326",
"modifiedBy": "72057594038056324",
"name": "Test_connector_group",
"enabled": true,
"description": "Test Connector Group",
"versionProfileId": "2",
"overrideVersionProfile": true,
"versionProfileName": "New Release",
"versionProfileVisibilityScope": "ALL",
"upgradeTimeInSecs": "25200",
"upgradeDay": "TUESDAY",
"location": "British Columbia, Canada",
"latitude": "53.7266683",
"longitude": "-127.6476206",
"dnsQueryType": "IPV4_IPV6",
"cityCountry": "Telkwa, CA",
"countryCode": "CA",
"connectors": [
{
"id": "217246660303024865",
"modifiedTime": "1617747782",
"creationTime": "1617747781",
"modifiedBy": "-2",
"name": "Test_provising_key-1",
"fingerprint": "ypAytG0R89+86b/HJEP3C86SJNiEjKLMXZGi7UzC070=",
"issuedCertId": "10718",
"enabled": true,
"assistantVersion": {
"id": "217246660303024865",
"modifiedTime": "1617751582",
"creationTime": "1617748526",
"modifiedBy": "72057594037928167",
"currentVersion": "21.67.2-5-gc17a10071-dirty",
"systemStartTime": "1617750694",
"applicationStartTime": "1617750694",
"lastBrokerConnectTime": "1617750694139955",
"lastBrokerDisconnectTime": "1617751234138000",
"brokerId": "72057594038008982",
"platform": "osx20",
"ctrlChannelStatus": "ZPN_STATUS_DISCONNECTED",
"latitude": "53.7266683",
"longitude": "-127.647621",
"privateIp": "192.168.96.1",
"publicIp": "192.168.96.1",
"loneWarrior": false,
"mtunnelId": "fAb5sxXJ2f0oua9P1Km3",
"upgradeAttempt": "0",
"appConnectorGroupId": "217246660303024864"
},
"upgradeAttempt": "0",
"provisioningKeyId": "6211"
},
{
"id": "217246660303024871",
"modifiedTime": "1617841545",
"creationTime": "1617841545",
"modifiedBy": "-2",
"name": "Test_provising_key-2",
"fingerprint": "TQ0iesqrg2CwSD/CyyP/Tdb4XpEid0o/c8v9yTiJZVE=",
"issuedCertId": "10723",
"enabled": true,
"upgradeAttempt": "0",
"provisioningKeyId": "6211"
},
{
"id": "217246660303025071",
"modifiedTime": "1622488661",
"creationTime": "1622488661",
"modifiedBy": "-2",
"name": "aanjali_provising_key-3",
"fingerprint": "bUULiQ4mu6FgMbtjqv4OdJdP02RABbHBdwUsLnUX5IY=",
"issuedCertId": "10765",
"enabled": true,
"upgradeAttempt": "0",
"provisioningKeyId": "6211"
},
{
"id": "217246660303025075",
"modifiedTime": "1622502016",
"creationTime": "1622502016",
"modifiedBy": "-2",
"name": "Test_provising_key-4",
"fingerprint": "TkL50KRJxbkaCEOLtkS/Exv9qeUoHcuMtTHfr/gS8FQ=",
"issuedCertId": "10766",
"enabled": true,
"assistantVersion": {
"id": "217246660303025075",
"modifiedTime": "1649111254",
"creationTime": "1622586222",
"modifiedBy": "72057594037928167",
"currentVersion": "22.81.3-475-g7a762ab92-dirty",
"systemStartTime": "1649111208",
"applicationStartTime": "1649110549",
"lastBrokerConnectTime": "1649110549447930",
"lastBrokerDisconnectTime": "1649111254190488",
"brokerId": "72057594038008982",
"platform": "osx20",
"ctrlChannelStatus": "ZPN_STATUS_DISCONNECTED",
"latitude": "53.7266683",
"longitude": "-127.647621",
"privateIp": "192.168.96.1",
"publicIp": "192.168.96.1",
"loneWarrior": false,
"mtunnelId": "UUaxEj75U2Zqx26dx+yf",
"previousVersion": "22.81.2-371-g32bcc188c-dirty",
"lastUpgradedTime": "1649110549",
"upgradeAttempt": "0",
"sargeVersion": "unknown",
"appConnectorGroupId": "217246660303024864"
},
"upgradeAttempt": "0",
"provisioningKeyId": "6211"
},
{
"id": "217246660303025200",
"modifiedTime": "1626298081",
"creationTime": "1626298081",
"modifiedBy": "-2",
"name": "Test_provising_key-5",
"fingerprint": "4G3ZCxvitnhAaIJ8l5LE/YAPWNr21ii3KuFALz6boU0=",
"issuedCertId": "10806",
"enabled": true,
"assistantVersion": {
"id": "217246660303025200",
"modifiedTime": "1644895989",
"creationTime": "1626396809",
"modifiedBy": "72057594037928167",
"expectedVersion": "21.40.0",
"currentVersion": "22.31.1-330-ga6f852a",
"systemStartTime": "1643339140",
"applicationStartTime": "1644891085",
"lastBrokerConnectTime": "1644891085862327",
"lastBrokerDisconnectTime": "1644895645857000",
"brokerId": "72057594038009216",
"restartTimeInSec": "1626397614",
"platform": "el7",
"upgradeStatus": "FAILED",
"ctrlChannelStatus": "ZPN_STATUS_DISCONNECTED",
"latitude": "53.7266683",
"longitude": "-127.647621",
"privateIp": "10.80.1.18",
"publicIp": "10.80.1.18",
"loneWarrior": false,
"mtunnelId": "2dQGmAm2lnU8Vr4CDuNE",
"previousVersion": "22.31.1-299-g5d10aad",
"lastUpgradedTime": "1644891085",
"upgradeAttempt": "1",
"appConnectorGroupId": "217246660303024864"
},
"upgradeAttempt": "0",
"provisioningKeyId": "6211"
},
{
"id": "217246660303025465",
"modifiedTime": "1631824019",
"creationTime": "1631824019",
"modifiedBy": "-2",
"name": "Test_provising_key-6",
"fingerprint": "vM16x2nqj14fvEbwcpDlA8Eb3gNnM9AbsQDmn6Hz/v4=",
"issuedCertId": "10904",
"enabled": true,
"upgradeAttempt": "0",
"provisioningKeyId": "6211"
},
{
"id": "217246660303026024",
"modifiedTime": "1642038720",
"creationTime": "1642038720",
"modifiedBy": "-2",
"name": "Test_provising_key-1642038720187",
"fingerprint": "0Go2S8Mn21WNU4/HoqGe+9hIWfGBmQaBCo5rswz1a5I=",
"issuedCertId": "11366",
"enabled": true,
"assistantVersion": {
"id": "217246660303026024",
"modifiedTime": "1644973491",
"creationTime": "1642038783",
"modifiedBy": "72057594037928167",
"expectedVersion": "22.48.2",
"currentVersion": "22.48.2-343-gd207bce",
"systemStartTime": "1644615566",
"applicationStartTime": "1644973049",
"lastBrokerConnectTime": "1644973049533440",
"lastBrokerDisconnectTime": "1644973491131990",
"brokerId": "72057594038009216",
"restartTimeInSec": "1645426800",
"platform": "el7",
"upgradeStatus": "IN_PROGRESS",
"ctrlChannelStatus": "ZPN_STATUS_DISCONNECTED",
"latitude": "53.7266683",
"longitude": "-127.647621",
"privateIp": "10.80.1.13",
"publicIp": "10.80.1.13",
"loneWarrior": true,
"mtunnelId": "UwE3y7rihtuhmDrbImWx",
"previousVersion": "22.31.1-298-g704f14d-dirty",
"lastUpgradedTime": "1644973049",
"upgradeAttempt": "1",
"sargeVersion": "unknown",
"appConnectorGroupId": "217246660303024864"
},
"upgradeAttempt": "0",
"provisioningKeyId": "6211"
},
{
"id": "217246660303026200",
"modifiedTime": "1647378868",
"creationTime": "1647378868",
"modifiedBy": "-2",
"name": "Test_provising_key-1647378868128",
"fingerprint": "2hsPJ82ah0WaJd9ga3+LzUKfkdlGWPUbOR4u49daD7I=",
"issuedCertId": "11454",
"enabled": true,
"assistantVersion": {
"id": "217246660303026200",
"modifiedTime": "1647386545",
"creationTime": "1647379967",
"modifiedBy": "72057594037928167",
"currentVersion": "22.81.1-280-ged0348f",
"systemStartTime": "1646188468",
"applicationStartTime": "1647383824",
"lastBrokerConnectTime": "1647383824885416",
"lastBrokerDisconnectTime": "1647386224883000",
"brokerId": "72057594038009216",
"platform": "el7",
"ctrlChannelStatus": "ZPN_STATUS_DISCONNECTED",
"latitude": "53.7266683",
"longitude": "-127.647621",
"privateIp": "10.80.1.18",
"publicIp": "10.80.1.18",
"loneWarrior": false,
"mtunnelId": "sIOxkb/nA71MgITUW0Kc",
"previousVersion": "22.81.1-272-g0670763",
"lastUpgradedTime": "1647382948",
"upgradeAttempt": "0",
"appConnectorGroupId": "217246660303024864"
},
"upgradeAttempt": "0",
"provisioningKeyId": "6211"
},
{
"id": "217246660303026201",
"modifiedTime": "1647379931",
"creationTime": "1647379930",
"modifiedBy": "-2",
"name": "Test_provising_key-1647379930647",
"fingerprint": "u9b4oAVtQckEyaIo47wgDjRuWoZ5m33GhsVFs+dx6VY=",
"issuedCertId": "11455",
"enabled": true,
"assistantVersion": {
"id": "217246660303026201",
"modifiedTime": "1647386665",
"creationTime": "1647379966",
"modifiedBy": "72057594037928167",
"currentVersion": "22.81.1-277-gfa90a4f",
"systemStartTime": "1644615619",
"applicationStartTime": "1647383916",
"lastBrokerConnectTime": "1647383916158382",
"lastBrokerDisconnectTime": "1647386316157000",
"brokerId": "72057594038009216",
"platform": "el7",
"ctrlChannelStatus": "ZPN_STATUS_DISCONNECTED",
"latitude": "53.7266683",
"longitude": "-127.647621",
"privateIp": "10.80.1.19",
"publicIp": "10.80.1.19",
"loneWarrior": false,
"mtunnelId": "EZN/k3wWzFguyrXbWNpW",
"upgradeAttempt": "0",
"appConnectorGroupId": "217246660303024864"
},
"upgradeAttempt": "0",
"provisioningKeyId": "6211"
},
{
"id": "217246660303026212",
"modifiedTime": "1647641202",
"creationTime": "1647641202",
"modifiedBy": "3",
"name": "Test_provising_key-1647641202311",
"fingerprint": "bCOax8cjDpModnA2nDKPGsz+ivFPeX627cZ2c/DCBAs=",
"issuedCertId": "11461",
"enabled": true,
"assistantVersion": {
"id": "217246660303026212",
"modifiedTime": "1649202229",
"creationTime": "1647641368",
"modifiedBy": "72057594037928167",
"expectedVersion": "22.73.4",
"currentVersion": "22.81.3-476-g9ac56e3-dirty",
"systemStartTime": "1644615566",
"applicationStartTime": "1649201603",
"lastBrokerConnectTime": "1649201603314251",
"lastBrokerDisconnectTime": "1649201903314000",
"brokerId": "72057594038009216",
"restartTimeInSec": "1649200054",
"platform": "el7",
"upgradeStatus": "FAILED",
"ctrlChannelStatus": "ZPN_STATUS_DISCONNECTED",
"latitude": "53.7266683",
"longitude": "-127.647621",
"privateIp": "10.80.1.13",
"publicIp": "10.80.1.13",
"loneWarrior": false,
"mtunnelId": "SIje4vBRBMoiU0aIwf6x",
"previousVersion": "22.81.1-350-g5719ab8",
"lastUpgradedTime": "1649201354",
"upgradeAttempt": "3",
"appConnectorGroupId": "217246660303024864"
},
"upgradeAttempt": "0",
"provisioningKeyId": "6211"
},
{
"id": "217246660303026219",
"modifiedTime": "1647895033",
"creationTime": "1647894135",
"modifiedBy": "72057594037986439",
"name": "1_aws_Test_provising_key-1647894135953",
"fingerprint": "APmk0n7apZVWbhK0QfB49YXHI4skEd7DFmnyvdM5vyQ=",
"issuedCertId": "11463",
"enabled": true,
"assistantVersion": {
"id": "217246660303026219",
"modifiedTime": "1649261054",
"creationTime": "1647894141",
"modifiedBy": "72057594037928167",
"expectedVersion": "22.73.4",
"currentVersion": "22.73.4",
"systemStartTime": "1647893233",
"applicationStartTime": "1649261054",
"lastBrokerConnectTime": "1649261054476416",
"lastBrokerDisconnectTime": "1649260992179021",
"brokerId": "72057594037937052",
"restartTimeInSec": "0",
"platform": "el7",
"upgradeStatus": "COMPLETE",
"ctrlChannelStatus": "ZPN_STATUS_AUTHENTICATED",
"latitude": "53.7266683",
"longitude": "-127.647621",
"privateIp": "10.18.7.119",
"publicIp": "52.10.226.98",
"loneWarrior": true,
"mtunnelId": "QidvI4uiIFEG7FYw31vp",
"previousVersion": "21.352.1",
"lastUpgradedTime": "1648582433",
"upgradeAttempt": "0",
"sargeVersion": "22.73.4",
"appConnectorGroupId": "217246660303024864"
},
"upgradeAttempt": "0",
"provisioningKeyId": "6211"
}
],
"lssAppConnectorGroup": false
}
],
"policyRule": {
"id": "217246660303025327",
"modifiedTime": "1645764372",
"modifiedBy": "72057594038008981",
"name": "SIEM selection rule for Test-log-receiver",
"ruleOrder": "13",
"priority": "5",
"policyType": "3",
"operator": "AND",
"actionId": "217246660303025321",
"action": "LOG",
"policySetId": "217246660303020729",
"defaultRule": false
}
},
{
"id": "217246660303023855",
"config": {
"id": "217246660303023855",
"modifiedTime": "1599782550",
"creationTime": "1592527281",
"modifiedBy": "217246660303022625",
"name": "Test Receiver For Http Slogging",
"description": "For testing HTTP slogging",
"enabled": true,
"sourceLogType": "zpn_trans_log",
"useTls": false,
"format": "%s{LogTimestamp:time} User Activity zpa-lss: ,%s{Customer},%s{SessionID},%s{ConnectionID},%s{InternalReason},%s{ConnectionStatus},%d{IPProtocol},%d{DoubleEncryption},%s{Username},%d{ServicePort},%s{ClientPublicIP},%s{ClientPrivateIP},%f{ClientLatitude},%f{ClientLongitude},%s{ClientCountryCode},%s{ClientZEN},%s{Policy},%s{Connector},%s{ConnectorZEN},%s{ConnectorIP},%d{ConnectorPort},%s{Host},%s{Application},%s{AppGroup},%s{Server},%s{ServerIP},%d{ServerPort},%d{PolicyProcessingTime},%d{ServerSetupTime},%s{TimestampConnectionStart:iso8601},%s{TimestampConnectionEnd:iso8601},%s{TimestampCATx:iso8601},%s{TimestampCARx:iso8601},%s{TimestampAppLearnStart:iso8601},%s{TimestampZENFirstRxClient:iso8601},%s{TimestampZENFirstTxClient:iso8601},%s{TimestampZENLastRxClient:iso8601},%s{TimestampZENLastTxClient:iso8601},%s{TimestampConnectorZENSetupComplete:iso8601},%s{TimestampZENFirstRxConnector:iso8601},%s{TimestampZENFirstTxConnector:iso8601},%s{TimestampZENLastRxConnector:iso8601},%s{TimestampZENLastTxConnector:iso8601},%d{ZENTotalBytesRxClient},%d{ZENBytesRxClient},%d{ZENTotalBytesTxClient},%d{ZENBytesTxClient},%d{ZENTotalBytesRxConnector},%d{ZENBytesRxConnector},%d{ZENTotalBytesTxConnector},%d{ZENBytesTxConnector},%s{Idp}\\n",
"auditMessage": "{\"logType\":\"User Activity\",\"tcpPort\":\"9412\",\"connectorGroups\":[{\"name\":\"blewis connector group\",\"id\":\"217246660303023569\"}],\"domainOrIpAddress\":\"192.168.111.1\",\"logStreamContent\":\"%s{LogTimestamp:time} User Activity zpa-lss: ,%s{Customer},%s{SessionID},%s{ConnectionID},%s{InternalReason},%s{ConnectionStatus},%d{IPProtocol},%d{DoubleEncryption},%s{Username},%d{ServicePort},%s{ClientPublicIP},%s{ClientPrivateIP},%f{ClientLatitude},%f{ClientLongitude},%s{ClientCountryCode},%s{ClientZEN},%s{Policy},%s{Connector},%s{ConnectorZEN},%s{ConnectorIP},%d{ConnectorPort},%s{Host},%s{Application},%s{AppGroup},%s{Server},%s{ServerIP},%d{ServerPort},%d{PolicyProcessingTime},%d{ServerSetupTime},%s{TimestampConnectionStart:iso8601},%s{TimestampConnectionEnd:iso8601},%s{TimestampCATx:iso8601},%s{TimestampCARx:iso8601},%s{TimestampAppLearnStart:iso8601},%s{TimestampZENFirstRxClient:iso8601},%s{TimestampZENFirstTxClient:iso8601},%s{TimestampZENLastRxClient:iso8601},%s{TimestampZENLastTxClient:iso8601},%s{TimestampConnectorZENSetupComplete:iso8601},%s{TimestampZENFirstRxConnector:iso8601},%s{TimestampZENFirstTxConnector:iso8601},%s{TimestampZENLastRxConnector:iso8601},%s{TimestampZENLastTxConnector:iso8601},%d{ZENTotalBytesRxClient},%d{ZENBytesRxClient},%d{ZENTotalBytesTxClient},%d{ZENBytesTxClient},%d{ZENTotalBytesRxConnector},%d{ZENBytesRxConnector},%d{ZENTotalBytesTxConnector},%d{ZENBytesTxConnector},%s{Idp}\\\\n\",\"name\":\"Barrett Receiver For Http Slogging\",\"description\":\"For%20testing%20HTTP%20slogging\",\"sessionStatuses\":[],\"policy\":{\"policyType\":\"Log Receiver Policy\",\"name\":\"SIEM selection rule for Barrett Receiver For Http Slogging\",\"action\":\"LOG\",\"ruleOrder\":\"8\",\"conditions\":[]}}",
"lssHost": "192.168.111.1",
"lssPort": "9412"
},
"connectorGroups": [
{
"id": "217246660303023569",
"modifiedTime": "1631303407",
"creationTime": "1573059625",
"modifiedBy": "72057594037978891",
"name": "blewis connector group",
"enabled": true,
"description": "Test connector group for testing",
"versionProfileId": "0",
"overrideVersionProfile": true,
"versionProfileName": "default",
"versionProfileVisibilityScope": "ALL",
"upgradeTimeInSecs": "28800",
"upgradeDay": "MONDAY",
"location": "Cohasset, CA 95973, USA",
"latitude": "39.8633343",
"longitude": "-121.85626100000002",
"dnsQueryType": "IPV4_IPV6",
"cityCountry": "Chico, US",
"countryCode": "US",
"connectors": [
{
"id": "217246660303023570",
"modifiedTime": "1618335871",
"creationTime": "1573059700",
"modifiedBy": "-2",
"name": "Test provisioning key-1",
"fingerprint": "+G26LgiYKkfsTdbWStli74UMp5VNNIBnxDRZCQkFU1s=",
"issuedCertId": "10725",
"enabled": true,
"assistantVersion": {
"id": "217246660303023570",
"modifiedTime": "1618346625",
"creationTime": "1573059703",
"modifiedBy": "72057594037928167",
"currentVersion": "21.67.2-382-g37085a340",
"systemStartTime": "1618346624",
"applicationStartTime": "1618337529",
"lastBrokerConnectTime": "1618344549545285",
"lastBrokerDisconnectTime": "1618346625077444",
"brokerId": "72057594037954572",
"platform": "osx18",
"ctrlChannelStatus": "ZPN_STATUS_DISCONNECTED",
"latitude": "39.8633343",
"longitude": "-121.856261",
"privateIp": "10.34.32.125",
"publicIp": "10.34.32.125",
"loneWarrior": true,
"mtunnelId": "bnHAKBjz8ChUhU8VPb9h",
"previousVersion": "20.58.0-31-g9695bc2f8-dirty",
"lastUpgradedTime": "1618335873",
"upgradeAttempt": "0",
"appConnectorGroupId": "217246660303023569"
},
"upgradeAttempt": "0",
"provisioningKeyId": "5638"
}
],
"lssAppConnectorGroup": false
}
],
"policyRule": {
"id": "217246660303023861",
"modifiedTime": "1637033290",
"creationTime": "1592527281",
"modifiedBy": "72057594037994933",
"name": "SIEM selection rule for Test Receiver For Http Slogging",
"ruleOrder": "8",
"priority": "10",
"policyType": "3",
"operator": "AND",
"actionId": "217246660303023855",
"action": "LOG",
"policySetId": "217246660303020729",
"defaultRule": false
}
}
]
}
If not provided, the default page size is 20. The maximum page size is 500.
A successful response returns code 200. To learn more, see [API Response Codes and Error Messages](/zpa/api-response-codes-and-error-messages).
Getting Details for a Particular LSS Configuration
To get details for a particular LSS configuration:
- Send a `GET` request to the following endpoint: `/mgmtconfig/v2/admin/customers/{customerId}/lssConfig/{lssId}`.
- Provide the following in the request endpoint:
- `customerId`: The ZPA tenant ID of the customer.
- `lssId`: The unique identifier of the LSS resource.
For example: `/mgmtconfig/v2/admin/customers/144118148382064640/lssConfig/144118148382065634`.
- [View an example response](#ViewExample3)
[]{
"id":"144118148382065634",
"config":{
"id":"144118148382065634",
"modifiedTime":"1706901238",
"creationTime":"1706901238",
"modifiedBy":"144118148382065531",
"name":"ExampleTest1",
"enabled":true,
"sourceLogType":"zpn_trans_log",
"useTls":false,
"format":"%s{LogTimestamp:time} User Activity zpa-lss: ,%s{Customer},%s{SessionID},%s{ConnectionID},%s{InternalReason},%s{ConnectionStatus},%d{IPProtocol},%d{DoubleEncryption},%s{Username},%d{ServicePort},%s{ClientPublicIP},%s{ClientPrivateIP},%f{ClientLatitude},%f{ClientLongitude},%s{ClientCountryCode},%s{ClientZEN},%s{Policy},%s{Connector},%s{ConnectorZEN},%s{ConnectorIP},%d{ConnectorPort},%s{Host},%s{Application},%s{AppGroup},%s{Server},%s{ServerIP},%d{ServerPort},%d{PolicyProcessingTime},%d{ServerSetupTime},%s{TimestampConnectionStart:iso8601},%s{TimestampConnectionEnd:iso8601},%s{TimestampCATx:iso8601},%s{TimestampCARx:iso8601},%s{TimestampAppLearnStart:iso8601},%s{TimestampZENFirstRxClient:iso8601},%s{TimestampZENFirstTxClient:iso8601},%s{TimestampZENLastRxClient:iso8601},%s{TimestampZENLastTxClient:iso8601},%s{TimestampConnectorZENSetupComplete:iso8601},%s{TimestampZENFirstRxConnector:iso8601},%s{TimestampZENFirstTxConnector:iso8601},%s{TimestampZENLastRxConnector:iso8601},%s{TimestampZENLastTxConnector:iso8601},%d{ZENTotalBytesRxClient},%d{ZENBytesRxClient},%d{ZENTotalBytesTxClient},%d{ZENBytesTxClient},%d{ZENTotalBytesRxConnector},%d{ZENBytesRxConnector},%d{ZENTotalBytesTxConnector},%d{ZENBytesTxConnector},%s{Idp},%s{c2c},%s{ClientCity},%s{MicroTenantID},%s{AppMicroTenantID},%j{Platform},%j{hostname}\\n",
"auditMessage":"{\"logType\":\"User Activity\",\"tcpPort\":\"443\",\"appConnectorGroups\":[{\"name\":\"Test\",\"id\":\"144118148382064753\"}],\"domainOrIpAddress\":\"ExampleTest1.com\",\"logStreamContent\":\"%s{LogTimestamp:time} User Activity zpa-lss: ,%s{Customer},%s{SessionID},%s{ConnectionID},%s{InternalReason},%s{ConnectionStatus},%d{IPProtocol},%d{DoubleEncryption},%s{Username},%d{ServicePort},%s{ClientPublicIP},%s{ClientPrivateIP},%f{ClientLatitude},%f{ClientLongitude},%s{ClientCountryCode},%s{ClientZEN},%s{Policy},%s{Connector},%s{ConnectorZEN},%s{ConnectorIP},%d{ConnectorPort},%s{Host},%s{Application},%s{AppGroup},%s{Server},%s{ServerIP},%d{ServerPort},%d{PolicyProcessingTime},%d{ServerSetupTime},%s{TimestampConnectionStart:iso8601},%s{TimestampConnectionEnd:iso8601},%s{TimestampCATx:iso8601},%s{TimestampCARx:iso8601},%s{TimestampAppLearnStart:iso8601},%s{TimestampZENFirstRxClient:iso8601},%s{TimestampZENFirstTxClient:iso8601},%s{TimestampZENLastRxClient:iso8601},%s{TimestampZENLastTxClient:iso8601},%s{TimestampConnectorZENSetupComplete:iso8601},%s{TimestampZENFirstRxConnector:iso8601},%s{TimestampZENFirstTxConnector:iso8601},%s{TimestampZENLastRxConnector:iso8601},%s{TimestampZENLastTxConnector:iso8601},%d{ZENTotalBytesRxClient},%d{ZENBytesRxClient},%d{ZENTotalBytesTxClient},%d{ZENBytesTxClient},%d{ZENTotalBytesRxConnector},%d{ZENBytesRxConnector},%d{ZENTotalBytesTxConnector},%d{ZENBytesTxConnector},%s{Idp},%s{c2c},%s{ClientCity},%s{MicroTenantID},%s{AppMicroTenantID}\\\\n\",\"name\":\"ExampleTest1\",\"description\":\"\",\"sessionStatuses\":[],\"enabled\":true,\"useTls\":false,\"policy\":{\"privilegedCapabilities\":{\"capabilities\":[],\"id\":null,\"capabilitiesMask\":0},\"policyType\":\"Log Receiver Policy\",\"name\":\"SIEM selection rule for ExampleTest1\"}}",
"readOnly":false,
"zscalerManaged":false,
"lssHost":"test1.com",
"lssPort":"443"
},
"connectorGroups":[
{
"id":"144118148382064753",
"modifiedTime":"1646169737",
"creationTime":"1473977866",
"modifiedBy":"144118148382065457",
"name":"Example Test",
"enabled":true,
"versionProfileId":"0",
"overrideVersionProfile":false,
"versionProfileName":"Default",
"upgradePriority":"WEEK",
"versionProfileVisibilityScope":"ALL",
"upgradeTimeInSecs":"43200",
"upgradeDay":"WEDNESDAY",
"location":"chd",
"latitude":"5.0",
"longitude":"5.0",
"dnsQueryType":"IPV4_IPV6",
"praEnabled":true,
"connectorGroupType":"APP",
"wafDisabled":false,
"readOnly":false,
"zscalerManaged":false,
"microtenantName":"Default",
"lssAppConnectorGroup":false
}
],
"policyRule":{
"id":"144118148382065640",
"modifiedTime":"1707851751",
"creationTime":"1706901238",
"modifiedBy":"144118148382065457",
"name":"SIEM selection rule for Example Test",
"ruleOrder":"3",
"priority":"2",
"policyType":"3",
"operator":"AND",
"actionId":"144118148382065634",
"action":"LOG",
"disabled":"0",
"policySetId":"144118148382064866",
"defaultRule":false,
"readOnly":false,
"zscalerManaged":false
}
}
A successful response returns code 200. To learn more, see [API Response Codes and Error Messages](/zpa/api-response-codes-and-error-messages).
[]Getting Details of All LSS Status Codes
To get details of all LSS status codes, send a `GET` request to the following endpoint: `/mgmtconfig/v2/admin/lssConfig/statusCodes`.
- [View an example response](#ViewExample5)
[]{
"zpn_auth_log":{
"ZPN_STATUS_AUTH_FAILED":{
"errorType":"NA",
"name":"Authentication failed",
"adminAction":"NA",
"status":"Error"
},
"ZPN_STATUS_DISCONNECTED":{
"errorType":"NA",
"name":"Disconnected",
"adminAction":"NA",
"status":"Success"
},
"ZPN_STATUS_AUTHENTICATED":{
"errorType":"NA",
"name":"Authenticated",
"adminAction":"NA",
"status":"Success"
}
},
"zpn_ast_auth_log":{
"ZPN_STATUS_AUTH_FAILED":{
"errorType":"NA",
"name":"Authentication failed",
"adminAction":"NA",
"status":"Error"
},
"ZPN_STATUS_DISCONNECTED":{
"errorType":"NA",
"name":"Disconnected",
"adminAction":"NA",
"status":"Success"
},
"ZPN_STATUS_AUTHENTICATED":{
"errorType":"NA",
"name":"Authenticated",
"adminAction":"NA",
"status":"Success"
}
},
"zpn_trans_log":{
"BRK_MT_SETUP_FAIL_BIND_TO_AST_LOCAL_OWNER":{
"errorType":"InternalError",
"name":"SE: Error in associating connection to App Connector",
"adminAction":"NA",
"status":"Error"
},
"BRK_MT_TERMINATED_IDLE_TIMEOUT":{
"errorType":"ActionableError",
"name":"SE: Timeout policy closed idle connection",
"adminAction":"open a new connection to the application",
"status":"Info"
},
"CLT_INVALID_DOMAIN":{
"errorType":"InternalError",
"name":"CLT: Invalid domain",
"adminAction":"NA",
"status":"Error"
},
"AST_MT_SETUP_ERR_HASH_TBL_FULL":{
"errorType":"InternalError",
"name":"AC: Connection database is full",
"adminAction":"NA",
"status":"Error"
},
"AST_MT_SETUP_ERR_CONN_PEER":{
"errorType":"InternalError",
"name":"AC: Error in creating Service Edge-server connection",
"adminAction":"NA",
"status":"Error"
},
"BRK_MT_SETUP_FAIL_REJECTED_BY_POLICY_APPROVAL":{
"errorType":"ActionableError",
"name":"SE: Application approval policy blocked access",
"adminAction":"Update the approval policy to allow the user access in the time window.",
"status":"Error"
},
"AST_MT_SETUP_ERR_AST_IN_PAUSE_STATE_FOR_UPGRADE":{
"errorType":"InternalError",
"name":"AC: App Connector in paused state for upgrade",
"adminAction":"NA",
"status":"Error"
},
"BRK_MT_SETUP_FAIL_ICMP_RATE_LIMIT_NUM_APP_EXCEEDED":{
"errorType":"ActionableError",
"name":"SE: Connection failed due to the number of ICMP requests with different domains exceeded",
"adminAction":"If the request rate is expected or the problem persists, contact Zscaler Support to learn more.",
"status":"Error"
},
"MT_CLOSED_DTLS_CONN_GONE_CLIENT_CLOSED":{
"errorType":"NA",
"name":"SE: Zscaler Client Connector DTLS session not present",
"adminAction":"NA",
"status":"Info"
},
"EXPTR_MT_TLS_SETUP_FAIL_VERSION_MISMATCH":{
"errorType":"ActionableError",
"name":"ZPA BA: TLS Wrong Version Number",
"adminAction":"BA app need TLS 1.2 to be enabled on application server",
"status":"Error"
},
"BRK_MT_SETUP_FAIL_RATE_LIMIT_LOOP_DETECTED":{
"errorType":"ActionableError",
"name":"SE: Connection failed due to Microtunnel loop",
"adminAction":"Broker rejected the mtunnel request because it detected a potential mtunnel creation looping issue.",
"status":"Error"
},
"MT_CLOSED_DTLS_CONN_GONE":{
"errorType":"NA",
"name":"SE: DTLS session not present",
"adminAction":"NA",
"status":"Info"
},
"CLT_INVALID_TAG":{
"errorType":"InternalError",
"name":"CLT: Invalid tag",
"adminAction":"NA",
"status":"Error"
},
"AST_MT_SETUP_ERR_NO_SYSTEM_FD":{
"errorType":"InternalError",
"name":"AC: File descriptors are exhausted",
"adminAction":"NA",
"status":"Error"
},
"AST_MT_SETUP_ERR_NO_PROCESS_FD":{
"errorType":"InternalError",
"name":"AC: File descriptors are exhausted for App Connector process",
"adminAction":"NA",
"status":"Error"
},
"BROKER_NOT_ENABLED":{
"errorType":"InternalError",
"name":"Client to Client is disabled for Public Service Edge",
"adminAction":"NA",
"status":"Error"
},
"AST_MT_SETUP_ERR_AST_CFG_DISABLED":{
"errorType":"ActionableError",
"name":"AC: Disabled in Admin Portal",
"adminAction":"NA",
"status":"Error"
},
"BRK_MT_BROKER_REQUEST_ZVPN_NOT_FOUND":{
"errorType":"ActionableError",
"name":"SE: Cannot find ZIA Public Service Edge to service the request ",
"adminAction":"No action required. If the problem persists, contact Zscaler Support to learn more.",
"status":"Error"
},
"MT_CLOSED_TLS_CONN_GONE_MANUAL_DRAIN":{
"errorType":"NA",
"name":"SE: Connection closed by manual drain",
"adminAction":"NA",
"status":"Info"
},
"BRK_MT_SETUP_FAIL_TOO_MANY_FAILED_ATTEMPTS":{
"errorType":"ActionableError",
"name":"SE: Connection failed due to the reached limit of failed attempts",
"adminAction":"Retry after the preset waiting period has elapsed. If the problem persists, contact Zscaler Support to learn more.",
"status":"Error"
},
"BRK_MT_AUTH_NO_SAML_ASSERTION_IN_MSG":{
"errorType":"ActionableError",
"name":"SE: SAML assertion is absent",
"adminAction":"Update IdP configuration",
"status":"Error"
},
"BRK_MT_SETUP_FAIL_CTRL_BRK_CANNOT_FIND_CONNECTOR":{
"errorType":"ActionableError",
"name":"SE: Application access is not available, because broker cannot find the connector",
"adminAction":"User requested application access is not available due to broker cannot find the connector",
"status":"Error"
},
"INVALID_DOMAIN":{
"errorType":"InternalError",
"name":"AC: DNS resolution failed",
"adminAction":"NA",
"status":"Error"
},
"BRK_MT_TERMINATED_BRK_SWITCHED":{
"errorType":"ActionableError",
"name":"SE: Connection is terminated due to broker switch",
"adminAction":"Connection is terminated due to broker switch. If the problem persists, contact Zscaler Support to learn more.",
"status":"Error"
},
"BRK_MT_REJECT_HARD_DISABLED_EXTRANET":{
"errorType":"ActionableError",
"name":"SE: Cannot send M-Tunnel request due to the disabled Extranet",
"adminAction":"Contact Zscaler Support to remove the hard disable feature flag for Extranet to continue sending Microtunnel requests.",
"status":"Error"
},
"AST_MT_SETUP_ERR_OPEN_SERVER_CLOSE":{
"errorType":"NA",
"name":"AC: Connection between server and App Connector was closed",
"adminAction":"NA",
"status":"Error"
},
"AST_MT_SETUP_ERR_BIND_TO_AST_LOCAL_OWNER":{
"errorType":"InternalError",
"name":"AC: Error in local connection",
"adminAction":"NA",
"status":"Error"
},
"NO_CONNECTOR_AVAILABLE":{
"errorType":"InternalError",
"name":"CA: App Connector is not available",
"adminAction":"NA",
"status":"Error"
},
"BRK_MT_AUTH_SAML_CANNOT_ADD_ATTR_TO_HEAP":{
"errorType":"InternalError",
"name":"SE: Authentication failed due to insufficient memory",
"adminAction":"NA",
"status":"Error"
},
"EXPTR_MT_TLS_SETUP_FAIL_NOT_TRUSTED_CA":{
"errorType":"ActionableError",
"name":"ZPA BA: CA Was Not Trusted",
"adminAction":"Use a cert with a trusted CA or change settings to not require it",
"status":"Error"
},
"AST_MT_SETUP_TIMEOUT_NO_ACK_TO_BIND":{
"errorType":"InternalError",
"name":"AC: Service Edge not responding to connection request from App Connector",
"adminAction":"NA",
"status":"Error"
},
"MULTIPLE_CLIENT_REGISTRATIONS_FOR_DOMAIN":{
"errorType":"ActionableError",
"name":"CLT: Multiple clients registered with the same domain",
"adminAction":"Try again later. Ensure that no two clients are registered with the same domain. If the problem persists, contact Zscaler Support.",
"status":"Error"
},
"CLT_PORT_UNREACHABLE":{
"errorType":"InternalError",
"name":"CLT: Port Unreachable",
"adminAction":"NA",
"status":"Error"
},
"BRK_MT_CLOSED_FROM_ASSISTANT":{
"errorType":"NA",
"name":"SE: Connection closed by App Connector",
"adminAction":"NA",
"status":"Success"
},
"C2C_CLIENT_CONN_EXPIRED":{
"errorType":"InternalError",
"name":"SE: Connection expired",
"adminAction":"NA",
"status":"Error"
},
"ZPN_ERR_EXTRANET_NO_TUNNEL_AVAILABLE":{
"errorType":"ActionableError",
"name":"CA: Cannot find tunnels for ZPA Public Service Edge",
"adminAction":"Verify and validate tunnel information.",
"status":"Error"
},
"BRK_MT_SETUP_FAIL_BIND_TO_CLIENT_LOCAL_OWNER":{
"errorType":"InternalError",
"name":"SE: Error in associating connection to Client Connector",
"adminAction":"NA",
"status":"Error"
},
"BRK_MT_AUTH_SAML_CANNOT_ADD_ATTR_TO_HASH":{
"errorType":"InternalError",
"name":"SE: Authentication failed due to insufficient resources",
"adminAction":"NA",
"status":"Error"
},
"MT_CLOSED_TLS_CONN_GONE_UPGRADE":{
"errorType":"InternalError",
"name":"SE: Connection terminated due to upgrade",
"adminAction":"NA",
"status":"Info"
},
"BRK_MT_SETUP_FAIL_REPEATED_DISPATCH":{
"errorType":"ActionableError",
"name":"SE: Exceeded limit of connection request attempts",
"adminAction":"If the error persists, contact Zscaler Support.",
"status":"Error"
},
"AST_MT_SETUP_ERR_OPEN_SERVER_ERROR":{
"errorType":"InternalError",
"name":"AC: Error connecting to server",
"adminAction":"NA",
"status":"Error"
},
"MT_CLOSED_TERMINATED":{
"errorType":"NA",
"name":"SE: Connection closed successfully",
"adminAction":"NA",
"status":"Success"
},
"DSP_MT_SETUP_FAIL_DISCOVERY_TIMEOUT":{
"errorType":"ActionableError",
"name":"CA: App Connector health information request timed out",
"adminAction":"Ensure that the App Connector can reach the ZPA Public Service Edge or ZPA Private Service Edge.",
"status":"Error"
},
"CUSTOMER_NOT_ENABLED":{
"errorType":"InternalError",
"name":"Client to Client is disabled for current customer",
"adminAction":"NA",
"status":"Error"
},
"BRK_CONN_UPGRADE_REQUEST_FAILED":{
"errorType":"ActionableError",
"name":"SE: Connection upgrade request is failed",
"adminAction":"Connection upgrade request is failed. If the problem persists, contact Zscaler Support to learn more.",
"status":"Error"
},
"C2C_MTUNNEL_FAILED_FORWARD":{
"errorType":"InternalError",
"name":"SE: Connection failed to the ZPA Private Service Edge",
"adminAction":"NA",
"status":"Error"
},
"EXPTR_MT_TLS_SETUP_FAIL_CERT_CHAIN_ISSUE":{
"errorType":"ActionableError",
"name":"ZPA BA: Cert Chaining Issue",
"adminAction":"Please update the cert with a properly configured chain",
"status":"Error"
},
"MT_CLOSED_DTLS_CONN_GONE_AST_CLOSED":{
"errorType":"NA",
"name":"SE: DTLS connection closed by app connector",
"adminAction":"NA",
"status":"Info"
},
"BRK_MT_SETUP_FAIL_WEBPROBE_HTTPS_DISABLED":{
"errorType":"ActionableError",
"name":"AC: Disabled Web probe",
"adminAction":"Enable the Web probe.",
"status":"Error"
},
"AST_MT_SETUP_ERR_RATE_LIMIT_REACHED":{
"errorType":"ActionableError",
"name":"ZPA PRA: Application request failed due to an exceeded rate limit",
"adminAction":"Ask the user to request the application again, after waiting for two seconds. If the error persists, contact Zscaler Support.",
"status":"Error"
},
"BRK_MT_SETUP_FAIL_RATE_LIMIT_NUM_APP_EXCEEDED":{
"errorType":"ActionableError",
"name":"SE: Connection failed due to the number of application domains exceeded",
"adminAction":"Broker rejected the mtunnel request because it exceeded the set rate limit for different domains.",
"status":"Error"
},
"CLT_WRONG_PORT":{
"errorType":"InternalError",
"name":"CLT: Wrong port",
"adminAction":"NA",
"status":"Error"
},
"ZIA_MT_BLOCKED_BY_SYSTEM_ERROR":{
"errorType":"ActionableError",
"name":"SE: Blocked by ZIA Inspection due to system error",
"adminAction":"NA",
"status":"Error"
},
"AST_MT_SETUP_TIMEOUT_CANNOT_CONN_TO_SERVER":{
"errorType":"ActionableError",
"name":"AC: Connection request to server timed out",
"adminAction":"Check connectivity to server",
"status":"Error"
},
"ZIA_MT_BLOCKED_BY_INSPECTION":{
"errorType":"ActionableError",
"name":"SE: Blocked by ZIA Inspection",
"adminAction":"NA",
"status":"Error"
},
"MT_CLOSED_TLS_CONN_GONE_SCIM_USER_DISABLE":{
"errorType":"InternalError",
"name":"SE: User disabled via SCIM",
"adminAction":"NA",
"status":"Info"
},
"MT_CLOSED_TLS_CONN_GONE_CLIENT_CLOSED":{
"errorType":"InternalError",
"name":"SE: Client Connector TLS session not present",
"adminAction":"NA",
"status":"Info"
},
"BRK_MT_SETUP_FAIL_NO_POLICY_FOUND":{
"errorType":"ActionableError",
"name":"SE: Policy is not configured for access",
"adminAction":"Update policy to allow user",
"status":"PolicyBlock"
},
"BRK_MT_AUTH_SAML_FINGER_PRINT_FAIL":{
"errorType":"ActionableError",
"name":"SE: Failed to verify the fingerprint of SAML response",
"adminAction":"Update IdP configuration",
"status":"Error"
},
"AST_MT_SETUP_ERR_NO_EPHEMERAL_PORT":{
"errorType":"InternalError",
"name":"AC: Source ports are exhausted",
"adminAction":"NA",
"status":"Error"
},
"BRK_CONN_UPGRADE_REQUEST_FORBIDDEN":{
"errorType":"ActionableError",
"name":"SE: Connection upgrade request is forbidden",
"adminAction":"Connection upgrade request is forbidden. If the problem persists, contact Zscaler Support to learn more.",
"status":"Error"
},
"AST_MT_SETUP_ERR_OPEN_SERVER_CONN":{
"errorType":"ActionableError",
"name":"AC: Cannot open connection to server",
"adminAction":"Check connectivity to server",
"status":"Error"
},
"CLT_PROBE_FAILED":{
"errorType":"InternalError",
"name":"CLT: Probe failed",
"adminAction":"NA",
"status":"Error"
},
"BRK_MT_SETUP_FAIL_REJECTED_BY_POLICY":{
"errorType":"ActionableError",
"name":"SE: Application policy blocked access",
"adminAction":"Update policy to allow user",
"status":"PolicyBlock"
},
"AST_MT_SETUP_ERR_APP_NOT_FOUND":{
"errorType":"ActionableError",
"name":"AC: Application segment not configured",
"adminAction":"Check App availability",
"status":"Error"
},
"AST_MT_SETUP_ERR_OPEN_BROKER_CONN":{
"errorType":"ActionableError",
"name":"AC: Cannot open connection to Service Edge",
"adminAction":"Check connectivity to broker",
"status":"Error"
},
"BRK_MT_SETUP_FAIL_ICMP_RATE_LIMIT_EXCEEDED":{
"errorType":"ActionableError",
"name":"SE: Connection failed due to rate limiting for ICMP requests",
"adminAction":"If the request rate is expected or the problem persists, contact Zscaler Support to learn more.",
"status":"Error"
},
"AST_MT_SETUP_ERR_OPEN_SERVER_TIMEOUT":{
"errorType":"InternalError",
"name":"App Connector timed out while setting up a data connection to a specific server.",
"adminAction":"NA",
"status":"Error"
},
"C2C_MTUNNEL_BAD_STATE":{
"errorType":"InternalError",
"name":"SE: Connection is in a bad state",
"adminAction":"NA",
"status":"Error"
},
"CLT_DUPLICATE_TAG":{
"errorType":"InternalError",
"name":"CLT: Duplicate tag",
"adminAction":"NA",
"status":"Error"
},
"AST_MT_SETUP_TIMEOUT":{
"errorType":"InternalError",
"name":"AC: Connection request timed out",
"adminAction":"NA",
"status":"Error"
},
"CLT_DOUBLEENCRYPT_NOT_SUPPORTED":{
"errorType":"InternalError",
"name":"CLT: Double Encryption not supported",
"adminAction":"NA",
"status":"Error"
},
"BRK_MT_SETUP_FAIL_CANNOT_SEND_MT_COMPLETE":{
"errorType":"InternalError",
"name":"SE: Cannot complete data connection setup",
"adminAction":"NA",
"status":"Error"
},
"BRK_MT_SETUP_FAIL_BIND_RECV_IN_BAD_STATE":{
"errorType":"InternalError",
"name":"SE: Unexpected data connection request",
"adminAction":"NA",
"status":"Error"
},
"APP_NOT_AVAILABLE":{
"errorType":"InternalError",
"name":"CA: Application is not available",
"adminAction":"NA",
"status":"Error"
},
"BRK_MT_CLOSED_ZIA_CONN_GONE_CLOSED":{
"errorType":"ActionableError",
"name":"SE: Connection to ZIA is closed",
"adminAction":"NA",
"status":"Error"
},
"BRK_MT_AUTH_SAML_NO_USER_ID":{
"errorType":"ActionableError",
"name":"SE: User information missing in SAML response",
"adminAction":"Update IdP configuration",
"status":"Error"
},
"AST_MT_SETUP_TIMEOUT_CANNOT_CONN_TO_BROKER":{
"errorType":"ActionableError",
"name":"AC: Connection request to Service Edge timed out",
"adminAction":"Check connectivity to broker",
"status":"Error"
},
"DSP_MT_SETUP_FAIL_MISSING_HEALTH":{
"errorType":"ActionableError",
"name":"CA: Missing information for continuous health reporting",
"adminAction":"Ensure that the App Connector can reach the ZPA Public Service Edge or ZPA Private Service Edge.",
"status":"Error"
},
"AST_MT_SETUP_ERR_DUP_MT_ID":{
"errorType":"InternalError",
"name":"AC: Duplicate connection tag ID",
"adminAction":"NA",
"status":"Error"
},
"AST_MT_TERMINATED":{
"errorType":"NA",
"name":"AC: Connection closed successfully",
"adminAction":"NA",
"status":"Success"
},
"AST_MT_SETUP_ERR_BIND_GLOBAL_OWNER":{
"errorType":"InternalError",
"name":"AC: Error in non local connection",
"adminAction":"NA",
"status":"Error"
},
"BRK_MT_CLOSED_FROM_CLIENT":{
"errorType":"NA",
"name":"SE: Connection closed by Client Connector",
"adminAction":"NA",
"status":"Success"
},
"BRK_MT_TERMINATED_APPROVAL_TIMEOUT":{
"errorType":"ActionableError",
"name":"SE: Just-in-Time Approval timed out",
"adminAction":"Ask the user to access the application in the approved time window. Update the approvals for the user.",
"status":"Error"
},
"AST_MT_SETUP_ERR_BIND_ACK":{
"errorType":"InternalError",
"name":"AC: Error processing response from Service Edge",
"adminAction":"NA",
"status":"Error"
},
"CLT_CONN_FAILED":{
"errorType":"InternalError",
"name":"CLT: Connection failed",
"adminAction":"NA",
"status":"Error"
},
"BRK_MT_SETUP_FAIL_ACCESS_DENIED":{
"errorType":"InternalError",
"name":"SE: ICMP access disabled",
"adminAction":"NA",
"status":"Error"
},
"AST_MT_SETUP_ERR_INIT_FOHH_MCONN":{
"errorType":"InternalError",
"name":"AC: Cannot setup connection to Service Edge",
"adminAction":"NA",
"status":"Error"
},
"AST_MT_SETUP_ERR_MEM_LIMIT_REACHED":{
"errorType":"ActionableError",
"name":"AC: Memory Limit Exceeded for PRA Connection",
"adminAction":"Add memory to the App connector or add additional App Connectors. Contact Zscaler Support to learn more.",
"status":"Error"
},
"BRK_MT_SETUP_FAIL_DUPLICATE_TAG_ID":{
"errorType":"InternalError",
"name":"SE: Duplicate connection tag ID",
"adminAction":"NA",
"status":"Error"
},
"ZPN_ERR_EXTRANET_NO_LOCATIONS_ASSOCIATED":{
"errorType":"ActionableError",
"name":"CA: Missing locations",
"adminAction":"Select a valid location for the associated application.",
"status":"Error"
},
"BRK_MT_AUTH_SAML_FAILURE":{
"errorType":"ActionableError",
"name":"SE: Authentication unsuccessful",
"adminAction":"NA",
"status":"Error"
},
"MT_CLOSED_TLS_CONN_GONE":{
"errorType":"InternalError",
"name":"SE: TLS session not present",
"adminAction":"NA",
"status":"Info"
},
"AST_MT_SETUP_ERR_PRA_UNAVAILABLE":{
"errorType":"InternalError",
"name":"AC: Connector cannot establish PRA m_tunnel",
"adminAction":"Check if pra capability is enabled on the app-connector group",
"status":"Error"
},
"C2C_MTUNNEL_NOT_FOUND":{
"errorType":"InternalError",
"name":"SE: Connection not found",
"adminAction":"NA",
"status":"Error"
},
"MT_CLOSED_INTERNAL_ERROR":{
"errorType":"InternalError",
"name":"SE: Internal error",
"adminAction":"NA",
"status":"Error"
},
"DSP_MT_SETUP_FAIL_CANNOT_SEND_TO_BROKER":{
"errorType":"InternalError",
"name":"CA: Error communicating with Service Edge",
"adminAction":"NA",
"status":"Error"
},
"CLT_READ_FAILED":{
"errorType":"InternalError",
"name":"CLT: Local socket read failed",
"adminAction":"NA",
"status":"Error"
},
"BRK_MT_SETUP_FAIL_CANNOT_SEND_TO_DISPATCHER":{
"errorType":"InternalError",
"name":"SE: Error communicating with CA",
"adminAction":"NA",
"status":"Error"
},
"OPEN_OR_ACTIVE_CONNECTION":{
"errorType":"NA",
"name":"SE: Request was successful",
"adminAction":"NA",
"status":"Info"
},
"AST_MT_SETUP_ERR_BROKER_BIND_FAIL":{
"errorType":"InternalError",
"name":"AC: Error in data connection to Service Edge",
"adminAction":"NA",
"status":"Error"
},
"BRK_MT_SETUP_FAIL_RATE_LIMIT_EXCEEDED":{
"errorType":"ActionableError",
"name":"SE: Connection failed due to rate limiting",
"adminAction":"Broker rejected the mtunnel request because it exceeded the set rate limit",
"status":"Error"
},
"BRK_MT_REJECT_MAX_WTAG_EXCEEDED":{
"errorType":"ActionableError",
"name":"SE: Maximum workload groups reached",
"adminAction":"Reduce the number of workload groups.",
"status":"Error"
},
"CLT_INVALID_CLIENT":{
"errorType":"InternalError",
"name":"CLT: Invalid client",
"adminAction":"NA",
"status":"Error"
},
"BRK_MT_SETUP_FAIL_APP_NOT_FOUND":{
"errorType":"ActionableError",
"name":"SE: Application not configured",
"adminAction":"Check App configuration",
"status":"Error"
},
"C2C_NOT_AVAILABLE":{
"errorType":"ActionableError",
"name":"SE: Remote assistance connection unavailable",
"adminAction":"The remote connection is not available.To learn more, contact Zscaler Support.",
"status":"Error"
},
"AST_MT_SETUP_ERR_MAX_SESSIONS_REACHED":{
"errorType":"ActionableError",
"name":"AC: Maximum PRA Session Limit Reached",
"adminAction":"Add cores and memory to the App Connector or add additional App Connectors. Contact Zscaler Support to learn more.",
"status":"Error"
},
"BRK_MT_AUTH_TWO_SAML_ASSERTION_IN_MSG":{
"errorType":"ActionableError",
"name":"SE: SAML assertion is too large",
"adminAction":"Update IdP configuration",
"status":"Error"
},
"AST_MT_SETUP_ERR_CPU_LIMIT_REACHED":{
"errorType":"ActionableError",
"name":"AC: CPU Limit Exceeded for PRA Connection",
"adminAction":"Add cores to the App Connector or add additional App Connectors. Contact Zscaler Support to learn more.",
"status":"Error"
},
"BRK_MT_TERMINATED":{
"errorType":"NA",
"name":"SE: Connection closed by Service Edge",
"adminAction":"NA",
"status":"Success"
},
"AST_MT_SETUP_ERR_NO_DNS_TO_SERVER":{
"errorType":"ActionableError",
"name":"AC: DNS resolution failed for unmonitored app",
"adminAction":"User requested application access is not available due to the connector not able to resolve DNS. If the error persists, contact Zscaler Support.",
"status":"Error"
},
"BRK_MT_BROKER_REQUEST_FAIL_SEND_TO_ZVPN":{
"errorType":"ActionableError",
"name":"SE: Connection failed to forward ZPA Public Service Edge request to ZIA Public Service Edge",
"adminAction":"No action required. If the problem persists, contact Zscaler Support to learn more.",
"status":"Error"
},
"CLT_PROTOCOL_NOT_SUPPORTED":{
"errorType":"InternalError",
"name":"CLT: Protocol not supported",
"adminAction":"NA",
"status":"Error"
},
"BRK_MT_AUTH_ALREADY_FAILED":{
"errorType":"ActionableError",
"name":"SE: Multiple authentication failures",
"adminAction":"Ask user to reauthenticate",
"status":"Error"
},
"BRK_MT_SETUP_FAIL_CONNECTOR_GROUPS_MISSING":{
"errorType":"ActionableError",
"name":"SE: App Connector group not configured",
"adminAction":"NA",
"status":"Error"
},
"BRK_MT_SETUP_FAIL_SCIM_INACTIVE":{
"errorType":"ActionableError",
"name":"SE: Application access blocked because user was not active with SCIM",
"adminAction":"Ask admin to sync user accounts via SCIM to activate users",
"status":"Error"
},
"BRK_MT_SETUP_FAIL_SAML_EXPIRED":{
"errorType":"ActionableError",
"name":"SE: Timeout policy blocked access",
"adminAction":"Reauthenticate",
"status":"reauthBlock"
},
"MT_CLOSED_TLS_CONN_GONE_AST_CLOSED":{
"errorType":"InternalError",
"name":"SE: App Connector TLS session not present",
"adminAction":"NA",
"status":"Info"
},
"EXPTR_MT_TLS_SETUP_FAIL_PEER":{
"errorType":"InternalError",
"name":"ZPA BA: TLS setup failed with peer",
"adminAction":"NA",
"status":"Error"
},
"BRK_MT_REJECT_EXTRANET_NOT_ENABLED":{
"errorType":"ActionableError",
"name":"SE: Cannot send Microtunnel request for Extranet application as Extranet is disabled",
"adminAction":"Contact Zscaler Support to enable Extranet feature for the customer to continue sending Microtunnel requests.",
"status":"Error"
},
"BRK_MT_AUTH_SAML_DECODE_FAIL":{
"errorType":"InternalError",
"adminAction":"NA",
"status":"Error"
},
"AST_MT_SETUP_ERR_BRK_HASH_TBL_FULL":{
"errorType":"InternalError",
"name":"SE: Failed to process SAML response",
"adminAction":"NA",
"status":"Error"
},
"APP_NOT_REACHABLE":{
"errorType":"InternalError",
"name":"CA: Application is not reachable",
"adminAction":"NA",
"status":"Error"
},
"BRK_MT_ZVPN_ERROR":{
"errorType":"ActionableError",
"name":"SE: Cannot send Microtunnel request",
"adminAction":"No action required. If the problem persists, contact Zscaler Support to learn more.",
"status":"Error"
},
"BRK_MT_SETUP_TIMEOUT":{
"errorType":"InternalError",
"name":"SE: Connection request timed out",
"adminAction":"NA",
"status":"Error"
},
"ZPN_ERR_SCIM_INACTIVE":{
"errorType":"InternalError",
"name":"SE: User termination request received from SCIM",
"adminAction":"NA",
"status":"Info"
}
},
"zpn_sys_auth_log":{
"ZPN_STATUS_AUTH_FAILED":{
"errorType":"NA",
"name":"Authentication failed",
"adminAction":"NA",
"status":"Error"
},
"ZPN_STATUS_DISCONNECTED":{
"errorType":"NA",
"name":"Disconnected",
"adminAction":"NA",
"status":"Success"
},
"ZPN_STATUS_AUTHENTICATED":{
"errorType":"NA",
"name":"Authenticated",
"adminAction":"NA",
"status":"Success"
}
}
}
A successful response returns code 200. To learn more, see [API Response Codes and Error Messages](/zpa/api-response-codes-and-error-messages).
[]Getting Details of All LSS Log Formats
To get details of all LSS log formats:
- Send a `GET` request to the following endpoint: `/mgmtconfig/v2/admin/customers/{customerId}lssConfig/logType/formats`.
- Provide the `customerId`, the ZPA tenant ID of the customer, in the request endpoint. For example: `/mgmtconfig/v2/admin/customers/72057594037927936/lssConfig/logType/formats`.
- [View an example response](#ViewExampleResponse7)
[]{
"zpn_smb_inspection_log":{
"tsv":"%s{LogTimestamp:time} SMB Inspection Logs zpa-lss: \\t%s{Customer}\\t%s{ConnectionID}\\t%s{UserID}\\t%d{AssistantID}\\t%s{Domain} \\t%d{ServerPort}\\t%s{Transport}\\t%s{InspectionProtocolConfig}\\t%s{TrafficClassfication}\\t%s{ProtocolClassification}\\t%s{ProtocolInspectionError}\\t%s{ProtocolVersion}\\t%s{ProtocolActivityType}\\t%d{SMBSessionControlRequests}\\t%d{SMBFileOperationRequests}\\t%d{SMBGeneralMessageRequests}\\t%d{SMBRPC}\\t%d{SMBEnumeration}\\t%d{SMBSessionEnumeration}\\t%d{SMBUserListEnum}\\t%d{Application}\\t%d{ApplicationGroup}\\t%d{InspectionPolicy}\\t%d{InspectionProfile}\\t%d{ParanoiaLevel}\\t%d{InspectionControlsHitCount}\\t%d{ProcessingTime}\\t%d{RequestProcessingTime}\\t%d{ResponseProcessingTime}\\t%d{TotalBytesProcessed}\\t%d{RequestBytes}\\t%d{ResponseBytes}\\t%d{DoubleEncryption}\\t%s(,){InspectionControlArray}\\t%s(,){ControlTypeArray}\\t%s(,){InspectionControlCategories}\\t%s(,){Actions}\\t%s(,){SeveritiesArray}\\t%s(,){DescriptiveExplanationsArray}\\n",
"csv":"%s{LogTimestamp:time} SMB Inspection Logs zpa-lss: ,%s{Customer},%s{ConnectionID},%s{UserID},%d{AssistantID},%s{Domain},%d{ServerPort},%s{Transport},%s{InspectionProtocolConfig},%s{TrafficClassfication},%s{ProtocolClassification},%s{ProtocolInspectionError},%s{ProtocolVersion},%s{ProtocolActivityType},%d{SMBSessionControlRequests},%d{SMBFileOperationRequests},%d{SMBGeneralMessageRequests},%d{SMBRPC},%d{SMBEnumeration},%d{SMBSessionEnumeration},%d{SMBUserListEnum},%d{Application},%d{ApplicationGroup},%d{InspectionPolicy},%d{InspectionProfile},%d{ParanoiaLevel},%d{InspectionControlsHitCount},%d{ProcessingTime},%d{RequestProcessingTime},%d{ResponseProcessingTime},%d{TotalBytesProcessed},%d{RequestBytes},%d{ResponseBytes},%d{DoubleEncryption},%s(,){InspectionControlArray},%s(,){ControlTypeArray},%s(,){InspectionControlCategories},%s(,){Actions},%s(,){SeveritiesArray},%s(,){DescriptiveExplanationsArray}\\n",
"json":"{\"LogTimestamp\": %j{LogTimestamp:time},\"Customer\": %j{Customer},\"ConnectionID\": %j{ConnectionID},\"UserID\": %j{UserID},\"AssistantID\": %j{AssistantID},\"Domain\": %j{Domain},\"ServerPort\": %d{ServerPort},\"Transport\": %j{Transport},\"InspectionProtocolConfig\": %j{InspectionProtocolConfig},\"TrafficClassfication\": %j{TrafficClassfication},\"ProtocolClassification\": %j{ProtocolClassification},\"ProtocolInspectionError\": %j{ProtocolInspectionError},\"ProtocolVersion\": %j{ProtocolVersion},\"ProtocolActivityType\": %j{ProtocolActivityType},\"SMBSessionControlRequests\": %d{SMBSessionControlRequests},\"SMBFileOperationRequests\": %d{SMBFileOperationRequests},\"SMBGeneralMessageRequests\": %d{SMBGeneralMessageRequests},\"SMBRPC\": %d{SMBRPC},\"SMBEnumeration\": %d{SMBEnumeration},\"SMBSessionEnumeration\": %d{SMBSessionEnumeration},\"SMBUserListEnum\": %d{SMBUserListEnum},\"Application\": %d{Application},\"ApplicationGroup\": %j{ApplicationGroup},\"InspectionPolicy\": %d{InspectionPolicy},\"InspectionProfile\": %d{InspectionProfile},\"ParanoiaLevel\": %j{ParanoiaLevel},\"InspectionControlsHitCount\": %d{InspectionControlsHitCount},\"ProcessingTime\": %d{ProcessingTime},\"RequestProcessingTime\": %d{RequestProcessingTime},\"ResponseProcessingTime\": %d{ResponseProcessingTime},\"TotalBytesProcessed\": %d{TotalBytesProcessed},\"RequestBytes\": %d{RequestBytes},\"ResponseBytes\": %d{ResponseBytes},\"DoubleEncryption\": %d{DoubleEncryption},\"InspectionControls\": [%j(,){InspectionControlArray}],\"InspectionControlTypes\": [%j(,){ControlTypeArray}],\"InspectionControlCategories\": [%j(,){InspectionControlCategories}],\"Actions\": [%j(,){Actions}],\"Severities\": [%j(,){SeveritiesArray}],\"Descriptions\": [%j(,){DescriptiveExplanationsArray}]}\\n"
},
"zpn_ast_comprehensive_stats":{
"tsv":"%s{LogTimestamp:time} Connector Metric zpa-lss: \\t%s{Connector}\\t%s{CPUUtilization}\\t%s{SystemMemoryUtilization}\\t%s{ProcessMemoryUtilization}\\t%s{AppCount}\\t%s{ServiceCount}\\t%s{TargetCount}\\t%s{AliveTargetCount}\\t%s{ActiveConnectionsToPublicSE}\\t%s{DisconnectedConnectionsToPublicSE}\\t%s{ActiveConnectionsToPrivateSE}\\t%s{DisconnectedConnectionsToPrivateSE}\\t%s{TransmittedBytesToPublicSE}\\t%s{ReceivedBytesFromPublicSE}\\t%s{TransmittedBytesToPrivateSE}\\t%s{ReceivedBytesFromPrivateSE}\\t%s{AppConnectionsCreated}\\t%s{AppConnectionsCleared}\\t%s{AppConnectionsActive}\\t%s{UsedTCPPortsIPv4}\\t%s{UsedUDPPortsIPv4}\\t%s{UsedTCPPortsIPv6}\\t%s{UsedUDPPortsIPv6}\\t%s{AvailablePorts}\\t%s{SystemMaximumFileDescriptors}\\t%s{SystemUsedFileDescriptors}\\t%s{ProcessMaximumFileDescriptors}\\t%s{ProcessUsedFileDescriptors}\\t%s{AvailableDiskBytes}\\t%s{MicroTenantID}\\n",
"csv":"%s{LogTimestamp:time} Connector Metric zpa-lss: ,%s{Connector},%s{CPUUtilization},%s{SystemMemoryUtilization},%s{ProcessMemoryUtilization},%s{AppCount},%s{ServiceCount},%s{TargetCount},%s{AliveTargetCount},%s{ActiveConnectionsToPublicSE},%s{DisconnectedConnectionsToPublicSE},%s{ActiveConnectionsToPrivateSE},%s{DisconnectedConnectionsToPrivateSE},%s{TransmittedBytesToPublicSE},%s{ReceivedBytesFromPublicSE},%s{TransmittedBytesToPrivateSE},%s{ReceivedBytesFromPrivateSE},%s{AppConnectionsCreated},%s{AppConnectionsCleared},%s{AppConnectionsActive},%s{UsedTCPPortsIPv4},%s{UsedUDPPortsIPv4},%s{UsedTCPPortsIPv6},%s{UsedUDPPortsIPv6},%s{AvailablePorts},%s{SystemMaximumFileDescriptors},%s{SystemUsedFileDescriptors},%s{ProcessMaximumFileDescriptors},%s{ProcessUsedFileDescriptors},%s{AvailableDiskBytes},%s{MicroTenantID}\\n",
"json":"{\"LogTimestamp\":%j{LogTimestamp:time},\"Connector\":%j{Connector},\"CPUUtilization\":%j{CPUUtilization},\"SystemMemoryUtilization\":%j{SystemMemoryUtilization},\"ProcessMemoryUtilization\":%j{ProcessMemoryUtilization},\"AppCount\":%j{AppCount},\"ServiceCount\":%j{ServiceCount},\"TargetCount\":%j{TargetCount},\"AliveTargetCount\":%j{AliveTargetCount},\"ActiveConnectionsToPublicSE\":%j{ActiveConnectionsToPublicSE},\"DisconnectedConnectionsToPublicSE\":%j{DisconnectedConnectionsToPublicSE},\"ActiveConnectionsToPrivateSE\":%j{ActiveConnectionsToPrivateSE},\"DisconnectedConnectionsToPrivateSE\":%j{DisconnectedConnectionsToPrivateSE},\"TransmittedBytesToPublicSE\":%j{TransmittedBytesToPublicSE},\"ReceivedBytesFromPublicSE\":%j{ReceivedBytesFromPublicSE},\"TransmittedBytesToPrivateSE\":%j{TransmittedBytesToPrivateSE},\"ReceivedBytesFromPrivateSE\":%j{ReceivedBytesFromPrivateSE},\"AppConnectionsCreated\":%j{AppConnectionsCreated},\"AppConnectionsCleared\":%j{AppConnectionsCleared},\"AppConnectionsActive\":%j{AppConnectionsActive},\"UsedTCPPortsIPv4\":%j{UsedTCPPortsIPv4},\"UsedUDPPortsIPv4\":%j{UsedUDPPortsIPv4},\"UsedTCPPortsIPv6\":%j{UsedTCPPortsIPv6},\"UsedUDPPortsIPv6\":%j{UsedUDPPortsIPv6},\"AvailablePorts\":%j{AvailablePorts},\"SystemMaximumFileDescriptors\":%j{SystemMaximumFileDescriptors},\"SystemUsedFileDescriptors\":%j{SystemUsedFileDescriptors},\"ProcessMaximumFileDescriptors\":%j{ProcessMaximumFileDescriptors},\"ProcessUsedFileDescriptors\":%j{ProcessUsedFileDescriptors},\"AvailableDiskBytes\":%j{AvailableDiskBytes},\"MicroTenantID\": %j{MicroTenantID}}\\n"
},
"zpn_auth_log_1id":{
"tsv":"%s{LogTimestamp:time} User Status zpa-lss: \\t%s{Customer}\\t%s{Username}\\t%s{SessionID}\\t%s{SessionStatus}\\t%s{Version}\\t%s{ZEN}\\t%s{CertificateCN}\\t%s{PrivateIP}\\t%s{PublicIP}\\t%f{Latitude}\\t%f{Longitude}\\t%s{CountryCode}\\t%s{TimestampAuthentication:iso8601}\\t%s{TimestampUnAuthentication:iso8601}\\t%d{TotalBytesRx}\\t%d{TotalBytesTx}\\t%s{Idp}\\t%s{Hostname}\\t%s{Platform}\\t%s{ClientType}\\t%s(,){TrustedNetworks}\\t%s(,){TrustedNetworksNames}\\t%s(,){PosturesHit}\\t%s(,){PosturesMiss}\\t%f{ZENLatitude}\\t%f{ZENLongitude}\\t%s{ZENCountryCode}\\t%s{fqdn_registered}\\t%s{fqdn_register_error}\\t%s{City}\\t%s{MicroTenantID}\\n",
"csv":"%s{LogTimestamp:time} User Status zpa-lss: ,%s{Customer},%s{Username},%s{SessionID},%s{SessionStatus},%s{Version},%s{ZEN},%s{CertificateCN},%s{PrivateIP},%s{PublicIP},%f{Latitude},%f{Longitude},%s{CountryCode},%s{TimestampAuthentication:iso8601},%s{TimestampUnAuthentication:iso8601},%d{TotalBytesRx},%d{TotalBytesTx},%s{Idp},%s{Hostname},%s{Platform},%s{ClientType},%s(,){TrustedNetworks},%s(,){TrustedNetworksNames}%s(,){PosturesHit},%s(,){PosturesMiss},%f{ZENLatitude},%f{ZENLongitude},%s{ZENCountryCode},%s{fqdn_registered},%s{fqdn_register_error},%s{City},%s{MicroTenantID}\\n",
"json":"{\"LogTimestamp\": %j{LogTimestamp:time},\"Customer\": %j{Customer},\"Username\": %j{Username},\"SessionID\": %j{SessionID},\"SessionStatus\": %j{SessionStatus},\"Version\": %j{Version},\"ZEN\": %j{ZEN},\"CertificateCN\": %j{CertificateCN},\"PrivateIP\": %j{PrivateIP},\"PublicIP\": %j{PublicIP},\"Latitude\": %f{Latitude},\"Longitude\": %f{Longitude},\"CountryCode\": %j{CountryCode},\"TimestampAuthentication\": %j{TimestampAuthentication:iso8601},\"TimestampUnAuthentication\": %j{TimestampUnAuthentication:iso8601},\"TotalBytesRx\": %d{TotalBytesRx},\"TotalBytesTx\": %d{TotalBytesTx},\"Idp\": %j{Idp},\"Hostname\": %j{Hostname},\"Platform\": %j{Platform},\"ClientType\": %j{ClientType},\"TrustedNetworks\": [%j(,){TrustedNetworks}],\"TrustedNetworksNames\": [%j(,){TrustedNetworksNames}],\"PosturesHit\": [%j(,){PosturesHit}],\"PosturesMiss\": [%j(,){PosturesMiss}],\"ZENLatitude\": %f{ZENLatitude},\"ZENLongitude\": %f{ZENLongitude},\"ZENCountryCode\": %j{ZENCountryCode},\"FQDNRegistered\": %j{fqdn_registered},\"FQDNRegisteredError\": %j{fqdn_register_error},\"City\": %j{City},\"MicroTenantID\": %j{MicroTenantID}}\\n"
},
"zpn_audit_log":{
"tsv":"Audit zpa-lss: \t%s{modifiedTime:iso8601}\t%s{creationTime:iso8601}\t%s{modifiedBy}\t%s{requestId}\t%s{sessionId}\t%s{auditOldValue}\t%s{auditNewValue}\t%s{auditOperationType}\t%s{objectType}\t%s{objectName}\t%d{objectId}\t%d{customerId}\t%s{modifiedByUser}\t%d{clientAuditUpdate}\\n",
"csv":"Audit zpa-lss: ,%s{modifiedTime:iso8601},%s{creationTime:iso8601},%d{modifiedBy},%s{requestId},%s{sessionId},%s{auditOldValue},%s{auditNewValue},%s{auditOperationType},%s{objectType},%s{objectName},%d{objectId},%d{customerId},%s{modifiedByUser},%d{clientAuditUpdate}\\n",
"json":"{\"ModifiedTime\":%j{modifiedTime:iso8601},\"CreationTime\":%j{creationTime:iso8601},\"ModifiedBy\":%d{modifiedBy},\"RequestID\":%j{requestId},\"SessionID\":%j{sessionId},\"AuditOldValue\":%j{auditOldValue},\"AuditNewValue\":%j{auditNewValue},\"AuditOperationType\":%j{auditOperationType},\"ObjectType\":%j{objectType},\"ObjectName\":%j{objectName},\"ObjectID\":%d{objectId},\"CustomerID\":%d{customerId},\"User\":%j{modifiedByUser},\"ClientAuditUpdate\":%d{clientAuditUpdate}}\\n"
},
"zpn_trans_log":{
"tsv":"%s{LogTimestamp:time} User Activity zpa-lss: \\t%s{Customer}\\t%s{SessionID}\\t%s{ConnectionID}\\t%s{InternalReason}\\t%s{ConnectionStatus}\\t%d{IPProtocol}\\t%d{DoubleEncryption}\\t%s{Username}\\t%d{ServicePort}\\t%s{ClientPublicIP}\\t%s{ClientPrivateIP}\\t%f{ClientLatitude}\\t%f{ClientLongitude}\\t%s{ClientCountryCode}\\t%s{ClientZEN}\\t%s{Policy}\\t%s{Connector}\\t%s{ConnectorZEN}\\t%s{ConnectorIP}\\t%d{ConnectorPort}\\t%s{Host}\\t%s{Application}\\t%s{AppGroup}\\t%s{Server}\\t%s{ServerIP}\\t%d{ServerPort}\\t%d{PolicyProcessingTime}\\t%d{ServerSetupTime}\\t%s{TimestampConnectionStart:iso8601}\\t%s{TimestampConnectionEnd:iso8601}\\t%s{TimestampCATx:iso8601}\\t%s{TimestampCARx:iso8601}\\t%s{TimestampAppLearnStart:iso8601}\\t%s{TimestampZENFirstRxClient:iso8601}\\t%s{TimestampZENFirstTxClient:iso8601}\\t%s{TimestampZENLastRxClient:iso8601}\\t%s{TimestampZENLastTxClient:iso8601}\\t%s{TimestampConnectorZENSetupComplete:iso8601}\\t%s{TimestampZENFirstRxConnector:iso8601}\\t%s{TimestampZENFirstTxConnector:iso8601}\\t%s{TimestampZENLastRxConnector:iso8601}\\t%s{TimestampZENLastTxConnector:iso8601}\\t%d{ZENTotalBytesRxClient}\\t%d{ZENBytesRxClient}\\t%d{ZENTotalBytesTxClient}\\t%d{ZENBytesTxClient}\\t%d{ZENTotalBytesRxConnector}\\t%d{ZENBytesRxConnector}\\t%d{ZENTotalBytesTxConnector}\\t%d{ZENBytesTxConnector}\\t%s{Idp}\\t%s{c2c}\\t%s{ClientCity}\\t%s{MicroTenantID}\\t%s{AppMicroTenantID}\\t%s{PRAConnectionID}\\t%s{PRAConsoleType}\\t%d{PRAApprovalID}\\t%d{PRACapabilityPolicyID}\\t%d{PRACredentialPolicyID}\\t%s{PRACredentialUserName}\\t%s{PRACredentialLoginType}\\t%s{PRAErrorStatus}\\t%s{PRAFileTransferList}\\t%s{PRARecordingStatus}\\t%s{PRASharedUsersList}\\t%s{PRASessionType}\\t%s{PRASharedMode}\\n",
"csv":"%s{LogTimestamp:time} User Activity zpa-lss: ,%s{Customer},%s{SessionID},%s{ConnectionID},%s{InternalReason},%s{ConnectionStatus},%d{IPProtocol},%d{DoubleEncryption},%s{Username},%d{ServicePort},%s{ClientPublicIP},%s{ClientPrivateIP},%f{ClientLatitude},%f{ClientLongitude},%s{ClientCountryCode},%s{ClientZEN},%s{Policy},%s{Connector},%s{ConnectorZEN},%s{ConnectorIP},%d{ConnectorPort},%s{Host},%s{Application},%s{AppGroup},%s{Server},%s{ServerIP},%d{ServerPort},%d{PolicyProcessingTime},%d{ServerSetupTime},%s{TimestampConnectionStart:iso8601},%s{TimestampConnectionEnd:iso8601},%s{TimestampCATx:iso8601},%s{TimestampCARx:iso8601},%s{TimestampAppLearnStart:iso8601},%s{TimestampZENFirstRxClient:iso8601},%s{TimestampZENFirstTxClient:iso8601},%s{TimestampZENLastRxClient:iso8601},%s{TimestampZENLastTxClient:iso8601},%s{TimestampConnectorZENSetupComplete:iso8601},%s{TimestampZENFirstRxConnector:iso8601},%s{TimestampZENFirstTxConnector:iso8601},%s{TimestampZENLastRxConnector:iso8601},%s{TimestampZENLastTxConnector:iso8601},%d{ZENTotalBytesRxClient},%d{ZENBytesRxClient},%d{ZENTotalBytesTxClient},%d{ZENBytesTxClient},%d{ZENTotalBytesRxConnector},%d{ZENBytesRxConnector},%d{ZENTotalBytesTxConnector},%d{ZENBytesTxConnector},%s{Idp},%s{c2c},%s{ClientCity},%s{MicroTenantID},%s{AppMicroTenantID},%s{PRAConnectionID},%s{PRAConsoleType},%d{PRAApprovalID},%d{PRACapabilityPolicyID},%d{PRACredentialPolicyID},%s{PRACredentialUserName},%s{PRACredentialLoginType},%s{PRAErrorStatus},%s{PRAFileTransferList},%s{PRARecordingStatus},%s{PRASharedUsersList},%s{PRASessionType},%s{PRASharedMode}\\n",
"json":"{\"LogTimestamp\": %j{LogTimestamp:time},\"Customer\": %j{Customer},\"SessionID\": %j{SessionID},\"ConnectionID\": %j{ConnectionID},\"InternalReason\": %j{InternalReason},\"ConnectionStatus\": %j{ConnectionStatus},\"IPProtocol\": %d{IPProtocol},\"DoubleEncryption\": %d{DoubleEncryption},\"Username\": %j{Username},\"ServicePort\": %d{ServicePort},\"ClientPublicIP\": %j{ClientPublicIP},\"ClientPrivateIP\": %j{ClientPrivateIP},\"ClientLatitude\": %f{ClientLatitude},\"ClientLongitude\": %f{ClientLongitude},\"ClientCountryCode\": %j{ClientCountryCode},\"ClientZEN\": %j{ClientZEN},\"Policy\": %j{Policy},\"Connector\": %j{Connector},\"ConnectorZEN\": %j{ConnectorZEN},\"ConnectorIP\": %j{ConnectorIP},\"ConnectorPort\": %d{ConnectorPort},\"Host\": %j{Host},\"Application\": %j{Application},\"AppGroup\": %j{AppGroup},\"Server\": %j{Server},\"ServerIP\": %j{ServerIP},\"ServerPort\": %d{ServerPort},\"PolicyProcessingTime\": %d{PolicyProcessingTime},\"ServerSetupTime\": %d{ServerSetupTime},\"TimestampConnectionStart\": %j{TimestampConnectionStart:iso8601},\"TimestampConnectionEnd\": %j{TimestampConnectionEnd:iso8601},\"TimestampCATx\": %j{TimestampCATx:iso8601},\"TimestampCARx\": %j{TimestampCARx:iso8601},\"TimestampAppLearnStart\": %j{TimestampAppLearnStart:iso8601},\"TimestampZENFirstRxClient\": %j{TimestampZENFirstRxClient:iso8601},\"TimestampZENFirstTxClient\": %j{TimestampZENFirstTxClient:iso8601},\"TimestampZENLastRxClient\": %j{TimestampZENLastRxClient:iso8601},\"TimestampZENLastTxClient\": %j{TimestampZENLastTxClient:iso8601},\"TimestampConnectorZENSetupComplete\": %j{TimestampConnectorZENSetupComplete:iso8601},\"TimestampZENFirstRxConnector\": %j{TimestampZENFirstRxConnector:iso8601},\"TimestampZENFirstTxConnector\": %j{TimestampZENFirstTxConnector:iso8601},\"TimestampZENLastRxConnector\": %j{TimestampZENLastRxConnector:iso8601},\"TimestampZENLastTxConnector\": %j{TimestampZENLastTxConnector:iso8601},\"ZENTotalBytesRxClient\": %d{ZENTotalBytesRxClient},\"ZENBytesRxClient\": %d{ZENBytesRxClient},\"ZENTotalBytesTxClient\": %d{ZENTotalBytesTxClient},\"ZENBytesTxClient\": %d{ZENBytesTxClient},\"ZENTotalBytesRxConnector\": %d{ZENTotalBytesRxConnector},\"ZENBytesRxConnector\": %d{ZENBytesRxConnector},\"ZENTotalBytesTxConnector\": %d{ZENTotalBytesTxConnector},\"ZENBytesTxConnector\": %d{ZENBytesTxConnector},\"Idp\": %j{Idp},\"ClientToClient\": %j{c2c},\"ClientCity\": %j{ClientCity},\"MicroTenantID\": %j{MicroTenantID},\"AppMicroTenantID\": %j{AppMicroTenantID},\"PRAConnectionID\": %j{PRAConnectionID},\"PRAConsoleType\": %j{PRAConsoleType},\"PRAApprovalID\": %d{PRAApprovalID},\"PRACapabilityPolicyID\": %d{PRACapabilityPolicyID},\"PRACredentialPolicyID\": %d{PRACredentialPolicyID},\"PRACredentialUserName\": %j{PRACredentialUserName},\"PRACredentialLoginType\": %j{PRACredentialLoginType},\"PRAErrorStatus\": %j{PRAErrorStatus},\"PRAFileTransferList\": %j{PRAFileTransferList},\"PRARecordingStatus\": %j{PRARecordingStatus},\"PRASharedUsersList\": %j{PRASharedUsersList},\"PRASessionType\": %j{PRASessionType},\"PRASharedMode\": %j{PRASharedMode}}\\n"
},
"zpn_waf_http_exchanges_log":{
"tsv":"%s{LogTimestamp:time} Web Inspection Logs zpa-lss: \\t%s{Customer}\\t%s{ConnectionID}\\t%s{UserID}\\t%d{AssistantID}\\t%s{ConnectionID}\\t%d{ExchangeSequenceIndex}\\t%d{TimestampRequestReceiveStart}\\t%d{TimestampRequestReceiveHeaderFinish}\\t%d{TimestampRequestReceiveFinish}\\t%d{TimestampRequestTransmitStart}\\t%d{TimestampRequestTransmitFinish}\\t%d{TimestampResponseReceiveStart}\\t%d{TimestampResponseReceiveFinish}\\t%d{TimestampResponseTransmitStart}\\t%d{TimestampResponseTransmitFinish}\\t%d{TotalTimeRequestReceive}\\t%d{TotalTimeRequestTransmit}\\t%d{TotalTimeResponseReceive}\\t%d{TotalTimeResponseTransmit}\\t%s{Domain}\\t%s{Method}\\t%s{Protocol}\\t%s{ProtocolVersion}\\t%s{ContentType}\\t%s{ContentEncoding}\\t%s{TransferEncoding}\\t%s{Host}\\t%s{OriginDomain}\\t%s{URL}\\t%s{UserAgent}\\t%s{HTTPError}\\t%s{ClientPublicIp}\\t%d{ClientPort}\\t%d{UpgradeHeaderPresent}\\t%d{StatusCode}\\t%d{RequestHdrSize}\\t%d{ResponseHdrSize}\\t%d{RequestBodySize}\\t%d{ResponseBodySize}\\t%d{Application}\\t%d{ApplicationGroup}\\t%d{InspectionPolicy}\\t%d{InspectionProfile}\\t%d{ParanoiaLevel}\\t%d{InspectionControlsHitCount}\\t%d{InspectionRuleProcessingTime}\\t%d{InspectionReqHeadersProcessingTime}\\t%d{InspectionReqBodyProcessingTime}\\t%d{InspectionRespHeadersProcessingTime}\\t%d{InspectionRespBodyProcessingTime}\\t%d{CertificateId},%d{DoubleEncryption}\\t%d{SSLInspection}\\t%d{TotalBytesProcessed}\t%s(,){InspectionControlArray}\t%s(,){ControlTypeArray}\t%s(,){InspectionControlCategories}\t%s(,){Actions}\t%s(,){SeveritiesArray}\t%s(,){DescriptiveExplanationsArray}\\n",
"csv":"%s{LogTimestamp:time} Web Inspection Logs zpa-lss: ,%s{Customer},%s{ConnectionID},%s{UserID},%d{AssistantID},%s{ConnectionID},%d{ExchangeSequenceIndex},%d{TimestampRequestReceiveStart},%d{TimestampRequestReceiveHeaderFinish},%d{TimestampRequestReceiveFinish},%d{TimestampRequestTransmitStart},%d{TimestampRequestTransmitFinish},%d{TimestampResponseReceiveStart},%d{TimestampResponseReceiveFinish},%d{TimestampResponseTransmitStart},%d{TimestampResponseTransmitFinish},%d{TotalTimeRequestReceive},%d{TotalTimeRequestTransmit},%d{TotalTimeResponseReceive},%d{TotalTimeResponseTransmit},%s{Domain},%s{Method},%s{Protocol},%s{ProtocolVersion},%s{ContentType},%s{ContentEncoding},%s{TransferEncoding},%s{Host},%s{OriginDomain},%s{URL},%s{UserAgent},%s{HTTPError},%s{ClientPublicIp},%d{ClientPort},%d{UpgradeHeaderPresent},%d{StatusCode},%d{RequestHdrSize},%d{ResponseHdrSize},%d{RequestBodySize},%d{ResponseBodySize},%d{Application},%d{ApplicationGroup},%d{InspectionPolicy},%d{InspectionProfile},%d{ParanoiaLevel},%d{InspectionControlsHitCount},%d{InspectionRuleProcessingTime},%d{InspectionReqHeadersProcessingTime},%d{InspectionReqBodyProcessingTime},%d{InspectionRespHeadersProcessingTime},%d{InspectionRespBodyProcessingTime},%d{CertificateId},%d{DoubleEncryption},%d{SSLInspection},%d{TotalBytesProcessed},%s(,){InspectionControlArray},%s(,){ControlTypeArray},%s(,){InspectionControlCategories},%s(,){Actions},%s(,){SeveritiesArray},%s(,){DescriptiveExplanationsArray}\\n",
"json":"{\"LogTimestamp\": %j{LogTimestamp:time},\"Customer\": %j{Customer},\"ConnectionID\": %j{ConnectionID},\"UserID\": %j{UserID},\"AssistantID\": %j{AssistantID},\"ExchangeSequenceIndex\": %d{ExchangeSequenceIndex},\"TimestampRequestReceiveStart\": %d{TimestampRequestReceiveStart},\"TimestampRequestReceiveHeaderFinish\": %d{TimestampRequestReceiveHeaderFinish},\"TimestampRequestReceiveFinish\": %d{TimestampRequestReceiveFinish},\"TimestampRequestTransmitStart\": %d{TimestampRequestTransmitStart},\"TimestampRequestTransmitFinish\": %d{TimestampRequestTransmitFinish},\"TimestampResponseReceiveFinish\": %d{TimestampResponseReceiveFinish},\"TimestampResponseTransmitStart\": %d{TimestampResponseTransmitStart},\"TimestampResponseTransmitFinish\": %d{TimestampResponseTransmitFinish},\"TotalTimeRequestReceive\": %d{TotalTimeRequestReceive},\"TotalTimeRequestTransmit\": %d{TotalTimeRequestTransmit},\"TotalTimeResponseReceive\": %d{TotalTimeResponseReceive},\"TotalTimeResponseTransmit\": %d{TotalTimeResponseTransmit},\"Domain\": %j{Domain},\"Method\": %j{Method},\"Protocol\": %j{Protocol},\"ProtocolVersion\": %j{ProtocolVersion},\"ContentType\": %j{ContentType},\"ContentEncoding\": %j{ContentEncoding},\"TransferEncoding\": %j{TransferEncoding},\"Host\": %j{Host},\"Destination\": %j{Destination},\"OriginDomain\": %j{OriginDomain},\"URL\": %j{URL},\"UserAgent\": %j{UserAgent},\"HTTPError\": %j{HTTPError},\"ClientPublicIp\": %j{ClientPublicIp},\"ClientPort\": %d{ClientPort},\"UpgradeHeaderPresent\": %d{UpgradeHeaderPresent},\"StatusCode\": %d{StatusCode},\"RequestHdrSize\": %d{RequestHdrSize},\"ResponseHdrSize\": %d{ResponseHdrSize},\"RequestBodySize\": %d{RequestBodySize},\"ResponseBodySize\": %d{ResponseBodySize},\"Application\": %d{Application},\"ApplicationGroup\": %d{ApplicationGroup},\"InspectionPolicy\": %d{InspectionPolicy},\"InspectionProfile\": %d{InspectionProfile},\"ParanoiaLevel\": %d{ParanoiaLevel},\"InspectionControlsHitCount\": %d{InspectionControlsHitCount},\"InspectionRuleProcessingTime\": %d{InspectionRuleProcessingTime},\"InspectionReqHeadersProcessingTime\": %d{InspectionReqHeadersProcessingTime},\"InspectionReqBodyProcessingTime\": %d{InspectionReqBodyProcessingTime},\"InspectionRespHeadersProcessingTime\": %d{InspectionRespHeadersProcessingTime},\"InspectionRespBodyProcessingTime\": %d{InspectionRespBodyProcessingTime},\"CertificateId\": %d{CertificateId},\"DoubleEncryption\": %d{DoubleEncryption},\"SSLInspection\": %d{SSLInspection},\"TotalBytesProcessed\": %d{TotalBytesProcessed},\"InspectionControls\": [%j(,){InspectionControlArray}],\"InspectionControlTypes\": [%j(,){ControlTypeArray}],\"InspectionControlCategories\": [%j(,){InspectionControlCategories}],\"Actions\": [%j(,){Actions}],\"Severities\": [%j(,){SeveritiesArray}],\"Descriptions\": [%j(,){DescriptiveExplanationsArray}]}\\n"
},
"zpn_sitec_auth_log":{
"tsv":"%s{LogTimestamp:time} Private Cloud Controller Status zpa-lss: \\t%s{Customer}\\t%s{SessionID}\\t%s{SessionType}\\t%s{SessionStatus}\\t%s{Version}\\t%s{PackageVersion}\\t%s{Platform}\\t%s{ZEN}\\t%s{SiteController}\\t%s{SiteControllerGroup}\\t%s{PrivateIP}\\t%s{PublicIP}\\t%f{Latitude}\\t%f{Longitude}\\t%s{CountryCode}\\t%s{TimestampAuthentication:iso8601}\\t%s{TimestampUnAuthentication:iso8601}\\t%d{CPUUtilization}\\t%d{MemUtilization}\\t%s{InterfaceDefRoute}\\t%s{DefRouteGW}\\t%s{PrimaryDNSResolver}\\t%s{HostUpTime}\\t%s{SiteControllerStartTime}\\t%d{NumOfInterfaces}\\t%d{BytesRxInterface}\\t%d{PacketsRxInterface}\\t%d{ErrorsRxInterface}\\t%d{DiscardsRxInterface}\\t%d{BytesTxInterface}\\t%d{PacketsTxInterface}\\t%d{ErrorsTxInterface}\\t%d{DiscardsTxInterface}\\t%d{TotalBytesRx}\\t%d{TotalBytesTx}\\t%s{MicroTenantID}\\n",
"csv":"%s{LogTimestamp:time} Private Cloud Controller Status zpa-lss: ,%s{Customer},%s{SessionID},%s{SessionType},%s{SessionStatus},%s{Version},%s{PackageVersion},%s{Platform},%s{ZEN},%s{SiteController},%s{SiteControllerGroup},%s{PrivateIP},%s{PublicIP},%f{Latitude},%f{Longitude},%s{CountryCode},%s{TimestampAuthentication:iso8601},%s{TimestampUnAuthentication:iso8601},%d{CPUUtilization},%d{MemUtilization},%s{InterfaceDefRoute},%s{DefRouteGW},%s{PrimaryDNSResolver},%s{HostUpTime},%s{SiteControllerStartTime},%d{NumOfInterfaces},%d{BytesRxInterface},%d{PacketsRxInterface},%d{ErrorsRxInterface},%d{DiscardsRxInterface},%d{BytesTxInterface},%d{PacketsTxInterface},%d{ErrorsTxInterface},%d{DiscardsTxInterface},%d{TotalBytesRx},%d{TotalBytesTx},%s{MicroTenantID}\\n",
"json":"{\"LogTimestamp\": %j{LogTimestamp:time},\"Customer\": %j{Customer},\"SessionID\": %j{SessionID},\"SessionType\": %j{SessionType},\"SessionStatus\": %j{SessionStatus},\"Version\": %j{Version},\"PackageVersion\": %j{PackageVersion},\"Platform\": %j{Platform},\"ZEN\": %j{ZEN},\"PrivateCloudController\": %j{SiteController},\"PrivateCloudControllerGroup\": %j{SiteControllerGroup},\"PrivateIP\": %j{PrivateIP},\"PublicIP\": %j{PublicIP},\"Latitude\": %f{Latitude},\"Longitude\": %f{Longitude},\"CountryCode\": %j{CountryCode},\"TimestampAuthentication\": %j{TimestampAuthentication:iso8601},\"TimestampUnAuthentication\": %j{TimestampUnAuthentication:iso8601},\"CPUUtilization\": %d{CPUUtilization},\"MemUtilization\": %d{MemUtilization},\"InterfaceDefRoute\": %j{InterfaceDefRoute},\"DefRouteGW\": %j{DefRouteGW},\"PrimaryDNSResolver\": %j{PrimaryDNSResolver},\"HostUpTime\": %j{HostUpTime},\"PrivateCloudControllerStartTime\": %j{SiteControllerStartTime},\"NumOfInterfaces\": %d{NumOfInterfaces},\"BytesRxInterface\": %d{BytesRxInterface},\"PacketsRxInterface\": %d{PacketsRxInterface},\"ErrorsRxInterface\": %d{ErrorsRxInterface},\"DiscardsRxInterface\": %d{DiscardsRxInterface},\"BytesTxInterface\": %d{BytesTxInterface},\"PacketsTxInterface\": %d{PacketsTxInterface},\"ErrorsTxInterface\": %d{ErrorsTxInterface},\"DiscardsTxInterface\": %d{DiscardsTxInterface},\"TotalBytesRx\": %d{TotalBytesRx},\"TotalBytesTx\": %d{TotalBytesTx},\"MicroTenantID\": %j{MicroTenantID}}\\n"
},
"zpn_http_trans_log":{
"tsv":"%s{LogTimestamp:time} Browser Access zpa-lss:\t%s{ConnectionID}\t%s{Exporter}\t%s{TimestampRequestReceiveStart:iso8601}\t%s{TimestampRequestReceiveHeaderFinish:iso8601}\t%s{TimestampRequestReceiveFinish:iso8601}\t%s{TimestampRequestTransmitStart:iso8601}\t%s{TimestampRequestTransmitFinish:iso8601}\t%s{TimestampResponseReceiveStart:iso8601}\t%s{TimestampResponseReceiveFinish:iso8601}\t%s{TimestampResponseTransmitStart:iso8601}\t%s{TimestampResponseTransmitFinish:iso8601}\t%d{TotalTimeRequestReceive}\t%d{TotalTimeRequestTransmit}\t%d{TotalTimeResponseReceive}\t%d{TotalTimeResponseTransmit}\t%d{TotalTimeConnectionSetup}\t%d{TotalTimeServerResponse}\t%s{Method}\t%s{Protocol}\t%s{Host}\t%s{URL}\t%s{UserAgent}\t%s{XFF}\t%s{NameID}\t%d{StatusCode}\t%d{RequestSize}\t%d{ResponseSize}\t%d{ApplicationPort}\t%s{ClientPublicIp}\t%d{ClientPublicPort}\t%s{ClientPrivateIp}\t%s{Customer}\t%s{ConnectionStatus}\t%s{ConnectionReason}\t%s{Origin}\t%s{CorsToken}\\n",
"csv":"%s{LogTimestamp:time} Browser Access zpa-lss: ,%s{ConnectionID},%s{Exporter},%s{TimestampRequestReceiveStart:iso8601},%s{TimestampRequestReceiveHeaderFinish:iso8601},%s{TimestampRequestReceiveFinish:iso8601},%s{TimestampRequestTransmitStart:iso8601},%s{TimestampRequestTransmitFinish:iso8601},%s{TimestampResponseReceiveStart:iso8601},%s{TimestampResponseReceiveFinish:iso8601},%s{TimestampResponseTransmitStart:iso8601},%s{TimestampResponseTransmitFinish:iso8601},%d{TotalTimeRequestReceive},%d{TotalTimeRequestTransmit},%d{TotalTimeResponseReceive},%d{TotalTimeResponseTransmit},%d{TotalTimeConnectionSetup},%d{TotalTimeServerResponse},%s{Method},%s{Protocol},%s{Host},%s{URL},%j{UserAgent},%s{XFF},%s{NameID},%d{StatusCode},%d{RequestSize},%d{ResponseSize},%d{ApplicationPort},%s{ClientPublicIp},%d{ClientPublicPort},%s{ClientPrivateIp},%s{Customer},%s{ConnectionStatus},%j{ConnectionReason},%s{Origin},%s{CorsToken}\\n",
"json":"{\"LogTimestamp\":%j{LogTimestamp:time},\"ConnectionID\":%j{ConnectionID},\"Exporter\":%j{Exporter},\"TimestampRequestReceiveStart\":%j{TimestampRequestReceiveStart:iso8601},\"TimestampRequestReceiveHeaderFinish\":%j{TimestampRequestReceiveHeaderFinish:iso8601},\"TimestampRequestReceiveFinish\":%j{TimestampRequestReceiveFinish:iso8601},\"TimestampRequestTransmitStart\":%j{TimestampRequestTransmitStart:iso8601},\"TimestampRequestTransmitFinish\":%j{TimestampRequestTransmitFinish:iso8601},\"TimestampResponseReceiveStart\":%j{TimestampResponseReceiveStart:iso8601},\"TimestampResponseReceiveFinish\":%j{TimestampResponseReceiveFinish:iso8601},\"TimestampResponseTransmitStart\":%j{TimestampResponseTransmitStart:iso8601},\"TimestampResponseTransmitFinish\":%j{TimestampResponseTransmitFinish:iso8601},\"TotalTimeRequestReceive\":%d{TotalTimeRequestReceive},\"TotalTimeRequestTransmit\":%d{TotalTimeRequestTransmit},\"TotalTimeResponseReceive\":%d{TotalTimeResponseReceive},\"TotalTimeResponseTransmit\":%d{TotalTimeResponseTransmit},\"TotalTimeConnectionSetup\":%d{TotalTimeConnectionSetup},\"TotalTimeServerResponse\":%d{TotalTimeServerResponse},\"Method\":%j{Method},\"Protocol\":%j{Protocol},\"Host\":%j{Host},\"URL\":%j{URL},\"UserAgent\":%j{UserAgent},\"XFF\":%j{XFF},\"NameID\":%j{NameID},\"StatusCode\":%d{StatusCode},\"RequestSize\":%d{RequestSize},\"ResponseSize\":%d{ResponseSize},\"ApplicationPort\":%d{ApplicationPort},\"ClientPublicIp\":%j{ClientPublicIp},\"ClientPublicPort\":%d{ClientPublicPort},\"ClientPrivateIp\":%j{ClientPrivateIp},\"Customer\":%j{Customer},\"ConnectionStatus\":%j{ConnectionStatus},\"ConnectionReason\":%j{ConnectionReason},\"Origin\":%j{Origin},\"CorsToken\":%j{CorsToken}}\\n"
},
"zpn_ldap_inspection_log":{
"tsv":"%s{LogTimestamp:time} LDAP Inspection Logs zpa-lss: \\t%s{Customer}\\t%s{ConnectionID}\\t%s{UserID}\\t%d{AssistantID}\\t%s{Domain}\\t%d{ServerPort}\\t%s{Transport}\\t%s{InspectionProtocolConfig}\\t%s{TrafficClassfication}\\t%s{ProtocolClassification}\\t%s{ProtocolInspectionError}\\t%s{ProtocolVersion}\\t%s{ProtocolActivityType}\\t%d{LDAPNullBindRequests}\\t%d{LDAPBindRequests}\\t%d{LDAPGeneralRequests}\\t%d{LDAPModifyRequests}\\t%d{LDAPSearchRequests}\\t%d{LDAPGroupQueryRequests}\\t%d{LDAPACLQueryRequests}\\t%d{LDAPObjectPropertyRequests}\\t%d{LDAPBaseObjectQueries}\\t%d{LDAPSingleLevelQueries}\\t%d{LDAPWholeSubTreeQueries}\\t%d{Application}\\t%d{ApplicationGroup}\\t%d{InspectionPolicy}\\t%d{InspectionProfile}\\t%d{ParanoiaLevel}\\t%d{InspectionControlsHitCount}\\t%d{ProcessingTime}\\t%d{RequestProcessingTime}\\t%d{ResponseProcessingTime}\\t%d{TotalBytesProcessed}\\t%d{RequestBytes}\\t%d{ResponseBytes}\\t%d{DoubleEncryption}\t%s(,){InspectionControlArray}\t%s(,){ControlTypeArray}\t%s(,){InspectionControlCategories}\t%s(,){Actions}\t%s(,){SeveritiesArray}\t%s(,){DescriptiveExplanationsArray}\\n",
"csv":"%s{LogTimestamp:time} LDAP Inspection Logs zpa-lss: ,%s{Customer},%s{ConnectionID},%s{UserID},%d{AssistantID},%s{Domain},%d{ServerPort},%s{Transport},%s{InspectionProtocolConfig},%s{TrafficClassfication},%s{ProtocolClassification},%s{ProtocolInspectionError},%s{ProtocolVersion},%s{ProtocolActivityType},%d{LDAPNullBindRequests},%d{LDAPBindRequests},%d{LDAPGeneralRequests},%d{LDAPModifyRequests},%d{LDAPSearchRequests},%d{LDAPGroupQueryRequests},%d{LDAPACLQueryRequests},%d{LDAPObjectPropertyRequests},%d{LDAPBaseObjectQueries},%d{LDAPSingleLevelQueries},%d{LDAPWholeSubTreeQueries},%d{Application},%d{ApplicationGroup},%d{InspectionPolicy},%d{InspectionProfile},%d{ParanoiaLevel},%d{InspectionControlsHitCount},%d{ProcessingTime},%d{RequestProcessingTime},%d{ResponseProcessingTime},%d{TotalBytesProcessed},%d{RequestBytes},%d{ResponseBytes},%d{DoubleEncryption},%s(,){InspectionControlArray},%s(,){ControlTypeArray},%s(,){InspectionControlCategories},%s(,){Actions},%s(,){SeveritiesArray},%s(,){DescriptiveExplanationsArray}\\n",
"json":"{\"LogTimestamp\": %j{LogTimestamp:time},\"Customer\": %j{Customer},\"ConnectionID\": %j{ConnectionID},\"UserID\": %j,{UserID},\"AssistantID\": %j{AssistantID},\"Domain\": %j{Domain},\"ServerPort\": %d{ServerPort},\"Transport\": %j{Transport},\"InspectionProtocolConfig\": %j{InspectionProtocolConfig},\"TrafficClassfication\": %j{TrafficClassfication},\"ProtocolClassification\": %j{ProtocolClassification},\"ProtocolInspectionError\": %j{ProtocolInspectionError},\"ProtocolVersion\": %j{ProtocolVersion},\"ProtocolActivityType\": %j{ProtocolActivityType},\"LDAPNullBindRequests\": %d{LDAPNullBindRequests},\"LDAPBindRequests\": %d{LDAPBindRequests},\"LDAPGeneralRequests\": %d{LDAPGeneralRequests},\"LDAPModifyRequests\": %d{LDAPModifyRequests},\"LDAPSearchRequests\": %d{LDAPSearchRequests},\"LDAPGroupQueryRequests\": %d{LDAPGroupQueryRequests},\"LDAPACLQueryRequests\": %d{LDAPACLQueryRequests},\"LDAPObjectPropertyRequests\": %d{LDAPObjectPropertyRequests},\"LDAPBaseObjectQueries\": %d{LDAPBaseObjectQueries},\"LDAPSingleLevelQueries\": %d{LDAPSingleLevelQueries},\"LDAPWholeSubTreeQueries\": %d{LDAPWholeSubTreeQueries},\"Application\": %d{Application},\"ApplicationGroup\": %j{ApplicationGroup},\"InspectionPolicy\": %d{InspectionPolicy},\"InspectionProfile\": %d{InspectionProfile},\"ParanoiaLevel\": %j{ParanoiaLevel},\"InspectionControlsHitCount\": %d{InspectionControlsHitCount},\"ProcessingTime\": %d{ProcessingTime},\"RequestProcessingTime\": %d{RequestProcessingTime},\"ResponseProcessingTime\": %d{ResponseProcessingTime},\"TotalBytesProcessed\": %d{TotalBytesProcessed},\"RequestBytes\": %d{RequestBytes},\"ResponseBytes\": %d{ResponseBytes},\"DoubleEncryption\": %d{DoubleEncryption},\"InspectionControls\": [%j(,){InspectionControlArray}],\"InspectionControlTypes\": [%j(,){ControlTypeArray}],\"InspectionControlCategories\": [%j(,){InspectionControlCategories}],\"Actions\": [%j(,){Actions}],\"Severities\": [%j(,){SeveritiesArray}],\"Descriptions\": [%j(,){DescriptiveExplanationsArray}]}\\n"
},
"zms_flow_log":{
"tsv":"%s{LogTimestamp:time} Flow Logs zms-lss: \\t%s{Customer}\\t%s{AgentID}\\t%s{AgentName}\\t%s{ResourceID}\\t%s{ResourceName}\\t%s{AppZoneID}\\t%s{AppZoneName}\\t%s{ConnectionStartTime:iso8601}\\t%s{SourceIP}\\t%s{DestinationIP}\\t%d(,){SourcePorts}\\t%d{DestinationPort}\\t%d{Protocol}\\t%s(,){AppName}\\t%s(,){AppExecutablePath}\\t%s{Direction}\\t%s{PolicyID}\\t%s{PolicyName}\\t%s{EnforcementReason}\\t%s{EnforcementAction}\\t%s{EnforcementDisposition}\\n",
"csv":"%s{LogTimestamp:time} Flow Logs zms-lss: ,%s{Customer},%s{AgentID},%s{AgentName},%s{ResourceID},%s{ResourceName},%s{AppZoneID},%s{AppZoneName},%s{ConnectionStartTime:iso8601},%s{SourceIP},%s{DestinationIP},%d(,){SourcePorts},%d{DestinationPort},%d{Protocol},%s(,){AppName},%s(,){AppExecutablePath},%s{Direction},%s{PolicyID},%s{PolicyName},%s{EnforcementReason},%s{EnforcementAction},%s{EnforcementDisposition}\\n",
"json":"{\"LogTimestamp\": %j{LogTimestamp:time},\"Customer\": %j{Customer},\"AgentID\": %j{AgentID},\"AgentName\": %j{AgentName},\"ResourceID\": %j{ResourceID},\"ResourceName\": %j{ResourceName},\"AppZoneID\": %j{AppZoneID},\"AppZoneName\": %j{AppZoneName},\"ConnectionStartTime\": %j{ConnectionStartTime:iso8601},\"SourceIP\": %j{SourceIP},\"DestinationIP\": %j{DestinationIP},\"SourcePorts\": [%d(,){SourcePorts}],\"DestinationPort\": %d{DestinationPort},\"Protocol\": %d{Protocol},\"AppName\": [%j(,){AppName}],\"AppExecutablePath\": [%j(,){AppExecutablePath}],\"Direction\": %j{Direction},\"PolicyID\": %j{PolicyID},\"PolicyName\": %j{PolicyName},\"EnforcementReason\": %j{EnforcementReason},\"EnforcementAction\": %j{EnforcementAction},\"EnforcementDisposition\": %j{EnforcementDisposition}}\\n"
},
"zpn_auth_log":{
"tsv":"%s{LogTimestamp:time} User Status zpa-lss: \\t%s{Customer}\\t%s{Username}\\t%s{SessionID}\\t%s{SessionStatus}\\t%s{Version}\\t%s{ZEN}\\t%s{CertificateCN}\\t%s{PrivateIP}\\t%s{PublicIP}\\t%f{Latitude}\\t%f{Longitude}\\t%s{CountryCode}\\t%s{TimestampAuthentication:iso8601}\\t%s{TimestampUnAuthentication:iso8601}\\t%d{TotalBytesRx}\\t%d{TotalBytesTx}\\t%s{Idp}\\t%s{Hostname}\\t%s{Platform}\\t%s{ClientType}\\t%s(,){TrustedNetworks}\\t%s(,){TrustedNetworksNames}\\t%s{SAMLAttributes}\\t%s(,){PosturesHit}\\t%s(,){PosturesMiss}\\t%f{ZENLatitude}\\t%f{ZENLongitude}\\t%s{ZENCountryCode}\\t%s{fqdn_registered}\\t%s{fqdn_register_error}\\t%s{City}\\t%s{MicroTenantID}\\n",
"csv":"%s{LogTimestamp:time} User Status zpa-lss: ,%s{Customer},%s{Username},%s{SessionID},%s{SessionStatus},%s{Version},%s{ZEN},%s{CertificateCN},%s{PrivateIP},%s{PublicIP},%f{Latitude},%f{Longitude},%s{CountryCode},%s{TimestampAuthentication:iso8601},%s{TimestampUnAuthentication:iso8601},%d{TotalBytesRx},%d{TotalBytesTx},%s{Idp},%s{Hostname},%s{Platform},%s{ClientType},%s(,){TrustedNetworks},%s(,){TrustedNetworksNames},%s{SAMLAttributes},%s(,){PosturesHit},%s(,){PosturesMiss},%f{ZENLatitude},%f{ZENLongitude},%s{ZENCountryCode},%s{fqdn_registered},%s{fqdn_register_error},%s{City},%s{MicroTenantID}\\n",
"json":"{\"LogTimestamp\": %j{LogTimestamp:time},\"Customer\": %j{Customer},\"Username\": %j{Username},\"SessionID\": %j{SessionID},\"SessionStatus\": %j{SessionStatus},\"Version\": %j{Version},\"ZEN\": %j{ZEN},\"CertificateCN\": %j{CertificateCN},\"PrivateIP\": %j{PrivateIP},\"PublicIP\": %j{PublicIP},\"Latitude\": %f{Latitude},\"Longitude\": %f{Longitude},\"CountryCode\": %j{CountryCode},\"TimestampAuthentication\": %j{TimestampAuthentication:iso8601},\"TimestampUnAuthentication\": %j{TimestampUnAuthentication:iso8601},\"TotalBytesRx\": %d{TotalBytesRx},\"TotalBytesTx\": %d{TotalBytesTx},\"Idp\": %j{Idp},\"Hostname\": %j{Hostname},\"Platform\": %j{Platform},\"ClientType\": %j{ClientType},\"TrustedNetworks\": [%j(,){TrustedNetworks}],\"TrustedNetworksNames\": [%j(,){TrustedNetworksNames}],\"SAMLAttributes\": %j{SAMLAttributes},\"PosturesHit\": [%j(,){PosturesHit}],\"PosturesMiss\": [%j(,){PosturesMiss}],\"ZENLatitude\": %f{ZENLatitude},\"ZENLongitude\": %f{ZENLongitude},\"ZENCountryCode\": %j{ZENCountryCode},\"FQDNRegistered\": %j{fqdn_registered},\"FQDNRegisteredError\": %j{fqdn_register_error},\"City\": %j{City},\"MicroTenantID\": %j{MicroTenantID}}\\n"
},
"zpn_pbroker_comprehensive_stats":{
"tsv":"%s{LogTimestamp:time} Service Edge Metric zpa-lss: \\t%s{PrivateSE}\\t%s{CPUUtilization}\\t%s{SystemMemoryUtilization}\\t%s{ProcessMemoryUtilization}\\t%s{UsedTCPPortsIPv4}\\t%s{UsedUDPPortsIPv4}\\t%s{UsedTCPPortsIPv6}\\t%s{UsedUDPPortsIPv6}\\t%s{AvailablePorts}\\t%s{SystemMaximumFileDescriptors}\\t%s{SystemUsedFileDescriptors}\\t%s{ProcessMaximumFileDescriptors}\\t%s{ProcessUsedFileDescriptors}\\t%s{AvailableDiskBytes}\\n",
"csv":"%s{LogTimestamp:time} Service Edge Metric zpa-lss: ,%s{PrivateSE},%s{CPUUtilization},%s{SystemMemoryUtilization},%s{ProcessMemoryUtilization},%s{UsedTCPPortsIPv4},%s{UsedUDPPortsIPv4},%s{UsedTCPPortsIPv6},%s{UsedUDPPortsIPv6},%s{AvailablePorts},%s{SystemMaximumFileDescriptors},%s{SystemUsedFileDescriptors},%s{ProcessMaximumFileDescriptors},%s{ProcessUsedFileDescriptors},%s{AvailableDiskBytes}\\n",
"json":"{\"LogTimestamp\":%j{LogTimestamp:time},\"PrivateSE\":%j{PrivateSE},\"CPUUtilization\":%j{CPUUtilization},\"SystemMemoryUtilization\":%j{SystemMemoryUtilization},\"ProcessMemoryUtilization\":%j{ProcessMemoryUtilization},\"UsedTCPPortsIPv4\":%j{UsedTCPPortsIPv4},\"UsedUDPPortsIPv4\":%j{UsedUDPPortsIPv4},\"UsedTCPPortsIPv6\":%j{UsedTCPPortsIPv6},\"UsedUDPPortsIPv6\":%j{UsedUDPPortsIPv6},\"AvailablePorts\":%j{AvailablePorts},\"SystemMaximumFileDescriptors\":%j{SystemMaximumFileDescriptors},\"SystemUsedFileDescriptors\":%j{SystemUsedFileDescriptors},\"ProcessMaximumFileDescriptors\":%j{ProcessMaximumFileDescriptors},\"ProcessUsedFileDescriptors\":%j{ProcessUsedFileDescriptors},\"AvailableDiskBytes\":%j{AvailableDiskBytes}}\\n"
},
"zpn_ast_auth_log":{
"tsv":"%s{LogTimestamp:time} Connector Status zpa-lss: \\t%s{Customer}\\t%s{SessionID}\\t%s{SessionType}\\t%s{SessionStatus}\\t%s{Version}\\t%s{Platform}\\t%s{ZEN}\\t%s{Connector}\\t%s{ConnectorGroup}\\t%s{PrivateIP}\\t%s{PublicIP}\\t%f{Latitude}\\t%f{Longitude}\\t%s{CountryCode}\\t%s{TimestampAuthentication:iso8601}\\t%s{TimestampUnAuthentication:iso8601}\\t%d{CPUUtilization}\\t%d{MemUtilization}\\t%d{ServiceCount}\\t%s{InterfaceDefRoute}\\t%s{DefRouteGW}\\t%s{PrimaryDNSResolver}\\t%s{HostStartTime}\\t%s{ConnectorStartTime}\\t%d{NumOfInterfaces}\\t%d{BytesRxInterface}\\t%d{PacketsRxInterface}\\t%d{ErrorsRxInterface}\\t%d{DiscardsRxInterface}\\t%d{BytesTxInterface}\\t%d{PacketsTxInterface}\\t%d{ErrorsTxInterface}\\t%d{DiscardsTxInterface}\\t%d{TotalBytesRx}\\t%d{TotalBytesTx}\\t%s{MicroTenantID}\\n",
"csv":"%s{LogTimestamp:time} Connector Status zpa-lss: ,%s{Customer},%s{SessionID},%s{SessionType},%s{SessionStatus},%s{Version},%s{Platform},%s{ZEN},%s{Connector},%s{ConnectorGroup},%s{PrivateIP},%s{PublicIP},%f{Latitude},%f{Longitude},%s{CountryCode},%s{TimestampAuthentication:iso8601},%s{TimestampUnAuthentication:iso8601},%d{CPUUtilization},%d{MemUtilization},%d{ServiceCount},%s{InterfaceDefRoute},%s{DefRouteGW},%s{PrimaryDNSResolver},%s{HostStartTime},%s{ConnectorStartTime},%d{NumOfInterfaces},%d{BytesRxInterface},%d{PacketsRxInterface},%d{ErrorsRxInterface},%d{DiscardsRxInterface},%d{BytesTxInterface},%d{PacketsTxInterface},%d{ErrorsTxInterface},%d{DiscardsTxInterface},%d{TotalBytesRx},%d{TotalBytesTx},%s{MicroTenantID}\\n",
"json":"{\"LogTimestamp\": %j{LogTimestamp:time},\"Customer\": %j{Customer},\"SessionID\": %j{SessionID},\"SessionType\": %j{SessionType},\"SessionStatus\": %j{SessionStatus},\"Version\": %j{Version},\"Platform\": %j{Platform},\"ZEN\": %j{ZEN},\"Connector\": %j{Connector},\"ConnectorGroup\": %j{ConnectorGroup},\"PrivateIP\": %j{PrivateIP},\"PublicIP\": %j{PublicIP},\"Latitude\": %f{Latitude},\"Longitude\": %f{Longitude},\"CountryCode\": %j{CountryCode},\"TimestampAuthentication\": %j{TimestampAuthentication:iso8601},\"TimestampUnAuthentication\": %j{TimestampUnAuthentication:iso8601},\"CPUUtilization\": %d{CPUUtilization},\"MemUtilization\": %d{MemUtilization},\"ServiceCount\": %d{ServiceCount},\"InterfaceDefRoute\": %j{InterfaceDefRoute},\"DefRouteGW\": %j{DefRouteGW},\"PrimaryDNSResolver\": %j{PrimaryDNSResolver},\"HostStartTime\": %j{HostStartTime},\"ConnectorStartTime\": %j{ConnectorStartTime},\"NumOfInterfaces\": %d{NumOfInterfaces},\"BytesRxInterface\": %d{BytesRxInterface},\"PacketsRxInterface\": %d{PacketsRxInterface},\"ErrorsRxInterface\": %d{ErrorsRxInterface},\"DiscardsRxInterface\": %d{DiscardsRxInterface},\"BytesTxInterface\": %d{BytesTxInterface},\"PacketsTxInterface\": %d{PacketsTxInterface},\"ErrorsTxInterface\": %d{ErrorsTxInterface},\"DiscardsTxInterface\": %d{DiscardsTxInterface},\"TotalBytesRx\": %d{TotalBytesRx},\"TotalBytesTx\": %d{TotalBytesTx},\"MicroTenantID\": %j{MicroTenantID}}\\n"
},
"zpn_sys_auth_log":{
"tsv":"%s{LogTimestamp:time} Service Edge Status zpa-lss: \\t%s{Customer}\\t%s{SessionID}\\t%s{SessionType}\\t%s{SessionStatus}\\t%s{Version}\\t%s{PackageVersion}\\t%s{Platform}\\t%s{ZEN}\\t%s{ServiceEdge}\\t%s{ServiceEdgeGroup}\\t%s{PrivateIP}\\t%s{PublicIP}\\t%f{Latitude}\\t%f{Longitude}\\t%s{CountryCode}\\t%s{TimestampAuthentication:iso8601}\\t%s{TimestampUnAuthentication:iso8601}\\t%d{CPUUtilization}\\t%d{MemUtilization}\\t%s{InterfaceDefRoute}\\t%s{DefRouteGW}\\t%s{PrimaryDNSResolver}\\t%s{HostUpTime}\\t%s{ServiceEdgeStartTime}\\t%d{NumOfInterfaces}\\t%d{BytesRxInterface}\\t%d{PacketsRxInterface}\\t%d{ErrorsRxInterface}\\t%d{DiscardsRxInterface}\\t%d{BytesTxInterface}\\t%d{PacketsTxInterface}\\t%d{ErrorsTxInterface}\\t%d{DiscardsTxInterface}\\t%d{TotalBytesRx}\\t%d{TotalBytesTx}\\t%s{MicroTenantID}\\n",
"csv":"%s{LogTimestamp:time} Service Edge Status zpa-lss: ,%s{Customer},%s{SessionID},%s{SessionType},%s{SessionStatus},%s{Version},%s{PackageVersion},%s{Platform},%s{ZEN},%s{ServiceEdge},%s{ServiceEdgeGroup},%s{PrivateIP},%s{PublicIP},%f{Latitude},%f{Longitude},%s{CountryCode},%s{TimestampAuthentication:iso8601},%s{TimestampUnAuthentication:iso8601},%d{CPUUtilization},%d{MemUtilization},%s{InterfaceDefRoute},%s{DefRouteGW},%s{PrimaryDNSResolver},%s{HostUpTime},%s{ServiceEdgeStartTime},%d{NumOfInterfaces},%d{BytesRxInterface},%d{PacketsRxInterface},%d{ErrorsRxInterface},%d{DiscardsRxInterface},%d{BytesTxInterface},%d{PacketsTxInterface},%d{ErrorsTxInterface},%d{DiscardsTxInterface},%d{TotalBytesRx},%d{TotalBytesTx},%s{MicroTenantID}\\n",
"json":"{\"LogTimestamp\": %j{LogTimestamp:time},\"Customer\": %j{Customer},\"SessionID\": %j{SessionID},\"SessionType\": %j{SessionType},\"SessionStatus\": %j{SessionStatus},\"Version\": %j{Version},\"PackageVersion\": %j{PackageVersion},\"Platform\": %j{Platform},\"ZEN\": %j{ZEN},\"ServiceEdge\": %j{ServiceEdge},\"ServiceEdgeGroup\": %j{ServiceEdgeGroup},\"PrivateIP\": %j{PrivateIP},\"PublicIP\": %j{PublicIP},\"Latitude\": %f{Latitude},\"Longitude\": %f{Longitude},\"CountryCode\": %j{CountryCode},\"TimestampAuthentication\": %j{TimestampAuthentication:iso8601},\"TimestampUnAuthentication\": %j{TimestampUnAuthentication:iso8601},\"CPUUtilization\": %d{CPUUtilization},\"MemUtilization\": %d{MemUtilization},\"InterfaceDefRoute\": %j{InterfaceDefRoute},\"DefRouteGW\": %j{DefRouteGW},\"PrimaryDNSResolver\": %j{PrimaryDNSResolver},\"HostUpTime\": %j{HostUpTime},\"ServiceEdgeStartTime\": %j{ServiceEdgeStartTime},\"NumOfInterfaces\": %d{NumOfInterfaces},\"BytesRxInterface\": %d{BytesRxInterface},\"PacketsRxInterface\": %d{PacketsRxInterface},\"ErrorsRxInterface\": %d{ErrorsRxInterface},\"DiscardsRxInterface\": %d{DiscardsRxInterface},\"BytesTxInterface\": %d{BytesTxInterface},\"PacketsTxInterface\": %d{PacketsTxInterface},\"ErrorsTxInterface\": %d{ErrorsTxInterface},\"DiscardsTxInterface\": %d{DiscardsTxInterface},\"TotalBytesRx\": %d{TotalBytesRx},\"TotalBytesTx\": %d{TotalBytesTx},\"MicroTenantID\": %j{MicroTenantID}}\\n"
},
"zpn_krb_inspection_log":{
"tsv":"%s{LogTimestamp:time} KRB Inspection Logs zpa-lss: \\t%s{Customer}\\t%s{ConnectionID}\\t%s{UserID}\\t%d{AssistantID}\\t%s{Domain}\\t%d{ServerPort}\\t%s{Transport}\\t%s{InspectionProtocolConfig} \\t%s{TrafficClassfication}\\t%s{ProtocolClassification}\\t%s{ProtocolInspectionError}\\t%s{ProtocolVersion}\\t%s{ProtocolActivityType}\\t%s{KRBRealm}t%s{KRBClientRealm}t%s{KRBUserPrincipal}t%s{KRBServicePrincipal}t%s{KRBEncryption}t%s{KRBTicketEncryption}t%s{KRBErrorCode}\\t%d{Application}\\t%d{ApplicationGroup}\\t%d{InspectionPolicy}\\t%d{InspectionProfile}\\t%d{ParanoiaLevel}\\t%d{InspectionControlsHitCount}\\t%d{ProcessingTime}\\t%d{RequestProcessingTime}\\t%d{ResponseProcessingTime}\\t%d{TotalBytesProcessed}\\t%d{RequestBytes}\\t%d{ResponseBytes}\\t%d{DoubleEncryption}\\t%s(,){InspectionControlArray}\\t%s(,){ControlTypeArray}\\t%s(,){InspectionControlCategories}\\t%s(,){Actions}\\t%s(,){SeveritiesArray}\\t%s(,){DescriptiveExplanationsArray}\\n",
"csv":"%s{LogTimestamp:time} KRB Inspection Logs zpa-lss:,%s{Customer},%s{ConnectionID},%s{UserID},%d{AssistantID},%s{Domain},%d{ServerPort},%s{Transport},%s{InspectionProtocolConfig},%s{TrafficClassfication},%s{ProtocolClassification},%s{ProtocolInspectionError},%s{ProtocolVersion},%s{ProtocolActivityType},%s{KRBRealm},%s{KRBClientRealm},%s{KRBUserPrincipal},%s{KRBServicePrincipal},%s{KRBEncryption},%s{KRBTicketEncryption},%s{KRBErrorCode},%d{Application},%d{ApplicationGroup},%d{InspectionPolicy},%d{InspectionProfile},%d{ParanoiaLevel},%d{InspectionControlsHitCount},%d{ProcessingTime},%d{RequestProcessingTime},%d{ResponseProcessingTime},%d{TotalBytesProcessed},%d{RequestBytes},%d{ResponseBytes},%d{DoubleEncryption},%s(,){InspectionControlArray},%s(,){ControlTypeArray},%s(,){InspectionControlCategories},%s(,){Actions},%s(,){SeveritiesArray},%s(,){DescriptiveExplanationsArray}\\n",
"json":"{\"LogTimestamp\": %j{LogTimestamp:time},\"Customer\": %j{Customer},\"ConnectionID\": %j{ConnectionID},\"UserID\": %j{UserID},\"AssistantID\": %j{AssistantID},\"Domain\": %j{Domain},\"ServerPort\": %d{ServerPort},\"Transport\": %j{Transport},\"InspectionProtocolConfig\": %j{InspectionProtocolConfig},\"TrafficClassfication\": %j{TrafficClassfication} ,\"ProtocolClassification\": %j{ProtocolClassification},\"ProtocolInspectionError\": %j{ProtocolInspectionError},\"ProtocolVersion\": %j{ProtocolVersion},\"ProtocolActivityType\": %j{ProtocolActivityType},\"KRBRealm\": %j{KRBRealm},\"KRBClientRealm\": %j{KRBClientRealm},\"KRBUserPrincipal\": %j{KRBUserPrincipal},\"KRBServicePrincipal\": %j{KRBServicePrincipal},\"KRBEncryption\": %j{KRBEncryption},\"KRBTicketEncryption\": %j{KRBTicketEncryption},\"KRBErrorCode\": %j{KRBErrorCode},\"Application\": %d{Application},\"ApplicationGroup\": %j{ApplicationGroup},\"InspectionPolicy\": %d{InspectionPolicy},\"InspectionProfile\": %d{InspectionProfile},\"ParanoiaLevel\": %j{ParanoiaLevel},\"InspectionControlsHitCount\": %d{InspectionControlsHitCount},\"ProcessingTime\": %d{ProcessingTime},\"RequestProcessingTime\": %d{RequestProcessingTime},\"ResponseProcessingTime\": %d{ResponseProcessingTime},\"TotalBytesProcessed\": %d{TotalBytesProcessed},\"RequestBytes\": %d{RequestBytes},\"ResponseBytes\": %d{ResponseBytes},\"DoubleEncryption\": %d{DoubleEncryption},\"InspectionControls\": [%j(,){InspectionControlArray}],\"InspectionControlTypes\": [%j(,){ControlTypeArray}],\"InspectionControlCategories\": [%j(,){InspectionControlCategories}],\"Actions\": [%j(,){Actions}],\"Severities\": [%j(,){SeveritiesArray}],\"Descriptions\": [%j(,){DescriptiveExplanationsArray}]}\\n"
},
"zpn_sitec_comprehensive_stats":{
"tsv":"%s{LogTimestamp:time} Private Cloud Controller Metric zpa-lss: \\t%s{SiteController}\\t%s{CPUUtilization}\\t%s{SystemMemoryUtilization}\\t%s{ProcessMemoryUtilization}\\t%s{UsedTCPPortsIPv4}\\t%s{UsedUDPPortsIPv4}\\t%s{UsedTCPPortsIPv6}\\t%s{UsedUDPPortsIPv6}\\t%s{AvailablePorts}\\t%s{SystemMaximumFileDescriptors}\\t%s{SystemUsedFileDescriptors}\\t%s{ProcessMaximumFileDescriptors}\\t%s{ProcessUsedFileDescriptors}\\t%s{AvailableDiskBytes}\\n",
"csv":"%s{LogTimestamp:time} Private Cloud Controller Metric zpa-lss: ,%s{SiteController},%s{CPUUtilization},%s{SystemMemoryUtilization},%s{ProcessMemoryUtilization},%s{UsedTCPPortsIPv4},%s{UsedUDPPortsIPv4},%s{UsedTCPPortsIPv6},%s{UsedUDPPortsIPv6},%s{AvailablePorts},%s{SystemMaximumFileDescriptors},%s{SystemUsedFileDescriptors},%s{ProcessMaximumFileDescriptors},%s{ProcessUsedFileDescriptors},%s{AvailableDiskBytes}\\n",
"json":"{\"LogTimestamp\":%j{LogTimestamp:time},\"PrivateCloudController\":%j{SiteController},\"CPUUtilization\":%j{CPUUtilization},\"SystemMemoryUtilization\":%j{SystemMemoryUtilization},\"ProcessMemoryUtilization\":%j{ProcessMemoryUtilization},\"UsedTCPPortsIPv4\":%j{UsedTCPPortsIPv4},\"UsedUDPPortsIPv4\":%j{UsedUDPPortsIPv4},\"UsedTCPPortsIPv6\":%j{UsedTCPPortsIPv6},\"UsedUDPPortsIPv6\":%j{UsedUDPPortsIPv6},\"AvailablePorts\":%j{AvailablePorts},\"SystemMaximumFileDescriptors\":%j{SystemMaximumFileDescriptors},\"SystemUsedFileDescriptors\":%j{SystemUsedFileDescriptors},\"ProcessMaximumFileDescriptors\":%j{ProcessMaximumFileDescriptors},\"ProcessUsedFileDescriptors\":%j{ProcessUsedFileDescriptors},\"AvailableDiskBytes\":%j{AvailableDiskBytes}}\\n"
}
}
[]Creating a New LSS Configuration
To create a new LSS configuration:
- Send a `POST` request to the following endpoint: `/mgmtconfig/v2/admin/customers/{customerId}/lssConfig`.
- Provide the `customerId`, the ZPA tenant ID of the customer, in the request endpoint. For example: `/mgmtconfig/v2/admin/customers/217246660302995456/lssConfig`.
- Include the request headers to provide information about the request context:
- Content-Type: `application/json`
- Authorization: `Bearer <access_token>`
- Use the following JSON payload to create a new LSS configuration and provide the following information:
- `name`: The object of the LSS resource.
- `format`: The format of the LSS resource.
- `lssHost`: The host of the LSS resource.
- `lssPort`: The port of the LSS resource.
- `filter`: The filter of the LSS resource.
- `sourceLogType`: The log type of the LSS resource. The supported values are:
- `zpn_trans_log`: Denotes the [User Activity](/zpa/about-user-activity-log-fields) log type.
- `zpn_auth_log`: Denotes the [User Status](/zpa/about-user-status-log-fields) log type.
- `zpn_ast_auth_log`: Denotes the [App Connector Status](/zpa/about-connector-status-log-fields) log type.
- `zpn_http_trans_log`: Denotes the [Browser Access](/zpa/about-browser-access-log-fields) log type.
- `zpn_audit_log`: Denotes the [Audit Log](/zpa/about-audit-log-fields) log type.
- `zpn_sys_auth_log`: Denotes the [Private Service Edge Status](/zpa/about-private-service-edge-status-log-fields) log type.
- `zpn_ast_comprehensive_stats`: Denotes the [App Connector Metrics](/zpa/about-app-connector-metrics-log-fields) log type.
- `zpn_waf_http_exchanges_log`: Denotes the [AppProtection](/zpa/about-appprotection-log-fields) log type.
- `zpn_smb_inspection_log`: Denotes the SMB Inspection log type.
- `zpn_ldap_inspection_log`: Denotes the LDAP Inspection log type.
- `zpn_krb_inspection_log`: Denotes the KRB Inspection log type.
- `zpn_pbroker_comprehensive_stats`: Denotes the [Private Service Edge Metrics](/zpa/about-private-service-edge-metrics-log-fields) log type.
- `zpn_sitec_auth_log`: Denotes the [Private Cloud Controller Status](/zpa/understanding-private-cloud-controller-status-log-fields) log type.
- `zpn_sitec_comprehensive_stats`: Denotes the [Private Cloud Controller Metrics](/zpa/understanding-private-cloud-controller-metrics-log-fields) log type.
- `zms_flow_log`: Denotes the [Microsegmentation Flow Logs](/zpa/about-microsegmentation-flow-log-fields) log type.
- [View the JSON payload](#ViewJSON)
[]{
"config":{
"name":"<Name of LSS Config>",
"description":"<Description of LSS Config>",
"format":"<Format of LSS Config>",
"lssHost":"<LSS Host>",
"lssPort":"<LSS Port>",
"enabled":<LSS Enabled>,
"filter":[
"<Success Code of LSS Config>"
],
"useTls":"<Use TLS>",
"sourceLogType":"<Log Type>"
},
"appConnectorGroups":[
{
"id":"<App Connector Group Id>"
}
],
"policyRuleResource":{
"conditions":[
{
"operands":[
{
"objectType":"<Type of Object>",
"values":[
"<Object IDs>"
]
},
{
"objectType":"<Type of Object>",
"values":[
"<Object IDs>"
]
}
]
}
]
}
}
- [View the sample JSON payload](#ViewSampleJSON)
[]{
"config":{
"name":"Test_Lss1",
"description":"Test_Lss1",
"enabled":true,
"format":"%s{LogTimestamp:time} User Activity zpa-lss: ,%s{Customer},%s{SessionID},%s{ConnectionID},%s{InternalReason},%s{ConnectionStatus},%d{IPProtocol},%d{DoubleEncryption},%s{Username},%d{ServicePort},%s{ClientPublicIP},%s{ClientPrivateIP},%f{ClientLatitude},%f{ClientLongitude},%s{ClientCountryCode},%s{ClientZEN},%s{Policy},%s{Connector},%s{ConnectorZEN},%s{ConnectorIP},%d{ConnectorPort},%s{Host},%s{Application},%s{AppGroup},%s{Server},%s{ServerIP},%d{ServerPort},%d{PolicyProcessingTime},%d{ServerSetupTime},%s{TimestampConnectionStart:iso8601},%s{TimestampConnectionEnd:iso8601},%s{TimestampCATx:iso8601},%s{TimestampCARx:iso8601},%s{TimestampAppLearnStart:iso8601},%s{TimestampZENFirstRxClient:iso8601},%s{TimestampZENFirstTxClient:iso8601},%s{TimestampZENLastRxClient:iso8601},%s{TimestampZENLastTxClient:iso8601},%s{TimestampConnectorZENSetupComplete:iso8601},%s{TimestampZENFirstRxConnector:iso8601},%s{TimestampZENFirstTxConnector:iso8601},%s{TimestampZENLastRxConnector:iso8601},%s{TimestampZENLastTxConnector:iso8601},%d{ZENTotalBytesRxClient},%d{ZENBytesRxClient},%d{ZENTotalBytesTxClient},%d{ZENBytesTxClient},%d{ZENTotalBytesRxConnector},%d{ZENBytesRxConnector},%d{ZENTotalBytesTxConnector},%d{ZENBytesTxConnector},%s{Idp},%s{c2c}\\n",
"lssHost":"10.1.1.5",
"lssPort":"8081",
"filter":[
],
"useTls":false,
"sourceLogType":"zpn_trans_log",
"logFormat":"csv"
},
"connectorGroups":[
{
"id":"72057594038010497",
"name":"Abcdefg"
},
{
"id":"72057594038011105",
"name":"App_Connector_Test_1"
},
{
"id":"72057594038011108",
"name":"App_Connector_Test_3"
}
],
"policyRuleResource":{
"conditions":[
{
"operands":[
{
"objectType":"SAML",
"entryValues":[
{
"lhs":"72057594038060988",
"rhs":"123"
},
{
"lhs":"72057594038052744",
"rhs":"testEmail@123.com"
}
]
},
{
"objectType":"SCIM_GROUP",
"entryValues":[
{
"lhs":"72057594037961373",
"rhs":"20471"
},
{
"lhs":"72057594037961373",
"rhs":"20524"
}
]
},
{
"objectType":"SCIM",
"entryValues":[
{
"lhs":"72057594037988777",
"rhs":"Barbara"
},
{
"lhs":"72057594037988776",
"rhs":"Jensen"
}
]
}
],
"operator":"OR"
}
],
"name":"Lss selection rule for Test_Lss"
}
}
- [View an example response](#ViewExample)
[]{
"id": "72057594038062417",
"config": {
"id": "72057594038062417",
"creationTime": "1638941485",
"modifiedBy": "72057594038046610",
"name": "Test_Lss1",
"description": "Test_Lss1",
"enabled": true,
"sourceLogType": "zpn_trans_log",
"useTls": false,
"format": "%s{LogTimestamp:time} User Activity zpa-lss: ,%s{Customer},%s{SessionID},%s{ConnectionID},%s{InternalReason},%s{ConnectionStatus},%d{IPProtocol},%d{DoubleEncryption},%s{Username},%d{ServicePort},%s{ClientPublicIP},%s{ClientPrivateIP},%f{ClientLatitude},%f{ClientLongitude},%s{ClientCountryCode},%s{ClientZEN},%s{Policy},%s{Connector},%s{ConnectorZEN},%s{ConnectorIP},%d{ConnectorPort},%s{Host},%s{Application},%s{AppGroup},%s{Server},%s{ServerIP},%d{ServerPort},%d{PolicyProcessingTime},%d{ServerSetupTime},%s{TimestampConnectionStart:iso8601},%s{TimestampConnectionEnd:iso8601},%s{TimestampCATx:iso8601},%s{TimestampCARx:iso8601},%s{TimestampAppLearnStart:iso8601},%s{TimestampZENFirstRxClient:iso8601},%s{TimestampZENFirstTxClient:iso8601},%s{TimestampZENLastRxClient:iso8601},%s{TimestampZENLastTxClient:iso8601},%s{TimestampConnectorZENSetupComplete:iso8601},%s{TimestampZENFirstRxConnector:iso8601},%s{TimestampZENFirstTxConnector:iso8601},%s{TimestampZENLastRxConnector:iso8601},%s{TimestampZENLastTxConnector:iso8601},%d{ZENTotalBytesRxClient},%d{ZENBytesRxClient},%d{ZENTotalBytesTxClient},%d{ZENBytesTxClient},%d{ZENTotalBytesRxConnector},%d{ZENBytesRxConnector},%d{ZENTotalBytesTxConnector},%d{ZENBytesTxConnector},%s{Idp},%s{c2c}\\n",
"auditMessage": "{\"logType\":\"User Activity\",\"tcpPort\":\"8081\",\"appConnectorGroups\":[{\"name\":\"Abcdefg\",\"id\":\"72057594038010497\"},{\"name\":\"App_Connector_Test_1\",\"id\":\"72057594038011105\"},{\"name\":\"App_Connector_Test_3\",\"id\":\"72057594038011108\"}],\"domainOrIpAddress\":\"10.1.1.5\",\"logStreamContent\":\"%s{LogTimestamp:time} User Activity zpa-lss: ,%s{Customer},%s{SessionID},%s{ConnectionID},%s{InternalReason},%s{ConnectionStatus},%d{IPProtocol},%d{DoubleEncryption},%s{Username},%d{ServicePort},%s{ClientPublicIP},%s{ClientPrivateIP},%f{ClientLatitude},%f{ClientLongitude},%s{ClientCountryCode},%s{ClientZEN},%s{Policy},%s{Connector},%s{ConnectorZEN},%s{ConnectorIP},%d{ConnectorPort},%s{Host},%s{Application},%s{AppGroup},%s{Server},%s{ServerIP},%d{ServerPort},%d{PolicyProcessingTime},%d{ServerSetupTime},%s{TimestampConnectionStart:iso8601},%s{TimestampConnectionEnd:iso8601},%s{TimestampCATx:iso8601},%s{TimestampCARx:iso8601},%s{TimestampAppLearnStart:iso8601},%s{TimestampZENFirstRxClient:iso8601},%s{TimestampZENFirstTxClient:iso8601},%s{TimestampZENLastRxClient:iso8601},%s{TimestampZENLastTxClient:iso8601},%s{TimestampConnectorZENSetupComplete:iso8601},%s{TimestampZENFirstRxConnector:iso8601},%s{TimestampZENFirstTxConnector:iso8601},%s{TimestampZENLastRxConnector:iso8601},%s{TimestampZENLastTxConnector:iso8601},%d{ZENTotalBytesRxClient},%d{ZENBytesRxClient},%d{ZENTotalBytesTxClient},%d{ZENBytesTxClient},%d{ZENTotalBytesRxConnector},%d{ZENBytesRxConnector},%d{ZENTotalBytesTxConnector},%d{ZENBytesTxConnector},%s{Idp},%s{c2c}\\\\n\",\"name\":\"Test_Lss1\",\"description\":\"Test_Lss1\",\"sessionStatuses\":[],\"enabled\":true,\"useTls\":false,\"policy\":{\"policyType\":\"App Policy\",\"name\":\"Lss selection rule for Test_Lss\",\"conditions\":[{\"criteria\":[{\"id\":\"72057594038060988\",\"type\":\"SAML\",\"value\":\"123\"},{\"id\":\"72057594038052744\",\"type\":\"SAML\",\"value\":\"testEmail@123.com\"},{\"id\":\"72057594037961373\",\"type\":\"SCIM_GROUP\",\"value\":\"20471\"},{\"id\":\"72057594037961373\",\"type\":\"SCIM_GROUP\",\"value\":\"20524\"},{\"id\":\"72057594037988777\",\"type\":\"SCIM\",\"value\":\"Barbara\"},{\"id\":\"72057594037988776\",\"type\":\"SCIM\",\"value\":\"Jensen\"}],\"operator\":\"OR\"}]}}",
"lssHost": "10.1.1.5",
"lssPort": "8081"
},
"connectorGroups": [
{
"id": "72057594038010497",
"name": "Abcdefg",
"lssAppConnectorGroup": false
},
{
"id": "72057594038011105",
"name": "App_Connector_Test_1",
"lssAppConnectorGroup": false
},
{
"id": "72057594038011108",
"name": "App_Connector_Test_3",
"lssAppConnectorGroup": false
}
],
"policyRule": {
"id": "72057594038062423",
"modifiedTime": "1638941486",
"creationTime": "1638941486",
"modifiedBy": "72057594038046610",
"name": "SIEM selection rule for Test_Lss1",
"ruleOrder": "64",
"priority": "1",
"policyType": "3",
"operator": "AND",
"actionId": "72057594038062417",
"conditions": [
{
"id": "4860132",
"modifiedTime": "1638941486",
"creationTime": "1638941486",
"modifiedBy": "72057594038046610",
"operator": "OR",
"negated": false,
"operands": [
{
"id": "4860133",
"creationTime": "1638941486",
"modifiedBy": "72057594038046610",
"objectType": "SAML",
"lhs": "72057594038060988",
"rhs": "123",
"name": "Example"
},
{
"id": "4860134",
"creationTime": "1638941486",
"modifiedBy": "72057594038046610",
"objectType": "SAML",
"lhs": "72057594038052744",
"rhs": "testEmail@123.com",
"name": "Email_test"
},
{
"id": "4860135",
"creationTime": "1638941486",
"modifiedBy": "72057594038046610",
"objectType": "SCIM_GROUP",
"lhs": "72057594037961373",
"rhs": "20471",
"name": "test"
},
{
"id": "4860136",
"creationTime": "1638941486",
"modifiedBy": "72057594038046610",
"objectType": "SCIM_GROUP",
"lhs": "72057594037961373",
"rhs": "20524",
"name": "test"
},
{
"id": "4860137",
"creationTime": "1638941486",
"modifiedBy": "72057594038046610",
"objectType": "SCIM",
"lhs": "72057594037988777",
"rhs": "Barbara",
"name": "name.givenName"
},
{
"id": "4860138",
"creationTime": "1638941486",
"modifiedBy": "72057594038046610",
"objectType": "SCIM",
"lhs": "72057594037988776",
"rhs": "Jensen",
"name": "name.familyName"
}
]
}
],
"action": "LOG",
"defaultRule": false
},
"policyRuleResource": {
"conditions": [
{
"negated": false,
"operands": [
{
"entryValues": [
{
"lhs": "72057594038060988",
"rhs": "123"
},
{
"lhs": "72057594038052744",
"rhs": "testEmail@123.com"
}
],
"objectType": "SAML"
},
{
"entryValues": [
{
"lhs": "72057594037961373",
"rhs": "20471"
},
{
"lhs": "72057594037961373",
"rhs": "20524"
}
],
"objectType": "SCIM_GROUP"
},
{
"entryValues": [
{
"lhs": "72057594037988777",
"rhs": "Barbara"
},
{
"lhs": "72057594037988776",
"rhs": "Jensen"
}
],
"objectType": "SCIM"
}
],
"operator": "OR"
}
],
"name": "Lss selection rule for Test_Lss",
"operator": "AND",
"policyType": "0"
}
}
A successful response returns code 201, meaning the LSS configuration is created. To learn more, see [API Response Codes and Error Messages](/zpa/api-response-codes-and-error-messages).
You choose the LSS configuration criteria you want to include in the JSON payload. Refer to the [Adding Field Descriptions](#AddingFieldDescriptions) section for supported values.
[]Adding Field Descriptions
The following table includes available fields you can use for the LSS configuration API use cases:
[](#GettingLSSLogFormats)[](#GettingLSSStatusCodes)
- [](/zpa/about-user-activity-log-fields)
- [](/zpa/about-user-status-log-fields)
- [](/zpa/about-connector-status-log-fields)
- [](/zpa/about-browser-access-log-fields)
- [](/zpa/about-audit-log-fields)
- [](/zpa/about-private-service-edge-status-log-fields)
- [](/zpa/about-app-connector-metrics-log-fields)
- [](/zpa/about-appprotection-log-fields)
-
-
-
- [](/zpa/about-private-service-edge-metrics-log-fields)
- [](/zpa/understanding-private-cloud-controller-status-log-fields)
- [](/zpa/understanding-private-cloud-controller-metrics-log-fields)
- [](/zpa/about-microsegmentation-flow-log-fields)
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
| Field | Description | Required | Value |
| ----- | ----------- | -------- | ----- |
| config.name | The name of the LSS configuration | Yes | String |
| config.description | The description of the LSS configuration | No | String |
| config.enabled | Whether this LSS configuration is enabled or not | No | Default: `true`Supported values: `true`, `false` |
| config.format | The format of the log type | Yes | The format given by the following API to get formats: `/mgmtconfig/v2/admin/lssConfig/logType/formats`. To learn more, see the Getting Details of All LSS Log Formats section. |
| config.lssPort | The port of the LSS configuration | Yes | String |
| config.lssHost | The host of the LSS configuration | Yes | String |
| config.filter | The filter for the LSS configuration | Yes | The format given by the following API to get status codes: `/mgmtconfig/v2/admin/lssConfig/statusCodes`. To learn more, see the Getting Details of All LSS Status Codes section. |
| config.useTls | Whether TLS is enabled or not | Yes | Default: `false`Supported values: `true`, `false` |
| config.sourceLogType | The log type of the LSS configuration | Yes | Supported log type values:`zpn_trans_log`: Denotes the User Activity log type.`zpn_auth_log`: Denotes the User Status log type.`zpn_ast_auth_log`: Denotes the App Connector Status log type.`zpn_http_trans_log`: Denotes the Browser Access log type.`zpn_audit_log`: Denotes the Audit Log log type.`zpn_sys_auth_log`: Denotes the Private Service Edge Status log type.`zpn_ast_comprehensive_stats`: Denotes the App Connector Metrics log type.`zpn_waf_http_exchanges_log`: Denotes the AppProtection log type.`zpn_smb_inspection_log`: Denotes the SMB Inspection log type.`zpn_ldap_inspection_log`: Denotes the LDAP Inspection log type.`zpn_krb_inspection_log`: Denotes the KRB Inspection log type.`zpn_pbroker_comprehensive_stats`: Denotes the Private Service Edge Metrics log type.`zpn_sitec_auth_log`: Denotes the Private Cloud Controller Status log type.`zpn_sitec_comprehensive_stats`: Denotes the Private Cloud Controller Metrics log type.`zms_flow_log`: Denotes the Microsegmentation Flow Logs log type. |
| appConnectorGroups | The App Connector groups to be added to the LSS configuration | No | Any long value in the App Connector Group IDs |
| policyRuleResource.objectType | The object type of the rule | No | Supported values:`APP``APP_GROUP``BRANCH_CONNECTOR_GROUP``CLIENT_TYPE``CONSOLE``COUNTRY_CODE``EDGE_CONNECTOR_GROUP` (i.e., Cloud Connector group)`IDP``LOCATION``MACHINE_GROUP``PLATFORM``POSTURE``PRIVILEGED_PORTAL``RISK_FACTOR_TYPE``SAML``SCIM``SCIM_GROUP``TRUSTED_NETWORK``USER``USER_GROUP``USER_PORTAL``WORKLOAD_TAG_GROUP` |
[]Getting Details of All LSS Client Types
To get details of all client types:
- Send a `GET` request to the following endpoint: `/mgmtconfig/v2/admin/lssConfig/customers/{customerId}/clientTypes`.
- Provide the `customerId`, the ZPA tenant ID of the customer, in the request endpoint. For example: `/mgmtconfig/v2/admin/lssConfig/customers/217246660302995456/clientTypes`.
- [View an example response](#exampleResponseClientTypes)
[]{
"zpn_client_type_exporter":"Web Browser",
"zpn_client_type_exporter_noauth":"Web Browser Unauthenticated",
"zpn_client_type_machine_tunnel":"Machine Tunnel",
"zpn_client_type_edge_connector":"Cloud Connector",
"zpn_client_type_zia_inspection":"ZIA Inspection",
"zpn_client_type_zapp":"Client Connector",
"zpn_client_type_slogger":"ZPA LSS",
"zpn_client_type_browser_isolation":"Cloud Browser",
"zpn_client_type_ip_anchoring":"ZIA Service Edge",
"zpn_client_type_zapp_partner":"Client Connector Partner",
"zpn_client_type_branch_connector":"Branch Connector",
"zpn_client_type_vdi":"Client Connector for VDI",
"zpn_client_type_simple_zsdk": "ZSDK Pre Login Tunnel",
"zpn_client_type_zsdk": "ZSDK Zero Trust Tunnel"
}
A successful response returns code 200. To learn more, see [API Response Codes and Error Messages](/zpa/api-response-codes-and-error-messages).
Updating a LSS Attribute
To update a LSS attribute:
- Provide the updated JSON payload from [Creating a New LSS Configuration](#CreatingLSS).
- Send a `PUT` request to the following endpoint: `/mgmtconfig/v2/admin/customers/{customerId}/lssConfig/{lssId}.`
- Provide the following in the request endpoint:
- `customerId`: The ZPA tenant ID of the customer.
- `lssId`: The unique identifier of the LSS resource.
For example: `/mgmtconfig/v2/admin/customers/217246660302995456/lssConfig/217246660303023855`.
- [View the JSON payload](#ViewJSON2)
[]{
"config":{
"name":"<Name of LSS Config>",
"description":"<Description of LSS Config>",
"format":"<Format of LSS Config>",
"lssHost":"<LSS Host>",
"lssPort":"<LSS Port>",
"enabled":<LSS Enabled>,
"filter":[
"<Success Code of LSS Config>"
],
"useTls":"<Use TLS>",
"sourceLogType":"<Log Type >"
},
"appConnectorGroups":[
{
"id":"<App Connector Group Id>"
}
],
"policyRuleResource":{
"conditions":[
{
"operands":[
{
"objectType":"<Type of Object>",
"values":[
"<Object IDs>"
]
},
{
"objectType":"<Type of Object>",
"values":[
"<Object IDs>"
]
}
]
}
]
}
}
A successful response returns code 204, meaning the LSS attribute is updated. To learn more, see [API Response Codes and Error Messages](/zpa/api-response-codes-and-error-messages).
If an LSS attribute is configured using Zscaler Deception, then the update and delete options are unavailable.
Deleting a LSS Attribute
To delete a LSS attribute:
- Send a `DELETE` request to the following endpoint: `/mgmtconfig/v2/admin/customers/{customerId}/lssConfig/{lssId}`.
- Provide the following in the request endpoint:
- `customerId`: The ZPA tenant ID of the customer.
- `lssId`: The unique identifier of the LSS resource.
For example: `/mgmtconfig/v2/admin/customers/{217246660302995456/lssConfig/217246660303025321`.
A successful response yields code 204, meaning the LSS attribute is deleted. To learn more, see [API Response Codes and Error Messages](/zpa/api-response-codes-and-error-messages).
If an LSS attribute is configured using Zscaler Deception, then the update and delete options are unavailable.