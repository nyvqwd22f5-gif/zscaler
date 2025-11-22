# Configuring the Default Authentication Profile
Source: https://help.zscaler.com/unified/configuring-default-authentication-profile
PDF: https://help.zscaler.com/pdf/com/en/1491251.pdf

In the Authentication Profile section on the Default Settings page in the Admin Portal, you can configure the Authentication Frequency.
To configure the default authentication profile:
- Go to **Administration** > **Identity** > **Internet & SaaS** > **Internet Authentication Settings**.
-
From the **Authentication Frequency**, choose how often users are required to authenticate to the Zscaler service.
- **Daily**:** **Authentication expires between 12 and 24 hours from the login time, depending on the time the user authenticated the day before.
-
**Only Once**: This is the default authentication interval. After users have logged in, they do not need to authenticate again as long as the [cookie](/unified/about-zscaler-cookies) is saved in the browser or as an Adobe Flash object. (Typically, the cookie expires in about two years.) However, to log out of Zscaler, users must log out of the service explicitly or delete the cookie from their browser.
Zscaler recommends choosing **Only Once **as your authentication frequency. To learn more, see [About User Authentication Frequency](/unified/about-user-authentication-frequency).
- **Once Per Session**:** **Authentication expires after the user closes the browser.** **In this case, no cookie is saved.
- **Custom**:** **Customize your authentication interval.
- **Custom Authentication Frequency (days)**:** **Enter the number of days, between 1 and 180 inclusive. Authentication is requested when the user's cookie expires.
These options don't apply to users with the Zscaler Client Connector feature.