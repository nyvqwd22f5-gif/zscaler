# URL Categories
Source: https://help.zscaler.com/zia/url-categories

API Reference Guide for the ZIA Cloud Service and Sandbox Submission APIs

**Base URL:** https://zsapi.[zscaler-cloud-name]/api/v1

## `GET /urlCategories`

Gets information about all or custom URL categories. By default, the response includes keywords.

**Tags:** URL Categories
**Consumes:** application/json
**Produces:** application/json

| Name | In | Type | Required | Description |
| ---- | --- | ---- | -------- | ----------- |
| customOnly | query | boolean | No | If set to true, gets information on custom URL categories only. |
| includeOnlyUrlKeywordCounts | query | boolean | No | By default this parameter is set to false, so the response includes URLs and keywords for custom URL categories only. If set to true, the response only includes URL and keyword counts. |

| Code | Description | Schema |
| ---- | ----------- | ------ |
| 200 | Successful Operation | array[UrlCategoryInformation] |

## `POST /urlCategories`

Adds a new custom URL category. If keywords are included within the request, they are added to the new category.

**Tags:** URL Categories
**Consumes:** application/json
**Produces:** application/json

| Name | In | Type | Required | Description |
| ---- | --- | ---- | -------- | ----------- |
| customCategory | body | UrlCategoryInformation | No | Custom URL category information. |

| Code | Description | Schema |
| ---- | ----------- | ------ |
| 200 | Successful Operation | UrlCategoryInformation |

## `GET /urlCategories/lite`

Gets a lightweight key-value list of all or custom URL categories.

**Tags:** URL Categories
**Consumes:** application/json
**Produces:** application/json
No parameters.

| Code | Description | Schema |
| ---- | ----------- | ------ |
| 200 | Successful Operation | array[UrlCategoryInformation] |

## `POST /urlCategories/review/domains`

For the specified list of URLs, finds matching entries present in existing custom URL categories. This endpoint allows you to review URLs for potential matches in existing categories to group-related entries in a single category.
The URLs specified are matched against the entries present in `urls` (referred as Custom URLs in the UI) and `dbCategorizedUrls` (referred as URLs Retaining Parent Category in the UI) fields of custom URL categories. The matches are returned only for URLs of Subdomain type that match with existing wildcard entries and not vice versa. The only exception is when a wildcard URL is matched against another wildcard entry, but the former is identified as a subdomain in relation to the wildcard match. For example, if a URL such as `.teams.microsoft.com` matches with `.microsoft.com`, the `.teams.microsoft.com` entry in this case is regarded as a subdomain in relation to the match found and is returned as part of the API response. However, if `.teams.microsoft.com` matches with `teams.microsoft.com`, this becomes a wildcard match against a subdomain and is discarded in the response.
**Note**: A maximum of 100 URLs can be sent in a request.
The matches found through this request can be added to the required custom URL categories using the `PUT /urlCategories/review/domains` request.

**Tags:** URL Categories
**Consumes:** application/json
**Produces:** application/json

| Name | In | Type | Required | Description |
| ---- | --- | ---- | -------- | ----------- |
| body | body | array[string] | Yes | The list of URLs that must be matched against the entries present in existing custom URL categories |

| Code | Description | Schema |
| ---- | ----------- | ------ |
| 200 | Successful Operation | array[UrlDomainReview] |

## `PUT /urlCategories/review/domains`

Adds the list of matching URLs fetched by `POST /urlCategories/review/domains` to the specified custom URL categories. The URL specified is added to either `urls` (referred to as Custom URLs in the UI) or `dbCategorizedUrls` (referred to as URLs Retaining Parent Category in the UI) fields of the custom category based on the following condition: If the matching URL is present in the `dbCategorizedUrls` field, the new entry is added to this field. Otherwise, it is added to the `urls` field.
**Note**:
- A maximum of 100 URL categories can be updated at once using this request.
- Only URLs that are of Subdomain type can be added to custom categories via this request. Wildcard matches cannot be added. To learn more, see the description for `POST /urlCategories/review/domains`.

**Tags:** URL Categories
**Consumes:** application/json
**Produces:** application/json

| Name | In | Type | Required | Description |
| ---- | --- | ---- | -------- | ----------- |
| body | body | array[UrlDomainReview] | Yes | Information about the URLs (of Subdomain type) and the respective custom categories to which they must be added. This information can be obtained from the response of POST `/urlCategories/review/domains`
. |

| Code | Description | Schema |
| ---- | ----------- | ------ |
| default | Successful Operation |  |

## `GET /urlCategories/urlQuota`

Gets information on the number of unique URLs that are currently provisioned for your organization as well as how many URLs you can add before reaching that number.

**Tags:** URL Categories
**Consumes:** application/json
**Produces:** application/json
No parameters.

| Code | Description | Schema |
| ---- | ----------- | ------ |
| 200 | Successful Operation | UrlsQuotaDOM |

## `DELETE /urlCategories/{categoryId}`

Deletes the custom URL category for the specified ID. You cannot delete a custom category while it is being used by a URL policy or NSS feed. Also, predefined categories cannot be deleted.

**Tags:** URL Categories
**Consumes:** application/json
**Produces:** application/json

| Name | In | Type | Required | Description |
| ---- | --- | ---- | -------- | ----------- |
| categoryId | path | string | Yes | The unique identifer for the custom URL category. |

| Code | Description | Schema |
| ---- | ----------- | ------ |
| 200 | Successful Operation |  |

## `GET /urlCategories/{categoryId}`

Gets the URL category information for the specified ID.

**Tags:** URL Categories
**Consumes:** application/json
**Produces:** application/json

| Name | In | Type | Required | Description |
| ---- | --- | ---- | -------- | ----------- |
| categoryId | path | string | Yes | The unique identifier for the URL category. |

| Code | Description | Schema |
| ---- | ----------- | ------ |
| 200 | Successful Operation | UrlCategoryInformation |

## `PUT /urlCategories/{categoryId}`

Updates the URL category for the specified ID. If keywords are included within the request, then they replace existing ones for the specified URL category . If the keywords attribute is not included the request, the existing keywords are retained.
You can perform a full update for the specified URL category. However, if attributes are omitted within the update request, the values for those attributes are cleared.
You can also perform an incremental update, to add or remove URLs, for the specified URL category using the action parameter. To learn more, see [URL Categories Use Cases](/zia/url-categories-use-cases).

**Tags:** URL Categories
**Consumes:** application/json
**Produces:** application/json

| Name | In | Type | Required | Description |
| ---- | --- | ---- | -------- | ----------- |
| categoryId | path | string | Yes | The unique identifer for the URL category. |
| action | query | string | No | The action applied to the URL category (i.e., add or remove from category list). When no action is specified, all the URLs sent in the request replace the existing ones. It is recommended that you specify the add or remove action to update the URL categories. This ensures that the update is performed only on the added or removed URLs. Specifying the action is useful when the URL category list is large. To learn more, see [URL Categories Use Cases](/zia/url-categories-use-cases). |
| customCategory | body | UrlCategoryInformation | No | Updates the URL category. |

| Code | Description | Schema |
| ---- | ----------- | ------ |
| 200 | Successful Operation | UrlCategoryInformation |

## `POST /urlLookup`

Retrieve Zscaler's default classification for a given set of URLs (e.g., ['abc.com', 'xyz.com']).
**Note**:
- Custom URL classification is not returned by this request. Any URLs that are not categorized under a predefined URL category return a value of `MISCELLANEOUS_OR_UNKNOWN`.
- Up to 100 URLs can be looked up per request, and a URL cannot exceed 1,024 characters.

**Tags:** URL Categories
**Consumes:** application/json
**Produces:** application/json

| Name | In | Type | Required | Description |
| ---- | --- | ---- | -------- | ----------- |
| urls | body | array[string] | No | The given set of URLs to be looked up. |

| Code | Description | Schema |
| ---- | ----------- | ------ |
| 200 | Successful Operation | array[UrlClassificationInfo] |

## Models
### AdminScope
An admin's scope can be limited to certain resources, policies, or reports. An admin's scope can be limited by LOCATION, LOCATION GROUP, or DEPARTMENT. If this is not specified, then the admin has an ORGANIZATION scope by default.
| Field | Type | Required | Description |
| ----- | ---- | -------- | ----------- |
| ScopeEntities | array[EntityReference] | No | Based on the admin scope type, the entities can be the ID/name pair of departments, locations, or location groups. The attribute name is subject to change. |
| Type | string | No | The admin scope type. The attribute name is subject to change. |
| scopeGroupMemberEntities | array[EntityReference] | No | Only applicable for the LOCATION_GROUP admin scope type, in which case this attribute gives the list of ID/name pairs of locations within the location group. The attribute name is subject to change. |

### EntityReference
This is an immutable reference to an entity that mainly consists of id and name.
| Field | Type | Required | Description |
| ----- | ---- | -------- | ----------- |
| extensions | object | No | Additional information about the entity |
| externalId | string | No | An external identifier used for an entity that is managed outside of ZIA. Examples include `zpaServerGroup` and `zpaAppSegments`. This field is not applicable to ZIA-managed entities. |
| id | integer (int64) | No | A unique identifier for an entity |
| name | string | No | The configured name of the entity |

### UrlCategoryInformation
URL category information as identified by Zscaler.
| Field | Type | Required | Description |
| ----- | ---- | -------- | ----------- |
| configuredName | string | No | Name of the URL category. This is only required for custom URL categories. |
| customCategory | boolean | No | Set to true for custom URL category. Up to 48 custom URL categories can be added per organization. |
| customIpRangesCount | integer (int32) | No | The number of custom IP address ranges associated to the URL category. |
| customUrlsCount | integer (int32) | No | The number of custom URLs associated to the URL category. |
| dbCategorizedUrls | array[string] | No | URLs added to a custom URL category are also retained under the original parent URL category (i.e., the predefined category the URL previously belonged to). The URLs entered are covered by policies that reference the original parent URL category as well as those that reference the custom URL category. For example, if you add www.amazon.com, this URL is covered by policies that reference the custom URL category as well as policies that reference its parent URL category of "Online Shopping". |
| description | string | No | Description of the URL category. Contains tag name and needs to be localized on client side in case of predefined category (customCategory=null or =false), else it contains the user-entered description which does not have localization support. |
| editable | boolean | No | Value is set to false for custom URL category when due to scope user does not have edit permission |
| id | string | Yes | URL category |
| ipRanges | array[string] | No | Custom IP address ranges associated to a URL category. Up to 2000 custom IP address ranges and retaining parent custom IP address ranges can be added, per organization, across all categories.
**Note**: This field is available only if the option to configure custom IP ranges is enabled for your organization. To enable this option, contact Zscaler Support. |
| ipRangesRetainingParentCategory | array[string] | No | The retaining parent custom IP address ranges associated to a URL category. Up to 2000 custom IP ranges and retaining parent custom IP address ranges can be added, per organization, across all categories. |
| ipRangesRetainingParentCategoryCount | integer (int32) | No | The number of custom IP address ranges associated to the URL category, that also need to be retained under the original parent category. |
| keywords | array[string] | No | Custom keywords associated to a URL category. Up to 2048 custom keywords can be added per organization across all categories (including bandwidth classes). |
| keywordsRetainingParentCategory | array[string] | No | Retained custom keywords from the parent URL category that is associated to a URL category. Up to 2048 retained parent keywords can be added per organization across all categories (including bandwidth classes). |
| scopes | array[AdminScope] | No | Scope of the custom categories. |
| superCategory | string | No | Super Category of the URL category. This field is required when creating custom URL categories. |
| type | string | No | Type of the custom categories. |
| urlKeywordCounts | object | No | URL and keyword counts for the URL category. |
| urls | array[string] | No | Custom URLs to add to a URL category. Up to 25,000 custom URLs can be added per organization across all categories (including bandwidth classes). |
| urlsRetainingParentCategoryCount | integer (int32) | No | The number of custom URLs associated to the URL category, that also need to be retained under the original parent category. |

### UrlCategoryReference
Information about the URL category
| Field | Type | Required | Description |
| ----- | ---- | -------- | ----------- |
| id | string | No | The unique identifier assigned to the custom URL category |
| name | string | No | This attribute is populated with the name configured by the admin in the case of custom categories and the predefined name in the case of default categories |

### UrlClassificationInfo
URL Classification details
| Field | Type | Required | Description |
| ----- | ---- | -------- | ----------- |
| url | string | No | URL string |
| urlClassifications | array[string] | No | Assigned URL categories (Zscaler's default URL categories) |
| urlClassificationsWithSecurityAlert | array[string] | No | Assigned URL categories (Zscaler's default URL categories) for security alerts |

### UrlDomainReview
Information about the URLs and their respective matching categories
| Field | Type | Required | Description |
| ----- | ---- | -------- | ----------- |
| domainType | string | No | The domain type of the URL |
| matches | array[UrlCategoryReference] | No | Information about the list of categories where a URL match is found |
| url | string | No | The URL that has a match in one or more existing custom URL categories |

### UrlKeywordCounts
URL and keyword count information
| Field | Type | Required | Description |
| ----- | ---- | -------- | ----------- |
| retainParentKeywordCount | integer (int32) | No | Count of total keywords with retain parent category. |
| retainParentUrlCount | integer (int32) | No | Count of URLs with retain parent category. |
| totalKeywordCount | integer (int32) | No | Total keyword count for the category. |
| totalUrlCount | integer (int32) | No | Custom URL count for the category. |

### UrlsQuotaDOM
| Field | Type | Required | Description |
| ----- | ---- | -------- | ----------- |
| remainingUrlsQuota | integer (int32) | No |  |
| uniqueUrlsProvisioned | integer (int32) | No |  |
