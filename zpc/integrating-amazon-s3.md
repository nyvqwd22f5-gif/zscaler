# Integrating with Amazon S3
Source: https://help.zscaler.com/zpc/integrating-amazon-s3
PDF: https://help.zscaler.com/pdf/com/en/1395616.pdf

You can integrate Zscaler Posture Control (ZPC) with Amazon Simple Storage Service (Amazon S3). This integration enables ZPC to send the alert data logs of your cloud assets to the Amazon S3 buckets for storage and data analysis by third-party SIEM tools. To learn more, see [Integrating Cloud Storage with Splunk](/zpc/integrating-cloud-storage-splunk).
Only ZPC Administrators can configure a cloud storage integration. To learn more, see [About Administrators](/zpc/about-administrators).
Integrating with Amazon S3
To integrate ZPC with Amazon S3:
- Go to **Administration **>** Integrations**.
- Click **Add** for cloud storage integration.
-
On the **Add Integration** page:
- For **Integration Name**, enter a unique name for the integration.
- For **Cloud Storage**, select **Amazon S3**.
[See image.](#zpc-selectstorage)
- Click **Next**.
-
Under **Cloud Storage**, complete the following steps to set up the permissions required to access the Amazon S3 bucket.
[See image.](#zpc-awsdetails)
- For **Amazon S3 Bucket Name**, enter the bucket name where the data must be stored.
- Click the **Copy** icon to copy the **S3 Bucket policy**. The policy authorizes ZPC to access the S3 bucket.
-
Log in to the [Amazon S3 console](https://console.aws.amazon.com/s3).
- Access the required bucket where you want to apply the bucket policy.
- Select **Permissions**.
- Under** Bucket policy**, click **Edit**.
- On the **Edit bucket policy** page, paste the **S3 bucket policy** and click **Save changes**.
[See image.](#zpc-awsedit)
- (Optional) For **Folder Location**, enter the folder location of the bucket.
-
Before testing the connection, check the encryption type that is applied to the S3 bucket.
- Select the **Properties** tab, then scroll down to **Default encryption**.
-
Select **Amazon S3 managed keys (SSE-S3)** as the encryption key type for the connection to be successful and eventually for seamless data transfer.
If you select AWS Key Management Service (SSE-KMS), then the connection fails.
[See image.](#zpc-kms)
- Click **Test Connection** to verify the connection between ZPC and Amazon S3 service. If the connection happens, then a message is displayed that the connection is successful.
- Click **Next**.
-
Review the integration summary. Click the **Edit** icon if you want to make any changes.
[See image.](#zpc-awssummary)
- Click **Finish**.
You can see the integration details on the **Integrations** page. The initial status is shown as *Pending* because data is not yet sent to the Amazon S3 bucket. You must configure and associate the [alert rules](/zpc/understanding-alert-rules) with this integration for ZPC to be able to send the data logs. After ZPC sends the data logs to the Amazon S3 bucket, then the status changes to *Success*. [See image.](#zpc-intstatus)
[]![Select the Amazon S3 cloud storage](/downloads/zpc/third-party-integrations/cloud-storage-integrations/integrating-amazon-s3/zpc-add-amazons3.png)
[]![Add the Amazon S3 cloud storage details](/downloads/zpc/third-party-integrations/cloud-storage-integrations/integrating-amazon-s3/zpc-amazon-cloud-storage-info.png)
[]![Review the details on the Summary page](/downloads/zpc/administration/integrations/cloud-storage-integrations/integrating-amazon-s3/zpc-add-integ-amazon-summary.png)
[]![View the integration status](/downloads/zpc/third-party-integrations/cloud-storage-integrations/integrating-amazon-s3/zpc-integ-status.png)
[]![Edit the Amazon S3 bucket policy](/downloads/zpc/third-party-integrations/cloud-storage-integrations/integrating-amazon-s3/zpc-edit-bucket-policy.png)
[]![Selecting Amazon S3 KMS](/downloads/zpc/third-party-integrations/cloud-storage-integrations/integrating-amazon-s3/zpc-amazons3-kms.png)