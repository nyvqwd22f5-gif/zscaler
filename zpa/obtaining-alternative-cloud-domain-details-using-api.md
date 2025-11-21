# Obtaining Alternative Cloud Domain Details Using API
Source: https://help.zscaler.com/zpa/obtaining-alternative-cloud-domain-details-using-api
PDF: https://help.zscaler.com/pdf/com/en/1485756.pdf

This article provides information for getting alternative cloud domain details using APIs. All APIs are rate limited. To learn more, see [Understanding Rate Limiting](/zpa/understanding-rate-limiting).
To get all alternative cloud domain details for the Zscaler cloud, send a `GET` request to the following endpoint in the Zscaler Path Cloud Controller: `/mgmtconfig/v1/admin/zpathCloud/getAltClouds`.
The following is an example response:
[
"TestCloud.com",
"TestCloud2.com"
]
A successful response returns code 200. To learn more, see [API Response Codes and Error Messages](/zpa/api-response-codes-and-error-messages).