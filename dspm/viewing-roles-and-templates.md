# Viewing the Roles and Templates
Source: https://help.zscaler.com/dspm/viewing-roles-and-templates
PDF: https://help.zscaler.com/pdf/com/en/1518586.pdf

DSPM creates IAM or custom roles in the cloud accounts and these roles are assigned with various permissions that allow DSPM to connect to the cloud account and discover resources for data scanning. You can view these roles on the Roles and Templates tab, copy them and verify if they are the same in the respective cloud account, in case of any [issues](/dspm/viewing-onboarding-issues).
To view the roles or download the templates:
- Go to **Administration** > **Configuration** > **Cloud Accounts**.
- Select the cloud account from the list.
-
Select the **Roles and Templates** tab.
You can view the templates and the corresponding roles created for the organization. The file name of the downloaded template includes the template version number.
- [AWS](#aws-templates)
- [Microsoft Azure](#azure-template)
- [GCP](#gcp-templates)
Availability of New Templates
DSPM releases new templates that include additional functionalities for scanning and collecting metadata. A notification banner is displayed on the **Roles and Templates** tab whenever a new template is available. [See image.](#new-template-notification) You can download the template to review the changes. If you click **Acknowledge**, the new template overrides the existing template, and DSPM validations and health checks are then performed on the new template upon deployment. If not acknowledged, DSPM validations and health checks continue on the existing template.
- You can acknowledge the template only if you are assigned an [administrator role](/dspm/predefined-roles-and-permissions). If you have a role with the View Cloud Accounts permission, you can only view or download the templates, but you cannot acknowledge them.
- If you acknowledge the new template for one organization or tenant, it is updated for all the onboarded organizations or tenants.
Redeploying Templates
You can redeploy the DSPM templates in the following scenarios:
- Upgrade to a new template
- Experience issues with custom roles that are created during onboarding
- Modify or delete a role
[]Download either the CloudFormation or Terraform template to your local system, extract the ZIP file, and run it on the AWS organization.
- Tree Discovery
- Orchestrator
- Monitoring Scope
- Evidence
- Data Events
You can view and copy the external ID, an optional identifier that is attached to the role. AWS recognizes this external ID and allows DSPM to access the AWS resources. To learn more, refer to the [AWS documentation](https://docs.aws.amazon.com/IAM/latest/UserGuide/id_roles_common-scenarios_third-party.html).
[See image.](#aws-roles)
[]Download the following templates to your local system, extract the ZIP file, and run it on the Azure tenant.
- Tree Discovery
- Azure Onboarding
- Evidence
[See image.](#viewtemplates)
[]Download the following templates to your local system, extract the ZIP file, and run it on the GCP organization.
- Tree Discovery
- GCP Onboarding
[See image.](#gcp-roles)
[]![Download the templates](/downloads/dspm/cloud-accounts-onboarding/cloud-account-management/viewing-roles-and-templates/dspm-azure-roles-templates.png)
[]![New template notification ](/downloads/dspm/administration/cloud-accounts-onboarding/microsoft-azure-cloud-accounts/downloading-role-and-templates-microsoft-azure/dspm-new-template-notification_0.png)
[]![View the AWS Roles and Templates](/downloads/dspm/cloud-accounts-onboarding/cloud-account-management/viewing-roles-and-templates/dspm-aws-roles-templates.png)
[]![View the GCP Roles and Templates](/downloads/dspm/administration/cloud-accounts-onboarding/about-cloud-accounts/dspm-gcp-roles-templates.png)