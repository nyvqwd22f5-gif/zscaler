# Configuring and Managing Web Server Banners
Source: https://help.zscaler.com/deception/configuring-and-managing-web-server-banners
PDF: https://help.zscaler.com/pdf/com/en/1531543.pdf

Web server banners are metadata about the service running on a web server. Typically, the web server banner is used in the server response header when an attacker connects to the web server. You can associate the web server banners with network decoys that have web service enabled. Zscaler Deception provides a list of reconfigured web server banners that can lure attackers when used with network decoys. You can also create custom web server banners that can lure attackers based on your business requirements. To learn how to use web server banners in network decoys, see [Configuring Services on a Network Decoy](/deception/configuring-services-network-decoy#configuring-web-service).
Creating a Web Server Banner
To create a web server banner:
- Go to **Miragemaker **> **Miscellaneous **> **Web Server Banners**.
-
Click **Add Web Server Banner**.
[See image.](#zd-wsb-banner-add-button)
-
In the **Web Server Banner Details **window, enter the **Name **that will be used as the web server banner message.
[See image.](#zd-wsb-banner-add)
- Click **Submit**.
Editing a Web Server Banner
To edit a web server banner:
- Go to **Miragemaker **> **Miscellaneous **> **Web Server Banners**.
- Locate the web server banner that you want to edit, and click the **Edit **icon.
-
Modify the **Name **field as required.
[See image.](#zd-wsb-banner-edit)
- Click **Submit.**
Default web server banners cannot be edited.
**Deleting a Web Server Banner**
To delete a web server banner:
- Go to **Miragemaker **> **Miscellaneous **> **Web Server Banners**.
-
Locate the web server banner that you want to delete, and click the **Delete **icon.
[See image.](#zd-wsb-banner-delete)
- In the confirmation window, click **OK**.
Default web server banners cannot be deleted.
[]![A screenshot capturing the option to add Web Server banner](/downloads/deception/miragemaker/miscellaneous/configuring-and-managing-web-server-banners/zscaler-deception-wsb-add-button.png)
[]![A screenshot capturing Web Server Banner Details window](/downloads/deception/miragemaker/miscellaneous/configuring-and-managing-web-server-banners/zscaler-deception-wsb-configuration.png)
[]![A screenshot capturing the edit Web Server Banner option](/downloads/deception/miragemaker/miscellaneous/configuring-and-managing-web-server-banners/zscaler-deception-wsb-edit-option.png)
[]![A screenshot capturing the delete Web Server Banner option](/downloads/deception/miragemaker/miscellaneous/configuring-and-managing-web-server-banners/zscaler-deception-wsb-delete-option.png)