# Deploying File-Based Gen AI Decoys
Source: https://help.zscaler.com/deception/deploying-file-based-generative-ai-decoys
PDF: https://help.zscaler.com/pdf/com/en/1531594.pdf

[Watch a video about Deploying File-Based Gen AI Decoys](https://fast.wistia.net/embed/iframe/qf0fwfsxxm).
File-based generative AI (Gen AI) decoys mimic the resources used to set up local large language models (LLMs). You can lure attackers by deploying these decoy file resources to one of the following assets:
- Endpoints via [landmine policies](/deception/about-policies)
- Azure cloud via [storage account container decoy](/deception/creating-storage-account-container-decoy-azure) or [storage account file share decoy](/deception/creating-storage-account-file-share-decoy-azure)
- Amazon Web Services (AWS) cloud via [S3 decoys](/deception/creating-s3-decoy-aws)
- [Network decoys](/deception/about-network-decoys) via [FTP](/deception/configuring-services-network-decoy#configuring-ftp-service) or [Share](/deception/configuring-services-network-decoy#configuring-shares-service) service
In addition, you can configure [session lures](/deception/configuring-session-lures-module) via [landmine polices](/deception/about-policies) to point to any file-based Gen AI decoys.
The following new file datasets were added to create file-based Gen AI decoys:
| File Dataset | Description |
| ------------ | ----------- |
| Falcon-7b | An LLM developed by the Technology Innovation Institute (TII) for use in summarization, text generation, and chatbots. |
| GPT-2 Large | An LLM developed by OpenAI optimized for generating high-quality, context-aware text across diverse applications. |
To learn more, see [About File Datasets](/deception/about-file-datasets).
- [Deploying Gen AI Decoys on Endpoints via Landmine Policies](#deploy-gen-ai-files-on-endpoints)
- [Deploying Gen AI Decoys on Public Cloud Platforms](#deploy-gen-ai-files-on-public-clouds)
- [Deploying Gen AI Decoys as Internal FTP or Share Service via Network Decoys](#deploy-gen-ai-files-as-ftp)
[]You can deploy file-based Gen AI decoys to your organization's endpoints by configuring the File Decoys module in [landmine policies](/deception/about-policies). Zscaler Deception provides preconfigured file datasets that mimic resources required to set up local LLMs. By configuring the File Decoys module in landmine polices, these file-based Gen AI decoys are deployed onto the endpoints. Any interactions with these decoys are logged as an event on the [Investigate dashboard](/deception/understanding-zscaler-deception-dashboard).
To deploy a file-based Gen AI decoy on endpoints via a landmine policy:
- [Add a new landmine policy](/deception/creating-landmine-policy#adding-policy).
-
[Specify a selection criterion for the policy](/deception/creating-landmine-policy#specifying-criteria).
If you want like to use an existing landmine policy, skip the previous steps.
- Go to **Deceive **> **Landmine **> **Policies**.
-
Locate the policy, and click the **Edit **icon under the **Actions **column.
[See image.](#edit-landmine-policy)
The policy configuration window appears.
-
In the policy configuration window:
- Go to** File Decoys** and locate the **Pre-configured File Datasets** section.
- Click **Add**.
- For **Dataset**, select a Gen AI file dataset from the Gen AI Decoys group.
- For **Path**, enter the path where you want the file-based Gen AI decoy to be placed.
- (Optional) For **Comment**, enter a comment.
- Select **Hidden **if you want the file to be hidden.
[See image.](#file-decoys-gen-ai)
-
Click **Save**.
You can deploy a maximum of two preconfigured file dataset decoys on each endpoint. If more than two preconfigured file dataset decoys are configured, any two files are selected at random.
[]
- [File-Based Gen AI Decoys on Microsoft Azure](#gen-ai-files-azure)
- [File-Based Gen AI Decoys on AWS](#gen-ai-files-aws)
[]
- [File-Based Gen AI Decoys as an FTP Service on Internal Network](#deploying-gen-ai-files-as-internal-FTP-service)
- [File-Based Gen AI Decoys as a Share Service on Internal Network](#deploying-gen-ai-as-share-internal)
- [File-Based Gen AI Decoys as an FTP Service on Zero Trust Network](#deploying-gen-ai-files-as-zero-trust-ftp-service)
- [File-Based Gen AI Decoys as a Share Service on Zero Trust Network](#deploying-gen-ai-files-as-share-zero-trust)
[]You can deploy file-based Gen AI decoys on your internal network by configuring FTP service for a network decoy. Zscaler Deception provides preconfigured file datasets that mimic resources required to set up local LLMs. By configuring the FTP service for a network decoy, these file-based Gen AI decoys are deployed on your organization's network. Any interactions with these decoys are logged as an event on the [Investigate dashboard](/deception/understanding-zscaler-deception-dashboard).
To deploy a file-based Gen AI decoy via an internal network decoy:
- [Create an internal network decoy](/deception/creating-internal-network-decoy).
-
[Configure the FTP service](/deception/configuring-services-network-decoy#configuring-ftp-service) for the network decoy and select a Gen AI file dataset from the **Pre-configured Application / Service** drop-down menu.
[See image.](#internal-ftp-service)
The file-based Gen AI decoy is deployed on your internal network as an FTP service.
[]You can deploy file-based Gen AI decoys on your internal network by configuring Share service for a network decoy. Zscaler Deception provides preconfigured file datasets that mimic resources required to set up local LLMs. By configuring the Share service for a network decoy, these file-based Gen AI decoys are deployed on your organization's network. Any interactions with these decoys are logged as an event on the [Investigate dashboard](/deception/understanding-zscaler-deception-dashboard).
To deploy a file-based Gen AI decoy via an internal network decoy:
- [Create an internal network decoy](/deception/creating-internal-network-decoy).
-
[Configure the Share service](/deception/configuring-services-network-decoy#configuring-shares-service) for the network decoy and select a Gen AI file dataset from the **File Dataset** drop-down menu.
[See image.](#internal-share-service)
The file-based Gen AI decoy is deployed on your internal network as a Share service.
[]You can deploy file-based Gen AI decoys on your Zero Trust network by configuring FTP service for a network decoy. Zscaler Deception provides preconfigured file datasets that mimic resources required to set up local LLMs. By configuring the FTP service for a network decoy, these file-based Gen AI decoys are deployed on your organization's network. Any interactions with these decoys are logged as an event on the [Investigate dashboard](/deception/understanding-zscaler-deception-dashboard).
To deploy a file-based Gen AI decoy via an internal network decoy:
- [Create a Zero Trust Network decoy](/deception/creating-zero-trust-network-decoy).
-
[Configure the FTP service](/deception/configuring-services-network-decoy#configuring-ftp-service) for the network decoy and select a Gen AI file dataset from the **Pre-configured Application / Service** drop-down menu.
[See image.](#zero-trust-ftp-service)
The file-based Gen AI decoy is deployed on your internal network as an FTP service.
[]You can deploy file-based Gen AI decoys on your Zero Trust network by configuring Share service for a network decoy. Zscaler Deception provides preconfigured file datasets that mimic resources required to set up local LLMs. By configuring the Share service for a network decoy, these file-based Gen AI decoys are deployed on your organization's network. Any interactions with these decoys are logged as an event on the [Investigate dashboard](/deception/understanding-zscaler-deception-dashboard).
To deploy a file-based Gen AI decoy via an internal network decoy:
- [Create a Zero Trust Network decoy](/deception/creating-zero-trust-network-decoy).
-
[Configure the Share service](/deception/configuring-services-network-decoy#configuring-shares-service) for the network decoy and select a Gen AI file dataset from the **File Dataset** drop-down menu.
[See image.](#zero-trust-share-service)
The file-based Gen AI decoy is deployed on your internal network as a Share service.
[]You can deploy file-based Gen AI decoys to your Azure cloud storages, such as storage account containers and storage account file shares. Zscaler Deception provides preconfigured file datasets that mimic resources required to set up local LLMs. You can deploy the decoy Gen AI file data sets to Azure's storage account containers and storage account file shares. Any interactions with these decoys are logged as an event on the [Investigate dashboard](/deception/understanding-zscaler-deception-dashboard).
Before deploying a file-based Gen AI decoy in the Azure cloud, ensure that you have [set up cloud deception with Microsoft Azure](/deception/setting-cloud-deception-microsoft-azure).
To deploy a file-based Gen AI decoy to the Azure cloud:
- Go to **Deceive **> **Cloud Deception **> **Azure**.
-
Create a [Storage Account Container decoy](/deception/creating-storage-account-container-decoy-azure) or [Storage Account File Share decoy](/deception/creating-storage-account-file-share-decoy-azure) by choosing a preconfigured Gen AI file dataset from the **File Dataset** drop-down menu.
[See image.](#azure-gen-ai-files)
The selected file-based Gen AI decoy is deployed in the Azure cloud.
The file-based Gen AI decoys are enumerated directly by adversaries, or you can point to Gen AI decoys via [landmine polices](/deception/about-policies) via [cloud lures](/deception/configuring-cloud-lures-module) or [session lures](/deception/configuring-session-lures-module).
[]You can deploy file-based Gen AI decoys to your AWS cloud storage via S3 decoy. Zscaler Deception provides preconfigured file datasets that mimic resources required to set up local LLMs. You can deploy the decoy Gen AI file data sets to S3. Any interactions with these decoys are logged as an event on the [Investigate dashboard](/deception/understanding-zscaler-deception-dashboard).
Before deploying a file-based Gen AI decoy in the AWS cloud, ensure that you have [set up cloud deception with AWS](/deception/setting-cloud-deception-aws).
To deploy a file-based Gen AI decoy to the AWS cloud:
- Go to **Deceive **> **Cloud Deception **> **AWS**.
-
Create an [S3 decoy](/deception/creating-s3-decoy-aws) by choosing a preconfigured Gen AI file dataset from the **File Dataset** drop-down menu.
[See image.](#s3-gen-ai-aws)
The selected file-based Gen AI decoy is deployed in the AWS cloud.
The file-based Gen AI decoys are enumerated directly by adversaries, or you can point to Gen AI decoys via [landmine polices](/deception/about-policies) via [session lures](/deception/configuring-session-lures-module).
[]
![A screenshot highlighting the Edit option for a landmine policy](/downloads/deception/deceive/gen-ai-decoys/creating-and-deploying-file-based-gen-ai-decoys/zscaler-deception-landmine-policy-page-edit-option.jpg)
[]
![A screenshot of Pre-Configured Secrion in File Decoys Module](/downloads/deception/deceive/gen-ai-decoys/creating-and-deploying-file-based-gen-ai-decoys/zscaler-deception-file-decoys-file-datasets.png)
[]
![A screenshot highlighting various options to add file datsets](/downloads/deception/deceive/gen-ai-decoys/creating-and-deploying-file-based-gen-ai-decoys/zscaler-deception-azure-file-gen-ai-decoys.png)
[]
![A screenshot highlighting File Datsets in S3 Decoys](/downloads/deception/deceive/gen-ai-decoys/creating-and-deploying-file-based-gen-ai-decoys/zscaler-deception-s3-decoys_0.png)
[]
![A screenshot highlighting the option to configure File Datsets via FTP service](/downloads/deception/deceive/gen-ai-decoys/creating-and-deploying-file-based-gen-ai-decoys/zscaler-deception-ftp-service-internal.png)
[]
![A screenshot highlighting the File Datasets as Shares service](/downloads/deception/deceive/gen-ai-decoys/creating-and-deploying-file-based-gen-ai-decoys/zscaler-deception-share-service-intenral.png)
[]
![A screenshot highlighting the File Datasets option in FTP service](/downloads/deception/deceive/gen-ai-decoys/creating-and-deploying-file-based-gen-ai-decoys/zscaler-deception-ftp-service-zero-trust.png)
[]
![A screenshot highlighting File Datsets in Shares service](/downloads/deception/deceive/gen-ai-decoys/creating-and-deploying-file-based-gen-ai-decoys/zscaler-deception-share-zero-trust.png)