# Viewing the Alert Graph
Source: https://help.zscaler.com/dspm/viewing-alert-graph
PDF: https://help.zscaler.com/pdf/com/en/1492596.pdf

DSPM displays the [alert details](/dspm/viewing-alert-details) in the form of an interactive graph for better understanding. The alert graph visually represents an alert resulting from a [policy](/dspm/about-data-posture-policies) evaluation performed on a specific data store. It consists of interactive nodes that provide contextual information (i.e., type of sensitive data present in the data store, if the data store is publicly exposed, the vulnerabilities associated with the data store, [malware](/dspm/viewing-malware-details) present in the data store about each entity associated with the primary resource).
The alert graph is a subset of the [Resource Inventory graph](/dspm/viewing-resource-inventory-graph) with the following differences:
- The sensitive data path represents only the associated resources that contain sensitive data along with matched DLP engines. For example, if a virtual machine is associated with three disks out of which two disks contain sensitive data, then the alert graph displays only those two disks with sensitive data along with matched DLP engines.
-
The vulnerabilities found in the resources are displayed in CVE or package node based on the policy. For example, if the primary resource contains packages with vulnerabilities, the alert graph displays a package node that lists the vulnerable packages. Click View All Packages to view all the packages associated with the resource on the [Vulnerabilities](/dspm/viewing-vulnerability-details) tab.
[See image.](#primary-resource)
-
The IAM nodes (users, services, external, etc. that have access to the primary resource) are displayed as entity in the alert graph.
[See image.](#entityresource)
If an entity contains vulnerabilities, you can view the details on the Vulnerabilties tab. To view the vulnerabilities:
-
[]Click the entity node and then click **ARN** or **ID**.
[See image.](#entity-node-drawer)
The drawer displays entity details along with the number of vulnerabilities associated with the entity based on the severity.
[See image.](#count-vulnerabiltiies)
-
Click the number to view additional details.
[See image.](#vulnerabilities-tab)
The alert graph is interactive only for [open and snoozed](/dspm/alert-status) alerts. For resolved and closed alerts, the graph is frozen and the nodes are unclickable. The graph is reactivated for a resolved alert only when you reset it and the alert moves to the open state based on the latest policy findings.
To view the alert graph:
- Go to **Alerts** > **Alert Views** > **Alerts**.
- Select the **All Alerts** tab.
- Click any **Alert ID** to view the drawer.
-
On the **Alert Details** tab, you can see a graph with several nodes and attack paths.
[See image.](#alert-graph)
[]![View the alert graph](/downloads/dspm/alerts/alert-details/viewing-alert-graph/dspm-azure-alert-graph.png)
[]![Viewing the CVEs for the primary resource](/downloads/dspm/alerts/alert-details/viewing-alert-graph/dspm-package-vulnerabilities_0.png)
[]![Viewing the entity resource](/downloads/dspm/alerts/alert-details/viewing-alert-graph/dspm-alert-graph-entity.png)
[]![Viewing the number of vulnerabilities](/downloads/dspm/alerts/alert-details/viewing-alert-graph/dspm-vulnerabilities-count.png)
[]![Viewing the entity node drawer](/downloads/dspm/alerts/alert-details/viewing-alert-graph/dspm-entity-node-drawer.png)
[]