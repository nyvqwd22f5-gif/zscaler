# Onboarding a Google Kubernetes Engine Cluster
Source: https://help.zscaler.com/zpc/onboarding-google-kubernetes-engine-cluster
PDF: https://help.zscaler.com/pdf/com/en/1442816.pdf

ZPC offers insight into your Google Kubernetes Engines (GKE) clusters. ZPC provides a script for you to download and run on your GKE clusters. The script enables ZPC APIs to access and collect GKE cluster configuration metadata. The script allowlists the ZPC IP address in the GKE cluster's `Control plane authorized networks` property.
If the GKE cluster is public, and has the `Control plane authorized networks` property disabled, the cluster is automatically be onboarded on ZPC.
Prerequisites
Before you onboard GKE clusters, you need to:
- Make sure the Kubernetes Engine API is enabled on the GCP service account project and the onboarded project.
- Make sure the service account has the viewer role to collect GKE configuration metadata.
Onboarding GKE Clusters in a single GCP account
To onboard GKE clusters in a single GCP account on ZPC:
- In the ZPC Admin Portal, go to **Administration** > **Cloud Accounts**.
- Click the **Accounts** tab.
- Click the **Actions** icon, then select the **Add Kubernetes Cluster** button for a GCP account.
[See image.](#add-gke-cluster)
- On the **Cluster Selection** page, you can view and search for the following GKE cluster details available on the selected GKE account:
- **Cluster Name**: Name of the GKE cluster.
- **Region**: Region of the GKE cluster.
- **Kubernetes Version**: Current Kubernetes version running on the cluster.
- **Status**: Onboarding status of the cluster (Success, Pending, or Failure).
- **Private Cluster**: View whether the cluster is private or public.
- **Control Plane Authorized Networks**: View whether the kubernetes cluster has authorized networks enabled or disabled.
- **Private Endpoint Enabled**: View the endpoint access type.
ZPC cannot onboard clusters with private only endpoint access. ZPC also needs you to allowlist your CloudShell IP address if you're onboarding a public and private cluster.
- Select clusters you want to onboard, then click **Next**.
[See image.](#select-gke-cluster)
If you have selected public clusters, they are automatically onboarded to ZPC. Hybrid clusters require you to run a bash script on the clusters for ZPC to communicate and collect metadata.
- On the **Cluster Access** page, click **Download the bash script**.
- Click **Log in to the GCP cloud console and execute the bash script**.
- After the script is deployed, in the ZPC Admin Portal, click **Finish**.
[See image.](#access-gke-cluster)
Onboarding GKE clusters in a GCP organization
You can choose to onboard GKE clusters from multiple account belonging to a single GCP organization. To onboard GKE clusters in a GCP organization on ZPC:
- In the ZPC Admin Portal, go to **Administration** > **Cloud Accounts**.
- Click the **Organizations** tab.
- Click the **Actions** icon, then select the **Add Kubernetes Cluster** button for a GCP organization.
[See image.](#add-gke-org-cluster)
- On the **Cluster Selection** page, you can view and search for the following GKE cluster details available on the selected GCP organization:
- **Cluster Name**: Name of the GKE cluster.
- **Region**: Region of the GKE cluster.
- **Kubernetes Version**: Current Kubernetes version running on the cluster.
- **Status**: Onboarding status of the cluster (Success, Pending, or Failure).
- **Private Cluster**: View whether the cluster is private or public.
- **Control Plane Authorized Networks**: View whether the kubernetes cluster has authorized networks enabled or disabled.
- **Private Endpoint Enabled**: View the endpoint access type.
ZPC cannot onboard clusters with private only endpoint access. ZPC also needs you to allowlist your CloudShell IP address if you're onboarding a public and private cluster.
- Select clusters you want to onboard, then click **Next**.
[See image.](#select-gke-org-cluster)
If you have selected public clusters, they are automatically onboarded to ZPC. Hybrid clusters require you to run a bash script on the clusters for ZPC to communicate and collect metadata.
- On the **Cluster Access** page, click **Download the bash script**.
- Click **Log in to the GCP cloud console and execute the bash script**.
- After the script is deployed, in the ZPC Admin Portal, click **Finish**.
[See image.](#access-gke-org-cluster)
[]
![View the add cluster button for GCP cloud accounts.](/downloads/zpc/administration/cloud-accounts/onboarding-kubernetes-clusters/onboarding-google-kubernetes-engine-cluster/zpc-gke-select-cluster.png)
[]
![View the select GKE clusters page.](/downloads/zpc/administration/cloud-accounts/onboarding-kubernetes-clusters/onboarding-google-kubernetes-engine-cluster/zpc-gke-select-cluster.png)
[]
![View the GKE cluster access page on ZPC.](/downloads/zpc/administration/cloud-accounts/onboarding-kubernetes-clusters/onboarding-google-kubernetes-engine-cluster/zpc-gke-cluster-access.png)
[]
![View the add cluster button for GCP organizations.](/downloads/zpc/administration/cloud-accounts/onboarding-kubernetes-clusters/onboarding-google-kubernetes-engine-cluster/zpc-gke-org-add-cluster.png)
[]
![View the select GKE clusters page.](/downloads/zpc/administration/cloud-accounts/onboarding-kubernetes-clusters/onboarding-google-kubernetes-engine-cluster/zpc-gke-select-cluster.png)
[]
![View the GKE cluster access page on ZPC.](/downloads/zpc/administration/cloud-accounts/onboarding-kubernetes-clusters/onboarding-google-kubernetes-engine-cluster/zpc-gke-cluster-access.png)