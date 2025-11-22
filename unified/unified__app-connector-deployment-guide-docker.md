# App Connector Deployment Guide for Docker
Source: https://help.zscaler.com/unified/app-connector-deployment-guide-docker
PDF: https://help.zscaler.com/pdf/com/en/1496141.pdf

The App Connector Docker image is available on Docker Hub for both the arm64 and amd64 platforms:
- `docker pull zscaler/zpa-connector:latest.amd64`
- `docker pull zscaler/zpa-connector:latest.arm64`
To learn more about the different repositories available, see [Docker Hub](https://hub.docker.com/r/zscaler/zpa-connector/tags?page=1&ordering=last_updated).
Docker support is not available for Kubernetes. To learn more about support for CentOS 7.x, see [End-of-Support for CentOS 7.x, RHEL 7.x, and Oracle Linux 7.x](/eos-eol/end-support-centos-7.x-rhel-7.x-and-oracle-linux-7.x).
Prerequisites
An environment variable named `ZPA_PROVISION_KEY` is required to run this image. You can retrieve the provisioning key from the [Admin Portal](https://admin.private.zscaler.com/). To learn more, see [About App Connector Provisioning Keys](/unified/about-app-connector-provisioning-keys).
Only one container per host is allowed. The container is deployed in a Docker Community Edition (CE) environment and is not an orchestration tool like Docker Swarm or Kubernetes.
[]Deploying a Docker Image on x86-64 Systems
A minimum of 2 cores and 4 GB RAM is required for x86-64 systems.
To deploy the Docker image, create a new container using the `run` command and provisioning key.
Docker provides a random name for the container if you don’t include the “`--name`” option when you run the following command. If you want, you can replace “`zpa-connector`” with a different container name.
For example:
The domain (e.g., api.private.com) in the echo statement will depend on what cloud you are on.
sudo docker run -d --init\
--name zpa-connector \
--cap-add cap_net_admin \
--cap-add cap_net_bind_service \
--cap-add cap_net_raw \
--cap-add cap_sys_nice \
--cap-add cap_sys_time \
--cap-add cap_sys_resource \
--restart always \
-e ZPA_PROVISION_KEY="3|api.private.zscaler.com|..." \
zscaler/zpa-connector:latest.amd64
To deploy the Docker image, create a new container using the `run` command and provisioning key.
Deploying a Docker Image on an Arm Platform
A minimum of 2 cores and 4 GB RAM is required for arm64 systems.
To deploy the Docker image on ARM64 architecture, create a new container using the run command and provisioning key.
Docker provides a random name for the container if you don’t include the “`--name`” option when you run the following command. If you want, you can replace “`zpa-connector`” with a different container name.
For example:
The domain (e.g., api.private.com) in the echo statement will depend on what cloud you are on.
sudo docker run -d --init\
--name zpa-connector \
--cap-add cap_net_admin \
--cap-add cap_net_bind_service \
--cap-add cap_net_raw \
--cap-add cap_sys_nice \
--cap-add cap_sys_time \
--cap-add cap_sys_resource \
--restart always \
-e ZPA_PROVISION_KEY="2|api.private.zscaler.com|..." \
zscaler/zpa-connector:latest.arm64
To deploy the Docker container, ensure `--init` is included in the `run` command.
Linux Capabilities
The following table provides a list of Linux capabilities that the container uses:
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
| `CAP_NET_ADMIN` | Performs the following network-related operations:Interfaces configuration.Administration of the IP firewall, masquerading, and accounting.Modifies the routing tables.Binds to any address for transparent proxying.Sets the type-of-service (TOS).Clears the driver statistics.Sets in promiscuous mode.Enables multicasting. | Fundamental to Private Applications networking. |
| `CAP_NET_BIND_SERVICE` | Binds a socket to the Internet domain privileged ports (port numbers less than 1024). | This capability is required to bind to a port below 1024. If you are running a service that listens to a port above 1024, remove this capability. |
| `CAP_NET_RAW` | Binds to any address for transparent proxying and uses RAW and PACKET sockets. | Fundamental to Private Applications networking. |
| `CAP_SYS_BOOT*` | Reboots or loads a new kernel for future execution. | This capability is optional and can be turned off in the container. |
| `CAP_SYS_NICE` | Performs the following network-related operations:Lowers the processed nice value (i.e., `nice(2)` and `setpriority(2)`) and changes the nice value for arbitrary processes.Sets scheduling policies in real-time for the calling process and sets scheduling policies and priorities for arbitrary processes (i.e., `sched_setscheduler(2)`, `sched_setparam(2)`, and `sched_attr(2)`).Sets CPU affinity for arbitrary processes (i.e., `sched_setaffinity(2)`).Sets the input or output (I/O) scheduling class and priority for arbitrary processes (i.e., `ioprio_set(2)`).Applies `migrate_pages(2)` to arbitrary processes and allows the processes to migrate to arbitrary nodes.Applies `move_pages(2)` to arbitrary processes.Uses the `MPOL_MF_MOVE_ALL` flag with `mbind(2)` and `move_pages(2)`. | Private Applications forks new processes and assigns the CPU affinity. |
| `CAP_SYS_TIME` | Sets the system clock (i.e., `settimeofday(2)`, `time(2)`, `adjtimex(2)`) and the real-time (hardware) clock. | N/A |
| `CAP_SYS_RESOURCE` | Increases resource limits. | Increases resource limits for `SYS_RESOURCE`. |