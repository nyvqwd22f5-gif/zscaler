# Obfuscating User Names for Admins
Source: https://help.zscaler.com/zia/obfuscating-user-names-admins
PDF: https://help.zscaler.com/pdf/com/en/1399736.pdf

You can specify whether real user names are visible or obfuscated for an admin when they view dashboards, reports, or insights. You can also obfuscate user names in NSS feeds. To learn more, see [Adding NSS Feeds for Web Logs](/zia/adding-nss-feeds-web-logs), [Adding NSS Feeds for Firewall Logs](/zia/adding-nss-feeds-firewall-logs), and [Adding NSS Feeds for DNS Logs](/zia/adding-nss-feeds-dns-logs).
Some regions have legal requirements that dictate that user names always remain obfuscated in reports and logs for admins. If admins need to view real user names, they must have an auditor grant them permission to do so. To learn more, see [About Auditors](/zia/about-auditors).
Prerequisites
To configure this setting for an admin account, your own admin account must meet the following conditions:
- Your admin account must have an admin role that has **Full** permission to **Administrators Access**. To learn more, see [Adding Admin Roles](/zia/adding-admin-roles).
- Your admin account must have [organizational admin scope](/zia/adding-admins). To learn more, see [About Admin Scope](/zia/about-admin-scope).
- If your organization has the [admin rank](/zia/about-admin-rank) feature enabled, and you're configuring this setting for another admin account, that admin must have an admin rank lower than or equal to your own admin rank.
Obfuscating User Names for Admins
To obfuscate user names for an admin viewing dashboards, reports, and insights, you must enable user name obfuscation for the [role](/zia/adding-admin-roles) assigned to the admin. In other words, you must edit the admin role assigned to the admin account or create an new role.
To obfuscate user names for an admin, do one of the following:
- [Assign the admin an existing role with user obfuscation enabled](#assignadmindiffrole)
- [Enable user obfuscation for an existing role](#editroleenableobfusc)
- [Add a new role with user obfuscation enabled and assign it to the admin](#createnewrole)
- [Add a new admin role and account](#new-admin-role-account)
- []Go to **Administration** > **Role Management**.
- In the **User Names** column, check which existing admin roles have user names **Obfuscated**. Ensure that all other permission settings for the existing admin role are appropriate for the admin you want to assign this role to.
[See image.](#seeimage00)
- Go to** Administration **>** ****Administrator Management**.
- Click the **Edit** icon next to the admin you want to enable user name obfuscation.
[See image.](#seeimage0)
The **Edit Administrator **window appears.
- In the **Edit Administrator **window, under **Role**, choose the appropriate admin role with user obfuscation enabled. In this example, it's HR-Access Control.
[See image.](#seeimage1)
- Click **Save** to exit the window.
- Click **Save** and [activate the change](/zia/saving-and-activating-changes-admin-portal).
[]![Screenshot showing visible and obfuscated user names in the Role Management window ](/downloads/zia/authentication-administration/administrator-role-management/obfuscating-user-names-admins/ZIA-6.1r-Ubfuscating-user-name-1.png)
[]![Screenshot showing the edit button in the Administrator Management section](/downloads/zia/authentication-administration/administrator-role-management/obfuscating-user-names-admins/ZIA-6.1r-Ubfuscating-user-name-2.png)
[]**![Screenshot of the Edit Administrator window showing how to select admin rule](/downloads/zia/authentication-administration/administrator-role-management/obfuscating-user-names-admins/ZIA-6.1r-Ubfuscating-user-name-3.png)
**
- []Go to** Administration **>** ****Administrator Management**.
- In the **Role** column, check which admin role is assigned to admin you want to edit. Also, check which other admins have been assigned this specific role, and ensure you want user obfuscation enabled for those admins as well.
- Go to **Administration **>** ****Role Management**.
- Click the **Edit** icon next to the role assigned to the admin you're editing.
[See image.](#seeimg1)
The **Edit Administrator **window appears.
- In the **Edit Administrator Role **window, under **User Names**, choose **Obfuscated**.
[See image.](#seeimage2)
- Click **Save** to exit the window.
- Click** Save **and** **[activate the change](/zia/saving-and-activating-changes-admin-portal).
[]**![Screenshot of the Edit Administrator Role window showing how to change users from visible to obsfuscated](/downloads/zia/authentication-administration/administrator-role-management/obfuscating-user-names-admins/ZIA-6.1r-Ubfuscating-user-name-5.png)
**
[]![Screenshot showing how edit admin](/downloads/zia/authentication-administration/administrator-role-management/obfuscating-user-names-admins/ZIA-6.1r-Ubfuscating-user-name-4.png)
- []Go to** Administration **>** ****Administrator Management**.
- Click the **Edit** icon next to the admin you want to enable user name obfuscation.
[See image.](#seeimage000)
- Under **Role**, click the **Add** icon.
[See image.](#seeimage3)
The **Add Administrator Role** window appears.
- In the **Add Administrator ****Role **window, follow [the instructions for adding a new admin role](/zia/adding-admin-roles), including how to enable user name obfuscation.
- In the **Edit Administrator **window, choose your new admin role.
- Click **Save** to exit the window.
- Click** Save **and** **[activate the change](/zia/saving-and-activating-changes-admin-portal).
[]![Screenshot showing the edit button in the Administrator Management section](/downloads/zia/authentication-administration/administrator-role-management/obfuscating-user-names-admins/ZIA-6.1r-Ubfuscating-user-name-2.png)
[]**![Screenshot showing how to add a new administrator with obsfuscation](/downloads/zia/authentication-administration/administrator-role-management/obfuscating-user-names-admins/ZIA-6.1r-Ubfuscating-user-name-6.png)
**
[]For convenience, Zscaler recommends creating the admin role first because you'll assign the role to the new admin.
- [Add a new admin role with user obfuscation enabled](/zia/adding-admin-roles)
- [Add a new admin account](/zia/adding-admins)