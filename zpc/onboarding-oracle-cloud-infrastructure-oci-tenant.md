# Onboarding an Oracle Cloud Infrastructure (OCI) Tenant
Source: https://help.zscaler.com/zpc/onboarding-oracle-cloud-infrastructure-oci-tenant
PDF: https://help.zscaler.com/pdf/com/en/1452956.pdf

Zscaler Posture Control (ZPC) supports onboarding Oracle Cloud Infrastructure (OCI) tenants. When onboarded, ZPC provides insight into your cloud account's security posture. ZPC provides a Terraform template that you can run on your OCI environment to onboard your OCI tenants.
ZPC requests for certain OCI tenancy information and creates a Terraform template that you can run on your OCI environment to onboard your OCI tenants. The Terraform template performs the following tasks:
- Creates a new user and group.
- Creates a new policy with the "Allow group attached to read all resources in tenancy" statement.
- Assigns the created user to the created group.
- Adds a public key as an API key for the created user.
- Returns the user OCID.
To onboard an OCI tenant to ZPC:
- On the Zscaler Posture Control Admin Portal, go to **Administration** > **Cloud Accounts**.
- Click **Add Account**.
- Under **Select Cloud Type**, click the **OCI** tile.
- Click **Next**.
[See image.](#select-oci-tile-img)
- On the **Configuration Details** page, enter the following OCI tenancy information that ZPC uses to create the Terraform template:
- **ZPC Alias** (optional): The tenant's name on ZPC. ZPC uses the OCI tenant name if you leave this field blank.
- **Tenancy OCID**: Unique identifier for the OCI tenant. Enter the root compartment ID.
- **Home Region**: Home region of the OCI tenant.
- [Finding Tenancy OCID and Home Region on the OCI console.](#tenancy-ocid-home-region-on-oci-console)
- **User Name**: User name ZPC needs to use to authenticate with the OCI tenant.
- **Group Name**: Group name where the user is residing on the OCI tenant.
- **Policy Name**: Policy ZPC needs to use for read permissions to OCI configuration metadata.
[See image.](#configuration-details-oci-img)
- You can enter a previously created user name and group name. However, the user must not be assigned to the group.
- You cannot use an already existing policy and must provide a new policy name.
- On the **Business Units** page, you can select your business unit from the drop-down menu.
- Click **Next**.
- On the **Download Template** page:
- Click the **Download Template** button.
- [Running the Terraform template on the OCI console.](#running-template-oci)
- Enter the **User OCID** generated on your OCI deployment.
- Click **Next**.
[See image.](#oci-download-template-img)
- On the **Summary** page, click **Finish**.
After you onboard a cloud account, you can verify whether the cloud account is onboarded successfully and configuration metadata is being collected.
[]
- Log in to the root compartment or tenancy using the default identity domain on the [Oracle Cloud Console](https://www.oracle.com/cloud/sign-in.html).
- Go to Compartments (**Navigation Menu** icon > **Identity and Security** > **Compartments**).
- Select the root compartment or tenancy. Copy the Tenancy OCID and the Home Region.
[See image.](#view-root-comp-region)
[]
![View root compartment and home region on OCI console.](/downloads/zpc/administration/cloud-accounts/onboarding-oracle-cloud-infrastructure-oci-tenant/root-comp-home-region.png)
[]
- Log in to the root compartment or tenancy using the default identity domain on the [Oracle Cloud Console](https://www.oracle.com/cloud/sign-in.html).
- Go to Stacks (**Navigation Menu** icon > **Developer Services** > **Resource Manager** > **Stacks**).
- Ensure the root compartment is selected, then click **Create Stack**
[See image.](#create-stack-image)
- Select the **My Configuration** radio button.
- Under the **Terraform configuration source**, select the **.Zip file** radio button.
- Click **Next**.
[See image.](#zip-config)
- On the **Configure variables** page, click **Next**.
- On the **Review** page, select the **Run apply** checkbox.
- Click **Create**.
- After the stack is created, click **Outputs**.
- Copy the **oci_identity_user** value.
[See image.](#copy-oci-identity-user)
[]
![View the stack page on OCI console.](/downloads/zpc/administration/cloud-accounts/onboarding-oracle-cloud-infrastructure-oci-tenant/zpc-oci-create-new-stack.png)
[]
![View terraform template options on OCI console.](/downloads/zpc/administration/cloud-accounts/onboarding-oracle-cloud-infrastructure-oci-tenant/zpc-oci-zip-config.png)
[]
![View user OCID on OCI console.](/downloads/zpc/administration/cloud-accounts/onboarding-oracle-cloud-infrastructure-oci-tenant/zpc-oci-copy-user-ocid.png)
[]
![View cloud type selection page on ZPC.](/downloads/zpc/administration/cloud-accounts/onboarding-oracle-cloud-infrastructure-oci-tenant/zpc-select-oci-onboarding-tile.png)
[]
![View OCI configuration details on ZPC.](/downloads/zpc/administration/cloud-accounts/onboarding-oracle-cloud-infrastructure-oci-tenant/zpc-configuration-details.png)
[]
![View the download template page for OCI on ZPC.](/downloads/zpc/administration/cloud-accounts/onboarding-oracle-cloud-infrastructure-oci-tenant/zpc-oci-download-template.png)