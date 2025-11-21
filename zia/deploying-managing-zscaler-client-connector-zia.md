# Deploying and Managing Zscaler Client Connector for ZIA
Source: https://help.zscaler.com/zia/deploying-managing-zscaler-client-connector-zia
PDF: https://help.zscaler.com/pdf/com/en/1401761.pdf

To properly deploy and manage Zscaler Client Connector  for the ZIA service, you must complete the following tasks in the ZIA Admin Portal and Zscaler Client Connector Portal.
- [Step 1: Manage Admin Access to the Zscaler Client Connector Portal](#manage-admin-access)
- [Step 2: Provision and Authenticate Users](#provision-authenticate-users)
Optionally, you can complete the following tasks when deploying or managing Zscaler Client Connector for ZIA:
- [Configure SSL Inspection](#configure-SSL)
- [Create Groups](#create-groups)
- [Create and Host PAC Files](#create-host-PAC-files)
[]You must manage admin access to the Zscaler Client Connector Portal in the ZIA Admin Portal. To learn more, see [Managing Admin Access to the Zscaler Client Connector Portal](/z-app/managing-admin-access-zscaler-app-portal).
[]To use the Zscaler service, you must have an authentication mechanism configured and users provisioned on the ZIA service. To learn more, see [About Provisioning and Authenticating Users](/zia/about-provisioning-authenticating-users).
If you do not have an authentication mechanism installed, you must use the Zscaler Client Connector Portal as your [Identity Provider (IdP)](/zia/about-identity-providers) to provision and authenticate users. One of the tasks you must complete to use the Zscaler Client Connector Portal as an IdP is [adding it as an IdP](/zia/adding-zscaler-client-connector-portal-idp) in the ZIA Admin Portal. To learn more, [Using the Zscaler Client Connector Portal as an Identity Provider](/z-app/using-zscaler-app-portal-identity-provider).
[]In order to enable [SSL Inspection](/zia/about-ssl-inspection) for Zscaler Client Connector, you must first enable the feature in the ZIA Admin Portal for each relevant platform. To learn more, see [Configuring SSL Inspection for Zscaler Client Connector](/z-app/configuring-ssl-inspection-zscaler-app).
[]For Zscaler Client Connector, you can apply certain policies or settings to specific [groups](/zia/about-groups). You must first create groups in the ZIA Admin Portal, and then ensure that the ZIA Admin Portal syncs these groups with the Zscaler Client Connector Portal. To learn more, see [Syncing Directory Groups between the ZIA Admin Portal and Zscaler Client Connector Portal](/z-app/syncing-directory-groups-between-zscaler-admin-portal-and-app-portal).
[]You can use PAC files in the [Zscaler Client Connector profiles](/z-app/about-zscaler-app-profiles) and [forwarding profiles](/z-app/about-forwarding-profiles) to determine how to direct your organization’s traffic.
To create custom PAC files for these profiles, Zscaler highly recommends that you use the ZIA Admin Portal default PAC file and customize it as necessary. Once you create a custom PAC file, you can [host it in the ZIA Admin Portal](/zia/about-hosted-pac-files).
To learn more, see [Best Practices for Using PAC Files with Zscaler Client Connector](/z-app/best-practices-using-pac-files-zscaler-app) and [Writing a PAC File](/zia/writing-pac-file).