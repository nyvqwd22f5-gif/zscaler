# App Connector Deployment Guide for OpenShift
Source: https://help.zscaler.com/zpa/app-connector-deployment-guide-openshift
PDF: https://help.zscaler.com/pdf/com/en/1485886.pdf

This deployment guide provides information on prerequisites, how to deploy an App Connector on Openshift, and post-deployment verification checks. For general information regarding App Connector deployment for ZPA, see [About Deploying App Connectors](/zpa/about-deploying-connectors).
- [Step 1: Make Sure You Have Met All App Connector Deployment Prerequisites](#Prereqs)
- [Step 2: Deploy the App Connector on OpenShift](#deploy)
- [Step 3: Verify the App Connector Deployment](#verifying)
- [Step 4: Manage Deployed App Connectors on OpenShift](#managing-deployed-app-connectors-on-openshift)
[]
Before deploying a ZPA App Connector on any supported platform, Zscaler highly recommends reading the following information and making the necessary changes to your organization's environment, where applicable.
- [App Connector Specifications and Sizing Requirements](#SpecsAndSizing)
- [App Connector Platform Prerequisites](#PlatformPrereqs)
- [App Connector Security Guidance and Firewall Requirements](#SecurityAndFirewallReqs)
After you have met all the prerequisites, you can deploy the App Connector on a supported platform.
[]The following specifications are recommended by Zscaler for each ZPA App Connector:
- Memory: 4 GB RAM
For Zscaler Digital Experience (ZDX) deployments, Zscaler recommends App Connectors to have 8 GB of RAM.
- CPU:
- 2 CPU cores (Xeon E5 class) for physical machines without hyperthreading
- 4 CPU cores (Xeon E5 class) for virtual machines (VMs) with hyperthreading
- Both Amazon Web Services (AWS) and Google Cloud Platform (GCP) require a minimum of 4 CPU cores due to hyperthreading
- To deploy an App Connector on AWS, Zscaler recommends using t3.xlarge (for non-production or low traffic App Connectors) or m5a.xlarge (for production or high traffic App Connectors)
- To deploy an App Connector on GCP, Zscaler recommends using a Linux RPM on n2-standard-4 or n2-highcpu-4
- Azure VMs older than V3 require 2 CPU cores, while VMs V3 and later require 4 CPU cores due to hyperthreading
- To deploy an App Connector on Azure, Zscaler recommends using Standard_F4s_v2 or Standard_D4s_v3 or later
To enable AppProtection using the default AppProtection profile provided by Zscaler, we recommend that your App Connectors have at least 8 CPU cores and 8 GB of memory. Ensure that your App Connectors are less than 40% for peak memory utilization and peak CPU utilization. If your CPU or memory utilization is above the suggested maximum, you need to add App Connectors to reach the maximum peak of 40% CPU and memory without AppProtection enabled. This rule also applies if you are using a smaller VM (4 CPUs, 4 GB). Your App Connector throughput might be 100 to 200 Mbps depending on App Connector sizing when using AppProtection. Monitor your App Connectors by going to the [App Connector dashboard](/zpa/viewing-app-connectors-dashboard).
The AppProtection recommendations are based on a mix of web traffic, 85% GET requests, and 15% POST and payload and response sizes of 32 KB. Smaller payload and response sizes might require less App Connector resources and result in higher throughput.
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
You can deploy additional App Connectors at any time, using the same provisioning key to add them to the [existing App Connector Group](/zpa/about-connectorgroups), while ensuring network and internet connectivity. App Connectors are designed to scale elastically. You can deploy additional App Connectors in the same App Connector Group to increase the total throughput as required by your deployment. Zscaler recommends you have a minimum of two healthy App Connectors to always ensure an available path. To learn more, see [About Deploying App Connectors](/zpa/about-deploying-connectors) and [Supported Platforms for App Connectors](/zpa/app-connector-management/app-connector-deployment-guides-supported-platforms).
After deployment, ensure that the App Connector meets your sizing requirements. To learn more, see [Verify App Connector Sizing Requirements](/zpa/managing-deployed-connectors#VerifySizing).
[]Understanding App Connector Throughput
Throughput numbers are aggregate (i.e., total inbound and outbound). The following best practices apply regarding App Connector throughput sizing:
- Check your existing VPN solution's average and peak throughput. Be sure to only account for user/client VPN traffic and not any site-to-site tunnel traffic.
- App Connectors communicate over the provided (default) gateway, which is most likely your ISP WAN broadband connection.
- Using double encryption affects throughput. However, the effect varies based on the number of applications that are enabled for double encryption.
So, if you have a 1 Gbps connection (aggregate) in your data center, you can use the throughput guidelines in the following table to make sure that you have enough App Connectors to support the connection and room for failover (N+1). For example, with a 1 Gbps connection, you would need to deploy 2 to 3 App Connectors if your applications are not using double encryption, but 4 to 6 App Connectors if they are. To learn more, see [Understanding Double Encryption](/zpa/understanding-double-encryption).
The following throughput guidelines apply based upon the recommended App Connector specifications:
| % of Applications with Double Encryption | Per App Connector Throughput |
| ---------------------------------------- | ---------------------------- |
| 0% | 500 Mbps |
| 25% | 437.5 Mbps |
| 50% | 375 Mbps |
| 75% | 312.5 Mbps |
| 100% | 250 Mbps |
It is possible to increase App Connector throughput up to 1 Gbps per App Connector by running the App Connector on hardware with more memory and CPUs along with increased network link speed. If you have a 10 Gbps connection (aggregate) in your data center, and you want to increase the App Connector throughput up to 1 Gbps per App Connector, you can increase the underlying VM spec as follows:
- 8 vCPU cores for virtual machines or 4 CPU cores for physical machines
- 8 GB RAM
The exact throughput can vary and depends on other network factors such as your internal network setup, latency, and whether you have double encryption, App Protection, and/or ZDX enabled. Make sure that you have enough App Connectors to support the connection and room for failover (N+1).
Zscaler recommends that you have more App Connectors with lower specifications rather than fewer App Connectors with higher specifications to horizontally scale your deployment. For example, if you have fewer App Connectors with higher specifications and one fails, you could adversely affect more user application traffic/sessions than a smaller App Connector that fails.
[]Before you begin any procedures within the [App Connector Deployment Guide](/zpa/app-connector-management/app-connector-deployment-guides-supported-platforms) for your platform, make sure that you have the following:
-
Intel x86_64/AMD64-based architecture
-
systemd
-
Root or sudo access to the system to configure a new package repository and install packages
-
DNS resolution and network access
-
An App Connector [provisioning key](/zpa/about-connectorprovisioning) obtained from the ZPA Admin Portal
-
A static MAC address
[]App Connectors can be deployed in different ways (as private cloud VMs, public cloud VMs, or OS packages), so the security features for each deployment type are slightly different.
Zscaler recommends treating access to App Connectors as privileged, so only authorized personnel can access an App Connector's console. By limiting access, there is the added benefit of shielding inter-process communication within the App Connector from attack.
Operating System Security
The App Connector VMs distributed by Zscaler for use in private clouds are configured without any remotely accessible services running. Swap partitions are disabled on the App Connector VMs to ensure that memory growth does not have an impact on App Connector performance. For enhanced security, you must use the `passwd` command to change the credentials on the default admin account. To learn more, see the [App Connector Deployment Guide](/zpa/app-connector-management/app-connector-deployment-guides-supported-platforms) for the platform you're using.
ZPA provides Security Technical Implementation Guide (STIG) VM images for AWS, GCP, Microsoft Azure, Nutanix, and VMware by default. To learn more, see [App Connector Software by Platform](/zpa/zpa-app-connector-software-by-platform). The remaining private and public cloud VM images provided by Zscaler are configured with minimal listening services to reduce the remotely exploitable attack surface. Because these are essentially unmodified operating systems (currently based on RHEL 9.x), you can patch these systems when necessary by using the standard yum OS update mechanism. Zscaler recommends that you harden the operating system, including the `sshd-config` file, on the VM images in accordance with your organization's security standards after initial deployment. To learn more, see [Update App Connector System Software](/zpa/managing-deployed-connectors#Updating).
Because vulnerabilities are regularly found in core open-source components such as DNS resolvers and the Linux Kernel, Zscaler recommends either patching or using new Zscaler-distributed VM images on a regular basis, or protecting App Connectors using firewall policies. Additionally, if you've installed the App Connector as a package, Zscaler recommends that you take similar precautions.
Some organizations choose to firewall or otherwise restrict outbound traffic to the internet from the data center. It is possible to deploy an App Connector in such an environment as long as the App Connector is able to reach all Zscaler data centers containing ZPA Public Service Edges. For firewall configuration information for your deployment, see [config.zscaler.com/private.zscaler.com/zpa](https://config.zscaler.com/private.zscaler.com/zpa) (for the private.zscaler.com cloud) or [config.zscaler.com/zpatwo.net/zpa](https://config.zscaler.com/zpatwo.net/zpa) (for the zpatwo.net cloud). To learn more, see [What Is My Cloud Name for ZPA?](/zpa/what-my-cloud-name-zpa)
Firewall Requirements and Interoperability Guidelines
All Zscaler data centers containing ZPA Public Service Edges must be allowed. A partial firewall configuration can result in connectivity problems for end users. Zscaler’s policy is to provide a 90-day notice for activating additional IP CIDR ranges to provide organizations with sufficient opportunity for changing control policies.
Because the service enforces TLS certificate pinning for both client and server certificates, all forms of inline or man-in-the-middle TLS interception or inspection must be disabled. App Connectors do not function if the TLS certificates presented by the ZPA Public Service Edges or ZPA Private Service Edges do not cryptographically verify against Zscaler-trusted public keys.
By design, certificate verification is not configurable to maintain the integrity of the service. Ensure that *.prod.zpath.net is in your SSL bypass list for traffic originating from the App Connector. This is necessary for allowing the App Connector to resolve and reach ZPA Public Service Edges or ZPA Private Service Edges. If you need to allowlist additional Zscaler IP addresses, see [config.zscaler.com/private.zscaler.com/zpa](https://config.zscaler.com/private.zscaler.com/zpa) (for the private.zscaler.com cloud) or [config.zscaler.com/zpatwo.net/zpa](https://config.zscaler.com/zpatwo.net/zpa) (for the zpatwo.net cloud). To learn more, see [What Is My Cloud Name for ZPA?](/zpa/what-my-cloud-name-zpa)
For ZPA integration with ZDX, App Connector firewall requirements must align with the respective ZDX configuration. You must configure the firewall to allow egress traffic on the TCP, UDP, and ICMP protocols. App Connectors must be able to egress traffic to port 443 for Zscaler Service Edge connections and the ports of all configured applications (i.e., ports that are configured in all application segments that are registered on the App Connector).
- [Platform-Specific Prerequisites to Deploy an App Connector on OpenShift](#platform-specific-prereqs)
- [Resources and Limits for App Connector Deployment for OpenShift](#resources-and-limits)
[]The following are the platform-specific prerequisites to deploy an App Connector on OpenShift:
- Helm 3
- Openshift 4.11
- Metrics Server
- DNS resolution and network access
- An App Connector [provisioning key](/zpa/about-connector-provisioning-keys) obtained from the ZPA Admin Portal
- Kubeadmin access on default namespace
- Intel x86_64 based architecture
The Docker image is only supported for x86 systems. The Docker image is not supported for arm64 systems. This process assumes you have full network access during the Helm installation to the Docker images hosted on [https://hub.docker.com/u/zscaler](https://hub.docker.com/u/zscaler). To learn more about the different Docker images available, refer to [Docker Hub](https://hub.docker.com/r/zscaler/zpa-connector/tags?page=1&ordering=last_updated).
[]Because vulnerabilities are regularly found in open-source core components such as DNS resolvers and the Linux kernel, Zscaler recommends the following:
- Pointing the Helm Chart to [the latest Docker tag](/zpa/app-connector-deployment-guide-openshift#image-version) and upgrading regularly.
- Protecting App Connectors using firewall policies.
Some organizations choose to firewall or otherwise restrict outbound traffic to the internet from the data center. It is possible to deploy an App Connector in such an environment as long as the App Connector is able to reach all Zscaler data centers containing ZPA Public Service Edges. To learn more, see [firewall configuration information](https://config.zscaler.com/private.zscaler.com/zpa) for your deployment and [App Connector Security Guidance and Firewall Requirements](/zpa/app-connector-deployment-guide-openshift#SecurityAndFirewallReqs).
To set custom resources for your deployments, see [OpenShift Online Life Cycle - Red Hat Customer Portal](https://docs.openshift.com/online/pro/dev_guide/compute_resources.html) and [Resource Management for Pods and Containers](https://kubernetes.io/docs/concepts/configuration/manage-resources-containers/).
- [CPU and Memory](#cpu-and-memory)
- [Horizontal Pod Autoscaler](#horizontal-pod-autoscaler)
- [Limits on File Descriptors](#limits-on-file-descriptors)
[]A minimum of 2 cores and 4 GB RAM is recommended for each pod. CPU and memory are the only resources you can change. You typically only need to make these resource changes if the hosts don’t meet the minimum requirements and the pods fail to run.
The unit "m" is a fractional CPU unit that represents milliCPU in CPU measurement for Horizontal Pod Autoscaling in Kubernetes. A milliCPU is used to express CPU resources in thousandths of a CPU core. For example, 1000m is equivalent to one CPU core. When configuring resource requests and limits for containers in Kubernetes, CPU requests and limits can be specified using the "m" unit. For example, if a container requires 0.5 CPU cores, the CPU request would be 500m. Memory resources are defined in bytes. Normally you use Mi (Mebibyte) or Gi (Gibibyte) units.
The resources and limits are currently set as follows:
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
[Horizontal Pod Autoscaler](https://kubernetes.io/docs/tasks/run-application/horizontal-pod-autoscale/) is supported per deployment based on CPU and memory metrics. The minimum recommended replicas for the App Connector is 2. The average utilization of 80% is used as a threshold for CPU/Memory usage in a Horizontal Pod Autoscaler deployment.
[]
The recommended resource limit (`rlimit`) on open files in the file descriptor for the App Connector application is 512K. OpenShift, by default, has a limit of 1048576. So you can run 2 pods on each node without changes to any settings. To deploy more pods, you need to change the `ulimit` configuration for the number of open files. Refer to the official Red Hat documentation for changing the `ulimit` configuration for number of open files.
[]
`provisionkey:
## @param provisionkey.value The App Connector provision key. Replace this with the user's actual provision key.
value: "1|api.private.zscaler.com|68F0AOEgpcG8McLmwdborq2m6v2A5oNEpSztJ/68F0AOEgpcG8McLmwdborq2m6v2 A5oNEpSztJ/68F0AOEgpcG8McLmwdborq2m6v2A5oNEpSztJ/68F0AOEgpcG8McLmwdborq2m6v2A5oNEpSztJ/68F0 AOEgpcG8McLmwdborq2m6v2A5oNEpSztJ/68F0AOEgpcG8McLmwdborq2m6v2A5oNEpSztJ/68F0AOEgpcG8McLmwdb orq2m6v2A5oNEpSztJ/68F0AOEgpcG8McLmwdborq2m6v2A5oNEpSztJ/68F0AOEgpcG8McLmwdborq2m6v2A5oNEpS ztJ/68F0AOEgpcG8McLmwdborq2m6v2A5oNEpSztJ==" `
[]
You should use a tag with a dated version rather than `latest.amd64` to ensure that the tag is a recent version. For example:
`tag: "2023-08-18.amd64"`
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
You must install the App Connector Helm Chart in order to deploy an App Connector on OpenShift.
- [Get the Helm Chart](#get-helm-chart)
- [Install the Helm Chart](#install-helm-chart)
- [Verify the Helm Chart Installation](#verify-helm-installation)
Only one Helm installation can be done with the default Helm Chart. If you need to install a new Helm Chart, delete or upgrade the current Helm Chart. You can also use the multiple App Connector groups deployment option if you want to deploy new App Connectors with new provisioning keys. To learn more, see [Deployment of Multiple App Connector Groups](/zpa/app-connector-deployment-guide-openshift#multiple-connector-groups).
[]
You can install a Helm Chart by either:
- [Adding the Helm Repository](#adding-helm-repo)
- [Manually Downloading the Helm Chart](#manual-download-helm-chart)
[]
- To add the zpa-app-connector-openshift Helm repository, use the following command:
`helm repo add zpa-helm-repo  https://dist.private.zscaler.com/helm-charts
"zpa-helm-repo" has been added to your repositories`
- To verify the Helm repository, use the following command:
`helm repo list
NAME URL
zpa-helm-repo https://dist.private.zscaler.com/helm-charts`
- To list the available zpa-app-connector-openshift Helm Charts, use the following command:
`helm search repo zpa-helm-repo
NAME CHART VERSION APP VERSION DESCRIPTION
zpa-helm-repo/zpa-app-connector-o... 0.1.0 23.386.1 A helm chart for deploying ZPA App Connector on...`
[]
You can download the source of the Helm Chart from [https://github.com/zscaler/zpa-openshift](https://github.com/zscaler/zpa-openshift).
[]
After you have added the Helm repository or manually downloaded the Helm Chart, you can install the Helm Chart. To install the Helm Chart, do the following:
You can retrieve the provisioning key from the [ZPA Admin Portal](https://admin.private.zscaler.com/). To learn more, see [About App Connector Provisioning Keys](/zpa/about-connector-provisioning-keys).
- Go to the folder containing the Helm package and log in as `kubeadmin`.
- You should be on the default project when you log in as `kubeadmin` unless there was a change in settings. If you are not on the default project, use the following command:
`oc project default`
- From the default namespace, install the Helm Chart by using the following commands:
The domain (e.g., api.private.com) in the echo statement will depend on what ZPA cloud you are on. To learn more, see [What Is My Cloud Name for ZPA?](/zpa/what-my-cloud-name-zpa).
`helm install [NAME] [CHART] [flags]
helm install [NAME] --set zsglobal.provisionkey.value="<provision_key>"  repo_name/chart_name`
Below is an example of successfully installing the Helm Chart:
`helm install zpa-connector --set zsglobal.provisionkey.value="1|api.private.zscaler.com|68F0AOEgpcG8McLmwdborq2m6v2A5oNEpSztJ/68F0AOEgpcG8McLmwdborq2m6v2 A5oNEpSztJ/68F0AOEgpcG8McLmwdborq2m6v2A5oNEpSztJ/68F0AOEgpcG8McLmwdborq2m6v2A5oNEpSztJ/68F0 AOEgpcG8McLmwdborq2m6v2A5oNEpSztJ/68F0AOEgpcG8McLmwdborq2m6v2A5oNEpSztJ/68F0AOEgpcG8McLmwdb orq2m6v2A5oNEpSztJ/68F0AOEgpcG8McLmwdborq2m6v2A5oNEpSztJ/68F0AOEgpcG8McLmwdborq2m6v2A5oNEpS ztJ/68F0AOEgpcG8McLmwdborq2m6v2A5oNEpSztJ==" zpa-helm-repo/zpa-app-connector-openshift
NAME: zpa-connector
LAST DEPLOYED: Wed May 10 16:21:02 2023
NAMESPACE: default
STATUS: deployed
REVISION: 1
TEST SUITE: None
NOTES:
Thank you for installing zpa-app-connector-openshift.
To learn more about the release, try:
$ helm status zpa-connector
$ helm get all zpa-connector`
If you downloaded the Helm chart from the GitHub repository ([https://github.com/zscaler/zpa-openshift](https://github.com/zscaler/zpa-openshift)), you'll need to provide the path to the folder containing Chart.yaml. For example:
`helm install zpa-connector --set zsglobal.provisionkey.value="1|api.private.zscaler.com|68F0AOEgpcG8McLmwdborq2m6v2A5oNEpSztJ/68F0AOEgpcG8McLmwdborq2m6v2 A5oNEpSztJ/68F0AOEgpcG8McLmwdborq2m6v2A5oNEpSztJ/68F0AOEgpcG8McLmwdborq2m6v2A5oNEpSztJ/68F0 AOEgpcG8McLmwdborq2m6v2A5oNEpSztJ/68F0AOEgpcG8McLmwdborq2m6v2A5oNEpSztJ/68F0AOEgpcG8McLmwdb orq2m6v2A5oNEpSztJ/68F0AOEgpcG8McLmwdborq2m6v2A5oNEpSztJ/68F0AOEgpcG8McLmwdborq2m6v2A5oNEpS ztJ/68F0AOEgpcG8McLmwdborq2m6v2A5oNEpSztJ==" zpa-app-connector-openshift/`
[]
To verify the Helm Chart installation, use the following command:
`helm list
NAME         NAMESPACE REVISION UPDATED                             STATUS  CHART                            APP VERSION
zpa-connector default  1       2023-09-19 14:15:25.681803 -0700 PDT deployed zpa-app-connector-openshift-23.386.1 2023-08-18.amd64`
To verify if the pods are running, use the following command:
`zscaler-zpa `is the namespace that is added when this Helm Chart is installed.
`oc get pods -n zscaler-zpa
NAME                                                        READY   STATUS        RESTARTS   AGE
zpa-connector-zpa-app-connector-openshift-f6f865fb8-qg2nx   1/1     Running       0          64s
zpa-connector-zpa-app-connector-openshift-f6f865fb8-spjtx   1/1     Running       0          19s`
[]
To verify the App Connector deployment, you can do the following:
- Verify that the deployed App Connector is [running and healthy](/zpa/managing-deployed-connectors#Status).
- Check that the deployment is [meeting your sizing requirements](/zpa/managing-deployed-connectors#VerifySizing).
[]
- [After App Connectors are Deployed](#after-app-connectors-are-deployed)
- [Update App Connector Manager Software](#update-zpa-connector-software)
- [View App Connector Logs](#view-app-connector-logs)
- [Configure Auto Deletion of Disconnected App Connectors](#config-auto-deletion)
- [Helm Customization](#helm-customization)
- [Node Affinity](#node-affinity)
- [Deployment of Multiple App Connector Groups](#multiple-connector-groups)
- [OpenShift App Connector Linux Capabilities](#linux-capabilities)
[]
After App Connectors are deployed, you can do the following:
- [Create application segments](/zpa/about-application/onboard) and [access policy rules](/zpa/about-policies) to pass application traffic through.
- [Configure a log receiver](/zpa/configuring-log-receiver) for your App Connectors to receive information about the App Connectors or users via the [Log Streaming Service (LSS)](/zpa/about-log-streaming-service).
[]
To update the App Connector Manager Software, do the following:
- Update the image version in the Helm Chart to [the corresponding Docker tag](/zpa/app-connector-deployment-guide-openshift#image-version).
- [Upgrade the Helm Chart](/zpa/app-connector-deployment-guide-openshift#helm-upgrade).
[]
To view App Connector logs, run the following command: `oc logs -f <Pod Name> -n zscaler-zpa`. For example:
`oc logs -f zpa-app-connector-openshift-f6f865fb8-78rlg -n zscaler-zpa`
[]
The threshold for App Connectors using the provisioning keys in an App Connector group is 100. The pods are ephemeral and consume a provisioning key utilization count each time they run. To avoid exceeding the App Connector threshold, Zscaler recommends configuring Auto Delete in your App Connector settings to remove App Connectors with a disconnected status after a set number of days. To learn more, see [Configuring App Connectors Page Settings](/zpa/configuring-app-connectors-settings).
[]
- [Change Helm Values During Initial Installation](#helm-change-values)
- [Helm Upgrade](#helm-upgrade)
- [Helm List](#helm-list)
- [Helm Rollback](#helm-rollback)
- [Helm Delete](#helm-delete)
[]To change Helm values during the initial installation:
These Helm Chart values only need to be changed if you need to customize the Helm Chart. The domain (e.g., api.private.com) in the echo statement will depend on what ZPA cloud you are on. To learn more, see [What Is My Cloud Name for ZPA?](/zpa/what-my-cloud-name-zpa).
- Open `values.yaml`.
- You can change the following values:
- [Provision Key](#provision-key)
- [Image Version](#image-version)
- [Resources and Limits](#resources-limits)
- Use the Helm install command when you change any values:
`helm install <release-name> zpa-app-connector-openshift/ -f zpa-app-connector-openshift/values.yaml`
[]
To upgrade the Helm repository zpa-app-connector-openshift, use the following command:
`helm upgrade <release-name> zpa-app-connector-openshift/ -f zpa-app-connector-openshift/values.yaml``helm upgrade zpa-connector zpa-app-connector-openshift/ -f zpa-app-connector-openshift/values.yaml
Release "zpa-connector" has been upgraded. Happy Helming!
NAME: zpa-connector
LAST DEPLOYED: Thu Sep 14 22:51:10 2023
NAMESPACE: default
STATUS: deployed
REVISION: 2
NOTES:
Thank you for installing zpa-app-connector-openshift.
To learn more about the release, try:
$ helm status zpa-connector
$ helm get all zpa-connector`
[]
To list the Helm releases associated with zpa-app-connector-openshift, use the following command:
`helm list
NAME         NAMESPACE REVISION UPDATED                             STATUS  CHART                            APP VERSION
zpa-connector default  1       2023-09-19 14:15:25.681803 -0700 PDT deployed zpa-app-connector-openshift-23.386.1 2023-08-18.amd64 `
[]
To roll back the Helm deployment, use the following command:
This is not applicable to the first version.
` helm rollback <release-name>`
[]
To delete the Helm deployment, use the following command:
` helm delete <release-name>`
[]
Zscaler does not explicitly add node affinity for the App Connector Helm Chart. To define nodes to be chosen for the App Connector pods to be scheduled on, do the following:
- Use the following commands to label the nodes:
`oc get nodes -A
oc label nodes <Node-name> type=zpa-app-connector`
- Use the following commands to add the namespace based on your nodes and match it with the label you added:
`kind: Namespace
metadata:
name: {{ .Values.zsglobal.namespace }}
+  annotations:
+    openshift.io/node-selector: "type=zpa-app-connector"`
With node affinity configured, the pods are only scheduled on the chosen nodes. To learn more, refer to the [OpenShift documentation](https://docs.openshift.com/container-platform/4.11/nodes/scheduling/nodes-scheduler-node-selectors.html).
[]
To support deployment of multiple App Connector groups, do the following:
- Make the following changes to `values.yaml`:
Provide a meaningful identifier to identify the new provision key under `secretIdentifier`, for example, an identifier matching the one in the ZPA Admin Portal. The domain (e.g., api.private.com) in the echo statement will depend on what ZPA cloud you are on. To learn more, see [What Is My Cloud Name for ZPA?](/zpa/what-my-cloud-name-zpa).
`## @param zsglobal.multiConnector [object] Configuration for multiple connectors
multiConnector:
## @param zsglobal.multiConnector.disable Deploy multiple connectors
enabled: true
## @param zsglobal.multiConnector.secretIdentifier App Connector Secret Identifier for storing provision key
secretIdentifier: app-connector-multi-demo-secret
Give the new provision key under
provisionkey:
## @param provisionkey.value The app-connector provision Key. Replace this with the user's actual provision key.
value: "1|api.private.zscaler.com|68F0AOEgpcG8McLmwdborq2m6v2A5oNEpSztJ/68F0AOEgpcG8McLmwdborq2m6v2 A5oNEpSztJ/68F0AOEgpcG8McLmwdborq2m6v2A5oNEpSztJ/68F0AOEgpcG8McLmwdborq2m6v2A5oNEpSztJ/68F0 AOEgpcG8McLmwdborq2m6v2A5oNEpSztJ/68F0AOEgpcG8McLmwdborq2m6v2A5oNEpSztJ/68F0AOEgpcG8McLmwdb orq2m6v2A5oNEpSztJ/68F0AOEgpcG8McLmwdborq2m6v2A5oNEpSztJ/68F0AOEgpcG8McLmwdborq2m6v2A5oNEpS ztJ/68F0AOEgpcG8McLmwdborq2m6v2A5oNEpSztJ=="`
- Run the `helm install <release-name>` command.
Use a name for the release that does not conflict with release names for other App Connector deployments. The same namespace will be used for all App Connectors when deployed using this method. [Horizontal Pod Autoscaling](/zpa/app-connector-deployment-guide-openshift#horizontal-pod-autoscaler) occurs in each App Connector group per deployment.
- Run the `helm install app-connector-multi-demo` command.
[]
OpenShift App Connector Linux Capabilities
The following table provides a list of OpenShift App Connector Linux capabilities that the container uses:
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
| `CAP_SETFCAP` | Set arbitrary capabilities on a file. | Set file capabilities. |
| `CAP_SYS_NICE` | Performs the following network-related operations:Lowers the processed nice value (i.e., nice(2) and setpriority(2)) and changes the nice value for arbitrary processes.Sets scheduling policies in real-time for the calling process and sets scheduling policies and priorities for arbitrary processes (i.e., sched_setscheduler(2), sched_setparam(2), and sched_attr(2)).Sets CPU affinity for arbitrary processes (i.e., sched_setaffinity(2)).Sets the input or output (I/O) scheduling class and priority for arbitrary processes (i.e., ioprio_set(2)).Applies migrate_pages(2) to arbitrary processes and allows the processes to migrate to arbitrary nodes.Applies move_pages(2) to arbitrary processes.Uses the MPOL_MF_MOVE_ALL flag with mbind(2) and move_pages(2). | ZPA forks new processes and assigns the CPU affinity. |
| `CAP_SYS_TIME` | Sets the system clock (i.e., settimeofday(2), time(2), adjtimex(2)) and the real-time (hardware) clock. | N/A |
| `CAP_SYS_RESOURCE` | Increases resource limits. | Increases resource limits for `SYS_RESOURCE`. |