# Integrating with Azure Blob Storage
Source: https://help.zscaler.com/dspm/integrating-azure-blob-storage
PDF: https://help.zscaler.com/pdf/com/en/1487536.pdf

You can integrate DSPM with your Azure Blob Storage. This integration enables DSPM to send the alert data logs of your cloud resources to the Azure Blob Storage containers for storage and data analysis by third-party SIEM or ITSM tools.
Only [users with admin roles](/dspm/predefined-roles-and-permissions) can configure a cloud storage integration.
Integrating with Azure Blob Storage
To configure the Azure Blob Storage integration:
- Go to **Administration **>** Integrations**.
-
On the **Integrations** page, click **Add**.
[See image.](#ds-addbutton)
-
On the **Add Integration** page:
- For **Integration Name**, enter a unique name.
- For **Cloud Storage**, select **Azure Blob Storage**.
[See image.](#ds-azureselect)
- Click **Next**.
-
Under **Cloud Storage**, complete the following steps to provide DSPM with write permissions on Azure Blob Storage.
[See image.](#ds-blobdetails)
- [Copy the connection string from the Azure portal.](#ds-azuresteps)
- For **Azure Storage Account Connection String**, paste the connection string you copied from the Azure portal.
- (Optional) **Container Location**: Enter the location of the storage container. It is mandatory to first create a folder in your Azure Blob Storage and then add the name.
- Click **Test Connection** to verify the connection between DSPM and the Azure Blob Storage. A message is displayed indicating the connection is verified.
- Click **Next**.
-
Review the integration summary. Click the **Edit** icon if you want to make any changes.
[See image.](#ds-ab-review)
- Click **Finish**.
You can see the integration details on the **Integrations** page. The initial status is shown as Pending because data is not yet sent to the Azure Blob Storage. You must configure and associate the [alert rules](/dspm/about-alerts) with this integration for DSPM to be able to send the data logs. When DSPM sends the data logs to the Blob Storage, then the status changes to Success.
- []Log in to the [Azure portal](https://portal.azure.com/).
- Go to your storage account.
- Under **Security **>** Networking**, select **Access Key**.
- Click **Show Keys** to view your access keys and connection strings. A connection string includes the authorization information required for DSPM to access data in your Azure Storage account. To learn more, refer to the [Azure Blob Storage documentation](https://docs.microsoft.com/en-us/azure/storage/common/storage-account-keys-manage?tabs=azure-portal).
- Copy the entire connection string for the relevant access key.
[]![Select the cloud storage](/downloads/dspm/third-party-integrations/cloud-storage-services/integrating-azure-blob-storage/ds-azureblob-select.png)
[]![Add an Azure Blob integration](/downloads/dspm/third-party-integrations/cloud-storage-services/integrating-azure-blob-storage/ds-azure-addbutton.png)
[]![Configure the Azure Blob storage](/downloads/dspm/third-party-integrations/cloud-storage-services/integrating-azure-blob-storage/ds-azure-addcsdetails.png)
[]![Review the integration](/downloads/dspm/third-party-integrations/cloud-storage-services/integrating-azure-blob-storage/ds-blob-summary.png)