# Creating and Managing Tags for AWS Resources
Source: https://help.zscaler.com/deception/creating-and-managing-tags-aws
PDF: https://help.zscaler.com/pdf/com/en/1531568.pdf

Tags are key-value pairs that allow you to organize resources in Amazon Web Services (AWS). You can configure and manage AWS tags directly from the Zscaler Deception Admin Portal for resources that are [deployed by Zscaler Deception](/deception/about-cloud-deception-with-aws). You can create the following types of tags from the Deception Admin Portal:
- Decoy Tags: Decoy tags are added to decoy resources, such as IAM decoys, S3 decoys, RDS decoys, etc., and the IAM Decoy User Access Policy.
- Management Tags: Management tags are added to all other resources.
Zscaler recommends configuring AWS tags in the Deception Admin Portal before [setting up the integration with AWS](/deception/setting-cloud-deception-aws#zd-integration-aws-decoys) as these tags are added to resources only when creating them in the AWS cloud.
Creating a Tag
To create a tag:
- Go to **Deceive **> **Cloud Deception **> **AWS** > **Settings**.
- Locate the AWS account for which you want to configure tags, and click the **Edit **icon.
-
In the **AWS Account Setting** window, click **Tags**.
[See image.](#zd-aws-add-tags-create)
The **Add Tags** window appears.
-
In the **Add Tags **window:
- To add a decoy tag:
- Under the **Decoy Tags** section, click **Add Tag**.
- Enter the key and value pair for the tag.
- To add a management tag:
- Under the **Management Tags** section, click **Add Tag**.
- Enter the key and value pair for the tag.
[See image.](#zd-add-tags)
- Click **Save**.
Do not use words or phrases such as `decoy`, `deception`, and `active defense`, etc. for the key and value pairs, as they can provide a hint to adversaries about the nature of decoy resources.
The tags are applied while creating and deploying new resources via the [deployment script](/deception/obtaining-deployment-script-aws). The new tags are not applied to existing decoys. If you want to apply new tags to all decoys, then you must [delete all decoys](/deception/managing-aws-decoys#zd-delete-aws-decoys), and deploy them again. However, tags are added to the IAM Decoy User Access Policy when any subsequent operation is performed via [deployment script](/deception/obtaining-deployment-script-aws).
Editing a Tag
To edit a tag:
- Go to **Deceive **> **Cloud Deception **> **AWS** > **Settings**.
- Locate the AWS account for which you want to configure tags, and click the **Edit **icon.
-
In the **AWS Account Setting** window, click **Tags**.
[See image.](#zd-aws-add-tags-edit)
The **Add Tags** window appears.
-
In the **Add Tags **window:
- To edit a decoy tag, under the **Decoy Tags** section, modify the key and value pair for the tag that you want to edit.
- To edit a management tag, under the **Management Tags** section, modify the key and value pair for the tag that you want to edit.
[See image.](#zd-edit-tags)
- Click **Save**.
- The modified decoy tags are not applied to existing decoy resources. The edited tags are applied only to the new decoy resources that are created after editing the tag. The existing decoy resources retain the old tags. If you want to apply modified tags to all decoys, then you must [delete all decoys](/deception/managing-aws-decoys#zd-delete-aws-decoys), and deploy them again. However, modified tags are added to the IAM Decoy User Access Policy during any subsequent operation performed via [deployment script](/deception/obtaining-deployment-script-aws).
- The modified management tags are applied to existing management resources created in AWS by Zscaler Deception during the integration when any operation is performed via [deployment script](/deception/obtaining-deployment-script-aws) subsequently.
Deleting a Tag
To delete a tag:
- Go to **Deceive **> **Cloud Deception **> **AWS** > **Settings**.
- Locate the AWS account for which you want to configure tags, and click the **Edit **icon.
-
In the **AWS Account Setting** window, click **Tags**.
[See image.](#zd-aws-add-tags-delete)
The **Add Tags** window appears.
-
In the **Add Tags **window:
- To delete a decoy tag, under the **Decoy Tags** section, click the **Delete** icon for the tag.
- To delete a management tag, under the **Management Tags** section, click the **Delete** icon for the tag.
[See image.](#zd-delete-tag)
- Click **Save**.
Deleting tags prevents further usage of the tags. The existing resources are not affected as the tags are not removed from them.
[]![A screenshot capturing the Add Tags window](/downloads/deception/deceive/cloud-deception/aws/creating-and-managing-tags-aws/deception-aws-setting-tags.png)
[]![A screenshot capturing the Add Tags window](/downloads/deception/deceive/cloud-deception/aws/creating-and-managing-tags-aws/deception-aws-setting-tags.png)
[]![A screenshot capturing the Add Tags window](/downloads/deception/deceive/cloud-deception/aws/creating-and-managing-tags-aws/deception-aws-setting-tags.png)
[]![A screenshot capturing the new tags configuration](/downloads/deception/deceive/cloud-deception/aws/configuring-and-managing-tags-aws/zscaler-deception-creating-tags.png)
[]![A GIF capturing how to edit a tag](/downloads/deception/deceive/cloud-deception/aws/creating-and-managing-tags-aws/deception-aws-edit-tags-gif.gif)
[]![A GIF capturing how to delete a tag](/downloads/deception/deceive/cloud-deception/aws/creating-and-managing-tags-aws/deception-aws-delete-tags-gif.gif)