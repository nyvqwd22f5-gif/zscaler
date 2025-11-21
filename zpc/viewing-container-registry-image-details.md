# Viewing the Container Registry Image Details
Source: https://help.zscaler.com/zpc/viewing-container-registry-image-details
PDF: https://help.zscaler.com/pdf/com/en/1417191.pdf

You can view additional details of the container registry images with vulnerabilities, so you can investigate and take the necessary action.
To view the container registry image details:
- Go to **Cloud Posture > Vulnerability Management**.
- Select the **Container Registry Images** tab to view the list of image tags.
[See image.](#registry-tab)
- Click the **Image Tag** to view the following details:
- **Image Details**: The details of that particular image tag.
- **Last Push Date**: The date when the image was last pushed into the repository.
- **Last Scan Date**: The date when the image was last scanned by ZPC.
- **Scan Status**: The status (Not Scanned, Completed, or Failed) of the vulnerability scan.
- **Scan Description**: The details of the scan.
- **Vulnerabilities**: The total number of vulnerabilities detected in the container image.
- **Vulnerabilities**: The table shows the list of CVE IDs along with the severity level, CVSS score, package name, package version, package path, fix version, and whether the fix is available. You can use the filters to view specific data or search for the required CVE ID. Click the CVE ID to view the CVE details. [See image.](#cve)
[See image.](#registry-drawer)
[![View the Container Registry tab](/downloads/zpc/container-registries-workloads/vulnerability-management/viewing-container-registry-image-details/zpc-vm-contregistry-tab.png)
]
[![View the container registry image details](/downloads/zpc/container-registries-workloads/vulnerability-management/viewing-container-registry-image-details/zpc-vm-containerregistry-packagepath.png)
]
[![View the CVE details](/downloads/zpc/vulnerability-integrations/vulnerability-management/viewing-container-registry-image-details/zpc-vm-vuln-properties.png)
]