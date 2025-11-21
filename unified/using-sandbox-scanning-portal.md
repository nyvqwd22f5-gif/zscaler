# Using the Sandbox Scanning Portal
Source: https://help.zscaler.com/zia/using-sandbox-scanning-portal
PDF: https://help.zscaler.com/pdf/com/en/1399831.pdf

With Advanced Sandbox, you can manually submit suspicious files for behavioral analysis by uploading them to the [Sandbox Scanning Portal](https://filecheck.zscaler.com).
[See image.](#seeimage1)
After you upload a file, the Sandbox engine performs the following actions:
- Executes and monitors suspicious objects in a controlled sandbox
- Records and analyzes any malicious behaviors
- Applies the [Malware Protection](/zia/configuring-malware-protection-policy) and [Sandbox](/zia/configuring-sandbox-policy) policies configured by your organization
About the Sandbox Scanning Portal Results
After the Sandbox analysis is complete, you can see the following results:
- **File Name**: Displays the name of the file you uploaded.
The file name cannot contain spaces.
- **MD5**:** **Displays the MD5 value you need to search for the file in the ZIA Admin Portal [Insight logs](/zia/about-insights-logs) and view the [Sandbox Detail Report](/zia/viewing-sandbox-reports-data#about-sandbox-detail-report).
The Zscaler service doesn't perform Sandbox analysis if the file is blocked by the [Malware Protection policy](/zia/configuring-malware-protection-policy), is clean, or was previously analyzed by the Sandbox engine.
- **Uploaded URL**: Displays the URL you need to search for either single or multiple files in the ZIA Admin Portal. See the next section for instructions.
- **Size(bytes)**: Displays the size (in bytes) of the file you uploaded.
- **Status**:** **This column can display one of the following statuses:
- **Blocked**: If you see a blocked sign, it indicates that the file was blocked based on the Malware Protection or Sandbox policies. This column also displays why the file was blocked (e.g., due to a virus or malicious behavior).
- **Check Mark**:** **If you see a check mark, it indicates one of the following results:
- The file was clean.
- The file was unknown and sent for analysis.
Besides the previously mentioned results, no other information about the file is viewable. All files are treated as confidential and the information they contain is not viewable in the Sandbox Scanning Portal.
To check whether the file was clean or sent for analysis, you must view the Sandbox logs, which you can access from the ZIA Admin Portal. See the next section for instructions.
[See image.](#seeimage2)
Checking the File Status
To check whether the file was clean or sent for analysis:
- Go to **Analytics** > **Web Insights**.
- Click the** Logs** tab.
- Under **Timeframe**, choose the appropriate time frame. For example, if you sent your files to the Sandbox Scanning Portal within the last day, you can select **Current Day**.
- Under **Select Filters**, you can choose to verify the status for a single file or for multiple files at once:
- [Check the Status for One File](#single-file)
- [Check the Status for Multiple Files](#multiple-files)
To learn more about the Sandbox Detail Report, see [About the Sandbox Detail Report](/zia/viewing-sandbox-reports-and-data#about-the-sandbox-detail-report).
[]![Screenshot of the Sandbox Scanning Portal](/downloads/zia/policies/sandbox/using-sandbox-scanning-portal/ZIA-Sandbox-Scanning-Portal_4.png)
[]![Screenshot of the Sandbox Scanning Portal results](/downloads/zia/documentation-knowledgebase/creating-and-managing-policies/sandbox/using-sandbox-scanning-portal/ZIA-Sandbox-Scanning-Portal-Results.png)
[]To check the status of a single file, do one of the following actions:
- [Filter by MD5 Value](#md5-value)
- [Filter by Uploaded URL](#uploaded-url)
- []Under** Select Filters**, choose **Sandbox MD5**.
- Enter the MD5 value for the file you uploaded to the Sandbox Scanning Portal. If you're pasting the MD5 value, ensure that you haven’t copied any extra spacing before the value, or the search won’t work.
- Choose **Exact Match** from the drop-down menu.
- Click **Apply Filters**.
- If a log isn’t generated, then the file is clean. If a log is generated, then the file was unknown and sent for analysis.
- In the **MD5** column, click the MD5 to view the Sandbox Detail Report for additional data from the analysis.
If you don't see the **MD5** column, click the **Menu** icon at the top right-hand corner, and select **MD5** to add the column.
- []Under **Select Filters**, choose **URL Search**.
- Ensure the **URL** tab is selected.
- Enter `https://filecheck.zscaler.com/``<Uploaded URL>`.
Replace <Uploaded URL> with the Uploaded URL that the Sandbox Scanning Portal provided for the file you uploaded. For example, if the Uploaded URL for a file is app/upload?timestamp_load=1477429427028×tamp_upload=1477436826011, enter `https://filecheck.zscaler.com/app/``upload?timestamp_load=1477429427028×tamp_upload=1477436826011`.
- Choose **Contains** or **Starts With** from the drop-down menu.
- Click **Apply Filters**.
- The **Threat Category **column lists the status of the file. If it displays **None**, the file is clean. If it displays **Sent for Analysis**, the Sandbox engine is analyzing the file.
If you don't see the **Threat Category** column, click the **Menu** icon at the top right-hand corner, and select **Threat Category** to add the column.
- In the **MD5** column, click the MD5 to view the Sandbox Detail Report for additional data from the analysis. If the file is clean, you won’t see a link.
If you don't see the **MD5** column, click the **Menu** icon at the top right-hand corner, and select **MD5** to add the column.
[]To check the status of multiple files that were uploaded simultaneously:
- Under **3. Select Filters**, choose **URL Search**.
- Ensure the **URL** tab is selected.
- Enter `https://filecheck.zscaler.com/``<Uploaded URL>`.
Replace <Uploaded URL component> with the first segment of the Uploaded URL. For example, if the Uploaded URL for a file is app/upload?timestamp_load=1477429427028×tamp_upload=1477436826011, enter `https://filecheck.zscaler.com/``app/upload?timestamp_load=1477429427028`. The first segment of the Uploaded URL is the same for files you upload simultaneously to the Sandbox Scanning Portal.
- Choose **Contains** or **Starts With** from the drop-down menu.
- Click **Apply Filters**.
- The **Threat Category **column lists the status of the file. If it displays **None**, the file is clean. If it displays **Sent for Analysis**, the Sandbox engine is analyzing the file.
If you don't see the **Threat Category** column, click the **Menu** icon at the top right-hand corner, and select **Threat Category** to add the column.
- In the **MD5** column, click the MD5 to view the Sandbox Detail Report for additional data from the analysis. If the file is clean, you won’t see a link.
If you don't see the **MD5** column, click the **Menu** icon at the top right-hand corner, and select **MD5** to add the column.