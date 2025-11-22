# Using Sandbox Integration with Isolation
Source: https://help.zscaler.com/isolation/using-sandbox-integration-isolation
PDF: https://help.zscaler.com/pdf/com/en/1517336.pdf

For Zscaler customers using both [Sandbox and Isolation](/isolation/about-sandbox-integration-isolation), an integration between these modules exists which provides additional benefits maximizing both security and end user productivity.
When a user opens an unknown file, such as a PDF or Microsoft Office document, the file initially opens in the isolated browser. This isolated environment prevents any malicious content from reaching the user's endpoint, but still allows them to access the original file to maximize user productivity, while this file is being analyzed by [Sandbox](/zia/about-sandbox). The file's status can be identified by the Isolation URL and the Sandbox banner.
Prerequisites
- Configure the Sandbox policy in ZIA. To learn more, see [Configuring the Sandbox Policy](/zia/configuring-sandbox-policy).
- Enable the Sandbox option for file transfer in your isolation profile. To learn more, see [Creating Isolation Profiles for ZIA](/isolation/creating-isolation-profiles-zia).
To use Sandbox with Isolation:
- Download a file that triggers a Sandbox policy. An isolated browser window opens to render the file.
[See image.](#new-file)
- When rendering is complete, the rendered file is scanned by Sandbox, and Sandbox determines whether the file contains malicious content. If it does, a red Sandbox banner appears. If it does not, a blue Sandbox banner appears.
- If it's malicious, click the red Sandbox banner and select your download option: the **Original File** or a **Flattened PDF. **Downloading a flattened PDF gives you the option to view the file with the malicious content removed.
[See image.](#malicious-file)
- If the content is benign, click the blue Sandbox banner to download the original file.
[See image.](#benign-file)
- Depending on your choice, the downloaded file is saved to your local device.
[]![A sample file appears in an isolated browser. ](/downloads/isolation/policy-management/using-sandbox-integration-isolation/Isolated-Browser_new-file_isolation-banner.png)
[]![The Sandbox banner alerts the user that the file is malicious, and offers the option once clicked to download a flattened PDF or the original file. ](/downloads/isolation/policy-management/using-sandbox-integration-isolation/Isolated-Browser_malicious-file-Sandbox-banner_squircles.png)
[]![The Sandbox banner alerts the user that the file is safe to download.](/downloads/isolation/policy-management/using-sandbox-integration-isolation/Isolated-Browser_benign-file-Sandbox-banner_squircles.png)