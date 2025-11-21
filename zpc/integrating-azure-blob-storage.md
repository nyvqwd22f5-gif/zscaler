# Integrating with Azure Blob Storage
Source: https://help.zscaler.com/zpc/integrating-azure-blob-storage
PDF: https://help.zscaler.com/pdf/com/en/1395681.pdf

You can integrate ZPC with your Azure Blob Storage. This integration enables ZPC to send the alert data logs of your cloud assets to the Azure Blob Storage containers for storage and data analysis by third-party SIEM tools. To learn more, see [Integrating Cloud Storage with Splunk](/zpc/integrating-cloud-storage-splunk).
Only ZPC Administrators can configure a cloud storage integration. To learn more, see [About Administrators](/zpc/about-administrators).
Integrating with Azure Blob Storage
To configure the Azure Blob Storage integration:
- Go to **Administration **>** Integrations**.
-
On the **Integrations** page, click **Add**.
[See image.](#zpc-addbutton)
-
On the **Add Integration** page:
- For **Integration Name**, enter a unique name.
- For **Cloud Storage**, select **Azure Blob Storage**.
[See image.](#zpc-selectablob)
- Click **Next**.
-
Under **Cloud Storage**, complete the following steps to set up the Azure Blob permissions.
- Log in to the [Azure portal](https://portal.azure.com/).
- Go to your storage account.
- Under **Security **>** Networking**, select **Access Key**.
- Click **Show Keys** to view your access keys and connection strings.
A connection string includes the authorization information required for ZPC to access data in your Azure Storage account. To learn more, see the [Azure Blob Storage Documentation](https://docs.microsoft.com/en-us/azure/storage/common/storage-account-keys-manage?tabs=azure-portal).
- Copy the entire connection string for the relevant key.
- For **Azure Storage Connection String**, paste the connection string value you copied in step e.
-
(Optional) Enter a folder name for the **Container Location**. It is mandatory to first create a folder in your Azure Blob Storage and then add the name.
[See image.](#zpc-permissions)
- Click **Next**.
-
Review the integration summary. Click the **Edit** icon if you want to make any changes.
[See image.](#zpc-review)
- Click **Finish**.
You can see the integration details on the **Integrations** page. The initial status is shown as **Pending** because data is not yet sent to the Azure Blob Storage. You must configure and associate the [alert rules](/zpc/understanding-alert-rules) with this integration for ZPC to be able to send the data logs. Once ZPC sends the data logs to the Blob Storage, then the status changes to **Success**. [See image.](#zpc-intstatus)
[]![Add a cloud storage integration](/downloads/zpc/third-party-integrations/cloud-storage-integrations/integrating-azure-blob-storage/zpc-integration-page.png)
[]![Select Azure cloud storage](/downloads/zpc/administration/integrations/cloud-storage-integrations/integrating-azure-blob-storage/zpc-add-integ-azure.png)
[]![Set up permissions to access Azure blob storage](/downloads/zpc/administration/integrations/cloud-storage-integrations/integrating-azure-blob-storage/zpc-integ-azure-storage.png?1652434958)
[]![Review the details on the Summary page](/downloads/zpc/administration/integrations/cloud-storage-integrations/integrating-azure-blob-storage/zpc-integ-azure-summary.png)
[]![Status shown on the Integrations page](/downloads/zpc/administration/integrations/cloud-storage-integrations/integrating-amazon-s3/zpc-integ-status.png)