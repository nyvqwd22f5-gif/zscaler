# About Branch Connectors
Source: https://help.zscaler.com/unified/about-branch-connectors
PDF: https://help.zscaler.com/pdf/com/en/1496896.pdf

Branch Connectors are virtual machine (VM) images that simplify traffic forwarding to Zscaler services without using shared server software.
Branch Connectors provide the following benefits and enable you to:
- Supply branches and data centers with fast and reliable access to the internet and private applications with a direct-to-cloud architecture.
- Simplify branch communications by eliminating complex routing, virtual private networks (VPNs), and firewalls while allowing for flexible forwarding and simple policy management.
Configuring Branch Connectors involves the following tasks:
- Configure a Branch Provisioning Template.
- Download the Branch Connector VM image from the Admin Portal.
- Deploy the Branch Connector.
Zscaler recommends you consider the following when configuring Branch Connectors:
- All existing Branch Connectors appear as Cloud Connectors in the Admin Portal after April 10, 2023. You must configure a new Branch Connector in the Admin Portal for it to be visible in the Branch Connector and Branch Connector Groups pages of the Admin Portal.
- Provisioning templates created before April 10, 2023, are no longer valid and must not be used. New provisioning templates must be used to properly provision a Branch Connector.
About the Branch Connectors Page
On the Branch Connectors page (Infrastructure > Private Access > Component > Branch Connectors), you can do the following:
- Refresh the Branch Connectors page to reflect the most current information.
- Expand all the rows in the table to see more information about each Branch Connector.
- Filter the Branch Connector information that appears in the table. By default, no filters are applied.
-
View a list of all deployed Branch Connectors. For each deployed Branch Connector, you can see:
- **Name**: The name of the Branch Connector.
- **Branch Connector Group**: The name of the group that the Branch Connector is part of.
![Viewing the Branch Connectors page in the ZPA Admin Portal](/downloads/unified/networking/private-applications/branch-connector-management/about-branch-connectors/about-branch-connectors-page.png)