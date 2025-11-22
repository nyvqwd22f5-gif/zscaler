# Configuring a Network Decoy Personality
Source: https://help.zscaler.com/deception/configuring-network-decoy-personality
PDF: https://help.zscaler.com/pdf/com/en/1531523.pdf

You can create [internal network](/deception/creating-internal-network-decoy) decoys and [Zero Trust Network](/deception/creating-zero-trust-network-decoy) decoys using network decoy personalities either manually or via [deception strategies](/deception/about-deception-strategy). The configuration of network decoy personalities is similar to configuring the network decoys.
To configure a network decoy personality:
- Go to **Miragemaker **> **Strategy Builder **> **Network Decoys**.
- Click **Add Personality**.
- In the **Personality Details **window:
- On the **General **tab:
- **Name**: Enter a name for the network decoy personality.
- **Description**: Enter a relevant description for the network personality.
- **Hostname Keywords**: Enter a list of keywords (one per line) that must be used to generate hostnames for the network decoys created using this personality.
- **Subdomains**: Enter the subdomains (one per line) that must be used with the network decoys created using this personality.
- **Tags**: Select one or more tags from the drop-down menu that you want to associate with the personality. When decoys are deployed via [deception strategies](/deception/creating-strategy) using a tag, the decoys are created by randomly choosing a personality associated with the tag. To create a new tag, click **Create Tags**, enter a name for the tag, and click **Save.**
- **MAC**: Select the Network Interface Card (NIC) manufacturer whose MAC Address Prefix should be used to generate a pseudo MAC address for the network decoys created using the personality.
- **Use Hostname Modifiers**: Enable to randomly generate a hostname for network decoys at the time of deployment.
[See image.](#zd-npd-add-pd-general)
- On the **Services **tab, configure the required services for the network decoys that are created using this personality. To learn how to configure the services, see [Configuring Services on a Network Decoy](/deception/configuring-services-network-decoy).
- On the **Active Directory **tab:
- **Add to Active Directory**: Enable to add the network decoys created using this personality as objects to the Active Directory.
- **Select OS Attribute**: Select an OS attribute that should appear in the network decoys created using this personality.
- **OU**: Select the Organizational Unit (OU) that you want to associate with network decoys created using this personality.
- **Description**: Enter a relevant description that must be added to the object in the Active Directory for the network decoys created using this personality.
[See image.](#ad-add-npd-ad-tab)
- Click **Submit**.
After configuring a network decoy personality, you can use it to create network decoys either [manually](/deception/using-network-decoy-personalities-and-services) or via [deception strategies](/deception/creating-strategy).
[]![A screenshot capturing the General Tab in the Personality Details window](/downloads/deception/miragemaker/strategy-builder/network-decoy-personalities/configuring-network-decoy-personality/zscaler-deception-personality-details-window.png)
[]![A screenshot capturing the AD tab in the Personlity Details window](/downloads/deception/miragemaker/strategy-builder/network-decoy-personalities/configuring-network-decoy-personality/zscaler-deception-personality-details-AD-tab.png)