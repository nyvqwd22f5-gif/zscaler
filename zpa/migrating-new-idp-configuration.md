# Migrating to a New IdP Configuration
Source: https://help.zscaler.com/zpa/migrating-new-idp-configuration
PDF: https://help.zscaler.com/pdf/com/en/1507641.pdf

This guide contains information on how to migrate from one identity provider (IdP) to another in the ZPA Admin Portal. Zscaler recommends editing the existing IdP to migrate to a new IdP. Adding a new IdP for migration can duplicate groups and departments, and your existing policies might no longer apply.
Prerequisites
Before you migrate an IdP, ensure that the following prerequisites are met:
- Ensure that the same user data (Groups, Users, Departments) are present in both IdPs.
- Ensure that the SAML and SCIM mapping attributes match in both IdPs.
-
For SAML, ensure that the NameID mapping is defined the same way in both IdPs. If you define NameID with the email or UPN attribute, ensure that the expression is the same in both IdPs. For example, see the following SAML assertion:
`<saml:Attribute Name="NameID" Format="urn:oasis:names:tc:SAML:1.1:nameid-format:emailAddress">
<saml:AttributeValue>user@example.com</saml:AttributeValue>
</saml:Attribute>`
-
For SCIM, ensure that the userName mapping is defined the same way in both IdPs. If you define userName with the email or UPN attribute, ensure that the expression is the same in both IdPs. For example, see the following payload:
`json
{
"schemas": ["urn:ietf:params:scim:schemas:core:2.0:User"],
"userName": "user@example.com",
...
}`
Migrating to a New IdP
The following methods are supported for migrating to a new SAML or SCIM IdP configuration:
- [Editing an Existing IdP and Migrating to a New IdP](#EditAndMigrate)
- [Migrating to a New IdP](#MigrateNewIdP)
Zscaler recommends you are aware of the following:
- Users logged in to the ZPA service during the migration see an authentication error message in Zscaler Client Connector and must reauthenticate to regain access. To ensure that this happens, [configure a timeout policy](/zpa/configuring-timeout-policies) for users to authenticate after the IdP configuration changes. Reauthentication is required to apply the new SAML attributes.
- If **SCIM Attributes for Policy** is enabled and users are not provisioning to the ZPA Admin Portal via SCIM, then the users cannot log in to the ZPA service using Zscaler Client Connector. [Add the users to the ZPA Admin Portal via SCIM](/zpa/enabling-scim-identity-management).
- Privileged Remote Access (PRA)- and browser-based authenticated sessions still require users to reauthenticate. Zscaler recommends creating a [timeout policy](/zpa/about-timeout-policy) to authenticate early (e.g., trigger the reauthentication by creating a timeout policy rule with the rule order set to 1, and with the reauthentication value set to less than 1 hour).
[]Edit the existing IdP to avoid recreating policies in ZPA that reference the SAML or SCIM attributes. This minimizes disruption to existing access policies and configurations.
Zscaler recommends this method to migrate to a new SAML or SCIM IdP configuration.
To edit an existing IdP configuration and migrate to a new IdP configuration:
- Go to **Authentication **> **User Authentication** > **IdP Configuration**.
-
[]Expand the IdP you want to modify in the table and click **Download Metadata**.
[See image.](#spMetadata)
If the IdP doesn't support the option to download the service provider metadata, you can copy the **Service Provider URL** and **Service Provider Entity ID**, and download the **Service Provider Certificate **(if the SAML request is enabled) to be used for IdP configurations.
-
Click the **Edit **icon for the IdP.
The **Edit IdP Configuration** window appears.
-
In the **Edit IdP Configuration **window:
- Copy the **SCIM Service Provider Endpoint**.
- Copy the token. If the token wasn't saved, click **Generate New Token** to generate a new token.
[See image.](#editIdPconfiguration)
- [][Configure a new IdP](/zpa/configuring-idp-single-sign) using the [metadata captured](#metadata). Verify that values for users, groups, and departments are the same in both IdPs to avoid any effects on ZPA policies based on users, groups, or departments.
- After the new IdP is configured, update the IdP configuration with the metadata from the new IdP. If the IdP doesn't have the option to download the metadata, then manually update the **Single Sign-On URL**, **IdP Entity ID**, and **IdP Certificate**.
-
Click **Save**.
A **Warning** window appears asking if you want to continue.
[See image.](#WarningConfirmation)
- Click **Continue Anyway**.
-
Click the **Edit **icon for the new IdP configuration.
The **Edit IdP Configuration** window appears.
- In the **Edit IdP Configuration** window, enable **SCIM Sync** to update the user data in the ZPA Admin Portal.
- Copy the list of attributes from the new IdP.
- Go to **Authentication **> **User Authentication** > **SAML Attributes**.
-
[Edit and replace the SAML attributes](/zpa/editing-saml-attributes) within the table so that they correspond to the attributes from the new IdP.
The following is an example of the SAML attributes before switching to the new IdP configuration.
[See image.](#SamlAttributesPreNewIdP)
The following is an example of the SAML attributes after copying the list of attributes to the [new IdP configuration](#newIdP).
[See image.](#SamlAttributesPostCopy)
Zscaler recommends updating all SAML Attribute names from the new IdP, including the attributes that are used in the policies, to ensure that existing policies continue to work without disruption. If the attribute name coming from both IdPs is the same, then this step is not required.
Validating Migration
To validate that the IdP migration is successful:
-
Reauthenticate against the new IdP to get the updated SAML assertion. Verify that users can authenticate by having them log out and log back in to Zscaler Client Connector.
Reauthentication does not happen automatically post-IdP migration until Zscaler Client Connector reconnects to the ZPA Public Service Edge, or until the user triggers a timeout policy that requires them to reauthenticate. This happens when the user performs one of the following actions:
- On the **Private Access **tab** **within Zscaler Client Connector, click **Off** and then click **On**.
- Exit and relaunch Zscaler Client Connector from the taskbar.
- Restart services in Zscaler Client Connector.
- On the **Private Access **tab** **within Zscaler Client Connector, click **Authenticate Early**.
- Create a [timeout policy](/zpa/about-timeout-policy) to authenticate early (e.g., trigger the reauthentication by creating a timeout policy rule with the rule order set to 1, and with the reauthentication value set to less than 1 hour).
- Verify that all existing policies with SAML or SCIM attributes are working as expected.
- Ensure users can access all applications and get correct policies.
Fallback Steps
To revert the configuration changes in the ZPA Admin Portal for fallback:
- [Add the IdP configuration](/zpa/configuring-idp-single-sign) from the previous IdP that was used before migration.
- [Enable SCIM Sync](/zpa/enabling-scim-identity-management) for the previous IdP configuration that was used before migration.
- Ensure users can log in and that policies are working as expected.
[]Prior to migrating to a new IdP configuration, you must create two IdP configurations to perform the migration. The two additional IdP configurations are considered dummy domains that are separate from the domain that is configured with the existing IdP, and separate from the IdP configuration that is planned to be migrated to the new IdP. The steps in this procedure use the following example IdP configurations:
- IdP 1: Includes a dummy domain (domain1.com) and a domain (domain2.com) to authenticate users.
- IdP 2: Includes a dummy domain (domain3.com) and is used post-migration for the IdP configuration.
After you create the two IdP configurations with the dummy domains, proceed to migrate to a new IdP configuration. Zscaler recommends using this migration method when [editing an existing IdP and migrating to a new IdP](#EditAndMigrate) does not work (e.g., when an existing IdP is being used for both admins and users).
To migrate to a new IdP configuration:
- [Configure a new IdP.](/zpa/configuring-idp-single-sign#Collapse2)
- [Set up your IdP and specify ZPA as the service provider.](/zpa/configuring-idp-single-sign#Collapse1)
- [Enable SCIM Sync and SCIM Attributes for policy](/zpa/enabling-scim-identity-management) to configure the SCIM integration between the ZPA service and the new IdP configuration.
- Ensure the new IdP is configured with all the SAML and SCIM attributes that are referenced in the ZPA policies to avoid any issues with policies. For example, Groups, Departments, Email, and Name attributes must be the same for both ZPA and for the new IdP for both SAML and SCIM.
- [Import the SAML attributes.](/zpa/importing-saml-attributes)
- Save the configuration in the ZPA Admin Portal.
- Start the SCIM sync from the IdP to update the user data in the ZPA Admin Portal.
- Wait for the IdP to finish the provisioning.
-
Edit the [access policies](/zpa/editing-access-policies), [timeout policies](/zpa/editing-timeout-policies), and [client forwarding policies](/zpa/editing-client-forwarding-policies) and add the same SCIM and SAML attributes from IdP 2 so that they have the same attributes from IdP 1.
[See image.](#saml-scim-attributes-in-policies)
An error message appears in Zscaler Client Connector if an admin accesses the application while this step is in progress.
[See image.](#FailedIdpVerificationClientConnector)
- Remove domain2.com from IdP 1.
- Add domain2.com to the newly created IdP configuration (IdP 2).
Ensure the existing IdP configuration is enabled and not modified in ZPA or on the IdP for a few days. The existing IdP can be decommissioned after you have validated that there aren't any observable issues post-migration.
Validating Migration
To validate that the IdP migration is successful:
- Verify that users can authenticate by using one of the following actions:
- On the **Private Access **tab** **within Zscaler Client Connector, click **Off** and then click **On**.
- Exit and relaunch Zscaler Client Connector from the taskbar.
- Restart services in Zscaler Client Connector.
- On the **Private Access **tab** **within Zscaler Client Connector, click **Authenticate Early**.
- Create a [timeout policy](/zpa/about-timeout-policy) to authenticate early (e.g., trigger the reauthentication by creating a timeout policy rule with the rule order set to 1, and with the reauthentication value set to less than 1 hour).
- Ensure users can access all applications and get correct policies.
- Verify that all existing policies with SAML or SCIM attributes are working as expected.
Fallback Steps
To revert the configuration changes in the ZPA Admin Portal for fallback:
- Remove the domain2.com dummy domain from IdP 2.
- Add the domain2.com dummy domain to IdP 1.
- Reauthenticate again to authenticate against IdP 1.
- Ensure the correct policies are being evaluated by ZPA using one of the following actions:
- Restart services in Zscaler Client Connector.
- Turn off and then turn on Private Access in Zscaler Client Connector.
- Log out and then log in to Zscaler Client Connector.
- [Enable SCIM Sync](/zpa/enabling-scim-identity-management) for the previous IdP configuration that was used before migration.
- Ensure users can log in and that policies are working as expected.
[]![Downloading the SP metadata](/downloads/zpa/authentication/saml-attributes/migrating-new-idp-configuration/zpa-sp-metadata.png)
[]![Viewing the Edit IdP Configuration window](/downloads/zpa/authentication/saml-attributes/migrating-new-idp-configuration/zpa-edit-idp-config-window2.png)
[]![Warning Error when Updating an IdP Configuration ](/downloads/zpa/authentication/saml-attributes/migrating-new-idp-configuration/zpa-edit-IdP-configuration-metadata-confirmation-warning.png)
[]![SAML Attributes Page Before Switching to the New IdP](/downloads/zpa/authentication/saml-attributes/migrating-new-idp-configuration/zpa-saml-attributes-pre-new-idp.png)
[]![SAML Attributes Page within the ZPA Admin Portal After Copying the Attributes](/downloads/zpa/authentication/saml-attributes/migrating-new-idp-configuration/zpa-saml-attributes-post-copy2.png)
[]![Viewing the SAML and SCIM Attributes Criteria in an expanded Policy](/downloads/zpa/authentication/saml-attributes/migrating-new-idp-configuration/zpa-saml-scim-attributes-expanded-view-policies-page.png)
[]![Failed IdP Verification Error in Zscaler Client Connector](/downloads/zpa/authentication/saml-attributes/migrating-new-idp-configuration/zscaler-client-connector-idp-verification-error.png)