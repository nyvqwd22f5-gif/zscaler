# Filtering & Customizing the Lookalike Domains Page
Source: https://help.zscaler.com/easm/filtering-customizing-lookalike-domains-page
PDF: https://help.zscaler.com/pdf/com/en/1508161.pdf

The [Lookalike Domains](/easm/about-lookalike-domains) page includes a set of filtering options that allows you to view a subset of data that matches specified criteria. You can set the criteria based on specific parameters of lookalike domains such as status, exposure score, risk category, and deception method. These parameters can be applied individually or together to the Lookalike Domains table to filter the data. You can customize the table columns by choosing to show or hide specific columns in the table and by reordering and sorting the columns.
The following sections describe how to apply filters on lookalike domains and how to customize the Lookalike Domains table columns.
The data on the Lookalike Domains page corresponds to your organization selected on the top-right corner.
Applying Filters
On the Lookalike Domains page (Insights > Lookalike Domains), you can select one or more filters along with appropriate values and apply the filters.
The following filters are available:
- **Status**: Filters the lookalike domains based on their [status](/easm/modifying-lookalike-domain-status). This filter allows you to select multiple values simultaneously by using the respective checkboxes. The following statuses are available for lookalike domains: Not Verified, Verified, and Risk Accepted, Resolved, and Disputed.
- **Exposure Score**: Filters the lookalike domains based on their exposure score and categorization into Low, Medium, High, and Critical, depending on the values chosen. This filter allows you to select multiple values simultaneously by using the respective checkboxes.
-
**Risk Category**: Filters the lookalike domains based on the risk category assigned. This filter allows you to select multiple values simultaneously by using the respective checkboxes.
[Available Risk Categories](#risk-categories)
- **Deception Method**: Filters the lookalike domains based on the deception tactic used in the domain name. Examples of deception techniques include the use of homograph (i.e., by exploiting similar-looking characters or homoglyphs), substituting letters with numbers, hyphenation, intentional typos, adding, removing, or transposing letters, etc. This filter allows you to select multiple values simultaneously by using the respective checkboxes.
[See image.](#lookalike-domain-filters)
Customizing Table Columns
You can customize the columns that appear within the Lookalike Domains table by using the following options:
- Choose the columns that must be shown within the table by clicking the **Settings** icon on the top-right corner. In the **Column Chooser** window that appears, you can select or deselect the columns by clicking on them to add or remove them from the table respectively. The table refreshes and displays the new column set. The **Lookalike Domain** column is always shown and cannot be modified.
-
Sort the list by a specific column in an alphabetical or numerical order by using the **Sort** icon shown in the column header. The sorting option is available only for specific columns, indicated by the **Sort** icon displayed next to the column name.
To appropriately sort the columns, ensure that only one column is sorted at a time and deselect the **Sort** icon for other columns which use the functionality simultaneously.
- []**Verified Phishing**: Indicates that the domain is verified to be a phishing site by Zscaler's web risk analyzer service.
- **Registered Lookalike**: Indicates that the domain is registered through an internet company that provides domain registration services (i.e., registrar).
- **Preventative Lookalike**: Indicates that the domain is not registered with a registrar.
[]![Applying filters on the lookalike domains list to view a subset of data in EASM Admin Portal](/downloads/easm/insights/lookalike-domains/filtering-customization-lookalike-domains/lookalike-domain-filters.png)