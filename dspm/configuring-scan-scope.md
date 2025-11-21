# Configuring Scan Scope
Source: https://help.zscaler.com/dspm/configuring-scan-scope
PDF: https://help.zscaler.com/pdf/com/en/1509661.pdf

Scan scope allows you to run DLP engines on file types that are relevant for these engines. You can apply the scan scope while configuring the scan settings. DSPM uses only the specified DLP engines to scan the resources for sensitive data.
[]Creating Scan Scope
To create a new scan scope:
-
On the **Scan Scope** page, click the **Create Scan Scope** button.
[See image.](#img_create_scope)
-
On the **General Information** page:
- **Engine Scope Name**: Enter a concise and descriptive name for your scan scope.
- **Engine Scope Description**: Enter a clear and detailed explanation of what your scan scope covers, allowing for a clear understanding of the scope of work.
[See image.](#img_scope_general)
- Click **Next**.
-
On the **Select Criteria** page:
- **DLP Engine**: Choose DLP engines for the scan scope. Choose all for a comprehensive scan or specific DLP engines to focus on specific DLP engines.
- **Specific DLP Engines**: Choose the DLP engines you want to include in your scope. This option is enabled only if you select specific DLP engines to scan.
- **File Type**: Choose the file types you want to include in your scan scope.
-
**Machine Learning Document Scan**: Enable if you want to use machine learning-powered document scanning.
File type filters and machine learning document scans are optimized for cloud storage and virtual machine resources.
[See image.](#img_scope_criteria)
- Click **Next**.
-
On the Summary page, review the configured details. If any changes are required, click the **Edit** icon to make the necessary modifications. To learn more, see [Editing or Deleting Scan Scopes](/dspm/editing-or-deleting-scan-scopes).
[See image.](#img_scope_summary)
- Click **Finish** to create the new scan scope.
[]![Create Scan Scope](/downloads/dspm/scan-settings/configuring-scan-scope/create_scope.png)
[]![Scan Scope General Information](/downloads/dspm/scan-settings/configuring-scan-scope/scope_general.png)
[]![Scan Scope Criteria](/downloads/dspm/scan-settings/configuring-scan-scope/scope_criteria.png)
[]![Scan Scope Summary](/downloads/dspm/scan-settings/configuring-scan-scope/scope_summary.png)