# About Data Sensitivity Settings
Source: https://help.zscaler.com/dspm/about-data-sensitivity-settings
PDF: https://help.zscaler.com/pdf/com/en/1478861.pdf

Sensitive data is confidential information such as personally identifiable information (PII), social security numbers, credit card information, financial data, login credentials, etc., that must be protected with strong security controls to prevent data breaches.
Knowing what type of sensitive data exists in your cloud environment and where it is located (regions) is crucial to keep track and monitor this data regularly and ensure the data is secure. An effective method to keep sensitive data secure is through data classification. By classifying sensitive data, you can have more visibility and prioritize the risks, if any, and quickly remediate the issues.
DSPM supports data classification by using robust [DLP engines and dictionaries](/dspm/about-dlp-engines-and-dictionaries) that are synced from Zscaler Internet Access (ZIA).
You can only view the DLP engines in the DSPM Admin Portal. You can add or modify a DLP engine in the ZIA Admin Portal if you have the [necessary permissions](/dspm/about-roles). When configuring a predefined or custom engine, you can also combine dictionaries with Boolean operators to create logical expressions.
Defining the data sensitivity provides the following benefits and enables you to:
- Classify sensitive data based on the level of sensitivity and risk.
- View the DLP engines and dictionaries that are used by DSPM for data classification.
- Manage the sensitivity setting for DLP engines.
- Add or modify DLP engines by navigating to the ZIA Admin Portal using single sign-on (SSO).
About the Data Sensitivity Settings Page
On the Data Sensitivity Settings page (Policies > Data Sensitivity Settings), you can do the following:
- View the list of DLP engines that are synced from ZIA. For each DLP engine, you can view:
- **DLP Engine Name**: The name of the DLP engine.
- **Engine Type**: The type (Predefined or Custom) of DLP engine.
- **Status**: The status (Active, Inactive, or Deleted) of the DLP engine.
- **Last Synced On**: The date and time the DLP engine was last synced with DSPM.
- **Sensitive**: The sensitivity setting (Enabled or Disabled) for the DLP engine. By default, the sensitivity setting is enabled for all DLP engines.
-
Modify the DLP engine configuration by navigating to the ZIA Admin Portal.
This option is visible only for ZIA users accessing the DSPM Admin Portal via SSO and with a DLP Policy Manager or ZIA Viewer role.
- [Disable the sensitivity setting](/dspm/disabling-sensitivity-setting-dlp-engines) for all DLP engines.
- Search for a specific DLP engine.
- [Modify the columns in the table](/dspm/using-tables).
- Sort the column data.
- [Disable the sensitivity setting](/dspm/disabling-sensitivity-setting-dlp-engines) for a specific DLP engine.
![The data sensitivity settings page](/downloads/dspm/policies/about-data-sensitivity-settings/ds-datasensitivityp.png)