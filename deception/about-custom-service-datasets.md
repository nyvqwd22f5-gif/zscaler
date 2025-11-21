# About Custom Service Datasets
Source: https://help.zscaler.com/deception/about-custom-service-datasets
PDF: https://help.zscaler.com/pdf/com/en/1531545.pdf

A custom service dataset is a mechanism that creates custom network services with customized requests and responses. The custom services can be created over any binary or text-based protocols in the application layer and can then be deployed using [network decoys](/deception/about-network-decoys). When deploying using network decoys, you can configure specific ports and network layer protocols (TCP or UDP). The adversaries can interact with the custom service via the port and protocol configured for [custom services in the network decoys](/deception/configuring-services-network-decoy#configuring-scada-iot-service). Typically, you can use custom service datasets to set up network deception for services that are available by default with network decoys.
Custom service datasets provide the following benefits and enable you to:
- Set up active defense using any custom network services with customized requests and responses over any binary or text-based protocols.
- Extend the network deception capabilities by creating network decoys with custom services that are not available by default.
- Leverage existing datasets or create new datasets that mimic custom services and deploy them using network decoys via specific ports and network protocols (TCP or UDP).
About the Custom Service Datasets Page
On the Custom Service Datasets Page (Miragemaker > Custom Service Dataset), you can do the following:
- View the list of custom service datasets, and search for a specific dataset by its name.
- [Configure a custom service dataset](/deception/configuring-custom-service-dataset).
- [Edit or delete a custom service dataset](/deception/editing-or-deleting-custom-service-dataset).
![A screeshot capturing the custom services datasets page](/downloads/deception/miragemaker/custom-service-datasets/about-custom-service-datasets/zscaler-deception-about-custom-service-datasets_0.png)