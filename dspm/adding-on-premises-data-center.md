# Adding an On-Premises Data Center
Source: https://help.zscaler.com/dspm/adding-on-premises-data-center
PDF: https://help.zscaler.com/pdf/com/en/1526566.pdf

You can add [on-premises data centers](/dspm/about-data-center) to DSPM to scan for sensitive data and posture risks.
Prerequisites
Make sure the following prerequisites are met:
- [Onboard the account using a custom model](/dspm/onboarding-microsoft-azure-tenant#SelectNetworkConfiguration) to establish network connectivity to the on-premises data center.
- Modify security groups to allow connections from the scanner or orchestrator subnets.
- Create a [custom role with required permissions to configure SQL authentication.](/dspm/configuring-sql-authentication-unmanaged-databases)
- Provide SQL connection strings and authentication credentials for our solution to access the on-premises data centers.
Adding On-Premises Data Center
To add an on-premises data center:
- Go to **Administration **>** Configuration **>** On-Premises Data Centers**.
-
On the **On-Premises Data Centers** page, click **Add Data Center**.
[See image.](#img_add)
-
In the **Add New On-Premises Data Center** drawer:
- [Data Center](#datacenter)
- [Associate Scanners to the Data Center](#association)
[See image.](#img-add-detail)
-
Click **Save**.
The **Add Data Center** window appears.
-
In the **Add Data Center** window, click **Confirm and Save**.
[See image.](#img-ds-admin-onprem-add-dc-confirm)
The on-premises data center is added and displayed on the [On-Premises Data Centers](/dspm/about-data-center) page.
To configure scan settings to scan the sensitive data in the on-premises data center, see [Configuring Scan Settings for On-Premises Data Center](/dspm/configuring-scan-settings-premise-unmanaged-database).
[]You must associate at least one scanner with the data center:
- [Associate Cloud Scanners for On-Premises Unmanaged Database](#cloud-scanners)
- [Associate On-Premise Scanners for File Servers](#on-premises-scanners)
[]
- **Select On-Premises Scanner Integration**: Select an existing [on-premises scanner integration](/dspm/about-premises-scanner-integrations) to associate with the data center.
[]
- **Association Name**: Enter a unique name for the cloud network association.
- **Connected Cloud**: Select the cloud service provider where your data center is associated.
- **DSPM Alias**: Select the DSPM alias for the selected cloud.
-
**Connected Cloud Region**: Select the region where the cloud is hosted.
Click the **+ Add** button to configure multiple cloud network associations for the data center.
- []**Data Center Name**: Enter a unique name for the on-premises data center.
- **Location**: Search for and select the region where the data center is located.
- **Business Unit**: Assign the [business unit](/dspm/about-business-units) to the data center.
[]![Add Data Center confirmation window for data centers with an annotation around Confirm and Save button.](/downloads/dspm/administration/on-premise-data-center/add-data-center/ds-admin-on-prem-add-confirm.png)
[]![Add New On-Premises Data Center with required fields to add a data center.](/downloads/dspm/administration/on-premise-data-center/add-data-center/ds-on-prem-dc-add-detail.png)
[]![On-Premises Data Centers page with an annotation around the Add Data Center button.](/downloads/dspm/administration/on-premise-data-center/add-data-center/ds-admin-on-prem-add.png)