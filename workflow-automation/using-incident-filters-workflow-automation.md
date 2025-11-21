# Using Incident Filters in Workflow Automation
Source: https://help.zscaler.com/workflow-automation/using-incident-filters-workflow-automation
PDF: https://help.zscaler.com/pdf/com/en/1468511.pdf

In the Workflow Automation Admin Portal, the incidents that occur in your organization are displayed on the Incidents page. You can use filters to modify the incidents that are displayed on the page. Some of the filters have predefined values that you select, and some of the filters require you to enter a text string value. The following filters have predefined values:
- **Action**
- **Channel**
- **Department**
- **Dictionary**
- **DLP Admin**
- **DLP Type**
- **Document Type**
- **Duplicated Incidents**
- **Engine**
- **External Collaborators Groups**
- **File Type**
- **Home Location**
- **Incident Group**
- **Integration**
- **Label**
- **Other Rule**
- **Priority**
- **Rule**
- **Severity**
- **Source DLP Type**
- **Status**
- **Work Location**
To use these predefined filters, select to include or exclude one or more of the predefined values that appear for these filters.
You must enter a text string for the following filters:
- **Application Category**
- **Application Name**
- **Client IP**
- **External Recipients**
- **File Modified By**
- **File Name**
- **File Shared By**
- **File Source Location**
- **Hostname or Application**
- **Internal Recipients**
- **Referrer URL**
- **Triggered Recipients**
- **URL**
- **User**
The text string values are not case sensitive. In addition, you can do the following:
- Enter multiple values for these filters by entering a comma between the text string values.
- Enter multiple strings within a single text string value. If you enter multiple strings within a text string value, each string is treated with an AND operation. For example, if you select the **Application Name** filter and enter `Microsoft Office` as the text string value, all incidents with an application name containing Microsoft and Office are returned with this filter, such as Microsoft Office, Microsoft Office 365, and Office 365 Microsoft. This filter does not return incidents with an application name containing only Microsoft or Office.
- For the Referrer URL filter and the URL filter, enter a complete URL (e.g., https://www.jumpshare.com/https-post) or enter a complete host name (e.g., www.jumpshare.com) for the URL.
You can do the following:
- [Apply Filters](#apply-filters)
- [Save Filters](#save-filters)
- [Apply Saved Filters](#apply-saved-filters)
- [Delete Saved Filters](#delete-saved-filters)
[]To apply filters:
-
On the **Incidents** page, click **Filters**. The **Filters** window appears, displaying all the available filters on the left side of the window. If you choose the **User Name** attribute, or the **Client IP** attribute, or the **Recipient Email** attribute for obfuscation, you cannot filter incidents using these obfuscated user attributes. Obfuscating the **Recipient Email** attribute disables the **External Recipients** filter, the **Internal Recipients **filter, and the **Triggered Recipients** filter. To learn more about obfuscation settings, see [Managing Account Settings](/workflow-automation/managing-account-settings) and [Managing Admin Assignments](/workflow-automation/managing-admin-assignments).
[See image.](#Filters-Window-Initial)
-
Select a filter and then select or enter the filter values to include or exclude on the right side of the window. As you select or enter the filter values, the number of values selected appears next to the filter. You can select multiple filters and their values. For filters with predefined values (e.g., **Department** and **Dictionary**), you can select to include or exclude all the filter values by selecting the **Select All **checkbox. To remove all the selected filters, click **Reset**.
[See image.](#Filters-Window-Filter-Selected)
- Click **Apply**. The **Incidents** page reappears, displaying the incidents that match the filter criteria.
[]To save filters:
-
On the **Incidents** page, click **Filters**. The **Filters** window appears, displaying all the available filters on the left side of the window.
[See image.](#Filters-Window-Initial-Save-Filters)
-
Select a filter and then select or enter the filter values to include or exclude on the right side of the window. You can select multiple filters and their values. For filters with predefined values (e.g., **Department** and **Dictionary**), you can select to include or exclude all the filter values by selecting the **Select All **checkbox.
[See image.](#Filters-Window-Filters-Selected-Save-Filters)
- Click **Save As. **The **My Filters** dialog window appears.
-
In the **My Filters** dialog window, enter a name for the filter in the **Filter Name** field.
[See image.](#My-Filters-Dialog-Window)
-
Click **Save**. The filter is saved and is available for selection under the **My Filters** drop-down menu in the **Filters** window.
[See image.](#My-Filters-Drop-Down-Menu)
[]To apply saved filters:
-
On the **Incidents** page, click **Filters**. The **Filters** window appears, displaying all the available filters on the left side of the window.
[See image.](#Filters-Window-Initial-Apply-Saved-Filters)
-
Select a saved filter from the **My Filters** drop-down menu. The **Filters** window reappears, displaying the filters associated with that saved filter.
[See image.](#Filters-Window-Select-Saved-Filter)
- Click **Apply**. The **Incidents** page reappears, displaying the incidents that match the filter criteria.
[]To delete saved filters:
-
On the **Incidents** page, click **Filters**. The **Filters** window appears, displaying all the available filters on the left side of the window.
[See image.](#Filters-Window-Initial-Delete-Saved-Filters)
-
From the **My Filters** drop-down menu, click the **Delete** icon next to the saved filter that you want to delete. A message appears asking whether you are sure that you want to delete the filter.
[See image.](#Filters-Window-Delete-Saved-Filter)
- Click **Yes**. The saved filter is deleted.
[]![Viewing the Filters window on the Incidents page in the Workflow Automation Admin Portal](/downloads/workflow-automation/incidents/using-incident-filters-workflow-automation/WA-Filters-Window-Initial_1.png)
[]![Viewing the Filters window with a few of the filter options selected to include and exclude for the Department filter. Accounting, Engineering, and Sales department filter options are included. Service Admin and Support department filter options are excluded.](/downloads/workflow-automation/incidents/using-incident-filters-workflow-automation/WA-Filters-Window-Filter-Selected_1.png)
[]![Viewing the Filters window on the Incidents page with all the available filters displayed](/downloads/workflow-automation/incidents/using-incident-filters-workflow-automation/WA-Filters-Window-Initial-Save-Filters_1.png)
[]![Viewing the Filters window with the Department filter and Dictionary filter selected](/downloads/workflow-automation/incidents/using-incident-filters-workflow-automation/WA-Filters-Window-Selected-Saved-Filters_0.png)
[]![Entering a filter name on the My Filters dialog window in the Filters window](/downloads/workflow-automation/incidents/using-incident-filters-workflow-automation/WA-My-Filters-Dialog-Window-Save-Filters_0.png)
[]![Viewing the saved filters in the Filters window in the Workflow Automation Admin Portal. The My Filters drop-down menu shows options for Credit Card Information, Resolved Incidents, Social Security Number Incidents - Accounting Department, Social Security Number Incidents - Critical, Social Security Number Incidents - Inline - Critical.](/downloads/workflow-automation/incidents/using-incident-filters-workflow-automation/WA-Filters-Window-My-Filters-Drop-Down-Menu_2.png)
[]![Viewing the Filters window on the Incidents page with all the available filters displayed](/downloads/workflow-automation/incidents/using-incident-filters-workflow-automation/WA-Filters-Window-Initial-Applied-Saved-Filters_0.png)
[]![Selecting a saved filter in the My Filters drop-down menu on the Filters window in the Workflow Automation Admin Portal](/downloads/workflow-automation/incidents/using-incident-filters-workflow-automation/WA-Filters-Window-My-Filter-Selected_2.png)
[]![Viewing the Filters window on the Incidents page with all the available filters displayed](/downloads/workflow-automation/incidents/using-incident-filters-workflow-automation/WA-Filters-Window-Initial-Delete-Filters_1.png)
[]![Filters window displaying the following message after you click the Delete icon next to a saved filter: Are you sure you want to delete? Along with No and Yes buttons for the response.](/downloads/workflow-automation/incidents/using-incident-filters-workflow-automation/WA-Filters-Window-Delete-Saved-Filters_2.png)