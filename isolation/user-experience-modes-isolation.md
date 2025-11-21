# User Experience Modes in Isolation
Source: https://help.zscaler.com/isolation/user-experience-modes-isolation
PDF: https://help.zscaler.com/pdf/com/en/1386596.pdf

[Watch a video about user experience modes in Isolation.](https://fast.wistia.net/embed/iframe/l066po6aes)
Isolation allows admins to select an isolation browser experience for their ZIA and ZPA users. The two options are Native Browser Experience and Browser-in-Browser Experience.
Native Browser Experience
Native Browser Experience is a way for users to benefit from the security of Isolation while keeping the look and feel of their original browser window. For example, the Isolation Menu and other session controls are hidden from view when a user enters the isolated session, which gives users a more typical web browsing experience. Though the Isolation Menu is hidden from view by default, it is still accessible by navigating to the [Isolation Bar](/isolation/using-isolation-bar-native-browser-experience). Other isolation features, such as tab affinity, are also disabled by default, but can still be accessed in this mode. To learn more, see [Using the Isolation Bar in Native Browser Experience](/isolation/using-isolation-bar-native-browser-experience).
[See image.](#Native-Browser-UX)
Browser-in-Browser Experience
Browser-in-Browser Experience presents the isolation window in addition to the user's original browser window that contains it. In this mode, the user can see all elements of the native browser window, as well as the isolation browser window controls. The isolation URL can be copied, reloaded, and manually edited in this mode. When the Isolation session is initiated, the user sees the address bar of the isolation browser and the additional menus and controls provided by Isolation. In this mode, the URL bar is editable, allowing the user to input the URL of their choice and browse to the desired web page if allowed by the defined policy.
Another feature when using this mode is tab affinity. This means that the tabs opened for one isolation session cannot be carried over to a separate browser window, even if it is another isolated session. Each tab only corresponds with the native browser from which it came.
In Browser-in-browser experience mode, each tab on the native browser is mapped to a tab on the isolation browser. When a user is in an isolation session initiated with browser-in-browser mode, the user cannot see multiple tabs of the isolation browser displayed in the single native browser window. If a user opens a new tab in the isolation browser, a new tab on the native browser is launched, providing access to the new tab on the isolation container.
[See image.](#B-in-B-UX)
Selecting an Isolation Experience for Users
Admins can choose the isolation experience for users within individual isolation profiles. This option is available when [creating](/isolation/creating-isolation-profiles-zia) and [editing](/isolation/editing-your-isolation-profile-zia) ZIA iIsolation profiles, as well as when [creating](/isolation/creating-isolation-profiles-zpa) and [editing](/isolation/editing-your-isolation-profile-zpa) ZPA Isolation profiles.
[See image.](#Edit-Isolation-Profile-UX)
![Native Browser Experience mode view](/downloads/zscaler-tech-pubs-style-guide/draft-articles/user-experience-modes-cloud-browser-isolation/Native-Browser-Experience_3.png)
[]
![Browser-in-browser experience mode view](/downloads/tech-pubs-drafts/isolation-draft-articles/user-experience-modes-cloud-browser-isolation-draft/Browser-in-browser_mode_editbale-URL_squircle.png)
[]
![Edit Isolation User Experience for a user profile](/downloads/tech-pubs-drafts/isolation-draft-articles/user-experience-modes-cloud-browser-isolation-draft/Select-isolation-experience.png)
[]