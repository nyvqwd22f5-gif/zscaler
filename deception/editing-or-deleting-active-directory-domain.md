# Editing or Deleting an Active Directory Domain
Source: https://help.zscaler.com/deception/editing-or-deleting-active-directory-domain
PDF: https://help.zscaler.com/pdf/com/en/1531329.pdf

You can edit or delete an Active Directory (AD) domain that you have configured in the Zscaler Deception Admin Portal.
You cannot edit or delete an AD domain managed by a [server agent](/deception/about-server-agent-domains).
Editing an AD Domain
To edit an AD domain:
- Go to **Deceive** > **Active Directory Decoys** > **Domains**.
-
Under **Actions**, click the **Edit** icon for the domain that you want to modify.
[See image.](#deception-edit-ad-domain)
-
In the **Domain Details** window, modify the AD domain configuration per your requirements.
[See image.](#deception-ad-domain-modify-details)
- Click **Save**.
After you edit the AD domain, [download and run the deployment script ](/deception/running-decoy-deployment-script-active-directory)again on the primary domain controller.
Deleting an AD Domain
To delete an AD domain:
- Go to **Deceive** > **Active Directory Decoys** > **Domains**.
-
Under **Actions**, click the **Edit** icon for the domain that you want to delete.
[See image.](#deception-delete-ad-domain)
- In the confirmation window, click **OK**.
Deleting an AD domain from the Deception Admin Portal does not remove the AD decoy objects created in the domain. You must [download and run the deployment script ](/deception/running-decoy-deployment-script-active-directory)to remove all decoys before you delete your domain from the Deception Admin Portal or manually remove the objects from the domain.
If you delete an AD domain and create it again in the Deception Admin Portal, you must redeploy the [deployment scripts](/deception/running-decoy-deployment-script-active-directory) and the triggers.
[]![Edit an AD domain](/downloads/deception/deceive/active-directory-decoys/active-directory-decoy-management/editing-or-deleting-active-directory-domain/zscaler-deception-ad-domain-edit-3.png)
[]![Edit AD domain details](/downloads/deception/deceive/active-directory-decoys/active-directory-decoy-management/editing-or-deleting-active-directory-domain/zscaler-deception-ad-domain-edit-details-1.png)
[]![Delete an AD domain](/downloads/deception/deceive/active-directory-decoys/active-directory-decoy-management/editing-or-deleting-active-directory-domain/zscaler-deception-ad-domain-delete-3.png)