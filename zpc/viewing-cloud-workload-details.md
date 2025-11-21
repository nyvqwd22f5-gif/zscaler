# Viewing the Cloud Workload Details
Source: https://help.zscaler.com/zpc/viewing-cloud-workload-details
PDF: https://help.zscaler.com/pdf/com/en/1417196.pdf

You can view additional details of the cloud instances that contain vulnerabilities, so you can investigate and take the necessary action.
To view the cloud instance details:
- Go to **Cloud Posture > Vulnerability Management**.
- Click the **Cloud Workloads** tab.
[See image.](#workload-tab)
- Click the **Instance** to view the following details:
- **Instance Details**: The details of that particular instance.
- **Availability Zone**: The availability zone where the cloud workload resides.
- **Region**: The region where the cloud workload resides.
- **Publicly Exposed**: Whether the cloud workload is publicly exposed or not.
- **Image ID**: The source machine image that is used to create the workload.
- **Platform**: The operating system (OS) platform that is running in the workload (Linux, UNIX, or Windows).
- **Operating System**: The running OS name and its version.
- **VPC**: The virtual private cloud (VPC) and the virtual network (VNet) that hosts the cloud workload.
The VNet information is displayed after the cloud workloads are scanned for vulnerabilities.
- **Scan Status**: The vulnerability scan status along with a detailed description.
- [Scan status and details](#scanstatus)
- **Last Scanned Date**: The date when the scan was last completed.
- **Business Unit**: The name of the [business unit](/zpc/about-business-units) that is associated with the cloud workload.
- **Vulnerabilities**: The total number of vulnerabilities detected in the cloud instance.
- **Vulnerabilities**: The table shows the list of CVE IDs along with the severity, CVSS score, package name, package version, package path, fix version, and whether the fix is available. You can use the filters to view specific data or search for the required CVE ID. Click the CVE ID to view the CVE details. [See image.](#cvedetails)
[See image.](#cloudinstance-drawer)
[![View the Cloud Workload details](/downloads/zpc/vulnerability-integrations/vulnerability-management/viewing-cloud-workload-details/zpc-vm-cloudworkload-tab.png)
]
[![View the cloud instance details](/downloads/zpc/container-registries-workloads/vulnerability-management/viewing-cloud-workload-details/zpc-vm-cloudinstance-drawer.png?1685699511)
]
[![View the CVE details](/downloads/zpc/vulnerability-integrations/vulnerability-management/viewing-cloud-workload-details/zpc-vm-cve-workload.png)
]
- **[]Completed**: Workload is scanned successfully.
- **Not Scanned**: Workloads that did not match any scanning rules.
- **Failed**: User intervention is required to solve the permission issues.
- **Unsupported**: This status is shown in the following scenarios:
- Instance is running either an unsupported OS or a virtual appliance.
- Instance root volume is using an unsupported file system.
- ZPC does not support the scanning of workloads using unmanaged disks.
- ZPC does not support the scanning of workloads encrypted using Azure disk encryption.
- ZPC does not support the scanning of workloads using customer-supplied encryption keys.
- ZPC does not support the scanning of marketplace AMI images.
- Region is not supported**.**