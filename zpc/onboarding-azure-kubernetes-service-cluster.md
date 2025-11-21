# Onboarding an Azure Kubernetes Service Cluster
Source: https://help.zscaler.com/zpc/onboarding-azure-kubernetes-service-cluster
PDF: https://help.zscaler.com/pdf/com/en/1447451.pdf

ZPC offers insight into your Microsoft Azure Kubernetes public clusters. ZPC provides a script for you to download and run on your AKS clusters. The script enables ZPC APIs to access and collect AKS cluster configuration metadata.
The script:
- Creates a cluster role and role binding with the service principal used for onboarding the Microsoft Azure account.
- Allowlists the ZPC IP addresses if your Kubernetes cluster has authorized IP ranges enabled.
Prerequisites
Before you onboard AKS clusters, you need to:
- Make sure the Microsoft Azure cloud accounts that contain the clusters are onboarded to ZPC. To learn how to onboard a Microsoft Azure account, see [Onboarding a Microsoft Azure Account](/zpc/onboarding-microsoft-azure-account).
- Make sure you are a Kubernetes Cluster Admin.
- Make sure you have necessary roles for the following authentication and authorization methods:
- **Azure AD Authentication with Kubernetes RBAC**: You need to be a part of the AAD group which has the Cluster Admin Access role.
- **Azure AD Authentication with Azure RBAC**: You have the `Azure Kubernetes Service RBAC Cluster Admin` role.
Onboarding AKS Clusters in a Single Microsoft Azure Account
To onboard AKS clusters in a single Microsoft Azure account on ZPC:
- In the ZPC Admin Portal, go to **Administration** > **Cloud Accounts**.
- Click the **Accounts** tab.
- Click the **Actions** icon, then select the **Add Kubernetes Cluster** option for a Microsoft Azure account.
[See image.](#add-aks-cluster)
- On the **Cluster Selection** page, you can view and search for the following AKS cluster details available in the selected Microsoft Azure account:
- **Cluster Name**: Name of the AKS cluster.
- **Region**: Region of the AKS cluster.
- **Kubernetes Version**: Current Kubernetes version running on the cluster.
- **Status**: Onboarding status of the cluster (Success, Pending, or Failure).
- **Private Cluster**: Whether the cluster is public or private.
- Select clusters you want to onboard, then click **Next**.
[See image.](#cluster-access)
- On the **Cluster Access** page, click **Download the bash script**.
- Click **Log in to AZURE cloud console and execute the bash script**.
- After the script is deployed, in the ZPC Admin Portal, click **Finish**.
Onboarding AKS clusters in a Microsoft Azure organization
You can choose to onboard AKS clusters from multiple accounts belonging to a single Microsoft Azure organization. To onboard AKS clusters in a Microsoft Azure organization on ZPC:
- In the ZPC Admin Portal, go to **Administration** > **Cloud Accounts**.
- Click the **Organizations** tab.
- Click the **Actions** icon, then select the **Add Kubernetes Cluster** option for a Microsoft Azure account.
[See image.](#add-aks-org-cluster)
- On the **Cluster Selection** page, you can view and search for the following AKS cluster details available on the selected Microsoft Azure organization:
- **Cluster Name**: Name of the AKS cluster.
- **Region**: Region of the AKS cluster.
- **Kubernetes Version**: Current Kubernetes version running on the cluster.
- **Status**: Onboarding status of the cluster (Success, Pending, or Failure).
- **Private Cluster**: Whether the cluster is public or private.
- Select clusters you want to onboard, then click **Next**.
[See image.](#cluster-access-org)
- On the **Cluster Access** page, click **Download the bash script**.
- Click **Log in to AZURE cloud console and execute the bash script**.
- After the script is deployed, in the ZPC Admin Portal, click **Finish**.
[]
![View the cluster selection page on ZPC](/downloads/zpc/administration/cloud-accounts/onboarding-kubernetes-clusters/onboarding-azure-kubernetes-service-cluster/zpc-aks-add-cluster.png)
[]
![View the cluster selection page on ZPC](/downloads/zpc/administration/cloud-accounts/onboarding-kubernetes-clusters/onboarding-azure-kubernetes-service-cluster/zpc-aks-org-add-cluster.png)
[]
![View the cluster access page on ZPC](/downloads/zpc/administration/cloud-accounts/onboarding-kubernetes-clusters/onboarding-azure-kubernetes-service-cluster/zpc-aks-cluster-access.png)
[]
![View the cluster access page on ZPC](/downloads/zpc/administration/cloud-accounts/onboarding-kubernetes-clusters/onboarding-azure-kubernetes-service-cluster/zpc-aks-cluster-access.png)