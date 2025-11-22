# Configuring a Web Application Container
Source: https://help.zscaler.com/deception/configuring-web-application-container
PDF: https://help.zscaler.com/pdf/com/en/1531451.pdf

You can create a web application container dataset that is a fully interactive application, such as Drupal, Jenkins, Joomla, etc., and deploy it as a Threat Intelligence (TI) or network decoy.
Before you create a web application container dataset, you must [create a docker image](/deception/creating-high-interaction-docker-container-image).
To create a web application container dataset:
- Go to **Miragemaker** > **High-Interaction Containers**.
-
Click **Add Container** > **Web Application**.
[See image.](#deception-add-web-app-container-option)
-
In the **Web Application Container** **Details** window:
- **Name**: Enter the name of the container.
- **Description**: Enter the description of the custom container.
-
**Port**: Enter the port number that the service running inside the docker container is listening to.
The port details cannot be changed after you save the container configuration. If you want to change the port details, you must delete and upload the docker image file again.
- **Hostname Keywords**: Enter hostname keywords. Zscaler Deception Admin Portal uses these keywords to recommend hostnames for decoys.
- **Subdomains**: Enter subdomain names. The Deception Admin Portal uses these names to recommend subdomain names for decoys.
- **MAC**: Select a system manufacturer's name from the drop-down menu.
- **Upload docker (tar/gzipped tar)**: Drag and drop the docker image (.tar.gz) file you created, or click **Browse** to upload the docker file.
[See image.](#deception-config-web-application-container)
-
Click **Submit**.
The web application container dataset is added to the **High-Interaction Containers** page.
After you create the web application container dataset, you can use it to deploy a [TI ](/deception/creating-threat-intelligence-decoy)or [network decoy](/deception/creating-internal-network-decoy).
[]![Add web application container option](/downloads/deception/miragemaker/understanding-miragemaker-module/zscaler-deception-web-application-high-interaction-containers.png)
[]![Configure a web application container](/downloads/deception/miragemaker/application-datasets/configuring-web-application-container/zscaler-deception-web-app-container-configuration-1.png)