# Integrating with Amazon S3
Source: https://help.zscaler.com/dspm/integrating-amazon-s3
PDF: https://help.zscaler.com/pdf/com/en/1487531.pdf

You can integrate DSPM with Amazon Simple Storage Service (Amazon S3). This integration enables DSPM to send the alert data logs of your cloud resources to the Amazon S3 buckets for storage.
Only [users with admin role](/dspm/predefined-roles-and-permissions) can configure a cloud storage integration.
Integrating with Amazon S3
To integrate DSPM with Amazon S3:
- Go to **Administration **>** Integrations**.
-
Click **Add** for cloud storage integration.
[See image.](#ds-awsadd)
-
On the **Add Integration** page:
- For **Integration Name**, enter a unique name for the integration.
- For **Cloud Storage**, select **Amazon S3**.
[See image.](#ds-cs-select)
- Click **Next**.
-
Under **Cloud Storage**, complete the following steps to set up the permissions required by DSPM to access the Amazon S3 bucket.
[See image.](#ds-configaws)
- For **Amazon S3 Bucket Name**, enter the bucket name where the data must be stored.
- Click the **Copy** icon to copy the **S3 Bucket policy**. The policy authorizes DSPM to access the S3 bucket. You need to paste this policy in the AWS console.
- Sign in to the [AWS Management Console](https://console.aws.amazon.com/s3).
- Access the required bucket where you want to apply the bucket policy.
- Select **Permissions**.
- Under** Bucket policy**, click **Edit**.
-
On the **Edit bucket policy** page, paste the **S3 bucket policy** you copied earlier, then click **Save changes**.
[See image.](#ds-addpolicy)
- In the DSPM Admin Portal, enter the **Folder Location **of the bucket.
- Before testing the connection, check the encryption type that is applied to the S3 bucket.
- On the [AWS Management Console](https://console.aws.amazon.com/s3), select the **Properties** tab, then scroll down to **Default encryption**.
-
Select **Amazon S3 managed keys (SSE-S3)** as the encryption key type for the connection to be successful and eventually for seamless data transfer.
If you select AWS Key Management Service (SSE-KMS), then the connection fails.
[See image.](#ds-awskms)
- Click **Test Connection** to check if the connection is established between DSPM and Amazon S3 service. A message is displayed to indicate the connection is successful.
- Click **Next**.
-
Review the integration summary. Click the **Edit** icon if you want to make any changes.
[See image.](#ds-awssummary)
- Click **Finish**.
You can see the integration details on the **Integrations** page. The initial status is shown as Pending because data is not yet sent to the Amazon S3 bucket. You must first configure and associate the [alert rules](/zpc/understanding-alert-rules) with this integration for DSPM to be able to send the data logs. After DSPM sends the data logs to the Amazon S3 Bucket, then the status changes to Success.
[]![Add a cloud storage integration](/downloads/dspm/third-party-integrations/cloud-storage-services/integrating-amazon-s3/ds-cs-addbutton.png)
[]![Select a cloud storage](/downloads/dspm/third-party-integrations/cloud-storage-services/integrating-amazon-s3/ds-aws-select.png)
[]![Configure the cloud storage](/downloads/dspm/third-party-integrations/cloud-storage-services/integrating-amazon-s3/ds-aws-addcsdetails.png)
[]![Add the DSPM policy](/downloads/zpc/third-party-integrations/cloud-storage-services/integrating-amazon-s3/ds-edit-bucket-policy.png)
[]![Select the encryption key type](/downloads/zpc/third-party-integrations/cloud-storage-services/integrating-amazon-s3/ds-aws-kms.png)
[]![Review the integration details](/downloads/dspm/third-party-integrations/cloud-storage-services/integrating-amazon-s3/ds-aws-summary.png)