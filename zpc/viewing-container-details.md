# Viewing the Container Details
Source: https://help.zscaler.com/zpc/viewing-container-details
PDF: https://help.zscaler.com/pdf/com/en/1447696.pdf

You can view additional details of the containers with vulnerabilities, so you can further investigate and remediate the issue.
To view the container details:
- Go to **Cloud Posture > Vulnerability Management**.
- Select the **Containers **tab.
[See image.](#container-tab)
- Click the **Container** to view a drawer with the following details:
- **Container Details**: For each container, you can see:
- **Cluster Type**: The type of Kubernetes cluster (Amazon Elastic Kubernetes Service (EKS)).
- **Cluster**: The name of the Kubernetes cluster.
- **Publicly Exposed**: Whether the container is publicly exposed or not.
- **Namespace**: The namespace associated with the Kubernetes cluster.
- **Repository Name**: The repository in which the container resides.
- **Image**: URI of the image used in the container.
- **Image Digest**: Unique identifier for the specific version of the image.
- **Last Scanned Date**: The date when the scan was last performed.
- **Scan Status**: The status of the vulnerability scan (Success, Failed, or Not Scanned).
- **Vulnerabilities**: The total number of vulnerabilities associated with this container.
- **Vulnerabilities**: The table shows the list of CVE IDs along with the severity, CVSS score, package name, package version, package path, fix version, and whether the fix is available. You can use the filters to view specific data or search for the required CVE ID. Click the CVE ID to view the CVE details. [See image.](#cve-details)
[See image.](#container-drawer)
[![View the container image details](/downloads/zpc/container-registries-workloads/vulnerability-management/viewing-container-details/zpc-vm-container-drawer.png)
]
[![View the Containers tab](/downloads/zpc/container-registries-workloads/vulnerability-management/viewing-container-details/zpc-vm-page.png)
]
[![View the CVE details](/downloads/zpc/container-registries-workloads/vulnerability-management/viewing-container-image-details/zpc-vs-cvedetails.png?1678684281)
]