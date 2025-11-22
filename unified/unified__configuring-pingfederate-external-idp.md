# Configuring PingFederate as an External IdP
Source: https://help.zscaler.com/unified/configuring-pingfederate-external-idp
PDF: https://help.zscaler.com/pdf/com/en/1505491.pdf

This guide provides information on how to configure PingFederate as an external identity provider (IdP) for ZIdentity to facilitate single sign-on (SSO) to various Zscaler services for admin access management. You can configure PingFederate as an external IdP to enable SSO to ZIdentity using the Security Assertion Markup Language (SAML) authentication protocol. You can provision users to ZIdentity from PingFederate using System for Cross-domain Identity Management (SCIM) provisioning.
If you want to leverage [step-up authentication](/unified/understanding-step-up-authentication), it is recommended to use OIDC-based integrations as most IdPs only support step-up authentication with the OIDC protocol.
- [OIDC-Based Authentication](#oidc-based-authentication)
- [SAML-Based Authentication](#saml-based-authentication)
- [IdP-Initiated SSO for ZIdentity Tenants Enabled with Experience Center](#idp-initiated-sso-flow)
[]Prerequisites
Ensure that you have configured:
- A datastore.
- An LDAP connection for the datastore to your directory server.
- A password credential validator.
- An IdP adpater.
- A policy contract.
- An authentication policy.
- An access token management instance.
- An OpenID connect policy.
- Access token mappings.
To learn more, refer to the [PingFederate documentation](https://docs.pingidentity.com/pingfederate/latest/administrators_reference_guide/pf_administrators_reference_guide.html).
Configuring PingFederate as OP for ZIdentity
To set up PingFederate as an IdP for ZIdentity:
- [1. Set up PingFederate as an OP in ZIdentity.](#set-up-pingfederate-zidentity-oidc)
- [2. Configure the OIDC-based integration in PingFederate.](#configure-oidc-integration)
- [3. Provision users for ZIdentity.](#provision-oidc-users)
- []Log in to the Admin Portal.
- Go to **Administration > Identity > ZIdentity > External Identities**.
-
Click** Add Primary IdP** (or **Add Secondary IdP**).
The **Add** **Primary Identity Provider **(or **Add Secondary** **Identity Provider**) window appears.
- In the **Add Primary Identity Provider **(or **Add Secondary Identity Provider**) window, on the **Basic **tab:
-
In the **General **section:
- **Name**: Enter a name for the IdP.
- **Identity Vendor**: Select **PingFederate **from the drop-down menu.
- **Domain**: Select the domain for which the IdP is responsible for authenticating the users. This allows the Zscaler service to display the correct IdP to authenticate an incoming user.
- **Protocol**: Select **OIDC**.
- **Status**: Select **Enabled**.
-
**Login ID Attribute**: Enter an attribute whose value must be used as the login ID. This attribute must exist in the tokens received from the IdP. By default, the `preferred_username` attribute is populated in this field when the **OIDC **option is selected in the **Protocol** field. You can use any attribute that is present in the ID token or UserInfo response, provided its value is in the email address format (e.g., <user_name>@domain.com>).
- Ensure that the domain part of the email addresses received in the ID tokens match with one of the domains configured in ZIdentity.
- Ensure that the attribute you enter matches exactly with the attribute in the ID token or UserInfo endpoint.
-
**Enforce Zscaler Admin MFA**: Enable this option to ensure that admins using an external IdP authenticate with the multi-factor authentication (MFA) process in ZIdentity, irrespective of whether MFA is configured on the external IdP.
An email is sent to all super admins in ZIdentity when the **Enforce Zscaler Admin MFA **option is disabled.
[See image.](#oidc-zidentity-basic)
-
In the **OIDC Configuration** section:
- **Input Method**: Select **Metadata URL**.
-
**Metadata URL**: Enter the PingFederate server's OIDC well-known URL and click **Fetch**.
- The format for the OIDC well-known URL is `https://<host>/.well-known/openid-configuration`.
- An example URL is `https://pingfederate.example.com/.well-known/openid-configuration`.
- You can obtain the metadata path from the PingFederate Admin Console. To do this, log in to the PingFederate Admin Console, click the **Help **icon in the top-right corner, select **OAuth Endpoints**, and locate the **OpenID Connect Metadata Endpoint** field.
[See image.](#metadata-url-pingfed-console)
- **Redirect URI: **Copy this value because it is used in a subsequent step.
- **Client ID**: Enter a random value. The actual client ID is generated while configuring a client for ZIdentity in the PingFederate Admin Console in a subsequent step. This random value entered in the field is replaced later with the actual client ID.
- **Client Secret**: Enter a random value. This value is manually overridden in a subsequent step. The actual client secret is generated while configuring a client for ZIdentity in the PingFederate Admin Console in a subsequent step. This random value entered in the field is replaced later with the actual client secret.
- In the **Requested Scopes** section, add required scopes. By default, when the OIDC protocol is selected, the `openid`, `email`, and `profile` scopes are added.
[See image.](#oidc-zidentity-configuration)
- Click **Save**.
- []Log in to the PingFederate Admin Console.
- Go to **Applications **> **OAuth **> **Client**.
-
Click **Add Client**.
[See image.](#add-client-oidc)
- On the **Client **configuration page:
- **Client ID**: Enter a custom client ID for the application.
- **Client Name**: Enter a name for the application.
- **Client Authentication**: Select the **Client Secret** option.
-
**Client Secret**: Select **Change Secret **and enter a custom value as client secret or click **Generate Secret **to generate a value automatically.
[See image.](#client-configuration-one)
- **Redirect URIs**: Enter the redirect URI copied from the Admin Portal, and click **Add**.
- **Bypass Authorization Approval**: Select **Bypass**.
- **Allowed Grant Types**: Select **Authorization** **Code**.
-
**Default Access Token Manager**: Select the access token manager that must be configured for the client from the drop-down menu. You must have configured an access token manager as mentioned in the prerequisites.
[See image.](#client-configuration-two)
- Click **Save**.
- In the Admin Portal, go to **Administration > Identity > ZIdentity > External Identities**.
-
Locate the IdP created for PingFederate on the **Primary Identity Provider** (or **Secondary Identity** **Provider**) table, and click the **Edit **icon.
The **Edit Primary Identity Provider** (or **Edit** **Secondary Identity Provider**) window appears.
- In the **Edit Primary IdP **(or **Edit Secondary IdP**) window:
-
On the **Basic **tab, under the **OIDC **Configuration section:
- **Client ID**: Override the previously configured random value with the actual client ID of the application created in the PingFederate Admin Console.
- **Client Secret**: Override the previously configured random value with the actual client secret of the application created in the PingFederate Admin Console.
[See image.](#replace-secrets-oidc)
- Click **Update**.
-
In the PingFederate Admin Console, go to **System **> **OAuth Settings **> **Scope Management**.
The **Scope Management **page appears.
-
On the **Scope Management **page, go to the **Common Scopes **tab, and click **Add Common Scope.**
[See image.](#add-common-scope-button)
The **Add Common Scope** page appears.
-
On the **Add Common Scope **page, enter `email` in the **Name **field, add a description, and click **Save**. Repeat the steps for adding a common scope to add `profile` and `openid` as common scopes.
[See image.](#add-common-scope-window)
The required scopes are added.
[See image.](#all-common-scopes)
- Go to **Applications **> **OAuth **> **OpenID Connect Policy Management**.
-
Click the policy name and go to the **Attribute Contract **tab. A policy must have been configured already. To learn more, refer to the [PingFederate documentaion](https://docs.pingidentity.com/pingfederate/latest/administrators_reference_guide/pf_configuring_oidc_policies.html).
[See image.](#openid-policy)
-
Add the required attributes by entering the attribute value, and clicking **Add**. The following image contains a reference table that provides a sample list of attributes for reference.
[See image.](#attribute-contract-tab)
- Select the **Attributes Scopes **tab.
-
Map the common scopes configured previously with the required attributes.
[See image.](#attribute-scopes-tab)
-
Select the **Contract Fulfillment** tab, and map the attributes with the appropriate values.
[See image.](#contract-fulfillment-tab)
- Select the **Summary **tab, and click **Save**.
- [][Provisioning via JIT](#oidc-jit-provisioning)
- [Provisoning via SCIM](#oidc-scim-provisioning)
- []In the Admin Portal, go to **Administration > Identity > ZIdentity > External Identities**.
- Locate the IdP entry created for PingFederate under the **Primary Identity Provider **(or **Secondary Identity Providers**) tab and click the **Edit **icon.
-
In the** Edit Primary IdP** (or **Edit Secondary IdP**) window:
- Select the **Provisioning **tab, and select **Enable Just-in-time (JIT) Provisioning**.
-
Enter `groups` as the **Just-in-time User Group Attribute** and map the `Primary Email` User Attribute with the `email` JIT User Attribute.
The mapping of the `Primary Email` attribute is mandatory as it is required for functionalities, such as password resetting and multi-factor authentication.
-
Map other ZIdentity user attributes with the appropriate PingFederate attributes as necessary. By default, the following attributes in ID tokens are mapped with the corresponding user attributes in ZIdentity:
| Attribute in ID Tokens | Default ZIdentity User Attributes |
| ---------------------- | --------------------------------- |
| given_name | First Name |
| family_name | Last Name |
| name | Display Name |
- If the external IdP is configured to send different attributes for `First Name`, `Last Name`, or `Display Name`, then you must map those attributes. For example, if the ID token from the external IdP includes `Surname` instead of `family_name`, then you must map it with the `Last Name` user attribute in ZIdentity. [See image.](#token-sample-jit-oidc)
- While mapping attributes, ensure that the attributes that you enter in the **Just-in-time Attribute** field match exactly with the attributes that would be received in the ID tokens.
[See image.](#jit-oidc-provisioning)
- Click **Update**.
- []In the Admin Portal, go to **Administration > Identity > ZIdentity > External Identities**.
- Locate the IdP entry created for PingFederate under the **Primary Identity Provider **(or **Secondary Identity Providers**) tab, and click the **Edit **icon.
- In the** Edit Primary IdP** (or **Edit Secondary IdP**) window:
- Select the **Provisioning **tab.
- In the **SCIM Configuration** section:
- Select **Enable SCIM Provisioning**.
-
Copy the **SCIM Endpoint URL**. This value is used in a subsequent step.
The **SCIM Endpoint URL** field appears only if the configurations for the IdP in the **Basic** tab are completed and saved.
[See image.](#scim-endpoint-oidc-note)
- Click **Generate Token **and **Bearer Token **value. This value is used in a subsequent step.
-
(Optional) Map the SCIM attributes (e.g., `addresses`) with the corresponding ZIdentity user attribute. This mapping is required only for attributes that need to be mapped to a custom user attribute in ZIdentity. To learn more about the SCIM attributes that require custom attribute mapping, see [Understanding SCIM](/unified/understanding-scim-0).
[See image.](#scim-provisioning-oidc-zidentity)
- Click **Update**.
- In the PingFederate Admin Console, go to **Applications **> **Integration **> **SP Connections**.
-
On the **SP Connections **page, click **Create Connection**.
[See image.](#create-sp-connection-oidc)
The **SP Connection** wizard opens.
-
In the **SP Connection **wizard:
-
On the **Connection Template **tab, select **Do Not Use a Template for This Connection**, and click **Next**.
[See image.](#connection-template-tab)
-
On the **Connection Type **tab, select **Outbound Provisioning **and select **SCIM Connector **from the **Type **drop-down menu.
If the **SCIM Connector** option is not available, you must install the SCIM Provisioner. To learn more, refer to the [PingFederate documentation](https://docs.pingidentity.com/r/en-us/pingfederate-scim-connector/pingfederate_scim_connector).
[See image.](#connection-type-tab)
- Click **Next**.
-
On the **General Info** tab:
- **Partner's Entity ID (Connection ID)**: Enter the **SCIM Endpoint URL** copied from the Admin Portal.
- **Connection Name**: Enter a name for the connection.
[See image.](#general-info-tab)
- Click **Next**.
-
On the **Outbound Provisioning **tab, click **Configure Provisioning**.
[See image.](#outbound-provisioning-tab)
The **Configure Channels **wizard appears.
- In the **Configure Channels **wizard:
-
On the **Target **tab:
- **SCIM URL**: Enter the **SCIM Endpoint URL** copied from the Admin Portal.
- **SCIM Version**: Select **2.0** from the drop-down menu.
- **Authentication Method**: Select** OAuth 2 Bearer Token **from the drop-down menu.
- **Access Token**: Enter the bearer token copied from the Admin Portal.
[See image.](#target-tab)
- Click **Next**.
-
On the **Manage Channels **tab:
-
Click **Create**.
[See image.](#manage-channels-tab)
The **Channel **wizard opens.
- In the **Channel **wizard:
-
On the **Channel Info **tab:
- **Channel Name**: Enter a name for the channel.
- **Max Threads**: Set value to `1`.
- **Timeout (Secs)**: Set value to `60`.
[See image.](#channel-info-tab)
- Click **Next**.
-
On the **Source **tab, select a previously configured data store from the **Active Data Store **drop-down menu.
[See image.](#source-tab)
- Click **Next**.
- On the **Source Settings **tab, keep the default configurations, and click **Next**.
-
On the **Source Location **tab, define **Base DN**, **Group DN **for users, and** Group DN **for groups.
[See image.](#source-locations-tab)
- Click **Next**.
-
On the **Attribute Mapping **tab:
- Map **userName** field with `userPrincipalName`.
- Map any other attributes as required.
[See image.](#attribute-mapping-tab)
- On the **Activation & Summary **tab, verify the configuration and click **Done**.
- Click **Done**.
[See image.](#manage-channels-final)
- Click **Done**
- Go to the **Activation & Summary **tab, verify the **SP Connection **details and click **Done**.
The SP Connection is configured.
[See image.](#sp-connections-final)
- Go to **System **> **Data Stores**.
-
On the **Data Stores **page, click the name of the data store used for the PingFederate application.
[See image.](#data-stores-page-oidc)
- On the **LDAP Configuration **page:
- Click **Advanced **at the bottom of the page.
-
On the **LDAP Binary Attributes** tab, add `objectGUID` as the binary attribute.
[See image.](#binary-attrubte-mapping)
- (Optional) Configure sync frequency and enable logs for debugging.
- [Customize SCIM provisioning frequency](#scim-provisioning-frequency)
- [Enable logs for debugging](#enable-logs-for-debugging)
- []In the PingFederate Admin Console, go to **System **> **Server **> **Protocol Settings**.
- On the **Protocol Settings **page, go to the **Outbound Provisioning**.
-
On the **Outbound Provisioning **tab, customize the **Synchronization Frequency**.
[See image.](#scim-sync-frequency-oidc)
- Click **Save**.
- []In the PingFederate Admin Console, go to **System **> **Server **> Log Settings.
-
On the **Log Settings **page, enable **Debug logging for core components**.
[See image.](#log-settings-oidc)
- Click **Save**.
[]![Configuring basic information for an IdP in ZIdentity](/downloads/zidentity/integration/external-idp-configuration/configuring-pingfederate-external-idp/Basic-tab.png)
[]![Obtaining the path for well-known URL in PingFederate Admin Console](/downloads/zidentity/integration/external-idp-configuration/configuring-pingfederate-external-idp/zidentity-metadata-url-path.png)
[]![Configuring OIDC options in the ZIdentity Admin Portal with a specifc options highlighted](/downloads/zidentity/integration/external-idp-configuration/configuring-pingfederate-external-idp/zidentity-pingfed-oidc-configuration_0.png)
[]![Clients page in PingFederate Admin Console with the option to add a client highlighted](/downloads/zidentity/integration/external-idp-configuration/configuring-pingfederate-external-idp/zidentity-add-client-id-oidc-pingfed.png)
[]![Configuring an OAuth client in PingFederate Admin Console](/downloads/zidentity/integration/external-idp-configuration/configuring-pingfederate-external-idp/zidentity-client-configuration-one.png)
[]![Confiuring an OAuth client in PingFederate Admin Console with various options highlighted](/downloads/zidentity/integration/external-idp-configuration/configuring-pingfederate-external-idp/zidentity-client-configuration-two.png)
[]![Configuring clinet ID and client secret in ZIdentity Admin Portal](/downloads/zidentity/integration/external-idp-configuration/configuring-pingfederate-external-idp/zidentity-oidc-pingfed-id-secret-replace.png)
[]![Scope management page in PingFederate Admin Console with the option to add a new scope highlighted](/downloads/zidentity/integration/external-idp-configuration/configuring-pingfederate-external-idp/zidentity-add-scommon-scope-option-oidc-pingfed.png)
[]![Adding a common scope in PingFederate Admin console](/downloads/zidentity/integration/external-idp-configuration/configuring-pingfederate-external-idp/zidentity-add-common-scope-window.png)
[]![Configuring common scope in PingFederate Admin Console](/downloads/zidentity/integration/external-idp-configuration/configuring-pingfederate-external-idp/zidentity-oid-ping-fed-all-common-scopes.png)
[]![OIDC policy management page in PingFederate Admin Console](/downloads/zidentity/integration/external-idp-configuration/configuring-pingfederate-external-idp/zidentity-oidc-policy-pingfed.png)
[]![Configuring attribute contact for a policy in PingFederate Admin Console](/downloads/zidentity/integration/external-idp-configuration/configuring-pingfederate-external-idp/zidentity-attribute-contract-tab-add.png)
[]![Configuring attribute scopes for a policy in OingFederate Admin Console](/downloads/zidentity/integration/external-idp-configuration/configuring-pingfederate-external-idp/zidentity-attribute-scopes-tab.png)
[]![Conifgurinf contract fulfillment in PingFederate Admin Console](/downloads/zidentity/integration/external-idp-configuration/configuring-pingfederate-external-idp/zidentity-contract-fulfillment-tab.png)
[]![Sample JIT token with blurred sensitive information](/downloads/zidentity/integration/external-idp-configuration/configuring-pingfederate-external-idp/zidentity-id-token-sample_0.png)
[]![Configuring JIT provisioning in ZIdentity](/downloads/zidentity/integration/external-idp-configuration/configuring-pingfederate-external-idp/zidentity-jit-pingfed-oidc.png)
[]![Configuring SCIM provisoning in ZIdentity with the SCIM Endpoint URL highlighted](/downloads/zidentity/integration/external-idp-configuration/configuring-pingfederate-external-idp/zidentity-scim-endpoint-url-oin-okta%20(1).png)
[]![Configuing SCIM provisioning in ZIdentity Admin Portal](/downloads/zidentity/integration/external-idp-configuration/configuring-pingfederate-external-idp/zidentity-scim-saml-oin.png)
[]![SP Connections page in PingFederate Admin Console with the option to create a connection highlighted](/downloads/zidentity/integration/external-idp-configuration/configuring-pingfederate-external-idp/zidentity-create-sp-connection.png)
[]![Configuring connection template for an SP connection in PingFederate Admin Console](/downloads/zidentity/integration/external-idp-configuration/configuring-pingfederate-external-idp/zidentity-connection-template-tab.png)
[]![Configuring connection type for an SP connection in PingFederate Admin Console](/downloads/zidentity/integration/external-idp-configuration/configuring-pingfederate-external-idp/zidentity-connection-type-tab.png)
[]![Configuring general information for an SP connection in PingFederate Admin Console](/downloads/zidentity/integration/external-idp-configuration/configuring-pingfederate-external-idp/zidentity-general-info-tab.png)
[]![Outbound provisioning tab in PingFederate Admin Console with the option to configure provisioning highlighted](/downloads/zidentity/integration/external-idp-configuration/configuring-pingfederate-external-idp/zidentity-configure-provisioning.png)
[]![Configure channels wizard in PingFederate Admin Console](/downloads/zidentity/integration/external-idp-configuration/configuring-pingfederate-external-idp/zidentity-target-tab.png)
[]![Configure channels wizard in PingFederate Admin Console with the option to create a new channel highlighted](/downloads/zidentity/integration/external-idp-configuration/configuring-pingfederate-external-idp/zidentity-manage-channels-tab.png)
[]![Configuring basic channel properties in PingFederate Admin Console](/downloads/zidentity/integration/external-idp-configuration/configuring-pingfederate-external-idp/zidentity-channel-info-tab.png)
[]![Selecting asource data store for a channel in PingFederate Admin Console](/downloads/zidentity/integration/external-idp-configuration/configuring-pingfederate-external-idp/zidentity-source-tab.png)
[]![Configuring source location for a channel in PingFederate Admin Console](/downloads/zidentity/integration/external-idp-configuration/configuring-pingfederate-external-idp/zidentity-source-location-tab.png)
[]![Attribute mapping for a channel in PingFederate Admin Console](/downloads/zidentity/integration/external-idp-configuration/configuring-pingfederate-external-idp/zidentity-attribute-mapping-tab.png)
[]![List of target channels in PingFederate Admin Console](/downloads/zidentity/integration/external-idp-configuration/configuring-pingfederate-external-idp/zidentity-manage-channels-final.png)
[]![SP Connections list in the PingFederate Admin Console with the connection highlighted](/downloads/zidentity/integration/external-idp-configuration/configuring-pingfederate-external-idp/zidentity-sp-connections-final.png)
[]![Data Stores page in PingFederate Admin Console with a data store highlighted a](/downloads/zidentity/integration/external-idp-configuration/configuring-pingfederate-external-idp/zidentity-datastore-value.png)
[]![Adding a binary attribute in PingFederate Admin Console](/downloads/zidentity/integration/external-idp-configuration/configuring-pingfederate-external-idp/zidentity-binary-attribute.png)
[]![Configuring sychronization frequency for provioning users in PingFederate Admin Console ](/downloads/zidentity/integration/external-idp-configuration/configuring-pingfederate-external-idp/zidentity-scim-frequency.png)
[]![Enabling logging for core components in PingFederate Admin Console](/downloads/zidentity/integration/external-idp-configuration/configuring-pingfederate-external-idp/zidentity-log-settings.png)
[]Prerequisites
Ensure that you have a way to integrate an authenticated identity with PingFederate through:
- IdP Adapters.
- Authentication Policies.
To learn more, refer to the [PingFederate documentation](https://docs.pingidentity.com/pingfederate/latest/administrators_reference_guide/pf_administrators_reference_guide.html).
Configuring PingFederate as IdP for ZIdentity
To set up PingFederate as an IdP for ZIdentity:
- [1. Set up PingFederate as an IdP in ZIdentity.](#set-up-pingfederate-in-zslogin)
- [2. Configure the SAML-based integration in PingFederate.](#configure-integration-saml-in-pingfederate)
- [3. Provision users for ZIdentity.](#provision-users-saml-jit-scim)
[]
- Log in to the Admin Portal.
- Go to **Administration > Identity > ZIdentity > External Identities**.
-
Click **Add Primary IdP **(or **Add Secondary IdP**).
[See image.](#add-secondary-idp-button)
The **Add Primary Identity Provider **(or **Add Secondary Identity Provider**) window appears.
-
In the **Add Primary Identity Provider **(or **Add Secondary Identity Provider**) window, on the **Basic **tab:
-
Under the **General **section:
- **Name**: Enter a name for the IdP.
- **Identity Vendor**: Select **PingFederate **from the drop-down menu.
- **Domain**: Select the domain for which the IdP is responsible for authenticating the users. This allows the Zscaler service to display the correct IdP to authenticate an incoming user.
- **Protocol**: Select **SAML**.
- **Status**: Select **Enabled**.
-
**Login ID Attribute**: Enter an attribute whose value must be used as the login ID. This attribute must exist in the token received from the IdP. By default, the `NameID` attribute is populated in this field when the **SAML** option is selected in the **Protocol** field. You can use any attribute that is present in the SAML token, provided its value is in the email address format (e.g., <user_name>@domain.com>).
- Ensure that the domain part of the email addresses received in the SAML token matches with one of the domains configured in ZIdentity.
- Ensure that the attribute you enter matches exactly with the attribute in the SAML token.
[See image.](#general-section-add-idp-window)
-
Under the **SAML Configuration **section:
- **Input Method**: Select **Metadata URL**.
-
**IdP Metadata URL**: Enter a random URL, and click **Fetch**.
The random URL is added for generating SP Metadata in the Admin Portal. This value is manually overridden in a subsequent step.
[See image.](#saml-section-add-idp-window)
- Click **Save**.
The IdP is added to the Admin Portal.
-
Locate the IdP on the **Primary Identity Provider **(or **Secondary Identity Provider**) table, and click the **Edit **icon.
[See image.](#edit-idp-button-zslogin)
The **Edit Primary Identity Provider **(or **Edit Secondary Identity Provider**) window appears.
- In the **Edit Primary Identity Provider **(or **Edit Secondary Identity Provider**) window:
-
On the **Basic **tab, under the **SAML Configuration **section, locate **SP Metadata**,** **and click **Download SP Metadata**.
[See image.](#download-sp-metadata-zslogin)
The SP Metadata is downloaded as an XML file.
-
On the **Advanced **tab:
- Enable **SAML Signing Request**.
- **Signing Algorithm**: Select the signing algorithm.
-
**SP SAML Certificate**: Click **Download Certificate**.
The **SP SAML Certificate** is downloaded.
- Enable** Encrypted SAML Assertion**.
-
**SAML Encryption Certificate**: Click **Download Certificate**.
The **SAML Encryption Certificate **is downloaded.
[See image.](#advanced-tab-idp-window)
- Click **Update**.
- []Log in to the PingFederate server.
- Go to **Applications **> **Integration **> **SP Connections**.
-
Click **Create Connection**.
[See image.](#create-connection-button-pingfederate)
The **SP Connection **wizard appears.
-
In the **SP Connection **wizard:
- On the **Connection Template **tab:
-
Select** Do Not Use a Template for This Connection**.
[See image.](#connection-templates-tab-pingfederate)
- Select **Next**.
- On the **Connection Type **tab:
-
Select **Browser SSO Profiles **as **Connection Template **and **SAML 2.0 **as **Protocol.**
[See image.](#connection-type-tab-pingfederate)
- Click **Next**.
- On the **Connection Options **tab:
-
Ensure that the **Browser SSO** option is selected.
[See image.](#connection-options-tab-pingfederate)
- Click **Next**.
- On the **Import Metadata **tab:
- **Metadata**: Select the **File **option, and click **Choose File**.
-
Upload the SP Metadata file downloaded from the Admin Portal.
[See image.](#import-metadata-tab-pingfederate)
- Click **Next**.
- On the **Metadata Summary **tab:
-
Verify the **Entity ID **value.
[See image.](#metadata-summary-tab-pingfederate)
- Click **Next**.
- On the **General Info **tab:
-
Review the connection details.
[See image.](#general-info-tab-pingfederate)
- Click **Next**.
- On the **Browser SSO **tab:
-
Click **Configure Browser SSO**.
[See image.](#browser-sso-tab-tab-pingfederate)
The **Browser SSO **wizard appears.
-
In the **Browser SSO **wizard:
- On the **SAML Profiles **tab:
-
Select **IdP-Initiated** **SSO **and **SP-Intiated SSO**.
[See image.](#saml-profiles-tab-pingfederate)
- Click **Next**.
- On the **Assertion Lifetime **tab:
- **Minutes Before**: (Optional) Modify the validity of the assertion before its issuance.
-
**Minutes After**: (Optional) Modify the validity of the assertion before its issuance.
[See image.](#assertion-lifetime-tab-pingfederate)
- Click **Next**.
- On the **Assertion Creation **tab:
-
Click **Configure Assertion Creation**.
[See image.](#assertion-creation-tab-pingfederate)
The **Assertion Creation **wizard appears.
-
In the **Assertion Creation **wizard:
- On the **Identity Mapping **tab:
-
Select **Standard**.
[See image.](#identity-mapping-tab-pingfederate)
- Click **Next**.
- On the **Attribute Contract **tab:
-
Add the attributes that you want to send to ZIdentity.
These values are included in the SAML assertion, and they must match the values on the Admin Portal.
[See image.](#attribute-contract-tab-pingfederate)
- Click **Next**.
-
On the **Authentication Source Mapping **tab, choose either to **Map New Adapter Instance** or **Map New Authentication Policy** based on your authentication configuration.
[See image.](#authentication-source-mapping-tab-pingfederate)
- Click **Next**.
- On the **Summary **tab:
-
Review the configured information.
[See image.](#summary-assertion-creation)
- Click **Done**.
The **Assertion Creation **wizard is closed, and you are redirected to the **Assertion Creation **tab in the **Browser SSO **wizard.
[See image.](#assertion-creation-tab-after-configuration)
- Click **Next**.
- On the **Protocol Settings **tab:
-
Click **Configure Protocol Settings**.
[See image.](#configure-protocol-settings-pingfederate)
The **Protocol Settings **wizard appears.
-
In the **Protocol Settings **wizard:
- On the **Assertion Consumer Service URL **tab:
-
Ensure that the **Endpoint URL **value is populated from the **SP Metadata **file uploaded to PingFederate.
[See image.](#acs-url-tab-pingfederate)
- Click **Next**.
- On the **Allowable SAML Bindings **tab:
-
Select **POST **method, and ensure that other methods are not selected.
[See image.](#allowable-saml-bindings-tab-pingfederate)
- Click **Next**.
-
On the **Signature Policy **tab, do not make any changes, and click **Next**.
[See image.](#signature-policy-tab-pingfederate)
- On the **Encryption Policy **tab:
-
(Optional) Select **The Entire Assertion **to enable an encryption policy.
If you do not want to enable an encryption policy, ensure that the **None **option is selected.
[See image.](#encryption-policy-tab-pingfederate)
- Click **Next**.
- On the **Summary **tab:
-
Review the configured information.
[See image.](#summary-protocol-settings-pingfederate)
- Click **Save**.
The **Protocol Settings **wizard is closed, and you are redirected to the **Protocol Settings **tab in the **Browser SSO **wizard.
[See image.](#protocol-settings-after)
- Click **Next**.
- On the **Summary **tab:
-
Review the configuration summary.
[See image.](#summary-browser-sso-tab-pingfederate)
- Click **Save**.
The **Browser SSO **wizard is closed, and you are redirected to the **SP Connection **wizard.
[See image.](#browser-sso-tab-after)
- Click **Next**.
- On the **Credentials **tab:
-
Click **Configure Credentials**.
[See image.](#configure-credentails-pingfederate)
The **Credentials **wizard appears.
-
In the **Credentials **wizard:
- On the **Digital Signature Settings **tab:
-
**Signing Certificate**: Select the certificate that you want to use for signing the SAML assertion from the drop-down menu. If a signing certificate is not available, you must add a new certificate to the PingFederate server. To add a new certificate, click **Manage Certificates**.
[See image.](#digital-signature-settings-tab-pingfederate)
The signing certificate is downloaded from the Admin Portal in a previous step.
- Click **Next**.
-
(Optional) On the **Select XML Encryption Certificate** tab:
If you want to encrypt assertions, select an algorithm and certificate for encryption using the following steps.
- Select an algorithm for **Block Encryption** and **Key Transport**.
-
Select a certificate. If a certificate is not available, click **Manage Certificates **to upload a new certificate.
[See image.](#xml-encryption-certificate-tab-pingfederate)
- Click **Next**.
- On the **Summary **tab:
-
Review the configuration summary.
[See image.](#summary-credentials-tab-pingfederate)
- Click **Done**.
The **Credentials **wizard is closed, and you are redirected to the **Credentials **tab in the **SP Connection **wizard.
[See image.](#credentials-wizard-pingfederate)
- Click **Next**.
- On the **Activation & Summary **tab:
-
Review the configuration summary.
[See image.](#activation-summary-tab-pingfederate)
- Click **Save**.
The **SP Connection **for ZIdentity is configured and saved.
- Ensure that the configured **SP Connection **is displayed on the **SP Connections **page.
-
Click **Select Action **for the configured SP Connection, and click **Export Metadata**.
[See image.](#export-metadata-tab-pingfederate)
The **Metadata Export **wizard appears.
-
In the **Metadata Export **wizard, on the **Export & Summary **tab, click **Export**.
[See image.](#export-summary-tab-pingfederate)
The **Metadata **file is downloaded.
- In the Admin Portal, go to **Administration > Identity > ZIdentity > External Identities**.
-
Locate the IdP on the **Primary Identity Provider **(or **Secondary Identity Provider**) table, and click the **Edit **icon.
[See image.](#edit-idp-button-zslogin-second)
The **Edit Primary Identity Provider **(or **Edit Secondary Identity Provider**) window appears.
- In the **Edit Primary Identity Provider **(or **Edit Secondary Identity Provider**) window:
-
On the **Basic **tab, under the **SAML Configuration **section:
- **Input Method**: Click **Upload Metadata**.
- **IdP Metadata**: Click **Upload IdP Metadata**.
[See image.](#saml-section-edit-idp-window)
-
Click **Update**.
This replaces the random URL entered for the** IdP Metadata URL** field in a previous step.
[]
You can provision PingFederate users for ZIdentity using just-in-time (JIT) provisioning or System for Cross-domain Identity Management (SCIM) provisioning.
- [JIT provisioning](#jit-provisioning)
- [SCIM provisioning](#scim-provisioning)
- []In the Admin Portal, go to **Administration > Identity > ZIdentity > External Identities**.
-
Locate the IdP on the **Primary Identity Provider **(or **Secondary Identity Provider**) table, and click the **Edit **icon.
[See image.](#edit-idp-button-zslogin-third)
The **Edit Primary Identity Provider **(or **Edit Secondary Identity Provider**) window appears.
-
In the **Edit Primary IdP** (or **Edit Secondary IdP**) window:
- Go to the **Provisioning **tab.
- Select **Enable Just-in-time (JIT)** Provisioning.
-
Map the ZIdentity user and group attributes with the appropriate PingFederate attributes as necessary. The mapping of the `Primary Email` attribute is mandatory as it is required for functionalities, such as password resetting and multi-factor authentication. By default, the following attributes in SAML assertions mapped with the corresponding user attributes in ZIdentity.
| Attribute in SAML Assertions | Default ZIdentity User Attributes |
| ---------------------------- | --------------------------------- |
| firstName | First Name |
| lastName | Last Name |
| displayName | Display Name |
- If the external IdP is configured to send different attributes for `First Name`, `Last Name`, or `Display Name`, then you must map those attributes. For example, if the SAML assertion from the external IdP includes `Surname` instead of `lastName`, then you must map it with the `Last Name` user attribute in ZIdentity.
-
While mapping attributes, ensure that the attributes you enter in the **Just-in-time Attribute** field match exactly with the attributes that would be received in the SAML assertions.
[See image.](#sample-saml-assertion)
[See image.](#edit-idp-window-jit)
- Click **Update**.
[]
- In the Admin Portal, go to **Administration > Identity > ZIdentity > External Identities**.
-
Locate the IdP on the **Primary Identity Provider **(or **Secondary Identity Provider**) table, and click the **Edit **icon.
[See image.](#edit-idpe-button-scim)
The **Edit Primary Identity Provider **(or **Edit Secondary Identity Provider**) window appears.
-
In the **Edit Primary IdP** (or **Edit Secondary IdP**) window:
- Go to the **Provisioning **tab.
- Select **Enable SCIM Provisioning**.
- Copy the **SCIM Endpoint URL **and **Bearer Token **value. This value is used in a subsequent step.
- (Optional) Map the SCIM attributes (e.g., `addresses`) with the corresponding ZIdentity user attribute. This mapping is required only for attributes that need to be mapped to a custom [user attribute](/unified/adding-user-attributes) in ZIdentity. To learn more about the SCIM attributes that require custom attribute mapping, see [Understanding SCIM](/unified/understanding-scim-0).
[See image.](#edit-idp-window-scim)
- Click **Update**.
- In the PingFederate server, go to **Applications **> **Integration **> **SP Connections**.
-
Locate the SP connection created for ZIdentity, and click the connection name to edit the configuration.
[See image.](#edit-sp-connection)
The **SP Connection **wizard appears.
- In the **SP** **Connection **wizard:
-
On the **Connection Type **tab, select **Outbound Provisioning **as **Connection Template**,** **and select **SCIM Connector **as **Type**.
[See image.](#edit-sp-connection-connection-type)
The **Outbound Provisioning** tab is added to the **SP Connection** wizard.
-
On the **Outbound Provisioning **tab, click **Configure Provisioning**.
[See image.](#outbound-provisioning-tab-pingfederate)
The **Configure Channels **wizard appears.
-
In the **Configure Channels **wizard:
-
On the **Target **tab:
- **SCIM URL**: Enter the **SCIM Endpoint URL **copied from the Admin Portal.
- **SCIM Version**: Select **2.0** from the drop-down menu.
- **Authentication Method**: Select **OAuth 2 Bearer Token **from the drop-down menu.
- **Access Token**: Enter the **Bearer Token **copied from the Admin Portal.
- Click **Next**.
[See image.](#target-tab-pingfederate)
- On the **Manage Channels **tab:
-
Click **Create**.
[See image.](#create-channel-button-pingfederate)
The **Channel **wizard appears.
To learn more about channels in PingFederate, refer to the [PingFederate Technical documentation](https://docs.pingidentity.com/r/en-us/pingfederate-112/help_saasmanagementtasklet_saasmanagementstate).
-
In the **Channel **wizard:
- On the **Channel Info **tab:
- **Channel Name**: Enter a name for the channel.
- **Max Threads**: Enter `1`.
-
**Timeout (Secs)**: Enter `60`.
[See image.](#channel-info-tab-pingfederate)
- Click **Next**.
- On the **Source **tab:
-
**Active Datastore**: Select the datastore from the drop-down menu.
[See image.](#source-tab-pingfederate)
- Click **Next**.
-
On the **Source Settings **tab, leave the configuration to its default settings, and click **Next**.
[See image.](#source-settings-tab-pingfederate)
- On the **Source Location **tab:
- **Base DN**: Enter the Base DN for your data store.
- Under the **Users **section:
- **Group DN**: Enter the Group DN for the users in your data store.
- Enable **Nested Search**.
-
Under the **Groups **section:
- **Group DN**: Enter the Group DN for groups in your data store.
- Enable **Nested Search**.
[See image.](#source-location-tab-pingfederate)
- Click **Next**.
- On the **Attribute Mapping **tab:
- Ensure that the **userName **filed is mapped to **userPrincipalName **attribute.
-
Map any other attributes as necessary. The mapping of the `Email` attribute is mandatory as it is required for functionalities, such as password resetting and multi-factor authentication.
[See image.](#attribute-mapping-pingfederate)
- Click **Next**.
- On the **Activation & Summary **tab:
-
**Channel Status**: Select **Active**.
[See image.](#channel-summary-tab-pingfederate)
- Click **Done**.
The **Channel **wizard is closed, and you are redirected to the **Manage Channels **tab.
[See image.](#manage-channels-pingfederate)
- Click **Done**.
The **Configure Channels** wizard is closed, and you are redirected to the **Outbound Provisioning **tab.
[See image.](#outbound-provisioning-tab-after-channel-configuration)
- Click **Next**.
-
On the **Activation & Summary **tab, review the configuration, and click **Save**.
[See image.](#configure-channels-activation-summary-pingfederate)
[]
![Option to add secondary IdP in ZSLogin](/downloads/zslogin/authentication/external-idp-configuration/configuring-pingfederate-external-idp/zidentity-add-idp_0.png)
[]
![Configuring basic Idp details in ZSLogin](/downloads/zslogin/authentication/external-idp-configuration/configuring-pingfederate-external-idp/zidentity-saml-pingfederate-basic.png)
[]
![Configuring SAML details in ZSLogin](/downloads/zslogin/authentication/external-idp-configuration/configuring-pingfederate-external-idp/zidentity-saml-configuration-pingfederate.png)
[]
![Option to edit an existing secodnary identity provider](/downloads/zslogin/authentication/external-idp-configuration/configuring-pingfederate-external-idp/zidentity-edit-idp-pingfed_0.png)
[]
![Option to download SP metadata in ZSLogin](/downloads/zslogin/authentication/external-idp-configuration/configuring-pingfederate-external-idp/zidentity-download-sp-metadata-pingfederate.png)
[]
![Configuring SAML signing options in ZSLogin](/downloads/zslogin/authentication/external-idp-configuration/configuring-pingfederate-external-idp/zidentity-idp-advanced-pingfederate.png)
[]
![SP Connections List View in PingFederate](/downloads/zslogin/authentication/external-idp-configuration/configuring-pingfederate-external-idp/zslogin-create-connection-button_0.jpg)
[]
![Connection Template in PingFederate](/downloads/zslogin/authentication/external-idp-configuration/configuring-pingfederate-external-idp/zslogin-connection-template-tab_0.jpg)
[]
![Connection Type Tab in PingFederate](/downloads/zslogin/authentication/external-idp-configuration/configuring-pingfederate-external-idp/zslogin-browser-sso_0.jpg)
[]
![Connection Options Tab in PingFederate](/downloads/zslogin/authentication/external-idp-configuration/configuring-pingfederate-external-idp/zslogin-connection-options_0.jpg)
[]
![Input Metadata Tab in PingFederate](/downloads/zslogin/authentication/external-idp-configuration/configuring-pingfederate-external-idp/zslogin-import-metadata_0.jpg)
[]
![Reviewing Entity ID details in PingFederate](/downloads/zslogin/authentication/external-idp-configuration/configuring-pingfederate-external-idp/zslogin-metadata-summary-tab.jpg)
[]
![General Info Tab in PingFederate](/downloads/zslogin/authentication/external-idp-configuration/configuring-pingfederate-external-idp/zslogin-general-info-tab_0.jpg)
[]
![Option to configure Browser SSO in PingFederate](/downloads/zslogin/authentication/external-idp-configuration/configuring-pingfederate-external-idp/zslogin-browser-sso-tab-new.jpg)
[]
![SAM Profiles Tab in PingFederate](/downloads/zslogin/authentication/external-idp-configuration/configuring-pingfederate-external-idp/zslogin-saml-profiles-tab_1.jpg)
[]
![Assertion Lifetime Tab in PingFederate](/downloads/zslogin/authentication/external-idp-configuration/configuring-pingfederate-external-idp/zslogin-assertion-lifetime_1.jpg)
[]
![Assertion Creation Tab in PingFederate](/downloads/zslogin/authentication/external-idp-configuration/configuring-pingfederate-external-idp/zslogin-assertion-creation-tab_1.jpg)
[]
![Identity Mapping Tab in PingFederate](/downloads/zslogin/authentication/external-idp-configuration/configuring-pingfederate-external-idp/zslogin-identity-mapping_1.jpg)
[]
![Attribute Contract Tab in PingFederate](/downloads/zslogin/authentication/external-idp-configuration/configuring-pingfederate-external-idp/zslogin-attribute-contract-tab.jpg)
[]
![Authentication Source Mapping Tab in PingFederate](/downloads/zslogin/authentication/external-idp-configuration/configuring-pingfederate-external-idp/acs-mapping-after-configuration.jpg)
[]
![Assertion Creation Summary Tab in PingFederate](/downloads/zslogin/authentication/external-idp-configuration/configuring-pingfederate-external-idp/zslogin-ac-summary.jpg)
[]
![Assertion Creation Tab in PingFederate](/downloads/zslogin/authentication/external-idp-configuration/configuring-pingfederate-external-idp/zslogin-assertion-creation-tab-after-configuration.jpg)
[]
![Protocol Settings Tab in PingFederate](/downloads/zslogin/authentication/external-idp-configuration/configuring-pingfederate-external-idp/zslogin-configure-protocol-settings-button.jpg)
[]
![ACS URL Tab in PingFederate](/downloads/zslogin/authentication/external-idp-configuration/configuring-pingfederate-external-idp/zslogin-acs-url-tab.jpg)
[]
![Allowable SAML Bindings Tab in PingFederate](/downloads/zslogin/authentication/external-idp-configuration/configuring-pingfederate-external-idp/zslogin-bindings-tab.jpg)
[]
![Signature Policy Tab in PingFederate](/downloads/zslogin/authentication/external-idp-configuration/configuring-pingfederate-external-idp/zslogin-encryption.jpg)
[]
![Encryption Policy Tab in PingFederate](/downloads/zslogin/authentication/external-idp-configuration/configuring-pingfederate-external-idp/zslogin-encryption-policy.jpg)
[]
![Protocol Settings Summary Tab in PingFederate](/downloads/zslogin/authentication/external-idp-configuration/configuring-pingfederate-external-idp/zslogin-protocol-settings-summary.jpg)
[]
![Protocol Settings Tab in PingFederate](/downloads/zslogin/authentication/external-idp-configuration/configuring-pingfederate-external-idp/zslogin-protocol-settings-tab-after.jpg)
[]
![Browser SSO Summary Tab in PingFederate](/downloads/zslogin/authentication/external-idp-configuration/configuring-pingfederate-external-idp/zslogin-sbrowser-sso-summary.jpg)
[]
![Browser SSO Tab in PingFederate](/downloads/zslogin/authentication/external-idp-configuration/configuring-pingfederate-external-idp/zslogin-browser-sso-tab.jpg)
[]
![Credentails Tab in PingFederate](/downloads/zslogin/authentication/external-idp-configuration/configuring-pingfederate-external-idp/zslogin-credentails-button.jpg)
[]
![Digital Signature Settings Tab in PingFederate](/downloads/zslogin/authentication/external-idp-configuration/configuring-pingfederate-external-idp/zslogin-certification-digital-settings_1.jpg)
[]
![Select XML Encryption Certificate Tab in PingFederate](/downloads/zslogin/authentication/external-idp-configuration/configuring-pingfederate-external-idp/zslogin-xml-certificate-tab.jpg)
[]
![Summary Tab under Credentails wizard in PingFederate](/downloads/zslogin/authentication/external-idp-configuration/configuring-pingfederate-external-idp/zslogin-credentails-wizard-summary.jpg)
[]
![Credentials Tab in PingFederate](/downloads/zslogin/authentication/external-idp-configuration/configuring-pingfederate-external-idp/zslogin-credentials-wizard.jpg)
[]
![SP Connection Activation & Summary in PingFederate](/downloads/zslogin/authentication/external-idp-configuration/configuring-pingfederate-external-idp/zslogin-sp-connection-summary.jpg)
[]
![Option to export metadata in PingFederate](/downloads/zslogin/authentication/external-idp-configuration/configuring-pingfederate-external-idp/zslogin-export-option-metadat.jpg)
[]
![Export & Summary Tab in PingFederate](/downloads/zslogin/authentication/external-idp-configuration/configuring-pingfederate-external-idp/zslogin-export-button-metadata.jpg)
[]
![Editing an existing IdP in ZSLogin](/downloads/zslogin/authentication/external-idp-configuration/configuring-pingfederate-external-idp/zidentity-edit-idp-pingfed_0.png)
[]
![Uploading IdP Metadat in ZSLogin](/downloads/zslogin/authentication/external-idp-configuration/configuring-pingfederate-external-idp/zidentity-metadate-upload-pingfed.png)
[]
![Editing an existing IdP in ZSLogin](/downloads/zslogin/authentication/external-idp-configuration/configuring-pingfederate-external-idp/zidentity-edit-idp-pingfed_0.png)
[]![A SAML assertion sample with blurred sensitive information.](/downloads/zidentity/integration/external-idp-configuration/configuring-pingfederate-external-idp/zidentity-saml-assertion-sample.png)
[]
![JIT attribute mapping in ZSLogin](/downloads/zidentity/integration/external-idp-configuration/configuring-pingfederate-external-idp/zidentity-saml-jit-provisioning.png)
[]
![Editing an IdP in ZSLogin Admin Portal](/downloads/zslogin/authentication/external-idp-configuration/configuring-pingfederate-external-idp/zidentity-edit-idp-pingfed.png)
[]
![Configuring SCIM provisioning in ZSLogin](/downloads/zidentity/integration/external-idp-configuration/configuring-pingfederate-external-idp/zidentity-pingfed-saml-scim-provisioning.png)
[]
![SP Connections List View](/downloads/zslogin/authentication/external-idp-configuration/configuring-pingfederate-external-idp/zslogin-connection-name_0.jpg)
[]
![Connection Type Tab with Outbound Provisionin Enabled in PingFederate](/downloads/zslogin/authentication/external-idp-configuration/configuring-pingfederate-external-idp/zslogin-outbound-enabled.jpg)
[]
![Outbound Provisionin Tab in PingFederate](/downloads/zslogin/authentication/external-idp-configuration/configuring-pingfederate-external-idp/zslogin-configure-provisioning.jpg)
[]
![Target Tab in PingFederate](/downloads/zslogin/authentication/external-idp-configuration/configuring-pingfederate-external-idp/zslogin-target-tab_1.jpg)
[]
![Manage Channels Tab in PingFederate](/downloads/zslogin/authentication/external-idp-configuration/configuring-pingfederate-external-idp/zslogin-create-channelbutton.jpg)
[]
![Channel Infor Tab in PingFederate](/downloads/zslogin/authentication/external-idp-configuration/configuring-pingfederate-external-idp/zslogin-channel-info-tab.jpg)
[]
![Source Tab in PingFederate](/downloads/zslogin/authentication/external-idp-configuration/configuring-pingfederate-external-idp/zslogin-source-tab.jpg)
[]
![Source Settings Tab in PingFederate](/downloads/zslogin/authentication/external-idp-configuration/configuring-pingfederate-external-idp/zslogin-source-settings-tab.jpg)
[]
![Source Location Tab in PingFederate](/downloads/zslogin/authentication/external-idp-configuration/configuring-pingfederate-external-idp/zslogin-source-location-tab.jpg)
[]
![Attribute Mapping Tab under Channel Wizard in PingFederate](/downloads/zslogin/authentication/external-idp-configuration/configuring-pingfederate-external-idp/zslogin-attribute-mapping-tab.jpg)
[]
![Activation & Summary Tab under Channel Wizard in PingFederate](/downloads/zslogin/authentication/external-idp-configuration/configuring-pingfederate-external-idp/zslogin-channel-activation-tab.jpg)
[]
![Manage Channels Tab in PingFederate](/downloads/zslogin/authentication/external-idp-configuration/configuring-pingfederate-external-idp/zslogin-manage-channel.jpg)
[]
![Outbound Provisioning Tab in PingFederate](/downloads/zslogin/authentication/external-idp-configuration/configuring-pingfederate-external-idp/zslogion-outbound-provisioning-after-channel-configuration.jpg)
[]
![SP Connection Activation & Summary in PingFederate](/downloads/zslogin/authentication/external-idp-configuration/configuring-pingfederate-external-idp/zslogin-summary-after-scim.jpg)
[]
During the IdP-initiated SSO for ZIdentity, tenants using OIDC or SAML protocols are redirected as follows:
- [OIDC Protocol](#OIDC-protocol-redirection)
- [SAML Protocol](#SAML-protocol-redirection)
To change the default redirection, contact [Zscaler Support](/contact-support).
[]
All admins authenticating using the SAML protocol for ZIdentity and IdP integrations are redirected to Experience Center. However, if the `zidServiceId` attribute is configured in the IdP within the ZIdentity tenant, then the admins are redirected to the ZIdentity Admin Portal instead of Experience Center.
[]
ZIdentity tenants that are enabled with Experience Center at the time of tenant creation and admins using OIDC protocol for ZIdentity and IdP integrations are redirected to the Experience Center.
ZIdentity tenants that are not enabled with Experience Center at the time of tenant creation and admins using OIDC protocol for ZIdentity and IdP integrations are redirected to the ZIdentity Admin Portal. They can click the Experience Center link and go to the Experience Center from the [ZIdentity Landing page](/zidentity/accessing-and-navigating-zidentity-landing-page).
[See image.](#ec-zidpage)
If you want to change this default behavior and have users redirected to the Experience Center, raise a Support ticket with the ticket type set to **Provisioning**.
[]
![ZIdentity Landing Page with highlighted banner at the top.](/downloads/tech-pubs-drafts/zidentity-draft-articles/draft-configuring-okta-external-idp-doc-57200/zid-landing-page-1.png)