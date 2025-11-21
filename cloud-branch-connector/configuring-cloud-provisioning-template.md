# Configuring a Cloud Provisioning Template
Source: https://help.zscaler.com/unified/configuring-cloud-provisioning-template
PDF: https://help.zscaler.com/pdf/com/en/1518566.pdf

This article provides information on how to configure a [cloud provisioning template](/unified/about-cloud-provisioning-templates) to create a cloud provisioning URL within the Admin Portal. This URL is used for deploying Cloud Connector as a virtual machine (VM) in Amazon Web Services (AWS), Microsoft Azure, and Google Cloud Platform (GCP). To learn more, see [Deploying Zscaler Cloud Connector with Amazon Web Services](/unified/deploying-zscaler-cloud-connector-amazon-web-services), [Deploying Zscaler Cloud Connector with Microsoft Azure](/unified/deploying-zscaler-cloud-connector-microsoft-azure), and [Deploying Zscaler Cloud Connector on the Google Cloud Platform](/unified/deploying-zscaler-cloud-connector-google-cloud-platform).
To add a Cloud Connector Provisioning Template:
- Go to **Infrastructure **> **Connectors **> **Cloud **> **Provisioning**.
- Click **Add Cloud Connector Provisioning Template**.
- On the **Add Cloud Connector Provisioning Template** page:
- On the **General Information** tab:
- **Name**: Enter a name for your provisioning template.
-
**Description**: (Optional) Enter additional information about the provisioning template.
[See image.](#general-information)
-
On the **Cloud Provider** tab, select **Amazon Web Services**, **Azure**, or **Google Cloud** as the cloud provider for which you want to deploy the Cloud Connector.
[See image.](#cloud-provider)
- On the **Location** tab:
- **Location Creation**: This field is set to **Automatic**.
-
**Location Template**: Select a location template from the drop-down menu based on your requirements. To learn more, see [About Location Templates](/cloud-branch-connector/about-location-templates).
[See image.](#location)
- On the **Group Information** tab:
- **Cloud Connector Group Creation**: This field is set to **Automatic**.
- **VM Size**: Depending on your selected cloud provider, you can configure your Cloud Connector VM size.
- **Amazon Web Services**: Select from **Small**, **Medium**, or **Large**. **Small** is set by default when auto scaling is enabled.
- **Azure**: **Small** is set by default.
- **GCP**: **Small** is set by default.
-
**Auto Scaling**: Enable or disable Auto Scaling for AWS or Azure. Zscaler does not support Auto Scaling for GCP.
In the AWS Marketplace, Auto Scaling is referred to as Auto Scaling. In the Azure Marketplace, Auto Scaling is referred to as Virtual Machine Scale Sets (VMSS). In the Admin Portal, references to Auto Scaling also refer to VMSS. To enable Auto Scaling or VMSS, contact Zscaler Support.
[See image.](#group-information)
-
On the **Review** tab, review the values and settings entered.
[See image.](#review-tab)
- Click **Save**. A cloud provisioning URL is created.
![The General Information tab on the Add Cloud Provisioning Template page](/downloads/cloud-branch-connector/administration/provisioning-configuration/configuring-cloud-provisioning-template/CCProvis%20General%20Info.png)
[]
![The Cloud Provider tab on the Add Cloud Provisioning Template page](/downloads/cloud-branch-connector/administration/provisioning-configuration/configuring-cloud-provisioning-template/CCProvis%20Cloud%20Providewr.png)
[]
![The Location tab on the Add Cloud Provisioning Template page](/downloads/cloud-branch-connector/administration/provisioning-configuration/configuring-cloud-provisioning-template/ccprovis%20location.png)
[]
![The Group Information tab on the Add Cloud Provisioning Template page](/downloads/cloud-branch-connector/administration/provisioning-configuration/configuring-cloud-provisioning-template/CCProvis%20Group%20Info.png)
[]
![The Review tab on the Add Cloud Provisioning Template page](/downloads/cloud-branch-connector/administration/provisioning-configuration/configuring-cloud-provisioning-template/CC%20Provis%20Review.png)
[]