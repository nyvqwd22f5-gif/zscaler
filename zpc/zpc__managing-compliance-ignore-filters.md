# Managing Compliance Ignore Filters
Source: https://help.zscaler.com/zpc/managing-compliance-ignore-filters
PDF: https://help.zscaler.com/pdf/com/en/1462851.pdf

You can edit or delete a previously created compliance ignore rule if it's no longer relevant to your organization's compliance posture needs. ZPC offers you the ability to enable or disable compliance ignore rules.
Enabling or Disabling Compliance Ignore Rules
To enable or disable a compliance ignore rule:
- On the **Compliance** page (Cloud Posture > Compliance), select the **Ignore Rules** tab.
- Use the **State** toggle bar to enable or disable a compliance ignore rule.
- In the **Enable Ignore Rule** or **Disable Ignore Rule** window, click **Enable** or **Disable**.
Editing Compliance Ignore Rules
To edit a compliance ignore rule:
- On the **Compliance** page (Cloud Posture > Compliance), select the **Ignore Rules** tab.
- Do one of the following:
- Click the **Actions** icon, then click **Edit**.
- Click the **Rule Name**, then use the **Actions** drop-down menu to select **Edit**.
- On the **General Information** page, do the following:
- **Ignore Rule Name**: Enter the ignore rule name.
- **Rule Description**(Optional): Enter the ignore rule description.
- **Ignore Rule End Date**(Optional): Use the drop-down menu to select when the ignore rule should no longer be applied.
- Click **Next**.
- On the **Ignore Filter Scope** page, you can determine the scope for the ignore rule using the following filters:
- [Policies](#compliance-ignore-filters-scope-policies)
- [Cloud Accounts](#compliance-ignore-filters-scope-cloud-accounts)
- [Tags](#compliance-ignore-filters-scope-tags)
- [Assets](#compliance-ignore-filters-scope-assets)
- [Regions](#compliance-ignore-filters-scope-regions)
- Click **Next**.
- On the **Summary** page, you can review the ignore rule details.
- Click **Finish**.
Deleting Compliance Ignore Rules
To delete a compliance ignore rule:
- On the **Compliance** page (Cloud Posture > Compliance), select the **Ignore Rules** tab.
- Do one of the following:
- Click the **Actions** icon, then click **Delete**.
- Click the **Rule Name**, then use the **Actions** drop-down menu to select **Delete**.
- In the **Delete Ignore Rule** window, click **Delete**.
[]
You can use the following options to filter compliance security policies that you want to ignore:
- **All Policies**: The filter applies to all policies.
- **Severity**: Select the required **Policy Severity** from the drop-down menu.
-
**Select Policies**: Select to view the **Select Existing Policies** page, and select the required policies from the table.
To learn more, see [About Security Policies.](/zpc/about-security-policies)
By default, the **All Policies** filter is selected.
[]
You can use the following options to filter cloud accounts that you want to ignore:
- **All Accounts**: The filter applies to all cloud accounts.
- **Select Accounts**: Select the required [cloud accounts](/zpc/about-cloud-accounts) that must be included in the filter.
- **Cloud Provider**: Select the cloud provider (**AWS**, **Azure**, **GCP**, or **Kubernetes**).
By default, the **All Accounts** filter is selected.
[]
You can select resources to ignore based on native cloud service provider tags.
Click the **Tags** drop-drown menu and choose **Select Tags**. Click the **Add Tags** icon that appears, to include the required tags.
By default, the **All Tags** filter is selected.
[]
You can use the following options to filter assets that you want to ignore:
- []**All Assets**: The filter applies to all assets.
- **Asset Type**: Select the required [Asset Type](/zpc/cloud-asset-types-and-asset-categories) from the drop-down menu. For example, S3 buckets or EC2 instances.
- **Asset Category**: Select the required [Asset Category](/zpc/cloud-asset-types-and-asset-categories) from the drop-down menu. For example, Analytics or Compute.
By default, the **All Assets** filter is selected.
[]
You can select resources to ignore based on the region they are available in.
Click the **Regions** drop-drown menu and choose **Select Regions**. Use the **Regions** drop-down menu to include the required regions.
By default, the **All Regions** filter is selected.