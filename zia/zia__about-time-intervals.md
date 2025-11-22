# About Time Intervals
Source: https://help.zscaler.com/zia/about-time-intervals
PDF: https://help.zscaler.com/pdf/com/en/1399151.pdf

[Watch a video about Time Intervals.](https://fast.wistia.net/embed/iframe/5216rd7peb)
You can define time intervals for use in policies. For example, if you want to block users from accessing shopping sites from 8:00 AM to 5:00 PM on weekdays, you can create a time interval called Weekdays that includes Monday through Friday from 8:00 AM to 5:00 PM.
When an organization creates time bound policies, policy behavior might differ between users. If the user is coming from a known location, the policy is applied based on the time zone configured for their location. If the user is a remote user (including users using Zscaler Client Connector), the policy is applied according to the time at the ZIA Public Service Edge they are connected to.
Consider the following example, an organization has a URL filtering policy using a time interval. This policy set to block the Social Networking [URL category](/zia/about-url-categories) Monday through Friday from 9:00 AM - 5:00 PM.
A user tries to access facebook.com through a ZIA Public Service Edge in the Paris data center. They come from a known location with the time zone configured as Europe/London on Tuesday at 5:30 PM. London time. [See image.](#seeimage1) This user is blocked from going to the site even though the time in Paris at that point in time is 6:30 PM. The reason for this behavior is because the ZIA Public Service Edge uses the time zone of the configured location for policy execution.
Consider another user, who is also in London and generates traffic through the Paris data center. This user is not from a known location, they are a remote user. They also try to go to Facebook at the same time.
This remote user is allowed to access Facebook. The reason for this behavior is that, though the user is located in London and the time in London is 5:30 PM, there is no location configured for remote users. Therefore, the ZIA Public Service Edge’s time zone is used for policy execution. Because the ZIA Public Service Edge used is in Paris and the time in Paris is 6:30 PM, the policy would not be triggered.
About the Time Intervals Page
On the **Time Intervals** page:
- [Define a new time interval](/zia/how-do-i-define-time-intervals).
- View a list of all configured time intervals:
- **Name:** The name of the time interval. You can sort this column.
- **Timeframe:** The days of the week and the time of day.
- Search for a configured time interval.
- [Edit a time interval](/zia/how-do-i-edit-delete-or-duplicate-items-admin-portal).
- [Modify the table and its columns](/zia/how-do-i-use-tables-admin-portal).
![Screenshot of the Zscaler Time Intervals page and tasks](/downloads/zia/documentation-knowledgebase/policies/about-time-intervals/zia-5.7-time-intervals.png)
[]![Screenshot of a location in London](/downloads/zia/documentation-knowledgebase/creating-and-managing-policies/about-policies/about-time-intervals/zia-london-location.png)