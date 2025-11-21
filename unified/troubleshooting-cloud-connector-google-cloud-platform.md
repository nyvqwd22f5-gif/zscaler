# Troubleshooting Cloud Connector with Google Cloud Platform
Source: https://help.zscaler.com/unified/troubleshooting-cloud-connector-google-cloud-platform
PDF: https://help.zscaler.com/pdf/com/en/1516381.pdf

This article provides troubleshooting information and guidelines about [Cloud Connector deployment in Google Cloud Platform (GCP)](/unified/deploying-zscaler-cloud-connector-google-cloud-platform). You can learn about different issues, potential causes, and corresponding solutions for the deployed Zscaler Cloud Connector.
- [Deployed Cloud Connector is not displayed in the Admin Portal](#deployedcloudconnector)
- [Unable to log in to the Admin Portal](#login)
- [Workloads unable to access internet applications](#internetapplications)
- [Workloads unable to access private applications](#privateapplications)
- [Unable to monitor the traffic in the ZIA Admin Portal](#ZIAportal)
- [Unable to monitor the traffic in the ZPA Admin Portal](#ZPAportal)
- [Traffic not restored on Cloud Connector failure](#TrafficRestore)
- [Cloud Connector experiencing connectivity disruptions](#ConnectivityDisruptions)
[]The following tables list provisioning and deployment issues and their corresponding troubleshooting actions.
Provisioning Issues
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
| Potential Causes | Troubleshooting Actions |
| ---------------- | ----------------------- |
| Deployed Cloud Connector is not displayed in the Admin Portal. | Check whether user data is missing or is provided in an incorrect format.You can verify user data by reviewing the GCP Secret Manager, or by reviewing the User Data file located on the appliance here: /etc/cloud/cloud.cfg.d/userdata.cfgVerify the API Key (api-key).Verify login credentials (username, password).Verify that the provisioning URL is in the correct format and there are no spaces.From the Admin Portal, verify that the Provisioning Template type is correct.Check whether the Cloud Connector has sufficient privileges to the GCP Secret Manager. Ensure that the GCP Secret Manager API is enabled and that the Cloud Connector can access it. Also, ensure that the service account that the Cloud Connector is using has the **Secret Manager Secret Accessor** role assigned to it.Verify the firewall rules to ensure that Cloud Connectors can reach the Zscaler Cloud.Verify that Cloud Connector can reach the package repository when using certificate authority.Verify that you can do a package update to confirm that the package repository is reachable and certificates are valid. Run the `sudo pkg update` command.Verify DNS resolution. |
| Terraform script fails to create a virtual private cloud (VPC) in a greenfield deployment. | Check whether the user has surpassed the VPC creation limit. Also, verify that the service principal that Terraform is using has permissions to create new VPCs. |
|  |
Deployment Issues
-
-
-
-
-
-
-
-
| Potential Causes | Troubleshooting Actions |
| ---------------- | ----------------------- |
| Cloud Connector is in the wrong geolocation in the Admin Portal. | Verify the following:The outbound NAT and routing take the appropriate egress path. In the Admin Portal, confirm the Public IP address.If the Public IP address is correct, contact Zscaler Support. |
| Cloud Connector is in an inactive state. | Verify the following:Verify registration and policy fetch by running the `sudo januscli status` command.The Cloud Connector instance is up and running within the GCP Management Console.The Admin Portal can be reached from the Cloud Connector VPC/subnet.GCP Secret Manager has the correct secret credentials in case of a secrets rotation.The network is connected. Verify the route tables, Cloud NAT, and DNS.The firewall rule is not blocking the Cloud Connector TCP/UDP 443 traffic. |
| In the Admin Portal, the Zscaler Internet Access (ZIA) gateway IP address is not populated. | From the Admin Portal, check the ZIA gateway configuration. If the gateway configuration is not set correctly, contact Zscaler Support. |
[]
| Potential Causes | Troubleshooting Action |
| ---------------- | ---------------------- |
| Account not created. | Contact Zscaler Support. |
| Cloud Connector SKUs not enabled. | Contact Zscaler Support. |
| Authentication failed. | Verify that the username and all credentials are valid. In the Admin Portal, confirm that the admin exists. |
| User could not access single sign-on (SSO) from the Admin Portal. | Contact Zscaler Support. |
[]The traffic from the deployed Cloud Connector might not be able to reach internet applications.
Check the following areas to isolate and identify what is preventing the traffic connection:
- [](/unified/about-zscaler-internet-access-gateways)
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
| **Potential Causes** | **Troubleshooting Action** |
| -------------------- | -------------------------- |
| The firewall policy attached to the Cloud Connector. | Verify that the ZIA firewall policy is not blocking any outbound traffic. |
| The connectivity from the Cloud Connector to ZIA. | Verify the following:In the Admin Portal, the ZIA Gateway is populatedSession logs display the Cloud Connector self-traffic.In the Admin Portal, your tunnel insights are displayed. |
| The ingress routing to the Cloud Connector. | Verify the following:The routing of the workloads. Depending on the architecture chosen, review Network Tags to ensure that workloads are using the correct Default Route.The firewall rule on the workload. |
| The egress path from the Cloud Connector. | Verify the following:The gateway configuration.The forwarding policy in the Admin Portal.The firewall rules and other services on egress.The routing of the Cloud Connector. Depending on the architecture chosen, review Network Tags to ensure that the Cloud Connectors are using the correct Default Route. |
| The status of the Cloud Connector. | Verify the following:The VM status of the Cloud Connector.The service status of the Cloud Connector. |
| Connectivity issues between Cloud Connectors within a group or cluster. | Verify the following:All Cloud Connectors communicate with each other within a given connector group or cluster via their service interface(s) to share information such as fully qualified domain name (FQDN)/wildcard FQDN synchronization.No firewall or security groups are blocking network communications between Cloud Connectors within a given VPC/VNet and their availability zones. |
[]If your workloads are unable to access private applications, verify the following:
- The parameters in the Terraform template that pertain to the Zscaler Private Access (ZPA) endpoints are accurate (specifically, the GCP Cloud DNS forwarding rules).
- The application name matches the GCP Cloud DNS forwarding configuration.
- The application is available from the ZPA Admin Portal.
- If FQDN-based ZPA App Segments are in use, verify that DNS is passing through the Cloud Connector.
[]If you are unable to monitor traffic in the ZIA Admin Portal, verify the following:
- The Cloud Connector location created in the ZIA Admin Portal is registered in the ZIA Admin Portal.
- The tunnel logs in the ZIA Admin Portal are showing traffic to ZIA.
- When filtering traffic in the Admin Portal, you use the ZIA filter.
- In the Admin Portal traffic forwarding rules drop-down menu, the [traffic forwarding method is ZIA](/unified/configuring-traffic-forwarding-rules).
[]If you are unable to monitor traffic in the ZPA Admin Portal, verify the following:
- The Cloud Connector is registered in the ZPA Admin Portal.
- In the Admin Portal, the forwarding filter is ZPA.
- In the ZPA Admin Portal, policy is configured correctly. Ensure that access policies and client forwarding policies are working.
[]If your traffic is not restored after Cloud Connector's connection failure, verify the following:
- The Cloud Connector backup instance is in good health with the high-availability model.
- In the Load Balancing console of GCP, the Cloud Connector instance is healthy.
[]
To avoid connectivity disruptions and/or unreachable destinations, IP forwarding must be enabled on the Cloud Connector service interface. The IP Forwarding setting is enabled by default on the service NIC of the Cloud Connector with the Zscaler Terraform deployment script. You can verify the setting from the GCP console. If the setting has been disabled, refer to the [GCP documentation](https://cloud.google.com/compute/docs/instances/update-instance-properties#updatable-properties) to re-enable the setting.