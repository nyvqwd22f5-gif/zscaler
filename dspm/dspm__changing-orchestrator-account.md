# Changing an Orchestrator Account
Source: https://help.zscaler.com/dspm/changing-orchestrator-account
PDF: https://help.zscaler.com/pdf/com/en/1478011.pdf

DSPM regularly scans the data stores of the target accounts by leveraging the [orchestrator template](/dspm/understanding-orchestrator) deployed in the AWS orchestrator account while onboarding.
After [onboarding an organization](/dspm/onboarding-aws-organization), you can change the orchestrator account if the existing orchestrator account is being decommissioned, deleted, or if an incorrect account was selected while onboarding. When you change the orchestrator account, you must run the orchestrator template in the new account. DSPM validates the template deployment and updates the [orchestrator status](/dspm/viewing-orchestrator-status) accordingly.
Until the new orchestrator account is successfully validated, the following changes occur:
- The existing orchestrator is disabled.
- The DSPM connection status moves to the Waiting for Connection state and Configuration status moves to the Pending state.
- The data scans are stopped.
- The target accounts move to the Needs Attention state.
Prerequisites
You must be assigned either an [administrator](/dspm/predefined-roles-and-permissions) role or a custom role with the Configure New Orchestrator permission.
Changing an Orchestrator Account
To change the orchestrator account:
- Go to **Administration **> **Configuration** > **Cloud Accounts**.
- Select the organization for which you want to change the orchestrator account.
-
Click **Manage** and then select **Configure New Orchestrator**.
[See image.](#select-configure-new-orch)
-
In the **New Orchestrator** window, read the caution and then select the **I understand** checkbox.
[See image.](#new-orch-window)
- Click **Continue**.
-
In the **Configure an Orchestrator Account** page, select the account and primary region where you want to deploy the orchestrator template and then click **Next**.
[See image.](#configure-orch-acocunt-page)
The existing orchestrator account checkbox is disabled. [See image.](#disabled-checkbox)
-
In the **Provide Permissions** page, download and run the templates.
Before running the template on the new orchestrator account, purge the template that was previously deployed on the existing orchestrator account. You can do this by deleting the corresponding stackset or running the `terraform destroy` command based on the template type.
- [Run the orchestrator template.](/dspm/onboarding-aws-organization#runorchtemplate)
- [Run the monitoring template.](/dspm/onboarding-aws-organization#runmonitoringscopetemplate)
[See image.](#provide-permissions)
- Click **Done**.
DSPM validates the template deployment every hour by checking the roles created and permissions granted.
If there is any issue while deploying the template, an error is displayed. Rerun the templates in the orchestrator account and target accounts.
After the template deployment is validated successfully, the target accounts move to the Successfully Configured state, and DSPM begins the [data scan](/dspm/about-scan-settings). The orchestrator status (DSPM Connection and Configuration Status) moves to the Successful state. [See image.](#orchestrator-status) You can view the orchestrator details on the [Overview](/dspm/viewing-organization-onboarding-status) tab.
[]![Configure a New Orchestrator](/downloads/dspm/administration/cloud-accounts-onboarding/aws-cloud-accounts/aws-organization/changing-orchestrator-account/dspm-configure-new-orchestrator.png)
[]![Configure a New Orchestrator window](/downloads/dspm/administration/cloud-accounts-onboarding/aws-cloud-accounts/aws-organization/changing-orchestrator-account/dspm-new-orchestrator-window.png)
[]![Configure a New Orchestrator page](/downloads/dspm/administration/cloud-accounts-onboarding/aws-cloud-accounts/aws-organization/managing-orchestrator-aws/dspm-configure-new-orchestrator-page.png)
[]![Download and run the templates](/downloads/dspm/administration/cloud-accounts-onboarding/aws-cloud-accounts/aws-organization/changing-orchestrator-account/dspm-aws-orchestrator-provide-permissions.png)
[]![Disabled existing orchestrator checkbox](/downloads/dspm/administration/cloud-accounts-onboarding/aws-cloud-accounts/aws-organization/managing-orchestrator-aws/dspm-existing-orch.png)
[]![View the orchestrator status](/downloads/dspm/administration/cloud-accounts-onboarding/aws-cloud-accounts/aws-organization/changing-orchestrator-account-aws/dspm-orchestrator-target-account-status.png)