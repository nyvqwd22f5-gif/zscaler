# Policy Management
Source: https://help.zscaler.com/cloud-branch-connector/policy-management

## `GET /ecRules/ecRdr`

Retrieves the list of traffic forwarding rules. To learn more, see [About Traffic Forwarding](cloud-branch-connector/about-traffic-forwarding).

**Tags:** Policy Management

| Name | In | Type | Required | Description |
| ---- | --- | ---- | -------- | ----------- |
| ruleName | query | string | No | The search string used to match against the rule name. |
| ruleOrder | query | string | No | The search string used to match against the rule order. |
| ruleDescription | query | string | No | The search string used to match against the rule description. |
| ruleForwardMethod | query | string | No | The search string used to match against the rule forwarding method. Supported forwarding methods are ZIA, ZPA, DIRECT, and DROP. |
| location | query | string | No | The search string used to match against the locations or sublocations used in rule configurations. |
| page | query | integer (int32) | No | Specifies the page offset. |
| pageSize | query | integer (int32) | No | Specifies the page size. The default size is 50. |
| sortBy | query | string | No | Rule parameter by which the list must be sorted. |
| sortOrder | query | string | No | Specifies whether the list must be sorted by ascending or descending rule order or by rule execution order. |

| Code | Description | Schema |
| ---- | ----------- | ------ |
| default | Default Response |  |

## `POST /ecRules/ecRdr`

Creates a new traffic forwarding rule. To learn more, see [Configuring Traffic Forwarding Rules](/cloud-branch-connector/configuring-traffic-forwarding-rule).

**Tags:** Policy Management
No parameters.

| Code | Description | Schema |
| ---- | ----------- | ------ |
| default | Default Response |  |

## `GET /ecRules/ecRdr/count`

Retrieves the count of traffic forwarding rules available in the Cloud & Branch Connector Admin Portal.

**Tags:** Policy Management

| Name | In | Type | Required | Description |
| ---- | --- | ---- | -------- | ----------- |
| predefinedRuleCount | query | boolean | No | Indicates whether the count of all rule rules (false) or only predefined rules is retrieved (true). |
| ruleName | query | string | No | The search string used to match against the rule name. |
| ruleOrder | query | string | No | The search string used to match against the rule order. |
| ruleDescription | query | string | No | The search string used to match against the rule description. |
| ruleForwardMethod | query | string | No | The search string used to match against the rule forwarding method. Supported values are `ZIA`, `ZPA`, `DIRECT`, and `DROP`. |
| location | query | string | No | The search string used to match against the locations or sublocations used in rule configurations. |

| Code | Description | Schema |
| ---- | ----------- | ------ |
| default | Default Response |  |

## `PUT /ecRules/ecRdr/{ruleId}`

Updates a traffic forwarding rule configuration based on the specified ID.

**Tags:** Policy Management

| Name | In | Type | Required | Description |
| ---- | --- | ---- | -------- | ----------- |
| ruleId | path | integer (int32) | Yes | ID of the rule. |

| Code | Description | Schema |
| ---- | ----------- | ------ |
| default | Default Response |  |
