# Viewing Active Directory Decoy Computers
Source: https://help.zscaler.com/deception/viewing-active-directory-decoy-computers
PDF: https://help.zscaler.com/pdf/com/en/1531599.pdf

You can [add an Internal network decoy to an Active Directory (AD) and AD DNS as a decoy computer object](/deception/adding-network-decoy-active-directory) to make it look like a legitimate domain-joined system. AD decoy computers detect AD enumeration activities and AD-related exploits.
After you add AD decoy computers, you can view them on the Decoy Computers page. Additionally, you can view the decoy deployment status and the last updated timestamp of the decoy.
To view AD decoy computers:
- Go to **Deceive** > **Active Directory Decoys** > **Decoy Computers**.
-
Select an AD domain from the **Domain** drop-down menu.
The AD decoy computers are displayed. For each deployed decoy computer, you can view:
- **Name**: The name of the AD decoy computer. The following icons indicate the deployment status:
- ![zscaler-deception-ad-decoy-green-icon.png](/downloads/deception/deceive/active-directory-decoys/creating-decoy-active-directory-user/zscaler-deception-ad-decoy-green-icon.png)
: Decoy successfully deployed.
- ![zscaler-deception-ad-decoy-yellow-icon.png](/downloads/deception/deceive/active-directory-decoys/creating-decoy-active-directory-user/zscaler-deception-ad-decoy-yellow-icon.png)
: Decoy updated, but deployment is pending.
- ![zscaler-deception-ad-decoy-grey-icon.png](/downloads/deception/deceive/active-directory-decoys/viewing-active-directory-decoy-computers/zscaler-deception-ad-decoy-grey-icon.png)
: Decoy deployment is pending.
- ![zscaler-deception-ad-decoy-red-icon.png](/downloads/deception/deceive/active-directory-decoys/viewing-active-directory-decoy-computers/zscaler-deception-ad-decoy-red-icon.png)
: Decoy deployment failed.
- **OU**: The organization unit (OU) path.
- **Operating System**: The operating system (OS) name. The OS details appear in the properties of the decoy computer in the AD domain.
- **Description**: The description of the AD decoy computer.
- **IP Address**: The IP address of the AD decoy computer.
- **Last Updated**: The timestamp when the AD decoy computer was last updated (password resets, login actions, etc.).
![View AD decoy computer details](/downloads/deception/deceive/active-directory-decoys/viewing-active-directory-decoy-computers/zscaler-deception-view-ad-computer-decoy-details-2.png)