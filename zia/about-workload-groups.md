# About Workload Groups
Source: https://help.zscaler.com/zia/about-workload-groups
PDF: https://help.zscaler.com/pdf/com/en/1461741.pdf

Only admins with full policy access can add or edit the workload groups.
The Workload Group page enables you to create workload groups to apply security policies for your cloud workloads deployed on the public cloud service provider such as the Amazon Web Services (AWS) platform. You can create a workload group by building an expression using various tag types and key-value pairs. You can use a maximum of 8 key-value pairs to build an expression for a workload group. To learn more, see [Understanding Workload Groups](/zia/understanding-workload-groups).
You can use the workload group as a criterion in ZIA policies such as SSL Inspection, Firewall Filtering, URL Filtering, and DLP to apply security policies to the workload traffic.
The Workload Groups page provides the following benefits and enables you to:
- Provide a dynamic approach using the ability to construct expressions for applying policies to your workload.
- Leverage cloud-native metadata available on the public cloud to apply policies to workload traffic.
**Prerequisites**
Ensure that your organization has a subscription to one of the Workload SKUs and an account in Zscaler Cloud & Branch Connector Admin Portal. When subscribed, contact Zscaler Support to enable the Workload Discovery Service Endpoint to access the Workload Groups feature.
**About the Workload Groups Page**
On the Workload Groups (Administration > Workload Groups) page, you can do the following:
- [Add a workload group](/zia/configuring-workload-groups).
- Search for a workload group.
- View a list of all configured workload groups. For each group, you can view the following information:
- **Name**: The name of the workload group.
- **Description**: &amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;lt;!--td {border: 1px solid #cccccc;}br {mso-data-placement:same-cell;}--&amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;gt;
Additional notes or information about the workload group.
- **Last Modified By**: The name of the latest user who modified the workload group.
- **Last Modified On**: The date and time the workload group was last modified.
- [Modify the table and its columns](/zia/how-do-i-use-tables-admin-portal).
- [Edit a workload group](/zia/editing-deleting-duplicating-items).
- Delete a workload group.
![Screenshot of the Workload Groups page in the Administration KB](/downloads/zia/policies/about-workload-groups/zia-about-workload-groups-page.png)