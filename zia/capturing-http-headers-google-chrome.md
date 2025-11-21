# Capturing HTTP Headers on Google Chrome
Source: https://help.zscaler.com/zia/capturing-http-headers-google-chrome
PDF: https://help.zscaler.com/pdf/com/en/1398981.pdf

At times, Zscaler Support might ask you to provide HTTP headers when troubleshooting certain issues. The HTTP headers identify the specific URL the browser accessed when you open a web page. Google Chrome has a built-in developer tool that allows you to capture HTTP headers and save them to a file. You can use the Google Chrome embedded HTTP header capture tool on Google Chrome version 54.0.2840.71 m and later. If you are running a different browser version, the steps might be different.
When capturing HAR files with sensitive data (e.g., Cookie, Set-Cookie, and Authorization headers), Personal Identifiable Information (PII) like usernames and passwords might be exposed. Delete any password data before sending these files to Zscaler Support.
Capturing HTTP Headers
To capture headers in Chrome:
- Do either of the following:
- Open the Developer Tools window by pressing `Ctrl+Shift+i`.
-
Open the** **menu in the top-right corner and go to** More Tools **> **Developer Tools**.
[See image.](#chrome-menu)
- Click the **Network** tab.
-
Make sure the record button is red and the **Preserve log **and** Disable Cache** options are checked.
[See image.](#chrome-buttons)
-
When the test is completed, click on the **Export** icon to download the sanitized HAR file. If you long click on the icon for a few seconds, you are given the option to export the HAR file with sensitive data.
[See image.](#chrome-save)
For Chrome versions later than 130, right-click on any transaction and select **Save all as HAR with content**.
- Click **Save **on the window that appears to download the file.
-
Select** **the **Console **tab, right-click on the message, and select **Save as**.
[See image.](#console-image)
- Click **Save **on the window that appears to download the file.
- Send the saved file to Zscaler Support.
[]![Go to Developer Tools by clicking More tools and then Developer tools](/downloads/tech-pubs-drafts/zia-draft-articles/capturing-http-headers-google-chrome-draft/Chrome%201_1.png)
[]![Ensure Record, Disable Cache, and Preserve log are selected](/downloads/tech-pubs-drafts/zia-draft-articles/capturing-http-headers-google-chrome-draft/Chrome%202.png)
[]![Options displayed after long click](/downloads/zia/troubleshooting/capturing-http-headers-google-chrome/Export%20HAR%20Edited.png)
[]![Click Console and then click on Save as](/downloads/tech-pubs-drafts/zia-draft-articles/capturing-http-headers-google-chrome-draft/Chrome%204.png)
Exporting HTTP Headers with Sensitive Data
Chrome version 130 and later does not include sensitive data by default when the **Export** or **Save **option is selected.
The sensitive data included contains only the specific information needed to assist Zscaler Support in troubleshooting more effectively. This includes the Cookie, Set-Cookie, and Authorization headers.
To store the HTTP header file with sensitive data:
- Open the **Developer Tools** window by pressing `Ctrl+Shift+i`.
- Click the **Settings** icon and go to **Preferences**.
- Scroll to the **Network **section and check **Allow to generate HAR (with sensitive data)**.
[See Image.](#test-image)
-
On the **Network** tab, check **Preserve Log** and **Disable cache** to save data after SSO redirects.
[See Image.](#preserve-log)
- Click the **Clear network log **icon (circle with a diagonal cross) before starting the test.
-
Optionally, click the **Stop recording network log **icon (red circle) when the test is complete.
[See Image.](#stop-rec)
-
Click and hold the **download** button and select** Export HAR (with sensitive data)**.
[See Image.](#download-button)
- Send the saved file to Zscaler Support.
Alternatively, you can:
- Right-click a transaction in the **Network** tab.
-
Select **Copy > Copy all as HAR (with sensitive data)**.
[See Image.](#copy-data)
- Send the saved file to Zscaler Support.
[]![Click the Settings icon and go to Preferences](/downloads/zia/troubleshooting/capturing-http-headers-google-chrome/settings%20prefs.png)
[]![make sure that Preserve logs and Disable cache is selected](/downloads/zia/troubleshooting/capturing-http-headers-google-chrome/Preserve%20logs.png)
[]![Click red circle or the circle with the cross to record or clear logs ](/downloads/tech-pubs-drafts/zia-draft-articles/capturing-http-headers-google-chrome-doc-54588/Export%20HTTP%20with%20sensitive%20data%201.png)
[]![Click and hold the download button to export HAR with sensitive data](/downloads/zia/troubleshooting/capturing-http-headers-google-chrome/Export%20HAR.png)
[]![Right click an entry and click Copy and then copy all as HAR](/downloads/zia/troubleshooting/capturing-http-headers-google-chrome/Copy%20and%20save%20HAR.png)