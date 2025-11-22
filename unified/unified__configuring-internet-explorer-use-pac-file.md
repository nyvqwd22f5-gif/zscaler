# Configuring Internet Explorer to Use a PAC File
Source: https://help.zscaler.com/unified/configuring-internet-explorer-use-pac-file
PDF: https://help.zscaler.com/pdf/com/en/1495481.pdf

To redirect your web traffic to the Zscaler cloud, you can configure your browser to use a PAC file. A PAC file is a text file that directs a browser to forward traffic to a proxy server before going to the destination server. The Zscaler service hosts a default PAC file that uses geolocation technology to forward traffic to the nearest Internet & SaaS Public Service Edge. To learn more, see [Using Default PAC Files to Forward Traffic to Internet & SaaS](/unified/using-default-pac-files-forward-traffic-internet-saas).
The browser version used in this example is Internet Explorer 20H2 (OS Build 19042.1526).
To configure Internet Explorer to use the Zscaler’s PAC file URL:
- Copy the default PAC file URL from your Admin Portal:
- Go to** Infrastructure **>** Internet & SaaS **>** Traffic Forwarding **>** Hosted PAC Files**.
- Copy the URL of the Proxy PAC to your clipboard.
[See image.](#Image1)
- Open Internet Explorer and click the **Gear** icon to open the **Tools **menu, then click **Internet options**.
[See image.](#Image2)
- In the **Internet Options** window, click **Connections**, then **LAN Settings**.
[See image.](#Image3)
The **Local Area Network (LAN) Settings **window appears.
- In the **Local Area Network (LAN) Settings** windows, select **Use automatic configuration script **and paste the PAC file URL that you copied from the Admin Portal.
[See image.](#Image4)
- Click **OK **to save the configuration.
[][![Screenshot of Hosted PAC Files page highlighting the URL of the default PAC file](/downloads/zia/documentation-knowledgebase/forwarding-your-traffic/pac-files/using-pac-files/configuring-internet-explorer-use-pac-file/ZIA-config-internet-explorer-copy-hosted-pac-file.png?1669267810)
]
[]![Screenshot of Internet Explorer settings highlighting the Internet options choice](/downloads/zia/documentation-knowledgebase/forwarding-your-traffic/pac-files/using-pac-files/configuring-internet-explorer-use-pac-file/ZIA_internet_explorer_internet_options_screenshot.png)
[]![Screenshot of Connections tab on Internet Options in Internet Explorer. LAN settings button is highlighted.](/downloads/zia/documentation-knowledgebase/forwarding-your-traffic/pac-files/using-pac-files/configuring-internet-explorer-use-pac-file/ZIA_LAN_settings_button_internet_explorer_screenshot.png)
![Screenshot of LAN Settings window highlighting Use automatic configuration script option. PAC file URL is entered in Address field.](/downloads/zia/documentation-knowledgebase/forwarding-your-traffic/pac-files/using-pac-files/configuring-internet-explorer-use-pac-file/ZIA_LAN_settings_pac_file_url_explorer_screenshot.png)
[]