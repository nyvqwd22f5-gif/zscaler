# About Indexed Document Match
Source: https://help.zscaler.com/zia/about-indexed-document-match
PDF: https://help.zscaler.com/pdf/com/en/1402021.pdf

[Watch a video on Indexed Document Matching.](https://fast.wistia.net/embed/iframe/5jnzyl383a)
[Indexed Document Match (IDM) templates](/zia/creating-indexed-document-match-template) allow you to fingerprint your organization’s critical documents that contain sensitive data. By fingerprinting and indexing your documents, you can create a document repository that the Zscaler service can use to identify completely or partially matching documents when evaluating outbound traffic with the Data Loss Prevention (DLP) policy.
Creating an IDM template in the [Index Tool](/zia/about-index-tool) allows you to upload and fingerprint your documents. You can upload text-based files and non-text-based documents (e.g., binary files). Once you create an IDM template, you can then apply the template to a custom DLP dictionary. When adding the template to the dictionary, you must choose the match accuracy level for the template. Match accuracy is the level of accuracy (i.e., the percentage of similarity) that a document must meet to count as a match for an indexed document.
To learn more, see [Creating an Indexed Document Match Template](/zia/creating-indexed-document-match-template) and [Defining Indexed Document Match Accuracy for Custom DLP Dictionaries](/zia/defining-idm-match-accuracy-custom-dlp-dictionaries).
After creating the dictionary, you can add it to a DLP engine and DLP policy rule. When the Zscaler service evaluates your outbound traffic with an IDM-defined DLP rule, it searches for matching documents as a whole, and doesn’t search for keywords and phrases.
For example, your organization uses employee information forms for new employees, which contain personally identifying information. You create an IDM template with a blank employee information form. An employee uploads a completed form, and the Zscaler service catches the form as a partial match for the indexed form.
About the Indexed Document Match Page
On the Indexed Document Match page, you can do the following:
- Search for an index template.
- View a list of IDM templates that are configured for your organization. For the templates, you can see the following:
- **Template Name**: The name of the template, as specified in the [Index Tool](/zia/creating-indexed-document-match-template). You can sort this column.
- **VM Name**: The virtual machine (VM) ID, as specified in the [Index Tool Configuration](/zia/adding-index-tool-configuration). You can sort this column.
- **Number of Documents**: The total number of documents currently indexed by the template.
- **Last Modified**: The date and time the template was last modified. You can sort this column.
- **Modified By**: The last admin user to modify the template. You can sort this column.
- [Modify the table and its columns](/zia/using-tables).
- [Delete an IDM index template](/zia/creating-indexed-document-match-template#delete-IDM-template).
- Go to the [Exact Data Match](/zia/about-exact-data-match) page, where you can view a list of all Exact Data Match (EDM) templates that are configured for your organization.
![Viewing and managing Indexed Document Match index templates within the ZIA Admin Portal](/downloads/zia/policies/data-loss-prevention/dlp-indexed-document-match/about-indexed-document-match/ZIA-About-Indexed-Document-Match.png?1615333803)