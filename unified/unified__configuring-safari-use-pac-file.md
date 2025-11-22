# Configuring Safari to Use a PAC File
Source: https://help.zscaler.com/unified/configuring-safari-use-pac-file
PDF: https://help.zscaler.com/pdf/com/en/1495501.pdf

To redirect your web traffic to the Zscaler cloud, you can configure your browser to use a PAC file. A PAC file is a text file that directs a browser to forward traffic to a proxy server before going to the destination server. The Zscaler service hosts a default PAC file that uses geolocation technology to forward traffic to the nearest Internet & SaaS Public Service Edge. To learn more, see [Using Default PAC Files to Forward Traffic to Internet & SaaS](/zia/using-default-pac-files-forward-traffic-zia).
The browser version used in this example is Safari 11.0.1 (13604.3.5).
To configure Safari to use Zscaler’s PAC file URL:
- Copy the default PAC file URL from your Admin Portal:
- Go to **Infrastructure **>** Internet & SaaS **>** Traffic Forwarding **>** Hosted PAC Files**.
- Copy the URL of the Proxy PAC to your clipboard.
[See image.](#Image1)
- Open Safari, open the Safari menu, then click **Preferences...**.
[See image.](#Image2)
- In the **Preferences** window, click **Advanced**.
[See image.](#Image3)
- In the **Advanced **tab, go to **Proxies** and click **Change Settings...**.
[See image.](#Image4)
The **Network** window appears.
- In the **Network** window, select **Automatic Proxy Configuration **and paste the PAC file URL that you copied from the Admin Portal.
[See image.](#Image5)
- Click **OK** to save the configuration.
- Restart Safari to enact changes.
[][![Screenshot of Hosted PAC Files page highlighting the URL of the default PAC file](/downloads/zia/documentation-knowledgebase/forwarding-your-traffic/pac-files/using-pac-files/configuring-safari-use-pac-file/hosted_pac_files_default_pac_url.png)
]
[][![Screenshot of Safari preferences tab circled with an orange box. There is also an arrow pointing to preferences, with the words "Click here to open the Preferences tab" next to the arrow](/downloads/zia/getting-started/first-90-days/how-do-i-configure-safari-use-pac-file/ZIA-Safari-Preferences-link.png)
]
[][![Screenshot of the Safari preferences tab with the Advanced tab circled.](/downloads/zia/getting-started/first-90-days/how-do-i-configure-safari-use-pac-file/ZIA-SafariPac-Advanced-Button.png)
]
[][![Screenshot of the Safari Advanced Preferences tab with the Change Settings option for proxies circled.](/downloads/zia/getting-started/first-90-days/how-do-i-configure-safari-use-pac-file/ZIA-Safari-Change-Proxies.png)
]
[][![Screenshot of the network proxy tab with an arrow pointing to the Automatic Proxy Configuration and another arrow pointing to the URL box](/downloads/zia/getting-started/first-90-days/how-do-i-configure-safari-use-pac-file/ZIA-Safari-Automatic-Proxy.png)
]