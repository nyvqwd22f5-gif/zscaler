# Understanding the Zscaler Cloud & Branch Connector API
Source: https://help.zscaler.com/cloud-branch-connector/understanding-zscaler-cloud-branch-connector-api
PDF: https://help.zscaler.com/pdf/com/en/1447251.pdf

The Zscaler Cloud & Branch Connector API gives you programmatic access to the following Zscaler Cloud & Branch Connector features:
- [Authentication](#authentication)
- [Activation](#activation)
- [Admin & Role Management](#adminrolemanagement)
- [Cloud & Branch Connector Groups](#cloudandbranchconnectorgroups)
- [Forwarding Gateways](#ForwardingGateways)
- [Location Management](#locationmanagement)
- [Partner Integrations](#cb-partner-integrations)
- [Policy Management](#PolicyManagement)
- [Policy Resources](#PolicyResources)
- [Provisioning](#provisioning)
Prior to using the API, Zscaler recommends that you review [Getting Started](/cloud-branch-connector/getting-started-api) for information regarding prerequisites, authentication, and making API calls.
For information on rate limits, see [Understanding Rate Limits](/cloud-branch-connector/understanding-rate-limits). To learn more about HTTP status codes, see [API Response Codes and Error Messages](/cloud-branch-connector/api-response-codes-and-error-messages). If you encounter any issues with the Zscaler Cloud & Branch Connector API, contact Zscaler Support.
[]Authentication API resources allow you to authenticate and create an API session, check for an existing API session, and delete an API session. To learn more, see:
- [Reference Guide > Authentication](/cloud-branch-connector/authentication)
- [Getting Started](/cloud-branch-connector/getting-started-api)
[]Activation API resources allow you to activate your configuration changes by pushing them to the Central Authority (CA). In order for any configuration changes to take effect, the Zscaler service requires you to activate the changes. To learn more, see:
- [Reference Guide > Activation](/cloud-branch-connector/activation)
- [Getting Started](/cloud-branch-connector/getting-started-api)
[]Admin & Role Management API resources allow you to retrieve admin user and role information to configure the level of access admins have in the Zscaler Cloud & Branch Connector Portal and API. These resources also allow you to add, update, or delete admins within your organization. To learn more, see:
- [Reference Guide > Admin and Role Management](/cloud-branch-connector/admin-and-role-management)
- [Admin and Role Management](/cloud-branch-connector/administration/administrator-role-management)
- [Getting Started](/cloud-branch-connector/getting-started-api)
[][Cloud & Branch Connector] group API resources allow you to apply policies to a group of deployed Cloud & Branch Connectors. They also make it easy to upgrade Cloud & Branch Connectors belonging to the same group to maintain redundancy while upgrades are being executed. To learn more, see:
- [Reference Guide > Cloud & Branch Connector Groups](/cloud-branch-connector/cloud-branch-connector-groups)
- [Cloud & Branch Connector Group Management](/cloud-branch-connector/administration/cloud-branch-connector-group-management)
- [Getting Started](/cloud-branch-connector/getting-started-api)
[]Location Management API resources allow you to retrieve location and location template information. These resources also allow you to create, update, and delete location templates. To learn more, see:
- [Reference Guide > Location Management](/cloud-branch-connector/location-management)
- [Location Management](/cloud-branch-connector/administration/location-management)
[]Partner Integrations API resources allow you to retrieve Amazon Web Services (AWS) accounts and AWS account group information. These resources also allow you to create, update, and delete AWS accounts and AWS account groups. To learn more, see:
- [Reference Guide > Partner Integrations](/cloud-branch-connector/partner-integrations)
- [Cloud Connector Partner Integrations](/cloud-branch-connector/administration/cloud-connector-partner-integrations)
[]Provisioning API resources allow you to retrieve available API keys and regenerate new API keys. To learn more, see:
- [Reference Guide > Provisioning](/cloud-branch-connector/provisioning)
- [Managing Credentials Using API](/cloud-branch-connector/managing-credentials-using-api)
[]Policy Management API resources allow you to create and update traffic forwarding rules and retrieve the list of available rules and the count of rules using the following endpoints. To learn more, see:
- [Reference Guide > Policy Management](/cloud-branch-connector/policy-management)
- [Traffic Forwarding](/cloud-branch-connector/forwarding/traffic-forwarding)
[]Policy Resources API endpoints allow you to create and manage specific objects used in policy configuration, such as IP & FQDN groups, network services, and ZPA application segments. To learn more, see:
- [Reference Guide > Policy Resources](/cloud-branch-connector/policy-resources)
- [Firewall Filtering](/cloud-branch-connector/administration/firewall-filtering)
[]Forwarding Gateways API resources allow you to retrieve the list of available ZPA application segments. To learn more, see:
- [Reference Guide > Forwarding Gateways](/cloud-branch-connector/forwarding-gateways)
- [Forwarding Methods](/cloud-branch-connector/administration/forwarding-methods)

## Contents
- **API Developer & Reference Guide**
  - [Getting Started](/cloud-branch-connector/getting-started-cloud-branch-connector-api)
  - [Configuring the Postman REST API Client](/cloud-branch-connector/configuring-postman-rest-api-client)
  - [API Response Codes and Error Messages](/cloud-branch-connector/api-response-codes-and-error-messages)
  - [Understanding Rate Limits](/cloud-branch-connector/understanding-rate-limits)
  - **Reference Guide**
    - [Activation](/cloud-branch-connector/activation)
    - [Admin and Role Management](/cloud-branch-connector/admin-and-role-management)
    - [Authentication](/cloud-branch-connector/authentication)
    - [Cloud & Branch Connector Groups](/cloud-branch-connector/cloud-branch-connector-groups)
    - [Forwarding Gateways](/cloud-branch-connector/forwarding-gateways)
    - [Location Management](/cloud-branch-connector/location-management)
    - [Partner Integrations](/cloud-branch-connector/partner-integrations)
    - [Policy Management](/cloud-branch-connector/policy-management)
    - [Policy Resources](/cloud-branch-connector/policy-resources)
    - [Provisioning](/cloud-branch-connector/provisioning)
    - [API Rate Limit Summary](/cloud-branch-connector/api-rate-limit-summary)
  - **Working with APIs**
    - [Deleting Cloud & Branch Connectors Using API](/cloud-branch-connector/deleting-cloud-branch-connectors-using-api)
    - [Managing Admin Users and Roles Using API](/cloud-branch-connector/managing-admin-users-and-roles-using-api)
    - [Managing Credentials Using API](/cloud-branch-connector/managing-credentials-using-api)