# Configuring a Custom Service Dataset
Source: https://help.zscaler.com/deception/configuring-custom-service-dataset
PDF: https://help.zscaler.com/pdf/com/en/1531546.pdf

You can create custom service datasets and use them in network decoys to configure network deception using custom services.
To create a custom service dataset:
- Go to **Miragemaker **> **Custom Service Datasets**.
-
Click **Add Dataset**.
[See image.](#zd-csd-add-option)
-
In the **Custom Service Dataset Details **window:
- **Name**: Enter a name for the custom service dataset.
- **Protocol**: Select the application layer protocol type (**Binary **or **Text**) that you want for your custom service.
- **Banner**: (Optional) Enter the banner message that is shown to adversaries when a connection is established with the service using network decoys. For binary protocols, the value entered for this field must be a Base64-encoded text.
- **Default Response**: (Optional) Enter the default response that is sent for unknown requests from adversaries. For binary protocols, the value entered for this field must be a Base64-encoded text.
- **Messages**: Configure request and response messages for the custom service as required. To add a request and its response, click **Add**, and enter the request and response value in the respective columns. For binary protocols, the values entered for request and response must be a Base64-encoded text.
[See image.](#zd-csd-details-window)
- Click **Submit**.
After configuring a custom service dataset, you can use it to set up network deception by configuring services on network decoys. To learn more, see [Configuring Services on a Network Decoy](/deception/configuring-services-network-decoy#configuring-scada-iot-service).
[]![A screenshot capturing the option to add a custom service dataset](/downloads/deception/miragemaker/custom-service-datasets/configuring-custom-service-dataset/zscaler-deception-add-custom-service-datasets.png)
[]![A screenshot capturing the Custom Service Dataset Details window](/downloads/deception/miragemaker/custom-service-datasets/configuring-custom-service-dataset/zscaler-deception-add-or-edit-custom-service-dataset.png)