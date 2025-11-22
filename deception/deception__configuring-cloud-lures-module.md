# Configuring the Cloud Lures Module
Source: https://help.zscaler.com/deception/configuring-cloud-lures-module
PDF: https://help.zscaler.com/pdf/com/en/1531304.pdf

The Cloud Lures module allows you to set up lures to Amazon Web Services (AWS) decoys or Microsoft Azure decoys on endpoints. You can set up lures for the following decoys:
- **AWS IAM**: Used to place the credentials of selected decoy AWS IAM users on endpoints. When this option is enabled, a hidden folder with the name `.aws `is created under `C:\Users\<username>\` on Windows endpoints and under `/users/<username>/`on Linux endpoints to store the credentials.
- **Azure File Shares**: Used to mount selected file share decoys on endpoints. When this option is enabled, the decoy file share is mounted as a network drive on the endpoints.
-
**Azure Service Principals**: Used to place the secrets of selected service principal decoys on endpoints. When this option is enabled, a hidden folder with the name `.azure `is created under `C:\Users\<username>\` on Windows endpoints to store secrets.
Service principal decoys are not supported on Linux endpoints.
-
**Azure Users**: Used to place the credentials of selected decoy Azure users on endpoints. When this option is enabled, a hidden folder with the name `.azure `is created under `C:\Users\<username>\` on Windows endpoints to store secrets.
Azure user decoys are not supported on Linux endpoints.
- **Azure Storage Explorer**: Used to enable access to storage account container decoys via the [Azure Storage Explorer app](https://azure.microsoft.com/en-in/products/storage/storage-explorer) from endpoints.
You must configure the supported AWS and Azure decoys before setting up the cloud lures.
To configure cloud lures for a landmine policy:
- Go to **Deceive **> **Landmine **> **Policies**.
-
In the landmine policies table, locate the landmine policy you want to use to deploy cloud lures on endpoints, and click the **Edit **icon.
[See image.](#option-to-edit-policy)
- In the policy configuration window, click **Cloud Lures**.
-
Locate the cloud decoys that you want to configure and for each decoy:
- Select **Enabled**.
-
Select a decoy from the **Target decoys** drop-down menu to use as a cloud lure.
The **GenAI** icon indicates lures that support generative AI decoys as target decoys.
[See image.](#zd-cloud-lures)
- Click **Save**.
[]![A screenshot capturing the option to edit a landmine policy](/downloads/deception/deceive/landmine-decoys/policies/configuring-cloud-lures-module/deception-landmine-policy-edit-one.png)
[]![A screenshot showing various cloud lure options](/downloads/deception/deceive/landmine-decoys/policies/configuring-cloud-lures-module/zscaler-deception-cloud-lures-module.png)