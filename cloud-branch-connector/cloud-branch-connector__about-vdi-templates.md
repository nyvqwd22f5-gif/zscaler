# About VDI Templates
Source: https://help.zscaler.com/cloud-branch-connector/about-vdi-templates
PDF: https://help.zscaler.com/pdf/com/en/1471706.pdf

In the Zscaler Cloud & Branch Connector Admin Portal, the VDI Template page displays the current templates and allows you to create new templates. Virtual Desktop Infrastructure (VDI) templates provide the VDI provisioning URL and the VDI access token, which are required for installing Zscaler Client Connector for VDI. To learn more, see [Step-by-Step Configuration Guide for Zscaler Client Connector for VDI](/cloud-branch-connector/step-step-configuration-guide-zscaler-client-connector-vdi).
VDI templates provide the following benefits and enable you to:
- Create a set of configurations that are applied to the VDI and dictate the VDI's behavior.
- Create different templates for differing requirements and reuse the templates in multi-region deployments.
About the VDI Templates Page
On the VDI Templates page (Administration > VDI Templates), you can do the following:
- [Add a VDI template](/cloud-branch-connector/configuring-vdi-templates).
- View a list of all VDI templates. For each VDI template, you can view:
- **Template Name**: The name of the template.
- **Auth Type**: Either IdP (identity provider) or Hosted DB.
- **IdP Name**: The IdP name, if **IdP** was selected as the authentication type.
- **System User**: The system user selected for the template.
- **Last Modified By**: The last admin to modify the template.
- **Provisioning URL**: The provisioning URL of the template.
- **Last Modified On**: The date and time the template was last modified.
- **Description**: The description of the template.
- [Edit](/cloud-branch-connector/editing-deleting-or-duplicating-items) a VDI template.
- [Delete](/cloud-branch-connector/editing-deleting-or-duplicating-items) a VDI template.
- Modify the table and its columns.
- Search for a VDI template.
- Filter the list of VDI templates by the following criteria:
- **System User**: Select one or more system users to view in a filtered list.
- **Last Modified By**: Select one or more admins to view in a filtered list.
![The VDI Agent Templates page in the Zscaler Cloud & Branch Connector Admin Portal](/downloads/tech-pubs-drafts/cloud-connector-draft-articles/about-vdi-templates-draft-doc-50724/ZCCVDITemplates.png)