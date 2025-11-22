# About Sandbox End User Notifications
Source: https://help.zscaler.com/unified/about-sandbox-end-user-notifications
PDF: https://help.zscaler.com/pdf/com/en/1494366.pdf

When [configuring](/unified/configuring-sandbox-policy) the Sandbox policy, you can choose the action the Sandbox takes when users download a file. Depending on the following action you choose, your users may see a particular end user notification (EUN).
- [Allow](#sandbox-allow-notification)
- [Quarantine](#sandbox-quarantine-notification)
- [Block](#sandbox-block-notification)
To learn about the recommended Sandbox actions, see [Recommended Sandbox Policy](/unified/recommended-sandbox-policy).
- []If you choose **Allow** for **Action for Subsequent Downloads**, users can download a file if it's known to be malicious, and no EUN is displayed.
- If you choose **Allow and do not scan** for **First-Time Action**, users can download an unknown file, and it's not sent for behavioral analysis. No EUN is displayed.
- If you choose **Allow and scan **for **First-Time Action**, users can download an unknown file, and it's sent for behavioral analysis. No EUN is displayed.
[]If your organization has Advanced Sandbox, you can add rules to the Sandbox policy and choose **Quarantine** for **First-Time Action**. When a user attempts to download an unknown file, the Zscaler service quarantines the file and then sends it to the Sandbox for analysis. The service also displays the following quarantine notification for the user:
****![Screenshot of the Sandbox quarantine end user notification (EUN)](/downloads/zia/policies/sandbox/about-sandbox-end-user-notifications/quarantine-eun.png)
****
You can customize this quarantine notification on the End User Notifications page. To learn more, see [Configuring the Quarantine Notification](/unified/configuring-quarantine-notification).
The Sandbox analysis may take a few minutes depending on the size and type of the file. If the file is safe, the download begins automatically. If the file is unsafe, then based on your configured Sandbox policy, the download might be blocked.
If a user manually refreshes this page or the service automatically refreshes it, a new quarantine transaction log is created for the file. However, the wait time for the Sandbox analysis isn't affected.
[]If you choose **Block** for **Action for Subsequent Downloads**, users are unable to download the file if it's known to be malicious, and the block EUN is displayed:
****![Screenshot of the Sandbox block end user notification (EUN)](/downloads/zia/documentation-knowledgebase/creating-and-managing-policies/sandbox/configuring-sandbox/sandbox-end-user-notifications-euns/zia-sandbox-block-notification.png)
****
You can customize this block notification on the End User Notifications page under Security Violation Notifications. To learn more, see [Configuring Block Notifications](/unified/configuring-block-notifications).