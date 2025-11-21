# About High-Interaction Containers
Source: https://help.zscaler.com/deception/about-high-interaction-containers
PDF: https://help.zscaler.com/pdf/com/en/1531453.pdf

High-interaction containers are self-contained docker container datasets that are fully interactive application decoys.
High-interaction containers provide the following benefits and enable you to:
- Upload custom docker images and deploy them as Threat Intelligence (TI) decoys or network decoys.
- Replace static application datasets with fully interactive application datasets.
- Engage adversaries and capture their attention for a longer period to understand their attack strategy.
About the High-Interaction Containers Page
On the High-Interaction Containers page (Miragemaker > High-Interaction Containers), you can do the following:
- View a list of predefined and custom high-interaction container datasets. For each container dataset, you can see:
- **Name**: The name of the container dataset and search for a specific entry.
- **Type**: The type of container dataset. **Web** indicates a web application container dataset and **Custom** indicates a custom protocol container dataset.
- **Ports**: The port on which the service runs inside the docker container.
- **Tag**: The version tag assigned to the container.
- **Description**: The description of the container dataset.
- Configure a [web application](/deception/configuring-web-application-container) or [custom protocol](/deception/configuring-custom-protocol-container) container dataset.
- [Edit or delete a container dataset](/deception/editing-or-deleting-high-interaction-container).![About the High Interaction Containers page](/downloads/deception/miragemaker/application-datasets/high-interaction-containers/about-high-interaction-containers/zscaler-deception-high-interaction-containers.png)
Each container runs a customized application, the format of the data sent in each request varies from application to application. Therefore, some high-interaction container datasets might capture fewer metrics than their static counterparts.