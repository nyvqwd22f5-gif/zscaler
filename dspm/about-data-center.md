# About On-Premises Data Centers
Source: https://help.zscaler.com/dspm/about-data-center
PDF: https://help.zscaler.com/pdf/com/en/1526556.pdf

An on-premises data center refers to a facility that hosts various IT infrastructure components, including databases, servers, and networking applications, which are managed independently by the organization rather than a cloud service provider. These data centers are typically located within the premises of the organization. On-premises data centers provide organizations with complete control over their data, security, and infrastructure, making them an essential component of many hybrid and on-premises IT environments.
DSPM scans the databases in these on-premises data centers, providing visibility into the sensitive data that is stored in the databases. This allows you to manage and secure the data and maintain a strong security posture.
Onboarding on-premises data centers to DSPM provides the following benefits and enables you to:
- Gain comprehensive visibility into data stored across all on-premises databases and systems.
- Improve your security posture of the databases.
- Have a unified view of data assets across hybrid environments (cloud and on-premise).
- Centralize risk assessment and management of on-premises databases.
Organizations can maintain consistent security policies and data protection measures across the hybrid infrastructure by integrating on-premises data centers with DSPM.
About the On-Premises Data Centers Page
On the On-Premises Data Centers page (Administration > Configuration > On-Premises Data Centers), you can do the following:
- Apply [filters](/dspm/using-filters) to view specific data.
- [Add an on-premises data center to DSPM](/dspm/add-data-center).
- View the list of on-premises data centers. For each on-premises data center, you can view:
- **Account**: The name of the data center. Click to view the data center details.
- [Data Center Details](#dc-details)
- **Location**: The regions where the data centers are located.
- **Business Unit**: The business unit assigned to the data center.
- **Added By**: The user who added the data center.
- **Added On**: The date and time the data center was added.
- Sort the column data.
- [Modify the table and its columns](/dspm/using-tables).
- Click the **Action** icon to [edit](/dspm/editing-or-deleting-unmanaged-database) or [delete](/dspm/editing-or-deleting-unmanaged-database) the data centers.
[]For each data center, you can:
- [Edit the data center configuration](/dspm/editing-or-deleting-unmanaged-database).
- [Delete the data center configuration](/dspm/editing-or-deleting-unmanaged-database).
- **Data Center**: View the following information for the data center:
- **Location**: The regions where the data centers are located.
- **Business Unit**: The business unit assigned to the data center.
- **Added on**: The date and time the data center was added.
- **Added by**: The user who added the data center.
- **Cloud Network Association**: View the following information for the cloud network association:
- **Association Name**: The name of the cloud network association.
- **Connected Cloud**: The cloud service provider where the data center is associated (Azure, AWS, or GCP).
- **DSPM Alias**: The DSPM alias for the selected cloud.
- **Connected Cloud Region**: The region where the cloud is hosted.
![The On-Premises Data Centers page with a list of data centers and annotations on different parts of the page.](/downloads/dspm/administration/on-premise-data-center/about-data-center/ds-admin-on-prem-about.png)