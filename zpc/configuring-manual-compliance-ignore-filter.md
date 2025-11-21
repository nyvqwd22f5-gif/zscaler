# Configuring a Manual Compliance Ignore Filter
Source: https://help.zscaler.com/zpc/configuring-manual-compliance-ignore-filter
PDF: https://help.zscaler.com/pdf/com/en/1462841.pdf

You might want to ignore compliance security policies from being evaluated by ZPC for your cloud deployment. For example, you might use AWS S3 buckets on your cloud deployment only for QA and would not want them to be evaluated for compliance. You can ignore specific policies for AWS S3 buckets and ZPC doesn't evaluate those specific security policies for any S3 bucket.
When a compliance security policy is ignored, all relevant assets for that policy are also ignored by ZPC. If you need some assets to be evaluated by ZPC for the same security policy, you can manually include those assets for ZPC evaluation.
- When you ignore a policy, its status changes to "Ignored". ZPC categorizes ignored policies as passed for its compliance score evaluation. You might notice a change in your policy compliance score after ignoring or including policies for ZPC evaluation.
- When you ignore an asset, its status changes to "Ignored". ZPC categorizes ignored assets as passed for its compliance score evaluation. You might notice a change in your asset compliance score after ignoring or including assets for ZPC evaluation.
Ignoring Compliance Security Policies
You can ignore one or multiple compliance security policies on ZPC. When you ignore a compliance security policy, all relevant assets are also ignored.
- [Ignore a Compliance Security Policy](#ignore-single-compliance-policy)
- [Ignore Multiple Compliance Security Policies](#ignore-multiple-compliance-policies)
Including Compliance Security Policies
You can include one or multiple previously ignored compliance security policies for ZPC evaluation. When you include a compliance security policy, all relevant assets are also included.
- [Include a Compliance Security Policy](#include-single-compliance-policies)
- [Include Multiple Compliance Security Policies](#include-multiple-compliance-policies)
Ignoring Assets for a Compliance Security Policy
You can ignore one or multiple assets for a particular compliance security policy. When you ignore an asset for a particular policy, ZPC continues to evaluate other compliance policy against the asset.
- [Ignore an Asset for a Compliance Security Policy](#ignore-single-asset)
- [Ignore Multiple Assets for a Compliance Security Policy](#ignore-multiple-assets)
Including Assets for a Compliance Security Policy
You can include one or multiple previously ignored assets for a security policy again for ZPC evaluation.
- [Include an Asset for a Compliance Security Policy](#include-single-asset)
- [Include Multiple Assets for a Compliance Security Policy](#include-multiple-assets)
[]
- Go to **Cloud Posture** > **Compliance**.
- Click the **Benchmark Name** for the compliance benchmark you want to select.
- For the included security policy you want to ignore, click the **Actions** icon, then select **Ignore Policy**.
[See image.](#ignore-single-compliance-policy-image)
- In the **Ignore Policy** window, enter a comment, then click **Ignore Policy**.
[See image.](#ignore-single-compliance-policy-window-image)
[]
- Go to **Cloud Posture** > **Compliance**.
- Click the **Benchmark Name** for the compliance benchmark you want to select.
- Select policies you want to ignore.
- Click **Actions**, then select **Ignore Policy**.
[See image.](#ignore-multiple-compliance-policies-image)
- In the **Ignore Policy** window, enter a comment, then click **Ignore Policy**.
[See image.](#ignore-multiple-compliance-policies-window-image)
[]
- Go to **Cloud Posture** > **Compliance**.
- Click the **Benchmark Name** for the compliance benchmark you want to select.
- For the ignored security policy you want to include, click the **Actions** icon, then select **Include Policy**.
[See image.](#include-single-compliance-policies-image)
- In the **Include Policy** window, enter a comment, then click **Include Policy**.
[See image.](#include-single-compliance-policies-window-image)
[]
- Go to **Cloud Posture** > **Compliance**.
- Click the **Benchmark Name** for the compliance benchmark you want to select.
- Select ignored policies you want to include.
- Click **Actions**, then select **Include Policy**.
[See image.](#include-multiple-compliance-policies-image)
- In the **Include Policy** window, enter a comment, then click **Include Policy**.
[See image.](#include-multiple-compliance-policies-window-image)
[]
- Go to **Cloud Posture** > **Compliance**.
- Click the **Benchmark Name** for the compliance benchmark you want to select.
- Click the **Policy ID** relevant to the asset you want to ignore.
- On the **Assets** tab, for the single asset you want to ignore, click the **Actions** icon, then select **Ignore Asset**.
[See image.](#ignore-single-asset-image)
- In the **Ignore Asset** window, enter a comment, then click **Ignore Asset**.
[See image.](#ignore-single-asset-window-image)
[]
- Go to **Cloud Posture** > **Compliance**.
- Click the **Benchmark Name** for the compliance benchmark you want to select.
- Click the **Policy ID** relevant to the asset you want to ignore.
- On the **Assets** tab, select all included assets to ignore.
- Click **Actions**, then select **Ignore Asset**.
- In the **Ignore Asset** window, enter a comment, then click **Ignore Asset**.
[]
- Go to **Cloud Posture** > **Compliance**.
- Click the **Benchmark Name** for the compliance benchmark you want to select.
- Click the **Policy ID** relevant to the asset you want to include.
- On the **Assets** tab, for the ignored single asset you want to include, click the **Actions** icon, then select **Include Asset**.
- In the **Include Asset** window, enter a comment, then click **Include Asset**.
[]
- Go to **Cloud Posture** > **Compliance**.
- Click the **Benchmark Name** for the compliance benchmark you want to select.
- Click the **Policy ID** relevant to the asset you want to ignore.
- On the **Assets** tab, select all ignored assets to include.
- Click **Actions**, then select **Include Asset**.
- In the **Include Asset** window, enter a comment, then click **Include Asset**.
[]
![View how to ignore a single policy.](/downloads/zpc/cloud-posture/compliance/configuring-compliance-ignore-filter/zpc-compliance-ignore-single-policy.png)
[]
![View the ignore window for a single policy.](/downloads/zpc/cloud-posture/compliance/configuring-compliance-ignore-filter/zpc-compliance-ignore-single-policy-pop-up.png)
[]
![View how to ignore multiple policies.](/downloads/zpc/cloud-posture/compliance/configuring-compliance-ignore-filter/zpc-compliance-ignore-multiple-policies.png)
[]
![View the ignore window for multiple policies.](/downloads/zpc/cloud-posture/compliance/configuring-compliance-ignore-filter/zpc-compliance-ignore-multiple-policies-pop-up.png)
[]
![View how to include a single policy.](/downloads/zpc/cloud-posture/compliance/configuring-compliance-ignore-filter/zpc-compliance-include-single-policy.png)
[]
![View the include window for a single policy.](/downloads/zpc/cloud-posture/compliance/configuring-compliance-ignore-filter/zpc-compliance-include-single-policy-pop-up.png)
[]
![View how to include multiple policies.](/downloads/zpc/cloud-posture/compliance/configuring-compliance-ignore-filter/zpc-compliance-include-multiple-policy.png)
[]
![View the include window for multiple policies.](/downloads/zpc/cloud-posture/compliance/configuring-compliance-ignore-filter/zpc-compliance-include-multiple-policy-pop-up.png)
[]
![View how to ignore a single asset.](/downloads/zpc/cloud-posture/compliance/configuring-compliance-ignore-filter/zpc-compliance-ignore-single-asset.png)
[]
![View the ignore window for a single asset.](/downloads/zpc/cloud-posture/compliance/configuring-compliance-ignore-filter/zpc-compliance-ignore-single-asset-pop-up.png)