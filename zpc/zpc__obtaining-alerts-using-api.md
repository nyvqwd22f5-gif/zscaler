# Obtaining Alerts Using API
Source: https://help.zscaler.com/zpc/obtaining-alerts-using-api
PDF: https://help.zscaler.com/pdf/com/en/1457296.pdf

This article provides information for managing Zscaler Posture Control (ZPC) alerts using APIs. All APIs are rate limited. To learn more, see [Understanding Rate Limiting](/zpc/understanding-rate-limiting).
Getting Cloud Alerts
To get a list of cloud alerts, send a `GET` request to the endpoint `/alerts/cloud`.
The following parameters might be passed when making the request to get cloud alerts for the specified parameters:
- `limit`: Indicates the page size. If not provided, the default page size is 100. The maximum limit for page size is 100.
- `offset`: Specifies the page number.
- `created[start]`: The created starting date for the alert in epoch seconds.
- `created[end]`: The created ending date for the alert in epoch seconds.
- `updated[start]`: The updated starting date for the alert in epoch seconds.
- `updated[end]`: The updated ending date for the alert in epoch seconds.
- `cloud_account_type`: Indicates the cloud account type of the alert based on the specified filter (AWS, GCP, AZURE, KUBERNETES).
- `business_units`: Filters the alert by business unit name based on the specified filter.
- `regions`: Filters the alerts based on the specified regions.
- `alert_status`: Filters the alerts by the specified `AlertStatus` value (OPEN, CLOSED, RESOLVED, IGNORED).
- `risk_level`: Filters the alerts by the specified `RiskLevel` value (LOW, MEDIUM, HIGH, CRITICAL).
- `order_by`: Orders the alerts by the specified `order_by` value. [Click here to see the supported values.](#order_by)
- `fields`: Filters the alerts by the specified `fields` value. [Click here to see the supported values.](#fields)
The following conditions apply when using the `created[start]`, `created[end]`, `updated[start]`, and `updated[end]` parameters:
- If start and end times are not specified, then alerts are retrieved for the last 48 hours by default.
- If only the start time is specified, then alerts are retrieved for up to 48 hours from the start time.
- If only the end time is specified, then alerts are retrieved from the end time to 48 hours before.
- If both the created and updated start and end times are specified, then only the alerts within the specified time range are retrieved.
- []`severity`: The severity level (Critical, High, Medium, or Low) of the cloud alert.
- `severity:asc`: The severity level in ascending order.
- `severity:desc`: The severity level in descending order.
- `created`: The timestamp when the cloud alert was created.
- `created:asc`: The timestamp when the cloud alert was created, and sorted in ascending order.
- `created:desc`: The timestamp when the cloud alert was created, and sorted in descending order.
- `updated`: The timestamp when the cloud alert was last modified.
- `updated:asc`: The timestamp when the cloud alert was last modified, and sorted in ascending order.
- `updated:desc`: The timestamp when the cloud alert was last modified, and sorted in descending order.
- `alert_status`: The status of the cloud alert (Open, Closed, Resolved, Reopened).
- `alert_status:asc`: The status of the cloud alert (Open, Closed, Resolved, Reopened), and sorted in ascending order.
- `alert_status:desc`: The status of the cloud alert (Open, Closed, Resolved, Reopened), and sorted in descending order.
- []`alert_id`: The unique identifier of the cloud alert.
- `alert_type`: The entity type of the cloud alert.
- `alert_desc`: The description of the cloud alert.
- `alert_status`: The status of the cloud alert (Open, Closed, Resolved, Reopened).
- `alert_status_desc`: The description of the cloud alert status.
- `alert_url`: The URL of the alert.
- `csp`: The Cloud Service Providers for the alert (AWS, GCP, AZURE, KUBERNETES, OCI).
- `severity`: The severity level (Critical, High, Medium, or Low) of the cloud alert.
- `risk_score`: The numeric representation of the risk.
- `threat_category`: The threat category the policy belongs to.
- `mitre_attack`: The link to the technique on the MITRE ATT&CK website.
- `theme`: The theme for the alert (Compliance, Security Events, or Security Exposure).
- `asset_category`: The top-level grouping of assets.
- `asset_type`: The type of the asset.
- `audit_procedure`: The steps to audit.
- `recommendations`: The recommended action to resolve the alert.
- `remediation_procedure`: The steps to resolve the alert.
- `alert_focus`: The focus of the alert (Asset, Identity).
- `reason`: The text description of the manually resolved alerts.
- `updated_by`: The user who modified the alert.
- `policy`: The unique identifier, the source, the name, and the description of the security policy.
- `cloud_resource`: The unique identifier, the name, the type, and the region of the cloud resource.
- `business_unit`: The name of the business unit.
- `cloud_account`: The unique identifier, the name, the organization, and the organization ID of the cloud account.
- `identity`: The unique identifier, the name, and the type of identity.
- `compliance`: The name, version, control number, type, and domains of the compliance benchmark.
- `kubernetes`: The cluster type (EKS, AKS, GKE).
- `created`: The timestamp when the cloud alert was created.
- `updated`: The timestamp when the cloud alert was last modified.
- [View an example response](#getCloudAlerts)
[]{
"alerts": [
{
"kind": "CloudAlert",
"alert_id": "123456",
"alert_type": "Security Group",
"alert_description": "The security group SG-12345678 allows inbound traffic from any IP address.",
"alert_status": "open",
"alert_status_description": "The alert is still open and has not yet been resolved.",
"alert_url": "https://example.com/alerts/",
"csp": "AWS",
"severity": "High",
"risk_level": "High",
"risk_score": "8.5",
"threat_category": "Network Security",
"mitre_attack": "T1071 - Application Layer Protocol",
"theme": "Network Security",
"asset_category": "Compute",
"asset_type": "EC2 Instance",
"age": 86400,
"audit_procedure": "The security group rules should be reviewed and the unnecessary rules should be removed.",
"recommendations": "Restrict the inbound traffic to the required IP addresses only.",
"remediation_procedure": "The security group rules should be modified to restrict the inbound traffic to the required IP addresses only.",
"alert_focus": "Network Security",
"reason": "The security group was created without proper restrictions on inbound traffic.",
"updated_by": "John Doe",
"created": 123234536456,
"updated": 123234537689,
"policy": {
"policy_id": "5678",
"policy_source": "example source",
"policy_name": "Example Policy",
"policy_description": "A description of the policy"
},
"cloud_resource": {
"resource_id": "abcd",
"resource_name": "Example Resource",
"resource_type": "EC2 Instance",
"resource_region": "us-east-1"
},
"identity": {
"identity_id": "xyz-789",
"identity_name": "Example User",
"identity_type": "User",
"identity_source": "Example Source"
},
"compliance": {
"name": "Example Compliance",
"version": "1.0",
"number": "xyz-75666",
"type": "Regulation",
"domains": "Finance, Healthcare"
},
"business_unit": {
"business_unit_name": "Example Business Unit"
},
"cloud_account": {
"account_id": "1234",
"account_name": "Example Account",
"organization": "Example Org",
"organization_id": "abc-123"
},
"kubernetes": {
"cluster_type": "GKE",
"cluster_name": "Example Cluster"
}
}
],
"total_count": 1,
"prev_link": "https://example.com/alerts/cloud/offset=1",
"next_link": "https://example.com/alerts/cloud/offset=3"
}
A successful response returns code 200. To learn more, see [API Response Codes and Error Messages](/zpc/api-response-codes-and-error-messages).
Getting IaC Alerts
To get a list of IaC alerts, send a `GET` request to the endpoint `/alerts/iac`.
The following parameters might be passed when making the request to get IaC alerts for the specified parameters:
- `limit`: Indicates the page size. If not provided, the default page size is 100. The maximum limit for page size is 100.
- `offset`: Specifies the page number.
- `created[start]`: The created starting date for the alert in epoch seconds.
- `created[end]`: The created ending date for the alert in epoch seconds.
- `updated[start]`: The updated starting date for the alert in epoch seconds.
- `updated[end]`: The updated ending date for the alert in epoch seconds.
- `cloud_account_type`: Indicates the cloud account type of the alert based on the specified filter (AWS, GCP, AZURE, KUBERNETES).
- `business_units`: Filters the alert by business unit name based on the specified filter.
- `regions`: Filters the alerts based on the specified regions.
- `alert_status`: Filters the alerts by the specified `AlertStatus` value (OPEN, CLOSED, RESOLVED, IGNORED).
- `risk_level`: Filters the alerts by the specified `RiskLevel` value (LOW, MEDIUM, HIGH, CRITICAL).
- `order_by`: Orders the alerts by the specified `order_by` value. [Click here to see the supported values.](#order_by_IAC)
- `fields`: Filters the alerts by the specified `fields` value. [Click here to see the supported values.](#fields_IAC)
The following conditions apply when using the `created[start]`, `created[end]`, `updated[start]`, and `updated[end]` parameters:
- If start and end times are not specified, then alerts are retrieved for the last 48 hours by default.
- If only the start time is specified, then alerts are retrieved for up to 48 hours from the start time.
- If only the end time is specified, then alerts are retrieved from the end time to 48 hours before.
- If both the created and updated start and end times are specified, then only the alerts within the specified time range are retrieved.
- []`severity`: The severity level (Critical, High, Medium, or Low) of the cloud alert.
- `severity:asc`: The severity level in ascending order.
- `severity:desc`: The severity level in descending order.
- `created`: The timestamp when the cloud alert was created.
- `created:asc`: The timestamp when the cloud alert was created, and sorted in ascending order.
- `created:desc`: The timestamp when the cloud alert was created, and sorted in descending order.
- `updated`: The timestamp when the cloud alert was last modified.
- `updated:asc`: The timestamp when the cloud alert was last modified, and sorted in ascending order.
- `updated:desc`: The timestamp when the cloud alert was last modified, and sorted in descending order.
- `alert_status`: The status of the cloud alert (Open, Closed, Resolved, Reopened).
- `alert_status:asc`: The status of the cloud alert (Open, Closed, Resolved, Reopened), and sorted in ascending order.
- `alert_status:desc`: The status of the cloud alert (Open, Closed, Resolved, Reopened), and sorted in descending order.
- []`alert_id`: The unique identifier of the cloud alert.
- `alert_type`: The entity type of the cloud alert.
- `alert_desc`: The description of the cloud alert.
- `alert_status`: The status of the cloud alert (Open, Closed, Resolved, Reopened).
- `alert_status_desc`: The description of the cloud alert status.
- `alert_url`: The URL of the alert.
- `csp`: The Cloud Service Providers for the alert (AWS, GCP, AZURE, KUBERNETES, OCI).
- `severity`: The severity level (Critical, High, Medium, or Low) of the cloud alert.
- `risk_score`: The numeric representation of the risk.
- `threat_category`: The threat category the policy belongs to.
- `mitre_attack`: The link to the technique on the MITRE ATT&CK website.
- `theme`: The theme for the alert (Compliance, Security Events, or Security Exposure).
- `asset_category`: The top-level grouping of assets.
- `asset_type`: The type of the asset.
- `audit_procedure`: The steps to audit.
- `recommendations`: The recommended action to resolve the alert.
- `remediation_procedure`: The steps to resolve the alert.
- `alert_focus`: The focus of the alert (Asset, Identity).
- `reason`: The text description of the manually resolved alerts.
- `updated_by`: The user who modified the alert.
- `policy`: The unique identifier, the source, the name, and the description of the security policy.
- `cloud_resource`: The unique identifier, the name, the type, and the region of the cloud resource.
- `business_unit`: The name of the business unit.
- `cloud_account`: The unique identifier, the name, the organization, and the organization ID of the cloud account.
- `identity`: The unique identifier, the name, and the type of identity.
- `compliance`: The name, version, control number, type, and domains of the compliance benchmark.
- `kubernetes`: The cluster type (EKS, AKS, GKE).
- `created`: The timestamp when the cloud alert was created.
- `updated`: The timestamp when the cloud alert was last modified.
- [View an example response](#getIaCAlerts)
[]{
"alerts": [
{
"kind": "IaCAlert",
"alert_id": "123456",
"alert_type": "Security Group",
"alert_description": "The security group SG-12345678 allows inbound traffic from any IP address.",
"alert_status": "open",
"alert_status_description": "The alert is still open and has not yet been resolved.",
"alert_url": "https://example.com/alerts/",
"csp": "AWS",
"severity": "High",
"risk_level": "High",
"risk_score": "8.5",
"threat_category": "Network Security",
"mitre_attack": "T1071 - Application Layer Protocol",
"theme": "Network Security",
"asset_category": "Compute",
"asset_type": "EC2 Instance",
"age": 86400,
"audit_procedure": "The security group rules should be reviewed and the unnecessary rules should be removed.",
"recommendations": "Restrict the inbound traffic to the required IP addresses only.",
"remediation_procedure": "The security group rules should be modified to restrict the inbound traffic to the required IP addresses only.",
"alert_focus": "Network Security",
"reason": "The security group was created without proper restrictions on inbound traffic.",
"updated_by": "John Doe",
"created": 123234536456,
"updated": 123234537689,
"policy": {
"policy_id": "5678",
"policy_source": "example source",
"policy_name": "Example Policy",
"policy_description": "A description of the policy"
},
"cloud_resource": {
"resource_id": "abcd",
"resource_name": "Example Resource",
"resource_type": "EC2 Instance",
"resource_region": "us-east-1"
},
"identity": {
"identity_id": "xyz-789",
"identity_name": "Example User",
"identity_type": "User",
"identity_source": "Example Source"
},
"compliance": {
"name": "Example Compliance",
"version": "1.0",
"number": "xyz-75666",
"type": "Regulation",
"domains": "Finance, Healthcare"
},
"business_unit": {
"business_unit_name": "Example Business Unit"
},
"cloud_account": {
"account_id": "1234",
"account_name": "Example Account",
"organization": "Example Org",
"organization_id": "abc-123"
},
"kubernetes": {
"cluster_type": "GKE",
"cluster_name": "Example Cluster"
}
}
],
"total_count": 1,
"prev_link": "https://example.com/alerts/cloud/offset=1",
"next_link": "https://example.com/alerts/cloud/offset=3"
}
A successful response returns code 200. To learn more, see [API Response Codes and Error Messages](/zpc/api-response-codes-and-error-messages).

## Contents
- **API Developer & Reference Guide**
  - [Getting Started](/zpc/getting-started-zpc-api)
  - [Understanding Rate Limiting](/zpc/understanding-rate-limiting)
  - [API Response Codes and Error Messages](/zpc/api-response-codes-and-error-messages)
  - **Reference Guide**
    - [Alerts](/zpc/alerts-api)
  - **Working with APIs**
    - [Obtaining Alerts Using API](/zpc/obtaining-alerts-using-api)