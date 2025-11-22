# Configuring Google Chrome to Use a PAC File
Source: https://help.zscaler.com/zia/configuring-google-chrome-use-pac-file
PDF: https://help.zscaler.com/pdf/com/en/1399181.pdf

To redirect your web traffic to the Zscaler cloud, you can configure your browser to use a PAC file. A PAC file is a text file that directs a browser to forward traffic to a proxy server before going to the destination server. The Zscaler service hosts a default PAC file that uses geolocation technology to forward traffic to the nearest ZIA Public Service Edge. To learn more, see [Using Default PAC Files to Forward Traffic to ZIA](/zia/using-default-pac-files-forward-traffic-zia).
The following steps describe how to configure Google Chrome to use a PAC file on Windows systems:
- [Windows 7](#windows7)
- [Windows 8 or later](#windows8)
[]The browser version used in this example is Google Chrome 53.0.2785.143 m. These steps may vary for different versions of Google Chrome.
To configure Google Chrome to use Zscaler’s PAC file URL:
- Copy the default PAC file URL from your ZIA Admin Portal:
- Go to **Administration **>** ****Hosted PAC Files**.
[See image.](#hosted-pac-files-windows8)
- Copy the URL of the Proxy PAC file to your clipboard.
[See image.](#Image1)
- Open Google Chrome, open the **Chrome** menu, then click **Settings**.
[See image.](#Image2)
- In the **Settings** window, click **Show advanced settings...**.
[See image.](#Image3)
- Under **Network,** click **Change proxy settings...**.
[See image.](#Image4)
The **Internet Properties** window appears.
- In the **Internet Properties** window, under the **Connections** tab, click **LAN settings**.
[See image.](#Image5)
The **Local Area Network (LAN) Settings** window appears.
- In the **Local Area Network (LAN) Settings** window, select **Use automatic configuration script **and paste the PAC file URL that you copied from the ZIA Admin Portal.
[See image.](#Image6)
- Click **OK** to save the configuration.
[]The browser version used in this example is Google Chrome 96.0.4664.45. These steps may vary for different versions of Google Chrome.
To configure Google Chrome to use Zscaler’s PAC file URL:
- Copy the default PAC file URL from your ZIA Admin Portal:
- Go to **Administration **>** ****Hosted PAC Files**.
[See image.](#hosted-pac-files-windows7)
- Copy the URL of the Proxy PAC file to your clipboard.
[See image.](#copy-hosted-pac-file)
- Open Google Chrome, open the **Chrome** menu, then click **Settings**.
[See image.](#google-chrome-settings)
- In the **Settings** window, click **Advanced **and then** System**.
- Click **Open your computer's proxy settings**.
[See image.](#chrome-system-settings-page)
The **Proxy **settings page of your system appears.
- In the **Proxy **settings page, enable **Use setup script **and then paste the PAC file URL that you copied from the ZIA Admin Portal into the **Script address **field.
[See image.](#proxy-settings-page)
- Click **Save **to save the configuration.
For more information about getting started on the Zscaler service, see [Getting Started](/zia/getting-started).
[![Screenshot of Hosted PAC Files menu in ZIA Admin Portal](/downloads/zia/documentation-knowledgebase/forwarding-your-traffic/pac-files/using-pac-files/configuring-google-chrome-use-pac-file/ZIA-admin-portal-hosted-pac-files-menu-windows8.png)
]
[]![Screenshot of Hosted PAC Files page highlighting the URL of the default PAC file](/downloads/zia/documentation-knowledgebase/forwarding-your-traffic/pac-files/using-pac-files/configuring-google-chrome-use-pac-file/ZIA-config-google-chrome-pac-copy-hosted-pac-file-windows8.png)
[] ![Screenshot of Google Chrome settings highlighting the Settings option](/downloads/zia/documentation-knowledgebase/forwarding-your-traffic/pac-files/using-pac-files/configuring-google-chrome-use-pac-file/ZIA-config-google-chrome-pac-select-settings.png)
[]![Screenshot of System page. Open your computer's proxy settings option is highlighted. ](/downloads/zia/documentation-knowledgebase/forwarding-your-traffic/pac-files/using-pac-files/configuring-google-chrome-use-pac-file/ZIA-config-google-chrome-pac-open-proxy-settings.png)
[]![Screenshot of Proxy Settings page of your system to enable Use Setup script option. PAC file URL is entered in Address field.](/downloads/zia/documentation-knowledgebase/forwarding-your-traffic/pac-files/using-pac-files/configuring-google-chrome-use-pac-file/ZIA-config-google-chrome-paste-pac-file-address.png)
[![Screenshot of Hosted PAC Files menu in ZIA Admin Portal](/downloads/zia/documentation-knowledgebase/forwarding-your-traffic/pac-files/using-pac-files/configuring-google-chrome-use-pac-file/ZIA-admin-portal-hosted-pac-files-menu-windows7.png)
]
[![Screenshot of Hosted PAC Files page highlighting the URL of the default PAC file](/downloads/zia/documentation-knowledgebase/forwarding-your-traffic/pac-files/using-pac-files/configuring-google-chrome-use-pac-file/ZIA-config-google-chrome-pac-copy-hosted-pac-file-windows7.png)
]
[![Screenshot of Google Chrome settings highlighting the Settings option](/downloads/zia/documentation-knowledgebase/forwarding-your-traffic/pac-files/using-pac-files/configuring-google-chrome-use-pac-file/ZIA-config-google-chrome-pac-select-settings-windows7.png)
]
[![Screenshot of Settings page on Google Chrome Settings. “Show advanced settings” is highlighted.](/downloads/zia/getting-started/first-90-days/how-do-i-configure-google-chrome-use-pac-file/show_advanced_settings_google_chrome_screenshot.png)
]
[![Screenshot of Settings page on Google Chrome Settings. Network section is highlighted. Change proxy settings buttons is highlighted. ](/downloads/zia/getting-started/first-90-days/how-do-i-configure-google-chrome-use-pac-file/network_settings_google_chrome_screenshot.png)
]
[![Screenshot of Connections tab on Internet Properties in Google Chrome. LAN settings button is highlighted.](/downloads/zia/documentation-knowledgebase/forwarding-your-traffic/pac-files/using-pac-files/configuring-google-chrome-use-pac-file/ZIA_LAN_settings_button_google-chrome_screenshot.png)
]
[![Screenshot of LAN Settings window highlighting Use automatic configuration script option. PAC file URL is entered in Address field.](/downloads/zia/documentation-knowledgebase/forwarding-your-traffic/pac-files/using-pac-files/configuring-google-chrome-use-pac-file/ZIA_LAN_settings_pac_file_url_google-chrome_screenshot.png)
]