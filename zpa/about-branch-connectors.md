# About Branch Connectors
Source: https://help.zscaler.com/zpa/about-branch-connectors
PDF: https://help.zscaler.com/pdf/com/en/1485656.pdf

Branch Connectors are virtual machine (VM) images that simplify traffic forwarding to Zscaler services (i.e., Zscaler Internet Access and Zscaler Private Access) without using shared server software. To learn more, see [What Is Zscaler Branch Connector?](/cloud-branch-connector/what-zscaler-branch-connector)
Branch Connectors provide the following benefits and enable you to:
- Supply branches and data centers with fast and reliable access to the internet and private applications with a direct-to-cloud architecture.
- Simplify branch communications by eliminating complex routing, virtual private networks (VPNs), and firewalls while allowing for flexible forwarding and simple policy management.
Configuring Branch Connectors involves the following tasks:
- Configure a Branch Provisioning Template. To learn more, see [Configuring a Branch Provisioning Template](/cloud-branch-connector/brnch/configuring-branch-provisioning-template).
- Download the Branch Connector VM image from the Zscaler Cloud & Branch Connector Admin Portal. To learn more, see [Downloading Branch Connector Images](/cloud-branch-connector/brnch/downloading-branch-connector-images).
- Deploy the Branch Connector. To learn more, see [Branch Connector Deployment Management](/cloud-branch-connector/deployment-management).
Zscaler recommends you consider the following when configuring Branch Connectors:
- All existing Branch Connectors appear as Cloud Connectors in the ZPA Admin Portal after April 10, 2023. You must configure a new Branch Connector in the [Zscaler Cloud & Branch Connector Admin Portal](/cloud-branch-connector/accessing-navigating-zscaler-cloud-branch-connector-admin-portal) for it to be visible in the Branch Connector and Branch Connector Groups pages of the ZPA Admin Portal.
- Provisioning templates created before April 10, 2023, are no longer valid and must not be used. New [provisioning templates](/cloud-branch-connector/about-branch-provisioning-template) must be used to properly provision a Branch Connector.
About the Branch Connectors Page
On the Branch Connectors page (Configuration & Control > Private Infrastructure > Branch Connector Management > Branch Connectors), you can do the following:
- View a list of applied filters available from the current and previous user sessions. Applied filters must be saved to the user session first before they can be viewed. Use the drop-down menu to select the applied filters to view. To learn more, see [Using Tables](/zpa/using-tables#filterData).
- Hide the filters on the page by clicking **Hide Filters**. Click **Show Filters** to display the filters.
- Refresh the Branch Connectors page to reflect the most current information.
- Filter the Branch Connector information that appears in the table. By default, no filters are applied. You can also save applied filters to your preferences so that they're visible in future user sessions. To learn more, see [Using Tables](/zpa/using-tables#filterData).
- Expand all the rows in the table to see more information about each Branch Connector.
- View a list of all deployed Branch Connectors. For each deployed Branch Connector, you can see:
- **Name**: The name of the Branch Connector.
- **Branch Connector Group**: The name of the group that the Branch Connector is part of.
- [Modify the columns displayed in the table.](/zpa/using-tables)
- Display more rows or a different page of the table.
- Open the [Zscaler Help Browser](/zpa/using-zscaler-help-browser) and view Help Portal articles without leaving the ZPA Admin Portal.
- Go to the [Branch Connector Groups](/zpa/about-branch-connector-groups) page to review your Branch Connector groups.
![Viewing the Branch Connector page](/downloads/zpa/branch-connector-management/about-branch-connectors/zpa-branch-connectors.png)