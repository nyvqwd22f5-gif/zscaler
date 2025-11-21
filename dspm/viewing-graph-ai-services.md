# Viewing the Graph for AI Services
Source: https://help.zscaler.com/dspm/viewing-graph-ai-services
PDF: https://help.zscaler.com/pdf/com/en/1524201.pdf

The graph for an AI service is a visual representation of the data scan result for the service. It depicts the access path for the AI service (Azure AI Foundry Hub or AWS Bedrock Knowledge Base) where it has access to the storage account containing sensitive data. DSPM also detects if the AI service is publicly exposed to the internet, including the public exposure path, and the list of entities that can access the AI service. These details are helpful to quickly evaluate and remediate the issues, protect the sensitive data, and maintain a strong security posture.
You can view graphs for the following AI services:
- AWS Bedrock Custom Model
- AWS Bedrock Imported Model
- AWS Bedrock Knowledge Base
- Azure AI Foundry Hub
- Azure AI Foundry
- Azure OpenAI
To view the graph for an AI service:
- Go to **Analytics** > **Resource Inventory**.
- On the **Resource Inventory** page, click the **AI service**.
- The graph is displayed on the **Risk Explorer** tab.
- [Azure AI Foundry Hub](#AzureAIFoundryHub)
- [AWS Bedrock Knowledge Base](#awsbedrockknowledgebase)
[]The following image is a sample of an Azure AI Foundry Hub graph:
[See image.](#ds-ai-graph)
Click the nodes to view additional details of each entity:
- [Storage Account](#ds-ai-st-acct)
- [Sensitive Record](#ds-ai-sensitiverecorddetails)
- [Public Internet](#ds-ai-pedetails)
- [Model](#ds-azureai-models)
- [Deployment](#ds-azureai-deployment)
- [Users](#ds-ai-userlist)
- [External](#ds-ai-externalentities)
- [Applications](#ds-ai-apps)
- [Services](#ds-ai-servicelist)
- [Managed Identity](#ds-ai-mgdidentity)
[]The following image is a sample of an AWS Bedrock Knowledge Base graph:
[See image](#ds-aws-bedrock-main-graph)
Click the nodes to view additional details of each entity:
- [Primary Resource](#ds-primaryresourceaws)
- [Resource](#ds-ai-resource-awsbedrock)
- [Model](#ds-awsbedrock-modelnode)
- [Resource with Sensitive Data](#ds-ai-awsbedrock-sensitivedataresource)
- [Sensitive Data Records](#ds-ai-awsbedrock-sensitivedatarecords)
- [Users](#ds-ai-awsbedrock-users)
- [Roles](#ds-ai-awsbedrock-roles)
- [Services](#ds-ai-awsbedrock-services)
- [Federated](#ds-ai-awsbedrock-federated)
- [External](#ds-ai-awsbedrock-external)
[]
![AWS Bedrock Knowledge Base has access to sensitive data records.](/downloads/dspm/analytics/graphs/viewing-graph-ai-services/ds-awsbedrock-graph.png)
[]View the list of models.
![List of models associated with the AWS Bedrock Knowledge Base.](/downloads/tech-pubs-drafts/dspm-draft-articles/1-12-0-viewing-graph-ai-services/ds-models-aws.png)
[]View details of AWS Bedrock Knowledge Base.
- **Data Store Type**: The type of data store.
- **Resource Type**: The type of primary resource.
- **Account ID**: The unique identifier of the account to which the primary resource belongs.
- **Account Name**: The name of the account in which the resource is located.
- **Organization ID**: The unique identifier of the organization to which the project belongs.
- **Region**: The region where the resource is located.
- **Last Completed Scan**: The status of the last scan.
- **Triggers**: Number of alerts raised for the resource.
- **Matched Files**: The number of files that matched the DLP engines.
- **DLP Engines**: The [DLP engines](/dspm/understanding-dlp-engines-and-dictionaries) that match sensitive records.
- **DLP Dictionaries**: The dictionaries associated with the DLP engines.
- **Document Categories**: The category of document detected in the resource.
- **Document Types**: The number of documents detected in the resource.
- **ARN**: Copy the Amazon Resource Name (ARN) to identify this resource in the AWS account.
- **Tags**: The tags associated with the resource.
- **Posture**: The [security posture ](/dspm/understanding-security-posture-state)of the resource.
![Details of the primary source with blurred out sensitive information.](/downloads/tech-pubs-drafts/dspm-draft-articles/doc-60745-viewing-graph-ai-services/IMG-1.png)
[]View details of the Amazon Bedrock resource types.
![A list of resource types available in the AWS Bedrock Knowledge Base.](/downloads/tech-pubs-drafts/dspm-draft-articles/doc-60745-viewing-graph-ai-services/img-2.png)
[]View the list of users who can access the resource.
![A list of users and their access level to a resource, and blurred out sensitive information.](/downloads/tech-pubs-drafts/dspm-draft-articles/doc-60745-viewing-graph-ai-services/img-3.png)
[]View the identity and access management (IAM) roles that has permissions to access the resource.
![A list of IAM roles that have permission to access the resource, and blurred out sensitive information.](/downloads/tech-pubs-drafts/dspm-draft-articles/doc-60745-viewing-graph-ai-services/img-5.png)
[]View the services that can access the resource.
![A list of services that can access the resource, and blurred out sensitive information.](/downloads/tech-pubs-drafts/dspm-draft-articles/doc-60745-viewing-graph-ai-services/img-6.png)
[]View the external entities that can access the resource. These entities are part of a different cloud account that is not onboarded to the DSPM Admin Portal.
![A list of external entities that can access the resource, and blurred out sensitive information.](/downloads/tech-pubs-drafts/dspm-draft-articles/doc-60745-viewing-graph-ai-services/img-7.png)
[]View the federated identities that can access the resource.
![A list of federated identities that can access the resource, and blurred out sensitive information.](/downloads/tech-pubs-drafts/dspm-draft-articles/doc-60745-viewing-graph-ai-services/img-8.png)
[]View details of the resources that contain sensitive data.
![Lists the resources that contain sensitive data records.](/downloads/tech-pubs-drafts/dspm-draft-articles/doc-60745-viewing-graph-ai-services/img-9.png)
[]View details of the sensitive record.
![The sensitive data records for an AWS Bedrock Knowledge Base with blurred out sensitive information.](/downloads/tech-pubs-drafts/dspm-draft-articles/doc-60745-viewing-graph-ai-services/img-10.png)
[]![Azure AI Foundry Hub has access to sensitive records.](/downloads/tech-pubs-drafts/dspm-draft-articles/1-12-0-viewing-graph-ai-services/ds-azurefoundry-graph_0.png)
[]The storage account that contains the sensitive records.
- **Go to Azure**: Access the Azure portal to view the storage account.
- **Metadata**: Click to view the metadata for the account.
- **View Sensitive Data**: Click to view the details of the sensitive records stored in the storage account.
![The scan result for the storage account.](/downloads/dspm/analytics/graphs/viewing-graph-ai-services/ds-ai-azureacct.png)
[]The details of the sensitive record, including the DLP engines and dictionaries that match the record, the security posture of the record, ID and tags, and the timestamp of the last completed scan.
![The details of the file containing credit card numbers.](/downloads/dspm/analytics/graphs/viewing-graph-ai-services/ds-ai-sensitiverecord.png)
[]The reason why the AI service is publicly exposed to the internet.
![Details of how the Azure AI Foundry instance is exposed to the internet.](/downloads/dspm/analytics/graphs/viewing-graph-ai-services/d-ai-publicexposuredetails.png)
[]The users who can access the AI service.
![Viewing the list of users and their access levels to access the AI service](/downloads/tech-pubs-drafts/dspm-draft-articles/doc-60745-viewing-graph-ai-services/img-12.png)
[]The external entities that can access the AI service. These entities are part of a different cloud account that is not onboarded to the DSPM Admin Portal.
![Viewing the external entities that can access the AI service.](/downloads/tech-pubs-drafts/dspm-draft-articles/doc-60745-viewing-graph-ai-services/img-13.png)
[]The applications that can access the AI service.
![Applications that can access the AI service.](/downloads/tech-pubs-drafts/dspm-draft-articles/doc-60745-viewing-graph-ai-services/img-14.png)
[]The services that can access the AI service.
![The services that can access the AI service.](/downloads/tech-pubs-drafts/dspm-draft-articles/doc-60745-viewing-graph-ai-services/img-16.png)
[]The managed identities (service principals) that can access the AI service.
![The managed identities that can access the AI service.](/downloads/tech-pubs-drafts/dspm-draft-articles/doc-60745-viewing-graph-ai-services/img-18.png)
[]View the list of associated models.
![Lists all the models associated with Azure AI Foundry Hub.](/downloads/tech-pubs-drafts/dspm-draft-articles/doc-60745-viewing-graph-ai-services/img-19.png)
[]View the list of all the deployments.
![List of all the deployments in Azure AI Foundry Hub.](/downloads/tech-pubs-drafts/dspm-draft-articles/draft-viewing-graph-ai-services/ds-azureai-deployments.png)