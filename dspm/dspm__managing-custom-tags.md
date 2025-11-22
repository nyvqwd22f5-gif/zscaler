# Managing Custom Tags
Source: https://help.zscaler.com/dspm/managing-custom-tags
PDF: https://help.zscaler.com/pdf/com/en/1504756.pdf

Custom tags are key-value pairs that allow you to organize, identify, and distinguish the resources created and deployed by DSPM in your cloud environment. Custom tags are created and applied to the DSPM resources while deploying the templates.
You can add, edit, or delete the custom tags, as required.
You must be assigned either an [Administrator role](/dspm/predefined-roles-and-permissions) or a custom role with the Configure Monitoring Scope permission in the DSPM Admin Portal.
Custom tags must match the syntax used by CSPs to prevent errors while reading the tags. Follow these guidelines while adding custom tags:
- [AWS](#awstags)
- [Azure](#azuretags)
- [GCP](#gcptags)
- []Keys and values are case sensitive.
- Custom tags can include lowercase letters, uppercase letters, numbers, or special characters (`+ = @ _ / -`).
- Custom tags shouldn't start with `aws`.
- Keys and values must have a minimum of 1 character and not exceed 63 characters.
- []Keys are case sensitive.
- Keys can include lowercase letters, uppercase letters, numbers, spaces, or special characters (`! @ # ^ * () _ {} : ; ' | . , [] ` ~ + = @ _ -`).
- Keys must have a minimum of 1 character and not exceed 128 characters.
- Values cannot exceed 256 characters.
- []Keys and values must include only lowercase letters, numbers, or special characters (`_ or -)`.
- Custom tags must have a minimum of 1 character and not exceed 128 characters.
Do not use the following predefined tags that are automatically assigned to the DSPM resources:
- z-dspm-tenant-id
- z-dspm-tenant-name
- z-dspm-resource
- z-lp-resource-type
- z-dspm-integration-id
- z-dspm-scanner-resource
- z-dspm-scan-id
- azure
- microsoft
- windows
Adding Custom Tags
To add custom tags:
- Go to **Administration** > **Configuration** >** Cloud Accounts**.
- Select the cloud account.
-
Click **Manage**, and then select **Manage Custom Tags** from the drop-down menu.
[See image.](#managecustomtags)
-
On the **Manage Custom Tags** page, enter the key and value for the tag.
[See image.](#addcustomtags)
- Click **Add More**, and enter key-value pairs to add more tags.
- Click **Next**.
- On the **Apply Changes** page, download and deploy the template.
-
Click **Done**.
[See image.](#applychanges)
You can see the number of custom tags added on the [Overview ](/dspm/viewing-onboarding-status)page.
Editing Custom Tags
When you modify a custom tag and deploy the templates, the new custom tag overrides the existing custom tag, and the resources are updated with the modified tags.
To edit custom tags:
- Go to **Administration** > **Configuration** >** Cloud Accounts**.
- Select the cloud account.
-
Click **Manage**, and then select **Manage Custom Tags** from the drop-down menu.
[See image.](#managecustom)
-
On the **Manage Custom Tags** page, modify the key and value for the required tag.
[See image.](#modifycustomtags)
- Click **Next**.
- On the **Apply Changes** page, download and deploy the templates.
- Click **Done**.
Deleting Custom Tags
When you delete custom tags, the tags are removed from the resources after you deploy the templates.
To delete custom tags:
- Go to **Administration** > **Configuration** >** Cloud Accounts**.
- Select the cloud account.
- Click **Manage**, and then select **Manage Custom Tags** from the drop-down menu.
-
On the **Manage Custom Tags** page, click the **Delete** icon for the custom tag that you want to delete.
[See image.](#deletecustomtags)
- Click **Next**.
- On the **Apply Changes** page, download and deploy the templates.
- Click **Done**.
[]![Manage Custom Tags](/downloads/dspm/administration/cloud-account-management/managing-custom-tags/dspm-manage-customtags_0.png)
[]![Manage Custom Tags page](/downloads/dspm/administration/cloud-account-management/managing-custom-tags/dspm-manage-custom-tags-page_0.png)
[]![Modify custom tags](/downloads/dspm/administration/cloud-account-management/managing-custom-tags/dspm-edit-custom-tags.gif)
[]![Manage Custom Tags](/downloads/dspm/administration/cloud-account-management/managing-custom-tags/dspm-manage-customtags_0.png)
[]![Delete custom tags](/downloads/dspm/administration/cloud-account-management/managing-custom-tags/dspm-manage-custom-tags-page-deleteicon.png)
[]![The Apply Changes page with the template that must be deployed.](/downloads/dspm/administration/cloud-account-management/managing-custom-tags/dspm-download-deploy-template.png)