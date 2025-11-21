# Creating Data Sources
Source: https://help.zscaler.com/uvm/creating-data-sources
PDF: https://help.zscaler.com/pdf/com/en/1527861.pdf

The Zscaler Security Operations (SecOps) platform collects and correlates security findings and business context from a wide range of external tools, such as vulnerability scanners, asset inventories, and cloud providers. To begin ingesting this data into your environment, you must first connect the relevant sources to your account. Establishing these connections ensures that the platform can continuously retrieve and normalize data for analysis, prioritization, and remediation workflows.
This article explains how to create a new data source. For information on managing existing sources, see [Managing Data Sources](/uvm/managing-data-sources).
To create a data source:
-
Go to **Configure** > **Sources**.
A list of all existing sources appears.
- Click** Create**.
-
Select a source from the available tiles. You can also search for a source in the search field.
The source setup page appears.
You can connect a generic AnySource connector, which allows you to upload or extract files from data storage platforms such as Google Cloud Platform (GCP) and AWS S3. To learn more, see [Connecting AnySource](/uvm/connecting-anysource).
- On the source setup page, configure the setup in the following sections:
- [Details](#details-section)
- [Retrieval](#retrieval-section)
- [Scheduling](#scheduling-section)
- [Remediation Detection Settings](#remediation-detection-settings)
- [Suppression Rules](#suppression-rules-section)
- (Optional) Click **Test** to verify the source's authentication and connectivity.
- Click **Save** to save the data source.
Saving the source redirects you to the Sources** **page, where all connected sources are listed. To ensure the data can be correctly processed and used across the platform, you must configure field mappings. Hover over the newly added source and click **Map Data** to map source fields to the corresponding platform fields.
[]In the **Details** section, enter the source's basic details:
- **Name**: Enter a unique name for the data source that accurately reflects the specific data stream instance.
- **Source Name**: Enter the display name for the source.
- **Override Icon Name**: (for AnySource only) If you're connecting an AnySource connector, you can override the default icon with one that matches the vendor's branding.
- **Description**: (Optional) Enter a brief description of the data the source retrieves.
[]In the **Retrieval** section, define how data is fetched from the vendor’s system:
-
**Authentication**: Select an existing authentication or click **Create New** to add an authentication for the vendor. To learn more, see [Configuring Authentications](/uvm/configuring-authentications).
Each source has its own unique set of required parameters outlined in the specific vendor's deployment guide in the [Source Configuration Guides ](/uvm/administration/connectors/sources/source-configuration-guides)section.
-
**Filters and Specifications**: Configure available data retrieval filters and specifications, when supported by the source.
For example, on the **CrowdStrike Managed Hosts** source, you can filter the ingested data by **Asset Types** and/or specify the **CrowdStrike Cloud Region **to target the appropriate environment.
[See image.](#data-retrieval-filters)
- **Gateway**: (Optional) Select a gateway. To learn more, see [Configuring the Zsacler SecOps Platform Gateway](/uvm/configuring-zscaler-gateway).
[]![retrieval for crowdstrike managed hosts stream including filter and specification fields for the stream](/downloads/uvm/configure/sources/creating-data-sources/crowdstrike%20managed%20hosts.png)
[]In the **Scheduling** section, set the frequency and time at which the platform retrieves data from the vendor.
- **Full Refresh Frequency**: Set the frequency and time for ingesting the full dataset.
-
**Incremental Refresh Frequency**: (Optional) When supported by the source, set the frequency and time for ingesting new or updated data only.
Zscaler recommends enabling Auto Scheduling for all data sources to ensure that related data is ingested in sync, supporting more accurate data transformations. To learn more, see [Managing Data Sources](/uvm/managing-data-sources). If you choose to schedule the run at the individual source level, Zscaler recommends setting an incremental refresh to run once daily, supplemented by a full refresh weekly, to ensure that automatic remediation detection takes effect.
[See image.](#scheduling-form)
For streaming AnySource connectors, scheduling is not required. These sources push data to the platform in real time.
[]![c64c6cda-e053-4c93-815c-5c04bfae384a.jpg](/downloads/uvm/configure/sources/creating-new-data-source/c64c6cda-e053-4c93-815c-5c04bfae384a.jpg)
[]In the **Remediation Detection Settings** section, set when findings automatically turn undetected.
Automatic finding remediation detection runs on both full and incremental data ingestions. For incremental ingestions, it only evaluates and ages findings that are included in that specific run, and not all existing findings that were ingested in previous runs.
- **Aging Criteria**:
- **Built-in Rule**: Enable the built-in aging rule to set a finding as **Undetected** immediately if it was not seen in the latest full refresh, but the asset on which the finding was found was seen with other findings in the latest full data refresh.
-
**Custom Rule**: Build a custom aging rule to support use cases that aren't covered by the fallback and built-in criteria.
The aging criteria conditions apply to a specific data source (i.e., the asset must be seen on the same data source that the finding was not seen on).
- **Fallback**: Enable the fallback rule to set a finding as **Undetected **based on the number of days that have passed since it was last seen.
[]In the **Advanced Settings** > **Suppression Rules** section, define rules and conditions to exclude specific data or to include only a subset of the dataset before it enters the platform.
Zscaler recommends configuring suppression rules only after ingesting data from the source at least once, to ensure that you can reference the correct field names when creating the rules. To learn more, see [Configuring Suppressions Rules](/uvm/configuring-suppression-rules).
Your new data is retrieved on the next data run. To retrieve the data immediately, hover over the source and click the **Process Now** icon.
[See image.](#process-now)
[]![mceclip0.png](/downloads/uvm/configure/sources/creating-new-data-source/mceclip0.png)