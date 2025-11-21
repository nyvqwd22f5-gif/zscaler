# Understanding the Functions of the AWS Deployment Script
Source: https://help.zscaler.com/deception/understanding-functions-aws-deployment-script
PDF: https://help.zscaler.com/pdf/com/en/1531575.pdf

Zscaler Deception relies on Amazon Web Services (AWS) logs to generate events in the [Deception dashboard](/deception/viewing-and-managing-zscaler-deception-dashboard) for interactions with AWS decoys. The deployment script for AWS Cloud Deception is responsible for creating logging resources, deploying decoys, deleting decoys, and enabling logging for the decoys via the logging resources in the AWS cloud. To collect and store logs, the deployment script creates various resources. The Zscaler Deception Admin Portal polls logs every 3 minutes from the logging resources created by the deployment script to generate events. The following table lists the resources created by the deployment script to enable log collection and storage for AWS decoys.
| Resource | Description |
| -------- | ----------- |
| DB Option and Parameter groups | To enable log collection via raw DB log files for Relational Database Service (RDS) decoys. |
| Security Group | To open inbound connections to ports 3306 (MySQL) and 5432 (PostgreSQL). |
| Logging Bucket | A Simple Storage Service (S3) bucket to collect logs for S3 and DynamoDB decoys enabled via CloudTrail. |
| CloudTrail | To enable logging to Logging Bucket and listening logs for Elastic Container Registry (ECR) and Identity and Access Management (IAM) decoys. |
| Log Access IAM User | A CLI user having access to poll logs from Logging Bucket and CloudTrial. |
| Access Keys | Access keys for the Log Access IAM User. |
| IAM User Policy | An access policy created for the Log Access IAM User. |
| Health Check Lambda Function | A lambda function that is triggered every 15 minutes from the Deception Admin Portal to check if the deployed decoys are present in the AWS account. |
| Health Check Lambda Function Access Policy | A policy created for the health check lambda function. |
The Deception Admin Portal polls logs from CloudTrail and Logging S3 Bucket every 3 minutes.
The following table lists the details of AWS logging resources utilized by the deployment script when creating various decoys.
| Decoy | Description |
| ----- | ----------- |
| S3 Decoy | Create an S3 Bucket and enable logging in CloudTrail. |
| IAM Decoy | Create an IAM decoy user with access keys and attach the IAM Decoy User Access Policy. |
| RDS Decoy | Create an RDS instance and create Option or Parameter group if not available already. |
| ECR Decoy | Create public or private container registeries. |
| DynamoDB Decoy | Create a DynamoDB instance and enable logging in CloudTrail. |
| VM Image Decoy | Deploy an EC2 instance, create a snapshot for the instace, and build an image from the snapshot.The EC2 instance is created using the t3.small/t2.small series available in the region of deployment. It persists for a duration for 5 minutes and is terminated after the snapshot is built. |
To learn how to obtain the deployment script for AWS Cloud Deception, see [Obtaining the Deployment Script for AWS](/deception/obtaining-deployment-script-aws).