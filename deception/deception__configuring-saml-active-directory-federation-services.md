# Configuring SAML for Active Directory Federation Services
Source: https://help.zscaler.com/deception/configuring-saml-active-directory-federation-services
PDF: https://help.zscaler.com/pdf/com/en/1531363.pdf

Zscaler recommends that you use the [ZIdentity Admin Portal](/zidentity/accessing-and-navigating-zidentity-admin-portal) to configure primary and secondary [external identity providers (IdPs)](/zidentity/about-external-identity-providers). ZIdentity supports both SAML and OpenID configurations. Contact Zscaler Support to subscribe to ZIdentity.
This article provides information on configuring Microsoft Active Directory Federation Services (ADFS) as the SAML identity provider (IdP) for the Zscaler Deception Admin Portal.
Prerequisites
Make sure the following prerequisites are met:
- Download the Federation Metadata XML file. To download the Federation Metadata XML file on the ADFS server, enter the following URL in your browser and save the file: `https://``<ADFS Sever Hostname>``/FederationMetadata/2007-06/FederationMetadata.xml`.
- Download the Metadata XML file from the Deception Admin Portal. To learn more, see [Obtaining SAML Setup Information](/deception/configuring-saml-single-sign#obtain-saml-setup-instn).
Configuring SAML for ADFS
Follow these steps to configure SAML for ADFS:
- [Step 1: Add Zscaler Deception as a Relying Party Trust](#add-zscaler-deception-relying-party-trust)
- [Step 2: Add Claim Rules](#add-claim-rule)
- [(Optional) Step 3: Configure SAML Group Provisioning for ADFS](#zd-add-group-saml-adfs)
- []Open the ADFS management application.
- In the left-side navigation panel, go to **ADFS** > **Relying Party Trusts**.
- Right-click on **Relying Party Trusts**, and click **Add Relying Party Trust Wizard** to add Zscaler Deception as a trusted party.
-
On the **Welcome** page, select **Claims aware**, and click **Start**.
[See image.](#adfs-add-claim-aware-app)
-
On the **Select Data Source** page:
- Select **Import data about the relying party from a file**.
- Browse to upload the Metadata XML file that you downloaded from the Deception Admin Portal.
- Click **Next**.
[See image.](#adfs-select-data-source)
-
On the **Specify Display Name **page, enter the display name, and then click **Next**.
[See image.](#adfs-saml-specify-display-name)
-
On the **Choose Access Control Policy **page, select **Permit everyone**, and click **Next**.
[See image.](#adfs-saml-access-control-policy)
-
On the **Ready to Add Trust **page, click **Next**.
[See image.](#adfs-saml-ready-add-trust)
-
On the **Finish** page, click **Close**.
[See image.](#adfs-saml-finish-relying-party)
A relying party trust entry is added to the **Relying Party Trusts** panel.
[See image.](#adfs-saml-rlying-trust-party-added)
- []In the **Relying Party Trusts** panel, select the [relying party trust](#add-zscaler-deception-relying-party-trust) that you created.
- Under **Actions**, click **Edit Claim Issuance Policy**.
-
In the **Edit Claim Issuance Policy** window, click **Add Rule**.
[See image.](#adfs-saml-add-claim-rule)
The **Add Transform Claim Rule Wizard** appears.
-
In the **Choose Rule Type** step, for **Claim rule template, **select **Send LDAP Attributes as Claims** from the drop-down menu, and click **Next**.
[See image.](#adfs-saml-claim-rule-template)
- In the **Configure Claim Rule** step:
- **Claim rule name**: Enter `User Principal Name`.
- **Attribute store**: Select **Active Directory** from the drop-down menu.
- **Mapping of LDAP attributes to outgoing claim types**:
- Under **LDAP Attribute**, select **User-Principal-Name **from the drop-down menu.
-
Under** Outgoing Claim Type**, select** E-Mail Address **from the drop-down menu.
[See image.](#adfs-saml-config-claim-rule)
- Click **Finish** to add the claim rule.
-
In the **Edit Claim Issuance Policy** window, click **Add Rule **to add another rule.
[See image.](#adfs-saml-add-second-rule)
The **Add Transform Claim Rule Wizard** that appears.
-
In the **Choose Rule Type** step, for **Claim rule template, **select **Transform an Incoming Claim **from the drop-down menu, and click **Next**.
[See image.](#adfs-saml-second-rule-template)
- In **Edit Rule - Email **window:
- **Claim rule name**: Enter `Email`.
- **Incoming claim type**: Select **E-Mail Address** from the drop-down menu.
- **Outgoing claim type: **Select **Name ID** from the drop-down menu.
- **Outgoing name ID format**: Select **Email** from the drop-down menu.
- Select **Pass through all claim values**.
-
Click **OK**.
[See image.](#adfs-saml-config-second-claim-rule)
-
When the **Edit Claim Issuance Policy** window displays the newly added claim rule in the list, click **Apply**, then click **OK** to save the rule.
[See image.](#adfs-saml-claim-rules-added)
After the configuration, sign in to the Deception Admin Portal page. You will see the identity provider's login button. Sign in with the SAML provider to verify if the integration is successful.
- []In the **Relying Party Trusts** panel, select the [relying party trust](#add-zscaler-deception-relying-party-trust) that you created.
- Under **Actions**, click **Edit Claim Issuance Policy**.
-
In the **Edit Claim Issuance Policy** window, click **Add Rule**.
[See image.](#deception-saml-group-add-claim-rule)
The **Add Transform Claim Rule Wizard** appears.
-
In the **Choose Rule Type** step, for **Claim rule template**, select **Send Group Membership as Claim** from the drop-down menu, and click **Next**.
[See image.](#deception-group-saml-select-claim-rule)
-
In the **Configure Claim Rule** step:
- **Claim rule name**: Enter the name of the group.
- **User's group**: Browse and select a user group.
- **Outgoing claim type**: Select **Group** from the drop-down menu.
- **Outgoing claim value**: Enter the group name.
[See image.](#deception-group-saml-adfs-config-claim-rule)
- Click **Finish**.
- Repeat the previous steps for each group you want to add.
-
In the **Edit Claim Issuance Policy** window, click **Add Rule**.
[See image.](#deception-group-saml-add-claim-rule-1)
-
In the **Choose Rule Type** step, for **Claim rule template**, select **Send LDAP Attributes as Claims** from the drop-down menu, and click **Next**.
[See image.](#deception-saml-adfs-claim-template-ldap)
- In the **Configure Claim Rule** step:
- **Claim rule name**: Enter `Name`.
- **Attribute store**: Select **Active Directory** from the drop-down menu.
-
In **Mapping of LDAP attributes to outgoing claim types**:
- **LDAP Attribute**: Select **Given-Name** from the drop-down menu.
- **Outgoing Claim Type**: Select **Name** from the drop-down menu.
[See image.](#deception-group-saml-config-claim-rule-ldap)
- Click **Finish**.
-
In the **Edit Claim Issuance Policy** window, click **Apply**.
[See image.](#deception-group-saml-adfs-apply-claim-rule-policy)
- Obtain the SAML Response Group Attribute value:
-
In the **Edit Claim Issuance Policy** window, select the group claim you created, and click **Edit Rule**.
[See image.](#deception-group-saml-edit-claim-rule)
-
In the **Edit Rule** window, click **View Rule Language**.
[See image.](#deception-group-saml-adfs-view-claim-lan)
The SAML Response Group Attribute is the value of the **Type** variable in the **issue** section.
[See image.](#deception-group-saml-adfs-attribute-value)
- Click **OK**.
-
Obtain the SAML Response Name Attribute value:
-
In the **Edit Claim Issuance Policy** window, select **Name**,** **and click **Edit Rule**.
[See image.](#deception-group-saml-adfs-edit-name-rule)
-
In the **Edit Rule** window, click **View Rule Language**.
[See image.](#deception-group-saml-adfs-name-view-lan)
The SAML Response Group Attribute is the value of the **Type** variable in the **issue** section.
[See image.](#deception-group-saml-adfs-name-attribute)
Use the SAML Response Group Attribute, SAML Response Name Attribute, and list of groups configured to set up [group-based SAML login](/deception/configuring-saml-single-sign#deception-obtain-saml-setup-instn).
[See image.](#deception-config-group-saml-adfs-using-attr)
[]![Add a claim aware application in ADFS](/downloads/deception/authentication/saml-configuration/configuring-saml-active-directory-federation-services/zscaler-deception-relying-party-trust-welcome.png)
[]![Upload the Metadata XML file](/downloads/deception/authentication/saml-configuration/configuring-saml-active-directory-federation-services/zscaler-deception-saml-adfs-select-data-source.png)
[]![Specify the display name](/downloads/deception/authentication/saml-configuration/configuring-saml-active-directory-federation-services/zscaler-deception-saml-adfs-specify-display-name.png)
[]![Select the access control policy](/downloads/deception/authentication/saml-configuration/configuring-saml-active-directory-federation-services/zscaler-deception-saml-adfs-select-access-control-policy.png)
[]![Select Next on the Ready to Add Trust page](/downloads/deception/authentication/saml-configuration/configuring-saml-active-directory-federation-services/zscaler-deception-saml-adfs-ready-to-add-trust.png)
[]![Complete adding relying party](/downloads/deception/authentication/saml-configuration/configuring-saml-active-directory-federation-services/zscaler-deception-saml-adfs-finish-adding-relying-trust-party.png)
[]![Relying party trust added](/downloads/deception/authentication/saml-configuration/configuring-saml-active-directory-federation-services/zscaler-deception-saml-adfs-relying-trust-party-added.png)
[]![Add a claim rule in ADFS](/downloads/deception/authentication/saml-configuration/configuring-saml-active-directory-federation-services/zscaler-deception-saml-adfs-add-rule.png)
[]![Select claim rule template](/downloads/deception/authentication/saml-configuration/configuring-saml-active-directory-federation-services/zscaler-deception-saml-adfs-select-rule-template.png)
[]![Configure claim rule ](/downloads/deception/authentication/saml-configuration/configuring-saml-active-directory-federation-services/zscaler-deception-saml-adfs-configure-claim-rule-template.png?1658730077)
[]![Add a second claim rule](/downloads/deception/authentication/saml-configuration/configuring-saml-active-directory-federation-services/zscaler-deception-saml-adfs-add-second-rule.png)
[]![Select the claim template for the second rule](/downloads/deception/authentication/saml-configuration/configuring-saml-active-directory-federation-services/zscaler-deception-saml-adfs-select-second-rule-template.png)
[]![Configure the second claim rule ](/downloads/deception/authentication/saml-configuration/configuring-saml-active-directory-federation-services/zscaler-deception-saml-adfs-edit-second-claim-rule.png)
[]![Claim rules added](/downloads/deception/authentication/saml-configuration/configuring-saml-active-directory-federation-services/zscaler-deception-saml-adfs-claim-rule-added.png)
[]![Add a claim rule](/downloads/deception/authentication/saml-configuration/configuring-saml-active-directory-federation-services/zscaler-deception-saml-group-adfs-add-rule.png)
[]![Select claim rule template](/downloads/deception/authentication/saml-configuration/configuring-saml-active-directory-federation-services/zscaler-deception-saml-group-adfs-select-claim-rule-template.png)
[]![Configuring a claim rule](/downloads/deception/authentication/saml-configuration/configuring-saml-active-directory-federation-services/zscaler-deception-saml-group-adfs-config-claim-rule-1.png)
[]![Add a claim rule](/downloads/deception/authentication/saml-configuration/configuring-saml-active-directory-federation-services/zscaler-deception-saml-group-adfs-add-rule-1.png)
[]![Select claim rule template for LDAP attributes](/downloads/deception/authentication/saml-configuration/configuring-saml-active-directory-federation-services/zscaler-deception-saml-group-adfs-select-claim-rule-template-ldap-1.png)
[]![Configure claim rule for LDAP](/downloads/deception/authentication/saml-configuration/configuring-saml-active-directory-federation-services/zscaler-deception-saml-group-adfs-config-claim-rule-ldap.png)
[]![Apply group SAML claim rule policy](/downloads/deception/authentication/saml-configuration/configuring-saml-active-directory-federation-services/zscaler-deception-saml-group-apply-claim-rule-policy.png)
[]![Edit the claim rule](/downloads/deception/authentication/saml-configuration/configuring-saml-active-directory-federation-services/zscaler-deception-saml-group-edit-claim-rule.png)
[]![View claim rule language](/downloads/deception/authentication/saml-configuration/configuring-saml-active-directory-federation-services/zscaler-deception-saml-group-view-rule-lan.png)
[]![SAML Group Attribute value](/downloads/deception/authentication/saml-configuration/configuring-saml-active-directory-federation-services/zscaler-deception-saml-group-attribute-value.png)
[]![Edit the Name claim rule](/downloads/deception/authentication/saml-configuration/configuring-saml-active-directory-federation-services/zscaler-deception-saml-group-adfs-name-edit-rule.png)
[]![View rule language for the Name claim](/downloads/deception/authentication/saml-configuration/configuring-saml-active-directory-federation-services/zscaler-deception-saml-group-name-view-rule-lan.png)
[]![View SAML Response Name Attribute value](/downloads/deception/authentication/saml-configuration/configuring-saml-active-directory-federation-services/zscaler-deception-saml-group-name-attribute-value.png)
[]![Configuring group SAML for ADFS](/downloads/deception/authentication/saml-configuration/configuring-saml-active-directory-federation-services/zscaler-deception-saml-group-adfs-config-2.png)