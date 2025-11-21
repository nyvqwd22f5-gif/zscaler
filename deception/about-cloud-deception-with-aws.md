# About Cloud Deception with AWS
Source: https://help.zscaler.com/deception/about-cloud-deception-with-aws
PDF: https://help.zscaler.com/pdf/com/en/1531506.pdf

You can integrate Amazon Web Services (AWS) with Zscaler Deception to set up various AWS-specific decoy resources in your environment to lure adversaries. Depending on the type of decoy and its configuration, an adversary can access, interact, or perform malicious operations with the cloud decoys in different ways. Such activities are logged as attacks. You can view and analyze the attack details from the [Deception dashboard](/deception/viewing-and-managing-zscaler-deception-dashboard).
Cloud Deception with AWS provides the following benefits and enables you to:
- Configure decoys that mimic legitimate AWS resources such as IAM decoys, S3 decoys, DynamoDB decoys, etc.
- Lure internal and external adversaries to AWS decoy resources and proactively take remedial action.
- Leverage landmine policies such as cloud lures, session lures, browser lures, and certain file decoys to lure internal adversaries.
You can deploy AWS decoys to detect malicious activities originating from adversaries within or outside your organization, depending on the type and configuration of the decoys. For example, lures for AWS decoys configured using landmine policies detect malicious activities from users within an organization as the landmine policies are deployed in devices managed by your organization. On the other hand, AWS decoys with public visibility can detect malicious activities from external adversaries who enumerate them with various tools.
Deception uses a deployment script to set up the integration and deploy decoys in the AWS cloud. The script also deploys all necessary resources such as functions, users, policies, etc. to manage Cloud Deception with AWS. A health check lambda function is also deployed that monitors and updates the health status of the deployed decoys to the Zscaler Deception Admin Portal every 15 minutes.
About the Cloud Deception AWS Page
On the Cloud Deception - AWS page (Deceive > Cloud Deception > AWS), you can do the following:
-
Go to the AWS decoys listed as follows:
- [IAM Decoys](/deception/creating-iam-decoy-aws)
- [S3 Decoys](/deception/creating-s3-decoy-aws)
- [RDS Decoys](/deception/creating-rds-decoy-aws)
- [ECR Decoys](/deception/creating-ecr-decoy-aws)
- [DynamoDB Decoys](/deception/creating-dynamo-db-decoy-aws)
- [VM Image Decoys](/deception/creating-vm-image-decoy-aws)
- [Generative AI Decoys](/deception/creating-generative-ai-decoy-aws)
You can also check the status, edit, or delete your AWS decoys from the respective tabs. To learn more, see [Managing AWS Decoys](/deception/managing-aws-decoys).
- View the list of AWS accounts added to the Deception Admin Portal. For each entry, you can see:
- **Enabled**: Indicates whether the AWS account is enabled for deploying decoys.
- **Account ID**: The numerical account ID associated with an AWS account.
- **IAM User**: An IAM user created to access logs.
- **CloudTrail ARN**: The Cloud Trail for gathering logs.
- **Logging Bucket**: An S3 bucket created by the deployment script for logging purposes.
- **Health Check Function**: A lambda function deployed to monitor and update the health status of the deployed decoys to the Deception Admin Portal.
- **Marked for Deletion**: Indicates if an AWS account was marked to be deleted from the Deception Admin Portal.
- [Obtain the deployment script to run it on the AWS CloudShell](/deception/obtaining-deployment-script-aws).
- [Configure the integration between AWS and Deception](/deception/setting-cloud-deception-aws#zd-integration-aws-decoys).
- [Manage Deception settings for an AWS account](/deception/deleting-aws-deception-settings).![A screenshot of the Cloud Deception AWS page in the Zscaler Deception Admin Portal](/downloads/deception/deceive/cloud-deception/aws/about-cloud-deception-with-aws/deception-about-aws-cloud-deception.png)