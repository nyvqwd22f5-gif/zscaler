# Connecting AnySource Using AWS S3
Source: https://help.zscaler.com/uvm/connecting-anysource-using-aws-s3
PDF: https://help.zscaler.com/pdf/com/en/1528386.pdf

![d7b700ee-7b9f-4688-94ec-a431558d0506.png](/downloads/uvm/configure/sources/anysource-aws-s3-method/d7b700ee-7b9f-4688-94ec-a431558d0506.png)
The Security Operations (SecOps) platform can integrate with your AWS S3 buckets to automatically extract data. When a new file is added to the bucket, an alert is triggered, and the file is retrieved.
Setting Up an S3 integration
Configuring an integration with your S3 data is a three-step process.
- Create a role that Zscaler can use to pull data.
- Create an SQS queue for the Zscaler to subscribe to.
- Configure your bucket to send “new object” notifications to the SQS queue.
Creating a Role for Zscaler
- Generate a unique identifier that will be used by Zscaler's service to assume the role. You can use this [UUID Generator](https://www.uuidgenerator.net).
- Run the SecOps platform's Cloud Formation Role Stack. You can either
a. [Follow the AWS instructions](https://console.aws.amazon.com/cloudformation/home?region=us-east-1#/stacks/create/review?stackName=AvalorStackIntegration&templateURL=https%3A%2F%2Favalor-platform-prod.s3.amazonaws.com/static/media/avalor-aws-standard.json)
OR
b. Use the command line:
`aws cloudformation create-stack \
--region <Region> \
--stack-name AvalorStackIntegration \
--capabilities CAPABILITY_NAMED_IAM \
--template-url https://avalor-platform-public-prod.s3.amazonaws.com/static/media/avalor-aws-standard.json \
--parameters ParameterKey=ExternalId, ParameterValue=<Generated UUID>`
- Replace `<Region>` with the region of the AWS service you’re retrieving data from.
- Replace `<Generated UUID>` with the UUID you created above.
- The `template-url` script provides permissions for AWS. If you're connecting to AnySource only, you can edit the script to modify or remove unnecessary permissions.
- [Permissions](#unnecessary-permissions)
After running the command, the RoleARNID value appears under the stack's Output tab.
[]{
"Action": [
"ec2:DescribeInstances",
"ecr:ListImages",
"ecr:DescribeImages",
"ecr:DescribeRepositories",
"ecr:DescribeImageScanFindings",
"rds:DescribeDBInstances",
"eks:ListClusters",
"eks:DescribeCluster",
"s3:ListAllMyBuckets",
"inspector2:ListFindings",
"securityhub:GetFindings"
],
"Effect": "Allow",
"Resource": "*"
},
Create an SQS Queue for Event Notifications
Create an SQS queue with the Access Policy as described in the [AWS Documentation](https://docs.aws.amazon.com/AmazonS3/latest/userguide/ways-to-add-notification-config-to-bucket.html#step1-create-sqs-queue-for-notification).
Name the queue `avalor-s3-event-forwarder`.
Copy and save the Queue ARN, to be used in the next step.
Make sure to send the Queue URL to your Zscaler Account team representative to complete the configuration process.
KMS Encryption (Optional)
If your organization uses KMS encryption, add the following to the key policy:
- Sid: Allow Role to use the key
Effect: Allow
Principal:
AWS: !GetAtt AvalorRole.Arn
Action:
- "kms:Decrypt"
- "kms:GenerateDataKey*"
Resource: "*"
Configure S3 Buckets
The final step is configuring an event notification from the S3 buckets where the data is generated for the SQS Queue. To complete the process, refer to [the AWS Documentation](https://docs.aws.amazon.com/AmazonS3/latest/userguide/enable-event-notifications.html).
When configuring the bucket:
- In step 6, select **All object create events **under the **Event Type**.
- In step 7, select **SQS Queue** as the Destination, then enter **SQS queue ARN**. Paste the ARN obtained from the previous step.
- Click **Save Changes**.
Repeat these steps for every bucket that you want to ingest data from.
Data Source Setup
After you finish setting up your S3 integration, send the following details to your Zscaler Account team representative to use in setting up the data source.
- AWS account ID
- Region
- Bucket
- Role ARN
- (Optional) Path
- (Optional) External ID: The external ID is the unique identifier you create when creating a role for Avalor. It is an additional security measure that can be used when accessing your account. While using an External ID is considered best practice, it is not mandatory.
- (Optional) File pattern (regex)
The Path and File Pattern Fields
You can utilize the Path and File pattern fields to manage which files are retrieved to the source. This is useful if you have a main bucket for all Zscaler files but want to divide the files into different sources. The Path and File pattern fields can be used separately or together to fit your use case best.
Path
The Path field is useful when you have sub-folders in your main bucket, and each folder contains files that should be associated with a different source in the platform. For example, if one folder holds logs from the production environment and another from the test environment, you can enter the specific path when setting up the source to ensure that only files from that path are uploaded to the source.
File
The File pattern field also allows better control over the files uploaded to a specific source. For example, by entering a “*.jsonl” pattern, the platform will only retrieve files with a .jsonl extension in that particular source. The file pattern should be entered in a regex format.