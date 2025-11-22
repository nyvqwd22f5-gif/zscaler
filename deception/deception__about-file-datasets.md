# About File Datasets
Source: https://help.zscaler.com/deception/about-file-datasets
PDF: https://help.zscaler.com/pdf/com/en/1531445.pdf

File datasets are realistic-looking decoy files and folders that you can use to configure network and landmine decoys.
File datasets provide the following benefits and enable you to:
- Deploy decoys quickly using the predefined file datasets based on industry, type of servers, or devices.
- Configure custom file datasets (static or dynamic) to enhance the authenticity of the decoy files.
You can use file datasets in the following use cases:
- Network deception: Populate decoy services that host files, such as Shares and FTP. For example, create a file dataset that seems to belong to the legal department, and deploy it on a decoy file server in a network segment.
- Landmine deception: Configure decoy files that match a user or system profile. For example, create a file dataset that mimics IT files and deploy them on an IT user endpoint.
About the File Datasets Page
On the File Datasets page (Miragemaker > Files > File Datasets), you can do the following:
-
View a list of predefined and custom file datasets. For each dataset, you can see:
- **Name**: The name of the file dataset.
- **Is Dynamic**: Indicates if the file dataset is dynamic or not.
The **GenAI** icon indicates a generative AI file dataset.
- Add a custom [static](/deception/adding-static-file-dataset) or [dynamic](/deception/adding-dynamic-file-dataset) file dataset.
- [Download a file dataset](/deception/downloading-file-dataset).
- [Edit or delete a file dataset](/deception/editing-or-deleting-file-dataset).
![A screenshot showing carious options in the File Datsets page](/downloads/deception/miragemaker/file-datasets-templates/file-datasets/about-file-datasets/zscaler-deception-about-file-datasets.png)