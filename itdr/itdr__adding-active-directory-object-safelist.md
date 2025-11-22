# Adding an Active Directory Object to the Safelist
Source: https://help.zscaler.com/itdr/adding-active-directory-object-safelist
PDF: https://help.zscaler.com/pdf/com/en/1531640.pdf

On the [Detailed Findings and Recommendations](/itdr/viewing-issue-finding-recommendation-details) page for an Active Directory (AD) issue, you can view the list of AD objects (user accounts and computers) that are vulnerable to attack. You can review these objects to confirm that they are not a risk and mark them as safe.
Adding objects to the safelist impacts the unified risk score on the [ITDR Posture - Active Directory Dashboard](/itdr/about-identity-posture-dashboard).
After you add objects to a safelist, they disappear from the Who is affected? section on the [Detailed Findings and Recommendations](/itdr/viewing-issue-finding-recommendation-details) page and [vulnerability report](/itdr/viewing-vulnerability-report) for that particular issue only. These objects are not marked safe if you select a different issue in the same AD domain.
To add an object to the safelist:
- Go to **ITDR** > **Dashboard**.
- On the **ITDR Posture - Active Directory Dashboard** page:
- Select an AD domain from the **Result for** drop-down menu.
-
Select a timestamp from the **scanned on** drop-down menu.
[See image.](#deception-itdr-object-safelist-timestamp)
The scan result for the AD domain appears.
-
Under **Detailed Findings and Recommendations**, click an issue.
[See image.](#deception-itdr-object-safelist-focus-area-issue)
- On the** Detailed Findings and Recommendations** page, scroll down to the **Who is affected?** section for the selected issue.
- Add objects to the safelist using one of the following methods:
-
To add a specific item to the object safelist, click the **Shield** icon to mark an object safe.
[See image.](#deception-itdr-object-safelist-focus-area)
-
To add multiple items to the object safelist, select the items, and click **Add Objects to Safelist**.
[See image.](#add-objects-to-safelists)
-
In the **Add to Safelist** window, enter a reason for marking this AD object safe and set an expiration date if needed.
[See image.](#deception-itdr-object-safelist-reason)
If you are adding multiple objects to the safelist simultaneously, the same reason and expiration date are applied to all those objects.
[See image.](#bulk-add-list)
-
Click **Save**.
The AD object is added to the safelist. You can [view and manage](/itdr/deleting-object-active-directory-object-safelist) it on the **Object Safelist** page.
[]![Selecting an AD domain and timestamp](/downloads/itdr/safelist/active-directory-safelists/active-directory-object-safelist/adding-active-directory-object-safelist/itdr-ad-domainselection-dashboard-new.png)
[]![Selecting a vulnerability issue](/downloads/itdr/safelist/active-directory-safelists/active-directory-object-safelist/adding-active-directory-object-safelist/itdr-ad-selected-issue.png)
[]![Adding an AD object to the safelist](/downloads/itdr/safelist/active-directory-safelists/active-directory-object-safelist/adding-active-directory-object-safelist/itdr-add-object-tosafelist-button.png)
[]![A screenshot highlighting the bulk option to add objects to safelists](/downloads/itdr/safelist/active-directory-safelists/active-directory-object-safelist/adding-active-directory-object-safelist/itdr-add-objects-t-sfaelists.png)
[]![Enter a reason for adding an AD object to safelist](/downloads/itdr/safelist/active-directory-safelists/active-directory-object-safelist/adding-active-directory-object-safelist/itdr-add-to-safelist-window.png)
[]![itdr-multiple-objects-tosafelist.png](/downloads/itdr/safelist/active-directory-safelists/active-directory-object-safelist/adding-active-directory-object-safelist/itdr-multiple-objects-tosafelist.png)