# Configuring Mozilla Firefox to Use a PAC File
Source: https://help.zscaler.com/zia/configuring-mozilla-firefox-use-pac-file
PDF: https://help.zscaler.com/pdf/com/en/1399186.pdf

To redirect your web traffic to the Zscaler cloud, configure your browser to use a PAC file. A PAC file is a text file that directs a browser to forward traffic to a proxy server before going to the destination server. The Zscaler service hosts a default PAC file that uses geolocation technology to forward traffic to the nearest ZIA Public Service Edge. To learn more, see [Using Default PAC Files to Forward Traffic to ZIA](/zia/using-default-pac-files-forward-traffic-zia).
The browser version used in this example is Mozilla Firefox 94.0.2.
To configure Mozilla Firefox to use Zscaler’s PAC file URL:
- Copy the default PAC file URL from your ZIA Admin Portal:
- Go to **Administration **>** ****Hosted PAC Files**.
[See image.](#hosted-pac-files-admin-portal)
- Copy the URL of the Proxy PAC to your clipboard.
[See Image.](#copy-service-default-pac-file)
- Open Mozilla Firefox, open the menu, then click **Settings**.
[See image.](#settings)
- Under the **General **section, scroll down to **Network Settings** and then click **Settings...**.
[See image.](#network-settings)
The **Connection Settings** window appears.
- In the **Connection Settings** window, select **Automatic proxy configuration URL **and paste the PAC file URL that you copied from the ZIA Admin Portal.
[See image. ](#connection-settings)
- Click **OK **to save the configuration.
For more information about getting started on the Zscaler service, see [Getting Started](/zia/getting-started).
[![Screenshot of Hosted PAC Files menu in ZIA Admin Portal](/downloads/zia/documentation-knowledgebase/forwarding-your-traffic/pac-files/using-pac-files/configuring-mozilla-firefox-use-pac-file/ZIA-admin-portal-hosted-pac-files-menu.png)
]
[![Screenshot of Hosted PAC Files page highlighting the URL of the default PAC file](/downloads/zia/documentation-knowledgebase/forwarding-your-traffic/pac-files/using-pac-files/configuring-mozilla-firefox-use-pac-file/ZIA-config-mozilla-firefox-copy-hosted-pac-file.png?1669268705)
]
[![Screenshot of Firefox browser highlighting the Settings menu](/downloads/zia/documentation-knowledgebase/forwarding-your-traffic/pac-files/using-pac-files/configuring-mozilla-firefox-use-pac-file/ZIA-config-mozilla-firefox-settings-menu.png)
]
[![Screenshot of Network page under the General settings tab. Settings button highlighted](/downloads/zia/documentation-knowledgebase/forwarding-your-traffic/pac-files/using-pac-files/configuring-mozilla-firefox-use-pac-file/ZIA-config-mozilla-firefox-network-settings.png)
]
[]![Screen shot of Connection Settings window in Mozilla Firefox Browser](/downloads/zia/documentation-knowledgebase/forwarding-your-traffic/pac-files/using-pac-files/configuring-mozilla-firefox-use-pac-file/ZIA-config-mozilla%20-firefox-connection_settings_window_firefox_screenshot.png)