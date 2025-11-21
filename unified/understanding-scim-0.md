# Understanding SCIM
Source: https://help.zscaler.com/unified/understanding-scim-0
PDF: https://help.zscaler.com/pdf/com/en/1505576.pdf

SCIM (System for Cross-domain Identity Management) is a standard protocol that you can use for provisioning and management of users and groups. Zscaler provides an easy and consistent mechanism for customers to use SCIM to manage the lifecycle of user and group accounts in the Zscaler cloud.
You can use SCIM for:
- Provisioning users and groups onto Zscaler.
- Automatically updating a user's group and department on the Zscaler user database to align with the changes in your user directory.
- Deprovisioning users from Zscaler database when users are deleted from your user directory.
There are two ways you can use SCIM with the Zscaler service. First, you can use custom SCIM clients to make REST API calls to Zscaler. To learn more, see [SCIM API Examples](/unified/scim-api-examples-1). Second, you can use one of the IdPs partnered with Zscaler.
For IdP configuration guides, see:
- [Configuring Okta as an External IdP](/unified/configuring-okta-external-idp)
- [Configuring Microsoft Entra ID as an External IdP](/unified/configuring-microsoft-entra-id-external-idp)
- [Configuring Microsoft AD FS as an External IdP](/unified/configuring-microsoft-ad-fs-external-idp)
- [Configuring PingOne as an External IdP](/unified/configuring-pingone-external-idp)
When creating users, the domain included in the username must be preregistered with Zscaler. For example, if a user has the username of "test@zslog.in", the domain "zslog.in" needs to be registered with your tenant on Zscaler. Also, the users should have a primary email address as the `Primary Email` attribute is mandatory in ZIdentity.
SCIM User Attributes
The following sections provide information on the association between SCIM user attributes and the corresponding column name in the ZIdentity database.
Core User Scheme
The following table provides information on the association between SCIM user attributes and the corresponding column name in the ZIdentity database for the Core User Scheme.
| SCIM Attribute Name | ZIdentity DB Column Name | Comments |
| ------------------- | ------------------------ | -------- |
| `ID` | `Composite value of (UserId and ZoneID)` | The unique identifier of the user |
| `EXTERNALID` | `scimExternalId` | An identifier used in the external system for user |
| `CREATED` | `createTime (int)` | The timestamp when the user was created |
| `LAST_MODIFIED` | `modTime (int)` | The timestamp when the user information was modified |
| `LOCATION` | `<OneIdentityBaseUrl>/scim/<IDP Composite ID>/Users/<Composite ID>` | The URL to locate the user resource |
| `VERSION` | `2.0` | SCIM version (hardcoded) |
| `RESOURCE_TYPE` | `User` | The type of resource (user) |
| `USERNAME` | `loginName` | The actual user ID used for authentication |
| `DISPLAY_NAME` | `displayName` | The display name of the user |
| `GIVENNAME` | `firstName` | The first name of the user |
| `FAMILYNAME` | `lastName` | The last name of the user |
| `NICK_NAME` | `nickName` | The nick name of the user |
| `PROFILE_URL` | `CustomAttributes` | The URL to the profile of the user |
| `TITLE` | `title` | The title or job of the user |
| `USER_TYPE` | `CustomAttributes` | The type of the user |
| `PREFERRED_LANGUAGE` | `language` | The preferred language of the user |
| `LOCALE` | `CustomAttributes` | The locale or language tag of the user |
| `TIME_ZONE` | `timeZone` | The timezone of the user |
| `ACTIVE` | `isDisabled()` | An indicator of whether the user is active or not |
| `PASSWORD` | `password` | The password used for authentication |
| `EMAILS` | `primaryEmail, secondaryEmail` | A list of email addresses associated with the user |
| `PHONENUMBERS` | `primaryPhone,mobilePhone` | A list of phone numbers associated with the user |
| `IMS` | `CustomAttributes` | The information on the Identity Management System used for user management and authentication |
| `PHOTOS` | `CustomAttributes` | The profile photo associated with the user |
| `ADDRESSES` | `CustomAttributes` | A list of addresses associated with the user |
| `GROUPS` | `groupIds Long[]` | The list of groups to which the user belongs |
| `ENTITLEMENTS` | `CustomAttributes` | The list of entitlements or permissions granted for the user |
| `ROLES` | `CustomAttributes` | A list of roles assigned to the user |
| `X509CERTIFICATES` | `CustomAttributes` | The list of X.509 certificates associated with the user |
Enterprise User Scheme
The following table provides information on the association between SCIM user attributes and the corresponding column name in the ZIdentity database for the Enterprise User Scheme.
| SCIM Attribute Name | ZIdentity DB Column Name | Comments |
| ------------------- | ------------------------ | -------- |
| `employeeNumber` | `CustomAttributes` | The employee number assigned to the user. This can be mapped to custom attributes. |
| `costCenter` | `CustomAttributes` | The cost center to which the user belongs. This can be mapped to custom attributes. |
| `organization` | `CustomAttributes` | The name of the organization to which the user belongs. This can be mapped to custom attributes. |
| `divison` | `CustomAttributes` | The name of the division name to which the user belongs. This can be mapped to custom attributes. |
| `department` | `department` | The name of the department to which the user belongs |
| `manager` | `CustomAttributes` | The manager or the supervisor of the user. This can be mapped to custom attributes. |
| `displayName` | `CustomAttributes` | The display name of the manager. This can be mapped to custom attributes. |
| `value` | `CustomAttributes` | The identifier used for the manager. This can be mapped to custom attributes. |
| `$ref` | `CustomAttributes` | The reference value (URL) to the user that establishes a hierarchical relationship with the user. This can be mapped to custom attributes. |
SCIM Group Attributes
The following table provides information on the association between SCIM group attributes and the corresponding column name in the ZIdentity database.
| SCIM Attribute Name | ZIdentity Store Attribute Name | Comments |
| ------------------- | ------------------------------ | -------- |
| `ID` | `Composite value of (GroupId and ZoneID)` | The unique identifier of the user |
| `EXTERNALID` | `scimExternalId` | An identifier used in the external system for user |
| `CREATED` | `createTime (int)` | The timestamp when the group was created |
| `LAST_MODIFIED` | `modTime (int)` | The timestamp when the group was modified |
| `LOCATION` | `<OneIdentityBaseUrl>/<TenantID>/scim/Users/<Composite ID>` | The URL to locate the group resource |
| `VERSION` | `2.0` | SCIM version (hardcoded) |
| `RESOURCE_TYPE` | `Group` | The type of resource (group) |
| `DISPLAYNAME` | `name` | The display name of the group |
| `Members` | `Assign users` | The list users who are part of the group |