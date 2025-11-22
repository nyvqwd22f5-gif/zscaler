# Configuring CloudTrail S3 Buckets for AWS Organization
Source: https://help.zscaler.com/zpc/configuring-cloud-trail-s3-buckets-aws-organization
PDF: https://help.zscaler.com/pdf/com/en/1440866.pdf

ZPC needs to connect to your AWS CloudTrail S3 buckets to detect changes in your AWS infrastructure. ZPC detects the CloudTrail buckets configured for your onboarded AWS accounts. A single AWS account might have multiple CloudTrail buckets configured. ZPC displays all the CloudTrail buckets for each AWS account. ZPC provides an automation script to run on your AWS CloudShell. The script provides ZPC access to read your CloudTrail information. To configure CloudTrail S3 buckets for onboarded accounts:
- Go to **Administration** > **Cloud Accounts**.
- Select the **Actions** icon, then click **Add CloudTrail** for the AWS account you want to connect.
- On the **Select S3 Buckets** page, you can:
- View S3 buckets and their details.
- Search for S3 buckets.
- Select single or multiple S3 buckets to connect their CloudTrail to ZPC.
- Click **Next**.
[See image.](#select-s3-buckets)
- On the **Deploy Template** page, you can:
- View the prerequisites for running the deploy template bash script. The deploy template script connects all selected CloudTrail S3 buckets on to ZPC.
- Copy the deploy template bash script.
[See image.](#cloudtrail-deploy-template)
- On the [AWS Management Console](https://aws.amazon.com/console/), run the copied bash script on the AWS CloudShell.
- After the script is deployed, in the ZPC Admin Portal, click **Finish**.
CloudTrail S3 Buckets Encrypted with KMS Key
If the CloudTrail S3 buckets you have onboarded to ZPC are encryped with a KMS key, ZPC needs additional permission in the KMS key policy to access the buckets.
To grant ZPC access to encrypted CloudTrail S3 buckets:
- Assign the `kms:Decrypt` IAM role permission to the `ZPCCustom` role created when you onboarded the AWS cloud account. To learn more, see [Onboarding an Amazon Web Services Account](/zpc/onboarding-amazon-web-services-account#onboarding-script).
-
Modify the KMS key policy for the associated CloudTrail S3 bucket:
- On the [AWS Management Console](https://aws.amazon.com/console/), select **CloudTrail**.
- In the left-side navigation, click **Trails**, then select the associated cloud trail.
- Click the **AWS KMS Key** URL.
[See image.](#aws-kms-key-image)
- On the **Key Policy** tab, click **Edit**.
- In the `kmsiampolicy` section of the policy add the `ZPCCustom` role for the AWS cloud account. If you have onboarded an AWS organization, add the `ZPCCustom` role for each member cloud account.
"Sid": "kmsiampolicy",
"Effect": "Allow",
"Principal": {
"AWS": [
"arn:aws:iam::795208966777:root",
"arn:aws:iam::795208977759:role/<Zscaler Created Role>"
]
}
- In the `kmspolicy` section of the policy add the S3 service and the bucket region.
"Sid": "kmspolicy",
"Effect": "Allow",
"Principal": {
"Service": [
"logs.us-east-2.amazonaws.com",
"cloudtrail.amazonaws.com",
"s3.<Bucket Region>.amazonaws.com",
"dynamodb.amazonaws.com"
]
}
[]
![View the select S3 buckets list for CloudTrail integration.](/downloads/zpc/administration/cloud-accounts/configuring-cloud-trail-s3-buckets-aws-organization/zpc-select-cloudtrail-buckets.png)
[]
![View the deploy template page for CloudTrail integration.](/downloads/zpc/administration/cloud-accounts/configuring-cloud-trail-s3-buckets-aws-organization/zpc-cloudtrail-deploy-template.png)
[]
![View KMS key on AWS console](/downloads/zcspm/onboarding-guide/microsoft-azure/configuring-zcspm-agent-azure-kubernetes-service/zpc-aws-kms-key-policy-ui-image.png)