# Adding a Static Application Dataset
Source: https://help.zscaler.com/deception/adding-static-application-dataset
PDF: https://help.zscaler.com/pdf/com/en/1531458.pdf

Static application datasets are web application front ends. These datasets consist of static HTML files, CSS files, JavaScript files, etc. that can be used as an interface to engage adversaries submitting credentials or performing text-based web application attacks.
Zscaler Deception provides a few predefined static application datasets that you can readily use to deploy network decoys. You can add custom static application datasets per your requirements.
Before you can add a static application dataset, you must create a compressed (.zip) file that includes the application dataset's files. The files must be present at the root of the zip file and not in a subdirectory.
To add a static application dataset:
- Go to **Miragemaker** > **Static Application Datasets**.
-
Click **Add Dataset**.
[See image.](#deception-miragemaker-add-static-app-dataset)
-
In the **Static Application Dataset Details** window:
- **Name**: Enter the name of the static application dataset.
-
**Web Server Banner**: Select a web server banner to advertise from the drop-down menu.
Click **Create Web Server Type** to create a new web server banner.
- **Hostname Keywords**: Enter hostname keywords. The Zscaler Deception Admin Portal uses these keywords to recommend hostnames for decoys.
- **Subdomains**: Enter subdomain names. The Deception Admin Portal uses these names to recommend subdomains for decoys.
- **MAC**: Select a system manufacturer's name from the drop-down menu.
- **Upload**: Click to upload the compressed (.zip) file containing the static web application dataset files.
[See image.](#deception-miragemaker-config-static-app-dataset)
-
Click **Submit**.
The static application dataset is added.
After you create the static application dataset, you can use it to deploy a [network decoy](/deception/creating-internal-network-decoy).
[]![Add a Static Application Dataset ](/downloads/deception/miragemaker/application-datasets/static-application-datasets/adding-static-application-dataset/Add_statis%20application.png)
[]![Static Application Dataset Details](/downloads/deception/miragemaker/application-datasets/adding-static-application-dataset/zscaler-deception-config-static-application-dataset.png)