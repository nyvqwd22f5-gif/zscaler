# Identifying the Zscaler Cloud Connector Version
Source: https://help.zscaler.com/cloud-branch-connector/identifying-zscaler-cloud-connector-version
PDF: https://help.zscaler.com/pdf/com/en/1446981.pdf

Zscaler provides automation templates for Amazon Web Services (AWS) and Microsoft Azure. When Zscaler Cloud Connector is deployed, these templates always detect the latest virtual machine (VM) version. Therefore, as long as the latest automation templates are deployed, there is no action required when deploying new VMs. You can locate your current Cloud Connector VM version via AWS and Azure.
Cloud Connector Version Location in AWS
To find the current Cloud Connector version in AWS:
- In the [AWS Marketplace](https://aws.amazon.com/marketplace/server/configuration?productId=2bc022b8-5d8c-4e13-aadb-ef3483e607fe), on the **Configure this software** page, locate all current and historical marketplace OS/VM versions and corresponding Amazon Machine Images (AMIs) per region to reference after locating your current Cloud Connector version.
[See image.](#CCVersionAWSStep1-2)
[]![Software version and AMI Id in the AWS Marketplace](/downloads/cloud-connector/deployment-management/identifying-zscaler-cloud-connector-version/CC%20Version%20AWS%20Step%201-2.jpg)
The latest AMI is listed in the table below and the corresponding AMI in region US West (Oregon) is ami-0c0f8d637a04769ea.
- Sign in to the [AWS console](https://zscc-account.signin.aws.amazon.com/console).
- In the **Search** bar, enter `EC2`. Then, under **Services**, select **EC2**.
[See image.](#CCVersionAWSStep1)
[]![Selecting EC2 from the AWS Console Search Bar](/downloads/cloud-connector/deployment-management/identifying-cloud-connector-version/CC%20Version%20AWS%20Step%201.jpg)
- On the **EC2 Dashboard** page, under **Resources**, select **Instances**. Alternatively, you can select **Instances** from the left-side navigation.
[See image.](#CCVersionAWSStep3)
[]![Selecting Instances under Resources or from the left-side navigation in the AWS Console](/downloads/cloud-connector/deployment-management/identifying-cloud-connector-version/CC%20Version%20AWS%20Step%203.jpg)
Selecting **Instances (running)** only shows currently deployed Cloud Connectors. Select **Instances (running)** only if you are searching for the version of a currently deployed Cloud Connector.
- On the **Instances** page, select the Instance ID of your Cloud Connector.
[See image.](#CCVersionAWSStep4)
[]![Selecting your Instance ID from the Instances page of the AWS Console](/downloads/cloud-connector/deployment-management/identifying-cloud-connector-version/CC%20Version%20AWS%20Step%204.jpg)
- On the **Instance summary** page, select **Details**.
[See image.](#CCVersionAWSStep5)
[]![Selecting Details from the Instance Summary page of the AWS Console](/downloads/cloud-connector/deployment-management/identifying-zscaler-cloud-connector-version/CC%20Version%20AWS%20Step%205-2.jpg)
- On the **Details** tab, under **Instance details**, your Cloud Connector version information is displayed in **AMI ID** and **AMI name**.
[See image.](#CCVersionAWSStep6)
[]![Locating your AMI ID and AMI Name to Identify your Cloud Connector Version in the AWS Console](/downloads/cloud-connector/deployment-management/identifying-zscaler-cloud-connector-version/CC%20Version%20AWS%20Step%206-3.jpg)
The following table displays information on AWS AMI releases.
| **Release Date** | **Software Version** |
| ---------------- | -------------------- |
| January 19, 2023 | ZS6.1.24.6 |
| October 19, 2023 | ZS6.1.26.0 |
| November 14, 2023 | ZS6.1.26.1 |
A change in network interfaces occurred between releases. In version ZS6.1.24.6, device index 0 is the management interface and device index 1 is the service interface. In version ZS6.1.26.0, device index 0 is the service interface and device index 1 is the management interface.
Cloud Connector Version Location in Azure
To find the current Cloud Connector version in Azure:
- Sign in to the [Azure portal](https://portal.azure.com/).
- In the upper-right corner of the portal, click the **Cloud Shell** icon.
[See image.](#CCVersionAzureStep2)
[]![Selecting the Cloud Shell icon in Microsoft Azure](/downloads/cloud-connector/deployment-management/identifying-zscaler-cloud-connector-version/CC%20Version%20Azure%20Step%202.jpg)
- From the drop-down menu in the Cloud Shell window, select **PowerShell**.
[See image.](#CCVersionAzureStep3)
[]![Selecting PowerShell from the dropdown menu of Cloud Shell in Microsoft Azure](/downloads/cloud-connector/deployment-management/identifying-zscaler-cloud-connector-version/CC%20Version%20Azure%20Step%203.jpg)
- Enter the following command:
`az vm image show --urn zscaler1579058425289:zia_cloud_connector:zs_ser_gen1_cc_01:latest`
[See image.](#CCVersionAzureStep4)
[]![Entering the command into PowerShell in Microsoft Azure](/downloads/cloud-connector/deployment-management/identifying-zscaler-cloud-connector-version/CC%20Version%20Azure%20Step%204.jpg)
- The current Cloud Connector version is displayed.
[See image.](#CCVersionAzureStep5)
[]![Viewing your Cloud Connector version in Microsoft Azure Cloud Shell](/downloads/cloud-connector/deployment-management/identifying-zscaler-cloud-connector-version/CC%20Version%20Azure%20Step%205.jpg)
- Additionally, on the `az vm list -g "resource group name" | grep -A 9 imageReference` line, ensure the `exactVersion` for the currently deployed Cloud Connector appliance matches the previous latest version.