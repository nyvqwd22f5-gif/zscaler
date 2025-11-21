# Adding or Deleting a Scanner Integration
Source: https://help.zscaler.com/dspm/adding-on-premises-scanner-integration
PDF: https://help.zscaler.com/pdf/com/en/1532040.pdf

You can add or delete a scanner integration when required.
You cannot edit the scanner details but you can:
- Regenerate the API key to renew it.
- Download the scanner image to reinstall or redeploy the scanner.
To learn more, see [About On-Premises Scanner Integrations](/dspm/about-premises-scanner-integrations).
Adding a Scanner Integration
To add a scanner integration:
- Go to **Administration** > **Configuration** > **On-Premises Scanners**.
-
On the **On-Premises Scanner Integrations** page, click **Add Scanner Integration**.
[See image.](#add-button)
The **Add On-Premises Scanner Integration** drawer appears.
-
In the **Add On-Premises Scanner Integration** drawer:
-
**Integration Name**: Enter a name for the scanner integration.
The integration name cannot be modified after it is saved.
-
Click **Save**.
[See image.](#name-save)
-
In the **API Key Management** section, click **Generate Key**.
[See image.](#generate-key)
The API key is generated and displayed.
API keys are not recoverable. Store the key securely during scanner installation. Regenerating the key invalidates all existing scanners using the current key.
- In the **Scanner Image Download** section:
- **Select the Virtualization Platform**: Select the platform on which the DSPM scanner image must be downloaded (i.e., **VMware** or **Hyper-V**).
- Click **Download Scanner Image **to download the DSPM scanner image in OVA format for **VMware**, or VHD format for **Hyper-V**.
- Use the **Checksum** value to verify the integrity of the downloaded image during the scanner configuration.
[See image.](#add)
Use the downloaded scanner image to configure your scanner and complete the integration. For more details, refer to your scanner installation documentation.
[]![On-Premises Scanner Integrations page with Add Scanner Integration button.](/downloads/dspm/administration/premise-scanners/adding-premises-scanner-integration/ds-scanner-add-button.png)
[]![On-Premises Scanner Integration drawer showing scanner name field with Save button annotated.](/downloads/dspm/administration/premise-scanners/adding-premises-scanner-integration/ds-scanner-addscanner-name.png)
[]![On-Premises Scanner Integration drawer with an annotation for Generate Key button.](/downloads/dspm/administration/premise-scanners/adding-premises-scanner-integration/ds-scannerkey-button.png)
[]![On-Premises Scanner Integration drawer with the details filled.](/downloads/dspm/administration/premise-scanners/adding-premises-scanner-integration/ds-scanneradd.png)
[]Deleting an On-Premises Scanner Integration
To delete a scanner integration:
- Go to **Administration** > **Configuration** > **On-Premises Scanners**.
- The **On-Premises Scanner Integrations** page, do one of the following:
-
Click the **Delete **icon (![fa-delete.png](/downloads/dspm/administration/premise-scanners/adding-premises-scanner-integration/fa-delete.png)
)** **for the required scanner integration.
[See image.](#delete-button)
-
Click the name of the scanner integration to view the [scanner integration](/dspm/about-premises-scanner-integrations) details, and click the **Delete** icon (![fa-delete.png](/downloads/dspm/administration/premise-scanners/adding-premises-scanner-integration/fa-delete.png)
).
[See image.](#details-delete)
-
In the **Delete On-Premises Scanner** window, read the message, and then enter `CONFIRM` in the text box.
[See image.](#confirm-delete)
- Click **Delete On-Premises Scanner**.
The scanner integration is deleted from the DSPM Admin Portal.
[]![On-Premises Scanner Integration page with an annotation highlighting the Delete option.](/downloads/dspm/administration/premise-scanners/adding-premises-scanner-integration/ds-scanner-delete-button.png)
[]![Scanner integration details page with an annotation for Delete option](/downloads/dspm/administration/premise-scanners/adding-premises-scanner-integration/ds-scanner-details-deletebutton.png)
[]![Confirmation window for deleting a scanner integration, with an input field to confirm to proceed.](/downloads/dspm/administration/premise-scanners/adding-premises-scanner-integration/ds-scanner-delete.png)