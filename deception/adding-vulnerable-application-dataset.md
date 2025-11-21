# Adding a Vulnerable Application Dataset
Source: https://help.zscaler.com/deception/adding-vulnerable-application-dataset
PDF: https://help.zscaler.com/pdf/com/en/1531479.pdf

You can configure vulnerable application datasets to emulate the requests and responses in dynamic web applications that are deployed using threat intelligence decoys and network decoys.
Before you can add a vulnerable application dataset, you must create a compressed (.zip) file that includes the necessary application dataset's files. The files must be present at the root of the zip file and not in a subdirectory. These files are requests and responses in YAML format. You can create these files based on the CVE disclosures for publicly disclosed vulnerabilities. To mimic a specific behavior of a legitimate application, you must extract necessary requests and responses by interacting with the legitimate application using web crawlers or other tools, and then create a YAML file for the requests and responses.
To add a vulnerable application dataset:
- Go to **Miragemaker** > **Vulnerable Application Datasets (CVE Datasets)**.
- Click **Add Dataset**.
-
In the **Vulnerable Application Datasets (CVE Datasets) Details** window:
- **Name**: Enter the name of the vulnerable application dataset.
- **Vulnerability Classification**: (Optional) Select the classification of the vulnerability mimicked by the vulnerable application dataset from the drop-down menu.
- **Description**: (Optional) Provide a description for the vulnerable application dataset.
- **CVE ID**: (Optional) Enter the CVE identifier assigned to the publicly disclosed vulnerability configured in the application dataset.
- **Tags**: (Optional) Select a tag that is appropriate for the vulnerable application dataset. To create new tags, enter a value and press `Enter`.
- **Upload**: Click to upload the compressed (.zip) file that has the vulnerable application dataset files. The compressed file size cannot exceed 5 MB.
[See image.](#vulnerable-application-datasets-details)
-
Click **Submit**.
The vulnerable application dataset is added.
After you create the vulnerable application dataset, you can use it to configure [dynamic application datasets](/deception/about-dynamic-application-datasets).
[]![A screenshot of the Vulnerable Application Datasets (CVE Datasets) Details page in the Zscaler Deception Portal](/downloads/deception/miragemaker/application-datasets/adding-vulnerable-application-dataset/zscaler-deception-adding-vulerable-application-dataset.jpg?1680773029)