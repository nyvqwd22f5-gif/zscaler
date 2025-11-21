# IAM Roles and Permissions for GCP
Source: https://help.zscaler.com/dspm/iam-roles-and-permissions-gcp
PDF: https://help.zscaler.com/pdf/com/en/1498651.pdf

As part of the onboarding process, you need to deploy DSPM templates in the Google Cloud Platform (GCP) project. These templates create service accounts and access management (IAM) roles that DSPM requires to connect to the GCP project, discover the resources, and scan data. Each role has permissions for various services and actions, such as resource discovery, data scanning, etc.
IAM Roles
DSPM creates the following IAM roles and service accounts to access the GCP projects:
- [Discovery Service Account](#resource-discovery-role)
- [Orchestrator Service Account](#orchestrator-role)
- [Scanner Service Account](#scanner-role)
- [Target Role](#target-role)
[]This service account is used to perform scan-related tasks on data stores present in monitored projects onboarded in DSPM. The service account is assigned the following Managed Roles, which provide the necessary permissions:
- Storage Object Viewer
- Cloud KMS CryptoKey Encrypter or Decrypter
- Service Usage Consumer
| Permission | Scope | Purpose |
| ---------- | ----- | ------- |
| `storage.managedFolders.list` | Monitored Projects | To get managed folders of buckets |
| `cloudkms.cryptoKeyVersions.useToDecrypt` | Monitored Projects | To decrypt resources for scans |
| `cloudkms.cryptoKeyVersions.useToEncrypt` | Monitored Projects | To encrypt resource for scans |
| `cloudsql.backupRuns.create` | Monitored Projects | To create latest cloud SQL backup |
| `cloudsql.backupRuns.delete` | Monitored Projects | To delete cloud SQL backups |
| `cloudsql.backupRuns.get` | Monitored Projects | To get latest cloud SQL backup |
| `cloudsql.backupRuns.list` | Monitored Projects | To list latest cloud SQL backups |
| `cloudsql.instances.get` | Monitored Projects | To get cloud SQL instances |
[]This service account is used by the scanner instance to perform scan-related tasks. The service account is assigned the following Managed Roles, which provide the necessary permissions:
- Storage Object Viewer
- Cloud KMS CryptoKey Encrypter or Decrypter
- Viewer
- Logs View Accessor
- Service Usage Consumer
- Service Account User
- Service Account Token Creator
| Permission | Scope | Purpose |
| ---------- | ----- | ------- |
| `logging.logEntries.list` | Monitored Projects | To list log entries from log views |
| `secretmanager.versions.access` | Monitored Projects | To access Zscaler DSPM secret version |
[]This service account is used by the orchestrator instance to perform scan and management operations. The service account is assigned the following Managed Roles, which provide the necessary permissions:
- Viewer
- Service Usage Consumer
- Service Account User
- Cloud KMS CryptoKey Encrypter or Decrypter
- Service Account Token Creator
| Permission | Scope | Purpose |
| ---------- | ----- | ------- |
| `compute.disks.use` | Orchestrator Project | To create Zscaler DSPM scanner instance disk |
| `compute.instances.attachDisk` | Orchestrator Project | To attach Zscaler DSPM scanner instance disk |
| `compute.instances.detachDisk` | Orchestrator Project | To detach Zscaler DSPM scanner instance disk |
| `compute.instances.delete` | Orchestrator Project | To delete Zscaler DSPM scanner instance |
| `compute.instanceGroups.update` | Orchestrator Project | To update Zscaler DSPM instance group manager |
| `compute.autoscalers.update` | Orchestrator Project | To update Zscaler DSPM instance group manager |
| `secretmanager.versions.access` | Orchestrator Project | To access Zscaler DSPM secret version |
| `compute.subnetworks.use` | Orchestrator Project | To attach Zscaler DSPM scanner instance to its subnetwork |
| `compute.instances.setMetadata` | Orchestrator Project | To create Zscaler DSPM scanner instance |
| `compute.instances.setLabels` | Orchestrator Project | To create Zscaler DSPM scanner instance |
| `compute.instances.setMachineType` | Orchestrator Project | To create Zscaler DSPM scanner instance |
| `compute.instances.setName` | Orchestrator Project | To create Zscaler DSPM scanner instance |
| `compute.instances.setServiceAccount` | Orchestrator Project | To assign Zscaler DSPM scanner instance service account |
| `cloudsql.instances.get` | Orchestrator Project | To get the restored cloud SQL instance details |
| `cloudsql.instances.list` | Orchestrator Project | To list the restored cloud SQL instances |
| `cloudsql.instances.delete` | Orchestrator Project | To delete the restored cloud SQL instances |
| `resourcemanager.projects.get` | Orchestrator Project | To retrieve the project details |
| `cloudsql.backupRuns.get` | Orchestrator Project | To get restored latest cloud SQL instance backup |
| `cloudsql.instances.restoreBackup` | Orchestrator Project | To restore latest cloud SQL backup |
| `cloudsql.users.update` | Orchestrator Project | To update restored cloud SQL user |
| `secretmanager.secrets.delete` | Orchestrator Project | To delete Zscaler DSPM secret |
| `secretmanager.secrets.update` | Orchestrator Project | To update Zscaler DSPM secret |
| `secretmanager.versions.add` | Orchestrator Project | To add Zscaler DSPM secret version |
| `compute.instances.create` | Orchestrator Project | To create Zscaler DSPM scanner instance |
| `compute.disks.create` | Orchestrator Project | To create Zscaler DSPM scanner instance disk |
| `cloudsql.instances.create` | Orchestrator Project | To create the restored cloud SQL instance |
| `secretmanager.secrets.create` | Orchestrator Project | To create Zscaler DSPM secret |
| `cloudsql.users.create` | Orchestrator Project | To create restored cloud SQL user |
| `logging.sinks.get` | GCP Organisation | To update Zscaler DSPM org log sink for buckets incremental scans |
| `logging.sinks.list` | GCP Organisation | To update Zscaler DSPM org log sink for buckets incremental scans |
| `logging.sinks.update` | GCP Organisation | To update Zscaler DSPM org log sink for buckets incremental scans |
[]This service account is used by DSPM to discover resources in the GCP projects and to instruct Local Scanner Platform to perform scan-related instructions. The service account is assigned the following Managed Roles, which provide the necessary permissions:
- Viewer
- Organization Policy Viewer
- Folder Viewer
- Service Usage Consumer
- Service Account User
- Security Reviewer
- Cloud Asset Viewer
| Permission | Scope | Purpose |
| ---------- | ----- | ------- |
| `storage.buckets.get` | Monitored Projects | To get storage buckets metadata |
| `storage.managedfolders.get` | Monitored Projects | To get managed folders metadata |
| `storage.managedfolders.list` | Monitored Projects | To list the managed folders |
| `storage.buckets.getIamPolicy` | Monitored Projects | To get the storage bucket's IAM policy metadata |
| `storage.managedfolders.getIamPolicy` | Monitored Projects | To get the managed folder's IAM policy |
| `cloudasset.assets.searchAllIamPolicies` | Monitored Projects/Organisation | To get GCP resources IAM policies |
| `compute.autoscalers.update` | Orchestrator Project | To update the Zscaler DSPM instance group manager scaling |
| `compute.instanceGroupManagers.use` | Orchestrator Project | To update the Zscaler DSPM instance group manager scaling |
| `compute.instanceGroupManagers.update` | Orchestrator Project | To update the Zscaler DSPM instance group manager scaling |
| `compute.subnetworks.use` | Orchestrator Project | To attach Zscaler DSPM instance to subnetworks |
| `compute.instances.setMetadata` | Orchestrator Project | To create Zscaler DSPM instance |
| `compute.instances.delete` | Orchestrator Project | To terminate Zscaler DSPM instance |
| `compute.instances.setLabels` | Orchestrator Project | To create Zscaler DSPM instance |
| `compute.instanceTemplates.create` | Orchestrator Project | To create Zscaler DSPM instance template |
| `compute.instances.create` | Orchestrator Project | To create Zscaler DSPM instance |
| `compute.disks.create` | Orchestrator Project | To create Disks for Zscaler DSPM instance |
| `compute.disks.setLabels` | Orchestrator Project | To create Disks for Zscaler DSPM instance |
| `compute.instanceTemplates.delete` | Orchestrator Project | To delete Zscaler DSPM instance template |