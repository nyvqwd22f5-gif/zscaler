# Creating a Strategy
Source: https://help.zscaler.com/deception/creating-strategy
PDF: https://help.zscaler.com/pdf/com/en/1531461.pdf

You can create a custom strategy to configure Network decoys, Threat Intelligence (TI) decoys, Active Directory (AD) decoys, and Landmine policies on a single page. When you create a strategy, you define a list of personalities or tags that must be deployed together to run a deception campaign for a particular use case. For example, when you configure a strategy for ransomware, you enable the endpoints ransomware detection feature along with network share decoys on the network.
Prerequisites
Before you create a Deception strategy, identify the following requirements:
- A use case such as Log4j, Conti Ransomware, etc.
- A department such as Information Technology (IT), Banking, Legal, Finance, etc.
- The type of decoys that are critical for deployment. For example, Network decoys, AD decoys, etc.
- The total number of decoys to be deployed.
Creating a Strategy
To create a strategy:
- Go to **Miragemaker **>** Strategy Builder **>** Deception Strategy**.
- Click **Add Strategies**.
[See image.](#deception-add-deception-strategy-option)
- In the **Strategy Detail** window:
-
[]On the **General** tab:
- **Name**: Enter the name of the strategy.
- **Description**: Enter the description of the strategy.
[See image.](#deception-strategy-general-settings)
-
[]On the **Network Decoys** tab, click **Add** to create a Network decoy:
- **Use Tag**: Enable to choose a tag for the Network decoy.
- **Personality/Tag**: Select a tag or personality from the drop-down menu. If **Use Tag** is enabled, this drop-down menu lists tags, otherwise it lists personalities.
- **Count**: Enter the number of Network decoys you want to create for the selected personality or tag.
[See image.](#deception-strategy-network-decoys-setting)
-
[]On the **Threat Intelligence** tab, click **Add** to create a Threat Intelligence (TI) decoy:
- **Use Tag**: Enable to choose a tag for the TI decoy.
- **Personality/Tag**: Select a tag or personality from the drop-down menu. If **Use Tag** is enabled, this drop-down menu lists tags, otherwise it lists personalities.
- **Count**: Enter the number of TI decoys you want to create for the selected personality or tag.
[See image.](#deception-strategy-TI-decoys-settings)
-
[]On the **Active Directory** tab, click **Add** to create an Active Directory (AD) decoy:
- **Use Tag**: Enable to choose a tag for the AD decoy.
- **Personality/Tag**: Select a tag or personality from the drop-down menu. If **Use Tag** is enabled, this drop-down menu lists tags, otherwise it lists personalities.
- **Count**: Enter the number of AD decoys you want to create for the selected personality or tag.
[See image.](#deception-strategy-AD-decoys-settings)
-
[]On the **Landmine** tab, select decoy personalities from the **Personalities** drop-down menu.
[See image.](#deception-strategy-landmine-decoy-settings)
- Click **Validate **to ensure that the corresponding Network, AD, and TI decoys are available for the configured landmine lures.
[See image.](#deception-validate-deception-strategy)
- After the strategy is validated, click **Save**.
The strategy is created.
[See image.](#deception-strategy-added)
After the strategy is created, you can [deploy it](/deception/deploying-deception-strategy-using-internal-network-decoy).
[]![The Deception Strategy page with an annotation around the Add Strategies button](/downloads/deception/miragemaker/strategy-builder/deception-strategy/creating-strategy/zscaler-decption-add-startegies-option-6.png)
[]![The Strategy Details window with an annotation around the General tab](/downloads/deception/miragemaker/strategy-builder/deception-strategy/creating-strategy/zscaler-decption-add-startegies-general-config-1.png)
[]![The Strategy Details window with an annotation around the Network Decoys tab](/downloads/deception/miragemaker/strategy-builder/deception-strategy/creating-strategy/zscaler-decption-add-startegies-nw-decoys-config-1.png)
[]![The Strategy Details window with an annotation around the Threat Intelligence tab](/downloads/deception/miragemaker/strategy-builder/deception-strategy/creating-strategy/zscaler-decption-add-startegies-ti-decoys-config-1.png)
[]![The Strategy Details window with an annotation around the Active Directory tab](/downloads/deception/miragemaker/strategy-builder/deception-strategy/creating-strategy/zscaler-decption-add-startegies-ad-decoys-config-1.png)
[]![The Strategy Details window with an annotation around the Landmine tab](/downloads/deception/miragemaker/strategy-builder/deception-strategy/creating-strategy/zscaler-decption-add-startegies-landmine-decoys-config-1.png)
[]![Landmine strategies validated on the Strategy Details window](/downloads/deception/miragemaker/strategy-builder/deception-strategy/creating-strategy/zscaler-decption-add-startegies-validated-landmine-2.png)
[]![The Deception Strategy page with an annotation around the new strategy that is added](/downloads/deception/miragemaker/strategy-builder/deception-strategy/creating-strategy/zscaler-decption-add-startegy-created-7.png)