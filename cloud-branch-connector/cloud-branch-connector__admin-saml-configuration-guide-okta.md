# Admin SAML Configuration Guide for Okta
Source: https://help.zscaler.com/cloud-branch-connector/admin-saml-configuration-guide-okta
PDF: https://help.zscaler.com/pdf/com/en/1420891.pdf

This guide demonstrates how to configure Okta as the identity provider for Zscaler Cloud & Branch Connector and use [SAML single sign-on (SSO) for admins](/cloud-branch-connector/accessing-administrator-management). To learn more about the steps in the Okta portal, refer to the [Okta documentation](https://help.okta.com/).
Prerequisites
Ensure that you have the following before configuring Okta:
- Okta account with admin privileges.
- [Zscaler cloud name](/cloud-branch-connector/what-my-cloud-name-zscaler-cloud-branch-connector).
- [Admin accounts created for your organization's admins](/cloud-branch-connector/adding-admins).
If you are subscribed to ZIdentity, some of the following options are only configurable within the ZIdentity Admin Portal. To learn more, see [What Is ZIdentity?](/zidentity/what-zidentity)
Configuring Admin SAML SSO with Okta
To configure Okta as the IdP for Cloud & Branch Connector and use SAML SSO for admins:
- [Step 1: Add the Zscaler Cloud and Branch Connector Administrator Application](#AddCloudandBranchAdminApp)
- [Step 2: Configure the SAML Admin SSO in Okta](#ConfiguringOkta)
- [Step 3: Configure SAML Admin SSO in the Cloud & Branch Connector Admin Portal](#ConfiguringinPortal)
- []Log in to [Okta](https://www.okta.com/login/).
-
On the left-side navigation, select **Applications**, then click **Applications**.
[See image](#Okta1B)
-
Click **Create App Integration**.
[See image.](#Okta1C)
-
Select **SAML 2.0**, then click **Next**.
[See image.](#Okta1D)
-
On the **Create SAML Integration** page, under **General settings**, enter `Zscaler Cloud and Branch Connector Administrator Application` as the **App name**, then click **Next**.
[See image.](#Okta1E)
-
In SAML Settings, enter the following for **Single sign on URL** and **Audience URI (SP Entity ID)**, respectively:
`https://connector.<Zscaler Cloud>.net/bac-adminsso.do``admin.<Zscaler Cloud>.net`
To learn more, see [What Is My Cloud Name for Zscaler Cloud & Branch Connector?](/cloud-branch-connector/what-my-cloud-name-zscaler-cloud-branch-connector)
[See image.](#Okta1F)
Click **Next**.
-
In **Help Okta Support understand how you configured this application**, select **I'm an Okta customer adding an internal app**.
[See image.](#Okta1G)
- Click **Finish**. Okta redirects you to the **Zscaler Cloud and Branch Connector Administrator Application** page.
[]
-
On the **Zscaler Cloud and Branch Connector Administrator Application** page, click **Assignments**.
[See image.](#Okta2A)
-
Click **Assign**, then select **Assign to people**.
[See image.](#Okta2B)
-
In the **Assign Zscaler Cloud and Branch Connector Administrator Application to People** window, select the admins you want to assign to the application.
[See image.](#Okta2C)
Okta redirects you to a new window.
-
Click **Save and Go Back**.
[See image.](#Okta2Ci)
- Click **Done**.
-
On the **Zscaler Cloud and Branch Connector Administrator Application** page, click **Sign On**.
[See image.](#Okta2D)
-
Under **SAML Setup**, click **View SAML setup instructions**.
[See image.](#Okta2E)
-
On the **How to Configure SAML 2.0 for Zscaler Cloud and Branch Connector Administrator Application** page, copy the **Identity Provider Issuer**.
[See image.](#Okta2F)
Under **X.509 Certificate**, click **Download certificate**.
[See image.](#Okta2Fi)
Okta downloads the certificate as a `.cert`, but the Zscaler Cloud & Branch Connector Admin Portal supports only `.cer` or `.pem` files. Ensure that the file is converted before uploading it to the portal.
[]
- In the portal, go to **Administration** > **Administrator Management** > **Administrators Management**.
-
In the **SAML Authentication for Administrators** section, under **IdP SAML Certificate**, click **Upload**.
[See image.](#Okta3B)
-
In the **IdP SAML Certificate** window, click **Choose File** and upload the certificate, then click **Upload** when complete.
[See image.](#Okta3C)
-
Under **Issuer**, paste the **Identity Provider Identifier** you copied from Okta, then click **Add Items**.
[See image.](#Okta3D)
-
Enable SAML Authentication.
[See image.](#Okta3E)
- Click **Save **and [activate the changes](/cloud-branch-connector/saving-and-activating-changes).
Testing the Admin SAML SSO
To test the SAML admin SSO, you can initiate the SAML connection from the Zscaler Cloud and Branch Connector Administrator Application.
-
On your Okta Dashboard, click the Four Square icon in the top right corner.
[See image.](#OktaTest1)
-
In **Okta Apps**, click **My end user dashboard**.
[See image.](#OktaTest2)
Okta redirects you to **My Apps**.
-
In the **Work** section, click **Zscaler Cloud and Branch Connector Administrator Application**. You are automatically signed in to the Zscaler Cloud & Branch Connector Admin Portal.
[See image.](#OktaTest3)
[]![Applications in Okta](/downloads/tech-pubs-drafts/cloud-connector-draft-articles/admin-saml-configuration-guide-okta-draft-doc-51903/Okta1B.png)
[]![Create App Integration in Okta](/downloads/tech-pubs-drafts/cloud-connector-draft-articles/admin-saml-configuration-guide-okta-draft-doc-51903/Okta1C.png)
[]![SAML 2.0 in Okta](/downloads/tech-pubs-drafts/cloud-connector-draft-articles/admin-saml-configuration-guide-okta-draft-doc-51903/Okta1D.png)
[]![App name set to Zscaler Cloud and Branch Connector Administrator Application in Okta](/downloads/tech-pubs-drafts/cloud-connector-draft-articles/admin-saml-configuration-guide-okta-draft-doc-51903/Okta1E.png)
[]![SAML SSO URL in Okta](/downloads/tech-pubs-drafts/cloud-connector-draft-articles/admin-saml-configuration-guide-okta-draft-doc-51903/Okta1F.png)
[]![Okta Support Feedback in Okta](/downloads/tech-pubs-drafts/cloud-connector-draft-articles/admin-saml-configuration-guide-okta-draft-doc-51903/Okta1G.png)
[]![Assignments in Okta](/downloads/tech-pubs-drafts/cloud-connector-draft-articles/admin-saml-configuration-guide-okta-draft-doc-51903/Okta2A.png)
[]![Assign to People in Okta](/downloads/tech-pubs-drafts/cloud-connector-draft-articles/admin-saml-configuration-guide-okta-draft-doc-51903/Okta2B.png)
[]![Assign button in Okta](/downloads/tech-pubs-drafts/cloud-connector-draft-articles/admin-saml-configuration-guide-okta-draft-doc-51903/Okta2C.png)
[]![Save and Go Back in Okta](/downloads/tech-pubs-drafts/cloud-connector-draft-articles/admin-saml-configuration-guide-okta-draft-doc-51903/Okta2Ca.png)
[]![Sign On in Okta](/downloads/tech-pubs-drafts/cloud-connector-draft-articles/admin-saml-configuration-guide-okta-draft-doc-51903/Okta2D.png)
[]![View SAML setup instructions in Okta](/downloads/tech-pubs-drafts/cloud-connector-draft-articles/admin-saml-configuration-guide-okta-draft-doc-51903/Okta2E.png)
[]![Identity Provider Issuer in Okta](/downloads/tech-pubs-drafts/cloud-connector-draft-articles/admin-saml-configuration-guide-okta-draft-doc-51903/Okta2F.png)
[]![X.509 Certificate in Okta](/downloads/tech-pubs-drafts/cloud-connector-draft-articles/admin-saml-configuration-guide-okta-draft-doc-51903/Okta2Fa.png)
[]![Upload under IdP SAML Certificate in the Zscaler Cloud & Branch Connector Admin Portal](/downloads/tech-pubs-drafts/cloud-connector-draft-articles/admin-saml-configuration-guide-okta-draft-doc-51903/Okta3B.png)
[]![Choose File in the IdP SAML Certificate window in the Zscaler Cloud & Branch Connector Admin Portal](/downloads/tech-pubs-drafts/cloud-connector-draft-articles/admin-saml-configuration-guide-okta-draft-doc-51903/Okta3C.png)
[]![Issuer under SAML Authentication for Administrators in the Zscaler Cloud & Branch Connector Admin Portal](/downloads/tech-pubs-drafts/cloud-connector-draft-articles/admin-saml-configuration-guide-okta-draft-doc-51903/Okta3D.png)
[]![Enable SAML Authentication in the Zscaler Cloud & Branch Connector Admin Portal](/downloads/tech-pubs-drafts/cloud-connector-draft-articles/admin-saml-configuration-guide-okta-draft-doc-51903/Okta3E.png)
[]![Four Square Icon in Okta](/downloads/tech-pubs-drafts/cloud-connector-draft-articles/admin-saml-configuration-guide-okta-draft-doc-51903/OktaTest1.png)
[]![My end user dashboard under Okta apps in Okta](/downloads/tech-pubs-drafts/cloud-connector-draft-articles/admin-saml-configuration-guide-okta-draft-doc-51903/OktaTest2.png)
[]![Zscaler Cloud and Branch Connector Administrator Application in Okta](/downloads/tech-pubs-drafts/cloud-connector-draft-articles/admin-saml-configuration-guide-okta-draft-doc-51903/OktaTets3.png)