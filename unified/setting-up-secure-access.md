# Setting up Secure Access
Source: https://help.zscaler.com/unified/setting-up-secure-access
PDF: https://help.zscaler.com/pdf/com/en/1486816.pdf

You can get started protecting your users quickly with Zscaler. Once you're set up, you'll be able to adjust your configuration as needed in the Admin Portal.
Before you begin, you must be logged in to an existing Zscaler account. To learn more, see [Signing in to the Admin Portal](/unified/signing-admin-portal).
Click the **Test Security** button to check the status of your current security configuration to understand your current vulnerabilities using Zscaler's [Internet Threat Exposure Analysis](http://securitypreview.zscaler.com/). You can return to this test after you have completed the onboarding process to see how you are protected.
To make your setup go as smoothly as possible, review the steps before beginning and make sure you have immediate access to all the information you will need, such as login information for your IdP.
You can click **Skip **to bypass all or part of the guided onboarding setup and go directly to the[ Experience Center home page](/unified/viewing-experience-center-home-page). You must then manually configure the skipped parts of the setup.
- [Step 1: Set up users.](#add-users)
- [Step 2: Set up traffic forwarding.](#traffic-forwarding)
- [Step 3: Set up security policies.](#policies)
- [Step 4: Fine-tune your security setup.](#refine-setup)
[]Click **Initiate Setup **to start adding users to be protected by Zscaler. You can repeat this process as many times as you need to from the Admin Portal.
To get started adding users, select one of the following:
- [Import users from your identity provider (IdP)](/unified/importing-users-idp)
- [Upload users from a comma-separated value (CSV) file](/unified/uploading-users-csv-file)
- [Add users manually](/unified/adding-users-manually)
During onboarding, you can assign users to one of two roles:
- **End User**: a regular user who does not require any administrator access. These users are assigned to the ZIdentity Dynamic Group Registered Domains group.
- **Full Admin**: an administrator with full access to add, edit, import, and delete users within the Admin Portal. These users are assigned to the ZIdentity Global Administrators group. This type of user is commonly called a super admin.
To learn more about ZIdentity groups, see [About User Groups](/zslogin/about-user-groups). If you want to change user roles before you complete onboarding, see [Editing Newly Onboarded Users](/unified/editing-newly-onboarded-users).
[]After you've added users to your setup, you'll send those users a link to install Zscaler Client Connector, an application that will ensure that all user traffic is protected with the security settings you decide. You can change these settings later if you need to.
Users must have administrator permissions on their devices that allow them to install applications.
To set up traffic forwarding:
- Click** Secure Setup** to specify the users you want to protect.
- On the **Clients **page, click the boxes for the applicable platforms for your users. Click **Next **to continue.
- On the **Traffic Forwarding** page, select whether your users currently connect to your organization via a VPN:
- If you're not using a VPN, select **No **and click **Next**.
- If you are using a VPN, select **Yes** and enter the IP addresses and hostnames for the VPN. Zscaler will ignore traffic to those addresses so that the VPN can continue to work. Click **Next **to continue.
- On the **Select Users for Zscaler Client Connector Distribution** page, select the users who you want to receive an email containing a link to download Zscaler Client Connector. You can check the box next to the **Name **heading to select all users. Click **Next **to continue.
- On the **Distribute Zscaler Client Connector Application** page:
- By default, users will receive automatic software updates to Zscaler Client Connector. Disable the toggle if you do not want users to receive automatic updates.
- Review the email that will be sent to the users you selected with links to install Zscaler Client Connector.
- Click **Finish **to send the email with installation links to your users.
[]The final step in securing your internet is defining the security policies for your organization.
Click **Set Up Policies** to start configuring the following types of security policies:
- [URL filtering](/unified/configuring-url-filtering): block, isolate, or allow internet destinations by URL category.
- [SSL inspection](/unified/configuring-ssl-inspection): configure what types of secure internet traffic (SSL) is inspected for added security.
- [Cyber threat protection](/unified/reviewing-cyber-threat-protection-policies): review additional protection policies for cyber threats, such as botnets, phishing, and malware.
- [Data protection](/unified/reviewing-data-protection-policies): review data protection policies that ensure sensitive data is not inadvertently leaked via email, social media, file sharing, or other means.
- [Privacy](/unified/configuring-user-privacy): configure how you protect your users' personally identifiable information (PII).
You can also configure the following settings:
- [Block countries](/unified/configuring-blocked-countries): block internet traffic from specific countries
- [Add your company logo to banners, emails, and notifications](/unified/adding-your-company-logo): add your company logo to banners, emails, and user notifications sent from Zscaler
When you have finished defining your initial policy configuration, click **Activate & Launch** to enable the policies you have selected and launch the Admin Portal.
[]When you complete the steps above, your organization's initial security configuration and access to the internet is complete and the [Networking dashboard](/unified/viewing-networking-dashboard) in the Admin Portal is displayed by default.
From the Admin Portal, you have full access to all Zscaler capabilities, such as fine-tuning security policies, [viewing analytics](/unified/signing-admin-portal#analytics), extending security to other SaaS and private applications and more. To learn more, see [Navigating within the Admin Portal](/unified/signing-admin-portal#navigating-admin-portal).