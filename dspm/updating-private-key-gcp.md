# Updating the Private Key for GCP
Source: https://help.zscaler.com/dspm/updating-private-key-gcp
PDF: https://help.zscaler.com/pdf/com/en/1498121.pdf

The private key is a confidential string associated with a GCP service account, which is necessary to access the service account from outside the Google Cloud environment, such as on other platforms or on-premises infrastructure. During the GCP account onboarding process, a private key is generated in JSON format when you apply the tree discovery template, which is then provided to DSPM as part of the account onboarding process.
If your service account keys need to be updated or have expired, you can update your service account key at any time.
Prerequisite
You must be assigned either an [Administrator role](/dspm/predefined-roles-and-permissions) or any role with permission to add accounts in the DSPM Admin Portal.
Download a private key for your service account in JSON format from the Google Cloud Console. To learn more on downloading a private key for a service account, refer to the [Google Cloud Documentation](https://cloud.google.com/iam/docs/keys-create-delete#creating).
Updating the Private Key
To update the private key, on the DSPM Admin Portal:
- Go to **Administration** > **Configuration** > **Cloud Accounts**.
- Select the GCP cloud account for which you want to update the service account.
-
Click **Manage**, and then select **Update Private Key** from the drop-down menu.
[See image.](#privatekey_dropdown)
-
In the **Update Private Key** window, upload the downloaded JSON file to the DSPM Admin Portal by either dragging and dropping the file, or clicking on **or click to browse** to select the file from your computer.
[See image.](#browsejson)
-
Click **Apply**.
[See image.](#privatekeyapply)
DSPM validates the updated private key by verifying it against the service account. If the validation is successful, a message appears indicating that the connection is established.
If the private key is invalid, or it does not match the service account, an error is displayed.
[See image.](#privatekeyconfirm)
- Click **Done**.
The private key is updated for the selected service account.
[]![Confirm Private Key](/downloads/dspm/administration/cloud-accounts-onboarding/gcp-cloud-accounts/updating-private-key-gcp/privatekeyconfirm.png)
[]![Upload JSON Private Key](/downloads/dspm/administration/cloud-accounts-onboarding/gcp-cloud-accounts/updating-private-key-gcp/privatekeyapply.png)
[]![Browse JSON Private Key](/downloads/dspm/administration/cloud-accounts-onboarding/gcp-cloud-accounts/updating-private-key-gcp/browsejson.png)
[]![Update Private Key Drop-down](/downloads/dspm/administration/cloud-accounts-onboarding/gcp-cloud-accounts/updating-private-key-gcp/privatekey_dropdown.png)