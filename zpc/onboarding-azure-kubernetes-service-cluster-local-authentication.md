# Onboarding an Azure Kubernetes Service Cluster with Local Authentication
Source: https://help.zscaler.com/zpc/onboarding-azure-kubernetes-service-cluster-local-authentication
PDF: https://help.zscaler.com/pdf/com/en/1452946.pdf

Microsoft Azure Kubernetes Service (AKS) clusters allow multiple authentication and authorization requests to the Kubernetes API, including integrations with Azure Active Directory (AD).
If you have enabled Azure AD authentication via Kubernetes RBAC or Azure RBAC, you can onboard those AKS clusters on ZPC using a bash script. To learn more, see [Onboarding an Azure Kubernetes Service Cluster](/zpc/onboarding-azure-kubernetes-service-cluster).
If you have not enabled Azure AD integration for an AKS cluster, ZPC can use a certificate and a secret key to authenticate with the AKS cluster and collect configuration metadata. When you select clusters to onboard, ZPC generates a bash script and a secret key. You need to run the bash script on your Kubernetes clusters and submit the secret key when the bash script is running. The script:
- Creates a cluster role and role binding with the service principal used for onboarding the Microsoft Azure account.
- Allowlists the ZPC IP addresses if your Kubernetes cluster has authorized IP ranges enabled.
- Sends a verification certificate to ZPC.
To onboard an AKS cluster with local authentication:
- In the ZPC Admin Portal, go to **Administration** > **Cloud Accounts**.
- Click the **Accounts** tab.
- Click the **Actions** icon, then select the **Add Kubernetes Cluster** option for a Microsoft Azure account.
[See image.](#cluster-select-local-auth)
- On the **Cluster Selection** page, you can view and search for the following AKS cluster details available in the selected Microsoft Azure account:
- **Cluster Name**: Name of the AKS cluster.
- **Region**: Region of the AKS cluster.
- **Kubernetes Version**: Current Kubernetes version running on the cluster.
- **Status**: Onboarding status of the cluster (Success, Pending, or Failure).
- **Private Cluster**: Whether the cluster is public or private.
- **Kubelet Collection**: Use the toggle to control whether Kubelet configuration metadata needs to be collected or not.
- Select clusters you want to onboard, then click **Next**.
[See image.](#cluster-access-local-auth)
- On the **Cluster Access** page, click **Download the bash script**.
- Click **Regenerate** to update the Zscaler secret key, then click **Copy**.
Make sure you copy and save the secret key. You need to submit this secret key for subsequent AKS clusters onboarding. Regenerating a key has no impact on already onboarded clusters.
- Click **Log in to AZURE cloud console and execute the bash script and input secret key**.
- After the script is deployed, in the ZPC Admin Portal, click **Finish**.
[]
![View the cluster selection page on ZPC.](/downloads/zpc/administration/cloud-accounts/onboarding-kubernetes-clusters/onboarding-azure-kubernetes-service-cluster-local-authentication/zpc-cluster-selection.png)
[]
![View the cluster access page on ZPC.](/downloads/zpc/administration/cloud-accounts/onboarding-kubernetes-clusters/onboarding-azure-kubernetes-service-cluster-local-authentication/zpc-cluster-access.png)