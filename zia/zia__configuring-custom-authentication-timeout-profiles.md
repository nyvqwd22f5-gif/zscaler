# Configuring Custom Authentication Timeout Profiles
Source: https://help.zscaler.com/zia/configuring-custom-authentication-timeout-profiles
PDF: https://help.zscaler.com/pdf/com/en/1457561.pdf

By default, the authentication timeout is shared across all locations; however, you can create and assign custom authentication timeout profiles to locations in your organization. You can create a maximum of 8 profiles, and assign each profile to any number of locations. To learn more, see [About Authentication Profiles](/zia/about-authentication-profiles).
This feature is in limited availability. To access this feature, contact your Zscaler Account Team.
Creating Custom Authentication Profiles
To create an authentication profile:
- Go to **Administration** > **Authentication Settings** > **Authentication Profiles**.
- Click **Add Authentication Profile**.
The **Add Authentication Profile **window appears.
- In the **Add Authentication Profile **window:
- **Name**: Enter a name for the profile.
- **Custom Authentication Frequency**: Enter a number to determine the frequency of the timeout depending on the interval.
- **Interval**: Choose either minutes, hours, or days.
The minimum frequency is 5 minutes and the maximum is 999 days. Zscaler recommends a frequency of 30 minutes or higher for a better user experience.
- Click **Save **and [activate the change](/zia/saving-and-activating-changes-admin-portal).
Assigning Custom Authentication Profiles to Locations
To assign a custom authentication profile to a location:
- Go to **Administration** >** Location Management**.
- Select the location you wish to assign the profile to from the list or use the search bar.
- Click the **Edit **icon for the location.
The **Edit Location **window appears.
- In the **Gateway Options **section, select an **A****uthentication Profile **from the drop-down menu.
- Click **Save **and [activate the change](/zia/saving-and-activating-changes-admin-portal).