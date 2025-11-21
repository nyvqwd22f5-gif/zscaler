# App Connector Deployment Guide for Kubernetes
Source: https://help.zscaler.com/zpa/app-connector-deployment-guide-kubernetes
PDF: https://help.zscaler.com/pdf/com/en/1509356.pdf

This deployment guide provides information on prerequisites, how to deploy an App Connector on Kubernetes, and post-deployment verification checks. For general information regarding App Connector deployment for ZPA, see [About Deploying App Connectors](/zpa/about-deploying-connectors). RISE with SAP App Connector deployments are supported on SAP-managed Kubernetes clusters. To learn more about creating a provisioning key for your SAP-managed deployment, see [Configuring App Connectors](/zpa/configuring-connectors) and [About App Connector Provisioning Keys](/zpa/about-connector-provisioning-keys).
- [Step 1: Make Sure You Have Met All App Connector Deployment Prerequisites](#Prereqs)
- [Step 2: Deploy the App Connector on Kubernetes](#deploy)
- [Step 3: Verify the App Connector Deployment](#verifying)
- [Step 4: Manage Deployed App Connectors on Kubernetes](#managing-deployed-app-connectors-on-kubernetes)
[]
The following specifications are recommended by Zscaler for each ZPA App Connector:
- Memory: 4 GB RAM
For Zscaler Digital Experience (ZDX) deployments, Zscaler recommends App Connectors to have 8 GB of RAM.
- CPU:
- 2 CPU cores (Xeon E5 class) for physical machines without hyperthreading
- 4 CPU cores (Xeon E5 class) for virtual machines (VMs) with hyperthreading
For ZDX deployments, Zscaler recommends App Connectors to have 4 CPU cores.
Using the [PassMark Software Pty Ltd](https://www.cpubenchmark.net/cpu_list.php) benchmark to verify the CPU Mark score, Zscaler recommends using a minimum CPU benchmark score of 2640 when choosing a CPU processor. The Intel Advanced Encryption Standard New Instructions (AES-NI) instruction set must also be enabled on the CPU processor.
To learn more, see the [App Connector Deployment Guide](/zpa/app-connector-management/app-connector-deployment-guides-supported-platforms) for your platform.
- Disk Space: 64 GB (thin provisioned) for all deployment platforms
- Network Card: 1 NIC (minimum)
For VMware platform deployment, the default configuration to allow the host to dynamically allocate VM resources is not recommended. Configure the VM setting to reserve the following memory and CPU allocations:
- Memory: 8 GB RAM
- CPU: total CPU GHz (the number of cores (2 or 4 cores) multiplied by the GHz per core)
To learn more, refer to the [VMware documentation](https://docs.vmware.com/en/VMware-vSphere/7.0/com.vmware.vsphere.resmgmt.doc/GUID-8B88D3D8-E9D9-4C05-A065-B3DE1FFFB401.html).
Using these specifications, each App Connector supports up to 500 Mbps of throughput. To learn more, see [Understanding App Connector Throughput](/zpa/connector-deployment-prerequisites#ConnectorThroughput) in this article. Based on Zscaler's recommendations, determine the App Connector sizing requirements for your deployment. If disk space fills up in the App Connector, Zscaler recommends archiving files and creating more log space. To learn more, see [Monitoring App Connector Performance](/zpa/monitoring-connector-performance#diskspace_archive).
500 Mbps of throughput is an aggregate of multiple streams of traffic.
After an App Connector is enrolled, an outbound TLS tunnel over port 443 is established to the ZPA cloud infrastructure. This communication channel provides various functionality and utilizes minimal bandwidth, which includes the following traffic:
- Periodic keepalives to ZPA Public Service Edges or ZPA Private Service Edges
- Application learning
- Application health reporting
- App Connector software upgrades (upgrades are completed based on a weekly schedule)
You can deploy additional App Connectors at any time, using the same provisioning key to add them to the [existing App Connector group](/zpa/about-connectorgroups), while ensuring network and internet connectivity. App Connectors are designed to scale elastically. You can deploy additional App Connectors in the same App Connector group to increase the total throughput as required by your deployment. Zscaler recommends you have a minimum of two healthy App Connectors to always ensure an available path. To learn more, see [About Deploying App Connectors](/zpa/about-deploying-connectors) and [Supported Platforms for App Connectors](/zpa/app-connector-management/app-connector-deployment-guides-supported-platforms).
After deployment, ensure that the App Connector meets your sizing requirements. To learn more, see [Verify App Connector Sizing Requirements](/zpa/managing-deployed-connectors#VerifySizing).
- [Platform-Specific Prerequisites to Deploy an App Connector on Kubernetes](#platform-specific-prereqs)
- [Resources and Limits for App Connector Deployment for Kubernetes](#resources-and-limits)
[]The following platform-specific prerequisites are needed to deploy an App Connector on Kubernetes:
- Helm 3
- Metrics server
- DNS resolution and network access
- An App Connector [provisioning key](/zpa/about-connector-provisioning-keys) obtained from the ZPA Admin Portal
- Kubernetes version 1.30 is the minimum recommended version
- Intel x86_64-based architecture
For Kubernetes deployment only, the Docker image is supported on x86_64 systems; arm64 systems are not supported. This process assumes you have full network access during the Helm installation to the Docker images hosted on [https://hub.docker.com/u/zscaler](https://hub.docker.com/u/zscaler). To learn more about the different Docker images available, refer to [Docker Hub](https://hub.docker.com/r/zscaler/zpa-connector/tags?page=1&ordering=last_updated).
[]Because vulnerabilities are regularly found in open-source core components such as DNS resolvers and the Linux kernel, Zscaler recommends the following:
- Pointing the Helm chart to the most recent Docker tag and upgrading regularly. Zscaler recommends using a tagged version of Docker rather than the latest version when using the Helm chart.
- Creating firewall policies using Kubernetes network policies to protect App Connectors.
Some organizations choose to firewall or otherwise restrict outbound traffic to the internet from the data center. It is possible to deploy an App Connector in such an environment as long as the App Connector is able to reach all Zscaler data centers containing ZPA Public Service Edges. To learn more, see [firewall configuration information](https://config.zscaler.com/private.zscaler.com/zpa) for your deployment and [App Connector Security Guidance and Firewall Requirements](/zpa/app-connector-deployment-guide-openshift).
To set custom resources for your deployments, refer to the [Kubernetes documentation](https://kubernetes.io/docs/concepts/configuration/manage-resources-containers/).
- [CPU and Memory](#cpu-and-memory)
- [Horizontal Pod Autoscaler](#horizontal-pod-autoscaler)
[]A minimum of 2 cores and 4 GB RAM is recommended for each pod. CPU and memory are the only resources you can change. You typically only need to make these resource changes if the hosts don’t meet the minimum requirements and the pods fail to run.
The unit "m" is a fractional CPU unit that represents milliCPU in CPU measurement for Horizontal Pod Autoscaling in Kubernetes. A milliCPU is used to express CPU resources in thousandths of a CPU core. For example, 1000m is equivalent to one CPU core. When configuring resource requests and limits for containers in Kubernetes, CPU requests and limits can be specified using the "m" unit. For example, if a container requires 0.5 CPU cores, the CPU request would be 500m. Memory resources are defined in bytes. Normally, you use Mi (Mebibyte) or Gi (Gibibyte) units.
The resources and limits are currently set as follows:
`## @param zsglobal.resources section resources
resources:
## @param zsglobal.resources.limits When you specify a resource limit for a container, it uses this to enforce a limit on the running container.
limits:
memory: "8000Mi"
cpu: "8000m"
## @param zsglobal.resources.requests When you specify a resource request for a container, it uses this to enforce where to schedule a pod with the minimum requirements.
requests:
memory: "4000Mi"
cpu: "2000m"`
[]
[Horizontal Pod Autoscaler](https://kubernetes.io/docs/tasks/run-application/horizontal-pod-autoscale/) is supported per deployment based on CPU and memory metrics. The minimum recommended replicas for the App Connector is 2. The average utilization of 80% is used as a threshold for CPU/Memory usage in a Horizontal Pod Autoscaler deployment.
[]
You must install the App Connector Helm chart to deploy an App Connector on Kubernetes.
- [Get the Helm Chart](#get-helm-chart)
- [Install the Helm Chart](#install-helm-chart)
- [Verify the Helm Chart Installation](#verify-helm-installation)
[]
You can install a Helm chart by adding the Helm repository:
- To add the zpa-app-connector-kubernetes Helm repository:
`helm repo add zpa-helm-repo
https://dist.private.zscaler.com/helm-charts/k8s/
"zpa-helm-repo" has been added to your repositories`
- To verify the Helm repository:
`helm repo list
NAME           URL
zpa-helm-repo  https://dist.private.zscaler.com/helm-charts`
- To list the available zpa-app-connector-kubernetes Helm charts:
`helm search repo zpa-helm-repo
NAME CHART VERSION APP VERSION DESCRIPTION
zpa-helm-repo/zpa-app-connector-o... 0.1.0 23.386.1 A helm chart for deploying ZPA App Connector on...`
[]
After you have added the Helm repository, you can install the Helm chart.
You can retrieve the provisioning key from the [ZPA Admin Portal](https://admin.private.zscaler.com/). To learn more, see [About App Connector Provisioning Keys](/zpa/about-connector-provisioning-keys).
- Switch to the default namespace if you are not on it, using the following command:
`kubectl config set-context --current --namespace=default`
- From the default namespace, install the Helm chart using the following commands:
`helm install [NAME] [CHART] [flags]
helm install [NAME] --set zsglobal.provisionkey.value="<provision_key>"
repo_name/chart_name`
Below is an example of successfully installing the Helm chart:
`helm install zpa-connector --set zsglobal.provisionkey.value="1|api.private.zscaler.com|XXXXXX" zpa-helm-repo/zpa-app-connector-kubernetes
NAME: zpa-connector
LAST DEPLOYED: Wed May 10 16:21:02 2023
NAMESPACE: default
STATUS: deployed
REVISION: 1
TEST SUITE: None
NOTES:
Thank you for installing zpa-app-connector-kubernetes.
To learn more about the release, try:
$ helm status zpa-connector
$ helm get all zpa-connector
`
[]
To verify the Helm chart installation, use the following command:
`helm list
NAME         NAMESPACE REVISION UPDATED                             STATUS  CHART                            APP VERSION
zpa-connector default  1       2023-09-19 14:15:25.681803 -0700 PDT deployed zpa-app-connector-kubernetes-23.386.1 2023-08-18.amd64`
To verify if the pods are running, use the following command:
`kubectl get pods -n zscaler-zpa
NAME                                                        READY   STATUS        RESTARTS   AGE
zpa-connector-zpa-app-connector-kubernetes-f6f865fb8-qg2nx  1/1     Running       0          64s
zpa-connector-zpa-app-connector-kubernetes-f6f865fb8-spjtx  1/1     Running       0          19s`
`zscaler-zpa` is the namespace that is added when this Helm Chart is installed.
Only one Helm installation can be performed with the default Helm chart. If you need to install a new Helm chart, delete or upgrade the current one. You can also use the multiple App Connector groups deployment option if you want to deploy new App Connectors with new provisioning keys. To learn more, see [Deployment of Multiple App Connector Groups](/zpa/app-connector-deployment-guide-kubernetes#multiple-connector-groups).
Troubleshooting the Helm Chart Installation
To troubleshoot the installation:
- Inspect the Helm chart deployment.
-
Use the `kubectl describe` command to inspect the pod, deployment, HPA, roles, etc. This will provide details on each component for troubleshooting purposes.
`kubectl describe pod zpa-connector-zpa-app-connector-kubernetes-9bc54b95-ns2dt -n zscaler-zpa
Name:             zpa-connector-zpa-app-connector-kubernetes-9bc54b95-ns2dt
Namespace:        zscaler-zpa
Priority:         0
Service Account:  zscaler-zpa-sa
Node:             ip-xxx.us-west-2.compute.internal/10.xxx.xxx.245
Start Time:       Tue, 10 Sep 2024 14:45:54 -0700
Labels:           app.kubernetes.io/instance=zpa-connector
app.kubernetes.io/name=zpa-app-connector-kubernetes
pod-template-hash=9bc54b95
Annotations:      <none>
Status:           Running
IP:               100.xxx.xxx.185
IPs:
IP:           100.xxx.xxx.185
Controlled By:  ReplicaSet/zpa-connector-zpa-app-connector-kubernetes-9bc54b95
Containers:
zpa-app-connector-kubernetes:
Container ID:   containerd://64d79c395745ab1552557d53e3c3b3374201995b159b514d22d11c025b877cad
Image:          docker.io/zscaler/zpa-connector:<tagged-version>.amd64
Image ID:       docker.io/zscaler/zpa-connector@sha256:b253fdb858e67194fe525decab128896868c3c5200ccf66706c99800e0a86eeb
Port:           <none>
Host Port:      <none>
State:          Running
Started:      Fri, 13 Sep 2024 12:39:25 -0700
Last State:     Success
Reason:
Exit Code:    0
Started:      Fri, 13 Sep 2024 12:32:25 -0700
Finished:     Fri, 13 Sep 2024 12:39:24 -0700
Ready:          False
Restart Count:  1`
[]
[]
To verify the App Connector deployment:
- Verify that the deployed App Connector is [running and healthy](/zpa/managing-deployed-connectors#Status).
- Use the `kubectl top pod -n <namespace>` command to verify the resource usage of the deployed pods to ensure that the deployment meets [your sizing requirements](/zpa/managing-deployed-connectors#VerifySizing).
[]
- [After App Connectors are Deployed](#after-app-connectors-are-deployed)
- [Update App Connector Manager Software](#update-zpa-connector-software)
- [View App Connector Logs](#view-app-connector-logs)
- [Configure Auto Deletion of Disconnected App Connectors](#config-auto-deletion)
- [Helm Customization](#helm-customization)
- [Node Affinity](#node-affinity)
- [Deployment of Multiple App Connector Groups](#multiple-connector-groups)
- [Scale Down Kubernetes Pods](#scale-down-pods)
- [Kubernetes App Connector Linux Capabilities](#linux-capabilities)
[]
After App Connectors are deployed, you can:
- [Create application segments](/zpa/about-application/onboard) and [access policy rules](/zpa/about-policies) to pass application traffic through.
- [Configure a log receiver](/zpa/configuring-log-receiver) for your App Connectors to receive information about the App Connectors or users via the [Log Streaming Service (LSS)](/zpa/about-log-streaming-service).
[]
To update the App Connector Manager Software:
- Update the image version in the Helm chart to [the corresponding Docker tag](/zpa/app-connector-deployment-guide-openshift#image-version).
- [Upgrade the Helm chart](/zpa/app-connector-deployment-guide-openshift#helm-upgrade).
[]
To view App Connector logs, run the following command: `kubectl logs -f <Pod Name> -n zscaler-zpa`. For example:
`kubectl logs -f zpa-app-connector-kubernetes-f6f865fb8-78rlg -n zscaler-zpa`
[]
The threshold for App Connectors using the provisioning keys in an App Connector group is 100. The pods are ephemeral and consume a provisioning key utilization count each time they run. To avoid exceeding the App Connector threshold, Zscaler recommends configuring Auto Delete in your App Connector settings to remove App Connectors with a disconnected status after a set number of days. To learn more, see [Configuring App Connector Page Settings](/zpa/configuring-app-connectors-settings).
[]
- [Change Helm Values During Initial Installation](#helm-change-values)
- [Helm Upgrade](#helm-upgrade)
- [Helm List](#helm-list)
- [Helm Rollback](#helm-rollback)
- [Helm Delete](#helm-delete)
[]These Helm chart values only need to be changed if you need to customize the Helm chart. The domain (e.g., api.private.com) in the echo statement depends on what ZPA cloud you are on. To learn more, see [What Is My Cloud Name for ZPA?](/zpa/what-my-cloud-name-zpa)
To change Helm values during the initial installation:
- Open `values.yaml`.
-
You can change the following values:
- [Provision Key](#provision-key)
- [Image Version](#image-version)
- [Resources and Limits](#resources-limits)
Use the Helm install command when you change any values:
`helm install <release-name> zpa-app-connector-kubernetes/ -f zpa-app-connector-kubernetes/values.yaml`
The `<release-name>` represents the user-defined name you've specified to manage the Helm chart.
[]
`provisionkey:
## @param provisionkey.value The App Connector provision key. Replace this with the user's actual provision key.
value:
"1|api.private.zscaler.com|XXXXXX"`
[]
You should use a tag with a dated version rather than `latest.amd64` to ensure that the tag is a recent version. For example:
`tag: "2024-06-20.amd64"`
[]
`## @param zsglobal.resources section resources
resources:
## @param zsglobal.resources.limits When you specify a resource limit for a container, it uses this to enforce limit on the running container.
limits:
memory: "8000Mi"
cpu: "8000m"
## @param zsglobal.resources.requests When you specify a resource request for a container, it uses this to enforce where to schedule a pod with the minimum requirements.
requests:
memory: "4000Mi"
cpu: "2000m"`
[]
To upgrade the Helm repository zpa-app-connector-kubernetes, use the following command:
`helm upgrade <release-name> zpa-app-connector-kubernetes/ -f zpa-app-connector-kubernetes/values.yaml
helm upgrade <release-name> --set zsglobal.provisionkey.value="<provision_key>" zpa-app-connector-kubernetes/ -f zpa-app-connector-kubernetes/values.yaml
helm upgrade zpa-connector zpa-app-connector-kubernetes/ -f zpa-app-connector-kubernetes/values.yaml
Release "zpa-connector" has been upgraded. Happy Helming!
NAME: zpa-connector
LAST DEPLOYED: Thu Sep 14 22:51:10 2023
NAMESPACE: default
STATUS: deployed
REVISION: 2
NOTES:
Thank you for installing zpa-app-connector-kubernetes.
To learn more about the release, try:
$ helm status zpa-connector
$ helm get all zpa-connector`
[]
To list the Helm releases associated with zpa-app-connector-kubernetes, use the following command:
`helm list
NAME         NAMESPACE REVISION UPDATED                             STATUS  CHART                            APP VERSION
zpa-connector default  1       2023-09-19 14:15:25.681803 -0700 PDT deployed zpa-app-connector-kubernetes-23.386.1 2023-08-18.amd64`
[]
To roll back the Helm deployment, use the following command:
` helm rollback <release-name>`
This is not applicable to the initial version.
[]
To delete the Helm deployment, use the following command:
` helm delete <release-name>`
[]
Zscaler does not explicitly add node affinity for the App Connector Helm chart. To define nodes to be chosen for the App Connector pods to be scheduled on:
- Use the following commands to label the nodes:
`kubectl get nodes -A
kubectl label nodes <Node-name> type=zpa-app-connector`
- Use the following commands to add the namespace based on your nodes and match it with the label you added:
`kind: Namespace
metadata:
name: {{ .Values.zsglobal.namespace }}
+  annotations:
+    kubernetes.io/node-selector: "type=zpa-app-connector"`
With node affinity configured, the pods are only scheduled on the chosen nodes. To learn more, refer to the [Kubernetes documentation](https://kubernetes.io/docs/concepts/scheduling-eviction/assign-pod-node/).
[]
To support deployment of multiple App Connector groups:
-
To download the complete Helm chart, use the following URL:
`https://dist.private.zscaler.com/helm-charts/k8s/zpa-app-connector-kubernetes-<version>.tgz`
- Make the following changes to `values.yaml`:
Provide a meaningful identifier for the new provision key under `secretIdentifier`. For example, use an identifier that matches the one in the ZPA Admin Portal. You don't need to specify the number of App Connectors. The default starts with a minimum of 2, and then autoscales as needed.
`multiConnector:
## @param zsglobal.multiConnector.enabled Deploy multiple connectors.
enabled: true
## @param zsglobal.multiConnector.numAppConnectorGroups Number of App Connector groups.
numAppConnectorGroups: 2
## @param zsglobal.multiConnector.multipleProvisionKeys Key,value pair representing name of App Connector and provision key.
multipleProvisionKeys:
## @param zsglobal.multiConnector.secretIdentifier App Connector Secret Identifier for storing provision key
- secretIdentifier: "app-connector-1"
value: "1|api.private.zscaler.com|XXXXXX"
- secretIdentifier: "app-connector-2"
value: "1|api.private.zscaler.com|XXXXXX"`
-
Run the `helm install` command listed in [Install the Helm Chart](#install-helm-chart).
[Horizontal Pod Autoscaling](#horizontal-pod-autoscaler) occurs in each App Connector group per deployment.
For all updates, you can update the repository.
[]
During periods of low resource use or inactivity, you might want to manually reduce the number of pods running in your deployment to optimize resource usage and reduce costs. This is especially useful when the Horizontal Pod Autoscaler (HPA) generates excess pods during high-demand periods.
Use the following command to remove excess pods generated by the HPA during idle periods:
`kubectl scale deployment <deployment-name> --replicas=<replica-count-to-scale-down>`
Active sessions with applications are terminated when this command is run.
The parameters used in the command are as follows:
`<deployment-name>`: The name of the deployment you want to scale down.
`<replica-count-to-scale-down>`: The number of pods you want to keep running.
For example, if you have a deployment named `app-connector` that has 8 running pods, and you want to scale down this deployment to 3 pods, run the following command:
`kubectl scale deployment app-connector --replicas=3`
Kubernetes will terminate 5 running pods and any active sessions with applications.
You can use:
- After traffic spikes have subsided and resource demands are lower.
- During maintenance windows, when fewer resources are required.
- To temporarily override the HPA during specific scenarios where you need manual control over resource scaling.
[]
The following table provides a list of Kubernetes App Connector Linux capabilities that the container uses:
-
-
-
-
-
-
-
-
-
-
-
-
-
-
-
| Linux Capability | Behavior or Operation | Description |
| ---------------- | --------------------- | ----------- |
| `CAP_NET_ADMIN` | Performs the following network-related operations:Interfaces configuration.Administration of the IP firewall, masquerading, and accounting.Modifies the routing tables.Binds to any address for transparent proxying.Sets the type-of-service (TOS).Clears the driver statistics.Sets in promiscuous mode.Enables multicasting. | Fundamental to ZPA networking. |
| `CAP_NET_BIND_SERVICE` | Binds a socket to the internet domain privileged ports (port numbers less than 1024). | This capability is required to bind to a port below 1024. If you are running a service that listens to a port above 1024, remove this capability. |
| `CAP_NET_RAW` | Binds to any address for transparent proxying and uses RAW and PACKET sockets. | Fundamental to ZPA networking. |
| `CAP_SETFCAP` | Sets arbitrary capabilities on a file. | Set file capabilities. |
| `CAP_SYS_NICE` | Performs the following network-related operations:Lowers the processed nice value (i.e., nice(2) and setpriority(2)) and changes the nice value for arbitrary processes.Sets scheduling policies in real-time for the calling process and sets scheduling policies and priorities for arbitrary processes (i.e., sched_setscheduler(2), sched_setparam(2), and sched_attr(2)).Sets CPU affinity for arbitrary processes (i.e., sched_setaffinity(2)).Sets the input or output (I/O) scheduling class and priority for arbitrary processes (i.e., ioprio_set(2)).Applies migrate_pages(2) to arbitrary processes and allows the processes to migrate to arbitrary nodes.Applies move_pages(2) to arbitrary processes.Uses the MPOL_MF_MOVE_ALL flag with mbind(2) and move_pages(2). | ZPA forks new processes and assigns the CPU affinity. |
| `CAP_SYS_TIME` | Sets the system clock (i.e., settimeofday(2), time(2), adjtimex(2)) and the real-time (hardware) clock. | N/A |
| `CAP_SYS_RESOURCE` | Increases resource limits. | Increases resource limits for `SYS_RESOURCE`. |