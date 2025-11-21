# Disabling the Sensitivity Setting for DLP Engines
Source: https://help.zscaler.com/dspm/disabling-sensitivity-setting-dlp-engines
PDF: https://help.zscaler.com/pdf/com/en/1479346.pdf

Data sensitivity determines how susceptible the data is along with the level of risk associated with it, which could lead to data breaches. For example, the sensitivity level is high for personally identifiable information (PII) or credit card numbers, moderate for email addresses, and low for data that does not have any sensitive or confidential information.
DSPM scans the data using the predefined DLP engines and dictionaries to detect and classify sensitive data and generates [alerts](/dspm/about-alerts). By default, the sensitivity setting is enabled for all DLP engines. You can disable the sensitivity setting when you don't want the DLP engines to classify the data as sensitive.
If you disable the sensitivity setting for all DLP engines, any new DLP engine that is added to Zscaler Internet Access (ZIA) is not automatically synced with DSPM. You need to manually enable the sensitiviy settings for such DLP engines in the DSPM Admin Portal.
To disable the sensitivity setting:
- Go to **Policy** > **Data Sensitivity Settings**.
-
Disable the sensitivity setting for all DLP engines.
[See image.](#ds-allengines)
- Read the confirmation message that appears, then click **Disable**.
- [See image.](#ds-msgforallengines)
-
Disable the data sensitivity setting for a specific DLP engine.
[See image.](#ds-oneengine)
-
Read the confirmation message that appears, then click **Disable**.
[See image.](#ds-disablemsgforone)
[]![Disable the sensitivity setting for all DLP engines](/downloads/dspm/policies/data-sensitivity-settings/disabling-sensitivity-setting-dlp-engines/ds-sensitivity-disableall.png)
[]![Confirmation message to disable sensitivity for all engines](/downloads/dspm/scan-settings/managing-scan-settings/enabling-or-disabling-data-sensitivity-criteria/ds-dsensitivity-disableallmsg.png)
[]![Disable the sensitivity setting for a specific DLP engine](/downloads/dspm/policies/data-sensitivity-settings/disabling-sensitivity-setting-dlp-engines/ds-sensitivity-disableone.png)
[]![Confirmation message to disable engine sensitivity](/downloads/dspm/scan-settings/managing-scan-settings/disabling-dlp-engine-sensitivity/ds-dsensitivity-disableonemsg.png)