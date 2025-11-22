# Removing Disabled Users in the Active Directory from the Zscaler User Database
Source: https://help.zscaler.com/zia/removing-disabled-users-active-directory-zscaler-user-database
PDF: https://help.zscaler.com/pdf/com/en/1399621.pdf

When users are marked disabled in the Active Directory (AD) server, they are still returned by the AD server when you use the following filters to synchronize users from the Active Directory server:
- **User Search Filter**
(objectClass=person)
- **Search Filter**
(objectClass=User)
As a result, users who were disabled in the AD aren't deleted from the Zscaler user database. Their cookies remain valid, allowing them to use the Zscaler service to browse the Internet.
Removing Disabled Users in the Active Directory
To make sure disabled users cannot browse through the Zscaler service, you need to specify a special LDAP search filter in the **User Search Filter** and **Search Filter** fields. This LDAP search filter instructs the AD to return all objects except those that have been disabled.
To modify these filters and remove disabled users from the AD:
- Go to **Administration **>** Authentication Settings**.
- In the **Authentication Profile** tab, under **Directory Type**, click **Advanced Configuration**.
- Add the following value to both the **User Search Filter** and **Search Filter** fields:
[See image.](#seeimage)
(!(UserAccountControl:1.2.840.113556.1.4.803:=2))
The following is an example:
(&(objectClass=User)(!(UserAccountControl:1.2.840.113556.1.4.803:=2)))
- Click **Save** and [activate the change](/zia/saving-and-activating-changes-admin-portal).
[]![Screenshot of the User Search Filter and Search Filter fields in the Edit Active Directory window](/downloads/zia/documentation-knowledgebase/authenticating-and-managing-users/ldap/knowledge-base/how-do-i-remove-disabled-users-active-directory-zscaler-user-database/user_search_filter_and_search_filter_fields_in_the_edit_active_directory_window.png)