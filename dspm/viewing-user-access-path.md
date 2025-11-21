# Viewing the User Access Path
Source: https://help.zscaler.com/dspm/viewing-user-access-path
PDF: https://help.zscaler.com/pdf/com/en/1482986.pdf

The user access path includes details of identity and access management (IAM) entities that can access the primary resource containing sensitive data. The nodes in the graph are interactive. You can click each node to view granular details of each entity.
[See image.](#ds-animatedimage)
To view the access path for an IAM entity:
- Go to **Analytics **> **Resource Inventory**.
- Click any **Resource Name** to view the Resource Inventory graph.
You can view the user access path for the following cloud environments:
- [AWS](#aws)
- [Azure](#azure)
- [GCP](#gcp)
[]
The Resource Inventory graph displays the sensitive records found in the primary resource along with external, federated, roles, services, and users that have access to this primary resource.
[See image.](#ds-graph)
Click the IAM nodes to see:
- **ARN**: The Amazon Resource Name (ARN) assigned to the user. ARN is a string that uniquely identifies an Amazon resource.
- **Entity Type**: The type of IAM entity.
- **Account ID**: The account ID of the entity.
- **Access Level**: The permissions assigned to the entity.
- **Last Activity**: The date and time the IAM entity last accessed the primary resource.
[See image.](#ds-usersarn)
Click **ARN** to view the additional details.
[See image.](#ds-arn)
Click **Show Access Path** to view another graph.
[See image.](#ds-arndetails)
Another graph displays the roles and permissions assigned to the entity, allowing it to access the primary resource.
[See image.](#ds-useraccess)
[]![View the user entity details](/downloads/dspm/analytics/graphs/viewing-user-access-path/ds-user-details.png)
[]![Click the ARN to view additional details](/downloads/dspm/analytics/graphs/viewing-user-access-path/ds-access-arn.png)
[]![Shows the ARN details.](/downloads/tech-pubs-drafts/dspm-draft-articles/viewing-user-access-path-draft/AWS%20Show%20Access%20Path%20Image.png)
[]![Shows the user access path](/downloads/dspm/analytics/graphs/viewing-user-access-path/ds-accesspathgraph.png)
[]![View the Resource Inventory graph](/downloads/dspm/analytics/graphs/viewing-user-access-path/ds-rsikexplorere.png)
[]![Shows the user access path.](/downloads/dspm/analytics/graphs/viewing-user-access-path/ds-riskexplorer-gif.gif)
[]
The Resource Inventory graph displays the sensitive records found in the primary resource along with users, external, applications, managed identity, and services that have access to this primary resource.
[See image.](#azure_graph)
Click the IAM nodes to see:
- **Entity Name**: The name of the Azure entity.
- **Entity Type**: The type of IAM entity.
- **Access Level**: The permissions assigned to the entity.
- **Last Activity**: The date and time the IAM entity last accessed the primary resource.
[See image.](#azure_external_entity_name)
Click **Entity Name **to view the additional details.
[See image.](#Azure_entity_name_details)
Click **Show Access Path** to view another graph.
[See image.](#Azure_show_access_path)
Another graph displays the roles and permissions assigned to the entity, allowing it to access the primary resource.
[See image.](#azure_user_access_path)
[]
![Viewing the Resource Inventory graph](/downloads/tech-pubs-drafts/dspm-draft-articles/viewing-user-access-path-draft/User%20Access%20Path%20Main%20Image%20New.png)
[]
![Shows the entity names.](/downloads/tech-pubs-drafts/dspm-draft-articles/viewing-user-access-path-draft/Azure%20External%20Entity%20Name%20Image_0.png)
[]
![Clicking entity name to view additional details](/downloads/tech-pubs-drafts/dspm-draft-articles/viewing-user-access-path-draft/Azure%20Entity%20Name%20Image_1.png)
[]
![Shows the entity details.](/downloads/tech-pubs-drafts/dspm-draft-articles/viewing-user-access-path-draft/Azure%20Show%20Access%20Path%20Image_0.png)
[]
![Shows the user access path.](/downloads/tech-pubs-drafts/dspm-draft-articles/viewing-user-access-path-draft/Azure%20user%20access%20path%20image.png)
[]
The Resource Inventory graph displays the sensitive records found in the primary resource along with users, external, service accounts, domains, and services that have access to this primary resource.
[See image.](#gcp_image_with_all_IAM_nodes)
Click the IAM nodes to see:
- **Entity Name**: The name of the Azure entity.
- **Entity Type**: The type of IAM entity.
- **Access Level**: The permissions assigned to the entity.
- **Last Activity**: The date and time the IAM entity last accessed the primary resource.
[See image.](#gcp_user_entity_details)
Click **Entity Name **to view the additional details.
[See image.](#gcp_entity_name_details)
Click **Show Access Path** to view another graph.
[See image.](#gcp_entity_details)
Another graph displays the roles and permissions assigned to the entity, allowing it to access the primary resource.
[See image.](#gcp_user_access_path)
[]
![View Resource Inventory graph](/downloads/dspm/analytics/graphs/viewing-user-access-path/ds-gcp-riskexplorer.png)
[]
![View the user entity details](/downloads/tech-pubs-drafts/dspm-draft-articles/viewing-user-access-path-draft/Viewing%20IAM%20node%20columns.png)
[]
![Entity name details](/downloads/tech-pubs-drafts/dspm-draft-articles/viewing-user-access-path-draft/Viewing%20Entity%20Name.png)
[]
![Viewing entity details](/downloads/tech-pubs-drafts/dspm-draft-articles/viewing-user-access-path-draft/Click%20Show%20Access%20Path_0.png)
[]
![View user access path ](/downloads/tech-pubs-drafts/dspm-draft-articles/viewing-user-access-path-draft/Viewing%20User%20Access%20Path.png)