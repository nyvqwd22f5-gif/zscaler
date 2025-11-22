# About Exact Data Match
Source: https://help.zscaler.com/unified/about-exact-data-match
PDF: https://help.zscaler.com/pdf/com/en/1492956.pdf

Using [Exact Data Match (EDM) index templates](/unified/creating-exact-data-match-template) allows the Zscaler service to identify a record from a structured data source that matches predefined criteria. For example, your organization might want to protect personally identifiable information (PII) from being lost or might want to give your employees the ability to share their own PII data using a personal email or file sharing account. In either case, identifying and correlating multiple tokens that contribute to a particular record, to identify ownership of that data, is crucial. To learn more, see [Understanding Exact Data Match Index Templates](/unified/understanding-exact-data-match-index-templates).
EDM provides the following benefits and enables you to:
- Identify and correlate multiple tokens that contribute to a particular record to identify ownership of data.
- Protect personally identifiable information (PII) from being lost.
- Give your employees the ability to share their own PII data using a personal email or file sharing account.
In the [Index Tool](/unified/about-index-tool), creating an EDM template allows you to define these tokens (i.e., criteria) for your data records by importing a CSV file. After the data is defined and submitted, you can then apply the template to a custom DLP dictionary or engine, which uses the criteria to match against your records. The Zscaler service then evaluates the EDM-defined DLP rule with the appropriate action for your outbound traffic.
[See image.](#EDM-Workflow-Diagram)
You can create up to 64 templates for your organization. The cell usage information displayed within the Admin Portal and the Index Tool can help you determine the size of your data records per template. For example, if you submit a CSV file to create an EDM template that has 40K records and each record includes 3 columns, then it uses 120K cells. Also, the number of records used within a template has an impact on how you determine the amount of memory (RAM) you need to allocate for your [Index Tool VM](/unified/configuring-index-tool-vmware).
To learn more, see [About the Index Tool](/unified/about-index-tool) and [Creating an Exact Data Match Template](/unified/creating-exact-data-match-template).
About the Exact Data Match Page
On the Exact Data Match page (Policies > Data Protection > Common Resources > Index Templates), you can do the following:
- Search for an EDM index template.
- View a list of all EDM templates that are configured for your organization. For the templates, you can see the following:
- **Template Name**: The name of the template, as specified in the [Index Tool](/unified/creating-exact-data-match-template). You can sort this column.
- **VM Name**: The virtual machine (VM) ID, as specified in the [Index Tool Configuration](/unified/adding-index-tool-configuration). You can sort this column.
- **Number of Cells**: The total number of cells currently in use by the template.
- **Last Modified**: The date and time the template was last modified.
- **Modified By**: The last admin user to modify the template.
- [Modify the table and its columns](/unified/using-tables).
- View EDM index template details, or [delete a template](/unified/creating-exact-data-match-template#DeleteTemplate-AdminPortal). You can also view template details within the [Index Tool](/unified/creating-exact-data-match-template).
- Go to the [Indexed Document Match (IDM)](/unified/about-indexed-document-match) page, where you can view a list of all IDM templates configured for your organization.
![Viewing and managing Exact Data Match index templates within the ZIA Admin Portal](/downloads/zia/policies/data-loss-prevention/dlp-exact-data-match/about-exact-data-match/ZIA-About-Exact-Data-Match.png)
[]![Workflow Diagram for Exact Data Match Index Template Creation](/downloads/zia/policies/data-loss-prevention/dlp-exact-data-match/about-exact-data-match/ZIA-Index-Template-Workflow.png)