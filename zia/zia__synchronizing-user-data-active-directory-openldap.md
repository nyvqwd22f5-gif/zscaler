# Synchronizing User Data with an Active Directory or OpenLDAP
Source: https://help.zscaler.com/zia/synchronizing-user-data-active-directory-openldap
PDF: https://help.zscaler.com/pdf/com/en/1399611.pdf

This article illustrates how to configure the Zscaler service to synchronize user information with a directory server, either Active Directory (AD) or OpenLDAP.
Prerequisites
For your directory servers and firewall, ensure the following:
- On your directory server, grant the Zscaler service read-only access on a specific port. Zscaler provides the IP addresses.
- Configure the directory server to allow the service to connect to the appropriate ports when the service performs an LDAP Bind.
Before you configure the Zscaler service, ensure the following:
- Add all your email domains to your Zscaler account. The service synchronizes data only from the configured domains. To view the domains, go to **Administration **>** Company Profile**.
- Know the IP address/hostname of your directory server.
- Know the Distinguished Name (DN) of a user with permission to bind to (or query) the directory server. The account doesn't require privileged access.
- Know the groups you want to synchronize.
- Know the location of the user and group objects in your directory structure.
If you are synchronizing data from an AD server, review these guidelines:
- The Zscaler service can synchronize user information from one forest in an organization. If your organization has multiple forests, you can set up an AD proxy. Otherwise, Zscaler recommends integrating with [SAML](/zia/configuring-saml).
- The Zscaler service can synchronize data from multiple domains, as long as they are all registered with Zscaler Support.
- The Zscaler service doesn't support nested groups. You must manually identify specific group names within each nested group and add them to the Group filter.
Synchronizing User Data with an Active Directory or OpenLDAP
- [1. Define the synchronization settings of the AD or LDAP server.](#define-synchronization-settings-ad-ldap)
- [2. Enforce authentication for the location.](#enforce-authentication-location)
- [3. (Optional) Enable Digest Authentication for the location.](#enable-digest-authentication-location)
- [4. Configure the authentication method.](#configure-auth-method)
Troubleshooting
To troubleshoot AD and LDAP synchronization errors, see [Troubleshooting AD & LDAP Synchronization Errors](/zia/troubleshooting-synchronization-errors).
[]Zscaler strongly recommends that you use the **Authentication Wizard** to define your synchronization settings rather than using the **Advanced Configuration**, because the wizard walks you through synchronizing user data from an enterprise directory server to the Zscaler service.
To define the synchronization settings of the directory server:
- Go to **Administration **>** Authentication Settings**.
- For **User Repository Type**, choose **Active Directory** or **OpenLDAP**.
- Select one of the following synchronization options and configure accordingly:
- [Authentication Wizard](#setupwizard)
- [Advanced Configuration (Active Directory)](#advancedconfig-ad)
- [Advanced Configuration (OpenLDAP)](#advancedconfig-ldap)
- Ensure **Disable Directory Sync & Enable SCIM Provisioning** is disabled.
- For **Authentication Frequency**, choose how often users are required to authenticate to the Zscaler service. If you select **Custom**, specify 1 to 180 days.
- Click **Save** and [activate the change](/zia/saving-and-activating-changes-admin-portal).
- []Go to **Administration **> **Location Management**.
- Click the **Edit** icon for the location you are enabling authentication for.
- Enable **Enforce Authentication**. To learn more, see [Configuring Locations](/zia/configuring-locations).
[See image.](#seeimage-2c)
- Click **Save** and [activate the change](/zia/saving-and-activating-changes-admin-portal).
[]![The Enforce Authentication switch in the Edit Location window.](/downloads/zia/authentication-administration/user-management-authentication-settings/active-directory-ldap/synchronizing-user-data-active-directory-openldap/ZIA-Gateway-Options-Enforce-Authentication.png)
- []Go to **Administration **> **Location Management**.
- Click the **Edit** icon for the location you are enabling digest authentication for.
- Enable **Enable Digest Authentication**. To learn more, see [Configuring Locations](/zia/configuring-locations).
[See image.](#seeimage-location-digestauth)
- Click **Save** and [activate the change](/zia/saving-and-activating-changes-admin-portal).
You can also exempt URL categories, URLs, or cloud apps from digest authentication. To learn more, see [About Advanced Settings](/zia/about-advanced-settings#digest-auth).
[]![The Enable Digest Authentication switch in the Edit Location window.](/downloads/zia/authentication-administration/user-management-authentication-settings/active-directory-ldap/synchronizing-user-data-active-directory-openldap/ZIA-Gateway-Options-Enable-Digest-Authentication.png)
[]The default authentication method for synchronized users is LDAP Bind. If you want to use another method, you can configure one of the following:
- [SAML](/zia/configuring-saml)
- [One-Time Token/One-Time Link](/zia/how-do-i-configure-one-time-token-or-one-time-link)
If you use a one-time token or one-time link to authenticate users whose information was synchronized from a directory server, the passwords are stored in the Zscaler database and not in the directory server.
[]The Authentication Wizard validates your entries and allows you to check the data before it's synchronized to the Zscaler service. After you complete the wizard, the parameters are stored and displayed on this tab. You can configure the service to automatically synchronize user data from the directory server daily, weekly, or monthly. If the directory server is unavailable at the scheduled time, the service tries to synchronize at the next scheduled time.
You can click **View Setup Log** anytime to review the settings you defined in the preceding steps as well as any errors or warnings.
[See image.](#seeimage-setuplog)
Follow the Authentication Wizard:
- [Primary Directory Server](#primary-directory)
- [Authentication](#authentication)
- [Detected Settings](#detected-settings)
- [Lookup & Attributes](#lookup-attributes)
- [Secondary Directory Server (Optional)](#secondary-directory)
- [Synchronization](#synchronization)
- [Authentication Parameters](#authentication-parameters)
- [Review](#review)
[]![ The View Setup Log window in the Authentication Wizard.](/downloads/zia/authentication-administration/user-management-authentication-settings/active-directory-ldap/synchronizing-user-data-active-directory-openldap/zia-authentication-wizard-view-setup-log-window-6_1.png)
[]Define the authentication agent and settings for the directory server. The Zscaler service can synchronize data for up to two sets of users. For example, it can synchronize data from two directory servers (e.g., one in Europe and another one in the US) if they have different user, group, and department information. Configure the service to synchronize from a secondary directory server only if it doesn't have duplicate user or group information. Don't set up a secondary server for redundancy.
Define the following **Directory Server** settings, and click **Next**:
- **Secondary Configuration**: Enable to synchronize with two directory servers that have different sets of user data. Don't enable this option to synchronize the service with two servers that have duplicate information.
- **Primary Directory Name**: Enter a name for the primary directory server.
- **Authentication Agent Hosting**: Choose one of the following agents:
- **Enterprise**: Choose if your organization installed a [Zscaler Authentication Bridge (ZAB)](/zia/about-zscaler-authentication-bridge). The following field appears:
- **Authentication Agent URL**: Enter the URL or IP address of the [ZAB](/zia/about-zscaler-authentication-bridge). Use one of the following formats:
- https://<ZAB IP Address> (e.g., https://192.0.2.20)
- https://<ZAB Hostname> (e.g., https://zab.safemarch.com)
- **Cloud**: Choose if the central authority (CA) queries your directory server directly.
- **Directory Server Address**: Enter the IP address of the directory server. You also can enter an FQDN that points to the IP addresses of multiple directory servers to provide fault tolerance and resiliency against server failures. If you enter an FQDN and the DNS resolution returns multiple IP addresses, the Zscaler service automatically ignores the servers that are inactive or unavailable and synchronizes with the server that is active or available.
- **Directory Type**: Choose one of the following directory types.
- Apple OpenDirectory
- IBM Domino
- Microsoft Active Directory
- Microsoft Active Directory with Exchange
- Novell eDirectory
- OpenLDAP
- **Port**: Enter the port to which the Zscaler service connects when it synchronizes data. The following are the default ports:
- **3268**: Use to connect to the Global Catalog of an AD server.
- **3269**: Use to connect to a Global Catalog AD server over a secure connection using SSL.
- **389**: Use to connect to an LDAP server. AD default port for listening.
- **636**: Use to connect to an LDAP server over a secure connection using SSL.
If your organization is synchronizing multiple domains from an AD server, select either port 3268 (non-secure) or 3269 (secure) so the Zscaler service can access the Global Catalog. The Global Catalog contains all domain objects in an AD forest. If your organization uses custom ports, specify them accordingly.
- **Secure LDAP**: Enable Secure LDAP to ensure that all data exchanged between the Zscaler Authentication Bridge (ZAB) and your directory server is encrypted.
Zscaler strongly recommends enabling this option to secure LDAP communications between the Zscaler service and your directory server.
[See image.](#seeimage-primaryds)
[]![The Primary Directory Server step in the Authentication Wizard](/downloads/zia/authentication-administration/user-management-authentication-settings/active-directory-ldap/synchronizing-user-data-active-directory-openldap/zia-authentication-wizard-primary-directory-server-6_1.png)
[]When a client, such as the Zscaler service, connects to a directory server, the server performs a BIND operation where it authenticates the client. If the operation is successful, the client is allowed to access the server. The directory server can require the client to enter a Distinguished Name (DN) and password, or it can allow the client to perform the query anonymously, without requiring credentials. In this step, specify whether the directory server allows anonymous access. If it doesn't, enter the DN and password required to access the server.
Define the following ​​​​​**Authentication** settings for the directory server, and click **Next**:
- **Use Anonymous Authentication**: Enable if the directory server allows anonymous access. Ensure that this option is also enabled on your directory server.
- **Bind DN**: Enter the DN of an administrator account that has permission to query the directory server. Use one of the following formats:
- domain\user** **(e.g., `zscaler\admin`)
- LDAP syntax (e.g., `cn=admin,cn=users,dc=zscaler,dc=net`)
- **Bind Password**: Enter the password of the administrator account entered above.
[See image.](#seeimage-auth)
[]![The Authentication step in the Authentication Wizard](/downloads/zia/authentication-administration/user-management-authentication-settings/active-directory-ldap/synchronizing-user-data-active-directory-openldap/zia-authentication-wizard-authentication-6_1.png)
[]If the Zscaler service successfully connects to the directory server, the wizard automatically populates the **Base DN** field. The base DN specifies the location or branch of the directory where the Zscaler service begins searching for users, groups, and departments. The service only retrieves objects from the branch that is specified in the **Base DN** field.
Define the following **Detected Settings**, and click **Next**:
- **Base DN**: The default option contains the DN of the top of the tree (e.g., `dc=example,dc=com`). Depending on your directory structure, this might return more results than desired. However, providing a more narrow starting search point on the tree might exclude some desired users and groups. Zscaler recommends you examine your directory structure, locate the branch with your desired users and groups, and then enter the base DN. To start the search from another location in the directory, choose it from the drop-down menu or enter its DN.
- **Pagination**: Choose one of the following pagination settings:
- **Auto (Recommended)**: The Zscaler service detects if your directory server supports pagination. If it does, it pages results that exceed 1,000 items. If it doesn't, it returns the first 1,000 items only.
- **Enabled**: The directory server pages the results that exceed 1,000 items.
- **Disabled**: The directory server returns the first 1,000 items only.
[See image.](#seeimage-detectedsettings)
[]![The Detected Settings step in the Authentication Wizard.](/downloads/zia/authentication-administration/user-management-authentication-settings/active-directory-ldap/synchronizing-user-data-active-directory-openldap/zia-authentication-wizard-detected-settings-6_1.png)
[]Specify which attributes represent the required user information. You can define filters to narrow down the results. Zscaler strongly recommends that you use an LDAP browser, such as Apache Studio Directory or Softerra, to view several actual users and confirm which attributes are being used to identify the user name, email address, department, and group information. If you are synchronizing information from an LDAP server and your organization uses custom LDAP attributes, consult your LDAP administrator to determine which attributes to use.
To define the **Lookup & Attributes**:
- In the **Lookup Parameters **section:
- **Lookup Parameters**: Choose one of the following lookup methods and enter the required information in the next field. Ensure that the information exists in the directory.
- **Auto**: Look up the user by an email address, Windows login domain name, DN (e.g., `dc=example,dc=com`), or LDAP attribute (e.g., `objectClass=User`). This is the easiest and recommended method.
- **Email**: Look up the user by the email address.
- **LDAP Attribute**: Look up the user by an LDAP attribute (e.g., `objectClass=User`).
- **LDAP DN**: Look up the user by the DN (e.g., `dc=example,dc=com`).
- **Windows Domain Login**: Look up the user by the Windows login domain name.
- **Lookup User Entry**: Enter the user information based on your chosen lookup parameter method, and click **Look Up User**. The Zscaler service queries the directory server for the user entry and attributes.
- **Lookup Results**: Displays the user's or group's attributes that were retrieved from the directory server. You can use this information to configure the following attributes.
- In the **Attribute Fields** section, specify the names of the attributes that represent the user's email address, full name, group, and department, and also define filters. The Zscaler service provides granular filters so you can synchronize only the relevant users, groups, and departments.
- **User Login**: Enter or choose the attribute representing the login name that users enter to log in and authenticate to the Zscaler service. This attribute is used to verify the login name that a user enters when authenticating to the service. Following are some guidelines for the login name:
- It must be in the form of an email address, though it doesn't have to be a valid email address.
- It must be unique, and the domain name must belong to the organization.
- If the value is not an email address, the service creates an email address by appending the domain name to it if your organization has registered a single domain on the service. If your organization has registered multiple domains and the value is not an email address, the synchronization fails.
- Zscaler recommends you use `userPrincipalName`, regardless of the number of domains hosted by the Zscaler service. Use `sAMAccountName`** **only if you have one domain hosted by the Zscaler service. Otherwise, you can use `proxyAddresses`, `userPrincipalName`, or `mail`.
- **Group Base DN**: (OpenLDAP only) Displays the base DN you provided to query the group.
- **User Full Name**: Enter or choose the attribute that represents user full names (e.g., `cn` or `displayName`). The Zscaler service displays the value in this attribute in the **Who** dialog that appears when administrators create policies.
- **Group Membership**: (Active Directory only) Enter or choose the attribute that represents which groups the user belongs to (e.g., `memberOf`). You can use groups to apply policies.
- **Group Search Filter**: Use this filter to narrow down the group objects that the Zscaler service returns after the synchronization. You can enter or choose a filter string to locate only the groups you want to apply policies to. The service synchronizes up to 16 groups per user. Zscaler recommends you use an LDAP browser to query filters prior to synchronizing group data with the directory server. Following are some guidelines:
- To import only one group, use the following filter:
(&(objectclass=group)(cn=<Group Name>*))
- To import multiple groups, use the following filter:
(&(objectclass=group)(|(cn=<Group Name 1>*)(cn=<Group Name 2>*)))
Following is an example of a filter that imports three groups called vips, standard users, and advanced users:
(&(objectClass=group)(|(cn=vips*)(cn=standard users*)(cn=advanced users*)))
Following is an example of a filter that imports all groups that begin with `Zscaler`:
(&(objectClass=group)(cn=zscaler*))
Replace <Group Name>,<Group Name 1>, and <Group Name 2> with the actual group name in the directory server. The asterisk (*) is required, so the filter automatically completes the Common Name (cn) value. The pipe (**|**) character means that at least one criteria must match. The ampersand (&) means that all criteria must be true.
- **User Search Filter**: Use this filter to narrow down the user objects that the Zscaler service returns after synchronization. You can enter or choose a filter string to locate specific users, such as users who belong to a specific group. For example, choose **objectClass=person** to narrow down the data to persons and not computers. Zscaler recommends you use an LDAP browser to query filters prior to synchronizing user data with the directory server.
- **Group Name**: Enter or choose the attribute that represents group names (e.g., `cn`).
- **Department Membership**: This attribute is used to populate the **Department **field in the reports produced by the Zscaler service. You can specify any attribute that identifies the information that should appear in the **Department** field. For example, you can use `department` or `ou`.
- **User Membership**: (OpenLDAP only) Enter or choose the attribute in the group entry that defines the members. For example, if the member entry is `cn=johndoe,cn=Users,dc=example,dc=com`, then the user membership attribute is `UniqueMember`.
- **User Attribute**: (OpenLDAP only) Enter or choose the user attribute that's part of the user membership attribute to uniquely identify the users in the group. For example, if the member entry is `cn=johndoe,cn=Users,dc=example,dc=com`, then the user attribute is `dn`.
- **Enable Password Change Sync**: (Active Directory only) Enable to scan the AD for password changes. If you enable this setting, the following digest authentication fields appear:
- **Enable User Deactivation Checks**: Enable to detect if a user account is deactivated on the AD. If you enable this setting, the following field appears:
- **Active Directory Poll Frequency (Seconds)**: Enter the frequency in seconds to poll the AD. You can't modify this field for the secondary directory server. The Zscaler service uses the same frequency you entered for the primary directory server.
- **Password Last Set Attribute**: Enter the attribute that represents the password last-changed time stamp (e.g., `pwdLastSet`).
- **User Deactivation Attribute**: Enter the attribute that represents user deactivation (e.g., `(userAccountControl:1.2.345.678901.2.3.456:=1)`).
- Click **Next**.
[See image for Active Directory.](#seeimage-lookupattributes-ad)
[See image for OpenLDAP.](#seeimage-lookupattributes-ldap)
[]![The Lookup & Attributes step in the Authentication Wizard for if you're configuring an Active Directory.](/downloads/zia/authentication-administration/user-management-authentication-settings/active-directory-ldap/synchronizing-user-data-active-directory-openldap/zia-authentication-wizard-lookup-attributes-active-directory-6_1.png)
[]![The Lookup & Attributes step in the Authentication Wizard for if you're configuring an OpenLDAP server.](/downloads/zia/authentication-administration/user-management-authentication-settings/active-directory-ldap/synchronizing-user-data-active-directory-openldap/zia-authentication-wizard-lookup-attributes-openldap-6_1.png)
[]This step appears only if you enabled **Secondary Configuration** in [Primary Directory Server](/zia/synchronizing-user-data-active-directory-openldap#primary-directory). If you're only configuring one directory server, skip this step.
To define the secondary **Directory Server** settings:
- In **Directory Server**:
- **Secondary Directory Name**: Enter a name for the secondary directory server.
- **Directory Server Address**: Enter the IP address of the secondary directory server. You also can enter an FQDN that points to the IP addresses of multiple directory servers to provide fault tolerance and resiliency against server failures. If you enter an FQDN and the DNS resolution returns multiple IP addresses, the Zscaler service automatically ignores the servers that are inactive or unavailable and synchronizes with the server that is active or available.
- **Port**: Enter the port to which the Zscaler service connects when it synchronizes data. The following are the default values:
- **3268**: Use to connect to the Global Catalog of an AD server.
- **3269**: Use to connect to a Global Catalog AD server over a secure connection using SSL.
- **389**: Use to connect to an LDAP server. AD default port for listening.
- **636**: Use to connect to an LDAP server over a secure connection using SSL.
If your organization is synchronizing multiple domains from an AD server, select either port 3268 (non-secure) or 3269 (secure) so the Zscaler service can access the Global Catalog. The Global Catalog contains all domain objects in an AD forest. If your organization uses custom ports, specify them accordingly.
- **Secure LDAP**: Enable Secure LDAP to ensure that all data exchanged between the Zscaler Authentication Bridge (ZAB) and your directory server is encrypted.
Zscaler strongly recommends enabling this option to secure LDAP communications between the Zscaler service and your directory server.
[See image.](#seeimage-secondaryds)
- Click **Next**.
- Repeat the following steps in the wizard for the secondary directory server:
- [Authentication](/zia/synchronizing-user-data-active-directory-openldap#authentication)
- [Detected Settings](/zia/synchronizing-user-data-active-directory-openldap#detected-settings)
- [Lookup & Attributes](/zia/synchronizing-user-data-active-directory-openldap#lookup-attributes)
[]![The Secondary Directory Server step in the Authentication Wizard.](/downloads/zia/authentication-administration/user-management-authentication-settings/active-directory-ldap/synchronizing-user-data-active-directory-openldap/zia-authentication-wizard-secondary-directory-server-6_1.png)
[]In **Synchronization**, click **Start Synchronization** to start synchronizing the Zscaler service with the directory server.
[See image.](#seeimage-startsync)
The wizard displays the synchronization status and results. After synchronization, you can click the numbers in the **Added**, **Modified**, and **Removed** columns to view and search through the entries discovered and verify whether the users, groups, and departments were synchronized correctly. When you're done, click **Next**.
[See image.](#seeimage-syncresults)
[]![The Start Synchronization button in the Authentication Wizard.](/downloads/zia/authentication-administration/user-management-authentication-settings/active-directory-ldap/synchronizing-user-data-active-directory-openldap/zia-authentication-wizard-start-synchronization-6_1.png)
[]![The number of Add Groups under Synchronization Results in the Authentication Wizard.](/downloads/zia/authentication-administration/user-management-authentication-settings/active-directory-ldap/synchronizing-user-data-active-directory-openldap/zia-authentication-wizard-synchronization-results-6_1.png)
[]To define the **Authentication Parameters**:
- In the **Primary Authentication Parameters** section:
- **User Authentication Filter:** Enter or choose a filter to search the primary directory server and find the user's DN when the user authenticates to the Zscaler service. Unlike the **User Search Filter** and **Group Search Filter**, the service only uses this filter when it authenticates a user, not when it synchronizes users from the directory server.
For example, if you use `(objectClass=User)`, the service searches for`(&(objectClass=user)(userPrincipalName=example@safemarch.com))`. `userPrincipalName` is the primary attribute being synchronized. In this scenario, the service receives only one response, which is the user who is authenticating.
Zscaler also supports an advanced filter option where the filter can be parameterized, such as `(&(objectClass=user)(sAMAccountName=${USER}))`. In this scenario, the search issued is `(&(objectClass=user)(sAMAccountName=john))`.
- **Test User Login**: Enter a test user's login ID.
- **Test User Password**: Enter a test user's password.
- **Check Authentication**: Click to verify the user's credentials, and ensure that the retrieved attributes are correct.
[See image.](#seeimage-authparam)
- In the **Secondary Authentication Parameters** section, in **User Authentication Filter**, enter or choose a filter to search the secondary directory server and find the user's DN when the user authenticates to the Zscaler service. This field section appears only if you enabled **Secondary Configuration** in [Primary Directory Server](/zia/synchronizing-user-data-active-directory-openldap#primary-directory).
[See image.](#seeimage-authparamsecondary)
- Click **Next**.
[]![The Primary Authentication Parameters section in the Authentication Wizard.](/downloads/zia/authentication-administration/user-management-authentication-settings/active-directory-ldap/synchronizing-user-data-active-directory-openldap/zia-authentication-wizard-authentication-parameters-6_1.png)
[]![The Secondary Authentication Parameters section in the Authentication Wizard.](/downloads/zia/authentication-administration/user-management-authentication-settings/active-directory-ldap/synchronizing-user-data-active-directory-openldap/zia-authentication-wizard-authentication-parameters-secondary-6_1.png)
[]In **Review**, click **Finish** to save the configuration and synchronized data, or exit the window to discard changes.
If you click **Finish**, the existing user authentication configuration is overwritten with the new configuration.
[See image.](#seeimage-review)
[]![Screenshot of the Review step in the Authentication Wizard.](/downloads/zia/authentication-administration/user-management-authentication-settings/active-directory-ldap/synchronizing-user-data-active-directory-openldap/zia-authentication-wizard-review-6_1.png)
[]
- In the **Edit Active Directory** window, in the **Global Configuration** section:
- **Synchronization Frequency**: Choose how often you want the Zscaler service to synchronize user information.
- **Manual**: Synchronize only when you click **Sync Now**.
- **Daily**: Synchronize every 24 hours at midnight in your organization's time zone.
- **Monthly**: Synchronize on the first day of every month at midnight in your organization's time zone.
- **Weekly**: Synchronize every Sunday at midnight in your organization's time zone.
- **Enable Second Directory**: Enable to synchronize with two directory servers that have different sets of user data. Don't enable this option to synchronize the service with two servers that have duplicate information. If you enable this option, The **Directory #1** and **Directory #2** tabs appear.
- **Authentication Agent Hosting**: Choose one of the following agents.
- **In-The-Cloud**: Choose if the central authority (CA) queries your directory server directly.
- **Enterprise-Hosted**: Choose if your organization installed a [Zscaler Authentication Bridge (ZAB)](/zia/about-zscaler-authentication-bridge). The following option appears:
- **Authentication Agent** **URL**: Enter the URL or IP address of the ZAB. Use one of the following formats:
- https://<ZAB IP Address> (e.g., https://192.0.2.20)
- https://<ZAB Hostname> (e.g., https://zab.safemarch.com)
- In the **Directory Server Details** section:
If you enabled **Enable Second Directory**, you see two directory tabs: **Directory #1** and **Directory #2**.
- **Directory Name**: Enter a name for the directory server.
- **Server Address**: Enter the IP address of the directory server. You also can enter an FQDN that points to the IP addresses of multiple directory servers to provide fault tolerance and resiliency against server failures. If you enter an FQDN and the DNS resolution returns multiple IP addresses, the Zscaler service automatically ignores the servers that are inactive or unavailable and synchronizes with the server that is active or available.
- **Secure Access**: Enable SSL inspection for the LDAP communications. Ensure you've installed an SSL certificate on your directory server.
Zscaler strongly recommends enabling this option to secure LDAP communications between the Zscaler service and your directory server.
- **Port**: Enter the port to which the Zscaler service connects when it synchronizes data. The following are the default ports:
- **3268**: Use to connect to the Global Catalog of an AD server.
- **3269**: Use to connect to a Global Catalog AD server over a secure connection using SSL.
- **389**: Use to connect to an LDAP server. AD default port for listening.
- **636**: Use to connect to an LDAP server over a secure connection using SSL.
If your organization is synchronizing multiple domains from an AD server, select either port 3268 (non-secure) or 3269 (secure) so the Zscaler service can access the Global Catalog. The Global Catalog contains all domain objects in an AD forest. If your organization uses custom ports, specify them accordingly.
- In the **Connection Parameters** section:
- **Base DN**: Enter the DN of the top of the tree (e.g., `dc=example,dc=com`). Depending on your directory structure, this might return more results than desired. However, providing a more narrow starting search point on the tree might exclude some desired users and groups. Zscaler recommends you examine your directory structure, locate the branch with your desired users and groups, and then enter the base DN. To start the search from another location in the directory, enter its DN.
- **Pagination**: Choose one of the following pagination options:
- **Auto (Recommended)**: The Zscaler service detects if your directory server supports pagination. If it does, it pages results that exceed 1,000 items. If it doesn't, it returns the first 1,000 items only.
- **Enabled**: The directory server pages results that exceed 1,000 items.
- **Disabled**: The directory server returns the first 1,000 items only.
- **Anonymous Authentication**: Enable if the directory server allows anonymous access. Ensure that this option is also enabled on your directory server. The following fields appear:
- **Bind DN**: Enter the DN of an administrator account that has permission to query the directory server. Use one of the following formats:
- domain\user** **(e.g., `zscaler\admin`)
- LDAP syntax (e.g., `cn=admin,cn=users,dc=zscaler,dc=net`)
- **Bind Password**: Enter the password of the administrator account entered above.
- In the **Attribute Fields** section:
- **Login Attribute**: Enter the attribute representing the login name that users enter to log in and authenticate to the Zscaler service. This attribute is used to verify the login name that a user enters when authenticating to the service. Following are some guidelines for the login name:
- It must be in the form of an email address, though it doesn't have to be a valid email address.
- It must be unique, and the domain name must belong to the organization.
- If the value isn't an email address, the service creates an email address by appending the domain name to it if your organization has registered a single domain on the service. If your organization has registered multiple domains and the value isn't an email address, the synchronization fails.
- Zscaler recommends you use `userPrincipalName`, regardless of the number of domains hosted by the Zscaler service. Use `sAMAccountName`** **only if you have one domain hosted by the Zscaler service. Otherwise, you can use `proxyAddresses`, `userPrincipalName`, or `mail`.
- **User Display Name Attribute**: Enter the attribute that represents user full names (e.g., `cn` or `displayName`). The Zscaler service displays the value in this attribute in the **Who** dialog that appears when administrators create policies.
- **Group Membership Attribute**: Enter the attribute that represents which groups the user belongs to (e.g., `memberOf`). You can use groups to apply policies.
- **Group Attribute Name**: Enter the attribute that represents group names (e.g., `cn`).
- **Department Name Attribute**: This attribute is used to populate the **Department **field in the reports produced by the Zscaler service. You can enter any attribute that identifies the information that should appear in the **Department** field. For example, you can use `department` or `ou`.
- In the **Digest Authentication** section:
- **Enable Password Change Sync**: Enable to scan the Active Directory for password changes. If you enable this setting, the following fields appear:
- **Enable User Deactivation Checks**: Enable to detect if a user account is deactivated on the AD. If you enable this setting, the following field appears:
- **Active Directory Poll Frequency (Seconds)**: Enter the frequency in seconds to poll the AD. You can't modify this field for the secondary directory server. The Zscaler service uses the same frequency you entered for the primary directory server.
- **Password Last Set Attribute**: Enter the attribute that represents the password last-changed time stamp (e.g., `pwdLastSet`).
- **User Deactivation Attribute**: Enter the attribute that represents user deactivation (e.g., `(userAccountControl:1.2.345.678901.2.3.456:=1)`).
- In the **Search** section:
- **Group Search Filter**: Use this filter to narrow down the group objects that the Zscaler service returns after the synchronization. You can enter a filter string to locate only the groups you want to apply policies to. The service synchronizes up to 16 groups per user. Zscaler recommends you use an LDAP browser to query filters prior to synchronizing group data with the directory server. Following are some guidelines:
- To import only one group, use the following filter:
(&(objectclass=group)(cn=<Group Name>*))
- To import multiple groups, use the following filter:
(&(objectclass=group)(|(cn=<Group Name 1>*)(cn=<Group Name 2>*)))
Following is an example of a filter that imports three groups called vips, standard users, and advanced users:
(&(objectClass=group)(|(cn=vips*)(cn=standard users*)(cn=advanced users*)))
Following is an example of a filter that imports all groups that begin with `Zscaler`:
(&(objectClass=group)(cn=zscaler*))
Replace <Group Name>,<Group Name 1>, and <Group Name 2> with the actual group name in the directory server. The asterisk (*) is required, so the filter automatically completes the Common Name (cn) value. The pipe (**|**) character means that at least one criteria must match. The ampersand (&) means that all criteria must be true.
- **User Search Filter**: Use this filter to narrow down the user objects that the Zscaler service returns after synchronization. You can enter a filter string to locate specific users, such as users who belong to a specific group. For example, enter `objectClass=person` to narrow down the data to persons and not computers. Zscaler recommends you use an LDAP browser to query filters prior to synchronizing user data with the directory server.
- **Advanced Search Filter**: Enable this if you want to use a separate search filter for the authentication process (e.g., a search filter that searches using non-email format attributes). If disabled, the Zscaler service uses the **User Search Filter** for synchronizing and authenticating users.
- **Search Filter**: Enter a filter to search the directory server and find the user's DN when the user authenticates to the Zscaler service. Unlike the **User Search Filter** and **Group Search Filter**, the service only uses this filter when it authenticates a user, not when it synchronizes users from the directory server.
For example, if you enter `(objectClass=User)`, the service searches for`(&(objectClass=user)(userPrincipalName=example@safemarch.com))`. `userPrincipalName` is the primary attribute being synchronized. In this scenario, the service receives only one response, which is the user who is authenticating.
Zscaler also supports an advanced filter option where the filter can be parameterized, such as `(&(objectClass=user)(sAMAccountName=${USER}))`. In this scenario, the search issued is `(&(objectClass=user)(sAMAccountName=john))`.
[See image.](#seeimage-ad)
- Click **Save**.
[]![The Edit Active Directory window shows fields for global configuration and directory details.](/downloads/zia/authentication-administration/user-management-authentication-settings/active-directory-ldap/synchronizing-user-data-active-directory-openldap/ZIA-Edit-Active-Directory-window-6_1.png)
[]
- In the **Edit LDAP** window, in the **Global Configuration** section:
- **Synchronization Frequency**: Choose how often you want the Zscaler service to synchronize user information.
- **Manual**: Synchronize only when you click **Sync Now**.
- **Daily**: Synchronize every 24 hours at midnight in your organization's time zone.
- **Monthly**: Synchronize on the first day of every month at midnight in your organization's time zone.
- **Weekly**: Synchronize every Sunday at midnight in your organization's time zone.
- **Enable Second Directory**: Enable to synchronize with two directory servers that have different sets of user data. Don't enable this option to synchronize the service with two servers that have duplicate information. If you enable this option, The **Directory #1** and **Directory #2** tabs appear below.
- **Authentication Agent Hosting**: Choose one of the following agents.
- **In-The-Cloud**: Choose if the central authority (CA) queries your directory server directly.
- **Enterprise-Hosted**: Choose if your organization installed a [Zscaler Authentication Bridge (ZAB)](/zia/about-zscaler-authentication-bridge). The following option appears:
- **Authentication Agent** **URL**: Enter the URL or IP address of the ZAB. Use one of the following formats:
- https://<ZAB IP Address> (e.g., https://192.0.2.20)
- https://<ZAB Hostname> (e.g., https://zab.safemarch.com)
- In the **Directory Server Details** section:
If you enabled **Enable Second Directory**, you see two directory tabs: **Directory #1** and **Directory #2**.
- **Directory Name**: Enter a name for the directory server.
- **Server Address**: Enter the IP address of the directory server. You also can enter an FQDN that points to the IP addresses of multiple directory servers to provide fault tolerance and resiliency against server failures. If you enter an FQDN and the DNS resolution returns multiple IP addresses, the Zscaler service automatically ignores the servers that are inactive or unavailable and synchronizes with the server that is active or available.
- **Secure Access**: Enable SSL inspection for the LDAP communications. Ensure you've installed an SSL certificate on your directory server.
Zscaler strongly recommends enabling this option to secure LDAP communications between the Zscaler service and your directory server.
- **Port**: Enter the port to which the Zscaler service connects when it synchronizes data. The following are the default ports:
- **3268**: Use to connect to the Global Catalog of an AD server.
- **3269**: Use to connect to a Global Catalog AD server over a secure connection using SSL.
- **389**: Use to connect to an LDAP server. AD default port for listening.
- **636**: Use to connect to an LDAP server over a secure connection using SSL.
If your organization is synchronizing multiple domains from an AD server, select either port 3268 (non-secure) or 3269 (secure) so the Zscaler service can access the Global Catalog. The Global Catalog contains all domain objects in an AD forest. If your organization uses custom ports, specify them accordingly.
- In the **Connection Parameters** section:
- **Advanced Base DN**: Enable if the users and groups you want to synchronize are in separate branches of your directory structure. The following fields appear:
- **User Base DN**: Enter the DN of the top of the tree (e.g., `dc=example,dc=com`). Depending on your directory structure, this might return more results than desired. However, providing a more narrow starting search point on the tree might exclude some desired users and groups. Zscaler recommends you examine your directory structure, locate the branch with your desired users and groups, and then enter the base DN. To start the search from another location in the directory, choose it from the drop-down menu or enter its DN.
- **Group Base DN**: Enter the DN of the branch or location where the group objects are located.
- **Base DN**: (Appears if **Advanced Base DN** is disabled.) Enter the DN of the top of the tree (e.g., `dc=example,dc=com`). Depending on your directory structure, this might return more results than desired. However, providing a more narrow starting search point on the tree might exclude some desired users and groups. Zscaler recommends you examine your directory structure, locate the branch with your desired users and groups, and then enter the base DN. To start the search from another location in the directory, enter its DN.
- **Pagination**: Choose one of the following pagination settings:
- **Auto (Recommended)**: The Zscaler service detects if your directory server supports pagination. If it does, it pages results that exceed 1,000 items. If it doesn't, it returns the first 1,000 items only.
- **Enabled**: The directory server pages results that exceed 1,000 items.
- **Disabled**: The directory server returns the first 1,000 items only.
- **Anonymous Authentication**: Enable if the directory server allows anonymous access. Ensure that this option is also enabled on your directory server. The following fields appear:
- **Bind DN**: Enter the DN of an administrator account that has permission to query the directory server. Use one of the following formats:
- domain\user** **(e.g., `zscaler\admin`)
- LDAP syntax (e.g., `cn=admin,cn=users,dc=zscaler,dc=net`)
- **Bind Password**: Enter the password of the administrator account entered above.
- In the **Attribute Fields** section:
- **Login Attribute**: Enter the attribute representing the login name that users enter to log in and authenticate to the Zscaler service. This attribute is used to verify the login name that a user enters when authenticating to the service. Following are some guidelines for the login name:
- It must be in the form of an email address, though it doesn't have to be a valid email address.
- It must be unique, and the domain name must belong to the organization.
- If the value is not an email address, the service creates an email address by appending the domain name to it if your organization has registered a single domain on the service. If your organization has registered multiple domains and the value isn't an email address, the synchronization fails.
- Zscaler recommends you use `userPrincipalName`, regardless of the number of domains hosted by the Zscaler service. Use `sAMAccountName`** **only if you have one domain hosted by the Zscaler service. Otherwise, you can use `proxyAddresses`, `userPrincipalName`, or `mail`.
- **User Display Name Attribute**: Enter the attribute that represents user full names (e.g., `cn` or `displayName`). The Zscaler service displays the value in this attribute in the **Who** dialog that appears when administrators create policies.
- **Member in Group**: Enter the attribute that represents which groups the user belongs to (e.g., `memberOf`). You can use groups to apply policies.
- **User in Member**: Enter the user attribute that's part of the user membership attribute to uniquely identify the users in the group. For example, if the member entry is `cn=johndoe,cn=Users,dc=example,dc=com`, then the user attribute is `dn`.
- **Group Attribute Name**: Enter the attribute that represents group names (e.g., `cn`).
- **Department Name Attribute**: This attribute is used to populate the **Department **field in the reports produced by the Zscaler service. You can enter any attribute that identifies the information that should appear in the **Department** field. For example, you can use `department` or `ou`.
- In the **Search** section:
- **Group Search Filter**: Use this filter to narrow down the group objects that the Zscaler service returns after the synchronization. You can enter a filter string to locate only the groups you want to apply policies to. The service synchronizes up to 16 groups per user. Zscaler recommends you use an LDAP browser to query filters prior to synchronizing group data with the directory server. Following are some guidelines:
- To import only one group, use the following filter:
(&(objectclass=group)(cn=<Group Name>*))
- To import multiple groups, use the following filter:
(&(objectclass=group)(|(cn=<Group Name 1>*)(cn=<Group Name 2>*)))
Following is an example of a filter that imports three groups called vips, standard users, and advanced users:
(&(objectClass=group)(|(cn=vips*)(cn=standard users*)(cn=advanced users*)))
Following is an example of a filter that imports all groups that begin with `Zscaler`:
(&(objectClass=group)(cn=zscaler*))
Replace <Group Name>,<Group Name 1>, and <Group Name 2> with the actual group name in the directory server. The asterisk (*) is required, so the filter automatically completes the Common Name (cn) value. The pipe (**|**) character means that at least one criteria must match. The ampersand (&) means that all criteria must be true.
- **User Search Filter**: Use this filter to narrow down the user objects that the Zscaler service returns after synchronization. You can enter a filter string to locate specific users, such as users who belong to a specific group. For example, enter `objectClass=person` to narrow down the data to persons and not computers. Zscaler recommends you use an LDAP browser to query filters prior to synchronizing user data with the directory server.
- **Advanced Search Filter**: Enable this if you want to use a separate search filter for the authentication process (e.g., a search filter that searches using non-email format attributes). If disabled, the Zscaler service uses the **User Search Filter** for synchronizing and authenticating users.
- **Search Filter**: Enter a filter to search the directory server and find the user's DN when the user authenticates to the Zscaler service. Unlike the **User Search Filter** and **Group Search Filter**, the service only uses this filter when it authenticates a user, not when it synchronizes users from the directory server.
For example, if you enter `(objectClass=User)`, the service searches for`(&(objectClass=user)(userPrincipalName=example@safemarch.com))`. `userPrincipalName` is the primary attribute being synchronized. In this scenario, the service receives only one response, which is the user who is authenticating.
Zscaler also supports an advanced filter option where the filter can be parameterized, such as `(&(objectClass=user)(sAMAccountName=${USER}))`. In this scenario, the search issued is `(&(objectClass=user)(sAMAccountName=john))`.
[See image.](#seeimage-ldap)
- Click **Save**.
[]![The Edit LDAP window shows fields for global configuration and directory details.](/downloads/zia/authentication-administration/user-management-authentication-settings/active-directory-ldap/synchronizing-user-data-active-directory-openldap/ZIA-Edit-LDAP-window-6_1.png)