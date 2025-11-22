# Viewing Benchmark Details
Source: https://help.zscaler.com/zpc/viewing-benchmark-details
PDF: https://help.zscaler.com/pdf/com/en/1406941.pdf

Zscaler Posture Control (ZPC) displays relevant information for each compliance benchmark it offers. You can view each benchmark in detail by selecting a benchmark from the [Compliance](/zpc/about-compliance) page.
About the Benchmark Details Page
On the Benchmark details page (Cloud Posture > Compliance), you can do the following:
- Filter benchmark details using available parameters. To learn more, see [Using Filters](/zpc/using-filters#compliance-filters).
- Export the benchmark details as a PDF file.
- View the **Policy Compliance Posture** donut chart: View the compliance score percentage, the passed policy count, the failed policy count, and the ignored policy count.
- View **Asset Compliance**: View the passed, ignored, and failed assets for the benchmark.
- View **Policy Compliance Trend**: View the passed and failed policy trend over the last 30 days.
- View the following policy details:
- **Policy ID**: Click the Policy ID for any security policy to view more compliance policy details. To learn more, see [Viewing Compliance Security Policy Details](/zpc/viewing-compliance-security-policy-details).
- **Control No**: The compliance control number for the policy.
- **Policy Name**: View the policy title.
- **Cloud**: View the cloud service provider the security policy protects.
- **Type**: View whether the policy is predefined or a custom policy.
- **Category**: View the compliance category, such as Networking.
- **Severity**: Static value signaling the severity of policy failure. The value can be **Critical**, **High**, **Medium**, or **Low**.
- **Passed Assets**: View the passed and total asset count for each security policy.
- **Status**: View whether the security policy status. A security policy passes only when all assets pass. The following status are available for the policy:
- **Passed**: The security policy has passed for all relevant assets.
- **Failed**: The security policy has failed for all relevant assets.
- **No Resources**: The security policy cannot be evaluated by ZPC as it does not have necessary resources.
- **Manual**: The security policy requires you to manually offer information for ZPC to evaluate it.
- **Disabled**: The security policy is disabled and is not being evaluated by ZPC.
- **Ignored**: The security policy is ignored and not being evaluated by ZPC.
- Ignore or include the policy for ZPC evaluation. To learn more, see [Configuring a Compliance Ignore Filter](/zpc/configuring-compliance-ignore-filter).
If you disabled a compliance benchmark, you can view the last date when the compliance information was generated. [See image.](#last-generated-compliance-information)
If you have just enabled a benchmark, ZPC shows the Policy Compliance Trend only after 24 hours.
[See image.](#policy-compliance-timeline-trend)
![View the compliance benchmark details on ZPC.](/downloads/zpc/cloud-posture/compliance/viewing-benchmark-details/zpc-viewing-compliance-benchmark-details.png)
[]
![View the last generated compliance benchmark details](/downloads/zpc/cloud-posture/compliance/about-benchmark-details/zpc-benchmark-details-last-generated.png)
[]
![View the policy compliance trend for newly enabled benchmarks](/downloads/zpc/cloud-posture/compliance/about-benchmark-details/zpc-benchmark-details-timeline-trend.png)