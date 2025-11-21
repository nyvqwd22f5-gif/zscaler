# Editing or Deleting a SAML Identity Provider
Source: https://help.zscaler.com/zidentity/editing-or-deleting-saml-identity-provider
PDF: https://help.zscaler.com/pdf/com/en/1532551.pdf

You can edit or delete a SAML identity provider (IdP) as necessary. You can also add a Request Signing and Decryption Certificate for SAML protocol.
Editing a SAML Identity Provider
To edit a SAML IdP:
- Go to **Integration **> **External Identities**.
-
On the **External Identities** page, click the **Edit** icon for the required primary or secondary SAML IdP.
[See image.](#1Edit-icon)
- Select the **Advanced **tab.
-
Edit the information in the **Authentication Request**, **Encrypted SAML Assertion**, **Request Signing and Decryption Certificate**, and **Session Attribute Mapping** sections.
[See image.](#edit-sections)
- Click **Update**.
A message is displayed indicating the IdP is updated successfully.
Adding a New Request Signing and Decryption Certificate
To add a new Request Signing and Decryption Certificate:
- Go to **Integration **> **External Identities**.
-
On the **External Identities** page, click the **Edit** icon for the required primary or secondary SAML IdP.
[See image.](#edit-icon2)
- Select the **Advanced **tab.
-
In the **Request Signing and Decryption Certificate **section, click **Add**. A new Request Signing and Decryption Certificate is added with two years of validity.
The following items appear for each certificate:
- **Name**: The name of the certificate.
- **Expiry**: The date when the certificate expires. The following icons appear when the certificate is expiring within 90 days.
- **Caution **icon: Appears when the certificate is about to expire.
- **Red Exclamation Mark **icon: Appears when the certificate is expired.
- **Download**: Click the **Download** icon to download the certificate. You might need to upload this certificate to the IdP.
- **Delete**: Click the **Delete **icon to delete the certificate. An active certificate cannot be deleted.
You can have a maximum of two Request Signing and Decryption Certificates at a time, out of which only one can be active.
[See image.](#add-certificate)
- Click **Update**.
Deleting a SAML Identity Provider
To delete a SAML IdP:
- Go to **Integration **> **External Identities**.
-
On the **External Identities** page, click the **Delete **icon for the required primary or secondary SAML IdP.
[See image.](#delete-icon)
-
Read the confirmation message, enter `YES`, then click **Delete**.
[See image.](#delete-confirmation)
[]
![External Identities page highlighted with edit icon. ](/downloads/tech-pubs-drafts/zidentity-draft-articles/draft-saml-identity-providers-doc-55564/external-idp-edit1.png)
[]![Advanced tab on Edit Secondary Identity Provider page. ](/downloads/tech-pubs-drafts/zidentity-draft-articles/draft-saml-identity-providers-doc-55564/edit-sec-idp.png)
[]
![External Identities page highlighted with delete icon. ](/downloads/tech-pubs-drafts/zidentity-draft-articles/draft-saml-identity-providers-doc-55564/external-idp-delete.png)
[]![Confirmation window for deleting secondary IdP.](/downloads/tech-pubs-drafts/zidentity-draft-articles/draft-saml-identity-providers-doc-55564/Delete-confirmation.png)
[]![External Identities page highlighted with edit icon. ](/downloads/tech-pubs-drafts/zidentity-draft-articles/draft-saml-identity-providers-doc-55564/external-idp-edit2.png)
[]![Advanced tab on Edit Secondary Identity Provider page with highlighted Add button to add a new request signing and decryption certificate](/downloads/tech-pubs-drafts/zidentity-draft-articles/draft-saml-identity-providers-doc-55564/add-certificate.png)