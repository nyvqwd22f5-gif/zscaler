# Obfuscating User Names for Admins
Source: https://help.zscaler.com/unified/obfuscating-user-names-admins
PDF: https://help.zscaler.com/pdf/com/en/1490781.pdf

You can specify whether real user names are visible or obfuscated for an admin when they view dashboards, reports, or insights. You can also obfuscate user names in NSS feeds. To learn more, see [Adding NSS Feeds for Web Logs](/unified/adding-nss-feeds-web-logs), [Adding NSS Feeds for Firewall Logs](/unified/adding-nss-feeds-firewall-logs), and [Adding NSS Feeds for DNS Logs](/unified/adding-nss-feeds-dns-logs).
Some regions have legal requirements that dictate that user names always remain obfuscated in reports and logs for admins. If admins need to view real user names, they must have an auditor grant them permission to do so. To learn more, see [About Auditors](/unified/about-auditors).
Prerequisites
To configure this setting for an admin account, your own admin account must meet the following conditions:
- Your admin account must have an admin role that has **Full** permission to **Administrators Access**. To learn more, see [Adding Admin Roles](/unified/adding-admin-roles).
- Your admin account must have organizational admin scope. To learn more, see [About Admin Scope](/unified/about-admin-scope).
- If your organization has the [admin rank](/unified/about-admin-rank) feature enabled, and you're configuring this setting for another admin account, that admin must have an admin rank lower than or equal to your own admin rank.
Obfuscating User Names for Admins
To obfuscate user names for an admin viewing dashboards, reports, and insights, you must enable user name obfuscation for the [role](/unified/adding-admin-roles) assigned to the admin. In other words, you must edit the admin role assigned to the admin account or create a new role.
To obfuscate user names for an admin, do one of the following:
- [Enable user obfuscation for an existing role.](#editroleenableobfusc)
- [Add a new admin role and account.](#new-admin-role-account)
- []Go to **Administration** > **Admin Management** >** Administrator Management **> **Internet Access Administrators**.
- On the **Administrators** page, in the **Role** column, check which admin role is assigned to admin you want to edit. Also, check which other admins have been assigned this specific role, and ensure you want user obfuscation enabled for those admins as well.
- Go to **Administration** > **Admin Management** > **Role Based Access Control** > **Internet & SaaS**.
- On the **Role Management** page, click the **Edit** icon next to the role assigned to the admin you're editing.
[See image.](#seeimg1)
The **Edit Administrator Role **window appears.
- In the **Edit Administrator Role **window, under **User Names**, choose **Obfuscated**.
[See image.](#seeimage2)
- Click **Save** to exit the window.
- Click** Save **and** **activate the change.
[]****![Screenshot of the Edit Administrator Role window showing how to change users from visible to obsfuscated](/downloads/zia/authentication-administration/administrator-role-management/obfuscating-user-names-admins/ZIA-6.1r-Ubfuscating-user-name-5.png)
****
[]![Screenshot showing how edit admin](/downloads/zia/authentication-administration/administrator-role-management/obfuscating-user-names-admins/ZIA-6.1r-Ubfuscating-user-name-4.png)
[]For convenience, Zscaler recommends creating the admin role first because you then assign the role to the new admin.
- [Add a new admin role with user obfuscation enabled.](/unified/adding-admin-roles)
- [Add a new admin account.](/unified/about-administrators)