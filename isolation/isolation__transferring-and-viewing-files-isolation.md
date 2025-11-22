# Transferring and Viewing Files in Isolation
Source: https://help.zscaler.com/isolation/transferring-and-viewing-files-isolation
PDF: https://help.zscaler.com/pdf/com/en/1373986.pdf

[Watch a video about transferring and viewing files in an isolation browser.](https://fast.wistia.net/embed/iframe/yfsb90jsen)
Isolation gives you the ability to render, transfer, download, view, and print web pages, inline content, and files. These controls are available in [the Isolation Bar](/isolation/using-isolation-bar-native-browser-experience).
Different rendering methods of web pages may provide different results for files viewed in Isolation, especially if you have Turbo Mode enabled for your isolation profile. To learn more, see [Using Turbo Mode for Isolation](/isolation/using-turbo-mode-isolation).
Files that you render within isolation are not rendered in their original format, but are converted into a PDF in the isolation browser and then rendered for viewing. The isolation browser provides a secure area called Protected Storage, where certain files can be rendered and held temporarily for the duration of the isolation session. To add a file to Protected Storage, select **Download** > **Protected Storage** while viewing the file. You can view available file types in isolation in both Google Chrome and Mozilla Firefox browsers.
PDF technology is powered by PDFTron WebViewer SDK copyright © PDFTron™ Systems Inc., 2001–2022, and distributed by Zscaler, Inc. under license.
Enable File Controls for Your Isolation Profile
Before you can begin downloading, uploading, or viewing files within isolation, make sure the Security Controls for your Zscaler Internet Access (ZIA) or Zscaler Private Access (ZPA) isolation profile are set to allow you to do so. To learn more, see [Creating Isolation Profiles for ZIA](/isolation/creating-isolation-profiles-zia) and [Creating Isolation Profiles for ZPA](/isolation/creating-isolation-profiles-zpa).
To ensure that you can access files from Isolation via a ZIA isolation profile, you must configure an exception rule for URL filtering. To learn more, see [About URL Filtering](https://help.zscaler.com/zia/about-url-filtering).
File Type Capabilities in Isolation
The lists below show the different file types and what you can do with them while they are in isolation.
You can upload and download the following file types to your Protected Storage and your device, and you can open them directly to render and view while in isolation:
- Video formats: .MP4, .OGG, . WEBM, .WAV
- Audio formats: .MP3, .WAV, .OGG
- Document formats: .PDF, .TXT, .DOC, .DOCX, .XLS, .XLSX, .PPTX, .PPT, .ODT, .ODS, .ODP
- Image formats: .JPG, .PNG, .GIF, .BMP, .SVG, .ICO, .WEBP, .APNG
- Compressed formats: .ZIP, .TAR, .7Z, .RAR
- Other formats: .JSON, .XML, .HTML, .CSV, .RTF, .VSDX
If a user accesses an Office file or password-protected file, they are prompted to enter the file-specific password. Then the file is rendered on the isolation browser for the duration of the isolated session.
Depending on the mobile device used, some file types such as PDFs require the user to allow pop-ups on their device. To learn more, see [Mobile User Experience in Isolation](/isolation/mobile-user-experience-isolation) and [Ranges & Limitations](/isolation/ranges-limitations).
You cannot render or view the following file types in isolation. However, you can still download or upload them directly to and from your device:
- Video formats: .AVI, .MOV, .WMV, .AVIF, .M4V, .M4A, .MKV, .OGV, .OGA
- Image formats: .TIFF, .MNG, .CUR
Uploading, Downloading, and Viewing Files in Isolation
The file size limit for uploading and downloading files in an isolated session is 1 GB per file. To learn more, see [Ranges & Limitations](/isolation/ranges-limitations).
You can upload multiple files simultaneously, and download files individually. Isolation does not set a minimum or maximum limit on how many files you can transfer at once, as it depends on each user's personal environment configurations.
Depending on the policies related to your isolation profile settings, some files might not be viewable or downloadable in isolation. To learn more, see [Sandbox Integration with Isolation](/isolation/sandbox-integration-isolation).
To download and view a file during an isolated session:
- Download a file while in isolation as you would in a normal browser window.
- Depending on your [isolation profile settings](/isolation/profiles), the file downloads either directly to your isolation browser's temporary **Protected Storage** or to your device's local storage. To learn more, see [Creating Isolation Profiles for ZIA](/isolation/creating-isolation-profiles-zia) and [Creating Isolation Profiles for ZPA](/isolation/creating-isolation-profiles-zpa).
- Go to the **Isolation Bar** and click **Show Saved Files**.
- From the list of downloads, double-click the file. A new tab within the isolation browser opens to display the rendered file for viewing.
Printing Content in Isolation
You can print web pages, inline content, and files from an isolated browser.
Disabling the printing feature for an isolation profile disables all possibility of being able to print the web page or document that is rendered in isolation. When printing is disabled on an isolation profile, the user cannot see the print option from the right-click menu or the print button in the Isolation Bar. If the user tries to select File > Print from the browser menu, or enter the key command `CTRL/CMD+P` shortcut, a message appears noting that this ability is disabled by policy.
To print Office files from your isolated browser:
- Click the **Print** button on the [Isolation Bar ](/isolation/using-isolation-bar-native-browser-experience)or use [the right-click menu](/isolation/using-right-click-menu-isolation).
You can also use the commands Ctrl+P on Windows devices or Cmd+P on Mac devices.
- Depending on what you are trying to print, different settings windows appear before the Print preview.
- If you are printing a web page or hyperlink that requires choosing sections of the page to print, the **Print **checklist appears.
In the **Print **checklist:
- Select** **the sections of the web page to print. The isolated browser automatically creates sections of the page to choose from.
- Click **Print**. When in mobile isolation, the appearance of the print button depends on the mobile device. To learn more, see [Mobile User Experience in Isolation](/isolation/mobile-user-experience-isolation).
[See image.](#Select-sections-checklist)
- If you are printing Office files, the **Office file settings **window appears.
In the **Office file settings **window:
- Select the number of **Pages to print**: all, current page, current view, or specific pages.
- (Optional) Select the checkboxes to include comments or annotations.
- Select the **Print Quality**: **High** or **Normal**.
- (Optional) Select the option to **Add Watermark**.
- Click **Print**.
[See image.](#Office-files)
- The **Print details** window appears in a new tab in the isolation browser.
In the **Print details** window:
- If printing inline content, select the number of pages to print: **All**, or a quantity from the drop-down menu.
- Select the **Layout**: **Portrait** or **Landscape**.
- Select the **Paper size** for the print job.
- Select the number of **Pages per sheet**.
- Select the **Margins **of the printed page(s): Choose the **Defaul**t or enter your own dimensions.
- Select the **Scale **of the printed page(s): Choose the **Defaul**t or enter your own dimensions.
- Select the checkbox for **Header and footers** and **Background graphics**.
- Click **Print**.
[See image.](#Isolation-print-window)
[]![Isolation Print Preview and Print details window](/downloads/isolation/end-user-isolation-experience/transferring-and-viewing-files-isolation/new-print-modal-options.png)
[]![Select sections of inline content to print](/downloads/zscaler-tech-pubs-style-guide/draft-articles/using-isolation-bar-native-browser-experience-draft-print-b/Print-Inline-Content_isolation-browser_select-sections-checklist.jpg)
[]![Office file settings print window](/downloads/zia/cloud-browser-isolation/transferring-and-viewing-files-cloud-browser-isolation/Office-files-print-setttings-window.jpg)