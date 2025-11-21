# Deploying a Strategy
Source: https://help.zscaler.com/deception/deploying-strategy
PDF: https://help.zscaler.com/pdf/com/en/1531462.pdf

You can deploy single or combined strategies to build and deploy environments with a single click.
Prerequisites
Before you can deploy strategies, make sure the following prerequisites are met:
-
Configure VLANs or subnets for placing the decoys. The VLANs or subnets must be trunked or passed through the virtual NICs of the Decoy Connector. To learn more, see [Configuring a Subnet](/deception/configuring-subnet).
This prerequisite is applicable to Internal decoys only.
- Have free IP addresses for trunked VLANs or subnets.
Deploying a Strategy
To deploy a single or combined strategies:
- Go to **Deceive** > **Deploy Strategy**.
- Click **Stop Decoys**.
- []Do one of the following to select a decoy type for the strategy:
- Click **Add Strategies** to create and deploy ZPA decoys on a dedicated cloud environment that is accessible using the Zscaler Private Access (ZPA) Zero Trust Network Access (ZTNA) platform.
-
Click the **Expand** icon next to **Add Strategies**, and then select **Internal Decoys** to create and deploy decoys within your organization's network.
[See image.](#deception-add-strategy-using-internal-decoys)
- In the **Deploy Network Strategy** window:
-
(Applicable to ZPA decoys only) Under **ZPA**, the **ZPA** toggle and all the ZPA domains are selected by default. You can click **Create domain** to add a new domain.
Enable **Real App** if you want to add and deploy ZPA decoys on unused ports of a real or production ZPA application segment.
- Under **Threat Intelligence Decoys**:
- **Enabled**: Select to enable Threat Intelligence (TI) decoys.
- **Domains**: Select a domain from the drop-down menu. Click **Create domain** to add a new domain.
- []Under **Active Directory Decoys**:
- **Enabled**: Select to enable Active Directory (AD) decoys.
- []**Domains**: Select a domain from the drop-down menu. Click **Create domain** to add a new domain. To learn more, see [Adding an Active Directory Domain](/deception/adding-active-directory-domain).
-
Under **Landmine Policy**, select **Enabled** to enable the landmine policy.
Landmine policy is enabled by default if you have selected [ZPA decoys](#deception-deploy-strategy-select-decoy-type).
[See image.](#deception-configure-network-strategy)
- Click **Next**.
-
Select one or more strategies from the **Strategies** drop-down menu. Only those strategies that match the decoy configuration are listed.
The **Default Automatic Decoys** strategy is selected by default.
-
The **Set Decoy Limit** displays the total number of decoys you can create for the selected strategy. Click the up arrow to increase the decoys by multiples of 1, 2, 3, etc. For example, if the selected strategy has 1 Network, 2 TI, and 2 AD decoys, click the up arrow to increase the count by multiples of 2. As a result, 2 Network, 4 TI, and 4 AD decoys are created. Alternatively, you can enter a number to increase the count.
[See image.](#deception-select-strategy-decoy-limit)
The** License Limit **displays the decoy limitations for your license plan. To learn more, see [Ranges & Limitations](/deception/ranges-and-limitations).
-
Click **Next**.
Configure the required decoy type depending on the selected strategy:
If a decoy type is not a part of the selected strategy, that particular decoy tab is disabled. For example, if the selected strategy doesn't include AD decoys, then the **Active Directory Decoys** tab is disabled.
- [Network decoys](#deception-deploy-strategy-config-network-decoy-step)
- [TI decoys](#deception-deploy-strategy-config-ti-step)
- [AD decoys](#deception-deploy-strategy-config-ad-step)
- [Landmine decoys](#deception-deploy-strategy-config-landmine-policy-step)
-
Click** Next**.
Under **Save Network Strategy**, the network strategy name is saved with the default naming convention (<`Strategy name`> <`Date and time`>).
-
Click **Create Decoys & Deploy **to create decoys and automatically deploy them. Use this option if there are no decoys deployed in the Deception Admin Portal, or all the active decoys are stopped.
If there are decoys that are already deployed, and you don't want to retrigger deployment automatically at the time of decoy creation, you can click **Create Decoys** to create new decoys and deploy them later.
[See image.](#deception-create-deploy-strategies)
The decoys that are in the strategy are created and deployed.
[See image.](#deception-strategies-deployed)
- Click **Start Decoys **for the configurations to take effect.
[]On the **Network Decoys** tab, configure the network decoys. If there are any [generative AI decoys ](/deception/understanding-generative-ai-decoys)that are deployed, they appear at the top of the page:
- **Hostname**: This field is automatically populated. Click the **Autogenerate** icon (![Autogenerate icon](/downloads/deception/deceive/network-decoys/creating-internal-network-decoy/zscaler-deception-auto-generate-icon.png)
) to generate another hostname suggestion, or manually enter a hostname. Make sure the hostname that represents the personality to a greater extent for better deployment. For example, if the personality is configured for a VPN, enter a hostname that represents a VPN server. Click the **Copy** icon (![zscaler-deception-deploy-network-strategy-copy-icon.png](/downloads/deception/deceive/deploy-strategy/deploying-strategy/zscaler-deception-deploy-network-strategy-copy-icon.png)
) to copy the hostname.
-
**Network Segment/Subnet**: Select a subnet where you want to place the decoy. Make sure to select a network segment where real VPN servers are also deployed.
This field is applicable to Internal decoys only and doesn't appear if the [decoy type](#deception-deploy-strategy-select-decoy-type) is a ZPA decoy.
-
**IP**: Enter an unused and unique IP address for static network segments. You can leave this field blank for DHCP.
This field is applicable to Internal decoys only and doesn't appear if the [decoy type](#deception-deploy-strategy-select-decoy-type) is a ZPA decoy.
-
**IPv6**: Enable the toggle and enter an unused and unique IPv6 address in the text field that appears. You can only configure IPv6 if you select an IPv6 subnet in the **Network Segment/Subnet **field.
This field is applicable to Internal decoys only and doesn't appear if the [decoy type](#deception-deploy-strategy-select-decoy-type) is a ZPA decoy.
-
**Personality**: The personality represents the type of Network decoy that is being created. This field is automatically populated.
[See image.](#deception-network-decoy-strategy-config)
[]On the **Threat Intelligence Decoys** tab, configure the TI decoys:
- **Hostname**: This field is automatically populated. You can click the **Autogenerate** icon (![Autogenerate icon](/downloads/deception/deceive/network-decoys/creating-internal-network-decoy/zscaler-deception-auto-generate-icon.png)
) to generate another hostname suggestion, or manually enter a hostname. Make sure that you enter a hostname that represents the personality to a greater extent for better deployment. For example, if the personality is configured for a VPN, then make sure to enter a hostname that represents a VPN server. Click the **Copy** icon (![zscaler-deception-deploy-network-strategy-copy-icon.png](/downloads/deception/deceive/deploy-strategy/deploying-strategy/zscaler-deception-deploy-network-strategy-copy-icon.png)
) to copy the hostname.
- **Dataset**: The dataset defines the type of system the decoy mimics. This field is automatically populated.
-
**Personality**: The personality represents the type of TI decoy that is being created. This field is automatically populated.
[See image.](#deception-ti-decoy-strategy)
[]On the **Active Directory Decoys** tab, configure the AD decoys:
- **Username**: This field is automatically populated. You can click the **Autogenerate** icon (![Autogenerate icon](/downloads/deception/deceive/network-decoys/creating-internal-network-decoy/zscaler-deception-auto-generate-icon.png)
) to generate another hostname suggestion, or manually enter a hostname.
- **Domain**: This field represents the domain the decoy belongs to. If [multiple domains](#deception-deploy-strategy-select-domain) were selected, then the field displays the domain in which the decoy is deployed. This field is automatically populated.
-
**Personality**: The personality represents the type of AD decoy that is being created. This field is automatically populated.
[See image.](#deception-ad-decoy-strategy-config)
[]On the **Landmine Policy** tab, configure the Landmine decoys:
- **Name**: The name of the Landmine policy.
- **Agentless**: The **X** icon indicates landmine agent, and the checkmark icon indicates landmine agentless.
-
**Personality Name**: The personality represents the type of Landmine policy that is being created. This field is automatically populated.
[See image.](#deception-landmine-policy-setting-strategy)
- **Selection Criteria**:
-
Click the **Edit** icon under **Actions** to configure the landmine policy's **Selection Criteria** and **Password Settings**. Make sure to select selection criteria that are only deployed on relevant machines. For example, if you are configuring selection criteria for a personality for the IT department, then the criteria must be deployed on the relevant hosts only. To learn more, see [Specifying Selection Criteria](/deception/creating-landmine-policy) and [Configuring Password Settings](/deception/configuring-password-settings).
[See image.](#deception-landmine-policy-config-selection-creteria)
-
Click **Next**.
[See image.](#deception-landmine-select-criteria-configured)
The landmine policy's selection criteria and password settings are configured.
[]![Add ZPA or Internal Decoys strategy](/downloads/deception/deceive/deploy-strategy/deploying-strategy/zscaler-deception-add-strategies-internal-decoys.png)
[]![Configure deploy strategy](/downloads/deception/deceive/deploy-strategy/deploying-strategy/zscaler-deception-deploy-network-strategy-settings-with-zpa-1.png)
[]![Select deploy strategies and set decoy limit](/downloads/deception/deceive/deploy-strategy/deploying-strategy/zscaler-deception-deploy-network-strategy-select-strategy-limit-3.png)
[]![Configure deploy strategy for network decoys](/downloads/deception/deceive/deploy-strategy/deploying-strategy/zscaler-deception-deploy-strategy-network-decoy-settings-2.png)
[]![Configure deploy strategy for TI decoys](/downloads/deception/deceive/deploy-strategy/deploying-strategy/zscaler-deception-deploy-strategy-ti-decoy-settings-1.png)
[]![Configure deploy strategy for AD decoys](/downloads/deception/deceive/deploy-strategy/deploying-strategy/zscaler-deception-deploy-strategy-ad-decoy-settings-1.png)
[]![Configure Landmine selection criteria](/downloads/deception/deceive/deploy-strategy/deploying-strategy/zscaler-deception-deploy-landmine-selection-criteria-settings-2.png)
[]![Configure deploy strategy for Landmine decoys](/downloads/deception/deceive/deploy-strategy/deploying-strategy/zscaler-deception-deploy-landmine-strategy-settings-1.png)
[]![Landmine decoy selection criteria configured](/downloads/deception/deceive/deploy-strategy/deploying-strategy/zscaler-deception-deploy-landmine-strategy-criteria-configured.png)
[]![Create deploy strategy](/downloads/deception/deceive/deploy-strategy/deploying-strategy/zscaler-deception-strategy-name-create.png)
[]![Decoys created and deployed](/downloads/deception/deceive/deploy-strategy/deploying-strategy/zscaler-deception-strategy-created-deployed-1.png)