# Connecting an Entra ID Tenant with the Zscaler ITDR Admin Portal
Source: https://help.zscaler.com/itdr/connecting-entra-id-tenant-zscaler-itdr-admin-portal
PDF: https://help.zscaler.com/pdf/com/en/1531778.pdf

You can connect an Entra ID tenant with the Zscaler ITDR Admin Portal to run posture scans and monitor change detections. Establishing a connection with Entra ID and running scans requires deployment of additional resources on the Azure cloud. Zscaler ITDR relies on a deployment script to create these resources.
Prerequisites
Before connecting an Entra ID tenant with the ITDR Admin Portal, ensure that you have:
- An Entra ID account with a Global Administrator role.
- Obtained Entra ID's Tenant ID, Subscription ID, and Region.
- Obtained the necessary PowerShell command to run the deployment script using one of the following methods:
- [Automated Download Method](/itdr/obtaining-deployment-script-azure#zd-direct-download-script)
- [Manual Download Method](/itdr/obtaining-deployment-script-azure#zd-manual-download-script)
Connecting an Entra ID Tenant with the ITDR Admin Portal
Follow these steps to connect an Entra ID tenant with the ITDR Admin Portal:
- [Step 1: Add Tenant Details in the ITDR Admin Portal](#adding-tenant-itdr)
- [Step 2: Deploy Scanning Resources in the Azure Portal](#deploy-resources-in-azure)
[]To add an Entra ID tenant to the ITDR Admin Portal:
- Go to **ITDR **> **Manage **> **Entra ID**.
-
Click **Add Tenant**.
[See image.](#add-tenant-button)
The **Tenant Details **window appears.
-
In the **Tenant Details **window:
- **Tenant ID**: Enter the tenant ID of the Entra ID tenant obtained from the Azure Portal.
- **Subscription ID**: Enter the subscription ID of the Entra ID tenant obtained from the Azure Portal.
- **Region**: Select the region to which the Entra ID tenant belongs from the drop-down menu.
- **Scan Frequency**: Select a preferred frequency at which the posture scans must run for the Entra ID tenant.
- **Scan Time**: Select a time of the day when the posture scan must start.
- **Scan Timeout**: Enter a time value (in minutes) for the posture scan to time out.
[See image.](#tenant-details-window-fill)
- Click **Save**.
[]To deploy scanning resources in the Azure Portal:
- Sign in to the [Azure Portal](http://https//portal.azure.com) as a Global Administrator.
-
Launch Cloud Shell by clicking the **Cloud Shell **icon on the top navigation bar.
[See image.](#cloud-shell-icon-azure-portal)
The **Cloud Shell** window appears.
-
In the **Cloud Shell **window:
- Set your shell environment to PowerShell.
- Run the deployment script using the command obtained via the [automated download method](/itdr/obtaining-deployment-script-azure#zd-direct-download-script) or [manual download method](/itdr/obtaining-deployment-script-azure#zd-manual-download-script).
- Enter the option to deploy resources and press `Enter`.
[See image.](#cloud-shell)
After resources are deployed, a prompt appears to grant read access to subscriptions. Three options are available for confirming subscription access:
- **Yes to all**: Grants read access to every subscription.
- **No to all**: Denies read access for all subscriptions.
- **Confirm for each**: Grant or deny access to each subscription individually.
If no option is selected, **No to all** is selected by default and can be changed later.
[See image](#Grant_reader_access)
Zscaler recommends adding remediation action permissions during the initial deployment. Skip this step if you do not want to perform remediations.
[See image.](#install_remediation_action_permissions)
The certificates generated for app registration are configured with one year validity for security reasons. If the certificate is expired, enter `3` and press `Enter` to renew the certificate.
[See image.](#powershell-syncsecrets)
-
Go to **App Registrations > All Applications**, locate and click the name of the application that is deployed for ITDR.
[See image.](#app-regsitration-entra-id)
-
On the application page, go to **Manage **> **API permissions**.
[See image.](#api-permissions-entra-id)
-
Click **Grant admin consent for <ITDR application name>**.
[See image.](#grant-admin-consent-button)
-
In the** Grant admin consent confirmation** window, click **Yes**.
[See image.](#grant-admin-consent-pop-up)
The required API permissions are granted for ITDR.
[See image.](#all-permissions-granted)
Due to enhancements and updates, the permissions required for connecting an Entra ID tenant might change. In such scenarios, run the deployment script again by appending the following additional options appended to the command:
`Update-AppRegistrationPermissions -Id <ITDRAppID>``
[]
![The Add Tenant button](/downloads/itdr/scan-configuration/entra-id-posture-scan/connecting-entra-id-tenant-zscaler-itdr-admin-portal/itdr-entra-ID-add-tenant.png)
[]
![The Tenant Details window](/downloads/itdr/scan-configuration/entra-id-posture-scan/connecting-entra-id-tenant-zscaler-itdr-admin-portal/Tenant%20Details.png)
[]
![The Cloud Shell option in Azure](/downloads/itdr/scan-configuration/entra-id-posture-scan/connecting-entra-id-tenant-zscaler-itdr-admin-portal/zscaler-deception-azure-powershell-launch%20(1).png)
[]
![View options to deploy resources in Azure Cloud Shell](/downloads/itdr/scan-configuration/entra-id-posture-scan/connecting-entra-id-tenant-zscaler-itdr-admin-portal/itdr-azure-cloud-shell.png)
[]
![View option to install remediation action permissions in Azure Cloud Shell](/downloads/itdr/scan-configuration/entra-id-posture-scan/connecting-entra-id-tenant-zscaler-itdr-admin-portal/itdr-azure-cloud-shell-remediation-permissions.png)
![Image]()
[]![The App Registration Page in Entra ID with the Zscaler ITDR app](/downloads/itdr/scan-configuration/entra-id-posture-scan/connecting-entra-id-tenant-zscaler-itdr-admin-portal/itdr-app-aregsiration-entra-id.png)
[]![The API Permissions option in Entra ID](/downloads/itdr/scan-configuration/entra-id-posture-scan/connecting-entra-id-tenant-zscaler-itdr-admin-portal/itdr-api-permissions.png)
[]![The Grant Admin consent option](/downloads/itdr/scan-configuration/entra-id-posture-scan/connecting-entra-id-tenant-zscaler-itdr-admin-portal/zscaler-deception-grant-button.png)
[]![The Admin Consent confirmation window](/downloads/itdr/scan-configuration/entra-id-posture-scan/connecting-entra-id-tenant-zscaler-itdr-admin-portal/zscaler-deception-grant-yes.png)
[]![API Permissions in Azure Portal](/downloads/itdr/scan-configuration/entra-id-posture-scan/connecting-entra-id-tenant-zscaler-itdr-admin-portal/zscaler-deception-granted.png)
[]![The PowerShell section with the ITDR deployment scripts](/downloads/itdr/scan-configuration/entra-id-posture-scan/connecting-entra-id-tenant-zscaler-itdr-admin-portal/itdr-sync-secrets.png)
[]![Options for reader access to subscriptions](/downloads/itdr/scan-configuration/entra-id-posture-scan/connecting-entra-id-tenant-zscaler-itdr-admin-portal/grant%20access_0.png)