# Editing or Deleting an Active Directory Decoy User
Source: https://help.zscaler.com/deception/editing-or-deleting-decoy-active-directory-user
PDF: https://help.zscaler.com/pdf/com/en/1531330.pdf

You can edit or delete an Active Directory (AD) decoy user that you have configured in the Zscaler Deception Admin Portal.
Editing an AD Decoy User
To edit an AD decoy user:
- Go to **Deceive** > **Active Directory Decoys** > **Decoy Users**.
- Select an AD domain from the **Domain** drop-down menu.
-
Under **Actions**, click the **Edit** icon for the user that you want to modify.
[See image.](#deception-ad-user-edit)
-
In the **Decoy Details** window, modify the AD decoy user configuration per your requirements.
[See image.](#deception-ad-user-edit-details)
- Click **Save**.
After you edit an AD decoy user, [download and run the deployment script](/deception/running-decoy-deployment-script-active-directory) again on the primary domain controller to sync up the updated attributes from the Deception Admin Portal to the domain. If you change the username of the AD decoy user, then you must remove the existing trigger configuration and import the triggers again.
When you edit an AD decoy user that is deployed in an AD domain managed by a server agent, you don't have to manually run deployment scripts and import the triggers. The server agent automatically deploys decoys and forwards logs.
Deleting an AD Decoy User
To delete an AD decoy user:
- Go to **Deceive** > **Active Directory Decoys** > **Decoy Users**.
- Select an AD domain from the **Domain** drop-down menu.
-
Under **Actions**, click the **Delete** icon for the user that you want to delete.
[See image.](#deception-ad-user-delete)
- In the confirmation window, click **OK**.
If you delete an AD decoy user and create it again in the Deception Admin Portal, you must redeploy the [deployment script](/deception/running-decoy-deployment-script-active-directory) and import the triggers.
When you delete an AD decoy user that is deployed in an AD domain managed by a server agent and create it again, you don't have to manually run deployment scripts and import the triggers. The server agent automatically deploys decoys and forwards logs.
[]![Edit an AD decoy user](/downloads/deception/deceive/active-directory-decoys/active-directory-decoy-management/editing-or-deleting-decoy-active-directory-user/zscaler-deception-ad-user-edit-3.png)
[]![Edit AD decoy user details](/downloads/deception/deceive/active-directory-decoys/active-directory-decoy-management/editing-or-deleting-decoy-active-directory-user/zscaler-deception-ad-user-edit-details.png)
[]![Delete an AD decoy user](/downloads/deception/deceive/active-directory-decoys/active-directory-decoy-management/editing-or-deleting-decoy-active-directory-user/zscaler-deception-ad-user-delete-3.png)