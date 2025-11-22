# Configuring Lures Using AWS Decoys
Source: https://help.zscaler.com/deception/configuring-lures-using-aws-decoys
PDF: https://help.zscaler.com/pdf/com/en/1531513.pdf

After configuring the [integration between Amazon Web Services (AWS) and Zscaler Deception](/deception/setting-cloud-deception-aws#zd-integration-aws-decoys) and [deploying the necessary decoys](/deception/setting-cloud-deception-aws#zd-aws-decoys-setup), you can use the decoys to set up lures for attackers. You can use different methods to set up lures depending on the type of decoys, as explained in the following sections:
- [IAM Decoys](#zd-iam-decoy-lure)
- [S3 Decoys](#zd-s3-decoy-lure)
- [RDS Decoys](#zd-rds-decoy-lure)
- [ECR Decoys](#zd-ecr-decoy-lure)
- [DynamoDB Decoys](#zd-dynamo-db-decoy-lure)
- [VM Image Decoys](#zd-vmi-decoy-lure)
- [Generative AI Decoys](#generative-ai-decoys)
[]IAM decoys in AWS are decoys that mimic legitimate users. You can lure attackers using user decoys by placing their credentials on endpoints via landmine policies. The landmine agents create a logged-on session using the user decoy credentials which allows users to access other decoy resources. You can place credentials of user decoys on endpoints by configuring lures using the following methods:
- [Cloud Lures](/deception/configuring-cloud-lures)
- [Session Lures via Bash History](/deception/configuring-session-lures)
- [File Decoys via Credential Files](/deception/configuring-file-decoys)
If an adversary uses the decoy credentials to log in to AWS or access decoy resources, the event is logged as an attack. You can view and analyze the attack details from the [Deception dashboard](/deception/viewing-and-managing-zscaler-deception-dashboard).
To learn more about IAM users in AWS, refer to the [AWS documentation](https://docs.aws.amazon.com/IAM/latest/UserGuide/introduction.html).
[]The Simple Storage Service (S3) is an object-based storage service in AWS. Deception allows you to create decoy S3 buckets that allow you to host decoy file datasets on the cloud to lure attackers. You can deploy S3 decoys as either public or private decoys. If the decoy is configured as public, then an adversary can discover and enumerate the files hosted using various tools. If the S3 decoy is configured as private, then you need to set up lures using the following methods:
- [Browser Lures](/deception/configuring-browser-lures)
- [Session Lures via Bash History](/deception/configuring-session-lures)
- [File Decoys via Credential Files](/deception/configuring-file-decoys)
An interaction with the S3 decoy is logged as an attack. You can view and analyze the attack details from the [Deception dashboard](/deception/viewing-and-managing-zscaler-deception-dashboard).
To learn more about S3 in AWS, refer to the [AWS documentation](https://docs.aws.amazon.com/AmazonS3/latest/userguide/Welcome.html).
[]The Relational Database Service (RDS) in AWS is a web service that allows you to set up and host relational databases on the cloud. Deception allows you to create decoy relational databases and host them in RDS to lure adversaries and detect the interactions. You can configure lures for RDS decoys on endpoints using the following methods:
- [Browser Lures](/deception/configuring-browser-lures)
- [Session Lures via Bash History](/deception/configuring-session-lures)
- [File Decoys via Credential Files](/deception/configuring-file-decoys)
An interaction with the RDS decoy is logged as an attack. You can view and analyze the attack details from the [Deception dashboard](/deception/viewing-and-managing-zscaler-deception-dashboard).
To learn more about RDS in AWS, refer to the [AWS documentation](https://docs.aws.amazon.com/AmazonRDS/latest/UserGuide/Welcome.html).
[]An Elastic Container Registry (ECR) is a service in AWS that hosts Docker images. Deception allows you to create ECR decoys that can be used to lure adversaries and detect their interactions with ECR decoys. You can use an ECR decoy to lure attackers to push or pull docker images. You can configure lures for ECR decoys on endpoints using the following methods:
- [Browser Lures](/deception/configuring-browser-lures)
- [Session Lures via Bash History](/deception/configuring-session-lures)
- [File Decoys via Credential Files](/deception/configuring-file-decoys)
An interaction with the ECR decoy is logged as an attack. You can view and analyze the attack details from the [Deception dashboard](/deception/viewing-and-managing-zscaler-deception-dashboard).
To learn more about ECR in AWS, refer to the [AWS documentation](https://docs.aws.amazon.com/AmazonECR/latest/userguide/what-is-ecr.html).
[]DynamoDB is a NoSQL, key-value pair database in AWS. Deception allows you to create decoy DynamoDB databases that can lure adversaries and detect their interactions. You can configure lures for DynamoDB decoys on endpoints using the following methods:
- [Session Lures via Bash History](/deception/configuring-session-lures)
- [File Decoys via Credential Files](/deception/configuring-file-decoys)
An interaction with the DynamoDB decoy is logged as an attack. You can view and analyze the attack details from the [Deception dashboard](/deception/viewing-and-managing-zscaler-deception-dashboard).
To learn more about DynamoDB in AWS, refer to the [AWS documentation](https://docs.aws.amazon.com/amazondynamodb/latest/developerguide/Introduction.html).
[]Virtual Machine (VM) images are used on AWS to launch new instances of your virtual machines. Deception allows you to create VM image decoys in AWS that can lure adversaries and detect attempts of exfiltration of data. A VM image decoy can be configured as a public or private decoy. You can use [browser lures](/deception/configuring-browser-lures) or [session lures](/deception/configuring-session-lures) to configure lures for VM image decoys. When an adversary uses the VM image decoy and boots it up to launch an instance, the VM image decoy communicates with Deception and logs the event as an attack. You can view and analyze the attack details from the [Deception dashboard](/deception/viewing-and-managing-zscaler-deception-dashboard).
To learn more about VM images in AWS, refer to the [AWS documentation](https://docs.aws.amazon.com/AWSEC2/latest/UserGuide/AMIs.html).
[]Amazon Bedrock is a fully managed service that makes high-performing foundation models from leading AI companies and Amazon available for your use through a unified API. Deception allows you to create generative AI decoys using these foundation models. The generative AI decoys are interactive, and you can customize the decoys to generate fake responses to lure attackers into entering more prompts. You can also log the prompts and responses between the adversary and the generative AI decoy to gain insights into the objectives of the adversaries. When an adversary accesses or interacts with the generative AI decoy, the event is logged as an attack. You can view and analyze the attack details from the [Deception dashboard](/deception/viewing-and-managing-zscaler-deception-dashboard).
To learn more about generative AI models in AWS, refer to the [AWS documentation](https://docs.aws.amazon.com/bedrock/latest/userguide/what-is-bedrock.html).