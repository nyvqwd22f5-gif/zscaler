# Viewing the Public Exposure Path
Source: https://help.zscaler.com/dspm/viewing-public-exposure-path
PDF: https://help.zscaler.com/pdf/com/en/1480566.pdf

Attack paths allow you to address security issues in your cloud infrastructure. A public exposure path is an attack path that shows the resources that contain sensitive data and are publicly exposed, which could allow adversaries to directly access such resources from the internet, leading to data breaches.
DSPM scans your cloud accounts and detects such publicly exposed resources along with the vulnerabilities or misconfigurations in the different components (network security group, load balancer, virtual network, etc.) that are associated with the resource. This information enables you to quickly analyze and remediate the issue.
[See image.](#ds-graphanimation)
The public exposure path is enabled only for the EC2 instances, virtual machines, and DB cluster resources.
To view the graph for a public exposure path:
- Go to **Analytics** > **Resource Inventory**.
-
On the **Resource Inventory** page, click the **Resource Name**.
[See image.](#ds-resource)
The graph is displayed on the **Risk Explorer** tab.
[See image.](#ds-riskexplorergraph)
- Click the **Public Internet** node to view the associated components through which the primary resource is exposed to the internet.
[See image.](#Public_internet_node_drawer)
-
Click **Show Public Exposure Path **to view a graph that visually represents the associated components, including those that have misconfigurations and vulnerabilities.
[See image.](#aws_public_exposure_path)
For cloud storage buckets and Azure containers, the reason for exposure is displayed with the following options:
- **View Metadata**: View the JSON file, copy or download the metadata, or go to the CSP portal to view the specific resource details.
[See image.](#View_metadata_for_storage_bucket)
- **Verify Exposed Files**: View the list of publicly exposed files that can be accessed anonymously. You can copy the file path, download the file, or export the files in CSV format to investigate the issue. You can also go to the CSP portal to view the file details.
[See image.](#Verify_exposed_files)
- **Verify Static Website**: View the static website hosted in the storage bucket or container.
[See image.](#pi_balcony)
- Click each node to view additional details for the entity.
[See image.](#aws_subnet_details)
- Click the **Warning** icon (![ds-warnicon.png](/downloads/dspm/analytics/graphs/viewing-public-exposure-path/ds-warnicon.png)
) to see the security issue. [See image.](#aws_vulnerability_description)
- Click **Go to AWS **to view the details on the AWS portal.
- Click **</> Metadata** to view the JSON file, copy or download the metadata, or go to the CSP portal.
[See image.](#aws_metadata)
How the Resources are Publicly Exposed
The resources are publicly exposed in the following ways:
- [AWS](#aws_publicly_exposed_ways)
- [Azure](#azure_publicly_exposed_ways)
- [GCP](#gcp_publicly_exposed_ways)
[]
- **Exposure via Amazon S3 Block Public Access Misconfigurations**: AWS provides settings to block account level misconfigurations that might lead to public exposure. To block the S3’s public exposure at the account level, ensure IgnorePublicAcls and RestrictPublicBuckets settings are set to true.
- **Exposure via AWS S3 Bucket ACLs**: This S3 bucket can use bucket ACLs to manage access control of S3 buckets. One or more ACLs are granting access to the principals http://acs.amazonaws.com/groups/global/AllUsers or http://acs.amazonaws.com/groups/global/AuthenticatedUsers, allowing the S3 bucket to be publicly accessible. The bucket level exposure created by this configuration leads to the S3’ bucket’s directory listing and potential loss of sensitive data.
- **Exposure via AWS S3 Bucket Policies**: S3 bucket policies provide granular access control and governance for S3 buckets. One or more policy statements as part of the bucket policy is granting access to the principal "*" which is resulting in the S3 bucket’s public exposure. A publicly exposed S3 bucket has the potential to disclose sensitive data to unauthorized entities.
- **Exposure via Hosted Website**: Hosted websites allow an S3 bucket to serve static web content like HTML, CSS, JS, etc. An enabled static website might accidentally transmit sensitive data over the web and this should be monitored carefully.
[]
![View public internet node drawer](/downloads/dspm/analytics/graphs/viewing-public-exposure-path/ds-public_internet_node_drawer_0.png)
[]
![Public exposure path](/downloads/dspm/analytics/graphs/viewing-public-exposure-path/ds-public_exposure_path_0.png)
[]
![Viewing subnet details](/downloads/dspm/analytics/graphs/viewing-public-exposure-path/ds-public_exposure_path_node.png)
[]
![Vulnerability description](/downloads/tech-pubs-drafts/dspm-draft-articles/viewing-public-exposure-path-draft/Info%20Icon.png)
[]
![View metadata](/downloads/dspm/analytics/graphs/viewing-public-exposure-path/ds-public_exposure_metadata.png)
[]
- **Exposed to the Internet**: An SQL server configured with a firewall rule that permits traffic from 0.0.0.0 - 255.255.255.255 allows traffic to reach the SQL server from any source over the public internet. To mitigate exposure risk, configure a firewall rule to permit traffic only from specific IP addresses of the application instances that require access to the SQL server.
- **Exposed to All Azure Tenants**: An SQL server firewall configuration offers an option to create an exception to "Allow Azure services and resources to access this server". With this configuration, the server not only becomes available to resources within the Azure subscriptions and resource groups of the customer but to every Azure tenant including subscriptions that do not belong to the customer. To mitigate exposure risk, configure a firewall rule to permit traffic only from a specific source (IP addresses) that might require access to the SQL server.
- **Static Websites**: This Azure storage account supports hosting static websites. When enabled, this creates a container named $web. Any object stored within this $web container gets instantly exposed anonymously (irrespective of firewall or container ACL) via the storage account’s primary endpoint. Ensure no sensitive information is stored in this folder as it will become publicly accessible.
- **Azure Storage Account is Publicly Exposed via Shared Key**: Shared access keys are configured on this storage account along with public network access. Enabling public network access allows the storage account to access all the resources in the storage account via those access keys from anywhere on the internet. It is recommended to use Entra authorization for authenticated access to storage accounts, or prevent public network access for this storage account by allowing access only from trusted networks or IP addresses.
- **Containers with Anonymous Access**: Storage containers with an access list configured with "Anonymous Container Read Access" allow anyone to access data (blobs) stored within the container. This particular configuration results in directory listing and access to all files in a storage container. To allow public access to specific files, set the access list to "Blob Anonymous Access" and configure public visibility for individual files.
- **SFTP/SSH Access**: This Azure storage account supports SFTP/SSH access for Azure data lake storage accounts. The containers exposed via SFTP can be accessed publicly as network ACLs settings are not appropriately configured. If this account needs to be exposed publicly for SFTP access, ensure to use an SSH key. To reduce exposure, disable Public SFTP access and restrict it to specific networks or IPs.
[]![Shows the Resource Inventory listing all the scanned resources.](/downloads/dspm/analytics/graphs/viewing-public-exposure-path/ds-resourceinventory-aws.png)
[]![Shows the public exposure path details.](/downloads/dspm/analytics/graphs/viewing-public-exposure-path/ds-riskexplorergraph.png)
[]![Details of entities associated with the publicly exposed resource](/downloads/dspm/analytics/graphs/viewing-public-exposure-path/ds-publicexposure_0.gif)
[]
- **Google Cloud Storage Bucket is Publicly Exposed Anonymously**: This storage bucket is publicly accessible to anyone over the internet. Check the role bindings in JSON to know the storage bucket’s public access level. To remove public exposure, delete the allUsers principal from the storage bucket's IAM policy bindings.
- **Google Cloud Storage Bucket is Publicly Exposed to Google Accounts**: This storage bucket is accessible to anyone with a Google account. To remove public exposure, delete the allAuthenticatedUsers principal from the storage bucket's IAM policy bindings.
- **Google Cloud Storage Bucket is Publicly Exposed Anonymously via Managed Folders**: This storage bucket contains one or more managed folders that are accessible to anyone over the internet. Check the IAM policy bindings in JSON to know the folders’ public access level. To remove public exposure, delete the allUsers principal from the folder's IAM policy bindings.
- **Google Cloud Storage Bucket is Publicly Exposed to Google Accounts via Managed Folders**: This bucket contains one or more managed folders that are accessible to anyone with a Google account. To remove public exposure, delete the allAuthenticatedUsers principal from these folders’ IAM policy bindings.
- **Static Website**: This storage bucket contains publicly exposed resources along with a static website. This might make sensitive data publicly accessible over the advertised public endpoint of the bucket. If this bucket should not have static website enabled, disable the bucket’s static website feature.
[]![Viewing public internet drawer for storage buckets](/downloads/dspm/analytics/graphs/viewing-public-exposure-path/ds-public_internet_cloud_storage_1.png)
[]
![View metadata for storage bucket](/downloads/dspm/analytics/graphs/viewing-public-exposure-path/ds-metadata_storage_bucket.png)
[]
![Verify exposed files](/downloads/dspm/analytics/graphs/viewing-public-exposure-path/ds-exposed_files_0.png)