# About Investigation
Source: https://help.zscaler.com/dspm/about-investigation
PDF: https://help.zscaler.com/pdf/com/en/1477766.pdf

[Watch a video on Investigation with DSPM.](https://fast.wistia.net/embed/iframe/my630v87t6)
Your cloud resources containing data might be located in different regions. Depending on the number of cloud accounts you have onboarded, DSPM offers insights by identifying sensitive data, vulnerabilities, or any other risks in your resources.
You might want to obtain certain information related to the security posture of your cloud resources without having to create alerts or filter information on the dashboard. For example, you want to look at all S3 buckets that were scanned in the past week and check what type of sensitive data is stored in these S3 buckets. You can leverage DSPM's Investigation feature to effectively parse such information, and based on the result, save the investigation or create a custom security policy.
The Investigation feature provides the following benefits and enables you to:
- Run queries on cloud resources and gain more insight into the security posture of your data.
- Customize queries, run them multiple times, inspect results, and then discard or save the queries, either as investigation queries or custom security policies.
About the Investigation Page
On the Investigation page (Analytics > Investigation), you can do the following:
- View the investigation queries that you've created. For each investigation, you can see:
- **Cloud**: The name of the cloud service provider (AWS, Azure, or GCP).
- **Query**: The query string.
- **Resource Type**: The type of resource on which the query is run.
- [Create a new investigation](/dspm/creating-new-investigation).
- Apply [filters](/dspm/using-filters) to view specific information.
- View the list of saved investigation queries.
- Search for a query in the searchable columns.
- [Show or hide columns](/dspm/using-tables).
-
Click the **Actions** icon to run, save, or [edit](/dspm/editing-or-deleting-investigation) a query.
When you run a query, the investigation results are displayed. [See image.](#ds-investigationresults) Click the Resource Name to view the [resource details](/dspm/viewing-resource-details).
![Create a new investigation and view the previously created queries](/downloads/dspm/analytics/investigation/about-investigation/ds-investigationpagenew.png)
[]![Investigation query results for an EC2 instance](/downloads/dspm/analytics/investigation/about-investigation/ds-investigation-results.png)