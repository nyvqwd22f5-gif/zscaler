# Understanding Browser-Based End User Notifications
Source: https://help.zscaler.com/unified/understanding-browser-based-end-user-notifications
PDF: https://help.zscaler.com/pdf/com/en/1493031.pdf

In the Admin Portal, you can configure different types of browser-based EUNs:
- [Block Notification](#block-notification)
- [Acceptable Use Policy (AUP)](#AUP-notification)
- [Caution Notification](#caution-notification)
- [Quarantine Notification](#quarantine-notification)
The Zscaler service supports [multiple languages](/unified/multiple-language-support-euns) for these notifications. You can also customize the appearance of the EUNs with CSS styles, HTML tags, and JavaScript. To learn more, see [Customizing the EUNs with CSS Styles](/unified/customizing-euns-css-styles).
[]This section provides an overview of the steps involved in configuring block notifications. For instructions on how to configure the individual steps, see [Configuring Block Notifications](/unified/configuring-block-notifications).
- [Configure the general settings for all block notifications.](#general-block-setting)
- [Configure the block notification for URL categorization.](#block-url-caegorizaion)
- [Configure the block notification for Security Violation.](#block-security-violation)
- [Configure the block notification for Web DLP Violation.](#block-web-dlp-violation)
- [Configure the IDP Proxy notification.](#IDP-proxy-notification)
- [Configure the contact information of your organization's IT support team for all block notifications.](#block-it-contact)
- [Preview the block EUNs.](#block-EUN-preview)
[]To display the AUP notification, users should be authenticated. However, for locations or sub-locations that do not have authentication enforced, you can still enable AUP and configure the notification frequency (in days) using the corresponding settings on the Location or the Sub-Location page. To learn more, see [Configuring Locations](/unified/configuring-locations#EnableAUP) and [Configuring Sub-Locations](/unified/configuring-sub-locations#EnableAUP).
- [Configure the AUP.](#configure-aup)
- [Configure the contact information of your organization's IT support team for AUP.](#aup-it-contact)
- [Preview the AUP.](#aup-EUN-preview)
[]This section provides an overview of the steps involved in configuring block notifications. For instructions on how to configure the individual steps, see [Configuring the Caution Notification](/unified/configuring-caution-notification).
- [Configure the general settings for the caution notification.](#general-caution-settings)
- [Configure the caution notification text.](#configure-caution)
- [Configure the contact information of your organization's IT support team for the caution notification.](#caution-it-contact)
- [Preview the caution EUN.](#caution-EUN-preview)
[]This section provides an overview of the steps involved in configuring block notifications. For instructions on how to configure the individual steps, see [Configuring the Quarantine Notification](/unified/configuring-quarantine-notification).
- [Configure the general settings for the quarantine notification.](#quarantine-notification-general-settings)
- [Configure the quarantine notification text.](#quarantine-notification-text)
- [Configure the contact information of your organization's IT support team for the quarantine notification.](#it-support-details-quarantine-notification)
[]![Screenshot of IDP Proxy Notification on the EUN Page.](/downloads/zia/documentation-knowledgebase/authenticating-and-managing-users/user-aup-and-notifications/configuring-user-notifications/about-acceptable-use-policy-and-end-user-notifications/ZIA-IDP-Proxy-Notification-Configuration.png)
[]Notification settings such as **Display Reason**, **Display Company Name**, and **Display Company Logo** are common for block, caution, and quarantine notifications.
![A screenshot of the general settings of the block notifications](/downloads/zia/authentication-administration/end-user-notifications/configuring-end-user-notifications/ZIA-Block-Configure-Notification.png)
[]![Screenshot of the URL Categorization notification configuration on the End User Notification page.](/downloads/zia/documentation-knowledgebase/authenticating-and-managing-users/user-aup-and-notifications/configuring-user-notifications/about-acceptable-use-policy-and-end-user-notifications/ZIA-Block-Notification-URL-Categorization.png?1629978293)
[]![Screenshot of the Security Violation notification configuration on the End User Notification page.](/downloads/zia/documentation-knowledgebase/authenticating-and-managing-users/user-aup-and-notifications/configuring-user-notifications/about-acceptable-use-policy-and-end-user-notifications/ZIA-Block-Notification-Security-Violation.png?1629978788)
[]![Screenshot of the Web DLP Violation notification configuration on the End User Notification page.](/downloads/zia/documentation-knowledgebase/authenticating-and-managing-users/user-aup-and-notifications/configuring-user-notifications/about-acceptable-use-policy-and-end-user-notifications/ZIA-Block-Notification-Web-DLP-Violation.png?1629978824)
[]![Screenshot of the IT Support contact configuration on the End User Notification page.](/downloads/zia/documentation-knowledgebase/authenticating-and-managing-users/user-aup-and-notifications/configuring-user-notifications/about-acceptable-use-policy-and-end-user-notifications/ZIA-Block-Notification-IT-Support-Contact.png?1629978860)
[]![Screenshot of the EUN Preview button on the End User Notification page.](/downloads/zia/documentation-knowledgebase/authenticating-and-managing-users/user-aup-and-notifications/configuring-user-notifications/about-acceptable-use-policy-and-end-user-notifications/ZIA-Block-EUN-Preview.png?1629978904)
[]![Screenshot of AUP configuration on the End User Notifications page.](/downloads/zia/documentation-knowledgebase/authenticating-and-managing-users/user-aup-and-notifications/configuring-user-notifications/about-acceptable-use-policy-and-end-user-notifications/ZIA-AUP-Notification-Configuration.png)
[]![Screenshot of the IT Support contact configuration on the End User Notification page.](/downloads/zia/documentation-knowledgebase/authenticating-and-managing-users/user-aup-and-notifications/configuring-user-notifications/about-acceptable-use-policy-and-end-user-notifications/ZIA-AUP-IT-Support-Contact.png)
[]![Screenshot of the AUP Preview button on the End User Notification page.](/downloads/zia/documentation-knowledgebase/authenticating-and-managing-users/user-aup-and-notifications/configuring-user-notifications/about-acceptable-use-policy-and-end-user-notifications/ZIA-AUP-EUN-Preview.png)
[]Notification settings such as **Display Reason**, **Display Company Name**, and **Display Company Logo** are common for block, caution, and quarantine notifications.
![Screenshot of general Caution settings on the EUN page.](/downloads/zia/documentation-knowledgebase/authenticating-and-managing-users/user-aup-and-notifications/configuring-user-notifications/about-acceptable-use-policy-and-end-user-notifications/ZIA-General-Setting-Caution-Notification.png)
[]![Screenshot of Caution configuration on the EUN page.](/downloads/zia/documentation-knowledgebase/authenticating-and-managing-users/user-aup-and-notifications/configuring-user-notifications/about-acceptable-use-policy-and-end-user-notifications/ZIA-Caution-Notification-Configuration.png)
[]![Screenshot of the IT Support contact configuration on the End User Notification page.](/downloads/zia/documentation-knowledgebase/authenticating-and-managing-users/user-aup-and-notifications/configuring-user-notifications/about-acceptable-use-policy-and-end-user-notifications/ZIA-Caution-Notification-IT-Support-Contact.png)
[]![Screenshot of the Caution EUN Preview button on the End User Notification page.](/downloads/zia/documentation-knowledgebase/authenticating-and-managing-users/user-aup-and-notifications/configuring-user-notifications/about-acceptable-use-policy-and-end-user-notifications/ZIA-Caution-EUN-Preview.png)
[]Notification settings such as **Display Reason**, **Display Company Name**, and **Display Company Logo** are common for block, caution, and quarantine notifications.
![A screenshot of the general settings of the quarantine notification](/downloads/zia/authentication-administration/end-user-notifications/configuring-end-user-notifications/quarantine-notification-general-settings.png)
[]![A screenshot of the quarantine notification text customization window](/downloads/zia/authentication-administration/end-user-notifications/configuring-end-user-notifications/quarantine-notification-text.png)
[]![A screenshot of the IT support fields in the end user notification](/downloads/zia/authentication-administration/end-user-notifications/configuring-end-user-notifications/IT-support.png)