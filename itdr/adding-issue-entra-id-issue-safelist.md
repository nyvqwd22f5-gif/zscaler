# Adding an Issue to the Entra ID Issue Safelist
Source: https://help.zscaler.com/itdr/adding-issue-entra-id-issue-safelist
PDF: https://help.zscaler.com/pdf/com/en/1531764.pdf

If an issue of a scanned Entra ID tenant on the [Detailed Findings and Recommendations](/itdr/viewing-entra-id-focus-area-details) page in the [Entra ID dashboard](/itdr/viewing-entra-id-focus-area-details) doesn't pose any risk, you can mark it as safe by adding it to the [Entra ID Issue Safelist](/itdr/about-entra-id-issue-safelist).
After you add an issue to the safelist, it disappears from the [Detailed Findings and Recommendations](/itdr/viewing-entra-id-focus-area-details) page and [vulnerability report](/itdr/viewing-entra-id-vulnerability-report) for the selected Entra ID tenant only. This issue is not marked safe if you select a different scanned Entra ID tenant.
To add an issue to the Entra ID Issue Safelist:
- Go to **ITDR** > **Dashboard **> **Entra ID**.
-
On the **Entra ID Dashboard** page:
- Select a tenant from the **Result for** drop-down menu.
- Select a timestamp from the **scanned on** drop-down menu.
[See image.](#zscaler-itdr-safelist-timestamp)
The scan result for the selected tenant appears.
-
Under **Detailed Findings and Recommendations**, click an issue.
[See image.](#itdr-focus-area-issue)
-
On the** Detailed Findings and Recommendations** page, click **Add Issue to Safelist** for the selected issue.
[See image.](#zscaler-itdr-issue-add-safelist)
-
In the **Add to Safelist** window, enter a reason for marking the issue safe and set an expiration date if needed.
[See image.](#zscaler-itdr-issue-safelist-reason)
-
Click **Save**.
The issue is added to the safelist. You can view and manage it from the [Entra ID Issue Safelist](/itdr/about-entra-id-issue-safelist).
[]![Option to select Entra ID Domain and Timestamp](/downloads/itdr/safelists/active-directory-safelists/active-directory-issue-safelist/adding-issue-active-directory-issue-safelist/itdr-entraid-tenant-selection.png)
[]![Issue in Focus Area of Entra ID Dashboard](/downloads/itdr/safelists/active-directory-safelists/active-directory-issue-safelist/adding-issue-active-directory-issue-safelist/itdr-entra-id-select-an-issue.png)
[]![Add to Safelist Option](/downloads/itdr/safelists/active-directory-safelists/active-directory-issue-safelist/adding-issue-active-directory-issue-safelist/itdr-add-issue-to-safelist-button.png)
[]![Add to Safelist Window](/downloads/itdr/safelists/active-directory-safelists/active-directory-issue-safelist/adding-issue-active-directory-issue-safelist/itdr-add-to-safelist-window.png)