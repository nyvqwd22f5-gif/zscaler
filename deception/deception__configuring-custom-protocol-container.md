# Configuring a Custom Protocol Container
Source: https://help.zscaler.com/deception/configuring-custom-protocol-container
PDF: https://help.zscaler.com/pdf/com/en/1531452.pdf

You can create a custom protocol container dataset, which is a non-web application (e.g., PostgreSQL database server), and deploy it as a network decoy.
Before you create a custom container dataset, you must [create a docker image](/deception/creating-high-interaction-docker-container-image).
To create a custom protocol container:
- Go to **Miragemaker** > **High-Interaction Containers**.
-
Click **Add Container** > **Other custom protocols**.
[See image.](#deception-add-custom-protocol-container-option)
-
In the **Other Custom Protocols Container Details** window:
- **Name**: Enter the name of the container.
- **Description**: Enter a description for the container.
- **Port**: Enter the port number that the service running inside the docker container is listening to.
- **Upload docker file (tar/gzipped tar)**: Drag and drop the docker image (.tar.gz) file you created, or click **Browse** to upload the file.
[See image.](#deception-config-other-protocol-container)
-
Click **Submit**.
The custom protocol container dataset is added to the **High-Interaction Containers** page.
After you create the custom protocol container dataset, you can use it as a service to deploy a [network decoy](/deception/creating-internal-network-decoy).
[]![Add a custom protocol container option](/downloads/deception/miragemaker/application-datasets/high-interaction-containers/configuring-custom-protocol-container/zscaler-deception-other-protocol-high-interaction-containers_0.png)
[]![Configure other custom protocols container](/downloads/deception/miragemaker/application-datasets/configuring-custom-protocol-container/zscaler-deception-config-custom-protocols-container.png)