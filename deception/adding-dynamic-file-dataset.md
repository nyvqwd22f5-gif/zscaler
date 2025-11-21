# Adding a Dynamic File Dataset
Source: https://help.zscaler.com/deception/adding-dynamic-file-dataset
PDF: https://help.zscaler.com/pdf/com/en/1531446.pdf

You can configure a file dataset that dynamically generates files for a network or endpoint decoy. Every time a decoy with a dynamic dataset is deployed, a new set of files is generated and then copied to the decoy.
To add a dynamic file dataset:
- Go to **Miragemaker** > **Files** > **File Datasets**.
-
Click **Add Dataset** > **Add Dynamic**.
[See image.](#deception-file-dataset-add-dynamic-option)
-
In the **File Dataset Details** window, provide values for the following fields:
- **Name**: Enter the name of the file dataset.
- **File Classification by Department**: Select the type of industry for which you want to generate the file dataset from the drop-down menu (e.g., **Human resources**, **Legal**, **IT-Security**, etc.).
- **File Templates**: Select the type of decoy file you want to deploy from the drop-down menu (e.g., **Backup Files**, **Default password protected files**, etc.). You can create custom file templates.
- **Custom Keywords**: Enter the keywords you want to include for the industry type. These keywords are used in file name permutations. For example, enter the organization names or abbreviations, upcoming project names, or any other keywords that might be of interest to an adversary.
- **Minimum Date **and** Maximum Date**: Select the start and end date. The dataset files appear on the endpoints for the specified date range.
- **Minimum Folders **and** Maximum Folders**: Enter the minimum and maximum numbers of folders. This range is used to randomly select a few folders every time an instance of a file dataset is generated for a decoy.
- **Minimum Files Per Folder** and **Maximum Files Per Folder**: Enter the minimum and maximum files per folder. This range is used to randomly select a few files per folder every time an instance of a file dataset is generated for a decoy.
[See image.](#deception-file-dataset-config-dynamic-details)
-
Click **Submit**.
The dynamic file dataset is added.
[See image.](#deception-file-dataset-dynamic-dataset-added)
[]![A screenshot highlighting the option to add dynamic dataset](/downloads/deception/miragemaker/file-datasets-templates/file-datasets/adding-dynamic-file-dataset/zscaler-deception-add-dynamic-dataset.png)
[]![Configure a dynamic file dataset](/downloads/deception/miragemaker/file-datasets/adding-dynamic-file-dataset/zscaler-deception-dynamic-dataset-config-details.png)
[]![A screenshot highlighting the newly added dataset](/downloads/deception/miragemaker/file-datasets-templates/file-datasets/adding-dynamic-file-dataset/zscaler-deception-dataset-new-dynamic.png)