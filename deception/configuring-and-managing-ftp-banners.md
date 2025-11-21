# Configuring and Managing FTP Banners
Source: https://help.zscaler.com/deception/configuring-and-managing-ftp-banners
PDF: https://help.zscaler.com/pdf/com/en/1531542.pdf

FTP banners are metadata about the service running on an FTP server. Typically, the FTP banner is used as a welcome string that is shown to clients connecting to FTP servers. You can associate the FTP banners with network decoys that have FTP service enabled. Zscaler Deception provides a list of reconfigured FTP banners that can lure attackers when used with network decoys. You can also create custom FTP banners that can lure attackers based on your business requirements. To learn how to use FTP banners in network decoys, see [Configuring Services on a Network Decoy](/deception/configuring-services-network-decoy#configuring-ftp-service).
Creating an FTP Banner
To create an FTP banner:
- Go to **Miragemaker **> **Miscellaneous **> **FTP Banners**.
-
Click **Add FTP Banner**.
[See image.](#zd-ftp-banner-add-button)
-
In the **FTP Banner Details **window, enter the **Name** that will be used as the FTP banner message.
[See image.](#zd-ftp-banner-add)
- Click **Submit**.
Editing an FTP Banner
To edit an FTP banner:
- Go to **Miragemaker **> **Miscellaneous **> **FTP Banners**.
- Locate the FTP banner that you want to edit, and click the **Edit **icon.
-
Modify the **Name **field as required.
[See image.](#zd-fto-banner-edit)
- Click **Submit.**
Default FTP banners cannot be edited.
**Deleting an FTP Banner**
To delete an FTP banner:
- Go to **Miragemaker **> **Miscellaneous **> **FTP Banners**.
-
Locate the FTP banner that you want to delete, and click the **Delete **icon.
[See image.](#zd-ftp-banner-delete)
- In the confirmation window, click **OK**.
Default FTP banners cannot be deleted.
[]![A screenshot capturing the option to add FTP banner](/downloads/deception/miragemaker/miscellaneous/configuring-and-managing-ftp-banners/zscaler-deception-add-ftp-banner-button.png)
[]![A screenshot capturing FTP Banner Details window](/downloads/deception/miragemaker/miscellaneous/configuring-and-managing-ftp-banners/zscaler-deception-configure-ftp.png)
[]![A screenshot capturing the edit FTP banner option](/downloads/deception/miragemaker/miscellaneous/configuring-and-managing-ftp-banners/zscaler-deception-edit-ftp.png)
[]![A screenshot capturing the delete FTP banner option](/downloads/deception/miragemaker/miscellaneous/configuring-and-managing-ftp-banners/zscaler-deception-delete-ftp-banner.png)