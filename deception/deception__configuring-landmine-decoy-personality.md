# Configuring a Landmine Decoy Personality
Source: https://help.zscaler.com/deception/configuring-landmine-decoy-personality
PDF: https://help.zscaler.com/pdf/com/en/1531533.pdf

Landmine decoy personalities are templates that allow you to use [deception strategies](/deception/about-deception-strategy) to create and deploy landmine decoys. Similar to landmine decoys, the landmine decoy personalities rely on policies to create landmine decoys. The policy configuration for landmine decoy personalities is similar to the policy configuration for [landmine decoys](/deception/about-landmine-decoys).
To create a landmine decoy personality:
- Go to **Miragemaker **> **Strategy Builder **> **Landmine**.
- Click **Add Policy**.
-
In the **Details **window:
- **Name**: Enter the name for the landmine decoy personality.
- **OS**: Select the operating system in which the landmine policies should be deployed.
- **Tags**: Select one or more tags from the drop-down menu that you want to associate with the personality. When decoys are deployed via [deception strategies](/deception/creating-strategy) using a tag, the decoys are created by randomly choosing a personality associated with the tag. To create a new tag, click **Create Tags**, enter a name for the tag, and click **Save.**
- **Agentless**: Enable to deploy the landmine policies without agents.
- **Ask user to review selection criteria**: Enable to allow users to review selection criteria when deploying using deception strategies.
[See image.](#zd-ldp-details)
-
Click **Save**.
The landmine decoy personality is added.
- Locate the landmine decoy personality in the table, and click the **Edit **icon to configure the policies.
-
In the policy configuration window, configure the following lures and settings as required:
- [Selection Criterion](/deception/creating-landmine-policy)
- [Password Settings](/deception/configuring-password-settings)
- [Defense Evasion](/deception/configuring-defense-evasion)
- [Privilege Escalation](/deception/configuring-privilege-escalation)
- [Cloud Lures](/deception/configuring-cloud-lures)
- [Browser Lures](/deception/configuring-browser-lures)
- [Session Lures](/deception/configuring-session-lures)
- [File Decoys](/deception/configuring-file-decoys)
- [Lure Settings](/deception/configuring-lure-settings)
- [Advanced Deception Capabilities](/deception/enable-advanced-deception-capabilities)
[See image.](#zd-policy-ldp)
After configuring a landmine decoy personality, you can use it to create and deploy [landmine decoys](/deception/about-landmine-decoys) via [deception strategies](/deception/about-deception-strategy).
[]![A screenshot capturing the Landmine Decoy Details window](/downloads/deception/miragemaker/strategy-builder/landmine-decoy-personalities/configuring-landmine-decoy-personality/zscaler-deception-landmine-policy-details-window.png)
[]![A screenshot capturing the policy configuration window of a landmine decoy personality](/downloads/deception/miragemaker/strategy-builder/landmine-decoy-personalities/configuring-landmine-decoy-personality/zscaler-deception-policy-details-ldp-new-image.png)