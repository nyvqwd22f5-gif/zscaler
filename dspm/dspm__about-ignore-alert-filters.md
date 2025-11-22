# About Ignore Alert Filters
Source: https://help.zscaler.com/dspm/about-ignore-alert-filters
PDF: https://help.zscaler.com/pdf/com/en/1477816.pdf

The ignore alert filter allows you to exclude the generation of alerts for less critical violations. By adding an ignore alert filter, you can avoid receiving notifications or taking actions on such policy violations. When you add an ignore alert filter, DSPM stops generating alerts for the selected filter scope, and notifications aren't sent to any [third-party integrations](/dspm/about-third-party-integrations). This allows you to focus on critical alerts and prioritize them. For example, you can add an ignore alert filter to exclude alerts that are generated for [policies ](/dspm/about-data-posture-policies)with low severity or for a specific [cloud account](/dspm/about-cloud-accounts).
The ignore alert filter provides the following benefits and enables you to:
- Ignore alerts that you do not want to be notified for or take action on.
- Reduce the number of alerts in the DSPM Admin Portal.
- Focus on critical alerts.
About the Ignore Alert Filter Page
On the Ignore Alert Filter page (Alerts > Alert Settings > Ignore Alert Filter), you can do the following:
- [Add an ignore alert filter.](/dspm/adding-ignore-filters)
- View the list of ignore alert filters. For each filter, you can see:
-
**Alert Filter Name**: The name of the ignore alert filter. Click to view additional details. You can also edit, delete, enable, or disable the filter.
[See image.](#details)
-
**Filter Scope**: The scope ([business unit](/dspm/about-business-units), [policy](/dspm/about-data-posture-policies), tags, etc.) selected for the ignore alert filter.
- If the selected scope is deleted (e.g., policies are deleted, accounts are offboarded, or the business unit is deleted), the ignore alert filter is disabled, and an exclamation mark is displayed indicating the alert filter is invalid. [See image.](#disabled-filter) Click the alert filter name to see the reason why the ignore alert filter is disabled. [See image.](#filter-drawer)
- You can enable the filter only after at least one filter scope is available.
- If multiple policies, accounts, or resource types are selected for the filter scope and only one of them is deleted, the ignore alert filter is not impacted.
- **Created By**: The user who created the filter.
- **Created Date**: The date and time the filter was created.
- **Updated By**: The user who updated the filter.
- **Last Updated**: The date and time the filter was updated.
- Search for a specific ignore alert filter.
- Sort the column data.
- [Modify the table and its columns.](/dspm/using-tables)
-
[Enable or disable the ignore alert filter.](/dspm/enabling-or-disabling-ignore-filters)
By default, the ignore alert filter is enabled.
- [Edit or delete the ignore alert filter.](/dspm/editing-or-deleting-ignore-filters)
![View the ignore alert filters](/downloads/dspm/alerts/ignore-alert-filters/about-ignore-alert-filters/dspm-ignore-alert-filter-page.png)
[]![View additional details of the ignore alert filter](/downloads/dspm/alerts/ignore-alert-filters/about-ignore-alert-filters/dspm-ignore-filter-drawer.png)
[]![View the disabled ignore alert filter](/downloads/dspm/alerts/ignore-alert-filters/about-ignore-alert-filters/dspm-invalid-filter.png)
[]![View the ignore alert filter drawer](/downloads/dspm/alerts/ignore-alert-filters/about-ignore-alert-filters/dspm-invalid-ignorealert-drawer.png)