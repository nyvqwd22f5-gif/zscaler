# Accessing Multiple Sessions In Isolation
Source: https://help.zscaler.com/isolation/accessing-multiple-sessions-isolation
PDF: https://help.zscaler.com/pdf/com/en/1417561.pdf

[Watch a video about accessing multiple sessions in Isolation.](https://fast.wistia.net/embed/iframe/fdy8wmrk1q)
Users can access multiple active isolation sessions at a time per device, per internet browser. For example, if a user begins an isolation session in a Chrome browser window, they can start an additional isolation session for a different web page in a Firefox browser window.
To access another isolation session using the same type of browser, an incognito mode window is required. For example, if you have a Chrome browser window open with an isolation session, opening a second Chrome browser window continues that same isolation session.
If the [Zscaler Internet Access (ZIA)](/isolation/creating-isolation-profiles-zia) or [Zscaler Private Access (ZPA)](/isolation/creating-isolation-profiles-zpa) isolation profile has the Cookie Persistence setting enabled in Security Controls, then the cookies migrate from existing or previous sessions to new sessions. However, this only applies to the browser window type. So, existing isolation sessions in Chrome browsers share cookie data with additional isolation sessions in Chrome browsers, but cannot migrate the data to additional isolated sessions in Firefox browser windows.
There is a limit of 10 active sessions per user at a time. To learn more, see [Ranges & Limitations](/isolation/ranges-limitations).