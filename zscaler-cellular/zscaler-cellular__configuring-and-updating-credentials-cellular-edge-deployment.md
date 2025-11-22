# Configuring and Updating Credentials for Cellular Edge Deployment
Source: https://help.zscaler.com/zscaler-cellular/configuring-and-updating-credentials-cellular-edge-deployment
PDF: https://help.zscaler.com/pdf/com/en/1519071.pdf

Zscaler requires your organization's [Cloud & Branch Connector](/cloud-branch-connector) credentials to initiate deployment of Zscaler Cellular Edges across regions. You must set up Cloud & Branch Connector credentials to allow Zscaler to deploy Cellular Edges.
To configure Cloud & Branch Connector credentials:
If you change the super admin credentials of the Cloud & Branch Connector Admin Portal, then you must update the credentials on the Configuration page in the Zscaler Cellular Admin Portal. Failure to update credentials in the Zscaler Cellular Admin Portal can lead to service disruption, affecting connectivity of your cellular devices that use Zscaler SIMs.
- [Log in to the Cloud & Branch Connector Admin Portal](/cloud-branch-connector/accessing-navigating-zscaler-cloud-branch-connector-admin-portal#LoggingIn).
-
Go to **Administration **> **API Key** **Management**.
[See image.](#api-key-management)
- Copy the API Key and save it for future use. To learn more about Cloud & Branch Connector's API keys, see [About API Key Management](/cloud-branch-connector/about-api-key-management)
- [Log in to the Zscaler Cellular Admin Portal via ZIdentity](/zscaler-cellular/accessing-and-navigating-zscaler-cellular-admin-portal#signing-in-to-the-portal).
- In the left-side navigation, click **Configuration**.
-
On the **Configuration **page:
- **Branch Connector Username**: Enter the username of the super admin for the Cloud & Branch Connector Admin Portal.
- **Branch Connector Password**: Enter the password of the super admin for the Cloud & Branch Connector Admin Portal.
- **Branch Connector API Key**: Enter the API key obtained from the Cloud & Branch Connector Admin Portal in a previous step.
[See image.](#configuration-page)
- Click **Save**.
[]![Obtaining API key from the Cloud & Branch Connector Admin Portal](/downloads/zscaler-cellular/dashboard-deployment-and-configuration/configuring-and-updating-credentials-cellular-edge-deployment/zscaler-cellular-api-key-management.png)
[]![Updating the Branch Connector credentials](/downloads/zscaler-cellular/dashboard-deployment-and-configuration/configuring-and-updating-credentials-cellular-edge-deployment/cellular-edge-the-configuration-page.png)