# Viewing the AI Inventory Details
Source: https://help.zscaler.com/dspm/viewing-ai-inventory-details
PDF: https://help.zscaler.com/pdf/com/en/1532164.pdf

The Artificial Intelligence (AI) Inventory displays AI models, AI services, AI tools and packages, and risks associated with the AI resources. This allows you to analyze and remediate the risks.
The AI Inventory provides a tabular view of AI resources that exist across all the onboarded cloud accounts:
- **AI Tools & Packages**: AI packages detected in the virtual machines (e.g., AWS EC2 instance).
- **Models**: All managed AI models (e.g., AWS Bedrock Knowledgebase), unmanaged AI models (e.g., installed on VMs via Ollama or Hugging Face), and customized models or imported models used by the organization.
- **Services**: AI Services configured on onboarded cloud accounts.
To view the AI resource details:
- Go to **Analytics **> **AI Inventory**.
- On the **AI Inventory** page, you can view the following details:
- [AI Tools & Packages](#ds-ai-tools-packages)
- [Models](#ds-models)
- [Services](#ds-services-tab)
- Export the data and [download the report](/dspm/downloading-reports) as an Excel file.
- Go to **Default View** > **Save as New View** at the top right to save a view. You can set a default view for a page which loads by default whenever you visit the page.
[]
- **Package Name**: The name of the AI package. Click the package name to [view additional details.](#ds-additional-details)
- **Package Version**: The version of the AI package.
- **Service Type**: The number of services using the package (e.g., AWS EC2 instance). Click the number to access a filtered view of the [Resource Inventory](/dspm/about-resource-inventory) page.
- **Package Type**: The type of AI package (e.g., Data Manipulation & Processing, Large Language Models (LLMs), MLOps Tools etc.).
- **Vulnerable**: The state of the vulnerability discovered in the package.
- **Severity Count**: The vulnerability statistics showing the number of critical, high, medium, low, or unknown vulnerabilities.
- **Status**: The usage approval status of the package. The default value is **Pending Review**. Click the **Action **icon and mark the approval status of the package for use within the organization as **Sanctioned **or **Unsanctioned**.
[See image.](#ds-ellipsis)
- **Package Tags**: The metadata tags associated with the package.
- **Package Language**: The coding language associated with the AI package (Python, C++, etc.).
[See image.](#ds-ai-tools-packages-img)
[]
- Description of the AI package.
- General information such as associated cloud service providers, region, service type, and severity count.
- Other details like Package Version, Package Type, Package Language, and Package Version.
You can click the **Actions **dropdown at the top-right to mark the package as **Sanctioned **or **Unsanctioned**.
![Shows additional details about the AI package](/downloads/tech-pubs-drafts/dspm-draft-articles/1-14-0-viewing-ai-inventory/ds-ai-package-addition_0.png)
[]
![Shows the AI package details](/downloads/tech-pubs-drafts/dspm-draft-articles/1-14-0-viewing-ai-inventory/ds-ai-tools-packages-new.png)
[]
![Shows the approval status of the package](/downloads/tech-pubs-drafts/dspm-draft-articles/1-14-0-viewing-ai-inventory/ds-extra.png)
[]
- **Model Name**: The name of the AI model. Click the model name to [view additional details.](#ds-additional-details-models)
- **Sub Model Type**: The type of AI model (e.g., Managed Model, Unmanaged Model, Custom Model etc.).
- **Service Type**: The number of AI services using the models (e.g., AWS Bedrock, Azure AI Foundry). Click the number to access a filtered view of the [Resource Inventory page](/dspm/about-resource-inventory) showing the services running the AI model.
- **DLP Engines**: The DLP engines used to classify the data.
- **Document Types**: The different document types present in the AI model.
- **Country**: The country where the AI service hosting the AI model is deployed.
- **Status**: The usage approval status of the model. The default value is **Pending Review**. Click the **Action **icon and mark the approval status of the model for use within the organization as **Sanctioned **or **Unsanctioned**.
- **Model URI**: The unique identifier of the AI model.
- **Last Updated**: The date and time when the AI model was last modified.
[See image.](#ds-models-tab)
[]
![Shows the details of all the AI models ](/downloads/tech-pubs-drafts/dspm-draft-articles/1-14-0-viewing-ai-inventory/ds-models-img.png)
[]
- Description of the AI model.
- **Cloud**: The number of cloud service providers associated with the AI model.
- **Services**: The number of services associated with the AI model.
- Other data such as Model URL, Sub Model Type, origin, and last updated details.
You can click the **Actions **dropdown at the top-right to mark the model as **Sanctioned **or **Unsanctioned**.
![Shows the additional details of AI models](/downloads/tech-pubs-drafts/dspm-draft-articles/1-14-0-viewing-ai-inventory/ds-model-additional-details.png)
[]
- **Resource Name**: The name of the AI service. Click the resource name to view additional details.
- [Resource Details](#ds-resource-details)
- [Resource Metadata](#ds-resource-metadata)
- **DLP Engines**: The DLP engines used to classify the data.
- **Document Types**: The different document types present in the AI service.
- **Service Type**: The type of service (e.g., microsoft.compute) used to deploy the AI service.
- **Posture**: The security posture of the AI service. Hover over the label to see the description of each posture.
- **Risk Level**: The severity of risk associated with the service.
- **Tags**: The tags associated with the service.
- **Cloud**: The cloud service provider where the service is hosted.
[See image.](#ds-ai-services-img)
[]
- **Service Description**: View a brief description of the service.
- **General Information**: View cloud, resource type, resource tags, service type, and posture details.
- **Other Information**: View subscription ID, subscription name, tenant ID, and region details.
![Additional details about the selected resource ](/downloads/tech-pubs-drafts/dspm-draft-articles/1-14-0-viewing-ai-inventory/ds-resource-details-ai_0.png)
[]View the metadata details of the resource. Click **Download JSON** to save the data as a JSON file.
![Metadata details of the selected resource](/downloads/tech-pubs-drafts/dspm-draft-articles/1-14-0-viewing-ai-inventory/ds-resource-metedata_0.png)
[]
![Shows the details of all the AI services](/downloads/tech-pubs-drafts/dspm-draft-articles/1-14-0-viewing-ai-inventory/ds-ai-services-img.png)