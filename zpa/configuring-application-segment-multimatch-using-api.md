# Configuring Application Segment Multimatch Using API
Source: https://help.zscaler.com/zpa/configuring-application-segment-multimatch-using-api
PDF: https://help.zscaler.com/pdf/com/en/1531143.pdf

This article provides information for managing application segment multimatch using APIs. All APIs are rate limited. To learn more, see [Using Application Segment Multimatch](/zpa/using-app-segment-multimatch) and [Understanding Rate Limiting](/zpa/understanding-rate-limiting).
Getting Application Segments by Domain That Are Incompatible with Application Segment Multimatch
To get application segments by domain that are incompatible with application segment Multimatch:
- Send a `POST` request to the following endpoint: `/customers/{customerId}/application/multimatchUnsupportedReferences`.
- Provide the `customerId`, the ZPA tenant ID of the customer, in the request endpoint. For example: `/customers/144118148382064640/application/multimatchUnsupportedReferences`.
- Include the request headers to provide information about the request context:
- Content-Type: `application/json`
- Authorization: `Bearer <access_token>`
- Use the following JSON payload and provide the domains for the application segments.
- [View the JSON payload](#getIncompatibleAppSegmentsJson)
[]
`[
"<domain>",
"<domain>"
]`
- [View an example JSON file](#getIncompatibleAppSegmentsExampleJson)
[]
`[
"app.example.com",
"legacy-app.internal.corp"
]`
- [View an example response](#getIncompatibleAppSegmentsExampleResponse)
[]
`[
{
"id":"216903833601306634",
"appSegmentName":"Corp App",
"domains":[
"app.example.com"
],
"matchStyle":"EXCLUSIVE",
"tcpPorts":[
8080,
8080
],
"udpPorts":[
],
"scopeId":null,
"scopeName":null,
"unsupportedFeatures":[
]
},
{
"id":"216903833601306645",
"appSegmentName":"Legacy App",
"domains":[
"legacy-app.internal.corp"
],
"matchStyle":"EXCLUSIVE",
"tcpPorts":[
443,
443
],
"udpPorts":[
],
"scopeId":null,
"scopeName":null,
"unsupportedFeatures":[
"BROWSER_ACCESS",
"Double Encryption"
]
}
]`
An unsuccessful response returns error code 400 if all or none of the domains of the application segment are not provided. For example, the following error code is returned if all or none of the domains of the application segment are not provided:
`{
"message":"Domain(s) are not provided for checking multimatch unsupported features"
}`
A successful response returns code 200. To learn more, see [API Response Codes and Error Messages](/zpa/api-response-codes-and-error-messages).
Bulk Updating Application Segment Multimatch for Applications
To bulk update (i.e., enable or disable) application segment Multimatch for a list of application segments:
- Send a `PUT` request to the following endpoint: `/customers/{customerId}/application/bulkUpdateMultiMatch`.
- Provide the `customerId`, the ZPA tenant ID, in the request endpoint. For example: `/customers/144118148382064640/application/bulkUpdateMultiMatch`.
- Include the request headers to provide information about the request context:
- Content-Type: `application/json`
- Authorization: `Bearer <access_token>`
- Use the following JSON payload and provide the following information for the application segments:
- `matchStyle`: Indicates if Multimatch is enabled for the application segment. If enabled (`INCLUSIVE`), the request allows traffic to match multiple applications. If disabled (`EXCLUSIVE`), the request allows traffic to match a single application. A domain can only be `INCLUSIVE` or `EXCLUSIVE`, and any application segment can only contain inclusive or exclusive domains. To learn more, see [Using Application Segment Multimatch](/zpa/using-app-segment-multimatch) and [Configuring Defined Application Segments](/zpa/configuring-application-segments).
- `applicationIds`: The IDs of the application segments. To learn more, see [Configuring Application Segments Using API](/zpa/configuring-application-segments-using-api).
- [View the JSON file](#BulkUpdateJson)
[]
`{
"applicationIds":[
<application segment ID>,
<application segment ID>
],
"matchStyle":"INCLUSIVE"
}`
- [View the example JSON file](#bulkUpdateExampleJson)
[]
`{
"applicationIds":[
216903833601306634,
216903833601306635
],
"matchStyle":"INCLUSIVE"
}`
If `matchStyle` is set to `INCLUSIVE` and the application segment has features that are unsupported for Multimatch, then the following error code 400 (i.e., bad request) is returned:
`{
"code": "features.not.supported.for.multimatch",
"message": "The following features [BROWSER_ACCESS] are not supported for multimatch in application segment Legacy App"
}`
Multimatch must be disabled if the configuration contains applications using the Access Type of Browser Access, AppProtection, or Privileged Remote Access. Additionally, Multimatch must be disabled if the configuration contains applications using Double Encryption, Inspect Traffic with ZIA, and Source IP Anchor. To learn more, see [Using Application Segment Multimatch](/zpa/using-app-segment-multimatch).
If all of the application segment IDs that share the same domain are not provided, the following error code 400 is returned:
`{
"code":"multimatch.inconsistent.missing.apps",
"message":"The following application(s) are missing from the request but are required for the update: [216903833601306650]"
}`
A successful response returns code 204, meaning the bulk update operation is successful. To learn more, see [API Response Codes and Error Messages](/zpa/api-response-codes-and-error-messages).