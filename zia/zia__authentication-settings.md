# Authentication Settings
Source: https://help.zscaler.com/zia/authentication-settings

API Reference Guide for the ZIA Cloud Service and Sandbox Submission APIs

**Base URL:** https://zsapi.[zscaler-cloud-name]/api/v1

## `GET /authSettings`

Retrieves the organization's default authentication settings information, including authentication profile and Kerberos authentication information.

**Tags:** Authentication Settings
**Consumes:** application/json
**Produces:** application/json
No parameters.

| Code | Description | Schema |
| ---- | ----------- | ------ |
| 200 | Successful Operation | AuthSettings |

## `PUT /authSettings`

Updates the organization's default authentication settings information.

**Tags:** Authentication Settings
**Consumes:** application/json
**Produces:** application/json

| Name | In | Type | Required | Description |
| ---- | --- | ---- | -------- | ----------- |
| body | body | AuthSettings | No | The default authentication settings information |

| Code | Description | Schema |
| ---- | ----------- | ------ |
| 200 | Successful Operation | AuthSettings |

## `GET /authSettings/lite`

Retrieves organization's default authentication settings information.

**Tags:** Authentication Settings
**Consumes:** application/json
**Produces:** application/json
No parameters.

| Code | Description | Schema |
| ---- | ----------- | ------ |
| 200 | Successful Operation | AuthSettings |

## Models
### AuthSettings
Organization's default authentication settings
| Field | Type | Required | Description |
| ----- | ---- | -------- | ----------- |
| authCustomFrequency | integer (int32) | No | How frequently the users are required to authenticate. This field is customized to set the value in days. Valid range is 1–180.
This field is not applicable to the Lite API. |
| authFrequency | string | No | How frequently the users are required to authenticate (i.e., cookie expiration duration after a user is first authenticated). This field is not applicable to the Lite API. |
| autoProvision | boolean | No | Enable SAML Auto-Provisioning |
| directorySyncMigrateToScimEnabled | boolean | No | Enable to disable directory synchronization for this user repository type so you can enable SCIM provisioning or SAML auto-provisioning. Use this setting to migrate from directory synchronization to SCIM provisioning. |
| kerberosEnabled | boolean | No | Whether or not to authenticate users using Kerberos |
| kerberosPwd | string | No | Read Only. Kerberos password can only be set through generateKerberosPassword api. |
| lastSyncEndTime | integer (int32) | No | Timestamp (epoch time in seconds) corresponding to the end of the last LDAP sync. This is reset when the organization's authentication type is changed to a different directory authentication type. Applicable only for directory-based authentication. This field is not applicable to the Lite API. |
| lastSyncStartTime | integer (int32) | No | Timestamp (epoch time in seconds) corresponding to the start of the last LDAP sync. This is reset when the organization's authentication type is changed to a different directory authentication type. Applicable only for directory-based authentication. This field is not applicable to the Lite API. |
| mobileAdminSamlIdpEnabled | boolean | No | Indicate the use of Mobile Admin as IdP |
| oneTimeAuth | string | No | When the orgAuthType is NONE, administrators must manually provide the password to new end users. For new users who have not yet authenticated, a one-time token or link with a temporary password is sent as an email by the security cloud. If SAML Single Sign-On is enabled, this one-time token is not applicable, and this field is ineffective. |
| orgAuthType | string | Yes | User authentication type. Setting it to an LDAP-based authentication requires a complete LdapProperties configuration. |
| passwordExpiry | string | No | Password expiration required for form-based authentication of hosted DB users. Not applicable for other authentication types (e.g. SAML SSO or Directory). |
| passwordStrength | string | No | Password strength required for form-based authentication of hosted DB users. Not applicable for other authentication types (e.g. SAML SSO or Directory). |
| samlEnabled | boolean | No | Whether or not to authenticate users using SAML Single Sign-On. Enabling SAML requires complete SamlSettings. |
