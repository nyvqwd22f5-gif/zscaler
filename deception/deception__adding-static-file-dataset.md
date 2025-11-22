# Adding a Static File Dataset
Source: https://help.zscaler.com/deception/adding-static-file-dataset
PDF: https://help.zscaler.com/pdf/com/en/1531447.pdf

You can configure a static file dataset if you don't want the files to be modified before deploying. Each decoy configured with a static dataset contains an exact copy of the files in the static dataset.
Before adding a static file dataset, you must have the required files in a compressed (.zip) file.
To add a static file dataset:
- Go to **Miragemaker** > **File** > **File Datasets**.
-
Click **Add Dataset** > **Add Static**.
[See image.](#deception-static-file-dataset-add-option)
-
In the **File Dataset Details** window:
- Enter a **Name** for the dataset.
- Click **Upload** and browse to upload the compressed (.zip) file.
[See image.](#deception-static-file-dataset-config-details)
-
Click **Submit**.
The static file dataset is added.
[See image.](#deception-static-file-dataset-added)
[]![A screenshot highlighting the option to a static dataset](/downloads/deception/miragemaker/file-datasets-templates/file-datasets/adding-static-file-dataset/zscaler-deception-add-static-datset.png)
[]![Configure a static file dataset](/downloads/deception/miragemaker/file-datasets/adding-static-file-dataset/zscaler-deception-static-dataset-config-details.png)
[]![A screenshot highlighting a newly added dataset](/downloads/deception/miragemaker/file-datasets-templates/file-datasets/adding-static-file-dataset/zscaler-deception-dataset-new.png)