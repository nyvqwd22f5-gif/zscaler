# Deployment Templates for Zscaler Cloud Connector
Source: https://help.zscaler.com/unified/deployment-templates-zscaler-cloud-connector
PDF: https://help.zscaler.com/pdf/com/en/1517511.pdf

Infrastructure as Code (IaC) deployment templates are available in [GitHub](https://github.com/zscaler) to assist in the deployment of Zscaler Cloud Connector in Amazon Web Services (AWS), Microsoft Azure, and Google Cloud Platform (GCP). AWS deployment templates are available in CloudFormation and Terraform repositories. Azure and GCP deployment templates are available in Terraform repositories. Links to the repositories are included in this article and in the Admin Portal (Infrastructure > Connectors > Cloud > Deployment Templates).
AWS Deployment Templates
When you deploy Cloud Connector with AWS, Instance Metadata Service Version 2 (IMDSv2) is enforced by default. To learn more about IMDSv2, refer to the [AWS documentation](https://docs.aws.amazon.com/AWSEC2/latest/UserGuide/configuring-instance-metadata-service.html).
AWS CloudFormation Templates
Before deploying your Cloud Connectors using CloudFormation, you must upload the Pre-Deployment Template to the AWS CloudFormation console and deploy the Pre-Deployment Template stack. If there is an existing Pre-Deployment Template stack that is out of date, you must update and replace the existing template. To learn more about updating an AWS CloudFormation stack, refer to the [AWS documentation](https://docs.aws.amazon.com/AWSCloudFormation/latest/UserGuide/using-cfn-updating-stacks-direct.html).
Use the templates in the [CloudFormation](https://github.com/zscaler/cloud-native-aws-cloud-connector-deploy) repository to create the deployment resources you need to deploy and operate Cloud Connector in an existing virtual private cloud (VPC). To learn more about the steps for deploying Cloud Connector using a CloudFormation template, see [Deploying Cloud Connector with Amazon Web Services](/unified/deploying-zscaler-cloud-connector-amazon-web-services).
The following table lists the templates you need for standard and advanced deployments.
-
-
-
-
-
-
-
| Standard Deployment (No Auto Scaling) | Advanced Deployment (Auto Scaling) |
| ------------------------------------- | ---------------------------------- |
| Pre-Deployment TemplateStarter Deployment TemplateAdd-on Template with Gateway Load Balancer (GWLB) (optional)Add-on Template with ZPA (optional) | Pre-Deployment TemplateStarter Deployment Template with Auto Scaling and Gateway Load Balancer (GWLB)Add-on Template with ZPA (optional) |
- [Pre-Deployment Template](#pre-deployment)
- [Starter Deployment Template](#cf-default-deployment-template)
- [Add-on Template with Gateway Load Balancer (GWLB)](#CF-GWLB)
- [Add-on Template with ZPA](#cf-default-route53)
- [Starter Deployment Template with Auto Scaling and GWLB](#cf-default-deployment-template-autoscaling)
AWS Terraform Templates
Use the templates in the [Terraform](https://github.com/zscaler/terraform-aws-cloud-connector-modules) repository to create the deployment resources required to deploy and operate Cloud Connector in a new or existing VPC.
- [Basic Deployment Templates](#t-templates)
- [Deployment Templates with Gateway Load Balancer (GWLB)](#t-templates-gwlb)
- [Deployment Templates with Auto Scaling](#t-templates-as)
[]
- [Starter Deployment Template](#t-default-deployment-template)
- [Starter Deployment Template with ZPA](#t-default-route53)
[]
- [Starter Deployment Template with GWLB](#t-gwlb)
- [Starter Deployment Template with GWLB and ZPA](#t-gwlb-zpa)
- [Custom Deployment Template with GWLB](#t-custom-gwlb)
[]
- [Starter Deployment Template with Auto Scaling and GWLB](#t-gwlb-autoscaling)
- [Starter Deployment Template with Auto Scaling, GWLB, and ZPA](#t-gwlb-autoscaling-zpa)
- [Custom Deployment Template with Auto Scaling and GWLB](#t-custom-gwlb-autoscaling)
[]
Use the Pre-Deployment Template (zs_cc_cf_template_zscc_macro) to create the pre-deployment resources you need to deploy and operate Cloud Connector in an existing VPC. This template creates the following resources:
- AWS CloudFormation macro
- AWS Lambda function
- Identity and Access Management (IAM) role to access the AWS Secrets Manager
- Permissions for invoking Lambda
- [See Resource Logs](#predeployment-resourcelogs)
[]
`AWS::CloudFormation::Macro
AWS::IAM::Role
AWS::Lambda::Function
AWS::Lambda::Permission`
[]Use the Starter Deployment Template (zs_cc_cf_template_simple) to create the resources you need to deploy and operate Cloud Connector in an existing VPC. The template creates the following resources:
- Instance Profile with IAM role and required policy permissions (Secrets Manager, Systems Manager [SSM], Workload Tags)
- AWS Lambda function
- EC2 instance
- Security group for Management interface
- Security group for Service Interface
- Service Network Interface
- Network Interface Attachment
After you upload the template to the AWS CloudFormation console, you must define the following parameters:
- VPC ID
- Availability zone of the subnets
- Subnet ID of Cloud Connector
- Cloud Connector instance key pair
- Cloud Connector instance type (small, medium, or large)
- Cloud Connector VM AWS EC2 instance type
- Cloud Connector provisioning URL
- Secrets Manager secret name (optional)
- EBS encryption enablement
- HTTP monitor probe port (optional)
Ensure that you define the HTTP Monitor Probe Port parameter to check the liveliness of the designated Cloud Connectors and to achieve high availability.
- [See Resource Logs](#cf-starter-output)
[]
`AWS::EC2::KeyPair::KeyName
AWS::EC2::VPC::Id
AWS::EC2::Subnet::Id
AWS::EC2::SecurityGroup
AWS::EC2::NetworkInterface
AWS::IAM::ManagedPolicy
AWS::IAM::Role
AWS::IAM::InstanceProfile
AWS::EC2::LaunchTemplate
AWS::EC2::Instance
AWS::EC2::NetworkInterfaceAttachment`
[]
Use the Add-on Template with ZPA (zs_cc_cf_template_zpa_r53) to create the resources you need to enable the Zscaler Private Access (ZPA) DNS resolver capability on the Cloud Connector in an existing VPC. The template creates the following resources:
- Outbound Route 53 resolver
- Security group
- IAM role to access the AWS Secrets Manager
- AWS Lambda function to retrieve the EC2 instance properties
- Up to 10 Resolver rules, one per domain
After you upload the template to the AWS CloudFormation console, you must define the following parameters:
- Your Zscaler Cloud name
- Your ZPA Cloud name
- VPC ID
- Outbound Resolver endpoints subnets
- Resolver target IPs
- Domain name(s) for ZPA application(s)
- [See Resource Logs](#cf-zpa-output)
[]
`AWS::CloudFormation::CustomResource
AWS::EC2::SecurityGroup
AWS::IAM::Role
AWS::Lambda::Function
AWS::Route53Resolver::ResolverEndpoint
AWS::Route53Resolver::ResolverRule
AWS::Route53Resolver::ResolverRule
AWS::Route53Resolver::ResolverRule
AWS::Route53Resolver::ResolverRule
AWS::Route53Resolver::ResolverRule
AWS::Route53Resolver::ResolverRule
AWS::Route53Resolver::ResolverRule
AWS::Route53Resolver::ResolverRuleAssociation  `
[]
Use the Add-on Template with GWLB (zs_cc_cf_template_gwlb) to load balance traffic across multiple Cloud Connectors. The template creates the following resources:
- Gateway Load Balancer
- Listener
- Target group
- VPC endpoint service
- VPC endpoints
After you upload the template to the AWS CloudFormation console, you must define the following parameters:
- ZS CC instance IDs
- ZS CC instance HTTP probe port
Ensure that you define the HTTP Monitor Probe Port parameter to check the liveliness of the designated Cloud Connectors and to achieve high availability.
- GWLB target failover rebalance strategy
- GWLB flow stickiness strategy
- Enable cross-zone load balancing
With cross-zone load balancing, the Gateway Load Balancer distributes requests evenly across the Cloud Connector instances in all enabled Availability Zones. If you disable cross-zone load balancing, the Gateway Load Balancer distributes requests evenly across the Cloud Connector instances in the workload's Availability Zone only. Traffic forwarding across Availability Zones is subject to additional AWS charges.
- [See Resource Logs](#cf-gwlb-output)
[]
`AWS::ElasticLoadBalancingV2::LoadBalancer
AWS::ElasticLoadBalancingV2::Listener
AWS::ElasticLoadBalancingV2::TargetGroup
AWS::EC2::VPCEndpointService
AWS::EC2::VPCEndpoint
AWS::EC2::VPCEndpoint`
Before uploading this template to the AWS CloudFormation console, you must create a new Amazon Simple Storage Service (S3) bucket and upload the[ Zscaler Cloud Connector Lambda ZIP file](https://github.com/zscaler/terraform-aws-cloud-connector-modules/blob/main/modules/terraform-zscc-asg-lambda-aws/zscaler_cc_lambda_service.zip). To learn more about Amazon S3, see [Amazon S3 bucket for auto scaling prerequisites](/unified/deploying-zscaler-cloud-connector-amazon-web-services#S3).
[]Use the Starter Deployment Template with Auto Scaling and GWLB (zs_cc_cf_template_asg_gwlb) to create the resources you need to deploy and operate Cloud Connector with Auto Scaling in an existing VPC.
To enable Auto Scaling, contact Zscaler Support.
The template creates the following resources:
- Launch template
- Auto Scaling group
- Instance profile with IAM role and required policy permissions (Secrets Manager, Systems Manager [SSM], Workload Tags)
- EC2 Instance
- Management network interface
- Service network interface
- Security group for management interface
- Security group for service interface
- Network interface attachment
- Lambda function
- Log group
- EventBridge rules
- Gateway Load Balancer
- Listener
- Target group
- VPC endpoint service
- VPC endpoints
After you upload the template to the AWS CloudFormation console, you must define the following parameters:
- VPC ID
- Availability Zone to deploy Zscaler Cloud Connector and GWLB/VPC endpoints
- Subnet ID for the Zscaler Cloud Connector Auto Scaling Group
- (Optional) Zscaler Cloud Connector AMI
- Zscaler Cloud Connector instance key pair
- (Optional) Existing IAM role to use for Zscaler Cloud Connector
- (Optional) Zscaler Cloud Connector management interface security group
- (Optional) Zscaler Cloud Connector service interface security group
- AWS Secrets Manager secret name
- Zscaler Cloud Connector instance size
Currently, only **small** instance types are supported for Cloud Connector.
- Cloud Connector VM AWS EC2 instance type
- Cloud Connector provisioning URL
- HTTP monitor probe port
Ensure that you define the HTTP monitor probe port parameter to check the liveliness of the designated Cloud Connectors and to achieve high availability.
- EBS encryption enablement
- Lambda S3 bucket name
- Lambda S3 key
- Auto Scaling group minimum size
- Auto Scaling group maximum size
- Auto Scaling group reuse instances on scale-in
- Auto Scaling group target CPU utilization value
- Auto Scaling group warm pool enabled
- Auto Scaling group warm pool state
- Auto Scaling group warm pool minimum size
- Auto Scaling group warm pool max group prepared capacity
- Log group retention
- GWLB target failover rebalance strategy
- GWLB flow stickiness strategy
- Enable cross-zone load balancing
- VPC endpoint subnets to create VPC endpoints in (one per Availability Zone)
- VPC endpoint service principals
- Require acceptance for newly created VPC endpoints
- [See Resource Logs](#cf-starter-output-autoscaling)
[]
`AWS::EC2::VPC::Id
AWS::EC2::KeyPair::KeyName
AWS::EC2::Image::Id
AWS::EC2::SecurityGroup
AWS::IAM::ManagedPolicy
AWS::IAM::Role
AWS::IAM::InstanceProfile
AWS::EC2::LaunchTemplate
AWS::AutoScaling::AutoScalingGroup
AWS::AutoScaling::ScalingPolicy
AWS::AutoScaling::WarmPool
AWS::Logs::LogGroup
AWS::Lambda::Function
AWS::Events::Rule
AWS::Lambda::Permission
AWS::ElasticLoadBalancingV2::LoadBalancer
AWS::ElasticLoadBalancingV2::TargetGroup
AWS::ElasticLoadBalancingV2::Listener
AWS::EC2::VPCEndpointService
AWS::EC2::VPCEndpointServicePermissions
AWS::EC2::VPCEndpoint`
[]
Use the Starter Deployment Template (base_1cc) to deploy your Cloud Connector in a new VPC. The template creates the following resources:
- VPC
- Cloud Connector subnet
- Public subnet
- Private subnet
- Key pair for SSH access
- Instance profile with IAM role and required policy permissions (Secrets Manager, SSM, Workload Tags)
- Elastic IP address associated with NAT gateway
- Cloud Connector VM
- AWS Lambda function to retrieve the EC2 instance properties
- Linux bastion host
- Linux workload server
- Internet gateway
- NAT gateway
- Management interface
- Service interface
- Network security group for management interface
- Network security group for service interface
- Route tables for routing the workload traffic through the Cloud Connector
- [See Resource Logs](#tf-starter-output)
[]
`data.aws_ami.cloudconnector
aws_key_pair.deployer
local_file.private_key
local_file.testbed
local_file.user_data_file
random_string.suffix
tls_private_key.key
module.bastion.data.aws_iam_policy_document.bastion_instance_assume_role_policy
module.bastion.data.aws_partition.bastion_current_partition
module.bastion.data.aws_ssm_parameter.amazon_linux_latest
module.bastion.data.aws_vpc.selected
module.bastion.aws_iam_instance_profile.bastion_host_profile
module.bastion.aws_iam_role.bastion_iam_role
module.bastion.aws_iam_role_policy_attachment.ssm_managed_instance_core
module.bastion.aws_instance.bastion
module.bastion.aws_security_group.bastion
module.bastion.aws_security_group_rule.internet
module.bastion.aws_security_group_rule.intranet
module.bastion.aws_security_group_rule.ssh
module.cc_iam.data.aws_iam_policy_document.instance_assume_role_policy
module.cc_iam.data.aws_secretsmanager_secret.cc_secret_name
module.cc_iam.aws_iam_instance_profile.cc_host_profile[0]
module.cc_iam.aws_iam_policy.cc_get_secrets_policy[0]
module.cc_iam.aws_iam_policy.cc_metrics_policy[0]
module.cc_iam.aws_iam_policy.cc_session_manager_policy[0]
module.cc_iam.aws_iam_role.cc_node_iam_role[0]
module.cc_iam.aws_iam_role_policy_attachment.cc_get_secrets_attachment[0]
module.cc_iam.aws_iam_role_policy_attachment.cc_metrics_attachment[0]
module.cc_iam.aws_iam_role_policy_attachment.cc_session_manager_attachment[0]
module.cc_sg.data.aws_vpc.selected
module.cc_sg.aws_security_group.cc_mgmt_sg[0]
module.cc_sg.aws_security_group.cc_service_sg[0]
module.cc_sg.aws_vpc_security_group_egress_rule.egress_cc_mgmt_tcp_12002[0]
module.cc_sg.aws_vpc_security_group_egress_rule.egress_cc_mgmt_tcp_443[0]
module.cc_sg.aws_vpc_security_group_egress_rule.egress_cc_mgmt_udp_123[0]
module.cc_sg.aws_vpc_security_group_egress_rule.egress_cc_service_all[0]
module.cc_sg.aws_vpc_security_group_egress_rule.egress_cc_service_tcp_443[0]
module.cc_sg.aws_vpc_security_group_egress_rule.egress_cc_service_udp_123[0]
module.cc_sg.aws_vpc_security_group_egress_rule.egress_cc_service_udp_443[0]
module.cc_sg.aws_vpc_security_group_ingress_rule.cc_mgmt_ingress_ssh[0]
module.cc_sg.aws_vpc_security_group_ingress_rule.ingress_cc_service_all[0]
module.cc_sg.aws_vpc_security_group_ingress_rule.ingress_cc_service_health_check[0]
module.cc_sg.aws_vpc_security_group_ingress_rule.ingress_cc_service_https_local[0]
module.cc_vm.data.aws_ebs_default_kms_key.current_kms_key[0]
module.cc_vm.data.aws_kms_alias.current_kms_arn[0]
module.cc_vm.aws_instance.cc_vm[0]
module.cc_vm.aws_network_interface.cc_vm_nic_index_0[0]
module.cc_vm.aws_network_interface.cc_vm_nic_index_1[0]
module.network.data.aws_availability_zones.available
module.network.data.aws_internet_gateway.igw_selected
module.network.data.aws_nat_gateway.ngw_selected[0]
module.network.data.aws_subnet.cc_subnet_selected[0]
module.network.aws_eip.eip[0]
module.network.aws_internet_gateway.igw[0]
module.network.aws_nat_gateway.ngw[0]
module.network.aws_route_table.cc_rt[0]
module.network.aws_route_table.public_rt[0]
module.network.aws_route_table.workload_rt[0]
module.network.aws_route_table_association.cc_rt_asssociation[0]
module.network.aws_route_table_association.public_rt_association[0]
module.network.aws_route_table_association.workload_rt_association[0]
module.network.aws_subnet.cc_subnet[0]
module.network.aws_subnet.public_subnet[0]
module.network.aws_subnet.workload_subnet[0]
module.network.aws_vpc.vpc[0]
module.workload.data.aws_partition.workload_current_partition
module.workload.data.aws_ssm_parameter.amazon_linux_latest
module.workload.data.aws_vpc.selected
module.workload.data.local_sensitive_file.zscaler_root_cert
module.workload.aws_iam_instance_profile.server_host_profile
module.workload.aws_iam_role.node_iam_role
module.workload.aws_iam_role_policy_attachment.ssm_managed_instance_core
module.workload.aws_instance.server_host[0]
module.workload.aws_security_group.node_sg
module.workload.aws_security_group_rule.server_node_ingress_self
module.workload.aws_security_group_rule.server_node_ingress_ssh`
[]Use the Starter Deployment Template with ZPA (base_1cc_zpa) to deploy your Cloud Connector in a new VPC. The template creates the following resources:
- VPC
- Cloud Connector Subnet
- Public Subnet
- Private Subnet
- Key Pair for SSH access
- Instance profile with IAM role and required policy permissions (Secrets Manager, Systems Manager [SSM], Workload Tags)
- Elastic IP address associated with NAT Gateway
- Cloud Connector VM
- Route 53 subnet, Resolver rules, and outbound endpoints
- Linux bastion host
- Linux workload server
- Internet gateway
- NAT gateway
- Management interface
- Service interface
- Network security group for management interface
- Network security group for service interface
- Route tables for routing the workload traffic through the Cloud Connector
- [See Resource Logs](#tf-zpa-output)
[]
`data.aws_ami.cloudconnector
aws_key_pair.deployer
local_file.private_key
local_file.testbed
local_file.user_data_file
random_string.suffix
tls_private_key.key
module.bastion.data.aws_iam_policy_document.bastion_instance_assume_role_policy
module.bastion.data.aws_partition.bastion_current_partition
module.bastion.data.aws_ssm_parameter.amazon_linux_latest
module.bastion.data.aws_vpc.selected
module.bastion.aws_iam_instance_profile.bastion_host_profile
module.bastion.aws_iam_role.bastion_iam_role
module.bastion.aws_iam_role_policy_attachment.ssm_managed_instance_core
module.bastion.aws_instance.bastion
module.bastion.aws_security_group.bastion
module.bastion.aws_security_group_rule.internet
module.bastion.aws_security_group_rule.intranet
module.bastion.aws_security_group_rule.ssh
module.cc_iam.data.aws_secretsmanager_secret.cc_secret_name
module.cc_iam.aws_iam_instance_profile.cc_host_profile[0]
module.cc_iam.aws_iam_policy.cc_get_secrets_policy[0]
module.cc_iam.aws_iam_policy.cc_metrics_policy[0]
module.cc_iam.aws_iam_policy.cc_session_manager_policy[0]
module.cc_iam.aws_iam_role.cc_node_iam_role[0]
module.cc_iam.aws_iam_role_policy_attachment.cc_get_secrets_attachment[0]
module.cc_iam.aws_iam_role_policy_attachment.cc_metrics_attachment[0]
module.cc_iam.aws_iam_role_policy_attachment.cc_session_manager_attachment[0]
module.cc_sg.data.aws_vpc.selected
module.cc_sg.aws_security_group.cc_mgmt_sg[0]
module.cc_sg.aws_security_group.cc_service_sg[0]
module.cc_sg.aws_security_group.outbound_endpoint_sg[0]
module.cc_sg.aws_vpc_security_group_egress_rule.egress_cc_mgmt_tcp_12002[0]
module.cc_sg.aws_vpc_security_group_egress_rule.egress_cc_mgmt_tcp_443[0]
module.cc_sg.aws_vpc_security_group_egress_rule.egress_cc_mgmt_udp_123[0]
module.cc_sg.aws_vpc_security_group_egress_rule.egress_cc_service_all[0]
module.cc_sg.aws_vpc_security_group_egress_rule.egress_cc_service_tcp_443[0]
module.cc_sg.aws_vpc_security_group_egress_rule.egress_cc_service_udp_123[0]
module.cc_sg.aws_vpc_security_group_egress_rule.egress_cc_service_udp_443[0]
module.cc_sg.aws_vpc_security_group_egress_rule.egress_outbound_endpoint_tcp_all[0]
module.cc_sg.aws_vpc_security_group_egress_rule.egress_outbound_endpoint_udp_all[0]
module.cc_sg.aws_vpc_security_group_ingress_rule.cc_mgmt_ingress_ssh[0]
module.cc_sg.aws_vpc_security_group_ingress_rule.ingress_cc_service_all[0]
module.cc_sg.aws_vpc_security_group_ingress_rule.ingress_cc_service_health_check[0]
module.cc_sg.aws_vpc_security_group_ingress_rule.ingress_cc_service_https_local[0]
module.cc_sg.aws_vpc_security_group_ingress_rule.ingress_outbound_endpoint_tcp_all[0]
module.cc_sg.aws_vpc_security_group_ingress_rule.ingress_outbound_endpoint_udp_all[0]
module.cc_vm.data.aws_ebs_default_kms_key.current_kms_key[0]
module.cc_vm.data.aws_kms_alias.current_kms_arn[0]
module.cc_vm.aws_instance.cc_vm[0]
module.cc_vm.aws_network_interface.cc_vm_nic_index_0[0]
module.cc_vm.aws_network_interface.cc_vm_nic_index_1[0]
module.network.data.aws_availability_zones.available
module.network.data.aws_internet_gateway.igw_selected
module.network.data.aws_nat_gateway.ngw_selected[0]
module.network.data.aws_subnet.cc_subnet_selected[0]
module.network.aws_eip.eip[0]
module.network.aws_internet_gateway.igw[0]
module.network.aws_nat_gateway.ngw[0]
module.network.aws_route_table.cc_rt[0]
module.network.aws_route_table.public_rt[0]
module.network.aws_route_table.route53_rt[0]
module.network.aws_route_table.route53_rt[1]
module.network.aws_route_table.workload_rt[0]
module.network.aws_route_table_association.cc_rt_asssociation[0]
module.network.aws_route_table_association.public_rt_association[0]
module.network.aws_route_table_association.route53_rt_asssociation[0]
module.network.aws_route_table_association.route53_rt_asssociation[1]
module.network.aws_route_table_association.workload_rt_association[0]
module.network.aws_subnet.cc_subnet[0]
module.network.aws_subnet.public_subnet[0]
module.network.aws_subnet.route53_subnet[0]
module.network.aws_subnet.route53_subnet[1]
module.network.aws_subnet.workload_subnet[0]
module.network.aws_vpc.vpc[0]
module.route53.aws_route53_resolver_endpoint.zpa_r53_ep
module.route53.aws_route53_resolver_rule.fwd_to_cc["appseg1"]
module.route53.aws_route53_resolver_rule.fwd_to_cc["appseg2"]
module.route53.aws_route53_resolver_rule.system["ZS-FreeBSD"]
module.route53.aws_route53_resolver_rule.system["ZS-NTP"]
module.route53.aws_route53_resolver_rule.system["ZS-ZPABeta"]
module.route53.aws_route53_resolver_rule.system["ZS-ZPAGov"]
module.route53.aws_route53_resolver_rule.system["ZS-Zpath"]
module.route53.aws_route53_resolver_rule.system["ZS-ZsCloud"]
module.route53.aws_route53_resolver_rule.system["ZS-ZsNet"]
module.route53.aws_route53_resolver_rule.system["ZS-Zscaler"]
module.route53.aws_route53_resolver_rule.system["ZS-ZscalerBeta"]
module.route53.aws_route53_resolver_rule.system["ZS-ZscalerGov"]
module.route53.aws_route53_resolver_rule.system["ZS-ZscalerOne"]
module.route53.aws_route53_resolver_rule.system["ZS-ZscalerThree"]
module.route53.aws_route53_resolver_rule.system["ZS-ZscalerTwo"]
module.route53.aws_route53_resolver_rule_association.r53_rule_association_system["ZS-FreeBSD"]
module.route53.aws_route53_resolver_rule_association.r53_rule_association_system["ZS-NTP"]
module.route53.aws_route53_resolver_rule_association.r53_rule_association_system["ZS-ZPABeta"]
module.route53.aws_route53_resolver_rule_association.r53_rule_association_system["ZS-ZPAGov"]
module.route53.aws_route53_resolver_rule_association.r53_rule_association_system["ZS-Zpath"]
module.route53.aws_route53_resolver_rule_association.r53_rule_association_system["ZS-ZsCloud"]
module.route53.aws_route53_resolver_rule_association.r53_rule_association_system["ZS-ZsNet"]
module.route53.aws_route53_resolver_rule_association.r53_rule_association_system["ZS-Zscaler"]
module.route53.aws_route53_resolver_rule_association.r53_rule_association_system["ZS-ZscalerBeta"]
module.route53.aws_route53_resolver_rule_association.r53_rule_association_system["ZS-ZscalerGov"]
module.route53.aws_route53_resolver_rule_association.r53_rule_association_system["ZS-ZscalerOne"]
module.route53.aws_route53_resolver_rule_association.r53_rule_association_system["ZS-ZscalerThree"]
module.route53.aws_route53_resolver_rule_association.r53_rule_association_system["ZS-ZscalerTwo"]
module.route53.aws_route53_resolver_rule_association.r53_rule_association_to_cc["appseg1"]
module.route53.aws_route53_resolver_rule_association.r53_rule_association_to_cc["appseg2"]
module.workload.data.aws_partition.workload_current_partition
module.workload.data.aws_ssm_parameter.amazon_linux_latest
module.workload.data.aws_vpc.selected
module.workload.data.local_sensitive_file.zscaler_root_cert
module.workload.aws_iam_instance_profile.server_host_profile
module.workload.aws_iam_role.node_iam_role
module.workload.aws_iam_role_policy_attachment.ssm_managed_instance_core
module.workload.aws_instance.server_host[0]
module.workload.aws_security_group.node_sg
module.workload.aws_security_group_rule.server_node_ingress_self
module.workload.aws_security_group_rule.server_node_ingress_ssh`
[]Use the Starter Deployment Template with Gateway Load Balancer (base_cc_gwlb) to deploy your Cloud Connector in a new VPC. The template creates the following resources:
- VPC
- Gateway Load Balancer
- Cloud Connector subnet
- Public subnet
- Private subnet
- Key pair for SSH access
- Instance profile with IAM role and required policy permissions (Secrets Manager, Systems Manager [SSM], Workload Tags)
- Elastic IP address associated with NAT gateway
- Two Cloud Connector VMs
- Route 53 subnet, Resolver rules, and outbound endpoints
- Linux bastion host
- Linux workload server
- Internet gateway
- NAT gateway
- Management interface
- Service interface
- Network security group for management interface
- Network security group for service interface
- Route tables for routing the workload traffic through the Cloud Connector and for rerouting traffic to the second Cloud Connector
- [See Resource Logs](#tf-resources-gwlb)
[]
`data.aws_ami.cloudconnector
aws_key_pair.deployer
local_file.private_key
local_file.testbed
local_file.user_data_file
random_string.suffix
tls_private_key.key
module.bastion.data.aws_iam_policy_document.bastion_instance_assume_role_policy
module.bastion.data.aws_partition.bastion_current_partition
module.bastion.data.aws_ssm_parameter.amazon_linux_latest
module.bastion.data.aws_vpc.selected
module.bastion.aws_iam_instance_profile.bastion_host_profile
module.bastion.aws_iam_role.bastion_iam_role
module.bastion.aws_iam_role_policy_attachment.ssm_managed_instance_core
module.bastion.aws_instance.bastion
module.bastion.aws_security_group.bastion
module.bastion.aws_security_group_rule.internet
module.bastion.aws_security_group_rule.intranet
module.bastion.aws_security_group_rule.ssh
module.cc_iam.data.aws_iam_policy_document.cc_autoscale_lifecycle_policy_document
module.cc_iam.data.aws_iam_policy_document.cc_get_secrets_policy_document
module.cc_iam.data.aws_iam_policy_document.cc_metrics_policy_document
module.cc_iam.data.aws_iam_policy_document.cc_session_manager_policy_document
module.cc_iam.data.aws_iam_policy_document.cc_tags_policy_document
module.cc_iam.data.aws_iam_policy_document.instance_assume_role_policy
module.cc_iam.data.aws_secretsmanager_secret.cc_secret_name
module.cc_iam.aws_iam_instance_profile.cc_host_profile[0]
module.cc_iam.aws_iam_instance_profile.cc_host_profile[1]
module.cc_iam.aws_iam_instance_profile.cc_host_profile[2]
module.cc_iam.aws_iam_instance_profile.cc_host_profile[3]
module.cc_iam.aws_iam_policy.cc_get_secrets_policy[0]
module.cc_iam.aws_iam_policy.cc_get_secrets_policy[1]
module.cc_iam.aws_iam_policy.cc_get_secrets_policy[2]
module.cc_iam.aws_iam_policy.cc_get_secrets_policy[3]
module.cc_iam.aws_iam_policy.cc_metrics_policy[0]
module.cc_iam.aws_iam_policy.cc_metrics_policy[1]
module.cc_iam.aws_iam_policy.cc_metrics_policy[2]
module.cc_iam.aws_iam_policy.cc_metrics_policy[3]
module.cc_iam.aws_iam_policy.cc_session_manager_policy[0]
module.cc_iam.aws_iam_policy.cc_session_manager_policy[1]
module.cc_iam.aws_iam_policy.cc_session_manager_policy[2]
module.cc_iam.aws_iam_policy.cc_session_manager_policy[3]
module.cc_iam.aws_iam_role.cc_node_iam_role[0]
module.cc_iam.aws_iam_role.cc_node_iam_role[1]
module.cc_iam.aws_iam_role.cc_node_iam_role[2]
module.cc_iam.aws_iam_role.cc_node_iam_role[3]
module.cc_iam.aws_iam_role_policy_attachment.cc_get_secrets_attachment[0]
module.cc_iam.aws_iam_role_policy_attachment.cc_get_secrets_attachment[1]
module.cc_iam.aws_iam_role_policy_attachment.cc_get_secrets_attachment[2]
module.cc_iam.aws_iam_role_policy_attachment.cc_get_secrets_attachment[3]
module.cc_iam.aws_iam_role_policy_attachment.cc_metrics_attachment[0]
module.cc_iam.aws_iam_role_policy_attachment.cc_metrics_attachment[1]
module.cc_iam.aws_iam_role_policy_attachment.cc_metrics_attachment[2]
module.cc_iam.aws_iam_role_policy_attachment.cc_metrics_attachment[3]
module.cc_iam.aws_iam_role_policy_attachment.cc_session_manager_attachment[0]
module.cc_iam.aws_iam_role_policy_attachment.cc_session_manager_attachment[1]
module.cc_iam.aws_iam_role_policy_attachment.cc_session_manager_attachment[2]
module.cc_iam.aws_iam_role_policy_attachment.cc_session_manager_attachment[3]
module.cc_sg.data.aws_vpc.selected
module.cc_sg.aws_security_group.cc_mgmt_sg[0]
module.cc_sg.aws_security_group.cc_mgmt_sg[1]
module.cc_sg.aws_security_group.cc_mgmt_sg[2]
module.cc_sg.aws_security_group.cc_mgmt_sg[3]
module.cc_sg.aws_security_group.cc_service_sg[0]
module.cc_sg.aws_security_group.cc_service_sg[1]
module.cc_sg.aws_security_group.cc_service_sg[2]
module.cc_sg.aws_security_group.cc_service_sg[3]
module.cc_sg.aws_vpc_security_group_egress_rule.egress_cc_mgmt_tcp_12002[0]
module.cc_sg.aws_vpc_security_group_egress_rule.egress_cc_mgmt_tcp_12002[1]
module.cc_sg.aws_vpc_security_group_egress_rule.egress_cc_mgmt_tcp_12002[2]
module.cc_sg.aws_vpc_security_group_egress_rule.egress_cc_mgmt_tcp_12002[3]
module.cc_sg.aws_vpc_security_group_egress_rule.egress_cc_mgmt_tcp_443[0]
module.cc_sg.aws_vpc_security_group_egress_rule.egress_cc_mgmt_tcp_443[1]
module.cc_sg.aws_vpc_security_group_egress_rule.egress_cc_mgmt_tcp_443[2]
module.cc_sg.aws_vpc_security_group_egress_rule.egress_cc_mgmt_tcp_443[3]
module.cc_sg.aws_vpc_security_group_egress_rule.egress_cc_mgmt_udp_123[0]
module.cc_sg.aws_vpc_security_group_egress_rule.egress_cc_mgmt_udp_123[1]
module.cc_sg.aws_vpc_security_group_egress_rule.egress_cc_mgmt_udp_123[2]
module.cc_sg.aws_vpc_security_group_egress_rule.egress_cc_mgmt_udp_123[3]
module.cc_sg.aws_vpc_security_group_egress_rule.egress_cc_service_all[0]
module.cc_sg.aws_vpc_security_group_egress_rule.egress_cc_service_all[1]
module.cc_sg.aws_vpc_security_group_egress_rule.egress_cc_service_all[2]
module.cc_sg.aws_vpc_security_group_egress_rule.egress_cc_service_all[3]
module.cc_sg.aws_vpc_security_group_egress_rule.egress_cc_service_geneve[0]
module.cc_sg.aws_vpc_security_group_egress_rule.egress_cc_service_geneve[1]
module.cc_sg.aws_vpc_security_group_egress_rule.egress_cc_service_geneve[2]
module.cc_sg.aws_vpc_security_group_egress_rule.egress_cc_service_geneve[3]
module.cc_sg.aws_vpc_security_group_egress_rule.egress_cc_service_tcp_443[0]
module.cc_sg.aws_vpc_security_group_egress_rule.egress_cc_service_tcp_443[1]
module.cc_sg.aws_vpc_security_group_egress_rule.egress_cc_service_tcp_443[2]
module.cc_sg.aws_vpc_security_group_egress_rule.egress_cc_service_tcp_443[3]
module.cc_sg.aws_vpc_security_group_egress_rule.egress_cc_service_udp_123[0]
module.cc_sg.aws_vpc_security_group_egress_rule.egress_cc_service_udp_123[1]
module.cc_sg.aws_vpc_security_group_egress_rule.egress_cc_service_udp_123[2]
module.cc_sg.aws_vpc_security_group_egress_rule.egress_cc_service_udp_123[3]
module.cc_sg.aws_vpc_security_group_egress_rule.egress_cc_service_udp_443[0]
module.cc_sg.aws_vpc_security_group_egress_rule.egress_cc_service_udp_443[1]
module.cc_sg.aws_vpc_security_group_egress_rule.egress_cc_service_udp_443[2]
module.cc_sg.aws_vpc_security_group_egress_rule.egress_cc_service_udp_443[3]
module.cc_sg.aws_vpc_security_group_ingress_rule.cc_mgmt_ingress_ssh[0]
module.cc_sg.aws_vpc_security_group_ingress_rule.cc_mgmt_ingress_ssh[1]
module.cc_sg.aws_vpc_security_group_ingress_rule.cc_mgmt_ingress_ssh[2]
module.cc_sg.aws_vpc_security_group_ingress_rule.cc_mgmt_ingress_ssh[3]
module.cc_sg.aws_vpc_security_group_ingress_rule.ingress_cc_service_all[0]
module.cc_sg.aws_vpc_security_group_ingress_rule.ingress_cc_service_all[1]
module.cc_sg.aws_vpc_security_group_ingress_rule.ingress_cc_service_all[2]
module.cc_sg.aws_vpc_security_group_ingress_rule.ingress_cc_service_all[3]
module.cc_sg.aws_vpc_security_group_ingress_rule.ingress_cc_service_geneve[0]
module.cc_sg.aws_vpc_security_group_ingress_rule.ingress_cc_service_geneve[1]
module.cc_sg.aws_vpc_security_group_ingress_rule.ingress_cc_service_geneve[2]
module.cc_sg.aws_vpc_security_group_ingress_rule.ingress_cc_service_geneve[3]
module.cc_sg.aws_vpc_security_group_ingress_rule.ingress_cc_service_health_check[0]
module.cc_sg.aws_vpc_security_group_ingress_rule.ingress_cc_service_health_check[1]
module.cc_sg.aws_vpc_security_group_ingress_rule.ingress_cc_service_health_check[2]
module.cc_sg.aws_vpc_security_group_ingress_rule.ingress_cc_service_health_check[3]
module.cc_sg.aws_vpc_security_group_ingress_rule.ingress_cc_service_https_local[0]
module.cc_sg.aws_vpc_security_group_ingress_rule.ingress_cc_service_https_local[1]
module.cc_sg.aws_vpc_security_group_ingress_rule.ingress_cc_service_https_local[2]
module.cc_sg.aws_vpc_security_group_ingress_rule.ingress_cc_service_https_local[3]
module.cc_vm.data.aws_ebs_default_kms_key.current_kms_key[0]
module.cc_vm.data.aws_kms_alias.current_kms_arn[0]
module.cc_vm.aws_instance.cc_vm[0]
module.cc_vm.aws_instance.cc_vm[1]
module.cc_vm.aws_instance.cc_vm[2]
module.cc_vm.aws_instance.cc_vm[3]
module.cc_vm.aws_network_interface.cc_vm_nic_index_0[0]
module.cc_vm.aws_network_interface.cc_vm_nic_index_0[1]
module.cc_vm.aws_network_interface.cc_vm_nic_index_0[2]
module.cc_vm.aws_network_interface.cc_vm_nic_index_0[3]
module.cc_vm.aws_network_interface.cc_vm_nic_index_1[0]
module.cc_vm.aws_network_interface.cc_vm_nic_index_1[1]
module.cc_vm.aws_network_interface.cc_vm_nic_index_1[2]
module.cc_vm.aws_network_interface.cc_vm_nic_index_1[3]
module.gwlb.aws_lb.gwlb
module.gwlb.aws_lb_listener.gwlb_listener
module.gwlb.aws_lb_target_group.gwlb_target_group
module.gwlb.aws_lb_target_group_attachment.gwlb_target_group_attachment[0]
module.gwlb.aws_lb_target_group_attachment.gwlb_target_group_attachment[1]
module.gwlb.aws_lb_target_group_attachment.gwlb_target_group_attachment[2]
module.gwlb.aws_lb_target_group_attachment.gwlb_target_group_attachment[3]
module.gwlb_endpoint.data.aws_caller_identity.current
module.gwlb_endpoint.data.aws_partition.current
module.gwlb_endpoint.aws_vpc_endpoint.gwlb_vpce[0]
module.gwlb_endpoint.aws_vpc_endpoint.gwlb_vpce[1]
module.gwlb_endpoint.aws_vpc_endpoint_service.gwlb_vpce_service[0]
module.network.data.aws_availability_zones.available
module.network.data.aws_internet_gateway.igw_selected
module.network.data.aws_nat_gateway.ngw_selected[0]
module.network.data.aws_nat_gateway.ngw_selected[1]
module.network.data.aws_subnet.cc_subnet_selected[0]
module.network.data.aws_subnet.cc_subnet_selected[1]
module.network.aws_eip.eip[0]
module.network.aws_eip.eip[1]
module.network.aws_internet_gateway.igw[0]
module.network.aws_nat_gateway.ngw[0]
module.network.aws_nat_gateway.ngw[1]
module.network.aws_route_table.cc_rt[0]
module.network.aws_route_table.cc_rt[1]
module.network.aws_route_table.public_rt[0]
module.network.aws_route_table.workload_rt[0]
module.network.aws_route_table.workload_rt[1]
module.network.aws_route_table_association.cc_rt_asssociation[0]
module.network.aws_route_table_association.cc_rt_asssociation[1]
module.network.aws_route_table_association.public_rt_association[0]
module.network.aws_route_table_association.public_rt_association[1]
module.network.aws_route_table_association.workload_rt_association[0]
module.network.aws_route_table_association.workload_rt_association[1]
module.network.aws_subnet.cc_subnet[0]
module.network.aws_subnet.cc_subnet[1]
module.network.aws_subnet.public_subnet[0]
module.network.aws_subnet.public_subnet[1]
module.network.aws_subnet.workload_subnet[0]
module.network.aws_subnet.workload_subnet[1]
module.network.aws_vpc.vpc[0]
module.workload.data.aws_partition.workload_current_partition
module.workload.data.aws_ssm_parameter.amazon_linux_latest
module.workload.data.aws_vpc.selected
module.workload.data.local_sensitive_file.zscaler_root_cert
module.workload.aws_iam_instance_profile.server_host_profile
module.workload.aws_iam_role.node_iam_role
module.workload.aws_iam_role_policy_attachment.ssm_managed_instance_core
module.workload.aws_instance.server_host[0]
module.workload.aws_instance.server_host[1]
module.workload.aws_security_group.node_sg
module.workload.aws_security_group_rule.server_node_ingress_self
module.workload.aws_security_group_rule.server_node_ingress_ssh`
[]Use the Starter Deployment Template with Gateway Load Balancer and ZPA (base_cc_gwlb_zpa) to deploy your Cloud Connector in a new VPC and to load balance traffic across multiple Cloud Connectors. Route 53 endpoints direct DNS resolver capability for ZPA. The template creates the following resources:
- VPC
- Gateway Load Balancer
- Cloud Connector subnet
- Public subnet
- Private subnet
- Key pair for SSH access
- Instance profile with IAM role and required policy permissions (Secrets Manager, Systems Manager [SSM], Workload Tags)
- Elastic IP address associated with NAT gateway
- Two Cloud Connector VMs
- Linux bastion host
- Linux workload server
- Internet gateway
- NAT gateway
- Management interface
- Service interface
- Network security group for management interface
- Network security group for service interface
- Route tables for routing the workload traffic through the Cloud Connector and for rerouting traffic to the second Cloud Connector
- Route 53 subnet, Resolver rules, and outbound endpoints
- [See Resource Logs](#tf-resources-gwlb-zpa)
[]
`data.aws_ami.cloudconnector
aws_key_pair.deployer
local_file.private_key
local_file.testbed
local_file.user_data_file
random_string.suffix
tls_private_key.key
module.bastion.data.aws_iam_policy_document.bastion_instance_assume_role_policy
module.bastion.data.aws_partition.bastion_current_partition
module.bastion.data.aws_ssm_parameter.amazon_linux_latest
module.bastion.data.aws_vpc.selected
module.bastion.aws_iam_instance_profile.bastion_host_profile
module.bastion.aws_iam_role.bastion_iam_role
module.bastion.aws_iam_role_policy_attachment.ssm_managed_instance_core
module.bastion.aws_instance.bastion
module.bastion.aws_security_group.bastion
module.bastion.aws_security_group_rule.internet
module.bastion.aws_security_group_rule.intranet
module.bastion.aws_security_group_rule.ssh
module.cc_iam.data.aws_secretsmanager_secret.cc_secret_name
module.cc_iam.aws_iam_instance_profile.cc_host_profile[0]
module.cc_iam.aws_iam_instance_profile.cc_host_profile[1]
module.cc_iam.aws_iam_instance_profile.cc_host_profile[2]
module.cc_iam.aws_iam_instance_profile.cc_host_profile[3]
module.cc_iam.aws_iam_policy.cc_get_secrets_policy[0]
module.cc_iam.aws_iam_policy.cc_get_secrets_policy[1]
module.cc_iam.aws_iam_policy.cc_get_secrets_policy[2]
module.cc_iam.aws_iam_policy.cc_get_secrets_policy[3]
module.cc_iam.aws_iam_policy.cc_metrics_policy[0]
module.cc_iam.aws_iam_policy.cc_metrics_policy[1]
module.cc_iam.aws_iam_policy.cc_metrics_policy[2]
module.cc_iam.aws_iam_policy.cc_metrics_policy[3]
module.cc_iam.aws_iam_policy.cc_session_manager_policy[0]
module.cc_iam.aws_iam_policy.cc_session_manager_policy[1]
module.cc_iam.aws_iam_policy.cc_session_manager_policy[2]
module.cc_iam.aws_iam_policy.cc_session_manager_policy[3]
module.cc_iam.aws_iam_role.cc_node_iam_role[0]
module.cc_iam.aws_iam_role.cc_node_iam_role[1]
module.cc_iam.aws_iam_role.cc_node_iam_role[2]
module.cc_iam.aws_iam_role.cc_node_iam_role[3]
module.cc_iam.aws_iam_role_policy_attachment.cc_get_secrets_attachment[0]
module.cc_iam.aws_iam_role_policy_attachment.cc_get_secrets_attachment[1]
module.cc_iam.aws_iam_role_policy_attachment.cc_get_secrets_attachment[2]
module.cc_iam.aws_iam_role_policy_attachment.cc_get_secrets_attachment[3]
module.cc_iam.aws_iam_role_policy_attachment.cc_metrics_attachment[0]
module.cc_iam.aws_iam_role_policy_attachment.cc_metrics_attachment[1]
module.cc_iam.aws_iam_role_policy_attachment.cc_metrics_attachment[2]
module.cc_iam.aws_iam_role_policy_attachment.cc_metrics_attachment[3]
module.cc_iam.aws_iam_role_policy_attachment.cc_session_manager_attachment[0]
module.cc_iam.aws_iam_role_policy_attachment.cc_session_manager_attachment[1]
module.cc_iam.aws_iam_role_policy_attachment.cc_session_manager_attachment[2]
module.cc_iam.aws_iam_role_policy_attachment.cc_session_manager_attachment[3]
module.cc_sg.data.aws_vpc.selected
module.cc_sg.aws_security_group.cc_mgmt_sg[0]
module.cc_sg.aws_security_group.cc_mgmt_sg[1]
module.cc_sg.aws_security_group.cc_mgmt_sg[2]
module.cc_sg.aws_security_group.cc_mgmt_sg[3]
module.cc_sg.aws_security_group.cc_service_sg[0]
module.cc_sg.aws_security_group.cc_service_sg[1]
module.cc_sg.aws_security_group.cc_service_sg[2]
module.cc_sg.aws_security_group.cc_service_sg[3]
module.cc_sg.aws_security_group.outbound_endpoint_sg[0]
module.cc_sg.aws_vpc_security_group_egress_rule.egress_cc_mgmt_tcp_12002[0]
module.cc_sg.aws_vpc_security_group_egress_rule.egress_cc_mgmt_tcp_12002[1]
module.cc_sg.aws_vpc_security_group_egress_rule.egress_cc_mgmt_tcp_12002[2]
module.cc_sg.aws_vpc_security_group_egress_rule.egress_cc_mgmt_tcp_12002[3]
module.cc_sg.aws_vpc_security_group_egress_rule.egress_cc_mgmt_tcp_443[0]
module.cc_sg.aws_vpc_security_group_egress_rule.egress_cc_mgmt_tcp_443[1]
module.cc_sg.aws_vpc_security_group_egress_rule.egress_cc_mgmt_tcp_443[2]
module.cc_sg.aws_vpc_security_group_egress_rule.egress_cc_mgmt_tcp_443[3]
module.cc_sg.aws_vpc_security_group_egress_rule.egress_cc_mgmt_udp_123[0]
module.cc_sg.aws_vpc_security_group_egress_rule.egress_cc_mgmt_udp_123[1]
module.cc_sg.aws_vpc_security_group_egress_rule.egress_cc_mgmt_udp_123[2]
module.cc_sg.aws_vpc_security_group_egress_rule.egress_cc_mgmt_udp_123[3]
module.cc_sg.aws_vpc_security_group_egress_rule.egress_cc_service_all[0]
module.cc_sg.aws_vpc_security_group_egress_rule.egress_cc_service_all[1]
module.cc_sg.aws_vpc_security_group_egress_rule.egress_cc_service_all[2]
module.cc_sg.aws_vpc_security_group_egress_rule.egress_cc_service_all[3]
module.cc_sg.aws_vpc_security_group_egress_rule.egress_cc_service_geneve[0]
module.cc_sg.aws_vpc_security_group_egress_rule.egress_cc_service_geneve[1]
module.cc_sg.aws_vpc_security_group_egress_rule.egress_cc_service_geneve[2]
module.cc_sg.aws_vpc_security_group_egress_rule.egress_cc_service_geneve[3]
module.cc_sg.aws_vpc_security_group_egress_rule.egress_cc_service_tcp_443[0]
module.cc_sg.aws_vpc_security_group_egress_rule.egress_cc_service_tcp_443[1]
module.cc_sg.aws_vpc_security_group_egress_rule.egress_cc_service_tcp_443[2]
module.cc_sg.aws_vpc_security_group_egress_rule.egress_cc_service_tcp_443[3]
module.cc_sg.aws_vpc_security_group_egress_rule.egress_cc_service_udp_123[0]
module.cc_sg.aws_vpc_security_group_egress_rule.egress_cc_service_udp_123[1]
module.cc_sg.aws_vpc_security_group_egress_rule.egress_cc_service_udp_123[2]
module.cc_sg.aws_vpc_security_group_egress_rule.egress_cc_service_udp_123[3]
module.cc_sg.aws_vpc_security_group_egress_rule.egress_cc_service_udp_443[0]
module.cc_sg.aws_vpc_security_group_egress_rule.egress_cc_service_udp_443[1]
module.cc_sg.aws_vpc_security_group_egress_rule.egress_cc_service_udp_443[2]
module.cc_sg.aws_vpc_security_group_egress_rule.egress_cc_service_udp_443[3]
module.cc_sg.aws_vpc_security_group_egress_rule.egress_outbound_endpoint_tcp_all[0]
module.cc_sg.aws_vpc_security_group_egress_rule.egress_outbound_endpoint_udp_all[0]
module.cc_sg.aws_vpc_security_group_ingress_rule.cc_mgmt_ingress_ssh[0]
module.cc_sg.aws_vpc_security_group_ingress_rule.cc_mgmt_ingress_ssh[1]
module.cc_sg.aws_vpc_security_group_ingress_rule.cc_mgmt_ingress_ssh[2]
module.cc_sg.aws_vpc_security_group_ingress_rule.cc_mgmt_ingress_ssh[3]
module.cc_sg.aws_vpc_security_group_ingress_rule.ingress_cc_service_all[0]
module.cc_sg.aws_vpc_security_group_ingress_rule.ingress_cc_service_all[1]
module.cc_sg.aws_vpc_security_group_ingress_rule.ingress_cc_service_all[2]
module.cc_sg.aws_vpc_security_group_ingress_rule.ingress_cc_service_all[3]
module.cc_sg.aws_vpc_security_group_ingress_rule.ingress_cc_service_geneve[0]
module.cc_sg.aws_vpc_security_group_ingress_rule.ingress_cc_service_geneve[1]
module.cc_sg.aws_vpc_security_group_ingress_rule.ingress_cc_service_geneve[2]
module.cc_sg.aws_vpc_security_group_ingress_rule.ingress_cc_service_geneve[3]
module.cc_sg.aws_vpc_security_group_ingress_rule.ingress_cc_service_health_check[0]
module.cc_sg.aws_vpc_security_group_ingress_rule.ingress_cc_service_health_check[1]
module.cc_sg.aws_vpc_security_group_ingress_rule.ingress_cc_service_health_check[2]
module.cc_sg.aws_vpc_security_group_ingress_rule.ingress_cc_service_health_check[3]
module.cc_sg.aws_vpc_security_group_ingress_rule.ingress_cc_service_https_local[0]
module.cc_sg.aws_vpc_security_group_ingress_rule.ingress_cc_service_https_local[1]
module.cc_sg.aws_vpc_security_group_ingress_rule.ingress_cc_service_https_local[2]
module.cc_sg.aws_vpc_security_group_ingress_rule.ingress_cc_service_https_local[3]
module.cc_sg.aws_vpc_security_group_ingress_rule.ingress_outbound_endpoint_tcp_all[0]
module.cc_sg.aws_vpc_security_group_ingress_rule.ingress_outbound_endpoint_udp_all[0]
module.cc_vm.data.aws_ebs_default_kms_key.current_kms_key[0]
module.cc_vm.data.aws_kms_alias.current_kms_arn[0]
module.cc_vm.aws_instance.cc_vm[0]
module.cc_vm.aws_instance.cc_vm[1]
module.cc_vm.aws_instance.cc_vm[2]
module.cc_vm.aws_instance.cc_vm[3]
module.cc_vm.aws_network_interface.cc_vm_nic_index_0[0]
module.cc_vm.aws_network_interface.cc_vm_nic_index_0[1]
module.cc_vm.aws_network_interface.cc_vm_nic_index_0[2]
module.cc_vm.aws_network_interface.cc_vm_nic_index_0[3]
module.cc_vm.aws_network_interface.cc_vm_nic_index_1[0]
module.cc_vm.aws_network_interface.cc_vm_nic_index_1[1]
module.cc_vm.aws_network_interface.cc_vm_nic_index_1[2]
module.cc_vm.aws_network_interface.cc_vm_nic_index_1[3]
module.gwlb.aws_lb.gwlb
module.gwlb.aws_lb_listener.gwlb_listener
module.gwlb.aws_lb_target_group.gwlb_target_group
module.gwlb.aws_lb_target_group_attachment.gwlb_target_group_attachment[0]
module.gwlb.aws_lb_target_group_attachment.gwlb_target_group_attachment[1]
module.gwlb.aws_lb_target_group_attachment.gwlb_target_group_attachment[2]
module.gwlb.aws_lb_target_group_attachment.gwlb_target_group_attachment[3]
module.gwlb_endpoint.data.aws_caller_identity.current
module.gwlb_endpoint.data.aws_partition.current
module.gwlb_endpoint.aws_vpc_endpoint.gwlb_vpce[0]
module.gwlb_endpoint.aws_vpc_endpoint.gwlb_vpce[1]
module.gwlb_endpoint.aws_vpc_endpoint_service.gwlb_vpce_service[0]
module.network.data.aws_availability_zones.available
module.network.data.aws_internet_gateway.igw_selected
module.network.data.aws_nat_gateway.ngw_selected[0]
module.network.data.aws_nat_gateway.ngw_selected[1]
module.network.data.aws_subnet.cc_subnet_selected[0]
module.network.data.aws_subnet.cc_subnet_selected[1]
module.network.aws_eip.eip[0]
module.network.aws_eip.eip[1]
module.network.aws_internet_gateway.igw[0]
module.network.aws_nat_gateway.ngw[0]
module.network.aws_nat_gateway.ngw[1]
module.network.aws_route_table.cc_rt[0]
module.network.aws_route_table.cc_rt[1]
module.network.aws_route_table.public_rt[0]
module.network.aws_route_table.route53_rt[0]
module.network.aws_route_table.route53_rt[1]
module.network.aws_route_table.workload_rt[0]
module.network.aws_route_table.workload_rt[1]
module.network.aws_route_table_association.cc_rt_asssociation[0]
module.network.aws_route_table_association.cc_rt_asssociation[1]
module.network.aws_route_table_association.public_rt_association[0]
module.network.aws_route_table_association.public_rt_association[1]
module.network.aws_route_table_association.route53_rt_asssociation[0]
module.network.aws_route_table_association.route53_rt_asssociation[1]
module.network.aws_route_table_association.workload_rt_association[0]
module.network.aws_route_table_association.workload_rt_association[1]
module.network.aws_subnet.cc_subnet[0]
module.network.aws_subnet.cc_subnet[1]
module.network.aws_subnet.public_subnet[0]
module.network.aws_subnet.public_subnet[1]
module.network.aws_subnet.route53_subnet[0]
module.network.aws_subnet.route53_subnet[1]
module.network.aws_subnet.workload_subnet[0]
module.network.aws_subnet.workload_subnet[1]
module.network.aws_vpc.vpc[0]
module.route53.aws_route53_resolver_endpoint.zpa_r53_ep
module.route53.aws_route53_resolver_rule.fwd_to_cc["appseg1"]
module.route53.aws_route53_resolver_rule.fwd_to_cc["appseg2"]
module.route53.aws_route53_resolver_rule.system["ZS-FreeBSD"]
module.route53.aws_route53_resolver_rule.system["ZS-NTP"]
module.route53.aws_route53_resolver_rule.system["ZS-ZPABeta"]
module.route53.aws_route53_resolver_rule.system["ZS-ZPAGov"]
module.route53.aws_route53_resolver_rule.system["ZS-Zpath"]
module.route53.aws_route53_resolver_rule.system["ZS-ZsCloud"]
module.route53.aws_route53_resolver_rule.system["ZS-ZsNet"]
module.route53.aws_route53_resolver_rule.system["ZS-Zscaler"]
module.route53.aws_route53_resolver_rule.system["ZS-ZscalerBeta"]
module.route53.aws_route53_resolver_rule.system["ZS-ZscalerGov"]
module.route53.aws_route53_resolver_rule.system["ZS-ZscalerOne"]
module.route53.aws_route53_resolver_rule.system["ZS-ZscalerThree"]
module.route53.aws_route53_resolver_rule.system["ZS-ZscalerTwo"]
module.route53.aws_route53_resolver_rule_association.r53_rule_association_system["ZS-FreeBSD"]
module.route53.aws_route53_resolver_rule_association.r53_rule_association_system["ZS-NTP"]
module.route53.aws_route53_resolver_rule_association.r53_rule_association_system["ZS-ZPABeta"]
module.route53.aws_route53_resolver_rule_association.r53_rule_association_system["ZS-ZPAGov"]
module.route53.aws_route53_resolver_rule_association.r53_rule_association_system["ZS-Zpath"]
module.route53.aws_route53_resolver_rule_association.r53_rule_association_system["ZS-ZsCloud"]
module.route53.aws_route53_resolver_rule_association.r53_rule_association_system["ZS-ZsNet"]
module.route53.aws_route53_resolver_rule_association.r53_rule_association_system["ZS-Zscaler"]
module.route53.aws_route53_resolver_rule_association.r53_rule_association_system["ZS-ZscalerBeta"]
module.route53.aws_route53_resolver_rule_association.r53_rule_association_system["ZS-ZscalerGov"]
module.route53.aws_route53_resolver_rule_association.r53_rule_association_system["ZS-ZscalerOne"]
module.route53.aws_route53_resolver_rule_association.r53_rule_association_system["ZS-ZscalerThree"]
module.route53.aws_route53_resolver_rule_association.r53_rule_association_system["ZS-ZscalerTwo"]
module.route53.aws_route53_resolver_rule_association.r53_rule_association_to_cc["appseg1"]
module.route53.aws_route53_resolver_rule_association.r53_rule_association_to_cc["appseg2"]
module.workload.data.aws_partition.workload_current_partition
module.workload.data.aws_ssm_parameter.amazon_linux_latest
module.workload.data.aws_vpc.selected
module.workload.data.local_sensitive_file.zscaler_root_cert
module.workload.aws_iam_instance_profile.server_host_profile
module.workload.aws_iam_role.node_iam_role
module.workload.aws_iam_role_policy_attachment.ssm_managed_instance_core
module.workload.aws_instance.server_host[0]
module.workload.aws_instance.server_host[1]
module.workload.aws_security_group.node_sg
module.workload.aws_security_group_rule.server_node_ingress_self
module.workload.aws_security_group_rule.server_node_ingress_ssh`
[]Use the Starter Deployment Template with Auto Scaling and Gateway Load Balancer (base_cc_gwlb_asg) to deploy your Cloud Connector in a new VPC.
To enable Auto Scaling, contact Zscaler Support.
The template creates the following resources:
- VPC
- Cloud Connector subnet
- Public subnet
- Private subnet
- Internet gateway
- NAT gateway
- Key pair for SSH access
- Instance profile with IAM role and required policy permissions (Secrets Manager, Systems Manager [SSM], Workload Tags)
- IAM policy for lifecycle actions
- IAM policy for CloudWatch metrics
- IAM policy for Lambda logs
- CloudWatch EventBridge rules for Lambda
- Cloudwatch log group
- Elastic IP address associated with NAT gateway
- Cloud Connector appliance
- Management interface
- Service interface
- Network security group for management interface
- Network security group for service interface
- Gateway Load Balancer
- Listener
- Target group
- VPC endpoint service
- VPC endpoints
- Linux bastion EC2 with automatic public IP
- Linux bastion IAM role
- Linux bastion security group
- Linux workload EC2 in a private subnet
- Linux workload IAM role
- Linux workload security group
- Linux workload route table sending default route next-hop VPC endpoint
- Launch template
- Auto Scaling group
- Lambda function
- Lambda permissions
- [Optional] SNS topic for email alerts
- [See Resource Logs](#tf-resources-gwlb-autoscaling)
[]
`[0]-[1] indicates default values where two duplicate/like resources (like cloud connectors) would be created
data.aws_ami.cloudconnector
aws_key_pair.deployer
local_file.private_key
local_file.testbed
local_file.user_data_file
random_string.suffix
tls_private_key.key
module.asg_lambda.data.aws_iam_policy_document.lambda_autoscale_lifecycle_policy_document
module.asg_lambda.data.aws_iam_policy_document.lambda_get_secrets_policy_document
module.asg_lambda.data.aws_iam_policy_document.lambda_logs_policy_document
module.asg_lambda.data.aws_iam_policy_document.lambda_metrics_policy_document
module.asg_lambda.data.aws_secretsmanager_secret.lambda_secret_name
module.asg_lambda.aws_cloudwatch_event_rule.asg_cloudwatch_instance_termination_event_rule
module.asg_lambda.aws_cloudwatch_event_rule.asg_cloudwatch_lifecycle_event_rule
module.asg_lambda.aws_cloudwatch_event_rule.asg_cloudwatch_scheduler_event_rule
module.asg_lambda.aws_cloudwatch_event_target.asg_cloudwatch_instance_termination_event_target
module.asg_lambda.aws_cloudwatch_event_target.asg_cloudwatch_lifecycle_event_target
module.asg_lambda.aws_cloudwatch_event_target.asg_cloudwatch_scheduler_event_target
module.asg_lambda.aws_cloudwatch_log_group.asg_cloudwatch_log_group
module.asg_lambda.aws_iam_policy.lambda_autoscale_lifecycle_policy
module.asg_lambda.aws_iam_policy.lambda_get_secrets_policy
module.asg_lambda.aws_iam_policy.lambda_logs_policy
module.asg_lambda.aws_iam_policy.lambda_metrics_policy
module.asg_lambda.aws_iam_role.asg_lambda_iam_role
module.asg_lambda.aws_iam_role_policy_attachment.lambda_autoscale_lifecycle_attachment
module.asg_lambda.aws_iam_role_policy_attachment.lambda_get_secrets_attachment
module.asg_lambda.aws_iam_role_policy_attachment.lambda_logs_attachment
module.asg_lambda.aws_iam_role_policy_attachment.lambda_metrics_attachment
module.asg_lambda.aws_lambda_function.asg_lambda_function
module.asg_lambda.aws_lambda_permission.asg_cloudwatch_instance_termination_permission
module.asg_lambda.aws_lambda_permission.asg_cloudwatch_lifecycle_permission
module.asg_lambda.aws_lambda_permission.asg_cloudwatch_scheduler_event_permission
module.bastion.data.aws_iam_policy_document.bastion_instance_assume_role_policy
module.bastion.data.aws_ssm_parameter.amazon_linux_latest
module.bastion.data.aws_vpc.selected
module.bastion.aws_iam_instance_profile.bastion_host_profile
module.bastion.aws_iam_role.bastion_iam_role
module.bastion.aws_iam_role_policy_attachment.ssm_managed_instance_core
module.bastion.aws_instance.bastion
module.bastion.aws_security_group.bastion
module.bastion.aws_security_group_rule.internet
module.bastion.aws_security_group_rule.intranet
module.bastion.aws_security_group_rule.ssh
module.cc_asg.data.aws_ebs_default_kms_key.current_kms_key[0]
module.cc_asg.data.aws_kms_alias.current_kms_arn[0]
module.cc_asg.data.aws_sns_topic.cc_asg_topic_selected[0]
module.cc_asg.aws_autoscaling_attachment.cc_asg_attachment_gwlb[0]
module.cc_asg.aws_autoscaling_attachment.cc_asg_attachment_gwlb[1]
module.cc_asg.aws_autoscaling_group.cc_asg[0]
module.cc_asg.aws_autoscaling_group.cc_asg[1]
module.cc_asg.aws_autoscaling_notification.cc_asg_notifications[0]
module.cc_asg.aws_autoscaling_policy.cc_asg_cpu_utilization_policy[0]
module.cc_asg.aws_autoscaling_policy.cc_asg_cpu_utilization_policy[1]
module.cc_asg.aws_launch_template.cc_launch_template[0]
module.cc_asg.aws_sns_topic.cc_asg_topic[0]
module.cc_asg.aws_sns_topic_subscription.cc_asg_topic_email_subscription[0]
module.cc_iam.data.aws_iam_policy_document.cc_autoscale_lifecycle_policy_document
module.cc_iam.data.aws_iam_policy_document.cc_get_secrets_policy_document
module.cc_iam.data.aws_iam_policy_document.cc_metrics_policy_document
module.cc_iam.data.aws_iam_policy_document.cc_session_manager_policy_document
module.cc_iam.data.aws_iam_policy_document.instance_assume_role_policy
module.cc_iam.data.aws_secretsmanager_secret.cc_secret_name
module.cc_iam.aws_iam_instance_profile.cc_host_profile[0]
module.cc_iam.aws_iam_policy.cc_autoscale_lifecycle_policy[0]
module.cc_iam.aws_iam_policy.cc_get_secrets_policy[0]
module.cc_iam.aws_iam_policy.cc_metrics_policy[0]
module.cc_iam.aws_iam_policy.cc_session_manager_policy[0]
module.cc_iam.aws_iam_role.cc_node_iam_role[0]
module.cc_iam.aws_iam_role_policy_attachment.cc_autoscale_lifecycle_attachment[0]
module.cc_iam.aws_iam_role_policy_attachment.cc_get_secrets_attachment[0]
module.cc_iam.aws_iam_role_policy_attachment.cc_metrics_attachment[0]
module.cc_iam.aws_iam_role_policy_attachment.cc_session_manager_attachment[0]
module.cc_sg.data.aws_vpc.selected
module.cc_sg.aws_security_group.cc_mgmt_sg[0]
module.cc_sg.aws_security_group.cc_service_sg[0]
module.cc_sg.aws_vpc_security_group_egress_rule.egress_cc_mgmt_tcp_443[0]
module.cc_sg.aws_vpc_security_group_egress_rule.egress_cc_mgmt_udp_123[0]
module.cc_sg.aws_vpc_security_group_egress_rule.egress_cc_service_all[0]
module.cc_sg.aws_vpc_security_group_egress_rule.egress_cc_service_geneve[0]
module.cc_sg.aws_vpc_security_group_egress_rule.egress_cc_service_tcp_443[0]
module.cc_sg.aws_vpc_security_group_egress_rule.egress_cc_service_udp_123[0]
module.cc_sg.aws_vpc_security_group_egress_rule.egress_cc_service_udp_443[0]
module.cc_sg.aws_vpc_security_group_ingress_rule.cc_mgmt_ingress_ssh[0]
module.cc_sg.aws_vpc_security_group_ingress_rule.ingress_cc_service_geneve[0]
module.cc_sg.aws_vpc_security_group_ingress_rule.ingress_cc_service_health_check[0]
module.gwlb.aws_lb.gwlb
module.gwlb.aws_lb_listener.gwlb_listener
module.gwlb.aws_lb_target_group.gwlb_target_group
module.gwlb_endpoint.data.aws_caller_identity.current
module.gwlb_endpoint.aws_vpc_endpoint.gwlb_vpce[0]
module.gwlb_endpoint.aws_vpc_endpoint.gwlb_vpce[1]
module.gwlb_endpoint.aws_vpc_endpoint_service.gwlb_vpce_service
module.network.data.aws_availability_zones.available
module.network.data.aws_internet_gateway.igw_selected
module.network.data.aws_nat_gateway.ngw_selected[0]
module.network.data.aws_nat_gateway.ngw_selected[1]
module.network.data.aws_subnet.cc_subnet_selected[0]
module.network.data.aws_subnet.cc_subnet_selected[1]
module.network.aws_eip.eip[0]
module.network.aws_eip.eip[1]
module.network.aws_internet_gateway.igw[0]
module.network.aws_nat_gateway.ngw[0]
module.network.aws_nat_gateway.ngw[1]
module.network.aws_route_table.cc_rt[0]
module.network.aws_route_table.cc_rt[1]
module.network.aws_route_table.public_rt[0]
module.network.aws_route_table.workload_rt[0]
module.network.aws_route_table.workload_rt[1]
module.network.aws_route_table_association.cc_rt_asssociation[0]
module.network.aws_route_table_association.cc_rt_asssociation[1]
module.network.aws_route_table_association.public_rt_association[0]
module.network.aws_route_table_association.public_rt_association[1]
module.network.aws_route_table_association.workload_rt_association[0]
module.network.aws_route_table_association.workload_rt_association[1]
module.network.aws_subnet.cc_subnet[0]
module.network.aws_subnet.cc_subnet[1]
module.network.aws_subnet.public_subnet[0]
module.network.aws_subnet.public_subnet[1]
module.network.aws_subnet.workload_subnet[0]
module.network.aws_subnet.workload_subnet[1]
module.network.aws_vpc.vpc[0]
module.workload.data.aws_ssm_parameter.amazon_linux_latest
module.workload.data.aws_vpc.selected
module.workload.aws_iam_instance_profile.server_host_profile
module.workload.aws_iam_role.node_iam_role
module.workload.aws_iam_role_policy_attachment.ssm_managed_instance_core
module.workload.aws_instance.server_host[0]
module.workload.aws_instance.server_host[1]
module.workload.aws_security_group.node_sg
module.workload.aws_security_group_rule.server_node_ingress_self
module.workload.aws_security_group_rule.server_node_ingress_ssh `
[]Use the Starter Deployment Template with Auto Scaling, GWLB, and ZPA (base_cc_gwlb_asg_zpa) to deploy your Cloud Connector in a new VPC.
To enable Auto Scaling, contact Zscaler Support.
The template creates the following resources:
- VPC
- Cloud Connector subnet
- Public subnet
- Private subnet
- Internet gateway
- NAT gateway
- Key pair for SSH access
- Instance profile with IAM role and required policy permissions (Secrets Manager, Systems Manager [SSM], Workload Tags)
- IAM policy for lifecycle actions
- IAM policy for CloudWatch metrics
- IAM policy for Lambda logs
- CloudWatch EventBridge rules for Lambda
- CloudWatch log group
- Elastic IP address associated with NAT gateway
- Cloud Connector appliance
- Management interface
- Service interface
- Network security group for management interface
- Network security group for service interface
- Gateway Load Balancer
- Listener
- Target group
- VPC endpoint service
- VPC rndpoints
- Linux bastion EC2 with automatic public IP
- Linux bastion IAM role
- Linux bastion security group
- Linux workload EC2 in private subnet
- Linux workload IAM role
- Linux workload security group
- Linux workload route table sending default route next-hop VPC endpoint
- Launch template
- Auto Scaling group
- Lambda function
- Lambda permissions
- (Optional) SNS topic for email alerts
- (Optional) Route 53 outbound endpoints
- (Optional) Route 53 Resolver rules
- (Optional) Route 53 security group
- (Optional) Route 53 subnet
- [See Resource Logs](#tf-resources-gwlb-autoscaling-zpa)
[]
`[0]-[1] indicates default values where two duplicate/like resources (like cloud connectors) would be created
data.aws_ami.cloudconnector
aws_key_pair.deployer
local_file.private_key
local_file.testbed
local_file.user_data_file
random_string.suffix
tls_private_key.key
module.asg_lambda.data.aws_iam_policy_document.lambda_autoscale_lifecycle_policy_document
module.asg_lambda.data.aws_iam_policy_document.lambda_get_secrets_policy_document
module.asg_lambda.data.aws_iam_policy_document.lambda_logs_policy_document
module.asg_lambda.data.aws_iam_policy_document.lambda_metrics_policy_document
module.asg_lambda.data.aws_secretsmanager_secret.lambda_secret_name
module.asg_lambda.aws_cloudwatch_event_rule.asg_cloudwatch_instance_termination_event_rule
module.asg_lambda.aws_cloudwatch_event_rule.asg_cloudwatch_lifecycle_event_rule
module.asg_lambda.aws_cloudwatch_event_rule.asg_cloudwatch_scheduler_event_rule
module.asg_lambda.aws_cloudwatch_event_target.asg_cloudwatch_instance_termination_event_target
module.asg_lambda.aws_cloudwatch_event_target.asg_cloudwatch_lifecycle_event_target
module.asg_lambda.aws_cloudwatch_event_target.asg_cloudwatch_scheduler_event_target
module.asg_lambda.aws_cloudwatch_log_group.asg_cloudwatch_log_group
module.asg_lambda.aws_iam_policy.lambda_autoscale_lifecycle_policy
module.asg_lambda.aws_iam_policy.lambda_get_secrets_policy
module.asg_lambda.aws_iam_policy.lambda_logs_policy
module.asg_lambda.aws_iam_policy.lambda_metrics_policy
module.asg_lambda.aws_iam_role.asg_lambda_iam_role
module.asg_lambda.aws_iam_role_policy_attachment.lambda_autoscale_lifecycle_attachment
module.asg_lambda.aws_iam_role_policy_attachment.lambda_get_secrets_attachment
module.asg_lambda.aws_iam_role_policy_attachment.lambda_logs_attachment
module.asg_lambda.aws_iam_role_policy_attachment.lambda_metrics_attachment
module.asg_lambda.aws_lambda_function.asg_lambda_function
module.asg_lambda.aws_lambda_permission.asg_cloudwatch_instance_termination_permission
module.asg_lambda.aws_lambda_permission.asg_cloudwatch_lifecycle_permission
module.asg_lambda.aws_lambda_permission.asg_cloudwatch_scheduler_event_permission
module.bastion.data.aws_iam_policy_document.bastion_instance_assume_role_policy
module.bastion.data.aws_ssm_parameter.amazon_linux_latest
module.bastion.data.aws_vpc.selected
module.bastion.aws_iam_instance_profile.bastion_host_profile
module.bastion.aws_iam_role.bastion_iam_role
module.bastion.aws_iam_role_policy_attachment.ssm_managed_instance_core
module.bastion.aws_instance.bastion
module.bastion.aws_security_group.bastion
module.bastion.aws_security_group_rule.internet
module.bastion.aws_security_group_rule.intranet
module.bastion.aws_security_group_rule.ssh
module.cc_asg.data.aws_ebs_default_kms_key.current_kms_key[0]
module.cc_asg.data.aws_kms_alias.current_kms_arn[0]
module.cc_asg.data.aws_sns_topic.cc_asg_topic_selected[0]
module.cc_asg.aws_autoscaling_attachment.cc_asg_attachment_gwlb[0]
module.cc_asg.aws_autoscaling_attachment.cc_asg_attachment_gwlb[1]
module.cc_asg.aws_autoscaling_group.cc_asg[0]
module.cc_asg.aws_autoscaling_group.cc_asg[1]
module.cc_asg.aws_autoscaling_notification.cc_asg_notifications[0]
module.cc_asg.aws_autoscaling_policy.cc_asg_cpu_utilization_policy[0]
module.cc_asg.aws_autoscaling_policy.cc_asg_cpu_utilization_policy[1]
module.cc_asg.aws_launch_template.cc_launch_template[0]
module.cc_asg.aws_sns_topic.cc_asg_topic[0]
module.cc_asg.aws_sns_topic_subscription.cc_asg_topic_email_subscription[0]
module.cc_iam.data.aws_iam_policy_document.cc_autoscale_lifecycle_policy_document
module.cc_iam.data.aws_iam_policy_document.cc_get_secrets_policy_document
module.cc_iam.data.aws_iam_policy_document.cc_metrics_policy_document
module.cc_iam.data.aws_iam_policy_document.cc_session_manager_policy_document
module.cc_iam.data.aws_iam_policy_document.instance_assume_role_policy
module.cc_iam.data.aws_secretsmanager_secret.cc_secret_name
module.cc_iam.aws_iam_instance_profile.cc_host_profile[0]
module.cc_iam.aws_iam_policy.cc_autoscale_lifecycle_policy[0]
module.cc_iam.aws_iam_policy.cc_get_secrets_policy[0]
module.cc_iam.aws_iam_policy.cc_metrics_policy[0]
module.cc_iam.aws_iam_policy.cc_session_manager_policy[0]
module.cc_iam.aws_iam_role.cc_node_iam_role[0]
module.cc_iam.aws_iam_role_policy_attachment.cc_autoscale_lifecycle_attachment[0]
module.cc_iam.aws_iam_role_policy_attachment.cc_get_secrets_attachment[0]
module.cc_iam.aws_iam_role_policy_attachment.cc_metrics_attachment[0]
module.cc_iam.aws_iam_role_policy_attachment.cc_session_manager_attachment[0]
module.cc_sg.data.aws_vpc.selected
module.cc_sg.aws_security_group.cc_mgmt_sg[0]
module.cc_sg.aws_security_group.cc_service_sg[0]
module.cc_sg.aws_vpc_security_group_egress_rule.egress_cc_mgmt_tcp_443[0]
module.cc_sg.aws_vpc_security_group_egress_rule.egress_cc_mgmt_udp_123[0]
module.cc_sg.aws_vpc_security_group_egress_rule.egress_cc_service_all[0]
module.cc_sg.aws_vpc_security_group_egress_rule.egress_cc_service_geneve[0]
module.cc_sg.aws_vpc_security_group_egress_rule.egress_cc_service_tcp_443[0]
module.cc_sg.aws_vpc_security_group_egress_rule.egress_cc_service_udp_123[0]
module.cc_sg.aws_vpc_security_group_egress_rule.egress_cc_service_udp_443[0]
module.cc_sg.aws_vpc_security_group_ingress_rule.cc_mgmt_ingress_ssh[0]
module.cc_sg.aws_vpc_security_group_ingress_rule.ingress_cc_service_geneve[0]
module.cc_sg.aws_vpc_security_group_ingress_rule.ingress_cc_service_health_check[0]
module.gwlb.aws_lb.gwlb
module.gwlb.aws_lb_listener.gwlb_listener
module.gwlb.aws_lb_target_group.gwlb_target_group
module.gwlb_endpoint.data.aws_caller_identity.current
module.gwlb_endpoint.aws_vpc_endpoint.gwlb_vpce[0]
module.gwlb_endpoint.aws_vpc_endpoint.gwlb_vpce[1]
module.gwlb_endpoint.aws_vpc_endpoint_service.gwlb_vpce_service
module.network.data.aws_availability_zones.available
module.network.data.aws_internet_gateway.igw_selected
module.network.data.aws_nat_gateway.ngw_selected[0]
module.network.data.aws_nat_gateway.ngw_selected[1]
module.network.data.aws_subnet.cc_subnet_selected[0]
module.network.data.aws_subnet.cc_subnet_selected[1]
module.network.aws_eip.eip[0]
module.network.aws_eip.eip[1]
module.network.aws_internet_gateway.igw[0]
module.network.aws_nat_gateway.ngw[0]
module.network.aws_nat_gateway.ngw[1]
module.network.aws_route_table.cc_rt[0]
module.network.aws_route_table.cc_rt[1]
module.network.aws_route_table.public_rt[0]
module.network.aws_route_table.workload_rt[0]
module.network.aws_route_table.workload_rt[1]
module.network.aws_route_table_association.cc_rt_asssociation[0]
module.network.aws_route_table_association.cc_rt_asssociation[1]
module.network.aws_route_table_association.public_rt_association[0]
module.network.aws_route_table_association.public_rt_association[1]
module.network.aws_route_table_association.workload_rt_association[0]
module.network.aws_route_table_association.workload_rt_association[1]
module.network.aws_subnet.cc_subnet[0]
module.network.aws_subnet.cc_subnet[1]
module.network.aws_subnet.public_subnet[0]
module.network.aws_subnet.public_subnet[1]
module.network.aws_subnet.workload_subnet[0]
module.network.aws_subnet.workload_subnet[1]
module.network.aws_vpc.vpc[0]
module.workload.data.aws_ssm_parameter.amazon_linux_latest
module.workload.data.aws_vpc.selected
module.workload.aws_iam_instance_profile.server_host_profile
module.workload.aws_iam_role.node_iam_role
module.workload.aws_iam_role_policy_attachment.ssm_managed_instance_core
module.workload.aws_instance.server_host[0]
module.workload.aws_instance.server_host[1]
module.workload.aws_security_group.node_sg
module.workload.aws_security_group_rule.server_node_ingress_self
module.workload.aws_security_group_rule.server_node_ingress_ssh
module.route53[0].data.aws_security_group.selected
module.route53[0].aws_route53_resolver_endpoint.zpa_r53_ep
module.route53[0].aws_route53_resolver_rule.fwd_to_cc["appseg1"]
module.route53[0].aws_route53_resolver_rule.system["ZS-FreeBSD"]
module.route53[0].aws_route53_resolver_rule.system["ZS-NTP"]
module.route53[0].aws_route53_resolver_rule.system["ZS-ZPABeta"]
module.route53[0].aws_route53_resolver_rule.system["ZS-ZPAGov"]
module.route53[0].aws_route53_resolver_rule.system["ZS-Zpath"]
module.route53[0].aws_route53_resolver_rule.system["ZS-ZsCloud"]
module.route53[0].aws_route53_resolver_rule.system["ZS-ZsNet"]
module.route53[0].aws_route53_resolver_rule.system["ZS-Zscaler"]
module.route53[0].aws_route53_resolver_rule.system["ZS-ZscalerBeta"]
module.route53[0].aws_route53_resolver_rule.system["ZS-ZscalerGov"]
module.route53[0].aws_route53_resolver_rule.system["ZS-ZscalerOne"]
module.route53[0].aws_route53_resolver_rule.system["ZS-ZscalerThree"]
module.route53[0].aws_route53_resolver_rule.system["ZS-ZscalerTwo"]
module.route53[0].aws_route53_resolver_rule_association.r53_rule_association_system["ZS-FreeBSD"]
module.route53[0].aws_route53_resolver_rule_association.r53_rule_association_system["ZS-NTP"]
module.route53[0].aws_route53_resolver_rule_association.r53_rule_association_system["ZS-ZPABeta"]
module.route53[0].aws_route53_resolver_rule_association.r53_rule_association_system["ZS-ZPAGov"]
module.route53[0].aws_route53_resolver_rule_association.r53_rule_association_system["ZS-Zpath"]
module.route53[0].aws_route53_resolver_rule_association.r53_rule_association_system["ZS-ZsCloud"]
module.route53[0].aws_route53_resolver_rule_association.r53_rule_association_system["ZS-ZsNet"]
module.route53[0].aws_route53_resolver_rule_association.r53_rule_association_system["ZS-Zscaler"]
module.route53[0].aws_route53_resolver_rule_association.r53_rule_association_system["ZS-ZscalerBeta"]
module.route53[0].aws_route53_resolver_rule_association.r53_rule_association_system["ZS-ZscalerGov"]
module.route53[0].aws_route53_resolver_rule_association.r53_rule_association_system["ZS-ZscalerOne"]
module.route53[0].aws_route53_resolver_rule_association.r53_rule_association_system["ZS-ZscalerThree"]
module.route53[0].aws_route53_resolver_rule_association.r53_rule_association_system["ZS-ZscalerTwo"]
module.route53[0].aws_route53_resolver_rule_association.r53_rule_association_to_cc["appseg1"]  `
[]Use the Custom Deployment Template with Gateway Load Balancer (cc_gwlb) to deploy your Cloud Connector in a new or existing VPC. The template creates the following resources:
- VPC
- Cloud Connector subnet
- Public subnet
- Private subnet
- Internet gateway
- NAT gateway
- Key pair for SSH access
- Instance profile with IAM role and required policy permissions (Secrets Manager, Systems Manager [SSM], Workload Tags)
- Elastic IP address associated with NAT gateway
- Cloud Connector appliance
- Management interface
- Service interface
- Network security group for management interface
- Network security group for service interface
- Gateway Load Balancer
- Listener
- Target group
- VPC endpoint service
- VPC endpoints
- (Optional) Route 53 outbound endpoints
- (Optional) Route 53 Resolver rules
- (Optional) Route 53 security group
- (Optional) Route 53 subnet
- [See Resource Logs](#tf-resources-custom-gwlb)
[]
`[0]-[1] indicates default values where two duplicate/like resources (like cloud connectors) would be created
data.aws_ami.cloudconnector
aws_key_pair.deployer
local_file.private_key
local_file.testbed
local_file.user_data_file
random_string.suffix
tls_private_key.key
module.cc_iam.data.aws_secretsmanager_secret.cc_secret_name
module.cc_iam.aws_iam_instance_profile.cc_host_profile[0]
module.cc_iam.aws_iam_instance_profile.cc_host_profile[1]
module.cc_iam.aws_iam_instance_profile.cc_host_profile[2]
module.cc_iam.aws_iam_instance_profile.cc_host_profile[3]
module.cc_iam.aws_iam_policy.cc_get_secrets_policy[0]
module.cc_iam.aws_iam_policy.cc_get_secrets_policy[1]
module.cc_iam.aws_iam_policy.cc_get_secrets_policy[2]
module.cc_iam.aws_iam_policy.cc_get_secrets_policy[3]
module.cc_iam.aws_iam_policy.cc_metrics_policy[0]
module.cc_iam.aws_iam_policy.cc_metrics_policy[1]
module.cc_iam.aws_iam_policy.cc_metrics_policy[2]
module.cc_iam.aws_iam_policy.cc_metrics_policy[3]
module.cc_iam.aws_iam_policy.cc_session_manager_policy[0]
module.cc_iam.aws_iam_policy.cc_session_manager_policy[1]
module.cc_iam.aws_iam_policy.cc_session_manager_policy[2]
module.cc_iam.aws_iam_policy.cc_session_manager_policy[3]
module.cc_iam.aws_iam_role.cc_node_iam_role[0]
module.cc_iam.aws_iam_role.cc_node_iam_role[1]
module.cc_iam.aws_iam_role.cc_node_iam_role[2]
module.cc_iam.aws_iam_role.cc_node_iam_role[3]
module.cc_iam.aws_iam_role_policy_attachment.cc_get_secrets_attachment[0]
module.cc_iam.aws_iam_role_policy_attachment.cc_get_secrets_attachment[1]
module.cc_iam.aws_iam_role_policy_attachment.cc_get_secrets_attachment[2]
module.cc_iam.aws_iam_role_policy_attachment.cc_get_secrets_attachment[3]
module.cc_iam.aws_iam_role_policy_attachment.cc_metrics_attachment[0]
module.cc_iam.aws_iam_role_policy_attachment.cc_metrics_attachment[1]
module.cc_iam.aws_iam_role_policy_attachment.cc_metrics_attachment[2]
module.cc_iam.aws_iam_role_policy_attachment.cc_metrics_attachment[3]
module.cc_iam.aws_iam_role_policy_attachment.cc_session_manager_attachment[0]
module.cc_iam.aws_iam_role_policy_attachment.cc_session_manager_attachment[1]
module.cc_iam.aws_iam_role_policy_attachment.cc_session_manager_attachment[2]
module.cc_iam.aws_iam_role_policy_attachment.cc_session_manager_attachment[3]
module.cc_sg.data.aws_vpc.selected
module.cc_sg.aws_security_group.cc_mgmt_sg[0]
module.cc_sg.aws_security_group.cc_mgmt_sg[1]
module.cc_sg.aws_security_group.cc_mgmt_sg[2]
module.cc_sg.aws_security_group.cc_mgmt_sg[3]
module.cc_sg.aws_security_group.cc_service_sg[0]
module.cc_sg.aws_security_group.cc_service_sg[1]
module.cc_sg.aws_security_group.cc_service_sg[2]
module.cc_sg.aws_security_group.cc_service_sg[3]
module.cc_sg.aws_vpc_security_group_egress_rule.egress_cc_mgmt_tcp_12002[0]
module.cc_sg.aws_vpc_security_group_egress_rule.egress_cc_mgmt_tcp_12002[1]
module.cc_sg.aws_vpc_security_group_egress_rule.egress_cc_mgmt_tcp_12002[2]
module.cc_sg.aws_vpc_security_group_egress_rule.egress_cc_mgmt_tcp_12002[3]
module.cc_sg.aws_vpc_security_group_egress_rule.egress_cc_mgmt_tcp_443[0]
module.cc_sg.aws_vpc_security_group_egress_rule.egress_cc_mgmt_tcp_443[1]
module.cc_sg.aws_vpc_security_group_egress_rule.egress_cc_mgmt_tcp_443[2]
module.cc_sg.aws_vpc_security_group_egress_rule.egress_cc_mgmt_tcp_443[3]
module.cc_sg.aws_vpc_security_group_egress_rule.egress_cc_mgmt_udp_123[0]
module.cc_sg.aws_vpc_security_group_egress_rule.egress_cc_mgmt_udp_123[1]
module.cc_sg.aws_vpc_security_group_egress_rule.egress_cc_mgmt_udp_123[2]
module.cc_sg.aws_vpc_security_group_egress_rule.egress_cc_mgmt_udp_123[3]
module.cc_sg.aws_vpc_security_group_egress_rule.egress_cc_service_all[0]
module.cc_sg.aws_vpc_security_group_egress_rule.egress_cc_service_all[1]
module.cc_sg.aws_vpc_security_group_egress_rule.egress_cc_service_all[2]
module.cc_sg.aws_vpc_security_group_egress_rule.egress_cc_service_all[3]
module.cc_sg.aws_vpc_security_group_egress_rule.egress_cc_service_geneve[0]
module.cc_sg.aws_vpc_security_group_egress_rule.egress_cc_service_geneve[1]
module.cc_sg.aws_vpc_security_group_egress_rule.egress_cc_service_geneve[2]
module.cc_sg.aws_vpc_security_group_egress_rule.egress_cc_service_geneve[3]
module.cc_sg.aws_vpc_security_group_egress_rule.egress_cc_service_tcp_443[0]
module.cc_sg.aws_vpc_security_group_egress_rule.egress_cc_service_tcp_443[1]
module.cc_sg.aws_vpc_security_group_egress_rule.egress_cc_service_tcp_443[2]
module.cc_sg.aws_vpc_security_group_egress_rule.egress_cc_service_tcp_443[3]
module.cc_sg.aws_vpc_security_group_egress_rule.egress_cc_service_udp_123[0]
module.cc_sg.aws_vpc_security_group_egress_rule.egress_cc_service_udp_123[1]
module.cc_sg.aws_vpc_security_group_egress_rule.egress_cc_service_udp_123[2]
module.cc_sg.aws_vpc_security_group_egress_rule.egress_cc_service_udp_123[3]
module.cc_sg.aws_vpc_security_group_egress_rule.egress_cc_service_udp_443[0]
module.cc_sg.aws_vpc_security_group_egress_rule.egress_cc_service_udp_443[1]
module.cc_sg.aws_vpc_security_group_egress_rule.egress_cc_service_udp_443[2]
module.cc_sg.aws_vpc_security_group_egress_rule.egress_cc_service_udp_443[3]
module.cc_sg.aws_vpc_security_group_ingress_rule.cc_mgmt_ingress_ssh[0]
module.cc_sg.aws_vpc_security_group_ingress_rule.cc_mgmt_ingress_ssh[1]
module.cc_sg.aws_vpc_security_group_ingress_rule.cc_mgmt_ingress_ssh[2]
module.cc_sg.aws_vpc_security_group_ingress_rule.cc_mgmt_ingress_ssh[3]
module.cc_sg.aws_vpc_security_group_ingress_rule.ingress_cc_service_all[0]
module.cc_sg.aws_vpc_security_group_ingress_rule.ingress_cc_service_all[1]
module.cc_sg.aws_vpc_security_group_ingress_rule.ingress_cc_service_all[2]
module.cc_sg.aws_vpc_security_group_ingress_rule.ingress_cc_service_all[3]
module.cc_sg.aws_vpc_security_group_ingress_rule.ingress_cc_service_geneve[0]
module.cc_sg.aws_vpc_security_group_ingress_rule.ingress_cc_service_geneve[1]
module.cc_sg.aws_vpc_security_group_ingress_rule.ingress_cc_service_geneve[2]
module.cc_sg.aws_vpc_security_group_ingress_rule.ingress_cc_service_geneve[3]
module.cc_sg.aws_vpc_security_group_ingress_rule.ingress_cc_service_health_check[0]
module.cc_sg.aws_vpc_security_group_ingress_rule.ingress_cc_service_health_check[1]
module.cc_sg.aws_vpc_security_group_ingress_rule.ingress_cc_service_health_check[2]
module.cc_sg.aws_vpc_security_group_ingress_rule.ingress_cc_service_health_check[3]
module.cc_sg.aws_vpc_security_group_ingress_rule.ingress_cc_service_https_local[0]
module.cc_sg.aws_vpc_security_group_ingress_rule.ingress_cc_service_https_local[1]
module.cc_sg.aws_vpc_security_group_ingress_rule.ingress_cc_service_https_local[2]
module.cc_sg.aws_vpc_security_group_ingress_rule.ingress_cc_service_https_local[3]
module.cc_vm.data.aws_ebs_default_kms_key.current_kms_key[0]
module.cc_vm.data.aws_kms_alias.current_kms_arn[0]
module.cc_vm.aws_instance.cc_vm[0]
module.cc_vm.aws_instance.cc_vm[1]
module.cc_vm.aws_instance.cc_vm[2]
module.cc_vm.aws_instance.cc_vm[3]
module.cc_vm.aws_network_interface.cc_vm_nic_index_0[0]
module.cc_vm.aws_network_interface.cc_vm_nic_index_0[1]
module.cc_vm.aws_network_interface.cc_vm_nic_index_0[2]
module.cc_vm.aws_network_interface.cc_vm_nic_index_0[3]
module.cc_vm.aws_network_interface.cc_vm_nic_index_1[0]
module.cc_vm.aws_network_interface.cc_vm_nic_index_1[1]
module.cc_vm.aws_network_interface.cc_vm_nic_index_1[2]
module.cc_vm.aws_network_interface.cc_vm_nic_index_1[3]
module.gwlb.aws_lb.gwlb
module.gwlb.aws_lb_listener.gwlb_listener
module.gwlb.aws_lb_target_group.gwlb_target_group
module.gwlb.aws_lb_target_group_attachment.gwlb_target_group_attachment[0]
module.gwlb.aws_lb_target_group_attachment.gwlb_target_group_attachment[1]
module.gwlb.aws_lb_target_group_attachment.gwlb_target_group_attachment[2]
module.gwlb.aws_lb_target_group_attachment.gwlb_target_group_attachment[3]
module.gwlb_endpoint.data.aws_caller_identity.current
module.gwlb_endpoint.data.aws_partition.current
module.gwlb_endpoint.aws_vpc_endpoint.gwlb_vpce[0]
module.gwlb_endpoint.aws_vpc_endpoint.gwlb_vpce[1]
module.gwlb_endpoint.aws_vpc_endpoint_service.gwlb_vpce_service[0]
module.network.data.aws_availability_zones.available
module.network.data.aws_internet_gateway.igw_selected
module.network.data.aws_nat_gateway.ngw_selected[0]
module.network.data.aws_nat_gateway.ngw_selected[1]
module.network.data.aws_subnet.cc_subnet_selected[0]
module.network.data.aws_subnet.cc_subnet_selected[1]
module.network.aws_eip.eip[0]
module.network.aws_eip.eip[1]
module.network.aws_internet_gateway.igw[0]
module.network.aws_nat_gateway.ngw[0]
module.network.aws_nat_gateway.ngw[1]
module.network.aws_route_table.cc_rt[0]
module.network.aws_route_table.cc_rt[1]
module.network.aws_route_table.public_rt[0]
module.network.aws_route_table_association.cc_rt_asssociation[0]
module.network.aws_route_table_association.cc_rt_asssociation[1]
module.network.aws_route_table_association.public_rt_association[0]
module.network.aws_route_table_association.public_rt_association[1]
module.network.aws_subnet.cc_subnet[0]
module.network.aws_subnet.cc_subnet[1]
module.network.aws_subnet.public_subnet[0]
module.network.aws_subnet.public_subnet[1]
module.network.aws_vpc.vpc[0]`
[]Use the Custom Deployment Template with Auto Scaling and Gateway Load Balancer (cc_gwlb_asg) to deploy your Cloud Connector in a new or existing VPC.
To enable Auto Scaling, contact Zscaler Support.
The template creates the following resources:
- VPC
- Cloud Connector subnet
- Public subnet
- Private subnet
- Internet gateway
- NAT gateway
- Key pair for SSH access
- Instance profile with IAM role and required policy permissions (Secrets Manager, Systems Manager [SSM], Workload Tags)
- IAM policy for lifecycle actions
- IAM policy for CloudWatch metrics
- IAM policy for Lambda logs
- CloudWatch EventBridge rules for Lambda
- CloudWatch log group
- Elastic IP address associated with NAT gateway
- Cloud Connector appliance
- Management interface
- Service interface
- Network security group for management interface
- Network security group for service interface
- Gateway Load Balancer
- Listener
- Target group
- VPC endpoint service
- VPC endpoints
- Launch template
- Auto Scaling group
- Lambda function
- Lambda permissions
- (Optional) SNS topic for email alerts
- (Optional) Route 53 outbound endpoints
- (Optional) Route 53 Resolver rules
- (Optional) Route 53 security group
- (Optional) Route 53 subnet
- [See Resource Logs](#tf-resources-custom-gwlb-autoscaling)
[]
`[0]-[1] indicates default values where two duplicate/like resources (like cloud connectors) would be created
data.aws_ami.cloudconnector
aws_key_pair.deployer
local_file.private_key
local_file.testbed
local_file.user_data_file
random_string.suffix
tls_private_key.key
module.asg_lambda.data.aws_iam_policy_document.lambda_autoscale_lifecycle_policy_document
module.asg_lambda.data.aws_iam_policy_document.lambda_get_secrets_policy_document
module.asg_lambda.data.aws_iam_policy_document.lambda_logs_policy_document
module.asg_lambda.data.aws_iam_policy_document.lambda_metrics_policy_document
module.asg_lambda.data.aws_secretsmanager_secret.lambda_secret_name
module.asg_lambda.aws_cloudwatch_event_rule.asg_cloudwatch_instance_termination_event_rule
module.asg_lambda.aws_cloudwatch_event_rule.asg_cloudwatch_lifecycle_event_rule
module.asg_lambda.aws_cloudwatch_event_rule.asg_cloudwatch_scheduler_event_rule
module.asg_lambda.aws_cloudwatch_event_target.asg_cloudwatch_instance_termination_event_target
module.asg_lambda.aws_cloudwatch_event_target.asg_cloudwatch_lifecycle_event_target
module.asg_lambda.aws_cloudwatch_event_target.asg_cloudwatch_scheduler_event_target
module.asg_lambda.aws_cloudwatch_log_group.asg_cloudwatch_log_group
module.asg_lambda.aws_iam_policy.lambda_autoscale_lifecycle_policy
module.asg_lambda.aws_iam_policy.lambda_get_secrets_policy
module.asg_lambda.aws_iam_policy.lambda_logs_policy
module.asg_lambda.aws_iam_policy.lambda_metrics_policy
module.asg_lambda.aws_iam_role.asg_lambda_iam_role
module.asg_lambda.aws_iam_role_policy_attachment.lambda_autoscale_lifecycle_attachment
module.asg_lambda.aws_iam_role_policy_attachment.lambda_get_secrets_attachment
module.asg_lambda.aws_iam_role_policy_attachment.lambda_logs_attachment
module.asg_lambda.aws_iam_role_policy_attachment.lambda_metrics_attachment
module.asg_lambda.aws_lambda_function.asg_lambda_function
module.asg_lambda.aws_lambda_permission.asg_cloudwatch_instance_termination_permission
module.asg_lambda.aws_lambda_permission.asg_cloudwatch_lifecycle_permission
module.asg_lambda.aws_lambda_permission.asg_cloudwatch_scheduler_event_permission
module.cc_asg.data.aws_ebs_default_kms_key.current_kms_key[0]
module.cc_asg.data.aws_kms_alias.current_kms_arn[0]
module.cc_asg.data.aws_sns_topic.cc_asg_topic_selected[0]
module.cc_asg.aws_autoscaling_attachment.cc_asg_attachment_gwlb[0]
module.cc_asg.aws_autoscaling_attachment.cc_asg_attachment_gwlb[1]
module.cc_asg.aws_autoscaling_group.cc_asg[0]
module.cc_asg.aws_autoscaling_group.cc_asg[1]
module.cc_asg.aws_autoscaling_notification.cc_asg_notifications[0]
module.cc_asg.aws_autoscaling_policy.cc_asg_cpu_utilization_policy[0]
module.cc_asg.aws_autoscaling_policy.cc_asg_cpu_utilization_policy[1]
module.cc_asg.aws_launch_template.cc_launch_template[0]
module.cc_asg.aws_sns_topic.cc_asg_topic[0]
module.cc_asg.aws_sns_topic_subscription.cc_asg_topic_email_subscription[0]
module.cc_iam.data.aws_iam_policy_document.cc_autoscale_lifecycle_policy_document
module.cc_iam.data.aws_iam_policy_document.cc_get_secrets_policy_document
module.cc_iam.data.aws_iam_policy_document.cc_metrics_policy_document
module.cc_iam.data.aws_iam_policy_document.cc_session_manager_policy_document
module.cc_iam.data.aws_iam_policy_document.instance_assume_role_policy
module.cc_iam.data.aws_secretsmanager_secret.cc_secret_name
module.cc_iam.aws_iam_instance_profile.cc_host_profile[0]
module.cc_iam.aws_iam_policy.cc_autoscale_lifecycle_policy[0]
module.cc_iam.aws_iam_policy.cc_get_secrets_policy[0]
module.cc_iam.aws_iam_policy.cc_metrics_policy[0]
module.cc_iam.aws_iam_policy.cc_session_manager_policy[0]
module.cc_iam.aws_iam_role.cc_node_iam_role[0]
module.cc_iam.aws_iam_role_policy_attachment.cc_autoscale_lifecycle_attachment[0]
module.cc_iam.aws_iam_role_policy_attachment.cc_get_secrets_attachment[0]
module.cc_iam.aws_iam_role_policy_attachment.cc_metrics_attachment[0]
module.cc_iam.aws_iam_role_policy_attachment.cc_session_manager_attachment[0]
module.cc_sg.data.aws_vpc.selected
module.cc_sg.aws_security_group.cc_mgmt_sg[0]
module.cc_sg.aws_security_group.cc_service_sg[0]
module.cc_sg.aws_vpc_security_group_egress_rule.egress_cc_mgmt_tcp_443[0]
module.cc_sg.aws_vpc_security_group_egress_rule.egress_cc_mgmt_udp_123[0]
module.cc_sg.aws_vpc_security_group_egress_rule.egress_cc_service_all[0]
module.cc_sg.aws_vpc_security_group_egress_rule.egress_cc_service_geneve[0]
module.cc_sg.aws_vpc_security_group_egress_rule.egress_cc_service_tcp_443[0]
module.cc_sg.aws_vpc_security_group_egress_rule.egress_cc_service_udp_123[0]
module.cc_sg.aws_vpc_security_group_egress_rule.egress_cc_service_udp_443[0]
module.cc_sg.aws_vpc_security_group_ingress_rule.cc_mgmt_ingress_ssh[0]
module.cc_sg.aws_vpc_security_group_ingress_rule.ingress_cc_service_geneve[0]
module.cc_sg.aws_vpc_security_group_ingress_rule.ingress_cc_service_health_check[0]
module.gwlb.aws_lb.gwlb
module.gwlb.aws_lb_listener.gwlb_listener
module.gwlb.aws_lb_target_group.gwlb_target_group
module.gwlb_endpoint.data.aws_caller_identity.current
module.gwlb_endpoint.aws_vpc_endpoint.gwlb_vpce[0]
module.gwlb_endpoint.aws_vpc_endpoint.gwlb_vpce[1]
module.gwlb_endpoint.aws_vpc_endpoint_service.gwlb_vpce_service
module.network.data.aws_availability_zones.available
module.network.data.aws_internet_gateway.igw_selected
module.network.data.aws_nat_gateway.ngw_selected[0]
module.network.data.aws_nat_gateway.ngw_selected[1]
module.network.data.aws_subnet.cc_subnet_selected[0]
module.network.data.aws_subnet.cc_subnet_selected[1]
module.network.aws_eip.eip[0]
module.network.aws_eip.eip[1]
module.network.aws_internet_gateway.igw[0]
module.network.aws_nat_gateway.ngw[0]
module.network.aws_nat_gateway.ngw[1]
module.network.aws_route_table.cc_rt[0]
module.network.aws_route_table.cc_rt[1]
module.network.aws_route_table.public_rt[0]
module.network.aws_route_table_association.cc_rt_asssociation[0]
module.network.aws_route_table_association.cc_rt_asssociation[1]
module.network.aws_route_table_association.public_rt_association[0]
module.network.aws_route_table_association.public_rt_association[1]
module.network.aws_subnet.cc_subnet[0]
module.network.aws_subnet.cc_subnet[1]
module.network.aws_subnet.public_subnet[0]
module.network.aws_subnet.public_subnet[1]
module.network.aws_vpc.vpc[0]
module.route53[0].data.aws_security_group.selected
module.route53[0].aws_route53_resolver_endpoint.zpa_r53_ep
module.route53[0].aws_route53_resolver_rule.fwd_to_cc["appseg1"]
module.route53[0].aws_route53_resolver_rule.system["ZS-FreeBSD"]
module.route53[0].aws_route53_resolver_rule.system["ZS-NTP"]
module.route53[0].aws_route53_resolver_rule.system["ZS-ZPABeta"]
module.route53[0].aws_route53_resolver_rule.system["ZS-ZPAGov"]
module.route53[0].aws_route53_resolver_rule.system["ZS-Zpath"]
module.route53[0].aws_route53_resolver_rule.system["ZS-ZsCloud"]
module.route53[0].aws_route53_resolver_rule.system["ZS-ZsNet"]
module.route53[0].aws_route53_resolver_rule.system["ZS-Zscaler"]
module.route53[0].aws_route53_resolver_rule.system["ZS-ZscalerBeta"]
module.route53[0].aws_route53_resolver_rule.system["ZS-ZscalerGov"]
module.route53[0].aws_route53_resolver_rule.system["ZS-ZscalerOne"]
module.route53[0].aws_route53_resolver_rule.system["ZS-ZscalerThree"]
module.route53[0].aws_route53_resolver_rule.system["ZS-ZscalerTwo"]
module.route53[0].aws_route53_resolver_rule_association.r53_rule_association_system["ZS-FreeBSD"]
module.route53[0].aws_route53_resolver_rule_association.r53_rule_association_system["ZS-NTP"]
module.route53[0].aws_route53_resolver_rule_association.r53_rule_association_system["ZS-ZPABeta"]
module.route53[0].aws_route53_resolver_rule_association.r53_rule_association_system["ZS-ZPAGov"]
module.route53[0].aws_route53_resolver_rule_association.r53_rule_association_system["ZS-Zpath"]
module.route53[0].aws_route53_resolver_rule_association.r53_rule_association_system["ZS-ZsCloud"]
module.route53[0].aws_route53_resolver_rule_association.r53_rule_association_system["ZS-ZsNet"]
module.route53[0].aws_route53_resolver_rule_association.r53_rule_association_system["ZS-Zscaler"]
module.route53[0].aws_route53_resolver_rule_association.r53_rule_association_system["ZS-ZscalerBeta"]
module.route53[0].aws_route53_resolver_rule_association.r53_rule_association_system["ZS-ZscalerGov"]
module.route53[0].aws_route53_resolver_rule_association.r53_rule_association_system["ZS-ZscalerOne"]
module.route53[0].aws_route53_resolver_rule_association.r53_rule_association_system["ZS-ZscalerThree"]
module.route53[0].aws_route53_resolver_rule_association.r53_rule_association_system["ZS-ZscalerTwo"]
module.route53[0].aws_route53_resolver_rule_association.r53_rule_association_to_cc["appseg1"]`
Azure Deployment Templates
This section describes the resources created when deploying Cloud Connector using a Terraform script. To learn more about deploying Cloud Connector in the Azure Marketplace, refer to [Deploying Zscaler Cloud Connector with Microsoft Azure](https://help.zscaler.com/unified/deploying-zscaler-cloud-connector-microsoft-azure).
Use the templates in the [Terraform](https://github.com/zscaler/terraform-azurerm-cloud-connector-modules) repository to create the deployment resources required to deploy and operate Cloud Connector in a new or existing VPC.
- [Basic Deployment Templates](#t-templates-azure)
- [Deployment Templates with Load Balancer](#t-templates-azure-lb)
- [Deployment Templates with Virtual Machine Scale Sets (VMSS)](#t-templates-azure-vmss)
[]
- [Starter Deployment Template](#t-azure-template)
- [Starter Deployment Template with ZPA](#t-azure-template-ZPA)
[]
- [Starter Deployment Template with Load Balancer](#t-azure-template4)
- [Starter Deployment Template with Load Balancer and ZPA](#t-azure-template-LB-ZPA)
- [Custom Deployment Template with Load Balancer](#t-azure-template5)
[]
- [Starter Deployment Template with VMSS and Load Balancer](#t-azure-template-VMSS1)
- [Starter Deployment Template with VMSS, Load Balancer, and ZPA](#t-azure-template-VMSS2)
- [Custom Deployment Template with VMSS and Load Balancer](#t-azure-template-VMSS3)
[]Use the Starter Deployment Template (base_1cc) to deploy your Cloud Connector in a new resource group and virtual network. The template creates the following resources:
- Resource group
- Cloud Connector subnet
- Ubuntu server bastion host
- Route tables for routing the workload traffic through the Cloud Connector
- Virtual network
- Bastion subnet
- Workload subnet
- Ubuntu server workload
- Public IP address for bastion host
- Local key pair for SSH access
- Cloud Connector VM
- Management interface
- Service interface
- Network security group for management interface
- Network security group for service interface
- NAT gateway
- Public IP address associated with NAT gateway
- [See Resource Logs](#tf-azure3)
[]
`azurerm_nat_gateway.nat-gw1 will be created
azurerm_nat_gateway_public_ip_association.nat-gw-association1 will be created
azurerm_public_ip.nat-pip will be created
azurerm_resource_group.main will be created
azurerm_route_table.server-rt1[0] will be created
azurerm_subnet.bastion-subnet[0] will be created
azurerm_subnet.cc-subnet will be created
azurerm_subnet.server-subnet[0] will be created
azurerm_subnet_nat_gateway_association.subnet-nat-association-ec will be created
azurerm_subnet_route_table_association.server-rt-assoc[0] will be created
azurerm_virtual_network.vnet1 will be created
local_file.testbed will be created
local_file.user-data-file will be created
null_resource.save-key will be created
random_string.suffix will be created
tls_private_key.key will be created
module.bastion.azurerm_linux_virtual_machine.bastion-vm will be created
module.bastion.azurerm_network_interface.bastion-nic will be created
module.bastion.azurerm_network_interface_security_group_association.bastion-nic-association will be created
module.bastion.azurerm_network_security_group.bastion-nsg will be created
module.bastion.azurerm_public_ip.bastion-pip will be created
module.cc-vm1.azurerm_linux_virtual_machine.cc-vm will be created
module.cc-vm1.azurerm_network_interface.cc-mgmt-nic will be created
module.cc-vm1.azurerm_network_interface.cc-service-nic will be created
module.cc-vm1.azurerm_network_interface_security_group_association.ec-mgmt-nic-association will be created
module.cc-vm1.azurerm_network_interface_security_group_association.ec-service-nic-association will be created
module.cc-vm1.azurerm_network_security_group.cc-nsg will be created
module.cc-vm1.azurerm_network_security_group.cc-service-nsg will be created
module.workload1.azurerm_linux_virtual_machine.server-vm[0] will be created
module.workload1.azurerm_network_interface.server-nic[0] will be created
module.workload1.azurerm_network_interface_security_group_association.server-nic-association[0] will be created
module.workload1.azurerm_network_security_group.server-nsg will be created`
[]
[]Use the Starter Deployment Template with ZPA (base_1cc_zpa) to deploy your Cloud Connector in a new resource group and virtual network. The template creates the following resources:
- Resource group
- Virtual network
- Cloud Connector subnet
- Bastion subnet
- Workload subnet
- NAT gateway
- Public IP Address associated with NAT gateway
- CentOS server workload
- Route tables for routing the workload traffic through the Cloud Connector
- Network security group for workload
- CentOS server bastion host
- Public IP address for bastion host
- Network security group for bastion host
- Cloud Connector VM
- Management interface
- Service interface network
- Network security group for management interface
- Network security group for service interface
- Local key pair for SSH access
- Azure private DNS Resolver virtual network link
- Azure private DNS subnet
- Azure private DNS Resolver
- Azure private DNS Resolver forwarding ruleset
- Azure private DNS Resolver outbound endpoint
- [See Resource Logs](#tf-azure-ZPA)
[]
`azurerm_private_dns_resolver_virtual_network_link.dns_vnet_link
local_file.private_key
local_file.testbed
local_file.user_data_file
random_string.suffix
tls_private_key.key
module.bastion.azurerm_linux_virtual_machine.bastion_vm
module.bastion.azurerm_network_interface.bastion_nic
module.bastion.azurerm_network_interface_security_group_association.bastion_nic_association
module.bastion.azurerm_network_security_group.bastion_nsg
module.bastion.azurerm_public_ip.bastion_pip
module.cc_identity.data.azurerm_user_assigned_identity.selected
module.cc_nsg.azurerm_network_security_group.cc_mgmt_nsg[0]
module.cc_nsg.azurerm_network_security_group.cc_service_nsg[0]
module.cc_vm.azurerm_availability_set.cc_availability_set[0]
module.cc_vm.azurerm_linux_virtual_machine.cc_vm[0]
module.cc_vm.azurerm_linux_virtual_machine.cc_vm[1]
module.cc_vm.azurerm_network_interface.cc_mgmt_nic[0]
module.cc_vm.azurerm_network_interface.cc_mgmt_nic[1]
module.cc_vm.azurerm_network_interface.cc_service_nic[0]
module.cc_vm.azurerm_network_interface.cc_service_nic[1]
module.cc_vm.azurerm_network_interface_security_group_association.cc_mgmt_nic_association[0]
module.cc_vm.azurerm_network_interface_security_group_association.cc_mgmt_nic_association[1]
module.cc_vm.azurerm_network_interface_security_group_association.cc_service_nic_association[0]
module.cc_vm.azurerm_network_interface_security_group_association.cc_service_nic_association[1]
module.network.data.azurerm_subnet.cc_subnet_selected[0]
module.network.azurerm_nat_gateway.ngw[0]
module.network.azurerm_nat_gateway_public_ip_association.ngw_association[0]
module.network.azurerm_public_ip.pip[0]
module.network.azurerm_resource_group.rg[0]
module.network.azurerm_route_table.private_dns_rt[0]
module.network.azurerm_route_table.workload_rt[0]
module.network.azurerm_subnet.bastion_subnet[0]
module.network.azurerm_subnet.cc_subnet[0]
module.network.azurerm_subnet.private_dns_subnet[0]
module.network.azurerm_subnet.workload_subnet[0]
module.network.azurerm_subnet_nat_gateway_association.cc_subnet_nat_association[0]
module.network.azurerm_subnet_route_table_association.private_dns_rt_association[0]
module.network.azurerm_subnet_route_table_association.workload_rt_association[0]
module.network.azurerm_virtual_network.vnet[0]
module.private_dns.azurerm_private_dns_resolver.dns_resolver
module.private_dns.azurerm_private_dns_resolver_dns_forwarding_ruleset.dns_forwarding_ruleset
module.private_dns.azurerm_private_dns_resolver_forwarding_rule.dns_forwarding_rule["appseg1"]
module.private_dns.azurerm_private_dns_resolver_forwarding_rule.dns_forwarding_rule["appseg2"]
module.private_dns.azurerm_private_dns_resolver_outbound_endpoint.dns_outbound_endpoint
module.workload.azurerm_linux_virtual_machine.workload_vm[0]
module.workload.azurerm_network_interface.workload_nic[0]
module.workload.azurerm_network_interface_security_group_association.workload_nic_association[0]
module.workload.azurerm_network_security_group.workload_nsg[0]`
[]Use the Starter Deployment Template with Load Balancer (base_cc_lb) to deploy your Cloud Connectors in a new resource group and virtual network. The template creates the following resources:
- Resource group
- Cloud Connector subnet
- Ubuntu server bastion host
- Route tables for routing the workload traffic through the Cloud Connector
- Virtual network
- Bastion subnet
- Workload subnet
- Ubuntu server workload
- Public IP address for bastion host
- Local key pair for SSH access
- Two Cloud Connector VMs
- Management interface
- Service interface
- Network security group for management interface
- Network security group for service interface
- NAT gateway
- Public IP address associated with NAT gateway
- Azure Load Balancer to monitor events triggering a failover
- [See Resource Logs](#tf-azure4)
[]
`azurerm_nat_gateway.nat-gw1 will be created
azurerm_nat_gateway_public_ip_association.nat-gw-association1 will be created
azurerm_public_ip.nat-pip will be created
azurerm_resource_group.main will be created
azurerm_route_table.server-rt1[0] will be created
azurerm_subnet.bastion-subnet[0] will be created
azurerm_subnet.cc-subnet will be created
azurerm_subnet.server-subnet[0] will be created
azurerm_subnet_nat_gateway_association.subnet-nat-association-ec will be created
azurerm_subnet_route_table_association.server-rt-assoc[0] will be created
azurerm_virtual_network.vnet1 will be created
local_file.testbed will be created
local_file.user-data-file will be created
null_resource.save-key will be created
random_string.suffix will be created
tls_private_key.key will be created
module.bastion.azurerm_linux_virtual_machine.bastion-vm will be created
module.bastion.azurerm_network_interface.bastion-nic will be created
module.bastion.azurerm_network_interface_security_group_association.bastion-nic-association will be created
module.bastion.azurerm_network_security_group.bastion-nsg will be created
module.bastion.azurerm_public_ip.bastion-pip will be created
module.cc-vm.azurerm_availability_set.cc-availability-set will be created
module.cc-vm.azurerm_lb.cc-lb will be created
module.cc-vm.azurerm_lb_backend_address_pool.cc-lb-backend-pool will be created
module.cc-vm.azurerm_lb_probe.cc-lb-probe will be created
module.cc-vm.azurerm_lb_rule.cc-lb-rule will be created
module.cc-vm.azurerm_linux_virtual_machine.cc-vm[0] will be created
module.cc-vm.azurerm_linux_virtual_machine.cc-vm[1] will be created
module.cc-vm.azurerm_network_interface.cc-mgmt-nic[0] will be created
module.cc-vm.azurerm_network_interface.cc-mgmt-nic[1] will be created
module.cc-vm.azurerm_network_interface.cc-service-nic[0] will be created
module.cc-vm.azurerm_network_interface.cc-service-nic[1] will be created
module.cc-vm.azurerm_network_interface_backend_address_pool_association.cc-vm-service-nic-lb-association[0] will be created
module.cc-vm.azurerm_network_interface_backend_address_pool_association.cc-vm-service-nic-lb-association[1] will be created
module.cc-vm.azurerm_network_interface_security_group_association.ec-mgmt-nic-association[0] will be created
module.cc-vm.azurerm_network_interface_security_group_association.ec-mgmt-nic-association[1] will be created
module.cc-vm.azurerm_network_interface_security_group_association.ec-service-nic-association[0] will be created
module.cc-vm.azurerm_network_interface_security_group_association.ec-service-nic-association[1] will be created
module.cc-vm.azurerm_network_security_group.cc-nsg will be created
module.cc-vm.azurerm_network_security_group.cc-service-nsg will be created
module.workload1.azurerm_linux_virtual_machine.server-vm[0] will be created
module.workload1.azurerm_linux_virtual_machine.server-vm[1] will be created
module.workload1.azurerm_network_interface.server-nic[0] will be created
module.workload1.azurerm_network_interface.server-nic[1] will be created
module.workload1.azurerm_network_interface_security_group_association.server-nic-association[0] will be created
module.workload1.azurerm_network_interface_security_group_association.server-nic-association[1] will be created
module.workload1.azurerm_network_security_group.server-nsg will be created`
[]Use the Starter Deployment Template with Load Balancer and ZPA (base_cc_lb_zpa) to deploy your Cloud Connectors in a new resource group and virtual network. The template creates the following resources:
- Resource group
- Virtual network
- Cloud Connector subnet
- Bastion subnet
- Workload subnet
- NAT gateway
- Public IP address associated with NAT gateway
- CentOS server workload
- Route tables for routing the workload traffic through the Cloud Connector
- Network security group for workload
- CentOS server bastion host
- Public IP address for bastion host
- Network security group for bastion host
- Cloud Connector VMs
- Management interface
- Service interface
- Network security group for management interface
- Network security group for service interface
- Local key pair for SSH access
- Azure Private DNS Resolver virtual network link
- Azure Private DNS subnet
- Azure Private DNS Resolver forwarding ruleset
- Azure Private DNS Resolver outbound endpoint
- Azure Load Balancer rules
- Azure Load Balancer backend address pool
- Azure Load Balancer health probe
- [See Resource Logs](#tf-azure-LB-ZPA)
[]
`azurerm_private_dns_resolver_virtual_network_link.dns_vnet_link
local_file.private_key
local_file.testbed
local_file.user_data_file
random_string.suffix
tls_private_key.key
module.bastion.azurerm_linux_virtual_machine.bastion_vm
module.bastion.azurerm_network_interface.bastion_nic
module.bastion.azurerm_network_interface_security_group_association.bastion_nic_association
module.bastion.azurerm_network_security_group.bastion_nsg
module.bastion.azurerm_public_ip.bastion_pip
module.cc_identity.data.azurerm_user_assigned_identity.selected
module.cc_lb.azurerm_lb.cc_lb
module.cc_lb.azurerm_lb_backend_address_pool.cc_lb_backend_pool
module.cc_lb.azurerm_lb_probe.cc_lb_probe
module.cc_lb.azurerm_lb_rule.cc_lb_rule
module.cc_nsg.azurerm_network_security_group.cc_mgmt_nsg[0]
module.cc_nsg.azurerm_network_security_group.cc_mgmt_nsg[1]
module.cc_nsg.azurerm_network_security_group.cc_service_nsg[0]
module.cc_nsg.azurerm_network_security_group.cc_service_nsg[1]
module.cc_vm.azurerm_linux_virtual_machine.cc_vm[0]
module.cc_vm.azurerm_linux_virtual_machine.cc_vm[1]
module.cc_vm.azurerm_network_interface.cc_mgmt_nic[0]
module.cc_vm.azurerm_network_interface.cc_mgmt_nic[1]
module.cc_vm.azurerm_network_interface.cc_service_nic[0]
module.cc_vm.azurerm_network_interface.cc_service_nic[1]
module.cc_vm.azurerm_network_interface_backend_address_pool_association.cc_vm_service_nic_lb_association[0]
module.cc_vm.azurerm_network_interface_backend_address_pool_association.cc_vm_service_nic_lb_association[1]
module.cc_vm.azurerm_network_interface_security_group_association.cc_mgmt_nic_association[0]
module.cc_vm.azurerm_network_interface_security_group_association.cc_mgmt_nic_association[1]
module.cc_vm.azurerm_network_interface_security_group_association.cc_service_nic_association[0]
module.cc_vm.azurerm_network_interface_security_group_association.cc_service_nic_association[1]
module.network.data.azurerm_subnet.cc_subnet_selected[0]
module.network.azurerm_nat_gateway.ngw[0]
module.network.azurerm_nat_gateway_public_ip_association.ngw_association[0]
module.network.azurerm_public_ip.pip[0]
module.network.azurerm_resource_group.rg[0]
module.network.azurerm_route_table.private_dns_rt[0]
module.network.azurerm_route_table.workload_rt[0]
module.network.azurerm_subnet.bastion_subnet[0]
module.network.azurerm_subnet.cc_subnet[0]
module.network.azurerm_subnet.private_dns_subnet[0]
module.network.azurerm_subnet.workload_subnet[0]
module.network.azurerm_subnet_nat_gateway_association.cc_subnet_nat_association[0]
module.network.azurerm_subnet_route_table_association.private_dns_rt_association[0]
module.network.azurerm_subnet_route_table_association.workload_rt_association[0]
module.network.azurerm_virtual_network.vnet[0]
module.private_dns.azurerm_private_dns_resolver.dns_resolver
module.private_dns.azurerm_private_dns_resolver_dns_forwarding_ruleset.dns_forwarding_ruleset
module.private_dns.azurerm_private_dns_resolver_forwarding_rule.dns_forwarding_rule["appseg1"]
module.private_dns.azurerm_private_dns_resolver_forwarding_rule.dns_forwarding_rule["appseg2"]
module.private_dns.azurerm_private_dns_resolver_outbound_endpoint.dns_outbound_endpoint
module.workload.azurerm_linux_virtual_machine.workload_vm[0]
module.workload.azurerm_network_interface.workload_nic[0]
module.workload.azurerm_network_interface_security_group_association.workload_nic_association[0]
module.workload.azurerm_network_security_group.workload_nsg[0]`
[]Use the Custom Deployment Template with Load Balancer (cc_lb) to deploy your Cloud Connector in a new or existing resource group and virtual network. The template creates the following resources:
- Resource group
- Cloud Connector subnet
- Virtual network
- Two Cloud Connector VMs
- Management interface
- Service interface
- Network security group for management interface
- Network security group for service interface
- Local key pair for SSH access
- NAT gateway
- Public IP address associated with NAT gateway
- Azure Load Balancer to monitor events triggering a failover
- [See Resource Logs](#tf-azure5)
[]
`azurerm_nat_gateway.nat-gw1[0] will be created
azurerm_nat_gateway_public_ip_association.nat-gw-association1[0] will be created
azurerm_public_ip.nat-pip[0] will be created
azurerm_resource_group.main[0] will be created
azurerm_subnet.cc-subnet[0] will be created
azurerm_subnet_nat_gateway_association.subnet-nat-association-ec[0] will be created
azurerm_virtual_network.vnet1[0] will be created
local_file.testbed will be created
local_file.user-data-file will be created
null_resource.save-key will be created
random_string.suffix will be created
tls_private_key.key will be created
module.cc-vm.azurerm_availability_set.cc-availability-set will be created
module.cc-vm.azurerm_lb.cc-lb will be created
module.cc-vm.azurerm_lb_backend_address_pool.cc-lb-backend-pool will be created
module.cc-vm.azurerm_lb_probe.cc-lb-probe will be created
module.cc-vm.azurerm_lb_rule.cc-lb-rule will be created
module.cc-vm.azurerm_linux_virtual_machine.cc-vm[0] will be created
module.cc-vm.azurerm_linux_virtual_machine.cc-vm[1] will be created
module.cc-vm.azurerm_network_interface.cc-mgmt-nic[0] will be created
module.cc-vm.azurerm_network_interface.cc-mgmt-nic[1] will be created
module.cc-vm.azurerm_network_interface.cc-service-nic[0] will be created
module.cc-vm.azurerm_network_interface.cc-service-nic[1] will be created
module.cc-vm.azurerm_network_interface_backend_address_pool_association.cc-vm-service-nic-lb-association[0] will be created
module.cc-vm.azurerm_network_interface_backend_address_pool_association.cc-vm-service-nic-lb-association[1] will be created
module.cc-vm.azurerm_network_interface_security_group_association.ec-mgmt-nic-association[0] will be created
module.cc-vm.azurerm_network_interface_security_group_association.ec-mgmt-nic-association[1] will be created
module.cc-vm.azurerm_network_interface_security_group_association.ec-service-nic-association[0] will be created
module.cc-vm.azurerm_network_interface_security_group_association.ec-service-nic-association[1] will be created
module.cc-vm.azurerm_network_security_group.cc-nsg will be created
module.cc-vm.azurerm_network_security_group.cc-service-nsg will be created`
[]Use the Starter Deployment Template with VMSS and Load Balancer (base_cc_vmss) to deploy your Cloud Connector in a new resource group and virtual network. The template creates the following resources:
- Resource group
- Cloud Connector subnets (one per zone)
- Ubuntu server bastion host
- Route tables for routing the workload traffic through the Cloud Connector
- Virtual network
- Bastion subnet
- Workload subnet
- Ubuntu server workload
- Public IP address for bastion host
- Local key pair for SSH access
- Cloud Connector Scale Set (one per zone)
- Management interface
- Service interface
- Network security group for management interface
- Network security group for service interface
- NAT gateway (one per zone)
- Public IP address associated with NAT gateway (one per zone)
- Azure Load Balancer
- Azure Function App
- Storage account
- Log analytics workspace
- Virtual Machine Scale Set settings (one per zone)
- [See Resource Logs](#tf-azure-template-VMSS1)
[]
`local_file.private_key will be created
local_file.user_data_file will be created
random_string.suffix will be created
tls_private_key.key will be created
module.bastion.azurerm_linux_virtual_machine.bastion_vm will be created
module.bastion.azurerm_network_interface.bastion_nic will be created
module.bastion.azurerm_network_interface_security_group_association.bastion_nic_association will be created
module.bastion.azurerm_network_security_group.bastion_nsg will be created
module.bastion.azurerm_public_ip.bastion_pip will be created
module.cc_functionapp.data.local_file.manual_sync_exist_status[0] will be read during apply
module.cc_functionapp.azurerm_application_insights.vmss_orchestration_app_insights will be created
module.cc_functionapp.azurerm_linux_function_app.vmss_orchestration_app_with_manual_sync[0] will be created
module.cc_functionapp.azurerm_log_analytics_workspace.vmss_orchestration_log_analytics_workspace[0] will be created
module.cc_functionapp.azurerm_service_plan.vmss_orchestration_app_service_plan will be created
module.cc_functionapp.azurerm_storage_account.cc_function_storage_account[0] will be created
module.cc_functionapp.azurerm_storage_blob.cc_function_storage_blob[0] will be created
module.cc_functionapp.azurerm_storage_container.cc_function_storage_container[0] will be created
module.cc_lb.azurerm_lb.cc_lb will be created
module.cc_lb.azurerm_lb_backend_address_pool.cc_lb_backend_pool will be created
module.cc_lb.azurerm_lb_probe.cc_lb_probe will be created
module.cc_lb.azurerm_lb_rule.cc_lb_rule will be created
module.cc_nsg.azurerm_network_security_group.cc_mgmt_nsg[0] will be created
module.cc_nsg.azurerm_network_security_group.cc_service_nsg[0] will be created
module.cc_vmss.azurerm_monitor_autoscale_setting.vmss_autoscale_setting[0] will be created
module.cc_vmss.azurerm_monitor_autoscale_setting.vmss_autoscale_setting[1] will be created
module.cc_vmss.azurerm_orchestrated_virtual_machine_scale_set.cc_vmss[0] will be created
module.cc_vmss.azurerm_orchestrated_virtual_machine_scale_set.cc_vmss[1] will be created
module.network.data.azurerm_subnet.cc_subnet_selected[0] will be read during apply
module.network.data.azurerm_subnet.cc_subnet_selected[1] will be read during apply
module.network.azurerm_nat_gateway.ngw[0] will be created
module.network.azurerm_nat_gateway.ngw[1] will be created
module.network.azurerm_nat_gateway_public_ip_association.ngw_association[0] will be created
module.network.azurerm_nat_gateway_public_ip_association.ngw_association[1] will be created
module.network.azurerm_public_ip.pip[0] will be created
module.network.azurerm_public_ip.pip[1] will be created
module.network.azurerm_resource_group.rg[0] will be created
module.network.azurerm_route_table.workload_rt[0] will be created
module.network.azurerm_subnet.bastion_subnet[0] will be created
module.network.azurerm_subnet.cc_subnet[0] will be created
module.network.azurerm_subnet.cc_subnet[1] will be created
module.network.azurerm_subnet.workload_subnet[0] will be created
module.network.azurerm_subnet_nat_gateway_association.cc_subnet_nat_association[0] will be created
module.network.azurerm_subnet_nat_gateway_association.cc_subnet_nat_association[1] will be created
module.network.azurerm_subnet_route_table_association.workload_rt_association[0] will be created
module.network.azurerm_virtual_network.vnet[0] will be created
module.workload.azurerm_linux_virtual_machine.workload_vm[0] will be created
module.workload.azurerm_network_interface.workload_nic[0] will be created
module.workload.azurerm_network_interface_security_group_association.workload_nic_association[0] will be created
module.workload.azurerm_network_security_group.workload_nsg[0] will be created`
[]Use the Starter Deployment Template with VMSS, Load Balancer, and ZPA (base_cc_vmss_zpa) to deploy your Cloud Connector in a new resource group and virtual network. The template creates the following resources:
- Resource group
- Cloud Connector subnets (one per zone)
- Ubuntu server bastion host
- Route tables for routing the workload traffic through the Cloud Connector.
- Virtual network
- Bastion subnet
- Workload subnet
- Ubuntu server workload
- Public IP address for bastion host
- Local key pair for SSH access
- Cloud Connector Scale Set (one per zone)
- Management interface
- Service interface
- Network security group for management interface
- Network security group for service interface
- NAT gateway (one per zone)
- Public IP address associated with NAT gateway (one per zone)
- Azure Load Balancer
- Azure Function App
- Storage account
- Log Analytics workspace
- Virtual Machine Scale Set settings (one per zone)
- Azure Private DNS Resolver virtual network link
- Azure Private DNS subnet
- Azure Private DNS Resolver Forwarding ruleset
- Azure Private DNS Resolver outbound endpoint
- [See Resource Logs](#tf-azure-template-VMSS2)
[]
`azurerm_private_dns_resolver_virtual_network_link.dns_vnet_link will be created
local_file.private_key will be created
local_file.testbed will be created
local_file.user_data_file will be created
random_string.suffix will be created
tls_private_key.key will be created
module.bastion.azurerm_linux_virtual_machine.bastion_vm will be created
module.bastion.azurerm_network_interface.bastion_nic will be created
module.bastion.azurerm_network_interface_security_group_association.bastion_nic_association will be created
module.bastion.azurerm_network_security_group.bastion_nsg will be created
module.bastion.azurerm_public_ip.bastion_pip will be created
module.cc_functionapp.data.local_file.manual_sync_exist_status[0] will be read during apply
module.cc_functionapp.azurerm_application_insights.vmss_orchestration_app_insights will be created
module.cc_functionapp.azurerm_linux_function_app.vmss_orchestration_app_with_manual_sync[0] will be created
module.cc_functionapp.azurerm_log_analytics_workspace.vmss_orchestration_log_analytics_workspace[0] will be created
module.cc_functionapp.azurerm_service_plan.vmss_orchestration_app_service_plan will be created
module.cc_functionapp.azurerm_storage_account.cc_function_storage_account[0] will be created
module.cc_functionapp.azurerm_storage_blob.cc_function_storage_blob[0] will be created
module.cc_functionapp.azurerm_storage_container.cc_function_storage_container[0] will be created
module.cc_lb.azurerm_lb.cc_lb will be created
module.cc_lb.azurerm_lb_backend_address_pool.cc_lb_backend_pool will be created
module.cc_lb.azurerm_lb_probe.cc_lb_probe will be created
module.cc_lb.azurerm_lb_rule.cc_lb_rule will be created
module.cc_nsg.azurerm_network_security_group.cc_mgmt_nsg[0] will be created
module.cc_nsg.azurerm_network_security_group.cc_service_nsg[0] will be created
module.cc_vmss.azurerm_monitor_autoscale_setting.vmss_autoscale_setting[0] will be created
module.cc_vmss.azurerm_monitor_autoscale_setting.vmss_autoscale_setting[1] will be created
module.cc_vmss.azurerm_orchestrated_virtual_machine_scale_set.cc_vmss[0] will be created
module.cc_vmss.azurerm_orchestrated_virtual_machine_scale_set.cc_vmss[1] will be created
module.network.data.azurerm_subnet.cc_subnet_selected[0] will be read during apply
module.network.data.azurerm_subnet.cc_subnet_selected[1] will be read during apply
module.network.azurerm_nat_gateway.ngw[0] will be created
module.network.azurerm_nat_gateway.ngw[1] will be created
module.network.azurerm_nat_gateway_public_ip_association.ngw_association[0] will be created
module.network.azurerm_nat_gateway_public_ip_association.ngw_association[1] will be created
module.network.azurerm_public_ip.pip[0] will be created
module.network.azurerm_public_ip.pip[1] will be created
module.network.azurerm_resource_group.rg[0] will be created
module.network.azurerm_route_table.private_dns_rt[0] will be created
module.network.azurerm_route_table.workload_rt[0] will be created
module.network.azurerm_subnet.bastion_subnet[0] will be created
module.network.azurerm_subnet.cc_subnet[0] will be created
module.network.azurerm_subnet.cc_subnet[1] will be created
module.network.azurerm_subnet.private_dns_subnet[0] will be created
module.network.azurerm_subnet.workload_subnet[0] will be created
module.network.azurerm_subnet_nat_gateway_association.cc_subnet_nat_association[0] will be created
module.network.azurerm_subnet_nat_gateway_association.cc_subnet_nat_association[1] will be created
module.network.azurerm_subnet_route_table_association.private_dns_rt_association[0] will be created
module.network.azurerm_subnet_route_table_association.workload_rt_association[0] will be created
module.network.azurerm_virtual_network.vnet[0] will be created
module.private_dns.azurerm_private_dns_resolver.dns_resolver will be created
module.private_dns.azurerm_private_dns_resolver_dns_forwarding_ruleset.dns_forwarding_ruleset will be created
module.private_dns.azurerm_private_dns_resolver_forwarding_rule.dns_forwarding_rule["appseg1"] will be created
module.private_dns.azurerm_private_dns_resolver_forwarding_rule.dns_forwarding_rule["appseg2"] will be created
module.private_dns.azurerm_private_dns_resolver_outbound_endpoint.dns_outbound_endpoint will be created
module.workload.azurerm_linux_virtual_machine.workload_vm[0] will be created
module.workload.azurerm_network_interface.workload_nic[0] will be created
module.workload.azurerm_network_interface_security_group_association.workload_nic_association[0] will be created
module.workload.azurerm_network_security_group.workload_nsg[0] will be created`
[]Use the Custom Deployment Template with VMSS and Load Balancer (cc_vmss) to deploy your Cloud Connector in a new or existing resource group and virtual network. The template creates the following resources:
- Resource group
- Cloud Connector subnets (one per zone)
- Virtual network
- Local key pair for SSH access
- Cloud Connector Scale Set (one per zone)
- Management interface
- Service interface
- Network security group for management interface
- Network security group for service interface
- NAT gateway (one per zone)
- Public IP address associated with NAT gateway (one per zone)
- Azure Load Balancer
- Azure Function App
- Storage account
- Log Analytics workspace
- Virtual Machine Scale Set settings (one per zone)
- [See Resource Logs](#tf-azure-template-VMSS3)
[]
`local_file.private_key will be created
local_file.testbed will be created
local_file.user_data_file will be created
random_string.suffix will be created
tls_private_key.key will be created
module.cc_functionapp.data.local_file.manual_sync_exist_status[0] will be read during apply
module.cc_functionapp.azurerm_application_insights.vmss_orchestration_app_insights will be created
module.cc_functionapp.azurerm_linux_function_app.vmss_orchestration_app_with_manual_sync[0] will be created
module.cc_functionapp.azurerm_log_analytics_workspace.vmss_orchestration_log_analytics_workspace[0] will be created
module.cc_functionapp.azurerm_service_plan.vmss_orchestration_app_service_plan will be created
module.cc_functionapp.azurerm_storage_account.cc_function_storage_account[0] will be created
module.cc_functionapp.azurerm_storage_blob.cc_function_storage_blob[0] will be created
module.cc_functionapp.azurerm_storage_container.cc_function_storage_container[0] will be created
module.cc_lb.azurerm_lb.cc_lb will be created
module.cc_lb.azurerm_lb_backend_address_pool.cc_lb_backend_pool will be created
module.cc_lb.azurerm_lb_probe.cc_lb_probe will be created
module.cc_lb.azurerm_lb_rule.cc_lb_rule will be created
module.cc_nsg.azurerm_network_security_group.cc_mgmt_nsg[0] will be created
module.cc_nsg.azurerm_network_security_group.cc_service_nsg[0] will be created
module.cc_vmss.azurerm_monitor_autoscale_setting.vmss_autoscale_setting[0] will be created
module.cc_vmss.azurerm_monitor_autoscale_setting.vmss_autoscale_setting[1] will be created
module.cc_vmss.azurerm_orchestrated_virtual_machine_scale_set.cc_vmss[0] will be created
module.cc_vmss.azurerm_orchestrated_virtual_machine_scale_set.cc_vmss[1] will be created
module.network.data.azurerm_subnet.cc_subnet_selected[0] will be read during apply
module.network.data.azurerm_subnet.cc_subnet_selected[1] will be read during apply
module.network.azurerm_nat_gateway.ngw[0] will be created
module.network.azurerm_nat_gateway.ngw[1] will be created
module.network.azurerm_nat_gateway_public_ip_association.ngw_association[0] will be created
module.network.azurerm_nat_gateway_public_ip_association.ngw_association[1] will be created
module.network.azurerm_public_ip.pip[0] will be created
module.network.azurerm_public_ip.pip[1] will be created
module.network.azurerm_resource_group.rg[0] will be created
module.network.azurerm_subnet.cc_subnet[0] will be created
module.network.azurerm_subnet.cc_subnet[1] will be created
module.network.azurerm_subnet_nat_gateway_association.cc_subnet_nat_association[0] will be created
module.network.azurerm_subnet_nat_gateway_association.cc_subnet_nat_association[1] will be created
module.network.azurerm_virtual_network.vnet[0] will be created`
GCP Deployment Templates
This section describes the resources created when deploying Cloud Connector using a Terraform script. To learn more, see [Deploying](/cloud-branch-connector/deploying-zscaler-cloud-connector-google-cloud-platform) [Zscaler Cloud Connector on the Google Cloud Platform](/unified/deploying-zscaler-cloud-connector-google-cloud-platform).
Use the templates in the [Terraform](https://github.com/zscaler/terraform-gcp-cloud-connector-modules) repository to create the deployment resources required to deploy and operate Cloud Connector in a new or existing VPC.
- [Basic Deployment Templates](#t-templates-gcp)
- [Deployment Templates with Load Balancer](#t-templates-gcp-lb)
[]
- [Starter Deployment Template](#t-gcp-template)
- [Starter Deployment Template with ZPA](#t-gcp-template-ZPA)
[]
- [Starter Deployment Template with Internal Load Balancer](#t-gcp-template4)
- [Starter Deployment Template with Internal Load Balancer and ZPA](#t-gcp-template-LB-ZPA)
- [Custom Deployment Template with Internal Load Balancer](#t-gcp-template5)
[]
[]Use the Starter Deployment Template (base_1cc) to deploy your Cloud Connector in a new VPC network. The template creates the following resources:
- Instance key pair for SSH access
- Management VPC network
- Management VPC router
- Management VPC NAT
- Management VPC management subnet
- Management VPC <> Service VPC peering
- Service VPC network
- Service VPC router
- Service VPC NAT
- Service VPC service subnet
- Service VPC workload subnet
- Workload compute instance
- Workload service account
- Workload VPC firewall rules
- Workload tagged default route next-hop Cloud Connector service interface
- Bastion compute instance
- Bastion service account
- Bastion VPC firewall rules
- Cloud Connector instance template
- Cloud Connector Managed Instance Group (MIG)
- Service interface on service VPC
- Management interface on management VPC
- User-managed service account attached to Cloud Connector VM with IAM access to either GCP Secret Manager or HashiCorp Vault, depending on the authentication method you chose
- [See Resource Logs](#tf-gcp3)
[]
`[0]-[1] indicates default values where two duplicate/like resources (like cloud connectors) would be created
data.google_compute_zones.available
google_compute_route.route_to_cc_vm
local_file.private_key
local_file.testbed
local_file.user_data_file
random_string.suffix
tls_private_key.key
module.bastion.google_compute_firewall.ssh_internet_ingress
module.bastion.google_compute_instance.bastion
module.bastion.google_service_account.service_account_bastion
module.cc_vm.data.google_compute_instance.cc_vm_instances[0]
module.cc_vm.data.google_compute_instance_group.cc_instance_groups[0]
module.cc_vm.google_compute_instance_group_manager.cc_instance_group_manager[0]
module.cc_vm.google_compute_instance_template.cc_instance_template
module.cc_vm.time_sleep.wait_60_seconds
module.iam_service_account.google_secret_manager_secret_iam_member.member
module.iam_service_account.google_service_account.service_account_ccvm
module.network.google_compute_firewall.default_service
module.network.google_compute_firewall.ssh_intranet_cc_mgmt
module.network.google_compute_network.mgmt_vpc_network[0]
module.network.google_compute_network.service_vpc_network[0]
module.network.google_compute_network_peering.management_to_service[0]
module.network.google_compute_network_peering.service_to_management[0]
module.network.google_compute_router.mgmt_vpc_router[0]
module.network.google_compute_router.service_vpc_router[0]
module.network.google_compute_router_nat.mgmt_vpc_nat_gateway[0]
module.network.google_compute_router_nat.service_vpc_nat_gateway[0]
module.network.google_compute_subnetwork.mgmt_subnet[0]
module.network.google_compute_subnetwork.mgmt_vpc_subnet_bastion[0]
module.network.google_compute_subnetwork.service_subnet[0]
module.network.google_compute_subnetwork.vpc_subnet_workload[0]
module.workload.google_compute_firewall.ssh_intranet_workload
module.workload.google_compute_instance.server_host
module.workload.google_service_account.service_account_workload`
[]
[]Use the Starter Deployment Template with ZPA (base_1cc_zpa) to deploy your Cloud Connector in a new VPC Network. The template creates the following resources:
- Instance key pair for SSH access
- Management VPC network
- Management VPC router
- Management VPC NAT
- Management VPC management subnet
- Management VPC <> Service VPC peering
- Service VPC network
- Service VPC router
- Service VPC NAT
- Service VPC service subnet
- Service VPC workload subnet
- Workload compute instance
- Workload service account
- Workload VPC firewall rules
- Workload tagged default route next-hop Cloud Connector service interface
- Bastion compute instance
- Bastion service account
- Bastion VPC firewall rules
- Cloud Connector instance template
- Cloud Connector Managed Instance Group (MIG)
- Service interface on service VPC
- Management interface on management VPC
- User-managed service account attached to Cloud Connector VM with IAM access to either GCP Secret Manager or HashiCorp Vault, depending on the authentication method you chose
- Cloud DNS VPC firewall rules
- Cloud DNS managed DNS forward zones
- [See Resource Logs](#tf-gcp-ZPA)
[]
`[0]-[1] indicates default values where two duplicate/like resources (like cloud connectors) would be created
data.google_compute_zones.available
google_compute_route.route_to_cc_vm
local_file.private_key
local_file.testbed
local_file.user_data_file
random_string.suffix
tls_private_key.key
module.bastion.google_compute_firewall.ssh_internet_ingress
module.bastion.google_compute_instance.bastion
module.bastion.google_service_account.service_account_bastion
module.cc_vm.data.google_compute_instance.cc_vm_instances[0]
module.cc_vm.data.google_compute_instance_group.cc_instance_groups[0]
module.cc_vm.google_compute_instance_group_manager.cc_instance_group_manager[0]
module.cc_vm.google_compute_instance_template.cc_instance_template
module.cc_vm.time_sleep.wait_60_seconds
module.iam_service_account.google_secret_manager_secret_iam_member.member
module.iam_service_account.google_service_account.service_account_ccvm
module.network.google_compute_firewall.default_service
module.network.google_compute_firewall.ssh_intranet_cc_mgmt
module.network.google_compute_network.mgmt_vpc_network[0]
module.network.google_compute_network.service_vpc_network[0]
module.network.google_compute_network_peering.management_to_service[0]
module.network.google_compute_network_peering.service_to_management[0]
module.network.google_compute_router.mgmt_vpc_router[0]
module.network.google_compute_router.service_vpc_router[0]
module.network.google_compute_router_nat.mgmt_vpc_nat_gateway[0]
module.network.google_compute_router_nat.service_vpc_nat_gateway[0]
module.network.google_compute_subnetwork.mgmt_subnet[0]
module.network.google_compute_subnetwork.mgmt_vpc_subnet_bastion[0]
module.network.google_compute_subnetwork.service_subnet[0]
module.network.google_compute_subnetwork.vpc_subnet_workload[0]
module.workload.google_compute_firewall.ssh_intranet_workload
module.workload.google_compute_instance.server_host
module.workload.google_service_account.service_account_workload
module.cloud_dns.google_compute_firewall.allow_cloud_dns[0]
module.cloud_dns.google_dns_managed_zone.dns_forward_zone["appseg1"]
module.cloud_dns.google_dns_managed_zone.dns_forward_zone["appseg2"]`
[]
Use the Starter Deployment Template with Internal Load Balancer (base_cc_ilb) to deploy your Cloud Connectors in a new VPC Network. The template creates the following resources:
- Instance key pair for SSH access
- Management VPC network
- Management VPC router
- Management VPC NAT
- Management VPC management subnet
- Management VPC <> Service VPC peering
- Service VPC network
- Service VPC router
- Service VPC NAT
- Service VPC service subnet
- Service VPC workload subnet
- Workload compute instance
- Workload service account
- Workload VPC firewall rules
- Workload tagged default route next-hop Internal Load Balancer front-end IP
- Bastion compute instance
- Bastion service account
- Bastion VPC firewall rules
- Cloud Connector instance template
- Cloud Connector Managed Instance Group (MIG)
- Service interface on service VPC
- Management interface on management VPC
- User-managed service account attached to Cloud Connector VM with IAM access to either GCP Secret Manager or HashiCorp Vault, depending on the authentication method you chose
- Standard passthrough internal Load Balancer
- Regional backend service for internal Load Balancer
- Compute health checks from internal Load Balancer
- Compute forwarding rule for internal Load Balancer
- Load Balancer VPC firewall rules
- [See Resource Logs](#tf-gcp4)
[]
`[0]-[1] indicates default values where two duplicate/like resources (like cloud connectors) would be created
ata.google_compute_zones.available
google_compute_route.route_to_cc_vm
local_file.private_key
local_file.testbed
local_file.user_data_file
random_string.suffix
tls_private_key.key
module.bastion.google_compute_firewall.ssh_internet_ingress
module.bastion.google_compute_instance.bastion
module.bastion.google_service_account.service_account_bastion
module.cc_vm.data.google_compute_instance.cc_vm_instances[0]
module.cc_vm.data.google_compute_instance.cc_vm_instances[1]
module.cc_vm.data.google_compute_instance.cc_vm_instances[2]
module.cc_vm.data.google_compute_instance.cc_vm_instances[3]
module.cc_vm.data.google_compute_instance_group.cc_instance_groups[0]
module.cc_vm.data.google_compute_instance_group.cc_instance_groups[1]
module.cc_vm.google_compute_instance_group_manager.cc_instance_group_manager[0]
module.cc_vm.google_compute_instance_group_manager.cc_instance_group_manager[1]
module.cc_vm.google_compute_instance_template.cc_instance_template
module.cc_vm.time_sleep.wait_60_seconds
module.iam_service_account.google_secret_manager_secret_iam_member.member
module.iam_service_account.google_service_account.service_account_ccvm
module.ilb.google_compute_address.ilb_ip_address
module.ilb.google_compute_firewall.allow_cc_health_check
module.ilb.google_compute_forwarding_rule.ilb_forwarding
module.ilb.google_compute_health_check.cc_health_check
module.ilb.google_compute_region_backend_service.backend_service
module.network.google_compute_firewall.default_service
module.network.google_compute_firewall.ssh_intranet_cc_mgmt
module.network.google_compute_network.mgmt_vpc_network[0]
module.network.google_compute_network.service_vpc_network[0]
module.network.google_compute_network_peering.management_to_service[0]
module.network.google_compute_network_peering.service_to_management[0]
module.network.google_compute_router.mgmt_vpc_router[0]
module.network.google_compute_router.service_vpc_router[0]
module.network.google_compute_router_nat.mgmt_vpc_nat_gateway[0]
module.network.google_compute_router_nat.service_vpc_nat_gateway[0]
module.network.google_compute_subnetwork.mgmt_subnet[0]
module.network.google_compute_subnetwork.mgmt_vpc_subnet_bastion[0]
module.network.google_compute_subnetwork.service_subnet[0]
module.network.google_compute_subnetwork.vpc_subnet_workload[0]
module.workload.google_compute_firewall.ssh_intranet_workload
module.workload.google_compute_instance.server_host
module.workload.google_service_account.service_account_workload`
[]Use the Starter Deployment Template with Load Balancer and ZPA (base_cc_ilb_zpa) to deploy your Cloud Connectors in a new VPC Network. The template creates the following resources:
- Instance key pair for SSH access
- Management VPC network
- Management VPC router
- Management VPC NAT
- Management VPC management subnet
- Management VPC <> Service VPC peering
- Service VPC network
- Service VPC router
- Service VPC NAT
- Service VPC service subnet
- Service VPC workload dubnet
- Workload compute instance
- Workload service account
- Workload VPC firewall rules
- Workload tagged default route next-hop Internal Load Balancer front-end IP
- Bastion compute instance
- Bastion service account
- Bastion VPC firewall rules
- Cloud Connector instance template
- Cloud Connector Managed Instance Group (MIG)
- Service interface on service VPC
- Management interface on management VPC
- User-managed service account attached to Cloud Connector VM with IAM access to either GCP Secret Manager or HashiCorp Vault, depending on the authentication method you chose
- Standard passthrough Internal Load Balancer
- Regional backend service for Internal Load Balancer
- Compute health checks from Internal Load Balancer
- Compute forwarding rule for Internal Load Balancer
- Load Balancer VPC firewall Rules
- Cloud DNS VPC firewall Rules
- Cloud DNS-managed DNS forward zones
- [See Resource Logs](#tf-gcp-LB-ZPA)
[]
`[0]-[1] indicates default values where two duplicate/like resources (like cloud connectors) would be created
ata.google_compute_zones.available
google_compute_route.route_to_cc_vm
local_file.private_key
local_file.testbed
local_file.user_data_file
random_string.suffix
tls_private_key.key
module.bastion.google_compute_firewall.ssh_internet_ingress
module.bastion.google_compute_instance.bastion
module.bastion.google_service_account.service_account_bastion
module.cc_vm.data.google_compute_instance.cc_vm_instances[0]
module.cc_vm.data.google_compute_instance.cc_vm_instances[1]
module.cc_vm.data.google_compute_instance.cc_vm_instances[2]
module.cc_vm.data.google_compute_instance.cc_vm_instances[3]
module.cc_vm.data.google_compute_instance_group.cc_instance_groups[0]
module.cc_vm.data.google_compute_instance_group.cc_instance_groups[1]
module.cc_vm.google_compute_instance_group_manager.cc_instance_group_manager[0]
module.cc_vm.google_compute_instance_group_manager.cc_instance_group_manager[1]
module.cc_vm.google_compute_instance_template.cc_instance_template
module.cc_vm.time_sleep.wait_60_seconds
module.iam_service_account.google_secret_manager_secret_iam_member.member
module.iam_service_account.google_service_account.service_account_ccvm
module.ilb.google_compute_address.ilb_ip_address
module.ilb.google_compute_firewall.allow_cc_health_check
module.ilb.google_compute_forwarding_rule.ilb_forwarding
module.ilb.google_compute_health_check.cc_health_check
module.ilb.google_compute_region_backend_service.backend_service
module.network.google_compute_firewall.default_service
module.network.google_compute_firewall.ssh_intranet_cc_mgmt
module.network.google_compute_network.mgmt_vpc_network[0]
module.network.google_compute_network.service_vpc_network[0]
module.network.google_compute_network_peering.management_to_service[0]
module.network.google_compute_network_peering.service_to_management[0]
module.network.google_compute_router.mgmt_vpc_router[0]
module.network.google_compute_router.service_vpc_router[0]
module.network.google_compute_router_nat.mgmt_vpc_nat_gateway[0]
module.network.google_compute_router_nat.service_vpc_nat_gateway[0]
module.network.google_compute_subnetwork.mgmt_subnet[0]
module.network.google_compute_subnetwork.mgmt_vpc_subnet_bastion[0]
module.network.google_compute_subnetwork.service_subnet[0]
module.network.google_compute_subnetwork.vpc_subnet_workload[0]
module.workload.google_compute_firewall.ssh_intranet_workload
module.workload.google_compute_instance.server_host
module.workload.google_service_account.service_account_workload
module.cloud_dns.google_compute_firewall.allow_cloud_dns[0]
module.cloud_dns.google_dns_managed_zone.dns_forward_zone["appseg1"]
module.cloud_dns.google_dns_managed_zone.dns_forward_zone["appseg2"]`
[]Use the Custom Deployment Template with Load Balancer (cc_ilb) to deploy your Cloud Connector in a new or existing VPC Network. The template creates the following resources:
- Instance key pair for SSH access
- Management VPC network
- Management VPC router
- Management VPC NAT
- Management VPC management subnet
- Management VPC <> Service VPC peering
- Service VPC network
- Service VPC touter
- Service VPC NAT
- Service VPC service dubnet
- Cloud Connector instance template
- Cloud Connector Managed Instance Group (MIG)
- Service interface on service VPC
- Management interface on management VPC
- User-managed service account attached to Cloud Connector VM with IAM access to either GCP Secret Manager or HashiCorp Vault, depending on the authentication method you chose
- Standard passthrough Internal Load Balancer
- Regional backend service for Internal Load Balancer
- Compute health checks from Internal Load Balancer
- Compute forwarding rule for Internal Load Balancer
- Load Balancer VPC firewall rules
- (Optional) Cloud DNS VPC firewall rules
- (Optional) Cloud DNS-managed DNS forward zones
- [See Resource Logs](#tf-gcp5)
[]
`[0]-[1] indicates default values where two duplicate/like resources (like cloud connectors) would be created
ata.google_compute_zones.available
google_compute_route.route_to_cc_vm
local_file.private_key
local_file.testbed
local_file.user_data_file
random_string.suffix
tls_private_key.key
module.bastion.google_compute_firewall.ssh_internet_ingress
module.bastion.google_compute_instance.bastion
module.bastion.google_service_account.service_account_bastion
module.cc_vm.data.google_compute_instance.cc_vm_instances[0]
module.cc_vm.data.google_compute_instance.cc_vm_instances[1]
module.cc_vm.data.google_compute_instance.cc_vm_instances[2]
module.cc_vm.data.google_compute_instance.cc_vm_instances[3]
module.cc_vm.data.google_compute_instance_group.cc_instance_groups[0]
module.cc_vm.data.google_compute_instance_group.cc_instance_groups[1]
module.cc_vm.google_compute_instance_group_manager.cc_instance_group_manager[0]
module.cc_vm.google_compute_instance_group_manager.cc_instance_group_manager[1]
module.cc_vm.google_compute_instance_template.cc_instance_template
module.cc_vm.time_sleep.wait_60_seconds
module.iam_service_account.google_secret_manager_secret_iam_member.member
module.iam_service_account.google_service_account.service_account_ccvm
module.ilb.google_compute_address.ilb_ip_address
module.ilb.google_compute_firewall.allow_cc_health_check
module.ilb.google_compute_forwarding_rule.ilb_forwarding
module.ilb.google_compute_health_check.cc_health_check
module.ilb.google_compute_region_backend_service.backend_service
module.network.google_compute_firewall.default_service
module.network.google_compute_firewall.ssh_intranet_cc_mgmt
module.network.google_compute_network.mgmt_vpc_network[0]
module.network.google_compute_network.service_vpc_network[0]
module.network.google_compute_network_peering.management_to_service[0]
module.network.google_compute_network_peering.service_to_management[0]
module.network.google_compute_router.mgmt_vpc_router[0]
module.network.google_compute_router.service_vpc_router[0]
module.network.google_compute_router_nat.mgmt_vpc_nat_gateway[0]
module.network.google_compute_router_nat.service_vpc_nat_gateway[0]
module.network.google_compute_subnetwork.mgmt_subnet[0]
module.network.google_compute_subnetwork.mgmt_vpc_subnet_bastion[0]
module.network.google_compute_subnetwork.service_subnet[0]
module.network.google_compute_subnetwork.vpc_subnet_workload[0]
module.workload.google_compute_firewall.ssh_intranet_workload
module.workload.google_compute_instance.server_host
module.workload.google_service_account.service_account_workload
module.cloud_dns.google_compute_firewall.allow_cloud_dns[0]
module.cloud_dns.google_dns_managed_zone.dns_forward_zone["appseg1"]
module.cloud_dns.google_dns_managed_zone.dns_forward_zone["appseg2"]`