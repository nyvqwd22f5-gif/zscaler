# Viewing the Resource Inventory Graph
Source: https://help.zscaler.com/dspm/viewing-resource-inventory-graph
PDF: https://help.zscaler.com/pdf/com/en/1478111.pdf

After DSPM completes the [data scan](/dspm/about-scan-settings) of the resources, the scan results are displayed in the form of graphs that are visually appealing and highly interactive. The graphs consist of interactive nodes that provide contextual information (e.g., cloud account name, primary resource type, ID, file path, number of files containing sensitive data, access levels, etc.) about the primary resource and the associated secondary resources.
The graphs also include attack paths that show how the resource is compromised either through public exposure, malware, by an IAM entity (user, service, role) with access privileges, vulnerabilities, etc. This information helps you analyze the issues in detail and remediate them immediately.
The following nodes and attack paths are depicted in the Resource Inventory graph:
- [List of Nodes](#ds-nodelist)
- [Attack Paths](#ds-attackpaths)
[See image.](#interactive-workflow)
To view the Resource Inventory graph for a resource:
- Go to **Analytics **> **Resource Inventory**.
- On the **Resource Inventory** page, you can see the scanned results for AWS, Azure, and GCP resources.
- Click any **Resource Name** to view the drawer.
-
On the **Risk Explorer** tab, you can see the graph for the selected resource:
- [AWS](/dspm/viewing-graph-aws-data-stores)
- [Azure](/dspm/viewing-graph-azure-data-stores)
- [GCP](/dspm/viewing-graph-gcp-data-stores)
The nodes and access paths vary depending on the [primary resource](/dspm/supported-data-stores) and its associated resources.
[]The following table explains each node and the entity it represents on the graph.
[](/dspm/about-unmanaged-database)
| Node | Description |
| ---- | ----------- |
| Account | The cloud account that contains the resource with sensitive data. |
| Applications | The applications that can access the resource. |
| Auto Scaling Group | A logical group that contains a collection of EC2 instances for automatic scaling and management. |
| AWS Elastic Network Interface (ENI) | A networking component (virtual card interface) attached to an EC2 instance for enabling network connectivity. |
| External | The external entities that can access the resource. |
| Federated | The federated entities that can access the resource. |
| Group | A logical container that consists of several users who are assigned the same role. |
| Instance Profile | A container for an IAM role that is used to pass the role information to an EC2 instance when the instance starts. |
| Internet Gateway | A virtual private cloud (VPC) component that enables resources in your public subnets (e.g., EC2 instances) to connect to the internet. |
| Load Balancer | Distributes incoming application traffic across multiple targets, such as EC2 instances, in multiple availability zones. |
| Managed Identity | The managed entities that can access the resource. |
| Network Access Control List (ACL) | The ACL defines which accounts and groups are granted access to S3 buckets along with the type of access. |
| Organization | The onboarded AWS organization comprising all the resources that are scanned by DSPM. |
| Organization Unit | A logical unit comprising a list of cloud accounts in a tenant. |
| Policy | A security control in the DSPM Admin Portal that detects misconfigurations or vulnerabilities in the cloud resources and triggers an alert. |
| Public Internet | This node is shown when DSPM detects that a resource containing sensitive data is publicly exposed and is accessed by unauthorized users. |
| Roles | The roles assigned to users and groups to perform various actions in the DSPM Admin Portal. |
| Route Table | A set of rules called routes that determine the destination of the network traffic from your subnet or gateway. |
| Security Group | Controls the inbound and outbound traffic for the cloud resource. |
| Services | The services (e.g., Azure App Services) that have access to the resource. |
| Service Accounts | The service accounts that have access to the resource. |
| Subnet | A range of IP addresses used to launch the resources in your VPC. You can connect a subnet to the internet, other VPCs, etc., and route traffic to and from your subnets using route tables. |
| Unmanaged Database | Databases that are deployed on virtual machines in the cloud. DSPM scans these databases for sensitive data. |
| User | The IAM users who can access the resource. |
| Web Application Firewall (WAF) | Allows to monitor the HTTP(S) requests and control access to your data. |
[]
![Shows the scan results in the form of graphs.](/downloads/tech-pubs-drafts/dspm-draft-articles/1-12-0-viewing-data-inventory-graph/ds-datainventory%20-%20graph.gif)
- []**Public Exposure Path**: Represents the misconfigurations in the primary and associated resources that could allow adversaries to gain initial access or perform lateral movement.
- **Access Path**: Represents the mapping of identity and access management (IAM) roles, users, external entities, federated identities, and services that have permissions to access the resource.
- **Known Vulnerabilities Path**: Represents the common vulnerabilities and exposures (CVEs) found in the resource.
- **Sensitive Data Path**: Represents the files that contain [sensitive data](/dspm/viewing-sensitive-data-details).
- **Associated Resources Path**: Represents all the resources associated with the primary resource (e.g., all the EBS volumes in an EC2 instance). You can also see the details of resources that don't contain any sensitive data and the resources that are not scanned by DSPM.
- **Malware Path**: Represents the malware found in the resource.