# Viewing Compliance Details
Source: https://help.zscaler.com/dspm/viewing-compliance-details
PDF: https://help.zscaler.com/pdf/com/en/1514771.pdf

You can view additional details of the compliance breaches, such as the list of [policies ](/dspm/about-data-posture-policies)that failed to comply with each benchmark, failed [resources](/dspm/viewing-resource-details), and DSPM policies mapped to compliance frameworks. The granular breach information allows you to quickly investigate and take the necessary action.
To view the compliance details:
- Go to **Analytics** > **Compliance**.
- Click any tile to view the compliance insights.
[See image.](#compliance_tiles)
- On the Compliance page, you can see the following tabs:
- [Summary](#summary)
- [Policies](#policies-tab)
- [Resources](#resource-tab)
- [Configuration](#configuration)
[]The Summary tab displays the total number of policies that failed to meet the compliance criteria, highlighting failed policies by severity and control category and providing actionable items for remediation. You can:
- Apply [filters](/dspm/using-filters) to view specific data.
- View the following details of the compliance framework:
- **Description**: The name of the compliance framework.
- **DLP Engines**: The DLP engines mapped to the compliance benchmarks.
- **Data Stores**: The total number of noncompliant data stores.
- View the number of failed policies by severity (**Critical**, **High**, **Medium**, and **Low**). Hover over the donut chart to see the number of failed policies for each severity. Click to view the list of policies with the severity filter applied.
- View the number of failed policies for each control category. Click to view the list of policies with the control category filter applied.
- View the compliance trend in a bar chart to assess the improvements or degradations. Hover over the chart to view the number of failed policies and resources for the control category. You can view the data for the last 7, 15, 30, 60, or 90 days.
![The summary tab with the list of policies and alerts for compliance issues](/downloads/dspm/analytics/compliance/viewing-compliance-details/dspm-compliance-summary-tab_0.png)
[]
![The compliance page with annotation around one of the compliance tiles.](/downloads/dspm/analytics/compliance/viewing-compliance-details/dspm-compliance-tiles.png)
[]The Configuration tab displays the mapping of DSPM policies to compliance frameworks. You can:
- View the name of the compliance framework and the DLP engines mapped to the benchmark.
- Apply [filters](/dspm/using-filters) to view specific data.
- View the list of failed policies. For each policy, you can see:
- **Policy Name**: The name of the policy mapped to the compliance framework.
- **Cloud**: The name of the cloud service provider.
- **Control Number**: A unique identifier assigned to a specific policy within a compliance framework.
- **Control Category**: The control category of the compliance framework that groups security controls addressing similar risks or compliance requirements.
- **Severity**: The severity (**Critical**, **High**, **Medium**, or **Low**) of policy failure.
- Search for a specific policy.
- Export the data and [download the report](/dspm/about-reports) as an Excel file.
![The configuration tab displaying the mapping of DSPM policies to compliance frameworks.](/downloads/dspm/analytics/compliance/viewing-compliance-details/dspm-compliance-configuration-tab.png)
[]The Resources tab displays the list of [resources](/dspm/about-data-inventory) that are noncompliant. You can:
- View the list of failed resources. For each resource, you can see:
- **Resource Name**: The name of the resource.
- **Cloud Account**: The account ID of the cloud account where the resource is stored.
- **Region**: The region where the resource is located.
- **DLP Engines**: The DLP engines that matched the data in the resource.
- **Resource ID**: The unique identifier for the resource.
- Apply [filters](/dspm/using-filters) to view specific data.
- Search for a specific resource.
- Export the data and [download the report](/dspm/downloading-reports) as an Excel file.
![The resources tab displaying the list of failed resources.](/downloads/dspm/analytics/compliance/viewing-compliance-details/dspm-compliance-resources-tab_0.png)
[]The Policies tab displays the list of policies that failed to comply with the benchmark. You can:
- View the list of failed policies. For each policy, you can see:
- **Policy Name**: The name of the failed policy. Click to view the [policy details](/dspm/viewing-policy-details).
- **Severity**: The severity (**Critical**, **High**, **Medium**, or **Low**) of policy failure.
- **Control Number**: A unique identifier assigned to a specific policy within a compliance framework.
- **Control Category**: The control category of the compliance framework that groups security controls addressing similar risks or compliance requirements.
- **Cloud**: The name of the cloud service provider.
- **Data Stores**: The number of data stores for which the policy failed.
- Apply [filters](/dspm/using-filters) to view specific data.
- Search for a specific policy.
- Export the data and [download the report](/dspm/about-reports) as an Excel file.
![The policies tab displaying the list of failed policies.](/downloads/dspm/analytics/compliance/viewing-compliance-details/dspm-compliance-policies-tab.png)