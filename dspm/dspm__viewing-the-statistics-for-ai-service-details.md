# Viewing the Statistics for AI Service Details
Source: https://help.zscaler.com/dspm/viewing-the-statistics-for-ai-service-details
PDF: https://help.zscaler.com/pdf/com/en/1529528.pdf

DSPM scans and identifies AI services and models that have access to resources containing sensitive data. The AI Security tab on the DSPM dashboard provides statistics of the data that is exposed to the AI services and models, the top data type exposed to the AI services, and more.
[See image.](#ds-aidashboardgif)
[]
![Shows a high-level overview of all AI Services and foundation models within the cloud environment.](/downloads/dspm/dashboard/viewing-the-statistics-for-ai-service-details/ai-security-gif.gif)
Widgets
The following widgets are shown on the AI Security tab. You can apply filters to view data specific to clouds, business units, accounts, regions, etc.
- [AI Metrics](#ds-aimetrics)
- [Data Exposed to AI Models](#ds-dataexposedtomodels)
- [Data Exposed to AI Services](#ds-dataexposedtoservices)
- [Top Data Shared with AI](#ds-topdatasharedwithai)
- [AI Insights](#ds-aiinsights)
[]View metrics related to the AI services deployed in your cloud environment.
-
**Deployed AI**: The number of AI services deployed across the cloud environment. You can view the details for the following AI services:
- AWS Bedrock Custom Model
- AWS Bedrock Imported Model
- AWS Bedrock Knowledge Base
- Azure AI Foundry Hub
- Azure AI Foundry
- Azure OpenAI
Click the tile to view the AI service details on the [Resource Inventory page.](/dspm/about-resource-inventory)
- **Data Shared with AI**: The number of data stores and files that can be accessed by the AI services. Click the number to view the data store details on the [Resource Inventory page.](/dspm/about-resource-inventory)
- **AI Tools & Packages Vulnerabilities**: The AI tools and packages that have vulnerabilities. Click the number to view the details on [AI & ML](/dspm/viewing-ai-service-details) tab on the Resource Inventory page.
- **Open Alerts on AI Resources**: The number of open alerts triggered for misconfigurations detected in the AI services. Click the tile to view the details on the [Alerts page](/dspm/about-alerts).
[See image.](#ds-aimetricsimage)
[]
![Shows metrics related to the AI services deployed in the cloud infrastructure.](/downloads/tech-pubs-drafts/dspm-draft-articles/1-14-0-viewing-statistics-ai-service-details/ds-ai-metrics.png)
[]AI services might use sanctioned or unsanctioned AI models, deployed through managed cloud service providers or self-managed cloud infrastructures. Some of these models could be potentially risky and expose sensitive data. Monitoring the AI models is crucial for identifying vulnerabilities and misconfigurations, preventing breaches, and ensuring compliance.
- Select the AI Model tab to view a list of all the AI models.
- [Managed AI Models](#ds-managedaimodels)
- [Unmanaged AI Models](#ds-unmanagedaimodels)
- Click the service under the Services column to view the [Resource Inventory page](/dspm/about-resource-inventory) that shows sensitive data that can be accessed by the AI model.
[]View all the managed AI models, along with the DLP engines and DLP triggers that match the files containing sensitive data.
![Shows the list of all the managed AI models that can access sensitive data.](/downloads/tech-pubs-drafts/dspm-draft-articles/1-12-0-viewing-ai-and-machine-learning-details/ds-managedaimodels.png)
[]View all the unmanaged AI models, along with the DLP engines and DLP triggers that match the files containing sensitive data.
![Shows the list of all the unmanaged AI models that can access sensitive data.](/downloads/tech-pubs-drafts/dspm-draft-articles/1-12-0-viewing-ai-and-machine-learning-details/ds-unmanagedaimodel.png)
[]DSPM provides a comprehensive overview of AI services deployed through managed cloud service providers and self-managed cloud infrastructures.
Select the AI Services tab to view a list of all the AI services.
- [Managed AI Services](#ds-managedaiservices)
- [Unmanaged AI Servces](#ds-unmanagedaiservices)
[]View all the managed AI services, along with the DLP engines and DLP triggers that match the files containing sensitive data. Click the AI service name under the Service Name column to view the [graph ](/dspm/viewing-graph-ai-services)that depicts the resources and sensitive records that can be accessed by the AI service.
![Shows list of all managed AI services that can access sensitive data.](/downloads/tech-pubs-drafts/dspm-draft-articles/1-12-0-viewing-ai-and-machine-learning-details/ds-managedaiservices.png)
[]View all the unmanaged AI services, along with the DLP engines and DLP triggers that match the files containing sensitive data.
![Shows the list of all unmanaged AI services that can access sensitive data.](/downloads/tech-pubs-drafts/dspm-draft-articles/1-12-0-viewing-ai-and-machine-learning-details/ds-unmanagedaiservices.png)
[]The chart displays the total number of files that can be accessed by the AI services. The chart displays the total number of files that can be accessed by the AI services.
-
**Gen AI Classificatio**n: Click each circle to view the total number of files for a specific document type along with the documents' subcategories.
[See image.](#ds-genaiclassificationimage)
-
**DLP Engines**: Click each circle to view the total number of files and tables shared with AI services along with DLP engines and dictionaries that match the files containing sensitive data. Select the **Show Sensitive Data Only **checkbox to view only those DLP engines that are marked as sensitive.
[See image.](#ds-dlpenginesimage)
[]
![Top data shared with AI services based on GenAI classification.](/downloads/dspm/dashboard/viewing-the-statistics-for-ai-service-details/ds-top-data-genai.png)
[]
![Data shared with AI services based on DLP engines.](/downloads/dspm/dashboard/viewing-the-statistics-for-ai-service-details/top-data-dlp.png)
[]View the total number of open alerts corresponding to each [Insight category](/dspm/viewing-insights-dashboard) displayed in the tiles. Click the number to view the details on the [Alerts page](/dspm/about-alerts).
[See image.](#ds-aiinisghtsimage)
[]
![Shows different Insights categories in tiles and their number of open alerts.](/downloads/tech-pubs-drafts/dspm-draft-articles/1-14-0-viewing-statistics-ai-service-details/ds-ai-inisghts.png)