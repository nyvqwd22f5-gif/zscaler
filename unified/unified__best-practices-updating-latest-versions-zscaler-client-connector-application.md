# Best Practices for Updating Latest Versions of Zscaler Client Connector Application
Source: https://help.zscaler.com/unified/best-practices-updating-latest-versions-zscaler-client-connector-application
PDF: https://help.zscaler.com/pdf/com/en/1492356.pdf

Before deploying the latest version of Zscaler Client Connector to all the user groups in your organization, Zscaler recommends you first test the latest versions of the app on specific user groups (e.g., Early Adopter user group), before deploying it to all your user groups. By doing this, you can prevent auto-updates and control deployment of the app to your organization's user groups.
Be advised during the update of Zscaler Client Connector, established client connections might be affected. Clients might need to re-establish their connections after the update.
To create a test group to automatically deploy the latest version of Zscaler Client Connector to specific user groups for testing purposes:
- [Go to the Admin Portal and create a user group for which you want to deploy the latest version of Zscaler Client Connector.](/unified/adding-user-groups)
- [Sync the directory groups between Internet & SaaS and Zscaler Client Connector](/unified/syncing-directory-groups-between-internet-saas-and-zscaler-client-connector)
- [Configure the update settings for Zscaler Client Connector](/unified/configuring-app-update-zscaler-client-connector-app-store)
Ensure that the version to install is set to **Latest** for the user group that you created for testing. For the other user groups in your organization, set a specific Zscaler Client Connector version based on your requirements.
For successful deployment of Zscaler Client Connector, see [Best Practices for Zscaler Client Connector Deployment](/unified/best-practices-zscaler-client-connector-deployment).