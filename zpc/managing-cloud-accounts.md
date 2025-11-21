# Managing Cloud Accounts
Source: https://help.zscaler.com/zpc/managing-cloud-accounts
PDF: https://help.zscaler.com/pdf/com/en/1411286.pdf

Your cloud deployment infrastructure might change over time to meet your business needs. You might:
- Want to change business units for cloud accounts that serve a different purpose.
- Have removed a cloud account or no longer want ZPC to scan configuration metadata for a specific cloud account.
- Have removed Kubernetes clusters in your cloud deployments.
You can address such changes on the Zscaler Posture Control Admin Portal.
Changing Business Units for Multiple Cloud Accounts
To change business units for multiple cloud accounts:
- Go to **Administration** > **Cloud Accounts**, then click the **Accounts** tab.
- Select the checkboxes for the cloud accounts you want to manage.
[See image.](#select-cloud-accounts)
- Click the **Actions** drop-down menu, then click **Change Business Unit**.
- Select the business unit you want to move the cloud accounts to from the drop-down menu.
- Mark the **I understand the consequences and want to proceed** checkbox.
[See image.](#confirm-bu-transfer)
- Click **Apply**.
Offboarding a Cloud Account
To offboard a cloud account from ZPC:
- Go to **Administration** > **Cloud Accounts**, then click the **Accounts** tab.
- Click the **Actions** drop-down menu for the cloud account you want to offboard, then click the **Delete Account** button.
[See image.](#offboard-cloud-account)
- Mark the **I understand the consequences and want to proceed** checkbox.
- Click **Delete**.
[See image.](#confirm-account-offboard)
Deleting an Organization
You can also choose to delete an organization and all the accounts in the organization. To delete an organization:
- Go to **Administration** > **Cloud Accounts**, then click the **Organization** tab.
- Click the **Actions** drop-down menu for the organization you want to offboard, then click the **Delete Organization** button.
[See image.](#offboard-organization)
- Mark the **I understand the consequences and want to proceed** checkbox.
- Click **Delete**.
[See image.](#confirm-organization-offboard)
Offboarding a Kubernetes Cluster
You can remove a Kubernetes Cluster from your cloud service provider and stop ZPC from scanning configuration metadata for the cluster. To offboard a Kubernetes cluster:
- Go to **Administration** > **Cloud Accounts**.
- Select **Kubernetes**.
[See image.](#view-kubernetes-tab)
- In the **Actions** column, click the **Delete** icon for the cluster you want to delete.
- In the confirmation pop-up, click **Delete**.
[See image.](#delete-confirmation)
If you want to delete multiple clusters:
- Select the clusters you want to delete, then click **Actions** > **Delete**.
[See image.](#delete-multiple-clusters)
- In the confirmation pop-up, click **Delete**.
After you offboard a Kubernetes cluster, you need to remove the additional permissions ZPC has on your cloud service provider:
- [EKS Clusters](#eks-cluster-permission-removal)
- [AKS Clusters](#aks-cluster-permission-removal)
- [GKE Clusters](#gke-cluster-permission-removal)
[]
![View the cloud accounts page on ZPC.](/downloads/zpc/administration/cloud-accounts/offboarding-cloud-account/zpc-select-cloud-accounts.png)
[]
![View the business unit transfer confirmation pop-up.](/downloads/zpc/administration/cloud-accounts/offboarding-cloud-account/zpc-confirm-bu-change.png)
[]
![View the cloud account actions drop-down menu.](/downloads/zpc/administration/cloud-accounts/offboarding-cloud-account/zpc-offboard-cloud-account.png)
[]
![View the delete cloud account confirmation pop-up.](/downloads/zpc/administration/cloud-accounts/offboarding-cloud-account/zpc-delete-account.png)
[]
![View the organization actions drop-down menu.](/downloads/zpc/administration/cloud-accounts/offboarding-cloud-account/zpc-offboard-organization.png)
[]
![View the delete organization confirmation pop-up.](/downloads/zpc/administration/cloud-accounts/offboarding-cloud-account/zpc-delete-organization.png)
[]
On the [AWS Management Console](https://aws.amazon.com/console/), run the following commands on the AWS CloudShell:
-
eksctl delete iamidentitymapping --arn <zscalerRoleARN>
-
kubectl delete clusterrolebindings zpc-reader
-
kubectl delete clusterrole zpc-read-role
If the EKS cluster is hybrid (i.e., the cluster type is private and public) you need to remove the following ZPC IP addresses that are placed in the allowlist:
- `52.13.162.179/32`
- `52.12.66.25/32`
- `34.212.243.119/32`
[]
On the [Microsoft Azure Portal](https://portal.azure.com/#cloudshell/), run the following commands on the Azure Powershell:
- Delete the Azure Kubernetes Service Cluster User Role:
az role assignment delete --assignee “<service-principal-id>” --role “Azure Kubernetes Service Cluster User Role” --scope "/subscriptions/<subscriptionId>/resourceGroups/<resourceGroup>/providers/Microsoft.ContainerService/ManagedClusters/<cluster>"
- Delete ZPC's cluster role binding:
kubectl delete clusterrolebindings zpc-reader-"<$servicePrincipalObjectId>"
Run the following command to get your Service Principal Object ID:
az ad sp show --id <ZPC-Service-Principal-Id> --query id --out tsv"
[]
If the GKE cluster you offboarded had the control plane authorized networks enabled, you need to remove the following ZPC IP addresses that are placed in the allowlist:
- `52.13.162.179/32`
- `52.12.66.25/32`
- `34.212.243.119/32`
[]
![View the cloud accounts page on ZPC.](/downloads/zpc/administration/cloud-accounts/onboarding-kubernetes-clusters/zpc-select-kubernetes-tab.png)
[]
![View multiple cluster actions on ZPC.](/downloads/zpc/administration/cloud-accounts/onboarding-kubernetes-clusters/zpc-delete-cluster.png)
[]
![View the delete cluster pop-up on ZPC.](/downloads/zpc/administration/cloud-accounts/onboarding-kubernetes-clusters/zpc-delete-cluster-confirmation.png)