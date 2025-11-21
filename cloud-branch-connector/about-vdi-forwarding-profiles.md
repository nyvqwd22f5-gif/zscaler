# About VDI Forwarding Profiles
Source: https://help.zscaler.com/cloud-branch-connector/about-vdi-forwarding-profiles
PDF: https://help.zscaler.com/pdf/com/en/1471721.pdf

In the Zscaler Cloud & Branch Connector Admin Portal, the VDI Forwarding Profile page displays the current forwarding profiles and allows you to create new forwarding profiles. Additionally, Zscaler Client Connector for VDI automatically fetches VDI forwarding profile policies every 60 minutes.
Virtual Desktop Infrastructure (VDI) forwarding profiles provide the following benefits and enable you to:
- Create rules to include or exclude destinations from being encapsulated in the tunnels that Zscaler Client Connector for VDI creates.
- Apply similar forwarding rules to multiple VDI groups in multiregion deployments.
About the VDI Forwarding Profile Page
On the VDI Forwarding Profile page (Administration > VDI Forwarding Profiles), you can do the following:
- [Add a VDI forwarding profile](/cloud-branch-connector/configuring-vdi-forwarding-profiles).
- View a list of all VDI forwarding profiles. For each VDI forwarding profile, you can view:
- **Template Name**: The name of the template.
- **Include IP Addresses**: The included IP addresses.
- **Exclude IP Addresses**: The excluded IP addresses.
- **Description**: The description of the template.
- [Edit](/cloud-branch-connector/editing-deleting-or-duplicating-items) a VDI forwarding profile.
- [Delete](/cloud-branch-connector/editing-deleting-or-duplicating-items) a VDI forwarding profile.
- Modify the table and its columns.
- Search for a VDI forwarding profile.
-
Filter the list of VDI forwarding profiles by the following criteria:
- **Include IP Addresses**: Select one or more included IP addresses to view in a filtered list.
- **Exclude IP Addresses**: Select one or more excluded IP addresses to view in a filtered list.
Include DNS server IP addresses in the Zscaler Client Connector for VDI forwarding profile because DNS requests must traverse the Cloud Connector or Branch Connector when leveraging Zscaler Private Access (ZPA). Similarly, configure ZPA synthetic IP addresses, which are located on the [IP Pool](/cloud-branch-connector/about-ip-pool) page, in the inclusion list.
![About the VDI Forwarding Profile page in the Zscaler Cloud & Branch Connector Admin Portal.](/downloads/tech-pubs-drafts/cloud-connector-draft-articles/about-vdi-forwarding-profiles-draft-doc-50724/ZCCVDIForwardingProfile.png)