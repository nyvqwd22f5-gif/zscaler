# Onboarding an Amazon Web Services Account
Source: https://help.zscaler.com/zpc/onboarding-amazon-web-services-account
PDF: https://help.zscaler.com/pdf/com/en/1394156.pdf

Zscaler Posture Control (ZPC) supports onboarding an AWS organization or a single AWS cloud account. When onboarded, ZPC provides insight into your account's security posture. ZPC provides two automation bash scripts, initial script and onboarding script, that you can run on your AWS Cloud Shell to onboard your AWS cloud accounts.
- [Initial Script](#initial-script)
- [Onboarding Script](#onboarding-script)
To onboard an AWS account to ZPC:
- [1. Ensure all prerequisites are met.](#prerequisites)
- [2. Onboard an AWS organization.](#onboard-aws-organization)
OR
- [2. Onboard a single AWS account.](#onboard-aws-account)
- [3. Configure the AWS CloudTrail.](#cloudtrailconfig)
If you've subscribed for vulnerability management, then set up vulnerability scanning for your AWS cloud workloads and cloud container registries. To learn more, see [Configuring Vulnerability Scanning for Cloud Accounts](/zpc/configuring-vulnerability-scanning-cloud-accounts).
Additionally, connect your Amazon Elastic Kubernetes Service (EKS) clusters with ZPC to gain visibility into your cluster security posture. To learn more, see [Onboarding an Amazon Elastic Kubernetes Service Cluster](/zpc/onboarding-amazon-elastic-kubernetes-service-cluster).
After you onboard a cloud account, you can verify whether the cloud account is onboarded successfully and configuration metadata is being collected. To learn more, see [About Cloud Accounts](/zpc/about-cloud-accounts).
[]Another mandatory step after onboarding your AWS cloud accounts is to configure ZPC to collect additional configuration metadata:
- Connect your AWS CloudTrail S3 buckets with ZPC to detect changes in your AWS infrastructure. To learn more, see [Configuring Cloud Trail S3 Buckets for AWS Organization](/zpc/configuring-cloud-trail-s3-buckets-aws-organization).
[]
The initial script:
- Creates a Role with name `ZPC-ORG-${TENANT_HASH}`.
- Grants the created role `arn:aws:iam::aws:policy/AWSOrganizationsReadOnlyAccess` policy via `sts:AssumeRole` depending on a `sts:ExternalId`.
[]
The onboarding script:
- Verifies if the script was run by the root user of the AWS management account or not.
- Assigns the following policies to the helper user:
- `arn:aws:iam::aws:policy/AdministratorAccess`
- `arn:aws:iam::aws:policy/AWSOrganizationsFullAccess`
- Creates the following:
- A CloudFormation Stack with name `ZPC-ORG-${TENANT_HASH}`.
- A CloudFormation StackSet with name `ZPC-ORG-${TENANT_HASH}`.
- A Helper user with the name `zpc-onboarding-helper-${TENANT_HASH}`.
ZPC creates the CloudFormation Stack and StackSet to create the `ZPCCustom` role on all selected AWS accounts. The script creates only the `ZPCCustom` role if you are onboarding a single AWS account.
- Assigns the `SecurityAudit` managed policy to the role.
- Assigns the following custom policies to the role:
- [Custom Policies](#custom-policies)
- Assigns the following policies to the role, if you enabled CloudTrail:
- [ZPCCloudTrailS3Access](#cloud-trail-s3-access)
- [ZPCCloudTrailS3AccessList](#cloud-trail-s3-access-list)
- Assigns the following policies to the role, if you enabled vulnerability scanning:
- [Workloads](#workloads)
- [Containers](#containers)
[]
- lambda:GetFunctionUrlConfig
- lambda:GetLayerVersion
- lambda:GetFunctionConcurrency
- apigateway:GET
- cloudformation:ListResources
- cloudformation:GetResource
- dynamodb:ListBackups
- dynamodb:DescribeBackup
- redshift-serverless:ListNamespaces
- redshift-serverless:ListWorkgroups
- redshift-serverless:GetNamespace
- redshift-serverless:GetWorkgroup
- states:ListActivities
- simspaceweaver:ListSimulations
- athena:GetNamedQuery
- athena:GetWorkGroup
- athena:ListWorkGroup
- states:DescribeActivity
- states:DescribeStateMachine
- batch:DescribeJobQueues
- simspaceweaver:DescribeSimulation
- lightsail:GetRelationalDatabases
- lightsail:GetContainerServices
- lightsail:GetRelationalDatabase
- lightsail:GetDisks
- lightsail:GetInstance
- lightsail:GetDisk
- appsync:GetGraphqlApi
- appsync:GetDomainName
- appsync:GetFunction
- appsync:GetResolver
- storagegateway:DescribeSMBFileShares
- apprunner:ListServices
- apprunner:DescribeService
- apprunner:ListVpcConnectors
- apprunner:DescribeVpcConnector
- workmail:ListOrganizations
- workmail:DescribeOrganization
- memorydb:DescribeAcls
- memorydb:DescribeClusters
- memorydb:DescribeUsers
- trustadvisor:Describe*
- trustadvisor:List*
- s3:GetObject
- s3:GetObjectAcl
- s3:GetObjectVersion
- s3:GetObjectVersionAcl
- s3:GetBucketLocation
- s3:GetBucketPolicy
- s3:ListBucket
- appstream:DescribeStacks
- appstream:DescribeUsers
- appstream:DescribeFleets
- appstream:DescribeApplications
- kinesisvideo:GetSignalingChannelEndPoint
- kinesisvideo:ListTagsForResource
- kinesisvideo:ListTagsForStream
- kinesisvideo:ListStreams
- kinesisvideo:ListSignalingChannels
- kinesisvideo:DescribeStream
- kinesisvideo:DescribeSignalingChannel
- elastictranscoder:ReadPipeline
- elastictranscoder:ListJobsByPipeline
- elastictranscoder:ListPipelines
- elastictranscoder:ReadJob
- grafana:ListWorkspaces
- grafana:DescribeWorkspace
- aps:DescribeWorkspace
- aps:ListWorkspaces
- aps:ListRuleGroupsNamespaces
- aps:DescribeRuleGroupsNamespace
- kafka:DescribeConfiguration
- kafka:DescribeClusterV2
- kafka:ListClustersV2
- kafka:ListConfigurations
- airflow:GetEnvironment
- airflow:ListEnvironments
- lex:DescribeBotVersion
- lex:DescribeBot
- lex:ListBots
- lex:DescribeResourcePolicy
- lex:ListBotAliases
- lex:DescribeBotAlias
- lex:ListBotVersions
- lex:ListTagsForResource
- wafv2:GetLoggingConfiguration
- wafv2:GetRuleGroup
- wafv2:GetIPSet
- cloudfront:ListDistributionsByWebACLId
- networkfirewall:ListFirewalls
- networkfirewall:DescribeFirewall
- networkfirewall:ListFirewallPolicies
- networkfirewall:DescribeFirewallPolicy
- networkfirewall:DescribeLoggingConfiguration
- networkfirewall:ListRuleGroups
- networkfirewall:DescribeRuleGroup
- fms:GetPolicy
- fms:ListResourceSets
- fms:GetResourceSet
- waf:ListRules
- waf:GetRule
- waf:ListIPSets
- waf:GetIPSets
- waf:ListRuleGroups
- waf:GetRuleGroup
- waf:ListActivatedRulesInRuleGroup
- appflow:ListFlows
- appflow:DescribeFlow
- appflow:DescribeConnectorProfiles
- appflow:DescribeConnectors
- appflow:DescribeConnector
- iotsitewise:ListAssetModels
- iotsitewise:ListAssets
- iotsitewise:DescribeAsset
- iotsitewise:ListPortals
- iotsitewise:ListProjects
- iotsitewise:DescribeProject
- iotdeviceadvisor:ListSuiteDefinitions
- iotdeviceadvisor:GetSuiteDefinition
- iotevents:ListInputs
- iotevents:DescribeInput
- iotanalytics:ListDatastores
- iotanalytics:ListPipelines
- iotanalytics:DescribeDatastore
- iotanalytics:DescribePipeline
- backup:ListCopyJobs
- backup:ListBackupJobs
- backup:ListFrameworks
- backup:ListProtectedResources
- backup:DescribeCopyJob
- backup:DescribeBackupJob
- backup:DescribeRestoreJob
- backup:DescribeReportPlan
- backup:DescribeGlobalSettings
- backup:ListRestoreJobs
- backup:DescribeFramework
- backup:GetBackupPlan
- backup:DescribeProtectedResource
- backup:DescribeReportJob
- backup:DescribeRecoveryPoint
- backup:ListBackupPlans
- backup:DescribeBackupVault
- backup:ListReportPlans
- backup:ListReportJobs
- backup:ListRecoveryPointsByBackupVault
- connect:ListSecurityKeys
- connect:DescribeInstance
- connect:DescribeInstanceStorageConfig
- connect:ListInstances
- connect:ListInstanceStorageConfigs
- connect:ListApprovedOrigins
- codeguru-reviewer:ListRepositoryAssociations
- codeguru-reviewer:ListCodeReviews
- codeguru-reviewer:DescribeRepositoryAssociation
- codeguru-reviewer:DescribeCodeReview
- codeguru-profiler:ListProfilingGroups
- codeguru-profiler:DescribeProfilingGroup
- apprunner:ListAssociatedServicesForWebAcl
- waf-regional:ListRules
- waf-regional:GetRule
- waf-regional:ListIPSets
- waf-regional:GetIPSets
- waf-regional:ListRuleGroups
- waf-regional:GetRuleGroup
- waf-regional:ListActivatedRulesInRuleGroup
- cognito-idp:ListResourcesForWebACL
- sagemaker:ListUserProfiles
- sagemaker:DescribeUserProfile
- sagemaker:ListNoteBookInstances
- sagemaker:DescribeNoteBookInstance
- sagemaker:ListLabelingJobs
- sagemaker:DescribeLabelingJob
- logs:ListLogDeliveries
- finspace:GetEnvironment
- finspace:ListEnvironments
- forecast:DescribeDataset
- forecast:DescribeDatasetGroup
- forecast:ListDatasetGroups
- frauddetector:GetDetectors
- frauddetector:GetOutcomes
- frauddetector:DescribeDetector
- codeartifact:ListDomains
- codeartifact:DescribeDomain
- codeartifact:ListRepositories
- codeartifact:DescribeRepository
- personalize:ListDatasetGroups
- personalize:DescribeDatasetGroup
- panorama:DescribeApplicationInstance
- panorama:DescribePackage
- panorama:ListPackages
- panorama:ListApplicationInstances
- glue:GetSecurityConfiguration
- glue:GetSecurityConfigurations
- serverlessrepo:GetApplication
- kendra:ListFaqs
- kendra:DescribeFaq
- kendra:LIstDataSources
- kendra:DescribeDataSource
-
[]
- s3:GetObjectAcl
- s3:GetObject
[]
- s3:ListBucket
[]
- ec2:CreateSnapshot*
- ec2:CreateTags
- ec2:CopySnapshot
- ec2:ModifySnapshotAttribute
- kms:Decrypt
- kms:Encrypt
- kms:ReEncrypt*
- kms:CreateGrant
- kms:GenerateDataKeyWithoutPlaintext
- kms:PutKeyPolicy
- ec2:DeleteSnapshot
[]
- ecr:GetAuthorizationToken
- ecr:ListImages
- ecr:BatchGetImage
- ecr:DescribeImages
- ecr:DescribeRepositories
- ecr:GetRepositoryPolicy
- ecr:BatchCheckLayerAvailability
- ecr:GetDownloadUrlForLayer
- ec2:DescribeRegions
[]
To onboard an AWS cloud account or an AWS organization to ZPC:
- You need to have access to the administrative AWS management account.
- You need to be a ZPC administrator. To learn more, see [About Administrators](/zpc/about-administrators).
[]
To onboard an AWS organization to ZPC:
- Go to **Administration** > **Cloud Accounts**.
- Click **Add Account**.
- Under **Select Cloud Type**, click the **AWS** tile.
[See image.](#general-information-org)
- Under **Select Onboarding Type**, click the **Organization** tile.
- Click **Next**.
- On the **Configuration** page, you can:
- View the prerequisites for running the configuration script. The configuration bash script lists all the AWS member accounts.
- Copy the configuration bash script.
[See image.](#org-onboarding)
- On the [AWS Management Console](https://aws.amazon.com/console/), run the copied bash script on the AWS CloudShell.
- After the script is deployed, in the ZPC Admin Portal, click **Next**.
- Select the AWS accounts you want to onboard to ZPC.
- Select your business unit from the drop-down menu.
- On the **Deploy Template** page, you can:
- View the prerequisites for running the deploy template bash script. The deploy template script onboard all selected AWS accounts to ZPC.
- Copy the deploy template bash script.
- On the [AWS Management Console](https://aws.amazon.com/console/), run the copied bash script on the AWS CloudShell.
- After the script is deployed, in the ZPC Admin Portal, click **Finish**.
[]
To onboard an AWS account on to ZPC:
- Go to **Administration** > **Cloud Accounts**.
- Click **Add Account**.
- Under **Select Cloud Type**, click the **AWS** tile.
[See image.](#general-information-account)
- Under **Select Onboarding Type**, click the **Account** tile.
- Click **Next**.
- On the **Configuration** page, you can:
- Select your business unit from the drop-down menu.
- View the prerequisites for running the configuration script. The configuration bash script lists all the AWS member accounts.
- Copy the configuration bash script.
[See image.](#acc-onboarding)
- On the [AWS Management Console](https://aws.amazon.com/console/), run the copied bash script on the AWS CloudShell.
- After the script is deployed, in the ZPC Admin Portal, click **Finish**.
[]
![View the general information page in onboarding.](/downloads/zpc/administration/cloud-accounts/onboarding-amazon-web-services-account/zpc-aws-onboarding-general-information.png?1688122320)
[]
![View the configuration page for onboarding an AWS organization.](/downloads/zpc/administration/cloud-accounts/onboarding-amazon-web-services-account/zpc-aws-org-onboarding.png?1673877915)
[]
![View the general information page in onboarding.](/downloads/zpc/administration/cloud-accounts/onboarding-amazon-web-services-account/zpc-aws-onboarding-account-general-information.png)
[]
![View the configuration page for onboarding an AWS account.](/downloads/zpc/administration/cloud-accounts/onboarding-amazon-web-services-account/zpc-aws-account-onboarding.png?1673877975)