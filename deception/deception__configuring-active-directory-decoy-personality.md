# Configuring an Active Directory Decoy Personality
Source: https://help.zscaler.com/deception/configuring-active-directory-decoy-personality
PDF: https://help.zscaler.com/pdf/com/en/1531538.pdf

Active Directory (AD) decoy personalities are templates that allow you to use [deception strategies](/deception/about-deception-strategy) to create and deploy [AD decoys](/deception/about-active-directory-decoys).
To create an AD decoy personality:
- Go to **Miragemaker **> **Strategy Builder **> **Active Directory Decoy**.
- Click **Add Personality**.
- In the **Decoy Details **window:
- **Name**: Enter the name for the AD decoy personality.
- **Tags**: Select one or more tags from the drop-down menu that you want to associate with the personality. When decoys are deployed via [deception strategies](/deception/creating-strategy) using a tag, the decoys are created by randomly choosing a personality associated with the tag. To create a new tag, click **Create Tags**, enter a name for the tag, and click **Save.**
- **Usernames**: Enter the usernames (one per line) for the AD decoys created using this personality.
- **OU**: Select the organization unit (OU) name for the AD user decoys created using this personality.
- **Pre auth not required**: Enable to make the user accounts vulnerable to AS-REP roasting attacks.
- **Can password expire**: Enable to activate the password expiration feature.
- **Group Membership**: Enter the group name of the decoy user. Adversaries often target user accounts that are members of privileged administrative groups.
- **Description**: Enter a description like a password or password hints that can detect the presence of adversaries within the environment. Adversaries often analyze the description attributes for information gathering and stored passwords.
- **SPN**: Enter Service Principal Names that you want to associate with decoy users.
- **Profile Path Condition**: Configure the `profilePath` attribute for the decoy user account. Adversaries analyze this attribute to discover file shares.
- **Use Modifiers**: Enable to randomly generate usernames based on the values entered for the **Usernames **field at the time of deployment.
- **Network Decoy Condition**: Configure the condition for network decoys.
- **Restrict Logon To**: Enable to configure the `logonworkstations` attribute for the decoy user account. Using this attribute, you can restrict the user’s accessibility to specific computers.
- **Make account Kerberoastable**: Enable to configure the `serviceprincipalname` attribute for the decoy account and make decoys vulnerable to Kerberoasting attacks.
[See image.](#zd-addp-window)
- Click **Save**.
After configuring an AD decoy personality, you can use it to create and deploy [AD decoys ](/deception/about-active-directory-decoys)via [deception strategies](/deception/about-deception-strategy).
[]![A screenshot capturing the AD decoy details personlity window](/downloads/deception/miragemaker/strategy-builder/active-directory-decoy-personalities/configuring-active-directory-decoy-personality/zscaler-deception-ad-decoy-personality.png)