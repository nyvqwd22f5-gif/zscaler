# Managing Asset Compliance Policies
Source: https://help.zscaler.com/uvm/managing-asset-compliance-policies
PDF: https://help.zscaler.com/pdf/com/en/1531111.pdf

After [creating a policy](/uvm/configuring-asset-compliance-policies), you can manage and adjust its settings and criteria in the Policies table, a centralized view of all policies. To view policies in your account, go to the AEM app and click Policies.
For access to Policies, your assigned role must include the Read, Create, Edit permissions under the Assets App > Policy Rule resource. To learn more, see [Creating Custom Roles](/uvm/creating-custom-roles) and [Assigning Roles to Users](/uvm/assigning-roles-users). Users assigned the Assets Admin role can create and manage policies, but can't delete them.
When managing policies, you can perform the following actions:
- [Edit a Policy](#edit-policy)
- [Delete a Policy](#delete-policy)
- [See Runs](#see-runs)
- [Duplicate a Policy](#duplicate-policy)
- [Process a Policy Immediately](#process-policy-immediately)
[]You can edit a policy to adjust its scope, refine asset filters, update tool coverage requirements, or modify conditions.
Editing a policy automatically updates all existing and future policy violations associated with it. Confirm the changes when prompted.
To edit a policy:
- Go to **Assets **> **Policies**.
-
Hover over the policy you want to edit, and click the **Edit** icon.
The **Edit Policy** page appears.
- Make the necessary changes.
- Click **Save**.
[]You can delete a policy if it is no longer needed, such as when a tool is decommissioned or replaced.
To delete a policy:
- Go to **Assets** > **Policies**.
- Choose one of the following options:
- To delete a single policy, hover over the policy and click the **Delete** icon.
- To delete multiple policies, select the policies from the table and click **Delete**.
- Select your preferred option in the warning window:
- Delete the policy but retain all existing violations.
- Delete both the policy and all associated violations.
- Click **Delete**.
[]Monitor policy runs to track timestamps, statuses, and potential failures. This can be useful for troubleshooting issues.
To see runs:
- Go to **Assets** > **Policies**.
-
Hover over the policy you want to monitor, and click the **See Runs** icon.
The **Policy Runs **page appears.
[]You can duplicate an existing policy to save time when creating a new policy with similar logic but slight modifications.
To duplicate a policy:
- Go to **Assets** > **Policies**.
-
Hover over the policy you want to duplicate, and click the **Duplicate** icon.
The duplicated policy setup page appears.
- Edit the policy as needed, including changing its name.
- Click **Save**.
[]Policies run automatically upon saving and at their scheduled trigger times. However, you can manually process a policy to sync updates on demand.
To manually process a policy:
- Go to **Assets **> **Policies**.
- Choose one of the following options:
- To process a single policy, hover over the policy and click the **Process Now** icon.
-
To process multiple policies, select the policies from the table and click **Process**.
The policy processes and updates the data in your AEM app.