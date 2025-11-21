# Configuring and Managing Datalists
Source: https://help.zscaler.com/deception/configuring-and-managing-datalists
PDF: https://help.zscaler.com/pdf/com/en/1531596.pdf

Datalists are ready-to-use parameters containing key-value pairs that can be used in various decoy personalities and generative AI decoys. Each datalist can have multiple key-value pairs and each key can have multiple values mapped to it. By default, Zscaler Deception provides a list of preconfigured datalists that can be used in [Network Decoy personalities](/deception/configuring-network-decoy-personality) (as Active Directory OUs), [Active Directory Decoy personalities](/deception/configuring-active-directory-decoy-personality) (as Group Memberships), [Landmine personalities](/deception/configuring-landmine-decoy-personality) (as Fakes in Defense Evasion), and interactive [generative AI decoys](/deception/configuring-services-network-decoy#deception-config-service-gen-ai-hi-interaction-app-section) (as Model Names). In addition, you can create custom datalists based on your requirements.
Creating a Datalist
To create a datalist:
- Go to **Miragemaker **> **Miscellaneous **> **Datalist**.
-
Click** Add Datalist**.
[See image.](#add-datalist-option)
The **Datalist Details** window appears.
-
In the **Datalist Details** window:
- **Name**: Enter a name for the datalist.
- For **Item 1**, configure the following fields:
-
**Key**: Select a key from the drop-down menu that must be associated with the datalist.
Alternatively, you can create a new key. To create a new key, click **Create new key**, enter a name for the key, and click **Save**.
[See image.](#create-new-key)
-
**Value**: Enter the values that must be mapped with the selected key. You can add multiple values. Each value must be on a new line.
When you select specific keys, the maximum number of values that can be added is restricted to 20.
[See image.](#keys_with_restriction)
-
(Optional) Click **Add data** to add another item to the datalist and configure the key-value pairs.
[See image.](#add-optional-item)
[See image.](#datalist-details-window)
- Click **Save**.
Downloading Datalists
To download a datalist:
- Go to **Miragemaker **> **Miscellaneous **> **Datalist**.
-
Locate the datalist that you want to download, and click the **Download **icon.
[See image.](#download-datalist)
The datalist is downloaded to your system as a JSON file.
To download all datalists:
- Go to **Miragemaker **> **Miscellaneous **> **Datalist**.
-
Click **Export**.
[See image.](#export-datalist)
All datalists are downloaded to your system as a collection in a ZIP file.
Editing a Datalist
To edit a datalist:
- Go to **Miragemaker **> **Miscellaneous **> **Datalist**.
- Locate the datalist that you want to edit, and click the **Edit **icon.
-
Modify the name, keys, values, or items as required.
[See image.](#edit-datalist)
- Click **Submit**.
The default datalists cannot be edited.
Deleting a Datalist
To delete a datalist:
- Go to **Miragemaker **> **Miscellaneous **> **Datalist**.
-
Locate the datalist that you want to delete, and click the **Delete **icon.
[See image.](#delete-datalist)
- In the confirmation window, click **OK**.
The default datalists cannot be deleted.
[]
![A screenshot highlighting the option to add a datalist](/downloads/deception/miragemaker/miscellaneous/configuring-and-managing-datalists/zscaler-deception-add-datalist-button.png)
[]
![A set of screenshots showing the steps to create a new key for a datalist](/downloads/deception/miragemaker/miscellaneous/configuring-and-managing-datalists/zscaler-deception-new-key.png)
[]![A set of screenshots showing the steps to create a new item in a datalist](/downloads/deception/miragemaker/miscellaneous/configuring-and-managing-datalists/zscaler-deception-datalist-add-data-item_0.png)
[]
![A screenshot showing the Datalist Details window](/downloads/deception/miragemaker/miscellaneous/configuring-and-managing-datalists/zscaler-deception-datalist-details.png)
[]
![A screenshot highlighing the option to download a datalist](/downloads/deception/miragemaker/miscellaneous/configuring-and-managing-datalists/zscaler-deception-download-datalist.png)
[]
![A screenshot highlighing the option to export a datalist](/downloads/deception/miragemaker/miscellaneous/configuring-and-managing-datalists/zscaler-deception-export-datalists.png)
[]
![A screenshot highlighting the option to edit a datalist](/downloads/deception/miragemaker/miscellaneous/configuring-and-managing-datalists/zscaler-deception-edit-datalists.png)
[]
![A screenshot highlighting the option to delete a datalist](/downloads/deception/miragemaker/miscellaneous/configuring-and-managing-datalists/zscaler-deception-delete-datalist.png)
[]
![View keys with restriction](/downloads/deception/miragemaker/miscellaneous/configuring-and-managing-datalists/zscaler-deception-datalist-keys-restriction.png)