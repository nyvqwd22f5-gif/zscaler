# Adding a Dynamic Application Dataset
Source: https://help.zscaler.com/deception/adding-dynamic-application-dataset
PDF: https://help.zscaler.com/pdf/com/en/1531482.pdf

You can configure dynamic application datasets that can be used in threat intelligence decoys and network decoys to create dynamic web applications that mimic select behaviors and the front-end UI of legitimate applications.
To add a dynamic application dataset:
- Go to **Miragemaker** > **Dynamic Application Datasets**.
- Click **Add Dataset**.
-
In the **Dynamic Application Datasets Details** window:
- **Name**: Enter the name of the dynamic application dataset.
- **Vulnerable Application Dataset**: Select the [vulnerable application dataset](/deception/adding-vulnerable-application-dataset) that must be used to configure the dynamic interactions of the application.
- **Fallback Static Application Dataset**: (Optional) Select a static application dataset that must be used to render the front-end UI of the application.
- **Web Server Banner**: (Optional) Select a web server banner that you want to be advertised from the drop-down menu. You can also create a new web server banner using the **Create Web Server Type** option.
- **Hostname Keywords**: Enter hostname keywords. The Zscaler Deception Admin Portal uses these keywords to recommend hostnames for decoys.
- **Subdomains**: Enter subdomain names. The Deception Admin Portal uses these names to recommend subdomains for decoys.
- **MAC**: Select a system manufacturer's name from the drop-down menu to create a legitimate-looking MAC address that can be used while deploying the decoy.
[See image.](#dynamic-application-datasets-details)
- Click **Submit**.
The dynamic application dataset is added.
After you create the dynamic application dataset, you can use it to deploy a [Threat Intelligence (TI) decoy](/deception/creating-internal-network-decoy) or [network decoy](/deception/creating-threat-intelligence-decoy).
[]![A screenshot of the Dynamic Application Datasets Details page in the Zscaler Deception Portal](/downloads/deception/miragemaker/application-datasets/adding-dynamic-application-dataset/zscaler-deception-adding-dynamic-application-dataset.jpg)