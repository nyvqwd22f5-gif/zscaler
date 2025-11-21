# Viewing the AI Service Details
Source: https://help.zscaler.com/dspm/viewing-ai-service-details
PDF: https://help.zscaler.com/pdf/com/en/1529815.pdf

The increasing usage of AI, whether deployed through managed AI services or self-managed infrastructures like open-source AI models, libraries and tools, requires robust management and security strategies. Unmanaged AI models lack management frameworks leading to security risks. Monitoring and tracking such models helps reduce significant risks to the security of cloud environments and ensures that the AI applications are secure and compliant.
DSPM scans and provides a comprehensive overview of AI & Machine Learning models and packages installed on virtual machines (LLM models running via [OLLAMA](https://ollama.com/) and [Hugging Face](https://huggingface.co/) deployed inside a VM). This provides insights about the AI models and packages.
To view the AI service details:
- Go to **Analytics **> **Resource Inventory**.
[See image.](#ds-resourceinventorypage)
- Click any AI resource name.
-
Select the **AI & ML** tab to view details about AI models and packages. The AI service details detected in an AWS EBS volume is provided here as an example.
The **AI Models** tab is selected by default.
- [AI Models](#ds-aimodels)
- [AI Packages](#ds-aipackage)
[]
- **Model Name**: The name of the AI model.
- **Volume**: The disk attached to the instance in which the AI model is installed.
- **Operating Platform**: The platform (e.g., Ollama or Hugging Face) used for managing and running the AI model.
- **Path**: The file path of the AI model.
- **Vendors**: The vendor providing the AI model.
- **Multi-Modal:** Whether the AI model supports different types of data generation, such as image, sound, etc.
- **Country**: The country where the AI model was originally developed.
- **Description**: A brief explanation about the AI model.
- **Number of Downloads**: The number of downloads associated with the model.
- **Origin**: The company that owns the AI model.
- **Model URL**: The URL associated with the AI model.
[See image.](#ds-aimodelstab)
[]
- **Package Name**: The name of the package. Click the package name to [view the vulnerability details.](#ds-vulnerability_details_package)
[See image.](#ds-aipackagedetailspage)
- **Package Type**: The type of the package (e.g., machine learning pipeline package).
- **Path**: The file path of the package.
- **Package Version**: The version of the package.
- **Vulnerable**: Whether the package is vulnerable or not.
- **Language: **The coding language associated with the AI package.
[See image.](#ds-aipackagestab)
[]
![Shows additional details about the selected AI package.](/downloads/tech-pubs-drafts/dspm-draft-articles/1-12-0-viewing-ai-service-details/ds-resourceinventory-aipackage-details%20page.png)
[]
![Shows the list of all the resource types available in your cloud infrastructure.](/downloads/tech-pubs-drafts/dspm-draft-articles/1-12-0-viewing-ai-service-details/ds-resourceinventory.png)
[]
![Shows all the AI models associated with the selected resource.](/downloads/tech-pubs-drafts/dspm-draft-articles/1-13-0-viewing-ai-service-details/ds-volume.png)
[]
![Shows all the AI packages associated with the selected resource.](/downloads/tech-pubs-drafts/dspm-draft-articles/1-12-0-viewing-ai-service-details/ds-resourceinventory-aipackages.png)
[]
-
**CVE ID**: The unique number assigned to the security vulnerability. Click the CVE ID to view the following vulnerability details:
- **Link to NVD**: View the CVE details on the [national vulnerability database (NVD) website](https://nvd.nist.gov/).
- **Link to CVE Details**: View the CVE details on the [CVE website](https://nvd.nist.gov/).
- **Package Name**: The name of the impacted package.
- **Package Version**: The version of the impacted package.
- **Fixed Version**: The version that includes a fix for the detected vulnerability.
- **Age of CVE**: The number of days and months since the CVE was first published.
- **Last Published Date**: The date when the CVE was last published.
- **Last Modified Date**: The date when the CVE was last updated.
- **Vulnerability Description**: A brief description about the vulnerability.
[See image.](#ds-vulnerabilitydetails)
- **Account:** The account in which the AI package is stored.
- **Severity**: The severity of the vulnerability (Low, Medium, High, Critical).
- **CVSS Score**: The standardized numerical score for assessing the severity of the vulnerability.
- **Package Name**: The name of the package.
- **Package Version**: The version of the package.
- **Provider**: The name of the cloud service provider.
- **Package Path**: The file path of the package.
- **Fix Available**: Whether a fix version is available or not.
- **Fixed Version**: The version that includes a fix for the vulnerability.
[]
![Shows the vulnerability details associated with the resource](/downloads/tech-pubs-drafts/dspm-draft-articles/1-13-0-viewing-ai-service-details/ds-vulnerability%20details.png)