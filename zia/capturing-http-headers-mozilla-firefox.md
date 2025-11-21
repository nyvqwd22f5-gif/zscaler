# Capturing HTTP Headers on Mozilla Firefox
Source: https://help.zscaler.com/zia/capturing-http-headers-mozilla-firefox
PDF: https://help.zscaler.com/pdf/com/en/1398971.pdf

At times, Zscaler Support might ask you to provide HTTP headers when troubleshooting certain issues. The HTTP headers identify the specific URL the browser accessed when you opened a web page. You can use Mozilla's Inspector tool to capture HTTP headers in Mozilla Firefox version 128. If you are running a different browser version, the steps might be different. To learn more, refer to the [Mozilla documentation](https://developer.mozilla.org/en-US/docs/Tools/Network_Monitor/request_details).
Capturing HTTP Headers
To capture header in Mozilla Firefox:
-
Do either of the following:
- Open the Developer Tools window by pressing `Ctrl+Shift+i`.
- Open the menu in the top-right corner and go to **More Tools **> **Developer Tools**.
[See image.](#web-dev)
-
In the **Web Developer Tools** window, select the **Network** tab.
[See image.](#network)
- In the **Network** tab, select **Disable Cache **and right-click the element you want to inspect.
-
Select **Save All As HAR**.
[See image.](#header)
- Click **Save** on the dialog box to download the file.
- Select the** Console **tab and right-click on the message.
-
Select **Save all Messages to File**.
[See image.](#console-image)
- Click **Save** on the dialog box to download the file.
- Send the saved file to Zscaler Support.
[]![Select Web Developer](/downloads/tech-pubs-drafts/zia-draft-articles/capturing-http-headers-mozilla-firefox-draft/Mozilla%201.png)
[]![Select Network](/downloads/tech-pubs-drafts/zia-draft-articles/capturing-http-headers-mozilla-firefox-draft/Mozilla%202.png)
[]![Save HAR file](/downloads/tech-pubs-drafts/zia-draft-articles/capturing-http-headers-mozilla-firefox-draft/Mozilla%203.png)
[]![Console page](/downloads/tech-pubs-drafts/zia-draft-articles/capturing-http-headers-mozilla-firefox-draft/Mozilla%204.png)