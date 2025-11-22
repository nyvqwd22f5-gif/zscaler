# Viewing Identities with Exposed Endpoint Credentials
Source: https://help.zscaler.com/itdr/viewing-identities-endpoint-exposures
PDF: https://help.zscaler.com/pdf/com/en/1531747.pdf

You can view the details of all the identities storing exposed credentials in a table format. You can double-click an [identity](/itdr/viewing-affected-active-directory-user-account-details) to view the issue and threat details. You can further investigate the issues and swiftly remediate the compromised identities to disrupt the attacker's operations.
To view the identity details with critical exposed credentials:
- Go to **ITDR **> **Dashboard** > **Endpoint Credential Exposure**.
- Click **Top Identities **on the **Dashboard **tab, or select the **Identities** tab.
- Select a date from the **As of Date** calendar to view the total number of identities storing exposed credential issues on that scan date.
[See image.](#itdr-exp-cred-identities-date)
-
The identities with exposed credentials are listed with the following information:
- **Identity**: The name of the system.
- **Type of risk**: The exposure risk type. Click the number to view all the exposure types.
[See image.](#itdr-exp-cred-identities-details)
Click the **Actions** menu to [copy specific columns in the table](/itdr/using-tables#itdr-copy-columns-table-section) and download the [exposed credentials as a CSV or JSON file](/itdr/using-tables#itdr-export-table-csv-section).
[]![Select a scan date](/downloads/itdr/dashboard/endpoint-credential-exposure/viewing-identities-endpoint-exposures/itdr-exp-cred-identities-date-2.png)
[]![View identities storing exposed credentials](/downloads/itdr/dashboard/endpoint-credential-exposure/viewing-identities-endpoint-exposures/itdr-exp-cred-identities-details-3.png)