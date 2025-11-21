# Editing or Deleting a Cloud Storage Integration
Source: https://help.zscaler.com/zpc/editing-or-deleting-cloud-storage-integration
PDF: https://help.zscaler.com/pdf/com/en/1395686.pdf

You can edit or delete any cloud storage integration (Amazon S3 Bucket, Azure Blob Storage, or Amazon Security Lake) as required.
Editing a Cloud Storage Integration
To edit a cloud storage integration:
- Go to **Administration **> **Integrations**.
- On the **Integrations** page, click the **Edit** icon for the cloud storage that you want to edit.
- In the **Edit Integration** window:
-
For Amazon S3 Bucket integration, change the **Integration Name**, **Amazon S3 Bucket Name**, or **Folder Location**.
[See image.](#s3bucket)
Whenever you edit an Amazon S3 Bucket integration, you must test the connection again.
-
For Azure Blob Storage integration, change the **Integration Name**, **Azure Storage Connection String**, or **Folder Location**.
[See image.](#editblob)
-
For Amazon Security Lake, change the **Integration Name**, **IAM Role**, **Amazon S3 Bucket Name**, **Folder Location**, and **Bucket Region** as required.
If you change the **Amazon S3 Bucket Name** or **Folder Location**, you must test the connection again.
[See image.](#edit-sl)
- Click **Save**.
Deleting a Cloud Storage Integration
To delete a cloud storage integration:
- Go to **Administration **>** Integrations**.
- On the **Integrations** page, click the **Delete** icon for the cloud storage that you want to delete.
-
In the **Delete Integration** window, read the message related to alert rules.
You cannot delete an integration if it is associated with alert rules. You must first move the alert rules to another integration. Until then, the **Delete** button is disabled.
[See image.](#delete)
- After you've moved the alert rules, click **Delete** to delete the integration.
[![Edit the Azure Blob storage details](/downloads/zpc/third-party-integrations/cloud-storage-integrations/editing-or-deleting-cloud-storage-integration/zpc-editazureblob.png)
]
[![Delete a cloud storage integration](/downloads/zpc/third-party-integrations/cloud-storage-integrations/editing-deleting-cloud-storage-integration/zpc-delete-msg-alerts.png)
]
[![Edit the Amazon S3 bucket details](/downloads/zpc/third-party-integrations/cloud-storage-integrations/editing-or-deleting-cloud-storage-integration/zpc-editamazonbucket.png)
]
[![Edit the Security Lake integration details](/downloads/zpc/third-party-integrations/cloud-storage-integrations/editing-or-deleting-cloud-storage-integration/zpc-edit-securitylake.png)
]