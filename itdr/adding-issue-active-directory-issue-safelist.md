# Adding an Issue to the Active Directory Issue Safelist
Source: https://help.zscaler.com/itdr/adding-issue-active-directory-issue-safelist
PDF: https://help.zscaler.com/pdf/com/en/1531638.pdf

If an issue on the [Detailed Findings and Recommendations](/itdr/viewing-focus-area-details) page of a scanned AD domain doesn't pose any risk, you can mark it as safe by adding it to the Active Directory Issue Safelist.
After you add an issue to the Active Directory Issue Safelist, it disappears from the [Detailed Findings and Recommendations](/itdr/viewing-focus-area-details) page and [vulnerability report](/itdr/viewing-vulnerability-report) for the selected AD domain only. This issue is not marked safe if you select a different scanned AD domain.
To add an issue to the Active Directory Issue Safelist:
- Go to **ITDR** > **Dashboard **> **Identity Posture.**
-
On the **Identity Posture **page:
- Select an AD domain from the **Result for** drop-down menu.
- Select a timestamp from the **scanned on** drop-down menu.
[See image.](#zscaler-deception-itdr-safelist-timestamp)
The scan result for the AD domain appears.
-
Under **Detailed Findings and Recommendations**, click an issue.
[See image.](#deception-itdr-focus-area-issue)
-
On the** Detailed Findings and Recommendations** page, click **Add Issue to Safelist** for the selected issue.
[See image.](#zscaler-deception-itdr-issue-add-safelist)
-
In the **Add to Safelist** window, enter a reason for marking the issue safe and set an expiration date if needed.
[See image.](#zscaler-deception-itdr-issue-safelist-reason)
-
Click **Save**.
The issue is added to the safelist. You can [view](/itdr/about-active-directory-posture-safelist-0) it on the **Active Directory Issue Safelist** page.
[]![Selecting an AD domain and timestamp](/downloads/itdr/safelists/entra-id-safelists/entra-id-issue-safelist/adding-issue-entra-id-issue-safelist/itdr-ad-domainselection-dashboard.png)
[]![Selecting a vulnerability issue](/downloads/itdr/safelists/entra-id-safelists/entra-id-issue-safelist/adding-issue-entra-id-issue-safelist/itdr-issue-selection-ad-dashboard.png)
[]![Adding a vulnerability issue to the safelist](/downloads/itdr/safelists/entra-id-safelists/entra-id-issue-safelist/adding-issue-entra-id-issue-safelist/itdr-add-issue-to-safelist-ad-button.png)
[]![Entering a reason for adding an issue to safelist](/downloads/itdr/safelists/entra-id-safelists/entra-id-issue-safelist/adding-issue-entra-id-issue-safelist/itdr-add-to-safelist-window.png)