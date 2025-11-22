# Adding an Entra ID Object to the Safelist
Source: https://help.zscaler.com/itdr/adding-entra-id-object-safelist
PDF: https://help.zscaler.com/pdf/com/en/1531767.pdf

On the [Detailed Findings and Recommendations](/itdr/viewing-entra-id-focus-area-details) page for an Entra ID issue in the [Entra ID dashboard](/itdr/about-entra-id-dashboard), you can view the list of Entra ID objects (users and service principals) that are vulnerable to attack. You can review these objects to confirm that they are not a risk and mark them as safe.
Adding objects to the safelist impacts the unified risk score on the [Entra ID Dashboard](/itdr/about-entra-id-dashboard).
After you add objects to a safelist, they disappear from the Who is affected? section on the [Detailed Findings and Recommendations](/itdr/viewing-entra-id-focus-area-details) page and [vulnerability report](/itdr/viewing-entra-id-vulnerability-report) for that particular issue only. These objects are not marked safe if you select a different issue in the same Entra ID tenant.
To add an object to the safelist:
- Go to **ITDR** > **Dashboard **> **Entra ID**.
- On the **Entra ID Dashboard**:
- Select an Entra ID tenant from the **Result for** drop-down menu.
-
Select a timestamp from the **scanned on** drop-down menu.
[See image.](#itdr-object-safelist-timestamp)
The scan result for the Entra ID tenant appears.
-
Under **Detailed Findings and Recommendations**, click an issue.
[See image.](#itdr-object-safelist-focus-area-issue)
- On the** Detailed Findings and Recommendations **page, scroll down to the **Who is affected?** section for the selected issue.
- Add objects to the safelist using one of the following methods:
-
To add a specific item to the object safelist, click the **Shield** icon to mark an object safe.
[See image.](#itdr-object-safelist-focus-area)
-
To add multiple items to the object safelist, select the items, and click **Add Objects to Safelist**.
[See image.](#add-objects-to-safelists)
-
In the **Add to Safelist** window, enter a reason for marking this Entra ID object safe and set an expiration date if needed.
[See image.](#itdr-object-safelist-reason)
If you are adding multiple objects to the safelist simultaneously, the same reason and expiration date are applied to all those objects.
[See image.](#bulk-add-list)
-
Click **Save**.
The Entra ID object is added to the safelist. You can view and manage it from the** **[Entra ID Object Safelist](/itdr/about-entra-id-object-safelist).
[]![Select Domain and Timestamp in Entra ID Dashboard](/downloads/itdr/safelists/entra-id-safelists/entra-id-object-safelist/adding-entra-id-object-safelist/itdr-entraid-tenant-selection.png)
[]![Issue in Focus Area](/downloads/itdr/safelists/entra-id-safelists/entra-id-object-safelist/adding-entra-id-object-safelist/itdr-entra-id-select-an-issue.png)
[]![Add to Safelist Option](/downloads/itdr/safelist/active-directory-safelists/active-directory-object-safelist/adding-active-directory-object-safelist/itdr-add-object-to-safelist-entra-id.png)
[]![A screenshot highlighting the option to add objects to safelist in bulk](/downloads/itdr/safelist/entra-id-safelist/entra-id-obejct-safelist/adding-entra-id-object-safelist/itdr-add-objects-to-safelists-entra-id.png)
[]![A screenshot of adding object to safelist option in remidiation chart](/downloads/itdr/safelist/entra-id-safelist/entra-id-obejct-safelist/adding-entra-id-object-safelist/itdr-flowchart-add-object-safelist.png)
[]![Add to Safelist Window ](/downloads/itdr/safelists/entra-id-safelists/entra-id-object-safelist/adding-entra-id-object-safelist/itdr-add-to-safelist-window.png)
[]![itdr-multiple-objects-tosafelist.png](/downloads/itdr/safelist/entra-id-safelist/entra-id-obejct-safelist/adding-entra-id-object-safelist/itdr-multiple-objects-tosafelist.png)