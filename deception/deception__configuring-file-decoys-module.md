# Configuring the File Decoys Module
Source: https://help.zscaler.com/deception/configuring-file-decoys-module
PDF: https://help.zscaler.com/pdf/com/en/1531307.pdf

The File Decoys module enables you to place decoy files on endpoints. The Zscaler Deception Admin Portal generates alerts when an adversary attempts to interact with these file decoys.
The File Decoys module is available only on Landmine Agents for Windows and Landmine Agentless for Linux endpoints. To learn more, see [Supported Deception Features for Landmine Agent and Agentless Installers](/deception/supported-deception-features-landmine-agent-and-agentless).
To configure file decoys for a landmine policy:
- Go to **Deceive **> **Landmine **> **Policies**.
-
In the landmine policies table, locate the landmine policy you want to use to deploy file decoys on endpoints, and click the **Edit **icon.
[See image.](#option-to-edit-policy)
- In the policy configuration window, click **File Decoys**, and configure the required decoys:
- [Custom File Decoys](#custom-file-decoys)
- [Credential File Decoys](#credential-file-decoys)
- [Preconfigured File Dataset Decoys](#pre-configured-file-dataset-decoys)
[]Custom file decoys are decoy files that are placed on a specific path with a specific name. These decoy files are activated when an adversary interacts with them. A custom file decoy can be a Microsoft Office or HTML file.
Custom file decoys are supported only for Windows endpoints via both Landmine Agent and Landmine Agentless.
To configure a custom file decoy:
-
Under the **Custom Files **section:
- Click **Add**.
- **Name**: Enter a name for the custom file decoy.
- **Path**: Enter the** **path to the custom file decoy.
- **File Type**: Select a file type from the drop-down menu. For example, select **PPT**,** XLSX**, **DOCX**, or **HTML**.
- **Comment**: (Optional) Enter a comment.
- **Hidden**: (Optional) Enable if you want to hide the file.
[See image.](#zd-fd-custom-files)
- Click **Save**.
You can deploy a maximum of two custom file decoys on each endpoint. If more than two custom file decoys are configured, any two are selected at random.
[]Credential file decoys are CSV files that contain credentials that point to your network decoys. These decoy files impersonate a careless user tracking credentials in plain text files instead of a password manager. Decoys that are included in the file are selected at random, and passwords are generated using the rules specified in the [Password Settings](/deception/configuring-password-settings) module.
Credential file decoys are supported for Windows endpoints (via Landmine Agents) and Linux endpoints (via Landmine Agentless).
To configure a credential file decoy:
-
Under the **Credential **section:
- Click **Add**.
- **Name**: Enter a name for the credential file decoy.
- **Path**: Enter the path to the credential file decoy.
- **Comment**: (Optional) Enter a comment.
-
**Hidden**: (Optional) Select if you want to hide the file. This option applies only to policies for Windows endpoints applied through Landmine Agents.
For policies applied to Linux endpoints through Landmine Agentless, you can hide the file by prefixing the file name with a dot (.).
[See image.](#linux-hide-file)
-
**Target Decoys**: Select one or more decoys from the drop-down menu as targets to generate credentials. Credentials to access the decoys are generated and placed in the credential file. When no decoy is selected, a target decoy is chosen randomly if a decoy with a supported service is enabled and deployed.
You can select interactive generative AI decoys as target decoys. If the target decoy is an authentication-enabled generative AI decoy, then adversaries can use the fake credentials stored in the credential file decoy to log in to the generative AI decoys. To learn more about authentication-enabled generative AI decoys, see [Configuring Services on a Network Decoy](/deception/configuring-services-network-decoy/#deception-config-service-gen-ai-hi-interaction-app-section).
[See image.](#zd-fd-credential)
- Click **Save**.
You can deploy a maximum of two credential file decoys on each endpoint. If more than two credential file decoys are configured, any two are selected at random.
[]Preconfigured file datasets enable you to create a directory of decoy files for each endpoint using the file datasets defined in Miragemaker. You can either generate file datasets dynamically or upload a static set of files.
File decoys using preconfigured file datasets are supported only for Windows endpoints (via Landmine Agents).
To configure a preconfigured file dataset decoy:
-
Under the **Preconfigured File Datasets** section:
- Click **Add**.
-
**Dataset**: Select a Miragemaker file dataset.
You can select generative AI file datasets to deploy [file-based generative AI decoys](/deception/creating-and-deploying-file-based-gen-ai-decoys) on endpoints.
- **Name**: Enter a name of your choice that must be used for the file decoy.
- **Path**: Enter the path to the file decoy.
- (Optional) **Comment**: Enter a comment.
- Select **Hidden** if you want the file to be hidden.
[See image.](#zd-fd-pre-config)
- Click **Save**.
You can deploy a maximum of two preconfigured file dataset decoys on each endpoint. If more than two preconfigured file dataset decoys are configured, any two files are selected at random.
[][![The option to edit a landmine policy](/downloads/deception/deceive/landmine-decoys/policies/configuring-file-decoys-module/deception-landmine-policy-edit-one.png)
]
[]![Configuring custom file decoys](/downloads/deception/deceive/landmine-decoys/policies/configuring-file-decoys-module/zscaler-deception-file-decoys-files-custom.jpg)
[]![Configuring preconfigured file datasets for file decoys](/downloads/deception/deceive/landmine-decoys/policies/configuring-file-decoys-module/deception-preconfigured-file-dataset.png)
[]![Configuring credential file decoys](/downloads/deception/deceive/landmine-decoys/policies/configuring-file-decoys-module/zscaler-deception-file-decoys-credential.png)
[]![Hiding a file decoy in Linux endpoints](/downloads/deception/deceive/landmine-decoys/policies/configuring-file-decoys-module/zscaler-deception-landmine-agentless-hide-file-linux.jpg)