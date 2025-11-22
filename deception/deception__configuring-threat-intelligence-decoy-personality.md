# Configuring a Threat Intelligence Decoy Personality
Source: https://help.zscaler.com/deception/configuring-threat-intelligence-decoy-personality
PDF: https://help.zscaler.com/pdf/com/en/1531528.pdf

Threat intelligence (TI) decoy personalities are templates that you can use in [deception strategies](/deception/about-deception-strategy) to create and deploy [TI decoys](/deception/about-threat-intelligence-decoys).
To create a TI decoy template:
- Go to **Miragemaker **> **Strategy Builder **> **Threat Intelligence Decoy**.
- Click **Add Personality**.
- In the **Decoy Details **window:
- **Name**: Enter the name for the decoy personality.
- **Tags**: Select one or more tags from the drop-down menu that you want to associate with the personality. When decoys are deployed via [deception strategies](/deception/creating-strategy) using a tag, the decoys are created by randomly choosing a personality associated with the tag. To create a new tag, click **Create Tags**, enter a name for the tag, and click **Save.**
- **Subdomains**: Enter the subdomains (one per line) that must be used with the TI decoys created using this personality.
- **Description**: Enter a relevant description for the personality.
- **Decoy Type**: Select the type of application decoy (**Static Application**, **Dynamic Application**, or **High Interaction Container**) that you want to deploy with the TI decoys created using this personality.
- **Datasets**: Based on the **Decoy Type** selection, select the application dataset that you want to deploy with the TI decoys that are created using this personality. You can add multiple datasets. To add an additional dataset, click **Add. **Select your preferred application datasets. For each dataset, enable or disable **Allow Port 80** to allow or block access to the application decoy via HTTP without encryption.
[See image.](#zd-tidp-details)
- Click **Save**.
After configuring a TI decoy personality, you can use it to create and deploy [TI decoys](/deception/about-threat-intelligence-decoys) via [deception strategies](/deception/about-deception-strategy).
[]![A screenshot capturing the TI Decoy Details window](/downloads/deception/miragemaker/strategy-builder/threat-intelligence-decoy-personalities/zscaler-deception-decoy-details-configuration.png)