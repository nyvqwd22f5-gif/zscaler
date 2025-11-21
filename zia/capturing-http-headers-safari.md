# Capturing HTTP Headers on Safari
Source: https://help.zscaler.com/zia/capturing-http-headers-safari
PDF: https://help.zscaler.com/pdf/com/en/1401661.pdf

At times, Zscaler Support might ask you to provide HTTP headers when troubleshooting certain issues. The HTTP headers identify the specific URL the browser accessed when you open a web page. You can use Safari's Inspector tool to capture HTTP headers in Safari version 17.5. If you are running a different browser version, the steps might be different. To learn more, refer to the [Safari documentation](https://support.apple.com/en-gb/guide/safari-developer/welcome/mac).
Capturing HTTP Headers
- In Safari, go to the desired website. In this example, it's www.zscaler.com.
-
From the **Develop** menu, click **Show Web Inspector**. The **Web Inspector** page opens.
[See image.](#inspect)
If you don't see the **Develop** menu,
- Click the **Safari** menu and select **Preferences**. The **Preferences** Window appears.
-
Click the **Advanced** tab and select the **Show features for web developers **checkbox.
[See image.](#web-dev)
-
Close the **Preferences** window. The **Develop** menu appears in the menu bar.
[See image.](#view-develop-menu)
- On the **Web Inspector** page, click the **Network** tab.
-
Select the **Disable Cache **checkbox and then reload the page.
[See image.](#network)
-
In the **Network** tab, right-click the element you want to inspect and select **Export HAR**. In this view, the HTTP headers are also visible in the **Headers** tab on the right pane.
[See image.](#header)
- Specify a name and click **Save** in the dialog box that appears to save the file.
- Send the saved file to Zscaler Support.
[]![Select Show Develop menu in menu bar](/downloads/Safari%202_1.png)
[]![View Develop Menu](/downloads/Safari%205.png)
[]![Select Web Inspector](/downloads/Safari%201_2.png)
[]![Select Network](/downloads/zia/troubleshooting/capturing-http-headers-safari/Safari%207.png)
[]![Export HAR file](/downloads/Safari%204.png)