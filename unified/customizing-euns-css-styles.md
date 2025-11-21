# Customizing EUNs with CSS Styles
Source: https://help.zscaler.com/zia/customizing-euns-css-styles
PDF: https://help.zscaler.com/pdf/com/en/1399641.pdf

The Zscaler service provides notification templates for the [Acceptable Use Policy (AUP)](/zia/configuring-acceptable-use-policy), [caution notification](/zia/configuring-caution-notification), [quarantine notification](/zia/configuring-quarantine-notification), and three different [block notifications](/zia/configuring-block-notifications) (URL Categorization, Security Violation, and Web DLP Violation). The end user notifications (EUNs) are made up of a number of discrete table rows and columns. Each row uses a CSS style to control the properties of the row. On the [Global Configuration page](/zia/about-acceptable-use-policy-and-end-user-notifications), there are message or text fields where you can enter CSS styles to modify the look of these notifications. You can change various properties and customize the appearance of the notifications, such as fonts, colors, borders, and dimensions, with CSS styles, HTML tags, and JavaScript.
The Zscaler service also supports multiple languages for these notifications. To learn more, see [Multiple Language Support for EUNs](/zia/multiple-language-support-for-euns).
This article describes the styles used in EUNs, and how you can use them to customize the appearance of EUNs with the various rows and their classes.
CSS style and JavaScript do not render when previewing EUN templates.
About CSS Styles
The following are the names of the CSS classes used to control the properties of the rows in a notification. You can use them to customize the appearance of EUNs.
[See image.](#cssclasses)
Zscaler Support uses the class `uq_cd` to identify EUNs. Zscaler strongly recommends you don't modify the class.
| CSS Class | Description |
| --------- | ----------- |
| `bh` | box header |
| `eu_co rsn` | reason |
| `eu_co` | EUN content |
| `eu_co ln` | link |
| `eu_co fo` | footer |
| `s_img` | static image |
| `red` | background |
| `eu_h` | EUN header |
| `btn` | button |
| `uq_cd` | unique code |
| `eu_co st` | static text |
Customizing EUNs With CSS Styles
The following are example configurations of CSS styles that you can use to change the appearance of EUNs.
- [Hiding Rows](#hiding-rows)
- [Hiding the Header](#hiding-header)
- [Hiding Footers](#footers)
- [Changing the Background Color](#background-color)
- [Changing the Size Limit](#size-limit)
- [Displaying a Timestamp](#timestamp)
[]Enter the following CSS style in the notification text or message field to hide a row that appears in an EUN:
<style>
.eu_co {
visibility:hidden;
}
</style>
![Screenshot of the CSS style used to hide a row in an EUN.](/downloads/zia/authentication-administration/end-user-notifications/customizing-euns-css-styles/ZIA-Web-DLP-Violation-Notification-Text.png)
In this example, the CSS style hides the EUN content in the Web DLP Violation notification.
![Screenshot showing before and after effects hiding a row using CSS style.](/downloads/zia/authentication-administration/end-user-notifications/customizing-euns-css-styles/ZIA-Deny-DLP-Hide-Row.png)
[]Enter the following CSS style in the notification text or message field to hide the header row that appears in an EUN:
`<style>
.eu_h {
font-size: 0;
}
.eu_h i {
display: none;
}
hr:first-of-type {
display: none;
}
</style>`
![Screenshot of the CSS style used to hide the EUN header.](/downloads/zia/authentication-administration/end-user-notifications/customizing-euns-css-styles/ZIA-URL-Categorization-Notification-Text.png)
In this example, the CSS style hides the header row in the URL Categorization notification.
![Screenshot showing the before and after effects of hiding the heading with CSS style..](/downloads/zia/authentication-administration/end-user-notifications/customizing-euns-css-styles/ZIA-Deny-URL-Category-Hide-Header.png)
[]All notification templates have two footers. One footer provides contact information for your IT Support. The other footer includes the Zscaler logo and a message by default.
- [Hide the IT Support Footer](#it-support-footer)
- [Hide the Zscaler Footer](#zscaler-footer)
[]To hide the IT Support** **footer, use the class `eu_co.fo` and enter the following CSS style in the notification text or message field.
<style>
.eu_co.fo {
font-size: 0;
}
.eu_co.fo i {
display: none;
}
hr:first-of-type {
display: none;
}
</style>
![Screenshot of the CSS style used to hide the IT Support footer](/downloads/zia/authentication-administration/end-user-notifications/customizing-euns-css-styles/ZIA-Security-Violation-Notifications-Text.png)
In this example, the CSS style hides the IT Support footer in the Web DLP Violation notification.
![Screenshot showing the before and after effects of hiding the IT support footer with CSS style.](/downloads/zia/authentication-administration/end-user-notifications/customizing-euns-css-styles/ZIA-EUN-Hide-IT-Support-Footer.png)
[]The Zscaler footer is divided into two sections. The logo uses the class `s_img`, and the message uses the class name `eu_co` st.
To hide the footer in a template, enter the following CSS style in the notification text or message field:
<style> .eu_co.st {display: none;} .s_img {display:none;} </style>
![Web DLP notification configuration](/downloads/zia/authentication-administration/end-user-notifications/customizing-euns-css-styles/web-dlp.png)
In this example, the CSS style hides the Zscaler footer in the Web DLP Violation notification.
![Hide footer in DLP notification](/downloads/zia/authentication-administration/end-user-notifications/customizing-euns-css-styles/dlp-hide-footer.png)
[]To change the background color of a notification, you must know the CSS class name of the notification's background. The background of each template is styled with a default color and uses the following CSS classes:
- The Acceptable Use Policy template uses green and class gr.
[See image.](#green)
- The caution template uses yellow and class yl.
[See image.](#yellow)
- The block template uses red and class red.
[See image.](#red)
- The quarantine template uses orange and class `or`.
[See image.](#quarantine-eun)
To change the background of a template to another color, enter the CSS class name of the template's background in the CSS style:
<style> .red {background-color:lightblue;} .yl {background-color:lightblue;} .bh {background-color:lightblue;} .eu_co.st {background-color:lightblue;} </style>
![Template color change in caution notification](/downloads/zia/authentication-administration/end-user-notifications/customizing-euns-css-styles/caution-css.png)
In this example, the CSS style changes the caution notification background to light blue.
![Image showing the effects of changing the background to light blue](/downloads/zia/documentation-knowledgebase/authenticating-and-managing-users/user-aup-and-notifications/knowledge-base/customizing-aup-and-euns-css-styles/prior_and_after_changing_background_color.png)
[]By default, a notification occupies 90% of your browser's width and has a maximum width of 790 pixels.
To change the size limit of the AUP and EUNs, enter the following CSS style:
<style> .m_tbl {width: 75%;max-width: 500px;} </style>
![Size limit change in caution notification](/downloads/zia/authentication-administration/end-user-notifications/customizing-euns-css-styles/caution-size-limit.png)
In this example, the CSS style changes the caution notification to occupy 75% of your browser's width and has a maximum width of 500 pixels.
![Example showing the effects of using CSS to change the notification size of EUN and AUP](/downloads/zia/documentation-knowledgebase/authenticating-and-managing-users/user-aup-and-notifications/knowledge-base/customizing-aup-and-euns-css-styles/prior_and_after_changing_the_notification_size.png)
[]To display a timestamp on the EUN, enter the following code:
<br><font size=-2>
<script type="text/javascript">
var e = Date.now();
var d = new Date(e);
document.write(d);
</script>
</font>
![Time display in URL notification](/downloads/zia/authentication-administration/end-user-notifications/customizing-euns-css-styles/url-notification-time-display.png?1652369444)
In this example, The CSS style displays a current date and time for the URL Categorization notification.
![Screenshot showing a notification that now has a timestamp](/downloads/zia/documentation-knowledgebase/authenticating-and-managing-users/user-aup-and-notifications/knowledge-base/how-do-i-customize-end-user-notifications-display-timestamp/notification_with_timestamp.png)
[]![Names of the CSS classes with arrows pointing to the properties of the rows they control](/downloads/zia/documentation-knowledgebase/authenticating-and-managing-users/user-aup-and-notifications/knowledge-base/customizing-aup-and-euns-css-styles/various_css_classes.png)
[]![Screenshot showing that the Acceptable Use Policy template uses green](/downloads/zia/documentation-knowledgebase/authenticating-and-managing-users/user-aup-and-notifications/knowledge-base/customizing-aup-and-euns-css-styles/green_acceptable_use_policy.png)
[]![Screenshot showing the caution template uses yellow](/downloads/zia/documentation-knowledgebase/authenticating-and-managing-users/user-aup-and-notifications/knowledge-base/customizing-aup-and-euns-css-styles/yellow_caution_template.png)
[]![Screenshot showing that the block template uses red](/downloads/zia/documentation-knowledgebase/authenticating-and-managing-users/user-aup-and-notifications/knowledge-base/customizing-aup-and-euns-css-styles/red_block_template.png)
[]![A screenshot of the quarantine end user notification](/downloads/zia/authentication-administration/end-user-notifications/customizing-euns-css-styles/quarantine-eun.png)