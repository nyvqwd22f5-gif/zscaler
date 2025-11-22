# About Dynamic Application Datasets
Source: https://help.zscaler.com/deception/about-dynamic-application-datasets
PDF: https://help.zscaler.com/pdf/com/en/1531481.pdf

Dynamic Application Datasets allow you to configure threat intelligence decoys and network decoys with dynamic web applications that mimic some of the behaviors of legitimate applications. While the dynamic interactions are configured using [Vulnerable Application Datasets](/deception/about-vulnerable-application-datasets-cve-datasets), the front-end UI of the application is configured by associating appropriate Static Application Datasets.
Dynamic application datasets provide the following benefits and enable you to:
- Create a building block for dynamic web application decoys by grouping necessary mimics of vulnerable behaviors, front-end UI, and other parameters into a single unit.
- Build threat intelligence decoys and network decoys for dynamic web applications with a high degree of resemblance to legitimate applications.
About the Dynamic Application Datasets Page
On the Dynamic Application Datasets page (Miragemaker > Dynamic Application Datasets), you can do the following:
- View the list of prepopulated and custom dynamic application datasets, and search for a specific entry by name. For each dynamic application dataset, you can see:
- **Name**: The name of the dynamic application dataset.
- **Static Application Datasets**: The list of static application datasets that are associated with the dynamic application dataset.
- **Vulnerable Application Datasets**: The list of vulnerable application datasets that are associated with the dynamic application dataset.
- [Configure a dynamic application dataset](/deception/adding-dynamic-application-dataset).
- [Edit or delete a dynamic application dataset](/deception/editing-or-deleting-dynamic-application-dataset).
![A screenshot of the Dynamic Application Datasets page in the Zscaler Deception Portal](/downloads/deception/miragemaker/application-datasets/about-dynamic-application-datasets/zscaler-deception-about-dynamic-application-dataset.png)