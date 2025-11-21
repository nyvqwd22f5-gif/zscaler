# About Cloud Accounts
Source: https://help.zscaler.com/zpc/about-cloud-accounts
PDF: https://help.zscaler.com/pdf/com/en/1395546.pdf

Zscaler Posture Control (ZPC) considers all Amazon Web Service (AWS) Accounts, Microsoft Azure Subscriptions, and Google Cloud Platform (GCP) projects as cloud accounts. AWS Organizations, Microsoft Azure Tenants, and GCP Organizations are considered organizations on ZPC. Multiple cloud accounts can be assigned to a business unit. To learn more about business units, see [About Business Units](/zpc/about-business-units).
The cloud accounts page provides the following benefits and enable you to:
- View all onboarded cloud accounts across all cloud types.
- Manage vulnerability scanning, Kubernetes clusters, and business units for all onboarded cloud accounts.
About the Cloud Accounts Page
On the Cloud Accounts page (Administration > Cloud Accounts) you can view the following tabs:
- [Accounts](#viewing-cloud-accounts)
- [Organizations](#viewing-cloud-organizations)
- [Kubernetes](#viewing-cloud-kubernetes-clusters)
![View the cloud accounts page on ZPC.](/downloads/zpc/administration/cloud-accounts/about-cloud-accounts/zpc-cloud-accounts-home.png?1673451357)
[]
The Accounts tab displays details about all the cloud accounts you have onboarded to ZPC.
On the Accounts tab, you can do the following:
- Filter cloud accounts using available parameters. To learn more, see [Using Filters](/zpc/using-filters).
- Export all cloud account information as an Excel file. The [downloaded Excel file](/zpc/downloading-reports) follows the "Cloudaccounts_(timestamp)" naming convention.
- [Select and apply saved filters](/zpc/using-filters).
- [Hide the filters](/zpc/using-filters).
- Onboard a new cloud account. To learn more, see [About Onboarding Cloud Accounts](/zpc/onboarding-cloud-accounts).
- Search for a cloud account.
- View the following cloud account details:
- **Account Name**: The account name.
- **Organization**: The organization name.
- **Business Unit**: The business unit associated with the cloud account.
- **Write Access**: Whether remediation is enabled or not for the cloud account.
- **Vulnerability Scan**: Whether the cloud account has vulnerability scanning configured or not.
- **Status**: The status of the cloud account.
- **Onboarded Date**: The timestamp for when the cloud account was onboarded.
- **Cloud**: The cloud service provider type.
- Sort the column data.
- [Modify the table and its columns](/zpc/using-tables).
- **Actions**: The following actions are available for cloud accounts based on the cloud service provider type:
- [Amazon Web Services](#aws-actions)
- [Microsoft Azure](#azure-actions)
- [Google Cloud Platform](#gcp-actions)
![View the accounts tab on ZPC.](/downloads/zpc/administration/cloud-accounts/viewing-accounts-tab/zpc-accounts-tab.png?1688633802)
[]
- **Change Business Units**: Modify the business unit.
- **Add Write Access**: Enable write access for the cloud service provider to allow remediation on the cloud account. To learn more, see [Enabling Write Access for the Cloud Account](/zpc/configuring-write-access-aws-cloud-account).
- **Manage CloudTrail**: Configure CloudTrail S3 buckets for ZPC to read audit trail information. To learn more, see [Configuring CloudTrail S3 Buckets for AWS Organization](/zpc/configuring-cloud-trail-s3-buckets-aws-organization).
- **Add CVE & Data Security**: Enable ZPC to scan the cloud account for vulnerability metadata.
- **Add Kubernetes Cluster**: Enable ZPC to scan the cloud account for Kubernetes cluster metadata. To learn more, see [Onboarding an Amazon Elastic Kubernetes Service Cluster](/zpc/onboarding-amazon-elastic-kubernetes-service-cluster).
- **Delete Account**: Offboard a cloud account. To learn more, see [Managing Cloud Accounts](/zpc/managing-cloud-accounts).
[]
- **Change Business Units**: Modify the business unit.
- **Add CVE & Data Security**: Enable ZPC to scan the cloud account for vulnerability metadata.
- **Add Kubernetes Cluster**: Enable ZPC to scan the cloud account for Kubernetes cluster metadata. To learn more, see [Onboarding an Azure Kubernetes Service Cluster](/zpc/onboarding-azure-kubernetes-service-cluster).
- **Delete Account**: Offboard a cloud account. To learn more, see [Managing Cloud Accounts](/zpc/managing-cloud-accounts).
[]
- **Change Business Units**: Modify the business unit.
- **Add CVE & Data Security**: Enable ZPC to scan the cloud account for vulnerability metadata.
- **Add Kubernetes Cluster**: Enable ZPC to scan the cloud account for Kubernetes cluster metadata. To learn more, see [Onboarding a Google Kubernetes Engine Cluster](/zpc/onboarding-google-kubernetes-engine-cluster).
- **Delete Account**: Offboard a cloud account. To learn more, see [Managing Cloud Accounts](/zpc/managing-cloud-accounts).
[]
The Organizations tab displays details about all the cloud account organizations you have onboarded on ZPC.
On the Organizations tab, you can do the following:
- Export all cloud organization information as an Excel file. The downloaded Excel file follows the "Organizations_(timestamp)" naming convention.
- Search for a cloud organization.
- View the following cloud organization details:
- **Organization Name**: The organization name.
- **Onboarded Accounts**: The onboarded and total number of cloud accounts in the organization.
- **Cloud**: The cloud service provider type.
- [Modify the table and its columns](/zpc/using-tables).
- **Actions**: The following actions are available for organizations based on the cloud service provider type:
- [Amazon Web Services](#aws-org-actions)
- [Microsoft Azure](#azure-org-actions)
- [Google Cloud Platform](#gcp-org-actions)
- [Oracle Cloud Infrastructre](#oci-org-actions)
![View the organizations tab on ZPC.](/downloads/zpc/administration/cloud-accounts/viewing-organizations-tab/zpc-organizations-tab.png)
[]
- **Manage Organizations**: Offboard a cloud account. To learn more, see [Offboarding a Cloud Account](/zpc/offboarding-cloud-account).
- **Add CloudTrail**: Configure CloudTrail S3 buckets for ZPC to read audit trail information. To learn more, see [Configuring CloudTrail S3 Buckets for AWS Organization](/zpc/configuring-cloud-trail-s3-buckets-aws-organization).
- **Add Vulnerability Scanning**: Enable ZPC to scan the cloud account for vulnerability metadata.
- **Add Kubernetes Cluster**: Enable ZPC to scan the cloud account for Kubernetes cluster metadata. To learn more, see [Onboarding an Amazon Elastic Kubernetes Service Cluster](/zpc/onboarding-amazon-elastic-kubernetes-service-cluster).
- **Delete Organization**: Delete the organization. To learn more, see [Offboarding a Cloud Account](/zpc/offboarding-cloud-account).
[]
- **Manage Organizations**: Offboard a cloud account. To learn more, see [Offboarding a Cloud Account](/zpc/offboarding-cloud-account).
- **Add Vulnerability Scanning**: Enable ZPC to scan the cloud account for vulnerability metadata.
- **Add Kubernetes Cluster**: Enable ZPC to scan the cloud account for Kubernetes cluster metadata. To learn more, see [Onboarding an Azure Kubernetes Service Cluster](/zpc/onboarding-azure-kubernetes-service-cluster).
- **Delete Organization**: Delete the organization. To learn more, see [Offboarding a Cloud Account](/zpc/offboarding-cloud-account).
[]
- **Manage Organizations**: Offboard a cloud account. To learn more, see [Offboarding a Cloud Account](/zpc/offboarding-cloud-account).
- **Add Vulnerability Scanning**: Enable ZPC to scan the cloud account for vulnerability metadata.
- **Add Kubernetes Cluster**: Enable ZPC to scan the cloud account for Kubernetes cluster metadata. To learn more, see [Onboarding a Google Kubernetes Engine Cluster](/zpc/onboarding-google-kubernetes-engine-cluster).
- **Delete Organization**: Delete the organization. To learn more, see [Offboarding a Cloud Account](/zpc/offboarding-cloud-account).
[]
- **Provide User OCID**: Enter the User OCID which is the output after running the Terraform template.
- **Provide Tenancy OCID**: Enter the Tenancy OCID for your root compartment. ZPC uses the tenancy OCID to generate the Terraform template.
- **Download the Template**: Download the Terraform template which you need to run on your OCI tenant to finish onboarding.
- **Delete Organization**: Delete the organization. To learn more, see [Offboarding a Cloud Account](/zpc/offboarding-cloud-account).
[]
The Kubernetes tab displays details about all the cloud accounts you have onboarded on ZPC.
On the Kubernetes tab, you can do the following:
- Filter Kubernetes clusters using available parameters. To learn more, see [Using Filters](/zpc/using-filters).
- Export all Kubernetes cluster information as an Excel file. The downloaded Excel file follows the "Kubernetes_(timestamp)" naming convention.
- [Select and apply saved filters](/zpc/using-filters).
- [Hide the filters](/zpc/using-filters).
- Search for a Kubernetes cluster.
- View the following Kubernetes cluster details:
- **Cluster Name**: The cluster name.
- **Account**: The Kubernetes cluster's associated cloud account ID.
- **Region**: The Kubernetes cluster's region.
- **Kubernetes Version**: The current Kubernetes version running on the cluster.
- **Cloud**: The cloud service provider type.
- **Status**: Whether the Kubernetes cluster is onboarded and collecting metadata or not. The following status are available for Kubernetes clusters:
- **Success**: The Kubernetes cluster has been onboarded and ZPC is collecting configuration metadata.
- **Warning **: The Kubernetes cluster has been onboarded but is unable to collect metadata for some services.
- **Error**: The Kubernetes cluster has not been onboarded yet.
- **Suspended**: The Kubernetes cluster has been onboarded but the tenant license is expired. ZPC cannot collect configuration metadata for suspended Kubernetes clusters.
- **Failed**: The Kubernetes cluster has been onboarded but the cloud account is deleted. ZPC cannot collect configuration metadata for failed Kubernetes clusters.
- **Actions**: The following actions are available for Kubernetes clusters:
- **Delete**: Delete the Kubernetes cluster.
- **Download script**: Download the ZPC bash script to run on the Kubernetes cluster.
- [Modify the table and its columns](/zpc/using-tables).
![View the Kubernetes tab on ZPC.](/downloads/zpc/administration/cloud-accounts/viewing-kubernetes-tab/zpc-kubernetes-tab.png)