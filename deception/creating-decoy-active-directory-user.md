# Creating an Active Directory Decoy User
Source: https://help.zscaler.com/deception/creating-decoy-active-directory-user
PDF: https://help.zscaler.com/pdf/com/en/1531332.pdf

[Watch a video on Creating Active Directory Decoy Users and Computers.](https://fast.wistia.net/embed/iframe/d0d5qnq153)
You can create an AD decoy user account in an Active Directory (AD) domain with different privilege levels. These decoy user accounts help you capture enumeration and detect privilege escalation techniques, such as brute force, Kerberoast detection, etc. Adversaries querying an AD find these decoy user accounts and use the credentials to access other assets in the organization. High fidelity alerts are triggered when the decoy accounts are accessed or when AD logs are analyzed.
Before adding and deploying a decoy user to an AD, you must [add an AD domain](/deception/adding-active-directory-domain).
To add an AD decoy user account:
- Go to **Deceive** > **Active Directory Decoys** > **Decoy Users**.
- From the **Domain** drop-down menu, select an AD domain on which you want to deploy the AD decoy user.
-
Click **Actions** and select **Add decoys**.
[See image.](#deception-add-ad-user-option)
-
In the **Decoy Details** window:
- **Username**: Enter a username for the decoy user.
-
**OU**: Enter the distinguished name of the organization unit (OU) name for the decoy user. If the AD domain is created with credentials, this field is automatically populated. If the AD domain is created without credentials, enter an OU name. For example, enter `OU=admins,OU=database,DC=example,DC=local`.
Make sure that the OU name is accurate. Otherwise, the deployment script throws an error during deployment.
- **First Name**: (Optional) Enter the first name of the decoy user.
- **Last Name**: (Optional) Enter the last name of the decoy user.
- **Office**: (Optional) Enter the office details of the decoy user.
- **Telephone Number**: (Optional) Enter the telephone number of the decoy user.
- **Email**: (Optional) Enter the email ID of the decoy user.
- **Can Password Expire**: Enable to activate the password expiration feature.
- **Pre-auth Not Required (Make account vulnerable to ASREPRoasting attacks)**: Enable to make the user account vulnerable to AS-REP roasting attacks.
-
**Group membership**: (Optional) Enter the group name of the decoy user. Adversaries often target user accounts that are members of privileged administrative groups.
If you add a decoy user to the Protected Groups, enumeration detection doesn't always work because of the SDProp process. To learn more, refer to the [Microsoft documentation.](https://learn.microsoft.com/en-us/windows-server/identity/ad-ds/plan/security-best-practices/appendix-c--protected-accounts-and-groups-in-active-directory#protected-groups)
- **Description**: (Optional) Enter a description like password or password hints that can detect the presence of adversaries within the environment. Adversaries often analyze the description attributes for information gathering and stored passwords.
- **Make Account Kerberoastable**: (Optional) Select a decoy from the drop-down menu to configure the `serviceprincipalname` attribute for the decoy account to make it vulnerable to Kerberoasting attacks.
- **Restrict Logon To**: (Optional) Select a decoy from the drop-down menu to configure the `logonworkstations` attribute for the decoy user account. Using this attribute, you can restrict the user’s accessibility to specific computers.
- **Profile Path**: (Optional) Select a decoy from the drop-down menu to configure the `profilePath` attribute for the decoy user account. Adversaries analyze this attribute to discover file shares.
[See image.](#deception-config-ad-user-details)
-
Click **Save**.
The AD decoy user account is added. The following icons indicate the decoy deployment status:
- ![zscaler-deception-ad-decoy-green-icon.png](/downloads/deception/deceive/active-directory-decoys/creating-decoy-active-directory-user/zscaler-deception-ad-decoy-green-icon.png)
: Decoy successfully deployed.
- ![zscaler-deception-ad-decoy-yellow-icon.png](/downloads/deception/deceive/active-directory-decoys/creating-decoy-active-directory-user/zscaler-deception-ad-decoy-yellow-icon.png)
: Decoy updated, but deployment is pending.
- ![zscaler-deception-ad-decoy-grey-icon.png](/downloads/deception/deceive/active-directory-decoys/creating-decoy-active-directory-user/zscaler-deception-ad-decoy-grey-icon.png)
: Decoy deployment pending.
- ![zscaler-deception-ad-decoy-red-icon.png](/downloads/deception/deceive/active-directory-decoys/creating-decoy-active-directory-user/zscaler-deception-ad-decoy-red-icon.png)
: Decoy deployment failed.
[See image.](#deception-ad-user-decoy-added)
After the AD decoy user is created, [run the deployment script on your AD domain controller](/deception/running-decoy-deployment-script-active-directory).
For AD decoys created using domains managed by server agents, you don't have to manually run the deployment scripts. The server agent automates AD decoy user deployment. If the decoy deployment has failed, click **Retry Failed Deployments** to submit the deployment request again.
[See image.](#deception-ad-decoy-user-server-agent)
[]![Add AD decoy user option](/downloads/deception/deceive/active-directory-decoys/creating-decoy-active-directory-user/zscaler-deception-ad-decoy-user-add-decoy.png)
[]![Configure AD decoy user details](/downloads/deception/deceive/active-directory-decoys/creating-decoy-active-directory-user/zscaler-deception-ad-decoy-config-details.png)
[]![AD decoy user added](/downloads/deception/deceive/active-directory-decoys/creating-decoy-active-directory-user/zscaler-deception-ad-decoy-users-deployed.png)
[]![View AD decoy users deployed in a domain managed by server agent](/downloads/deception/deceive/active-directory-decoys/creating-decoy-active-directory-user/zscaler-deception-ad-user-deployed-server-agent.png)