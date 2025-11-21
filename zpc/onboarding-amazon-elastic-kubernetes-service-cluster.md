# Onboarding an Amazon Elastic Kubernetes Service Cluster
Source: https://help.zscaler.com/zpc/onboarding-amazon-elastic-kubernetes-service-cluster
PDF: https://help.zscaler.com/pdf/com/en/1433796.pdf

ZPC offers insight into your Amazon Elastic Kubernetes Service (EKS) public and hybrid clusters. ZPC provides a script for you to download and run on your EKS clusters. The script enables ZPC APIs to access and collect EKS cluster configuration metadata. The script:
- Updates the `publicAccessCidr` property of the hybrid (public and private) clusters with ZPC IP addresses.
- Creates a cluster role binding within Kubernetes.
- Creates an IAM identity mapping.
Prerequisites
Before you onboard EKS clusters, you need to:
- Make sure the AWS cloud accounts that contain the clusters are onboarded to ZPC. To learn how to onboard an AWS account, see [Onboarding an Amazon Web Services Account](/zpc/onboarding-amazon-web-services-account).
- Make sure you are a Kubernetes Cluster Admin.
- Have permissions to:
- Update `aws-auth` configmap in the `kube-system` namespace.
- Create, update, and delete the cluster role and the cluster role binding.
- Have the following additional permissions for hybrid clusters:
- `UpdateClusterConfig`
- `DescribeCluster`
To learn more, see the [AWS documentation](https://docs.aws.amazon.com/eks/latest/userguide/add-user-role.html).
Onboarding EKS Clusters in a Single AWS account
To onboard EKS clusters in a single AWS account on ZPC:
- In the ZPC Admin Portal, go to **Administration** > **Cloud Accounts**.
- Click the **Accounts** tab.
- Click the **Actions** icon, then select the **Add Kubernetes Cluster** button for an AWS account.
[See image.](#view-cloud-accounts)
-
On the **Cluster Selection** page, you can view and search for the following EKS cluster details available in the selected AWS account:
- **Cluster Name**: Name of the EKS cluster.
- **Region**: Region of the EKS cluster.
- **Kubernetes Version**: Current Kubernetes version running on the cluster.
- **Endpoint Access**: View the endpoint access type.
- **Status**: Onboarding status of the cluster (Success, Pending, or Failure).
ZPC cannot onboard clusters with private-only endpoint access. ZPC also needs you to allowlist your CloudShell IP address if you're onboarding a public and private cluster.
- Select clusters you want to onboard, then click **Next**.
[See image.](#select-clusters)
- On the **Cluster Access** page, click **Download the bash script**.
- Click **Log in to the AWS cloud console and execute the bash script**.
- After the script is deployed, in the ZPC Admin Portal, click **Finish**.
[See image.](#cluster-access)
Onboarding EKS clusters in an AWS organization
You can choose to onboard EKS clusters from multiple accounts belonging to a single AWS organization. To onboard EKS clusters in an AWS organization on ZPC:
- On the ZPC Admin Portal, go to **Administration** > **Cloud Accounts**.
- Click the **Organizations** tab.
- Click the **Actions** icon, then select the **Add Kubernetes Cluster** button for an AWS organization.
[See image.](#view-cloud-accounts-org)
-
On the **Cluster Selection** page, you can view and search for the following EKS cluster details available on the selected AWS organization:
- **Cluster Name**: Name of the EKS cluster.
- **Region**: Region of the EKS cluster.
- **Kubernetes Version**: Current Kubernetes version running on the cluster.
- **Endpoint Access**: View the endpoint access type.
- **Status**: Onboarding status of the cluster (Success, Pending, or Failure).
ZPC cannot onboard clusters with private-only endpoint access. ZPC also needs you to allowlist your CloudShell IP address if you're onboarding a public and private cluster.
- Select clusters you want to onboard, then click **Next**.
[See image.](#select-clusters-org)
- On the **Cluster Access** page, click **Download the bash script**.
- Click **Log in to the AWS cloud console and execute the bash script**.
- After the script is deployed, in the ZPC Admin Portal, click **Finish**.
[See image.](#cluster-access-org)
[]
![View the cloud accounts page on ZPC](/downloads/zpc/administration/cloud-accounts/onboarding-kubernetes-clusters/onboarding-kubernetes-account/zpc-eks-cloud-accounts.png)
[]
![View the cluster selection page on ZPC](/downloads/zpc/administration/cloud-accounts/onboarding-kubernetes-clusters/onboarding-kubernetes-account/zpc-eks-cluster-selection.png)
[]
![View the cluster access page on ZPC](/downloads/zpc/administration/cloud-accounts/onboarding-kubernetes-clusters/onboarding-kubernetes-account/zpc-eks-cluster-access.png)
[]
![View the cloud accounts page on ZPC](/downloads/zpc/administration/cloud-accounts/onboarding-kubernetes-clusters/onboarding-kubernetes-account/zpc-eks-cloud-accounts.png)
[]
![View the cluster selection page on ZPC](/downloads/zpc/administration/cloud-accounts/onboarding-kubernetes-clusters/onboarding-kubernetes-account/zpc-eks-cluster-selection.png)
[]
![View the cluster access page on ZPC](/downloads/zpc/administration/cloud-accounts/onboarding-kubernetes-clusters/onboarding-kubernetes-account/zpc-eks-cluster-access.png)