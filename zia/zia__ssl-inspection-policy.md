# SSL Inspection Policy
Source: https://help.zscaler.com/zia/ssl-inspection-policy

API Reference Guide for the ZIA Cloud Service and Sandbox Submission APIs

**Base URL:** https://zsapi.[zscaler-cloud-name]/api/v1

## `GET /sslInspectionRules`

Retrieves all SSL inspection rules

**Tags:** SSL Inspection Policy
**Consumes:** application/json
**Produces:** application/json
No parameters.

| Code | Description | Schema |
| ---- | ----------- | ------ |
| 200 | Successful Operation | array[SSLInspectionRule] |

## `POST /sslInspectionRules`

Creates a new SSL inspection rule

**Tags:** SSL Inspection Policy
**Consumes:** application/json
**Produces:** application/json

| Name | In | Type | Required | Description |
| ---- | --- | ---- | -------- | ----------- |
| body | body | SSLInspectionRule | No | The SSL inspection rule information |

| Code | Description | Schema |
| ---- | ----------- | ------ |
| 200 | Successful Operation | SSLInspectionRule |

## `DELETE /sslInspectionRules/{ruleId}`

Deletes an existing SSL inspection rule based on the specified ID

**Tags:** SSL Inspection Policy
**Consumes:** application/json
**Produces:** application/json

| Name | In | Type | Required | Description |
| ---- | --- | ---- | -------- | ----------- |
| ruleId | path | integer | Yes | Unique identifier for the SSL inspection rule |

| Code | Description | Schema |
| ---- | ----------- | ------ |
| default | Successful Operation |  |

## `GET /sslInspectionRules/{ruleId}`

Retrieves the SSL inspection rule based on the specified ID

**Tags:** SSL Inspection Policy
**Consumes:** application/json
**Produces:** application/json

| Name | In | Type | Required | Description |
| ---- | --- | ---- | -------- | ----------- |
| ruleId | path | integer | Yes | Unique identifier for the SSL inspection rule |

| Code | Description | Schema |
| ---- | ----------- | ------ |
| 200 | Successful Operation | SSLInspectionRule |

## `PUT /sslInspectionRules/{ruleId}`

Updates the SSL inspection rule based on the specified ID

**Tags:** SSL Inspection Policy
**Consumes:** application/json
**Produces:** application/json

| Name | In | Type | Required | Description |
| ---- | --- | ---- | -------- | ----------- |
| ruleId | path | integer | Yes | Unique identifier for the SSL inspection rule |
| body | body | SSLInspectionRule | No | The SSL inspection rule information |

| Code | Description | Schema |
| ---- | ----------- | ------ |
| 200 | Successful Operation | SSLInspectionRule |

## Models
### AppSegment
Application Segment information
| Field | Type | Required | Description |
| ----- | ---- | -------- | ----------- |
| externalId | integer (int64) | No | Indicates the external ID. Applicable only when this reference is of an external entity. |
| id | integer (int32) | No | A unique identifier assigned to the Application Segment |
| name | string | No | The name of the Application Segment |
| zpaTenantId | integer (int64) | No | ID of the ZPA tenant where the Application Segment is configured |

### DecryptSubActions
| Field | Type | Required | Description |
| ----- | ---- | -------- | ----------- |
| blockSslTrafficWithNoSniEnabled | boolean | No |  |
| blockUndecrypt | boolean | No |  |
| http2Enabled | boolean | No |  |
| minClientTLSVersion | string | No |  |
| minServerTLSVersion | string | No |  |
| ocspCheck | boolean | No |  |
| serverCertificates | string | No |  |

### DoNotDecryptSubActions
| Field | Type | Required | Description |
| ----- | ---- | -------- | ----------- |
| blockSslTrafficWithNoSniEnabled | boolean | No |  |
| bypassOtherPolicies | boolean | No |  |
| minTLSVersion | string | No |  |
| ocspCheck | boolean | No |  |
| serverCertificates | string | No |  |

### EntityReference
This is an immutable reference to an entity that mainly consists of id and name
| Field | Type | Required | Description |
| ----- | ---- | -------- | ----------- |
| extensions | object | No | Additional information about the entity |
| externalId | string | No | An external identifier used for an entity that is managed outside of ZIA. Examples include `zpaServerGroup` and `zpaAppSegments`. This field is not applicable to ZIA-managed entities. |
| id | integer (int64) | No | A unique identifier for an entity |
| name | string | No | The configured name of the entity |

### ExpressionContainer
One or more tag types (and associated tags) combined using logical operators within a workload group
| Field | Type | Required | Description |
| ----- | ---- | -------- | ----------- |
| operator | string | No | The operator (either AND or OR) used to create logical relationships among tag types |
| tagContainer | TagContainer | No | Contains one or more tags and the logical operator used to combine the tags within a tag type |
| tagType | string | No | The tag type selected from a predefined list |

### SSLAction
| Field | Type | Required | Description |
| ----- | ---- | -------- | ----------- |
| decryptSubActions | DecryptSubActions | No |  |
| doNotDecryptSubActions | DoNotDecryptSubActions | No |  |
| overrideDefaultCertificate | boolean | No |  |
| showEUN | boolean | No |  |
| showEUNATP | boolean | No |  |
| sslInterceptionCert | EntityReference | No |  |
| type | string | No |  |

### SSLInspectionRule
SSL inspection rule information
| Field | Type | Required | Description |
| ----- | ---- | -------- | ----------- |
| accessControl | string | No | Access privilege to this rule based on the admin's RBA |
| action | SSLAction | Yes | Action taken when the traffic matches policy |
| cloudApplications | array[SslPolicyWebApplication] | No | Cloud applications for which the SSL inspection rule is applied. When this attribute is not set, it implies ANY applications. |
| defaultRule | boolean | No | A Boolean value that indicates whether the rule is the default rule or not |
| departments | array[EntityReference] | No | Name-ID pairs of departments for which the rule is applied. If not set, rule is applied for all departments. |
| description | string | No | Description provided by the administrator. |
| destIpGroups | array[EntityReference] | No | User-defined destination IP address groups on which the rule is applied. If not set, rule is not restricted to specific destination IP address groups. |
| deviceGroups | array[EntityReference] | No | Name-ID pairs of device groups for which the rule is applied |
| deviceTrustLevels | array[string] | No | List of device trust levels for which the rule must be applied. While the High Trust, Medium Trust, or Low Trust evaluation is applicable only to Zscaler Client Connector traffic, Unknown evaluation applies to all traffic. The trust levels are assigned to the devices based on your posture configurations in the Zscaler Client Connector Portal. If no value is set, this field is ignored during the policy evaluation. |
| devices | array[EntityReference] | No | Name-ID pairs of devices for which the rule is applied |
| groups | array[EntityReference] | No | Name-ID pairs of groups for which the rule is applied. If not set, rule is applied for all groups. |
| id | integer (int32) | No | System generated identifier for the SSL inspection rule |
| labels | array[EntityReference] | No | Name-ID pairs of rule labels associated with the rule |
| lastModifiedBy | object | No | Admin user that last modified the rule. Ignore if the request is POST or PUT. For GET, ignore if the rule is for the current version. |
| lastModifiedTime | integer (int32) | No | Timestamp when the rule was last modified. Ignore if the request is POST or PUT. For GET, ignore if the rule is for the current version. |
| locationGroups | array[EntityReference] | No | Name-ID pairs of locations groups for which the rule must be applied. |
| locations | array[EntityReference] | No | Name-ID pairs of location for which the rule is applied. If not set, rule is applied for all locations. |
| name | string | Yes | Rule name |
| order | integer (int32) | Yes | Order of rule execution with respect to other SSL inspection rules. |
| platforms | array[string] | No | Zscaler Client Connector device platforms for which the rule must be applied. If not set, rule is applied to all device platforms |
| predefined | boolean | No | A Boolean value that indicates whether the rule is a predefined SSL inspection rule or not |
| proxyGateways | array[EntityReference] | No | The proxy chaining gateway for which this rule is applicable. Ignore if the forwarding method is not Proxy Chaining. |
| rank | integer (int32) | Yes | Admin rank assigned to this rule |
| roadWarriorForKerberos | boolean | No | When set to true, the rule is applied to remote users that use PAC with Kerberos authentication. Otherwise, it is a don't care. |
| sourceIpGroups | array[EntityReference] | No | User-defined source IP address groups on which the rule is applied. If not set, rule is not restricted to specific source IP address groups. |
| state | string | No | State whether it is enabled, disabled, or just set to monitoring |
| timeWindows | array[EntityReference] | No | The time intervals during which the rule applies |
| urlCategories | array[SslUrlCategory] | No | List of URL categories for which rule must be applied |
| userAgentTypes | array[string] | No | User agent type list |
| users | array[EntityReference] | No | Name-ID pairs of users for which the rule is applied. If not set, user criteria is not considered in rule enforcement. |
| workloadGroups | array[WorkloadGroup] | No | List of workload groups for which this rule is applicable |
| zpaAppSegments | array[AppSegment] | No | List of Source IP Anchoring-enabled ZPA Application Segments for which this rule is applicable |

### SslPolicyWebApplication
| Field | Type | Required | Description |
| ----- | ---- | -------- | ----------- |
| appCatModified | boolean | No |  |
| appNotReady | boolean | No |  |
| backendName | string | No |  |
| deprecated | boolean | No |  |
| misc | boolean | No |  |
| name | string | No |  |
| originalName | string | No |  |
| val | integer (int32) | No |  |
| webApplicationClass | string | No |  |

### SslUrlCategory
| Field | Type | Required | Description |
| ----- | ---- | -------- | ----------- |
| backendName | string | No |  |
| comments | string | No |  |
| deprecated | boolean | No |  |
| mask | integer (int32) | No |  |
| name | string | No |  |
| urlSupercategory | string | No |  |
| userConfiguredName | string | No |  |
| val | integer (int32) | No |  |

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

### WorkloadGroup
Workload group information
| Field | Type | Required | Description |
| ----- | ---- | -------- | ----------- |
| description | string | No | The description of the workload group |
| expression | string | No | The workload group expression containing tag types, tags, and their relationships. |
| expressionJson | WorkloadTagExpression | No | The workload group expression containing tag types, tags, and their relationships represented in a JSON format. |
| id | integer (int32) | No | A unique identifier assigned to the workload group |
| lastModifiedBy | EntityReference | No | Information about the admin that last modified the workload group |
| lastModifiedTime | integer (int32) | No | Timestamp when the workload group was last modified |
| name | string | No | The name of the workload group |

### WorkloadTagExpression
| Field | Type | Required | Description |
| ----- | ---- | -------- | ----------- |
| expressionContainers | array[ExpressionContainer] | No | Contains one or more tag types (and associated tags) combined using logical operators within a workload group |
