# Identifying the PAC File on a Device Using Browsers
Source: https://help.zscaler.com/unified/identifying-pac-file-device-using-browsers
PDF: https://help.zscaler.com/pdf/com/en/1495511.pdf

Zscaler recommends that you install [a PAC file](/unified/using-default-pac-files-forward-traffic-internet-saas) for each user to ensure coverage outside the corporate network. When a PAC file is configured on a user's browser, it instructs the browser to forward traffic to a proxy server.
There are methods you can use to identify the PAC file configured on a user's device. For example, you can take traffic captures and check the PAC file requests, or check the registry entry for the PAC file configured.
The following sections include information for browser-specific methods. These features belong to the browsers and are not related to Zscaler.
- [Google Chrome](#chrome)
- [Internet Explorer](#ie)
- [Mozilla Firefox](#firefox)
- [Opera](#opera)
- [Safari](#safari)
To learn how to configure your browser to use a PAC file, see:
- [Configuring Google Chrome to use a PAC file](/unified/configuring-google-chrome-use-pac-file)
- [Configuring Internet Explorer to use a PAC file](/unified/configuring-internet-explorer-use-pac-file)
- [Configuring Mozilla Firefox to use a PAC file](/unified/configuring-mozilla-firefox-use-pac-file)
- [Configuring Safari to use a PAC file](/unified/configuring-safari-use-pac-file)
[]If your user is using Google Chrome, do the following:
The browser version used in this example is Google Chrome 96.0.4664.45.
- Enter **chrome://net-export/** into the address bar.
- In the **Options** menu, make sure **Strip private information** is selected, then click **Start Logging to Disk**.
[See image.](#start-logging-chrome)
- In the **Save As** window, click **Save** to save the log as a JSON file.
[See image.](#save-as-chrome)
- Click **Stop Logging**.
[See image.](#stop-logging-chrome)
- Click **Show File**.
[See image.](#show-file-chrome)
- Open the saved JSON file and search for the keyword `proxySettings`.
You see the URL of the PAC file configured to the user's browser, similar to the following example:
`"proxySettings":{"effective":{"pac_url":"http://pac.zscalerbeta.net/zscalerbeta.net/proxy.pac"},
"original":{"pac_url":"http://pac.zscalerbeta.net/zscalerbeta.net/proxy.pac"}}`
[]![Screenshot of Start Logging option in the Google Chrome window](/downloads/zia/documentation-knowledgebase/forwarding-your-traffic/pac-files/using-pac-files/identifying-pac-file-on-device-using-browsers/ZIA-google-chrome-start-logging.png)
![Screenshot of Save As window for saving log](/downloads/zia/documentation-knowledgebase/forwarding-your-traffic/pac-files/using-pac-files/identifying-pac-file-on-device-using-browsers/ZIA-google-chrome-save-log.png)
[]
[]![Screenshot of Stop Logging option in the Google Chrome window](/downloads/zia/documentation-knowledgebase/forwarding-your-traffic/pac-files/using-pac-files/identifying-pac-file-on-device-using-browsers/ZIA-google-chrome-stop-logging.png)
[]![Screenshot of Show File option in the Google Chrome window](/downloads/zia/documentation-knowledgebase/forwarding-your-traffic/pac-files/using-pac-files/identifying-pac-file-on-device-using-browsers/ZIA-google-chrome-show-file.png)
[]If your user is using Mozilla Firefox, do the following:
The browser version used in this example is Mozilla Firefox 44.0.2.
- Enter **about:config **into the address bar.
- Click **I'll be careful, I promise!**
[See image.](#seeimage1)
- In the **Search** field, enter the word "proxy." The URL of the PAC file configured to the user's browser appears in the value of **network.proxy.autoconfig_url**.
[See image.](#seeimage2)
[]![Screenshot of the I'll be careful, I promise button in Mozilla Firefox](/downloads/zia/documentation-knowledgebase/forwarding-your-traffic/pac-files/knowledge-base/how-do-i-use-browser-identify-pac-file-device/i'll_be_careful,_i_promise_button_in_mozilla_firefox.png)
[]![Screenshot of network.proxy.autoconfig_url in Mozilla Firefox ](/downloads/zia/documentation-knowledgebase/forwarding-your-traffic/pac-files/knowledge-base/how-do-i-use-browser-identify-pac-file-device/network.proxy.autoconfig_url_in_mozilla_firefox_.png)
[]If your user is using Internet Explorer, do the following:
The browser version used in this example is Internet Explorer 11.0.9600.17905.
- Click the Gear icon to open the Tools menu. Then click **Internet options**.
[See image.](#seeimage3)
- In the **Internet Options **window, click **Connections**, then **LAN Settings**.
[See image.](#seeimage4)
- In the **Local Area Network (LAN) Settings** window, the URL of the PAC file configured to the user's browser appears in the **Address **field under **Use automatic configuration script**.
[See image.](#seeimage5)
[]![Screenshot of the Settings Icon and the Internet options button in Internet Explorer](/downloads/zia/documentation-knowledgebase/forwarding-your-traffic/pac-files/knowledge-base/how-do-i-use-browser-identify-pac-file-device/settings_icon_&_internet_options_button_in_internet_explorer.png)
[]![Screenshot of the Connection tab and LAN settings button in the Internet Options window](/downloads/zia/documentation-knowledgebase/forwarding-your-traffic/pac-files/knowledge-base/how-do-i-use-browser-identify-pac-file-device/connection_tab_&_lan_settings_button_in_the_internet_options_window.png)
[]![Screenshot of the Address field in the Local Area Network (LAN) Settings window](/downloads/zia/documentation-knowledgebase/forwarding-your-traffic/pac-files/knowledge-base/how-do-i-use-browser-identify-pac-file-device/address_field_in_the_local_area_network_(lan)_settings_window.png)
[]If your user is using Opera, do the following:
The browser version used in this example is Opera 36.0.
- Click **Menu**, then click **Settings**.
[See image.](#seeimage6)
- Click **Browser**, then navigate to **Network**. Click **Change Proxy Settings**.
[See image.](#seeimage7)
- In the **Internet Properties** window, click **LAN settings**.
[See image.](#seeimage8)
- In the **Local Area Network (LAN) Settings** window, the URL of the PAC file configured to the user's browser appears in the **Address **field under **Use automatic configuration script**.
[See image.](#seeimage9)
[]![Screenshot of the Settings button in the Opera Menu](/downloads/zia/documentation-knowledgebase/forwarding-your-traffic/pac-files/knowledge-base/how-do-i-use-browser-identify-pac-file-device/settings_button_in_the_opera_menu.png)
[]![Screenshot of the Change proxy settings... button in Opera](/downloads/zia/documentation-knowledgebase/forwarding-your-traffic/pac-files/knowledge-base/how-do-i-use-browser-identify-pac-file-device/change_proxy_settings..._button_in_opera.png)
[]![Screenshot of the LAN settings button in the Internet Properties window](/downloads/zia/documentation-knowledgebase/forwarding-your-traffic/pac-files/knowledge-base/how-do-i-use-browser-identify-pac-file-device/lan_settings_button_in_the_internet_properties_window.png)
[]![Screenshot of the Address field in the Local Area Network (LAN) Settings window](/downloads/zia/documentation-knowledgebase/forwarding-your-traffic/pac-files/knowledge-base/how-do-i-use-browser-identify-pac-file-device/address_field_in_the_local_area_network_(lan)_settings_window.png)
[]If your user is using Safari, do the following:
The browser version used in this example is Safari 11.0.3 (13604.5.6).
- Open Safari, open the Safari menu, then click **Preferences...**.
The **Preferences** window appears.
- Click **Advanced**.
The **Advanced** tab appears.
- Go to Proxies and click **Change Settings...**.
The **Network** window appears.
- Select **Automatic Proxy Configuration** and you see any PAC file addresses being used.