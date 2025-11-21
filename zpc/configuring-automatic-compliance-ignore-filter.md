# Configuring an Automatic Compliance Ignore Filter
Source: https://help.zscaler.com/zpc/configuring-automatic-compliance-ignore-filter
PDF: https://help.zscaler.com/pdf/com/en/1467971.pdf

You might want to ignore compliance security policies from being evaluated by ZPC for your cloud deployment. For example, you might use some AWS S3 buckets located in a specific region on your cloud deployment only for QA and would not want them to be evaluated for compliance. You can configure an automatic compliance ignore rule and use the scope to tactfully remove the QA AWS S3 buckets from being evaluated against a specific set of compliance policies.
Configuring Automatic Compliance Ignore Rules
You can create an automatic compliance ignore rule on ZPC and specify the scope where the rule operates. To create an automatic compliance ignore rule:
- Go to **Cloud Posture** > **Compliance**.
- Select the **Ignore Rules** tab, then click **Add Ignore Rule**.
- On the **General Information** page:
- **Ignore Rule Name**: Enter the ignore rule name.
- **Rule Description **(Optional): Enter the ignore rule description.
- **Ignore Rule End Date **(Optional): Use the drop-down menu to select when the ignore rule should no longer be applied.
- Click **Next**.
-
On the **Ignore Filter Scope** page, you can determine the scope for the ignore rule using the following filters:
- [Policies](#compliance-ignore-filters-scope-policies)
- [Cloud Accounts](#compliance-ignore-filters-scope-cloud-accounts)
- [Tags](#compliance-ignore-filters-scope-tags)
- [Assets](#compliance-ignore-filters-scope-assets)
- [Regions](#compliance-ignore-filters-scope-regions)
Using the filters, you can create ignore filters such as:
- [Ignore all policies for QA cloud accounts for S3 buckets in the ap-east-1 region.](#ignore-scope-example)
- Click **Next**.
- On the **Summary** page, you can review the ignore rule details.
- Click **Finish**.
ZPC ignores all assets and policies matching the compliance ignore filter for the compliance score evaluation.
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
[]
![View how to configure the compliance ignore rule scope.](/downloads/zpc/cloud-posture/compliance/zpc-compliance-ignore-scope-example.gif.gif)