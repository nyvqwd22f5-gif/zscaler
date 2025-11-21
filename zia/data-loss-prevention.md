# Data Loss Prevention
Source: https://help.zscaler.com/zia/data-loss-prevention

API Reference Guide for the ZIA Cloud Service and Sandbox Submission APIs

**Base URL:** https://zsapi.[zscaler-cloud-name]/api/v1

## `GET /dlpDictionaries`

Gets information on all custom and predefined DLP dictionaries.

**Tags:** Data Loss Prevention
**Consumes:** application/json
**Produces:** application/json

| Name | In | Type | Required | Description |
| ---- | --- | ---- | -------- | ----------- |
| search | query | string | No | The search string used to match against a DLP dictionary's name or description attributes. |

| Code | Description | Schema |
| ---- | ----------- | ------ |
| 200 | Successful Operation | array[DlpDictionaryDom] |

## `POST /dlpDictionaries`

Adds a new custom DLP dictionary.

**Tags:** Data Loss Prevention
**Consumes:** application/json
**Produces:** application/json

| Name | In | Type | Required | Description |
| ---- | --- | ---- | -------- | ----------- |
| dlpdictionary | body | DlpDictionaryDom | No | The information for a custom DLP Dictionary that uses Patterns and Phrases, Exact Data Match (EDM), or Indexed Document Match (IDM). To learn more, see [Adding Custom DLP Dictionaries](/zia/adding-custom-dlp-dictionary). |

| Code | Description | Schema |
| ---- | ----------- | ------ |
| 200 | Successful Operation | DlpDictionaryDom |

## `GET /dlpDictionaries/lite`

Gets a name and ID dictionary of all custom and predefined DLP dictionaries.

**Tags:** Data Loss Prevention
**Consumes:** application/json
**Produces:** application/json
No parameters.

| Code | Description | Schema |
| ---- | ----------- | ------ |
| 200 | Successful Operation | array[DlpDictionaryDom] |

## `POST /dlpDictionaries/validateDlpPattern`

Validates the pattern used by a Pattern and Phrases DLP dictionary type, and provides error information if the pattern is invalid. To learn more about how to define valid patterns for custom DLP dictionaries, see [Defining Patterns for Custom DLP Dictionaries](/zia/defining-patterns-custom-dictionaries).

**Tags:** Data Loss Prevention
**Consumes:** application/json
**Produces:** application/json
No parameters.

| Code | Description | Schema |
| ---- | ----------- | ------ |
| 200 | Successful Operation | SMMsgStatusInfo |

## `GET /dlpDictionaries/{dictId}/predefinedIdentifiers`

Retrieves the list of identifiers that are available for selection in the specified hierarchical DLP dictionary. This information can be obtained for predefined hierarchical dictionaries such as the Driver’s License (United States), Passport Number (European Union), and Credentials and Secrets dictionaries and their clones.
Each identifier represents a sub-dictionary that consists of specific patterns. The Driver’s License (United States) dictionary includes one sub-dictionary for each state in the United States and the District of Columbia. For example, the Driver's License (United States) dictionary includes one sub-dictionary for each state in the United States, and you can customize this dictionary to detect the driver's licenses issued by specific states (e.g., California, New York, and Texas) by selecting the respective sub-dictionary identifier.
To learn more about hierarchical dictionaries, see [Understanding Predefined DLP Dictionaries](/zia/understanding-predefined-dlp-dictionaries).

**Tags:** Data Loss Prevention
**Produces:** application/json

| Name | In | Type | Required | Description |
| ---- | --- | ---- | -------- | ----------- |
| dictId | path | integer | Yes | The ID of the hierarchical DLP dictionary |

| Code | Description | Schema |
| ---- | ----------- | ------ |
| 200 | Successful Operation | array[string] |

## `DELETE /dlpDictionaries/{dlpDictId}`

Deletes a custom DLP dictionary. You cannot delete predefined DLP dictionaries.

**Tags:** Data Loss Prevention
**Consumes:** application/json
**Produces:** application/json

| Name | In | Type | Required | Description |
| ---- | --- | ---- | -------- | ----------- |
| dlpDictId | path | integer | Yes | The unique identifier for the DLP dictionary. |

| Code | Description | Schema |
| ---- | ----------- | ------ |
| default | Successful Operation |  |

## `GET /dlpDictionaries/{dlpDictId}`

Gets DLP dictionary information for the specified ID.

**Tags:** Data Loss Prevention
**Consumes:** application/json
**Produces:** application/json

| Name | In | Type | Required | Description |
| ---- | --- | ---- | -------- | ----------- |
| dlpDictId | path | integer | Yes | The unique identifier for the DLP dictionary. |

| Code | Description | Schema |
| ---- | ----------- | ------ |
| 200 | Successful Operation | DlpDictionaryDom |

## `PUT /dlpDictionaries/{dlpDictId}`

Updates a custom or predefined DLP dictionary.

**Tags:** Data Loss Prevention
**Consumes:** application/json
**Produces:** application/json

| Name | In | Type | Required | Description |
| ---- | --- | ---- | -------- | ----------- |
| dlpDictId | path | integer | Yes | The unique identifier for the DLP dictionary. |
| dlpdictionary | body | DlpDictionaryDom | No | The information for a custom or predefined DLP Dictionary that uses Patterns and Phrases, Exact Data Match (EDM), or Indexed Document Match (IDM). To learn more, see [Editing Predefined DLP Dictionaries](/zia/editing-predefined-dlp-dictionaries), and [Adding Custom DLP Dictionaries](/zia/adding-custom-dlp-dictionary) which provides more information regarding defining phrases and patterns, as well as EDM fields and IDM accuracy. |

| Code | Description | Schema |
| ---- | ----------- | ------ |
| 200 | Successful Operation | DlpDictionaryDom |

## `GET /dlpEngines`

Get a list of DLP engines.

**Tags:** Data Loss Prevention
**Consumes:** application/json
**Produces:** application/json
No parameters.

| Code | Description | Schema |
| ---- | ----------- | ------ |
| 200 | Successful Operation | array[DlpEngineDom] |

## `POST /dlpEngines`

Adds a new custom DLP engine. A DLP engine is a collection of one or more [DLP Dictionaries](/zia/about-dlp-dictionaries), combined using logical operators. DLP engines can be used in DLP policies to detect specific content in the users' traffic. The Zscaler service provides predefined DLP engines and supports custom DLP engines. To learn more, see [About DLP Engines](/zia/about-dlp-engines) and [Understanding DLP Engines](/zia/understanding-dlp-engines).
**Note**: To enable `/dlpEngines` endpoints that use POST, PUT, and DELETE methods for your organization, contact Zscaler Support.

**Tags:** Data Loss Prevention
**Consumes:** application/json
**Produces:** application/json

| Name | In | Type | Required | Description |
| ---- | --- | ---- | -------- | ----------- |
| body | body | DlpEngineDom | No | Details of a custom DLP engine formed by combining DLP dictionaries using logical operators. To learn how to add custom DLP engines, see [Adding Custom DLP Engines](/zia/adding-custom-dlp-engine). |

| Code | Description | Schema |
| ---- | ----------- | ------ |
| 200 | Successful Operation | DlpEngineDom |

## `GET /dlpEngines/lite`

Gets a name and ID dictionary for all DLP engines.

**Tags:** Data Loss Prevention
**Consumes:** application/json
**Produces:** application/json
No parameters.

| Code | Description | Schema |
| ---- | ----------- | ------ |
| 200 | Successful Operation | array[DlpEngineDom] |

## `POST /dlpEngines/validateDlpExpr`

Validates the logical expression within a DLP engine that is formed by combining DLP dictionaries and provides error information if the expression is invalid. To learn more about DLP engine expressions, see [Understanding DLP Engines](/zia/understanding-dlp-engines).
**Note**: To enable `/dlpEngines` endpoints that use POST, PUT, and DELETE methods for your organization, contact Zscaler Support.

**Tags:** Data Loss Prevention
**Consumes:** application/json
**Produces:** application/json

| Name | In | Type | Required | Description |
| ---- | --- | ---- | -------- | ----------- |
| body | body | string | No | Logical expression within a DLP engine formed by combining DLP dictionaries using operators. This parameter requires the input in a certain format. For example, an expression combining ABA Bank Routing Numbers and Credit Cards dictionaries using an AND operator with zero match count each would be ((D63.S > 0) AND (D38.S > 0)), where 63 is the ID of the Credit Cards dictionary and 38 is the ID of the ABA Bank Routing Numbers dictionary. The dictionary ID is wrapped around by a prefix (D) and a suffix (.S).
Engine expression examples:
- `((D63.S > 1))`
- `((D63.S > 1) AND (D38.S > 0))`
- `((D63.S > 1) OR (D38.S > 0))`
- `(D63.S > 0) AND ( NOT ( (D61.S > 0) ) ) )`
- `(SUM(D63.S, D38.S) > 3)`
In the preceding examples, 63 represents the ID of the Credit Cards dictionary, 61 is the Financial Statements dictionary ID, and 38 is the ABA Bank Routing Numbers dictionary ID.
**Note**: Zscaler recommends validating DLP engine expressions by sending a POST request to `/dlpEngines/validateDlpExpr` before configuring a DLP engine. |

| Code | Description | Schema |
| ---- | ----------- | ------ |
| 200 | Successful Operation | DlpEngineExpValidationResponse |

## `DELETE /dlpEngines/{dlpEngineId}`

Deletes the custom DLP engine with the specified ID.
**Note**: To enable `/dlpEngines` endpoints that use POST, PUT, and DELETE methods for your organization, contact Zscaler Support.

**Tags:** Data Loss Prevention
**Consumes:** application/json
**Produces:** application/json

| Name | In | Type | Required | Description |
| ---- | --- | ---- | -------- | ----------- |
| dlpEngineId | path | integer | Yes | The unique identifier for the DLP engine. |

| Code | Description | Schema |
| ---- | ----------- | ------ |
| default | Successful Operation |  |

## `GET /dlpEngines/{dlpEngineId}`

Gets DLP engine information for the specified ID.

**Tags:** Data Loss Prevention
**Consumes:** application/json
**Produces:** application/json

| Name | In | Type | Required | Description |
| ---- | --- | ---- | -------- | ----------- |
| dlpEngineId | path | integer | Yes | The unique identifier for the DLP engine. |

| Code | Description | Schema |
| ---- | ----------- | ------ |
| 200 | Successful Operation | DlpEngineDom |

## `PUT /dlpEngines/{dlpEngineId}`

Updates DLP engine information for the specified ID. To learn more, see [About DLP Engines](/zia/about-dlp-engines) and [Editing Predefined DLP Engines](/zia/editing-predefined-dlp-engines).
**Note**: To enable `/dlpEngines` endpoints that use POST, PUT, and DELETE methods for your organization, contact Zscaler Support.

**Tags:** Data Loss Prevention
**Consumes:** application/json
**Produces:** application/json

| Name | In | Type | Required | Description |
| ---- | --- | ---- | -------- | ----------- |
| dlpEngineId | path | integer | Yes | The unique identifier for the DLP engine. |
| body | body | DlpEngineDom | No |  |

| Code | Description | Schema |
| ---- | ----------- | ------ |
| 200 | Successful Operation | DlpEngineDom |

## `GET /dlpExactDataMatchSchemas`

Exact Data Match (EDM) templates (or EDM schemas) allow the Zscaler service to identify a record from a structured data source that matches predefined criteria. Using the Index Tool, you can create an EDM template that allows you to define this criteria (i.e., define the tokens) for your data records by importing a CSV file. After the data is defined and submitted within the tool, you can then apply the EDM template to a custom DLP dictionary or engine. This endpoint gets the EDM templates for all Index Tools used by the organization. To learn more, see [About Exact Data Match](/zia/about-exact-data-match) and [About the Index Tool](/zia/about-index-tool).

**Tags:** Data Loss Prevention
**Consumes:** application/json
**Produces:** application/json
No parameters.

| Code | Description | Schema |
| ---- | ----------- | ------ |
| 200 | Successful Operation | array[AdvancedDataProtectionSchema] |

## `GET /dlpExactDataMatchSchemas/lite`

Gets a list of active EDM templates (or EDM schemas) and their criteria (or token details), only.

**Tags:** Data Loss Prevention
**Consumes:** application/json
**Produces:** application/json

| Name | In | Type | Required | Description |
| ---- | --- | ---- | -------- | ----------- |
| schemaName | query | string | No | The EDM schema name. |
| activeOnly | query | boolean | No | If set to true, only active EDM templates (or schemas) are returned in the response. |
| fetchTokens | query | boolean | No | If set to true, the criteria (i.e., token details) for the active templates are returned in the response. |

| Code | Description | Schema |
| ---- | ----------- | ------ |
| 200 | Successful Operation | array[AdvancedDataProtectionSchemaLite] |

## `GET /dlpNotificationTemplates`

Gets a list of DLP notification templates. To learn more, see [About DLP Notification Templates](/zia/about-dlp-notification-templates).

**Tags:** Data Loss Prevention
**Consumes:** application/json
**Produces:** application/json
No parameters.

| Code | Description | Schema |
| ---- | ----------- | ------ |
| 200 | Successful Operation | array[DlpNotificationTemplate] |

## `POST /dlpNotificationTemplates`

Adds a new DLP notification template. To learn more, see [Configuring DLP Notification Templates](/zia/configuring-dlp-notification-templates).

**Tags:** Data Loss Prevention
**Consumes:** application/json
**Produces:** application/json
No parameters.

| Code | Description | Schema |
| ---- | ----------- | ------ |
| 200 | Successful Operation | DlpNotificationTemplate |

## `DELETE /dlpNotificationTemplates/{templateId}`

Deletes a DLP notification template.

**Tags:** Data Loss Prevention
**Consumes:** application/json
**Produces:** application/json

| Name | In | Type | Required | Description |
| ---- | --- | ---- | -------- | ----------- |
| templateId | path | integer | Yes | The unique identifer for the DLP notification template. |

| Code | Description | Schema |
| ---- | ----------- | ------ |
| default | Successful Operation |  |

## `GET /dlpNotificationTemplates/{templateId}`

Gets DLP notification template information for the specified ID.

**Tags:** Data Loss Prevention
**Consumes:** application/json
**Produces:** application/json

| Name | In | Type | Required | Description |
| ---- | --- | ---- | -------- | ----------- |
| templateId | path | integer | Yes | The unique identifer for the DLP notification template. |

| Code | Description | Schema |
| ---- | ----------- | ------ |
| 200 | Successful Operation | DlpNotificationTemplate |

## `PUT /dlpNotificationTemplates/{templateId}`

Updates a DLP notification template.

**Tags:** Data Loss Prevention
**Consumes:** application/json
**Produces:** application/json

| Name | In | Type | Required | Description |
| ---- | --- | ---- | -------- | ----------- |
| templateId | path | integer | Yes | The unique identifer for the DLP notification template. |

| Code | Description | Schema |
| ---- | ----------- | ------ |
| 200 | Successful Operation | DlpNotificationTemplate |

## `GET /icapServers`

Gets a the list of DLP servers using ICAP. To learn more, see [About ICAP Communication Between Zscaler and DLP Servers](/zia/about-icap-communication-between-zscaler-and-dlp-servers), [Enabling Secure ICAP](/zia/enabling-secure-icap), and [Enabling Unencrypted ICAP](/zia/enabling-unencrypted-icap).

**Tags:** Data Loss Prevention
**Consumes:** application/json
**Produces:** application/json
No parameters.

| Code | Description | Schema |
| ---- | ----------- | ------ |
| 200 | Successful Operation | array[ICAPServer] |

## `GET /icapServers/lite`

Gets a name and ID dictionary for all DLP servers using ICAP.

**Tags:** Data Loss Prevention
**Consumes:** application/json
**Produces:** application/json
No parameters.

| Code | Description | Schema |
| ---- | ----------- | ------ |
| 200 | Successful Operation | array[ICAPServer] |

## `GET /icapServers/{icapServerId}`

Get DLP server (i.e., for servers using ICAP) information for the specified ID.

**Tags:** Data Loss Prevention
**Consumes:** application/json
**Produces:** application/json

| Name | In | Type | Required | Description |
| ---- | --- | ---- | -------- | ----------- |
| icapServerId | path | integer | Yes | The unique identifier for the DLP server using ICAP. |

| Code | Description | Schema |
| ---- | ----------- | ------ |
| 200 | Successful Operation | ICAPServer |

## `GET /idmprofile`

Indexed Document Match (IDM) templates (or IDM profiles) allow you to fingerprint your organization’s critical documents that contain sensitive data. By fingerprinting and indexing your documents, you can create a document repository that the Zscaler service can use to identify completely or partially matching documents when evaluating outbound traffic against a DLP policy. Using the Index Tool, you can create an IDM template that allows you to upload and fingerprint your documents. After  you create an IDM template, you can then apply it to a custom DLP dictionary. This endpoint gets all of the IDM templates for all Index Tools used by the organization. To learn more, see [About Indexed Document Match](/zia/about-indexed-document-match) and [About the Index Tool](/zia/about-index-tool).

**Tags:** Data Loss Prevention
**Consumes:** application/json
**Produces:** application/json
No parameters.

| Code | Description | Schema |
| ---- | ----------- | ------ |
| 200 | Successful Operation | array[IdmProfile] |

## `GET /idmprofile/lite`

-> Gets a list of active IDM templates (or IDM profiles) and their criteria, only.

**Tags:** Data Loss Prevention
**Consumes:** application/json
**Produces:** application/json

| Name | In | Type | Required | Description |
| ---- | --- | ---- | -------- | ----------- |
| activeOnly | query | boolean | No | If set to true, only active IDM templates (or profiles) are returned in the response. |

| Code | Description | Schema |
| ---- | ----------- | ------ |
| 200 | Successful Operation | array[IdmProfileSummary] |

## `GET /idmprofile/{profileId}`

Get IDM template information for the specified ID.

**Tags:** Data Loss Prevention
**Consumes:** application/json
**Produces:** application/json

| Name | In | Type | Required | Description |
| ---- | --- | ---- | -------- | ----------- |
| profileId | path | integer | Yes | The unique identifier for the IDM template (or profile). |

| Code | Description | Schema |
| ---- | ----------- | ------ |
| 200 | Successful Operation | IdmProfile |

## `GET /incidentReceiverServers`

Gets a list of DLP Incident Receivers. To learn more, see [About Zscaler Incident Receiver](/zia/about-zscaler-incident-receiver).

**Tags:** Data Loss Prevention
**Consumes:** application/json
**Produces:** application/json
No parameters.

| Code | Description | Schema |
| ---- | ----------- | ------ |
| 200 | Successful Operation | array[IncidentReceiverServer] |

## `GET /incidentReceiverServers/lite`

Gets a name and ID dictionary for all DLP Incident Receivers.

**Tags:** Data Loss Prevention
**Consumes:** application/json
**Produces:** application/json
No parameters.

| Code | Description | Schema |
| ---- | ----------- | ------ |
| 200 | Successful Operation | array[IncidentReceiverServer] |

## `GET /incidentReceiverServers/{incidentReceiverServerId}`

Gets DLP Incident Receiver information for the specified ID.

**Tags:** Data Loss Prevention
**Consumes:** application/json
**Produces:** application/json

| Name | In | Type | Required | Description |
| ---- | --- | ---- | -------- | ----------- |
| incidentReceiverServerId | path | integer | Yes | The unique identifier for the Incident Receiver. |

| Code | Description | Schema |
| ---- | ----------- | ------ |
| 200 | Successful Operation | IncidentReceiverServer |

## `GET /webDlpRules`

Gets a list of DLP policy rules, excluding SaaS Security DLP policy rules. To learn more, see [Configuring DLP Policy Rules with Content Inspection](/zia/configuring-dlp-policy-rules-content-inspection#Rules) and [Configuring DLP Policy Rules without Content Inspection](/zia/configuring-dlp-policy-rules-without-content-inspection#Add).

**Tags:** Data Loss Prevention
**Consumes:** application/json
**Produces:** application/json
No parameters.

| Code | Description | Schema |
| ---- | ----------- | ------ |
| 200 | Successful Operation | array[WebDlpRule] |

## `POST /webDlpRules`

Adds a new DLP policy rule. To learn more, see [Configuring DLP Policy Rules with Content Inspection](/zia/configuring-dlp-policy-rules-content-inspection#Rules) and [Configuring DLP Policy Rules without Content Inspection](/zia/configuring-dlp-policy-rules-without-content-inspection#Add).

**Tags:** Data Loss Prevention
**Consumes:** application/json
**Produces:** application/json

| Name | In | Type | Required | Description |
| ---- | --- | ---- | -------- | ----------- |
| body | body | WebDlpRule | No | The DLP policy rule information. |

| Code | Description | Schema |
| ---- | ----------- | ------ |
| 200 | Successful Operation | WebDlpRule |

## `GET /webDlpRules/lite`

Gets name and ID dictionary for all DLP policy rules, excluding SaaS Security DLP policy rules.

**Tags:** Data Loss Prevention
**Consumes:** application/json
**Produces:** application/json
No parameters.

| Code | Description | Schema |
| ---- | ----------- | ------ |
| 200 | Successful Operation | array[WebDlpRule] |

## `DELETE /webDlpRules/{ruleId}`

Deletes a DLP policy rule. This endpoint is not applicable to SaaS Security API DLP policy rules.

**Tags:** Data Loss Prevention
**Consumes:** application/json
**Produces:** application/json

| Name | In | Type | Required | Description |
| ---- | --- | ---- | -------- | ----------- |
| ruleId | path | integer | Yes | The unique identifier for the DLP policy rule. |

| Code | Description | Schema |
| ---- | ----------- | ------ |
| default | Successful Operation |  |

## `GET /webDlpRules/{ruleId}`

Gets DLP policy rule information for the specified ID.

**Tags:** Data Loss Prevention
**Consumes:** application/json
**Produces:** application/json

| Name | In | Type | Required | Description |
| ---- | --- | ---- | -------- | ----------- |
| ruleId | path | integer | Yes | The unique identifier for the DLP policy rule. |

| Code | Description | Schema |
| ---- | ----------- | ------ |
| 200 | Successful Operation | WebDlpRule |

## `PUT /webDlpRules/{ruleId}`

Updates a DLP policy rule. This endpoint is not applicable to SaaS Security DLP policy rules.

**Tags:** Data Loss Prevention
**Consumes:** application/json
**Produces:** application/json

| Name | In | Type | Required | Description |
| ---- | --- | ---- | -------- | ----------- |
| ruleId | path | integer | Yes | The unique identifier for the DLP policy rule. |
| body | body | WebDlpRule | No | The DLP policy rule information. |

| Code | Description | Schema |
| ---- | ----------- | ------ |
| 200 | Successful Operation | WebDlpRule |

## Models
### AdvancedDataProtectionSchema
Exact Data Match (EDM) template (i.e., schema) information.
| Field | Type | Required | Description |
| ----- | ---- | -------- | ----------- |
| cellsUsed | integer (int64) | No | The total number of cells used by the EDM schema (i.e., EDM template). |
| createdBy | object | No | The login name (or userid) the admin who created the EDM schema (i.e., EDM template). Ignored if the request is PUT, POST, or DELETE. |
| edmClient | object | No | The unique identifer for the Index Tool that was used to create the EDM template. This attribute is ignored by PUT requests, but required for POST requests. |
| fileUploadStatus | string | No | The status of the EDM template's CSV file upload to the Index Tool. This attribute is required by PUT and POST requests. |
| filename | string | No | The generated filename, excluding the extention. |
| lastModifiedBy | object | No | The admin that modified the EDM template's schema last. |
| lastModifiedTime | integer (int32) | No | Timestamp when the EDM schema (i.e., EDM template) was last modified. Ignored if the request is PUT, POST, or DELETE. |
| origColCount | integer (int32) | No | The total count of actual columns selected from the CSV file. This attribute is required by PUT and POST requests. |
| originalFileName | string | No | The name of the CSV file uploaded to the Index Tool. This attribute is required by PUT and POST requests. |
| projectName | string | No | The EDM schema (i.e., EDM template) name. This attribute is ignored by PUT requests, but required for POST requests. |
| revision | integer (int32) | No | The revision number of the CSV file upload to the Index Tool. This attribute is required by PUT requests. |
| schedule | object | No | The schedule details, if present for the EDM schema (i.e., EDM template). Ignored if the request is PUT, POST, or DELETE. |
| schedulePresent | boolean | No | Indicates whether the EDM schema (i.e., the EDM template configured using the Index Tool) has a schedule. |
| schemaActive | boolean | No | Indicates the status of a specified EDM schema (i.e., EDM template). If this value is set to true, the schema is active and can be used by DLP dictionaries. |
| schemaId | integer (int32) | No | The identifier (1-65519) for the EDM schema (i.e., EDM template) that is unique within the organization. |
| tokenList | array[AdvancedDataProtectionSchemaToken] | No | The list of tokens (or criteria) to match against. Up to 16 tokens can be selected for data matching. This attribute is required by PUT and POST requests. |

### AdvancedDataProtectionSchemaLite
Exact Data Match (EDM) template (i.e., schema) information retrieved by /dlpExactDataMatchSchemas/lite.
| Field | Type | Required | Description |
| ----- | ---- | -------- | ----------- |
| schema | object | No | The identifier (1-65519) for the EDM schema (i.e., EDM template) that is unique within the organization. |
| tokens | array[AdvancedDataProtectionSchemaToken] | No | The tokens (or criteria) used by the EDM schema (i.e., EDM template). |

### AdvancedDataProtectionSchemaSchedule
Exact Data Match (EDM) template (i.e., schema) schedule information.
| Field | Type | Required | Description |
| ----- | ---- | -------- | ----------- |
| scheduleDayOfMonth | array[string] | No | The day of the month the EDM schema (i.e., EDM template) is scheduled for. This attribute is required by PUT and POST requests, and if the scheduleType is set to MONTHLY. |
| scheduleDayOfWeek | array[string] | No | The day of the week the EDM schema (i.e., EDM template) is scheduled for. This attribute is required by PUT and POST requests, and if the scheduleType is set to WEEKLY. |
| scheduleDisabled | boolean | No | If set to true, the schedule for the EDM schema (i.e., EDM template) is temporarily in a  disabled state. This attribute is required by PUT requests in order to disable or enable a schedule. |
| scheduleTime | integer (int32) | No | The time of the day (in minutes) that the EDM schema (i.e., EDM template) is scheduled for. For example: at 3am= 180 mins. This attribute is required by PUT and POST requests. |
| scheduleType | string | No | The schedule type for the EDM schema (i.e., EDM template), Monthly, Weekly, Daily, or None. This attribute is required by PUT and POST requests. |

### AdvancedDataProtectionSchemaToken
Exact Data Match (EDM) template (i.e., schema) token (or criteria) information.
| Field | Type | Required | Description |
| ----- | ---- | -------- | ----------- |
| colLengthBitmap | integer (int64) | No | The length of the column bitmap in the hashed file. |
| hashfileColumnOrder | integer (int32) | No | The column position for the token in the hashed file, starting from 1. |
| name | string | No | The token (i.e., criteria) name. This attribute is required by PUT and POST requests. |
| originalColumn | integer (int32) | No | The column position for the token in the original CSV file uploaded to the Index Tool, starting from 1. This attribue required by PUT and POST requests. |
| primaryKey | boolean | No | Indicates whether the token is a primary key. |
| type | string | No | The token type. This attribute is required by PUT and POST requests. |

### AppSegment
Application Segment information
| Field | Type | Required | Description |
| ----- | ---- | -------- | ----------- |
| externalId | integer (int64) | No | Indicates the external ID. Applicable only when this reference is of an external entity. |
| id | integer (int32) | No | A unique identifier assigned to the Application Segment |
| name | string | No | The name of the Application Segment |
| zpaTenantId | integer (int64) | No | ID of the ZPA tenant where the Application Segment is configured |

### CloudApplicationInstanceLite
| Field | Type | Required | Description |
| ----- | ---- | -------- | ----------- |
| id | integer (int32) | No | The cloud application instance ID. |
| name | string | No | The cloud application instance name. |
| type | string | No | The instance of the cloud application selected from the available options. |

### DictionaryPatternActionString
DLP dictionary pattern and action
| Field | Type | Required | Description |
| ----- | ---- | -------- | ----------- |
| action | string | No | The action applied to a DLP dictionary using patterns |
| pattern | string | No | DLP dictionary pattern |

### DictionaryPhraseActionString
DLP dictionary phrase and action
| Field | Type | Required | Description |
| ----- | ---- | -------- | ----------- |
| action | string | No | The action applied to a DLP dictionary using phrases |
| phrase | string | No | DLP dictionary phrase |

### DlpDictionaryDom
A DLP dictionary contains a set of patented algorithms that are designed to detect specific kinds of information in user traffic. For a list of and information on all predefined dictionaries, see [About DLP Dictionaries](/zia/about-dlp-dictionaries).
You can modify predefined DLP dictionaries or create custom dictionaries for content that is not properly covered by them. For example, using the cloud service API, you can create custom DLP dictionaries that trigger based on specific patterns and phrases. To learn more, see [Adding Custom DLP Dictionaries](/zia/adding-custom-dlp-dictionary), [Defining Patterns for Custom DLP Dictionaries](/zia/defining-patterns-custom-dictionaries), and [Defining Phrases for Custom DLP Dictionaries](/zia/defining-phrases-custom-dictionaries). You can also create custom DLP dictionaries based on Exact Data Match (EDM) or Indexed Document Match (IDM). To learn more, see [About Exact Data Match](/zia/about-exact-data-match) and see [About Indexed Document Match](/zia/about-indexed-document-match).
| Field | Type | Required | Description |
| ----- | ---- | -------- | ----------- |
| binNumbers | array[integer (int32)] | No | The list of Bank Identification Number (BIN) values that are included or excluded from the Credit Cards dictionary. BIN values can be specified only for Diners Club, Mastercard, RuPay, and Visa cards. Up to 512 BIN values can be configured in a dictionary.
**Note**: This field is applicable only to the predefined Credit Cards dictionary and its clones. |
| confidenceThreshold | string | No | The DLP confidence threshold |
| custom | boolean | No | This value is set to true for custom DLP dictionaries. |
| customPhraseMatchType | string | No | The DLP custom phrase match type |
| customPhraseSupported | boolean | No | A Boolean constant that indicates that custom phrases are supported for the DLP dictionary using the true value. This field is applicable only to predefined DLP dictionaries with a [high confidence score threshold](/zia/editing-predefined-dlp-dictionaries#confidence). |
| description | string | No | The description of the DLP dictionary |
| dictTemplateId | integer (int32) | No | ID of the predefined dictionary (original *source* dictionary) that is used for cloning. This field is applicable only to cloned dictionaries. Only a limited set of identification-based predefined dictionaries (e.g., Credit Cards, Social Security Numbers, National Identification Numbers, etc.) can be cloned. Up to 4 clones can be created from a predefined dictionary. |
| dictionaryCloningEnabled | boolean | No | A Boolean constant that indicates that the cloning option is supported for the DLP dictionary using the true value. This field is applicable only to predefined DLP dictionaries. |
| dictionaryType | string | No | The DLP dictionary type. |
| exactDataMatchDetails | array[ExactDataMatchDetail] | No | Exact Data Match (EDM) related information for custom DLP dictionaries. To learn more about the schemaId, primaryField, and secondaryFields, see AdvancedDataProtectionSchemaLite model. This information is retrieved by the /dlpExactDataMatchSchemas/lite endpoint. |
| hierarchicalDictionary | boolean | No | A true value indicates that the DLP dictionary is of hierarchical type that includes sub-dictionaries. A false value indicates that the dictionary is not hierarchical. |
| hierarchicalIdentifiers | array[string] | No | The list of identifiers selected within a DLP dictionary of hierarchical type. Each identifier represents a sub-dictionary that consists of specific patterns. To retrieve the list of identifiers that are available for selection within a specific hierarchical dictionary, send a GET request to `/dlpDictionaries/{dictId}/predefinedIdentifiers`.
To learn about hierarchical dictionaries, see [Configuring the URL Filtering Policy](/zia/understanding-predefined-dlp-dictionaries).
**Note**: This field is applicable to predefined hierarchical dictionaries, such as the Driver’s License (United States), Passport Number (European Union), and Credentials and Secrets dictionaries or their clones. |
| id | integer (int32) | No | Unique identifier for the DLP dictionary |
| idmProfileMatchAccuracy | array[IdmProfileMatchAccuracyDetail] | No | List of Indexed Document Match (IDM) profiles and their corresponding match accuracy for custom DLP dictionaries. |
| ignoreExactMatchIdmDict | boolean | No | Indicates whether to exclude documents that are a 100% match to already-indexed documents from triggering an Indexed Document Match (IDM) Dictionary. |
| includeBinNumbers | boolean | No | A true value denotes that the specified Bank Identification Number (BIN) values are included in the Credit Cards dictionary. A false value denotes that the specified BIN values are excluded from the Credit Cards dictionary.
**Note**: This field is applicable only to the predefined Credit Cards dictionary and its clones. |
| includeSsnNumbers | boolean | No | A true value denotes that the Social Security numbers (SSNs) specified using the **ssnNumbers** field are included in the dictionary. A false value denotes that the specified SSNs are excluded from the dictionary.
**Note**: This field is applicable only to the predefined Social Security Numbers (US) dictionary and its clones. |
| name | string | No | The DLP dictionary's name |
| nameL10nTag | boolean | No | Indicates whether the name is localized or not. This is always set to True for predefined DLP dictionaries. |
| patterns | array[DictionaryPatternActionString] | No | List containing the patterns used within a custom DLP dictionary. This attribute is not applicable to predefined DLP dictionaries |
| phrases | array[DictionaryPhraseActionString] | No | List containing the phrases used within a custom DLP dictionary. This attribute is not applicable to predefined DLP dictionaries. |
| predefinedClone | boolean | No | This field is set to true if the dictionary is cloned from a predefined dictionary. Otherwise, it is set to false. |
| predefinedCountActionType | string | No | This field specifies whether duplicate matches of a phrase from a dictionary must be counted individually toward the match count or ignored, thereby maintaining a single count for multiple occurrences.
**Note**: This field is currently applicable only to the [predefined Names dictionaries](/zia/understanding-predefined-dlp-dictionaries), such as Names (US), Names (Canada), and Names (Spain). |
| proximity | integer (int32) | No | The DLP dictionary proximity length that defines how close a high confidence phrase must be to an instance of the pattern (that the dictionary detects) to count as a match.
** Note**: Proximity length is supported only for specific predefined DLP dictionaries with a [high confidence score threshold](/zia/editing-predefined-dlp-dictionaries#confidence) and custom DLP dictionaries configured with the **Match Any Patterns And Any Phrases** option. |
| proximityEnabledForCustomDictionary | boolean | No | A Boolean constant that indicates if proximity length is enabled or disabled for a custom DLP dictionary. A true value indicates that proximity length is enabled, whereas a false value indicates that it is disabled.
**Note**: This field is applicable only for specific custom DLP dictionaries configured with the **Match Any Patterns And Any Phrases** option. For predefined DLP dictionaries, this field value is always set to false. |
| proximityLengthEnabled | boolean | No | A Boolean constant that indicates whether the proximity length option is supported for a DLP dictionary or not. A true value indicates that the proximity length option is supported, whereas a false value indicates that it is not supported.
**Note**: Proximity length is supported only for specific predefined DLP dictionaries with a [high confidence score threshold](/zia/editing-predefined-dlp-dictionaries#confidence) and custom DLP dictionaries configured with the **Match Any Patterns And Any Phrases** option. |
| ssnNumbers | array[string] | No | The list of Social Security numbers (SSNs) that are included or excluded from the dictionary based on the value set for **includeSsnNumbers**. Up to 512 SSNs can be added to a dictionary.
**Note**: This field is applicable only to the predefined Social Security Numbers (US) dictionary and its clones. |
| thresholdType | string | No | DLP threshold type |

### DlpEngineDom
DLP engine information.
| Field | Type | Required | Description |
| ----- | ---- | -------- | ----------- |
| customDlpEngine | boolean | No | Indicates whether this is a custom DLP engine. If this value is set to true, the engine is custom. |
| description | string | No | The DLP engine's description. |
| engineExpression | string | No | The logical expression that defines a DLP engine by combining DLP dictionaries using logical operators, namely All (AND), Any (OR), Exclude (NOT), and Sum (the total number of content matches). To learn more about DLP engine expressions, see [Understanding DLP Engines](/zia/understanding-dlp-engines).
Engine expression examples:
- `((D63.S > 1))`
- `((D38.S > 1) AND (D63.S > 1))`
- `((D38.S > 1) OR (D63.S > 1))`
- `((D38.S > 0) AND ( NOT ( (D61.S > 0) ) )`
- `(SUM(D63.S, D38.S) > 3)`
In the preceding examples, 63 represents the ID of the Credit Cards dictionary ID, 61 is the Financial Statements ID, and 38 is the ABA Bank Routing Numbers dictionary ID. Each dictionary ID is wrapped around by a prefix (D) and a suffix (.S). |
| id | integer (int32) | No | The unique identifier for the DLP engine. |
| name | string | No | The DLP engine name as configured by the admin. This attribute is required in POST and PUT requests for custom DLP engines. |
| predefinedEngineName | string | No | The name of the predefined DLP engine. |

### DlpEngineExpValidationResponse
Error message information that is returned when a DLP engine expression is invalid.
| Field | Type | Required | Description |
| ----- | ---- | -------- | ----------- |
| errMsg | string | No | Error message from DLP engine expression validation |
| errParameter | string | No | Error parameter in the DLP engine expression |
| errSuggestion | string | No | Suggestion for error correction |
| status | string | No | DLP engine expression validation status |

### DlpNotificationTemplate
DLP notification template information.
| Field | Type | Required | Description |
| ----- | ---- | -------- | ----------- |
| attachContent | boolean | No | If set to true, the content that is violation is attached to the DLP notification email. |
| htmlMessage | string | Yes | The template for the HTML message body that must be displayed in the DLP notification email. |
| id | integer (int32) | No | The unique identifier for a DLP notification template. |
| name | string | Yes | The DLP notification template name. |
| plainTextMessage | string | Yes | The template for the plain text UTF-8 message body that must be displayed in the DLP notification email. |
| subject | string | Yes | The Subject line that is displayed within the DLP notification email. |

### EntityReference
This is an immutable reference to an entity that mainly consists of an ID and name
| Field | Type | Required | Description |
| ----- | ---- | -------- | ----------- |
| extensions | object | No | Additional information about the entity |
| externalId | string | No | An external identifier used for an entity that is managed outside of ZIA. Examples include `zpaServerGroup` and `zpaAppSegments`. This field is not applicable to ZIA-managed entities. |
| id | integer (int64) | No | A unique identifier for an entity |
| name | string | No | The configured name of the entity |

### ExactDataMatchDetail
Exact Data Match (EDM) details. The primaryField and secondaryFields in the exactDataMatchDetails object use integer values from the hashfileColumnOrder field. To use the values from hashfileColumnOrder in primaryField, the primaryKey in AdvancedDataProtectionSchemaToken must be set to true.
| Field | Type | Required | Description |
| ----- | ---- | -------- | ----------- |
| dictionaryEdmMappingId | integer (int32) | No | The unique identifier for the EDM mapping. |
| primaryField | integer (int32) | No | The EDM template's primary field. |
| schemaId | integer (int32) | No | The unique identifier for the EDM template (or schema). |
| secondaryFieldMatchOn | string | No | The EDM secondary field to match on. |
| secondaryFields | array[integer (int32)] | No | The EDM template's secondary fields. |

### ExpressionContainer
One or more tag types (and associated tags) combined using logical operators within a workload group
| Field | Type | Required | Description |
| ----- | ---- | -------- | ----------- |
| operator | string | No | The operator (either AND or OR) used to create logical relationships among tag types |
| tagContainer | TagContainer | No | Contains one or more tags and the logical operator used to combine the tags within a tag type |
| tagType | string | No | The tag type selected from a predefined list |

### ICAPServer
DLP server (i.e., servers using ICAP) information.
| Field | Type | Required | Description |
| ----- | ---- | -------- | ----------- |
| id | integer (int32) | No | The unique identifier for a DLP server. |
| name | string | Yes | The DLP server name. |
| status | string | Yes | The DLP server status |
| url | string | Yes | The DLP server URL. |

### IdmProfile
Indexed Document Match (IDM) template (or profile) information.
| Field | Type | Required | Description |
| ----- | ---- | -------- | ----------- |
| host | string | No | The fully qualified domain name (FQDN) of the IDM template's host machine. |
| idmClient | object | No | The unique identifer for the Index Tool that was used to create the IDM template. This attribute is required by POST requests, but ignored if provided in PUT requests. |
| lastModifiedTime | integer (int32) | No | The date and time the IDM template was last modified. |
| modifiedBy | object | No | The admin that modified the IDM template last. |
| numDocuments | integer (int32) | No | The number of documents associated to the IDM template. |
| port | integer (int32) | No | The port number of the IDM template's host machine. |
| profileDesc | string | No | The IDM template's description. |
| profileDirPath | string | No | The IDM template's directory file path, where all files are present. |
| profileId | integer (int32) | No | The identifier (1-64) for the IDM template (i.e.,  IDM profile) that is unique within the organization. |
| profileName | string | No | The IDM template name, which is unique per Index Tool. |
| profileType | string | No | The IDM template's type. |
| scheduleDay | integer (int32) | No | The day the IDM template is scheduled for. This attribute is required by PUT and POST requests. |
| scheduleDayOfMonth | array[string] | No | The day of the month that the IDM template is scheduled for. This attribute is required by PUT and POST requests, and when scheduleType is set to MONTHLY. |
| scheduleDayOfWeek | array[string] | No | The day of the week the IDM template is scheduled for. This attribute is required by  PUT and POST requests, and when scheduleType is set to WEEKLY. |
| scheduleDisabled | boolean | No | If set to true, the schedule for the IDM template is temporarily in a disabled state. This attribute is required by PUT requests in order to disable or enable a schedule. |
| scheduleTime | integer (int32) | No | The time of the day (in minutes) that the IDM template is scheduled for. For example: at 3am= 180 mins. This attribute is required by PUT and POST requests. |
| scheduleType | string | No | The schedule type for the IDM template's schedule (i.e., Monthly, Weekly, Daily, or None). This attribute is required by PUT and POST requests. |
| uploadStatus | string | No | The status of the file uploaded to the Index Tool for the IDM template. |
| userName | string | No | The username to be used on the IDM template's host machine. |
| version | integer (int32) | No | The version number for the IDM template. |
| volumeOfDocuments | integer (int64) | No | The total volume of all the documents associated to the IDM template. |

### IdmProfileMatchAccuracyDetail
Indexed Document Match (IDM) template (or profile) match accuracy details.
| Field | Type | Required | Description |
| ----- | ---- | -------- | ----------- |
| adpIdmProfile | object | No | The IDM template reference. You can configure this field using the information retrieved by the /idmprofile/lite endpoint. |
| matchAccuracy | string | No | The IDM template match accuracy. |

### IdmProfileSummary
IDM template (i.e., IDM profile) summary information.
| Field | Type | Required | Description |
| ----- | ---- | -------- | ----------- |
| clientVm | object | No | The name of the Index Tool virtual machine (VM) that the IDM template belongs to. |
| lastModified | integer (int32) | No | The timestamp the IDM template was last modified. |
| modifiedBy | object | No | The admin that modified the IDM template last. |
| numDocuments | integer (int32) | No | The number of documents. |
| profileId | integer (int32) | No | The unique identifier for the IDM template (i.e., IDM profile). |
| templateName | string | No | The IDM template name. |

### IncidentReceiverServer
Zscaler Incident Receiver information.
| Field | Type | Required | Description |
| ----- | ---- | -------- | ----------- |
| flags | integer (int32) | No | The Incident Receiver server flag. |
| id | integer (int32) | No | The unique identifier for the Incident Receiver. |
| name | string | Yes | The Incident Receiver server name. |
| status | string | Yes | The status of the Incident Receiver. |
| url | string | Yes | The Incident Receiver server URL. |

### PolicyWebApplication
| Field | Type | Required | Description |
| ----- | ---- | -------- | ----------- |
| appCatModified | boolean | No |  |
| appNotReady | boolean | No |  |
| backendName | string | No |  |
| deprecated | boolean | No |  |
| misc | boolean | No |  |
| name | string | No |  |
| originalName | string | No |  |
| underMigration | boolean | No |  |
| val | integer (int32) | No |  |
| webApplicationClass | string | No | The cloud application class selected from the available options |

### SMMsgStatusInfo
Error message information that is returned when an invalid pattern is identified within a custom DLP dictionary
| Field | Type | Required | Description |
| ----- | ---- | -------- | ----------- |
| errMsg | string | No |  |
| errParameter | string | No |  |
| errPosition | integer (int32) | No |  |
| errSuggestion | string | No |  |
| idList | array[integer (int32)] | No |  |
| status | string (byte) | No |  |

### Tag
The list of tags (key-value pairs) selected within a tag type
| Field | Type | Required | Description |
| ----- | ---- | -------- | ----------- |
| key | string | No | The *key* component present in the key-value pair contained in a tag |
| value | string | No | The *value* component present in the key-value pair contained in a tag |

### TagContainer
One or more tags combined using logical operators within a tag type
| Field | Type | Required | Description |
| ----- | ---- | -------- | ----------- |
| operator | string | No | The logical operator (either AND or OR) used to combine the tags within a tag type |
| tags | array[Tag] | No | One or more tags, each consisting of a key-value pair, selected within a tag type. If multiple tags are present within a tag type, they are combined using a logical operator.
**Note**: A maximum of 8 tags can be added to a workload group, irrespective of the number of tag types present. |

### WebDlpRule
DLP policy rule information.
| Field | Type | Required | Description |
| ----- | ---- | -------- | ----------- |
| accessControl | string | No | The access privilege for this DLP policy rule based on the admin's state. |
| action | string | No | The action taken when traffic matches the DLP policy rule criteria. |
| auditor | object | No | The auditor to which the DLP policy rule must be applied. |
| cloudApplications | array[string] | No | The list of cloud applications to which the DLP policy rule must be applied. |
| departments | array[EntityReference] | No | The Name-ID pairs of departments to which the DLP policy rule must be applied. |
| description | string | No | The description of the DLP policy rule. |
| dlpDownloadScanEnabled | boolean | No | If this field is set to true, DLP scan is enabled for file downloads from cloud applications configured in the rule. If this field is set to false, DLP scan is disabled for downloads from the cloud applications. |
| dlpEngines | array[EntityReference] | No | The list of DLP engines to which the DLP policy rule must be applied. |
| excludedDepartments | array[EntityReference] | No | The name-ID pairs of the departments that are excluded from the DLP policy rule. |
| excludedDomainProfiles | array[EntityReference] | No | The list of [domain profiles](/zia/about-domain-profiles) that must be added to the DLP rule criteria in order to apply the DLP rules to all domains excluding the domains that are part of the specified profiles. A maximum of 8 profiles can be selected. |
| excludedGroups | array[EntityReference] | No | The name-ID pairs of the groups that are excluded from the DLP policy rule. |
| excludedUsers | array[EntityReference] | No | The name-ID pairs of the users that are excluded from the DLP policy rule. |
| externalAuditorEmail | string | No | The email address of an external auditor to whom DLP email notifications are sent. |
| fileTypes | array[string] | No | The list of file types for which the DLP policy rule must be applied.
**Note**:
- BITMAP, JPEG, PNG, and TIFF file types are exclusively supported when optical character recognition (OCR) is enabled for DLP rules with content inspection.
- FTCATEGORY_ALL_OUTBOUND is applicable only when an external DLP engine is used for DLP rules without content inspection. |
| groups | array[EntityReference] | No | The Name-ID pairs of groups to which the DLP policy rule must be applied. |
| icapServer | object | No | The DLP server, using ICAP, to which the transaction content is forwarded. |
| id | integer (int32) | No | The unique identifier for the DLP policy rule. |
| includedDomainProfiles | array[EntityReference] | No | The list of [domain profiles](/zia/about-domain-profiles) that must be added to the DLP rule criteria in order to apply the DLP rules only to domains that are part of the specified profiles. A maximum of 8 profiles can be selected. |
| labels | array[EntityReference] | No | The Name-ID pairs of rule labels associated to the DLP policy rule. |
| lastModifiedBy | object | No | The admin that modified the DLP policy rule last. |
| lastModifiedTime | integer (int32) | No | Timestamp when the DLP policy rule was last modified. |
| locationGroups | array[EntityReference] | No | The Name-ID pairs of locations groups to which the DLP policy rule must be applied. |
| locations | array[EntityReference] | No | The Name-ID pairs of locations to which the DLP policy rule must be applied. |
| matchOnly | boolean | No | The match only criteria for DLP engines. |
| minSize | integer (int32) | No | The minimum file size (in KB) used for evaluation of the DLP policy rule. |
| name | string | No | The DLP policy rule name. |
| notificationTemplate | object | No | The template used for DLP notification emails. |
| order | integer (int32) | No | The rule order of execution for the DLP policy rule with respect to other rules. |
| parentRule | integer (int32) | No | The unique identifier of the parent rule under which an exception rule is added.
**Note**: Exception rules can be configured only when the inline DLP rule evaluation type is set to evaluate all DLP rules in the DLP Advanced Settings. To learn more, see [Configuring DLP Advanced Settings](/zia/configuring-dlp-advanced-settings). |
| protocols | array[string] | No | The protocol criteria specified for the DLP policy rule. |
| rank | integer (int32) | No | The admin rank of the admin who created the DLP policy rule. |
| severity | string | No | Indicates the severity selected for the DLP rule violation |
| state | string | No | Enables or disables the DLP policy rule. |
| subRules | array[WebDlpSubRule] | No | The list of exception rules added to a parent rule.
** Note**:
- All attributes within the `WebDlpRule` model are applicable to the sub-rules.
- Exception rules can be configured only when the inline DLP rule evaluation type is set to evaluate all DLP rules in the DLP Advanced Settings. To learn more, see [Configuring DLP Advanced Settings](\"/zia/configuring-dlp-advanced-settings\"). |
| timeWindows | array[EntityReference] | No | The Name-ID pairs of time windows to which the DLP policy rule must be applied. |
| urlCategories | array[EntityReference] | No | The list of URL categories to which the DLP policy rule must be applied. |
| users | array[EntityReference] | No | The Name-ID pairs of users to which the DLP policy rule must be applied. |
| withoutContentInspection | boolean | No | Indicates a DLP policy rule without content inspection, when the value is set to true. |
| workloadGroups | array[WorkloadGroup] | No | The list of preconfigured workload groups to which the policy must be applied. To learn more, see [About Workload Groups](/zia/about-workload-groups) and [Configuring Workload Groups]( /zia/configuring-workload-groups). |
| zccNotificationsEnabled | boolean | No | If this field is set to true, Zscaler Client Connector notification is enabled for the block action triggered by the web DLP rule. If this field is set to false, Zscaler Client Connector notification is disabled.
**Note**: This field can be configured only if the Web DLP Violation end user notification is enabled. |
| zscalerIncidentReceiver | boolean | No | Indicates whether a Zscaler Incident Receiver is associated to the DLP policy rule. |

### WebDlpSubRule
| Field | Type | Required | Description |
| ----- | ---- | -------- | ----------- |
| accessControl | string | No | The access privilege for this DLP policy rule based on the admin's state |
| action | string | No | The action taken when traffic matches the DLP policy rule criteria |
| auditor | EntityReference | No | The auditor to which the DLP policy rule must be applied |
| cloudAppInstances | array[CloudApplicationInstanceLite] | No | List of cloud application instances to which the rule applies |
| cloudApplications | array[PolicyWebApplication] | No | The list of cloud applications to which the DLP policy rule must be applied |
| departments | array[EntityReference] | No | The Name-ID pairs of departments to which the DLP policy rule must be applied |
| description | string | No | The description of the DLP policy rule |
| dlpDownloadScanEnabled | boolean | No | If this field is set to true, DLP scan is enabled for file downloads from cloud applications configured in the rule. If this field is set to false, DLP scan is disabled for downloads from the cloud applications. |
| dlpEngines | array[EntityReference] | No | The list of DLP engines to which the DLP policy rule must be applied |
| excludedDepartments | array[EntityReference] | No | The name-ID pairs of the departments that are excluded from the DLP policy rule |
| excludedDomainProfiles | array[EntityReference] | No | List of domain profiles that have to be excluded in the criteria for the rule |
| excludedGroups | array[EntityReference] | No | The name-ID pairs of the groups that are excluded from the DLP policy rule |
| excludedUsers | array[EntityReference] | No | The name-ID pairs of the users that are excluded from the DLP policy rule |
| externalAuditorEmail | string | No | The email address of an external auditor to whom DLP email notifications are sent |
| fileTypes | array[string] | No | The list of file types for which the DLP policy rule must be applied.
**Note**:
- BITMAP, JPEG, PNG, and TIFF file types are exclusively supported when optical character recognition (OCR) is enabled for DLP rules with content inspection.
- FTCATEGORY_ALL_OUTBOUND is applicable only when an external DLP engine is used for DLP rules without content inspection. |
| groups | array[EntityReference] | No | The Name-ID pairs of groups to which the DLP policy rule must be applied |
| icapServer | EntityReference | No | The DLP server, using ICAP, to which the transaction content is forwarded. |
| id | integer (int32) | No | The unique identifier for the DLP policy rule |
| includedDomainProfiles | array[EntityReference] | No | List of domain profiles that have to be included in the criteria for the rule |
| labels | array[EntityReference] | No | The Name-ID pairs of rule labels associated to the DLP policy rule |
| lastModifiedBy | EntityReference | No | The admin that modified the DLP policy rule last |
| lastModifiedTime | integer (int32) | No | Timestamp when the DLP policy rule was last modified |
| locationGroups | array[EntityReference] | No | The Name-ID pairs of locations groups to which the DLP policy rule must be applied |
| locations | array[EntityReference] | No | The Name-ID pairs of locations to which the DLP policy rule must be applied |
| matchOnly | boolean | No | The match only criteria for DLP engines |
| minSize | integer (int32) | No | The minimum file size (in KB) used for evaluation of the DLP policy rule |
| name | string | No | The DLP policy rule name |
| notificationTemplate | EntityReference | No | The template used for DLP notification emails |
| order | integer (int32) | No | The rule order of execution for the DLP policy rule with respect to other rules |
| parentRule | integer (int32) | No | Parent rule ID, applicable for exception rules when the inline DLP rule evaluation type is set to evaluate all DLP rules. |
| protocols | array[string] | No | The protocol criteria specified for the DLP policy rule |
| rank | integer (int32) | No | The admin rank of the admin who created the DLP policy rule |
| severity | string | No | Rule's severity level |
| sourceIpGroups | array[EntityReference] | No | List of source IP groups to which the rule applies |
| state | string | No | Enables or disables the DLP policy rule |
| timeWindows | array[EntityReference] | No | The Name-ID pairs of time windows to which the DLP policy rule must be applied |
| urlCategories | array[EntityReference] | No | The list of URL categories to which the DLP policy rule must be applied |
| userRiskScoreLevels | array[string] | No | The list of user risk score levels to which the rule applies. If this field is not set, the rule is applied t all user risk score levels. |
| users | array[EntityReference] | No | The Name-ID pairs of users to which the DLP policy rule must be applied |
| withoutContentInspection | boolean | No | Indicates a DLP policy rule without content inspection, when the value is set to true. |
| workloadGroups | array[WorkloadGroup] | No | List of workload groups to which the rule applies |
| zccNotificationsEnabled | boolean | No | Indicates whether Zscaler Client Connector notifications are enabled or not. This configuration is applicable only for the Block rule action. |
| zpaAppSegments | array[AppSegment] | No | List of Source IP Anchoring-enabled ZPA application segments to which the rule applies |
| zscalerIncidentReceiver | boolean | No | Indicates whether a Zscaler Incident Receiver is associated to the DLP policy rule |

### WorkloadGroup
Workload group information
| Field | Type | Required | Description |
| ----- | ---- | -------- | ----------- |
| description | string | No | Additional information of the workload group |
| expression | string | No | The workload group expression containing tag types, tags, and their relationships. |
| expressionJson | WorkloadTagExpression | No | The workload group expression containing tag types, tags, and their relationships represented in a JSON format. |
| id | integer (int32) | No | A unique identifier assigned to the workload group |
| lastModifiedBy | EntityReference | No | Information about the user that last modified the workload group |
| lastModifiedTime | integer (int32) | No | Timestamp of when the workload group was last modified |
| name | string | No | The name of the workload group |

### WorkloadTagExpression
| Field | Type | Required | Description |
| ----- | ---- | -------- | ----------- |
| expressionContainers | array[ExpressionContainer] | No | Contains one or more tag types (and associated tags) combined using logical operators within a workload group |
