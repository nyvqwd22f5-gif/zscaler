# Onboarding a Private Google Kubernetes Engine Cluster
Source: https://help.zscaler.com/zpc/onboarding-private-google-kubernetes-engine-cluster
PDF: https://help.zscaler.com/pdf/com/en/1459166.pdf

Private GKE clusters offer an additional layer of security by only allowing API access to the Kubernetes control plane from within the network where the cluster is deployed. ZPC cannot make inbound API requests into the Kubernetes control plane to retrieve configuration details for private GKE clusters.
ZPC offers a lightweight agent that can be deployed on the GKE private cluster which has access to the Kubernetes API and sends configuration metadata back to ZPC. The agent typically consumes 100MB to 300MB, and upto 500MB of memory to function.
Prerequisites
Ensure that the private GKE cluster has ingress firewall rules for the following protocols and ports enabled:
- udp:53
- tcp:53
- tcp:22
- tcp:10250
Onboarding Private GKE Clusters
To onboard private GKE clusters to ZPC:
- In the Zscaler Posture Control Admin Portal, go to **Administration** > **Cloud Accounts**.
- Click the **Accounts** tab.
- Click the **Actions** icon, then select **Add Kubernetes Cluster** for a GCP account.
[See image.](#add-gke-cluster-image)
- On the **Cluster Selection** page, you can view and search for the following GKE cluster details available on the selected GCP account:
- **Cluster Name**: Name of the GKE cluster.
- **Region**: Region of the GKE cluster.
- **Kubernetes Version**: Current Kubernetes version running on the cluster.
- **Status**: Onboarding status of the private cluster. The following onboarding status are available:
- **Success**: The agent is sending all required information to ZPC.
- **Pending**: The agent is deployed on your GKE cluster but has not connected to ZPC yet.
- **Warning**: ZPC is receiving only partial data from the agent.
- **Error**: The agent is unable to connect to ZPC or is able to connect but is unable to send any information to ZPC.
- **Private Cluster**: View whether the Kubernetes cluster is private or public.
- **Control Plane Authorized Networks**: View whether the Kubernetes cluster has authorized networks enabled or disabled.
- **Private Endpoint Enabled**: View whether the Kubernetes cluster is private or public.
- **Kubelet Collection**: Use the toggle button to enable or disable Kubelet configuration metadata collection.
- Select the GKE clusters you want to onboard to ZPC.
[See image.](#gke-private-cluster-selection)
- On the **Cluster Access** page, you can view the following details for each GKE private clusters:
- **Cluster Name**: Name of the private GKE cluster.
- **Account**: The GCP cloud account name.
- **Region**: Region of the private GKE cluster.
- **API Key**: Download the API key .env file for the private GKE cluster. ZPC generates a unique API key for each private cluster you have chosen to onboard.
- **CRD**: Download the Custom Resource Definition (CRD) .yaml file for the private GKE cluster. ZPC extends the Kubernetes API and creates a unique custom resource definition file for installing ZPC agents on your GKE private clusters.
- [Creating the ZPC Agent on a GKE Private Cluster.](#create-agent-on-gcp)
If you have selected public and private clusters on the **Cluster Selection** page, you can view details for both cluster types.
- Click **Finish**.
[See image.](#gke-private-cluster-access)
After you click **Finish**, the GKE cluster's status changes to "Pending". When ZPC is able to confirm you have completed the GKE private cluster onboarding on the GCP Cloud Console, the GKE cluster's status changes to "Success".
You cannot view the created API key for the GKE cluster again, but regenerate or deactivate the API key for each cluster in the "Pending" status. You may have deleted the GKE cluster and want to deactivate the API key or rotate the API key to meet your company's compliance standards.
- [Regenerating or Deactivating the API key on ZPC.](#regen-deactivate-api-key)
You can download the CRD file for each private GKE cluster in the "Pending" status.
- [Download the CRD file on ZPC.](#downloading-crd-file)
[]
To regenerate or deactivate the API key:
- In the Zscaler Posture Control Admin Portal, go to **Administration** > **Cloud Accounts**.
- Click the **Kubernetes** tab.
- Click the **Actions** icon for the GKE cluster you want to regenerate or deactivate the API key.
[See image.](#gke-private-actions)
- Click **Regenerate API Key** to regenerate the API key. You need to copy the bash command and run it on your GKE private cluster for ZPC to continue collecting configuration metadata. You also need to reinstall the operator with the new API key and the CRD file. To learn more, see the [Creating the ZPC Agent on a GKE Private Cluster.](/zpc/onboarding-private-google-kubernetes-engine-cluster#create-agent-on-gcp) section of this article.
[See image.](#gke-private-regenerate-private-key)
- Click **Deactivate API Key** to deactivate the API key. ZPC can no longer collect configuration metadata.
[]
![View the actions drop-down menu for GKE clusters.](/downloads/zpc/administration/cloud-accounts/onboarding-kubernetes-clusters/onboarding-private-google-kubernetes-engine-cluster/zpc-private-gke-actions-menu.png)
[]
![View the regenerate API key pop-up menu on ZPC](/downloads/zpc/administration/cloud-accounts/onboarding-kubernetes-clusters/onboarding-private-google-kubernetes-engine-cluster/zpc-private-gke-regenerate-api-pop-up.png)
[]
To download the CRD .yaml file on ZPC for a private GKE cluster:
- In the Zscaler Posture Control Admin Portal, go to **Administration** > **Cloud Accounts**.
- Click the **Kubernetes** tab.
- Click the **Actions** icon for the GKE cluster you want to download the CRD file for.
- Click **Download CRD**.
[]
![View the add Kubernetes cluster for GCP cloud accounts.](/downloads/zpc/administration/cloud-accounts/onboarding-kubernetes-clusters/onboarding-private-google-kubernetes-engine-cluster/zpc-private-gke-add-gke-cluster.png)
[]
![View the cluster selection page for GKE on ZPC.](/downloads/zpc/administration/cloud-accounts/onboarding-kubernetes-clusters/onboarding-private-google-kubernetes-engine-cluster/zpc-private-gke-cluster-selection-page.png)
[]
![View the cluster access page for GKE on ZPC.](/downloads/zpc/administration/cloud-accounts/onboarding-kubernetes-clusters/onboarding-private-google-kubernetes-engine-cluster/zpc-private-gke-cluster-access-ui.png)
[]
You can create a ZPC agent on your private GKE clusters using the API key, operator, and the CRD file generated on ZPC.
To create a ZPC agent on a private GKE cluster:
- Access the [GCP Cloud Console](https://console.cloud.google.com/), and enter `Kubernetes Clusters` in the Search bar.
[See image.](#gcp-kubernetes-clusters)
- Select the private cluster you have chosen to onboard to ZPC.
[See image.](#select--gke-private-clusters)
- Click **CONNECT**, then copy the command-line access command. You need to connect to this private cluster using this command from a linked VM instance.
[See image.](#get-command-line-access)
- Enter `Compute Engine` in the Search bar.
[See image.](#gcp-compute-engine-search)
- Connect to the VM instance linked to the private Kubernetes cluster you have chosen to onboard to ZPC.
[See image.](#gcp-ssh-connect-vm)
- Run the command-line access bash command you copied in a previous step to access the private GKE cluster.
- Run the following command to create a namespace on the private GKE cluster for ZPC:
kubectl create ns zpc
- Upload the API Key .env and the CRD .yaml file to the private GKE cluster.
[See image.](#gcp-upload-yaml-files)
- Run the following command to create the ZPC API key on your private GKE cluster:
kubectl create secret generic zpc-api-key-credentials --save-config --dry-run=client --from-env-file=<API Key file name> --namespace=zpc -o yaml | kubectl apply -f -
- Run the following command to create the ZPC operator on your private GKE cluster:
curl -s https://int.app.zscwp.io/kspm-script/operator_install.sh | bash -s https://int.api.zscwp.io 060838874158.dkr.ecr.us-west-2.amazonaws.com 1.0.0 us
Creating the ZPC operator on your GKE private cluster requires you to submit the API key generated on ZPC.
- Run the following command to create the ZPC custom resource definition on your private GKE cluster:
kubectl apply -f kubernetesagent.yaml
[]
![View how to access Kubernetes clusters on GCP.](/downloads/zpc/administration/cloud-accounts/onboarding-kubernetes-clusters/onboarding-private-google-kubernetes-engine-cluster/zpc-private-gcp-kubernetes-clusters.png)
[]
![Select private GKE cluster on GCP.](/downloads/zpc/administration/cloud-accounts/onboarding-kubernetes-clusters/onboarding-private-google-kubernetes-engine-cluster/zpc-private-gke-select-cluster.png)
[]
![Get command to access private GKE cluster.](/downloads/zpc/administration/cloud-accounts/onboarding-kubernetes-clusters/onboarding-private-google-kubernetes-engine-cluster/zpc-private-gke-get-command-line-access-gcp.png)
[]
![View Compute Engines on GCP.](/downloads/zpc/administration/cloud-accounts/onboarding-kubernetes-clusters/onboarding-private-google-kubernetes-engine-cluster/zpc-private-gke-compute-engines.png)
[]
![View accessing SSH terminal for virtual machine.](/downloads/zpc/administration/cloud-accounts/onboarding-kubernetes-clusters/onboarding-private-google-kubernetes-engine-cluster/zpc-private-gke-ssh-connect-vm.png)
[]
![View uploaded YAML files on GKE cluster.](/downloads/zpc/administration/cloud-accounts/onboarding-kubernetes-clusters/onboarding-private-google-kubernetes-engine-cluster/zpc-private-gke-upload-yaml-file.png)