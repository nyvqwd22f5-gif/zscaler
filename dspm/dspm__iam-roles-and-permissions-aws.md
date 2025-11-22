# IAM Roles and Permissions for AWS
Source: https://help.zscaler.com/dspm/iam-roles-and-permissions-aws
PDF: https://help.zscaler.com/pdf/com/en/1486391.pdf

As part of the [onboarding](/dspm/onboarding-aws-organization) process, you need to deploy the DSPM templates that create roles and permissions in the AWS organization. These templates create multiple IAM roles with the required permissions to establish a trust relationship between DSPM, the [orchestrator account](/dspm/understanding-orchestrator)[,] and target accounts. Each role has permissions for various services and actions such as resource discovery, CloudTrail log collection, etc.
IAM Roles
DSPM creates the following IAM roles to access the AWS accounts:
- [Resource Discovery Role](#resourcediscovery)
- [Zscaler Access Role](#accessrole)
- [Orchestrator Instance Profile Role](#orchestratorinstanceprofile)
- [Scanner Instance Profile Role](#scannerinstanceprofile)
- [Target Role](#targetrole)
- [Put Evidence Role](#putevidencerole)
- [Get Evidence Role](#getevidence-role)
- [][Mandatory Permissions](#mandatory-RD-permissions)
- [Additional Permissions for AWS Bedrock Resources](#additional-RD-permissions)
[]If the AWS Bedrock resources are encrypted with KMS keys, DSPM fails to collect the metadata. To enable metadata collection, explicitly add the kms:Decrypt and kms:GenerateDataKey permissions to the resource discovery role.
To add the permissions:
- Sign in to the AWS Management Console and go to **IAM**.
- In the left-side navigation, select **Roles**.
- Search and select the resource discovery role created by DSPM.
- On the **Permissions **tab, click **DSPM-BASIC-CUSTOM-POLICY**.
-
In the **Policy editor**, add the following permissions and click **Next**.
- `kms:GenerateDataKey`
- `kms:Decrypt`
[See image.](#policyeditor-section)
- Click **Save changes**.
[]The resource discovery role is required for DSPM to discover resources within the onboarded accounts and collect CloudTrail logs. The role has the following permissions:
| Permission | Effect | Scope | Purpose |
| ---------- | ------ | ----- | ------- |
| `logs:ListLogDeliveries` | Allow | Monitored Accounts | To list the log delivery settings for a specific log group |
| `memorydb:DescribeAcls` | Allow | Monitored Accounts | To describe the access control lists (ACLs) associated with a MemoryDB cluster |
| `memorydb:DescribeUsers` | Allow | Monitored Accounts | To describe the users associated with a MemoryDB cluster |
| `redshift-serverless:GetWorkgroup` | Allow | Monitored Accounts | To retrieve information about a specific Amazon Redshift Serverless workgroup |
| `redshift-serverless:ListNamespaces` | Allow | Monitored Accounts | To list all the namespaces in an Amazon Redshift Serverless account |
| `redshift-serverless:GetNamespace` | Allow | Monitored Accounts | To retrieve information about a specific namespace in Amazon Redshift Serverless |
| `redshift-serverless:GetWorkgroup` | Allow | Monitored Accounts | To retrieve information about a specific workgroup in Amazon Redshift Serverless |
| `redshift-serverless:ListWorkgroups` | Allow | Monitored Accounts | To list all the workgroups in an Amazon Redshift Serverless account |
| `elasticache:DescribeReplicationGroups` | Allow | Monitored Accounts | To describe the replication groups associated with an Amazon ElastiCache cluster |
| `wafv2:ListResourcesForWebACL` | Allow | Monitored Accounts | To list all the resources that are associated with a specific AWS WAFv2 web ACL |
| `s3:GetObject` | Deny | Monitored Accounts |  |
| `dynamodb:BatchGetItem` | Deny | Monitored Accounts |  |
| `dynamodb:GetItem` | Deny | Monitored Accounts |  |
| `dynamodb:Query` | Deny | Monitored Accounts |  |
| `dynamodb:Scan` | Deny | Monitored Accounts |  |
[]The DSPM access role is required for DSPM to perform operations in Simple Queue Service (SQS) that is created as part of the template deployment. The role has the following permissions:
| Permission | Effect | Scope | Purpose |
| ---------- | ------ | ----- | ------- |
| `sts:AssumeRole` | Allow | Orchestrator Account | To assume a role in AWS |
| `autoscaling:Describe*` | Allow | Orchestrator Account | To retrieve information about Auto Scaling resources |
| `ec2:Describe*` | Allow | Orchestrator Account | To retrieve information about Amazon EC2 resources |
| `ec2:CreateLaunchTemplateVersion` | Allow | Orchestrator Account | To create a new version of a launch template |
| `autoscaling:UpdateAutoScalingGroup` | Allow | Only resources created by DSPM (based on tags) | To update Zscaler DSPM’s Auto Scaling group |
| `ec2:TerminateInstances` | Allow | Only resources created by DSPM (based on tags) | To terminate one or more Zscaler DSPM’s Amazon EC2 instances |
| `kms:GenerateDataKey` | Allow | Only resources created by DSPM (based on tags) | To generate a data key for Zscaler DSPM’s key that can be used to encrypt data |
| `kms:Decrypt` | Allow | Only resources created by DSPM (based on tags) | To decrypt ciphertext that was encrypted using Zscaler DSPM’s key in the AWS Key Management Service (KMS) |
[]The orchestrator instance profile role is used by the orchestrator instance present in the primary region to organize data scanning. The role has the following permissions:
| Permission | Effect | Scope | Purpose |
| ---------- | ------ | ----- | ------- |
| `sqs:ReceiveMessage` | Allow | Orchestrator Account | To retrieve one or more messages from an SQS queue |
| `sqs:Get*` | Allow | Orchestrator Account | To retrieve information about an SQS queue, including its attributes and permissions |
| `sqs:List*` | Allow | Orchestrator Account | To list SQS queues and their attributes |
| `rds:RestoreDBClusterFromSnapshot` | Allow | Orchestrator Account | To restore database cluster from a snapshot of an RDS database cluster |
| `rds:RestoreDBInstanceFromDBSnapshot` | Allow | Orchestrator Account | To restore database instance from a snapshot of an RDS database instance |
| `rds:CreateDBCluster` | Allow | Orchestrator Account | To create an RDS cluster |
| `rds:CreateDBInstance` | Allow | Orchestrator Account | To create an RDS instance |
| `rds:CopyDBSnapshot` | Allow | Orchestrator Account | To copy a snapshot of an RDS database instance |
| `rds:CopyDBClusterSnapshot` | Allow | Orchestrator Account | To copy a snapshot of an RDS database cluster |
| `rds:ModifyDBClusterSnapshotAttribute` | Allow | Only resources created by DSPM (based on tags) | To modify the attributes of a database cluster snapshot |
| `rds:AddTagsToResource` | Allow | Orchestrator Account | To add tags to an RDS resource |
| `rds:List*` | Allow | Orchestrator Account | To list various RDS resources |
| `rds:Describe*` | Allow | Orchestrator Account | To describe various RDS resources, such as database instances, snapshots, and clusters |
| `rds:ModifyDBInstance` | Allow | Only resources created by DSPM (based on tags) | To modify an RDS instance |
| `rds:ModifyDBCluster` | Allow | Only resources created by DSPM (based on tags) | To modify an RDS cluster |
| `rds:DeleteDBClusterSnapshot` | Allow | Only resources created by DSPM (based on tags) | To delete a snapshot of Zscaler DSPM’s RDS database cluster created for scanning |
| `rds:DeleteDBSnapshot` | Allow | Only resources created by DSPM (based on tags) | To delete a snapshot of Zscaler DSPM’s RDS database instance created for scanning |
| `rds:ModifyDBSnapshot` | Allow | Only resources created by DSPM (based on tags) | To modify a snapshot of Zscaler DSPM’s RDS database instance created for scanning |
| `rds:ModifyDBSnapshotAttribute` | Allow | Only resources created by DSPM (based on tags) | To share the Zscaler DSPM’s database snapshot created for scanning |
| `rds:DeleteDBInstance` | Allow | Only resources created by DSPM (based on tags) | To delete the Zscaler DSPM’s RDS database instance created for scanning |
| `rds:DeleteDBCluster` | Allow | Only resources created by DSPM (based on tags) | To delete the Zscaler DSPM’s RDS database cluster created for scanning |
| `s3:GetObjectAcl` | Allow | Only resources created by DSPM (based on tags) | To retrieve the access control list (ACL) of an S3 object from resources created by DSPM (based on tags) |
| `s3:GetObject` | Allow | Only resources created by DSPM (based on tags) | To retrieve the S3 object from resources created by DSPM (based on tags) |
| `s3:DeleteObjectVersion` | Allow | Only resources created by DSPM (based on tags) | To delete the specific version of the S3 object from resources created by DSPM (based on tags) |
| `s3:ListBucket` | Allow | Only resources created by DSPM (based on tags) | To list the objects in resources created by DSPM (based on tags) |
| `s3:DeleteObject` | Allow | Only resources created by DSPM (based on tags) | To delete an S3 object from resources created by DSPM (based on tags) |
| `sts:AssumeRole` | Allow | Orchestrator Account | To assume a role in AWS |
| `iam:PassRole` | Allow | Orchestrator Account | To pass an IAM role |
| `ec2:RunInstance*` | Allow | Only resources created by DSPM (based on tags) | To start the scanner instance |
| `ec2:StartInstances` | Allow | Only resources created by DSPM (based on tags) | To start the scanner instance |
| `ec2:CreateVolume` | Allow | Orchestrator Account | To create volume for scanning |
| `ec2:CreateTags` | Allow | Orchestrator Account | To create tags for EC2 resources |
| `ec2:CreateSnapshot*` | Allow | Orchestrator Account | To create snapshot of EC2 volumes |
| `ec2:List*` | Allow | Orchestrator Account | To list the EC2 resources |
| `ec2:Describe*` | Allow | Orchestrator Account | To describe the EC2 resources |
| `ec2:Get*` | Allow | Orchestrator Account | To get EC2 resources |
| `kms:Decrypt` | Allow | Orchestrator Account | To decrypt ciphertext that was encrypted using a KMS key |
| `kms:Encrypt` | Allow | Orchestrator Account | To encrypt plaintext using a KMS key |
| `kms:ReEncrypt*` | Allow | Orchestrator Account | To re-encrypt ciphertext that was encrypted using a KMS key |
| `kms:GenerateDataKey*` | Allow | Orchestrator Account | To generate a data key without plaintext |
| `kms:List*` | Allow | Orchestrator Account | To list various KMS resources, such as keys and grants |
| `kms:Get*` | Allow | Orchestrator Account | To retrieve various KMS resources, such as keys and grants |
| `kms:Describe*` | Allow | Orchestrator Account | To describe various KMS resources, such as keys and grants |
| `kms:CreateGrant` | Allow | Orchestrator Account | To create a grant for a KMS key |
| `secretsmanager:GetSecretValue` | Allow | Only resources created by DSPM (based on tags) | To retrieve the value of a secret |
| `secretsmanager:PutSecretValue` | Allow | Only resources created by DSPM (based on tags) | To create or update the value of a secret |
| `secretsmanager:TagResource` | Allow | Only resources created by DSPM (based on tags) | To tag a secret |
| `secretsmanager:UpdateSecret` | Allow | Only resources created by DSPM (based on tags) | To update the Zscaler DSPM’s secret |
| `secretsmanager:DeleteSecret` | Allow | Only resources created by DSPM (based on tags) | To delete the Zscaler DSPM’s secret |
| `secretsmanager:PutResourcePolicy` | Allow | Only resources created by DSPM (based on tags) | To update the Zscaler DSPM’s secret policy |
| `secretsmanager:CreateSecret` | Allow | Orchestrator Account | To create a secret |
| `ec2:TerminateInstances` | Allow | Only resources created by DSPM (based on tags) | To terminate Zscaler DSPM’s EC2 instances |
| `ec2:StopInstances` | Allow | Only resources created by DSPM (based on tags) | To stop Zscaler DSPM’s EC2 instances |
| `ec2:DetachVolume` | Allow | Only resources created by DSPM (based on tags) | To detach Zscaler DSPM’s volumes from scanner EC2 instances |
| `ec2:DeleteVolume` | Allow | Only resources created by DSPM (based on tags) | To delete Zscaler DSPM’s volumes |
| `ec2:AttachVolume` | Allow | Only resources created by DSPM (based on tags) | To attach Zscaler DSPM’s volumes to scanner EC2 instances |
| `iam:CreateServiceLinkedRole` | Allow | Orchestrator Account | To create RDS service-linked role if it does not exist |
| `autoscaling:UpdateAutoScalingGroup` | Allow | Only resources created by DSPM (based on tags) | To update the Zscaler DSPM auto-scaling group |
| `ec2:CreateNetworkInsightsPath` | Allow | Orchestrator Account | To create a Network Insights path. This permission is conditional and only required if Custom Network is used. |
| `ec2:DescribeNetworkInsightsPaths` | Allow | Orchestrator Account | To describe one or more Network Insights pathsThis permission is conditional and only required if Custom Network is used. |
| `ec2:DeleteNetworkInsightsPath` | Allow | Orchestrator Account | To delete a Network Insights pathThis permission is conditional and only required if Custom Network is used. |
| `ec2:StartNetworkInsightsAnalysis` | Allow | Orchestrator Account | To start a Network Insights analysisThis permission is conditional and only required if Custom Network is used. |
| `ec2:DescribeNetworkInsightsAnalyses` | Allow | Orchestrator Account | To describe one or more Network Insights analysesThis permission is conditional and only required if Custom Network is used. |
| `ec2:DeleteNetworkInsightsAnalysis` | Allow | Orchestrator Account | To delete a Network Insights analysisThis permission is conditional and only required if Custom Network is used. |
| `tiros:CreateQuery` | Allow | Orchestrator Account | To create a VPC reachability queryThis permission is conditional and only required if Custom Network is used. |
| `tiros:ExtendQuery` | Allow | Orchestrator Account | To extend a VPC reachability queryThis permission is conditional and only required if Custom Network is used. |
| `tiros:GetQueryAnswer` | Allow | Orchestrator Account | To get the VPC reachability query answerThis permission is conditional and only required if Custom Network is used. |
| `tiros:GetQueryExplanation` | Allow | Orchestrator Account | To get the VPC reachability query explanationThis permission is conditional and only required if Custom Network is used. |
| `tiros:GetQueryExtensionAccounts` | Allow | Orchestrator Account | To list accounts that might be useful in a new queryThis permission is conditional and only required if Custom Network is used. |
[]The scanner instance profile role is used by the scanner instances to perform data scanning and has the following permissions:
| Permission | Allow | Scope | Purpose |
| ---------- | ----- | ----- | ------- |
| `sts:AssumeRole` | Allow | All resources | To assume a role in AWS |
| `secretsmanager:GetSecretValue` | Allow | Only resources created by DSPM (based on tags) | To get the value of a secret |
| `sqs:ReceiveMessage` | Allow | DSPM Queues | To retrieve one or more messages from an SQS queue |
| `sqs:DeleteMessage` | Allow | Only resources created by DSPM (based on tags) | To delete a message from an SQS queue |
| `sqs:Get*` | Allow | DSPM Queues | To retrieve information about an SQS queue, including its attributes and permissions |
| `sqs:List*` | Allow | DSPM Queues | To list SQS queues and their attributes |
| `kms:Decrypt` | Allow | All resources | To decrypt ciphertext that was encrypted using a KMS key |
| `s3:GetObjectAcl` | Allow | Only resources created by DSPM (based on tags) | To retrieve the access control list (ACL) of an S3 object from DSPM export bucket |
| `s3:GetObject` | Allow | DSPM Export Bucket | To retrieve the S3 object from DSPM export bucket |
| `s3:ListBucket` | Allow | DSPM Export Bucket | To list the objects in DSPM export bucket |
[]The target role is an IAM role created in the target accounts containing permissions to CreateSnapshot, GetObject from S3, etc. The role has the following permissions:
| Permission | Data Store Type or Managed Policy | Scope | Purpose |
| ---------- | --------------------------------- | ----- | ------- |
| `dynamodb:ExportTableToPointInTime` | DynamoDB | Monitored Account | To export a DynamoDB table to Amazon S3 at a specific point in time |
| `s3:AbortMultipartUpload` | DynamoDB | DSPM S3 export bucket in orchestrator account | To abort a multipart upload to the export S3 bucket |
| `s3:PutObject` | DynamoDB | DSPM S3 export bucket in orchestrator account | To upload an object to the export S3 bucket |
| `s3:PutObjectAcl` | DynamoDB | DSPM S3 export bucket in orchestrator account | To set the access control list (ACL) for an object in the export S3 bucket |
| `events:Describe*` | EventBridge | Monitored Accounts | To describe various resources in Amazon EventBridge |
| `events:List*` | EventBridge | Monitored Accounts | To list various resources in Amazon EventBridge |
| `events:EnableRule` | EventBridge | Monitored Accounts | To enable a rule in Amazon EventBridge |
| `events:PutRule` | EventBridge | Monitored Accounts | To create or update a rule in Amazon EventBridge |
| `events:PutTargets` | EventBridge | Monitored Accounts | To add or update targets for a rule in Amazon EventBridge |
| `iam:PassRole` | EventBridge | Monitored Accounts | To pass an IAM role to Amazon EventBridge |
| `events:DisableRule` | EventBridge | Monitored Accounts | To disable an Amazon EventBridge rule |
| `kms:PutKeyPolicy` | RDS | Monitored Accounts | To set the key policy for a KMS key |
| `kms:CreateGrant` | RDS | Monitored Accounts | To create a grant for a KMS key |
| `rds:CreateDBClusterSnapshot` | RDS | Monitored Accounts | To create a snapshot of an RDS database cluster |
| `rds:CreateDBSnapshot` | RDS | Monitored Accounts | To create a snapshot of an RDS database instance |
| `rds:CopyDBSnapshot` | RDS | Monitored Accounts | To copy a snapshot of an RDS database instance |
| `rds:CopyDBClusterSnapshot` | RDS | Monitored Accounts | To copy a snapshot of an RDS database cluster |
| `rds:ModifyDBClusterSnapshotAttribute` | RDS | Monitored Accounts | To modify the attributes of a database cluster snapshot |
| `rds:RestoreDBInstanceFromDBSnapshot` | RDS | Monitored Account | To restore a database instance from a snapshot |
| `rds:AddTagsToResource` | RDS | Monitored Accounts | To add tags to an RDS resource |
| `rds:List*` | RDS | Monitored Accounts | To list various RDS resources |
| `rds:Describe*` | RDS | Monitored Accounts | To describe various RDS resources, such as database instances, snapshots, and clusters |
| `rds:DeleteDBClusterSnapshot` | RDS | Only resources created by DSPM (based on tags) | To delete a snapshot of Zscaler DSPM’s RDS database cluster created for scanning |
| `rds:DeleteDBSnapshot` | RDS | Only resources created by DSPM (based on tags) | To delete a snapshot of Zscaler DSPM’s RDS database instance created for scanning |
| `rds:ModifyDBSnapshotAttribute` | RDS | Only resources created by DSPM (based on tags) | To share the Zscaler DSPM’s database snapshot created for scanning |
| `rds:DeleteDBInstance` | RDS | Only resources created by DSPM (based on tags) | To delete the Zscaler DSPM’s RDS database instance created for scanning |
| `s3:Get*` | S3 | Monitored Accounts | To retrieve objects from an S3 bucket |
| `s3:List*` | S3 | Monitored Accounts | To list objects in an S3 bucket |
| `s3:GetReplicationConfiguration` | S3 | Monitored Accounts | To retrieve the replication configuration for an S3 bucket |
| `bedrock:ListImportedModels` | AWS Bedrock | Monitored Accounts | To enable scanning for custom and imported models |
| `bedrock:GetImportedModel` | AWS Bedrock | Monitored Accounts | To enable scanning for custom and imported models |
| `ec2:CreateSnapshot*` | Workload | Monitored Accounts | To create a snapshot of an EC2 instance's root volume or a specific volume |
| `ec2:CreateTags` | Workload | Monitored Accounts | To create tags for EC2 resources |
| `ec2:List*` | Workload | Monitored Accounts | To list various EC2 resources |
| `ec2:Describe*` | Workload | Monitored Accounts | To describe various EC2 resources |
| `ec2:Get*` | Workload | Monitored Accounts | To retrieve various EC2 resources |
| `ec2:CopySnapshot` | Workload | Monitored Accounts | To copy an EC2 snapshot |
| `kms:Decrypt` | Workload | Monitored Accounts | To decrypt ciphertext that was encrypted using a KMS key |
| `kms:Encrypt` | Workload | Monitored Accounts | To encrypt plaintext using a KMS key |
| `kms:ReEncrypt*` | Workload | Monitored Account | To re-encrypt ciphertext that was encrypted using a KMS key |
| `kms:GenerateDataKeyWithoutPlaintext` | Workload | Monitored Accounts | To generate a data key without plaintext |
| `kms:List*` | Workload | Monitored Accounts | To list various KMS resources, such as keys and grants |
| `kms:Get*` | Workload | Monitored Accounts | To retrieve various KMS resources, such as keys and grants |
| `kms:Describe*` | Workload | Monitored Accounts | To describe various KMS resources, such as keys and grants |
| `ec2:ModifySnapshotAttribute` | Workload | Only resources created by DSPM (based on tags) | To modify the attributes of Zscaler DSPM’s ec2 snapshot created for scanning |
| `ec2:DeleteSnapshot` | Workload | Only resources created by DSPM (based on tags) | To delete the Zscaler DSPM’s snapshot created for scanning |
| `secretsmanager:GetSecretValue` | Unmanaged Database | Monitored Account | To read the secret value from the secret managerThis permission is conditional and only required if Custom Network is used with Unmanaged DB Scanning. |
[]The Put Evidence role is required for DSPM to store evidence data snippets in the specified S3 bucket. The role has the following permissions:
| Permission | Effect | Scope | Purpose |
| ---------- | ------ | ----- | ------- |
| `s3:PutObject` | Allow | Evidence Bucket only | To put objects into the S3 bucket |
| `s3:PutObjectAcl` | Allow | Evidence Bucket only | To set the Access Control List (ACL) for an object in the export S3 bucket |
| `s3:GetBucketAcl` | Allow | Evidence Bucket only | To retrieve the ACL |
| `s3:GetBucketLocation` | Allow | Evidence Bucket only | To retrieve the region where a specific Amazon S3 bucket is located |
| `s3:DeleteObject` | Allow | Evidence Bucket only | To delete objects in the S3 bucket |
| `kms:Encrypt` | Allow | Evidence KMS Key | To encrypt plaintext using a KMS key |
| `kms:ReEncrypt` | Allow | Evidence KMS Key | To reencrypt ciphertext that was encrypted using a KMS key |
| `kms:GenerareDataKey` | Allow | Evidence KMS Key | To generate a data key for evidence KMS key to encrypt data |
| `kms:DescribeKey` | Allow | Evidence KMS Key | To describe the KMS key |
| `kms:Decrypt` | Allow | Evidence KMS Key | To decrypt ciphertext that was encrypted using a KMS key |
[]The Get Evidence role is required for DSPM to retrieve evidence data snippets from the specified S3 bucket. The role has the following permissions:
| Permission | Effect | Scope | Purpose |
| ---------- | ------ | ----- | ------- |
| `s3:GetObjectAcl` | Allow | Evidence Bucket only | To retrieve the Access Control List (ACL) of an S3 object from DSPM export bucket |
| `s3:GetObject` | Allow | Evidence Bucket only | To retrieve the S3 object from DSPM export bucket |
| `s3:GetBucketAcl` | Allow | Evidence Bucket only | To retrieve the ACL |
| `s3:GetBucketLocation` | Allow | Evidence Bucket only | To retrieve the region where a specific Amazon S3 bucket is located |
| `s3:ListBucket` | Allow | Evidence Bucket only | To list the objects in the DSPM export bucket |
| `kms:Decrypt` | Allow | Evidence KMS Key | To decrypt ciphertext that was encrypted using a KMS key |
[]
![The Policy editor section with the list of permissions for the selected role.](/downloads/dspm/administration/cloud-accounts-onboarding/aws-cloud-accounts/aws-organization/onboarding-aws-organization/dspm-aws-policy-editor.png)