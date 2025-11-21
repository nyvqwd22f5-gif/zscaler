# Predefined Roles and Permissions
Source: https://help.zscaler.com/zpc/predefined-roles-and-permissions
PDF: https://help.zscaler.com/pdf/com/en/1459056.pdf

Zscaler Posture Control (ZPC) provides a set of predefined roles and permissions that you can assign to groups. All users within that group are assigned the same predefined role.
Administrators with a View Only role cannot perform any create, read, update, and delete (CRUD) operations or export any data. The **Actions** column in the table and the **Export** icon across the ZPC Admin Portal are hidden for this role.
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
-
-
-
| Predefined Role | Modules | Sub Modules | Permissions |
| --------------- | ------- | ----------- | ----------- |
| Administrator | All | All | All |
| View Only Administrator | All | All | View OnlySave Investigation |
| Security Operations (SecOps) | AlertsCloud PostureInvestigationPolicies | All | All |
| Administration | Administrators and Groups | View Administrators and GroupsEdit AdministratorExport Administrators and Groups |
| Integrations | View Integrations |
| Analytics | Executive Report | All |
| Compliance Auditor | Cloud Posture | Compliance | All |
| Administration | Administrators and Groups | Add AdministratorEdit AdministratorExport Administrators and Groups |
| Scheduled Reports | All |
| IaC Administrator | Administration | Version Control & CI/CD SystemsWorkstations & IDEs | All |
| Administrators and Groups | Add AdministratorEdit AdministratorDelete AdministratorAdd GroupEdit GroupDelete GroupView Administrators and GroupsExport Administrators and Groups |
| Integrations | View Integrations |
| Policies | IaC Policies | All |
| Alerts | IaC Alerts | All |
| IaC Developer | Administration | Workstations & IDEs | All |
| IT Administrator | Administration | Scheduled ReportsIntegrationsWorkstations & IDEsVersion Control & CICD SystemsSingle Sign-OnContainer Registries & WorkloadsCloud AccountsBusiness Unit ManagementAudit Logs | All |
| Administrators and Groups | Add AdministratorEdit AdministratorDelete AdministratorAdd GroupEdit GroupDelete GroupView Administrators and GroupsExport Administrators and Groups |
| Role Management | Edit RoleView RoleExport Role |
| Analytics | Executive Report | All |
| Vulnerability Administrator | Administration | Container Registries & Workloads | All |
| Administrators and Groups | View Administrators and GroupsEdit AdministratorExport Administrators and Groups |
| Cloud Posture | Vulnerability Management | All |
| Vulnerability Viewer | Administration | Container Registries & Workloads | View Only |
| Cloud Posture | Vulnerability Management | View Only |
| Kubernetes Onboarding | Administration | Cloud Accounts | Add KSPM IntegrationsEdit KSPM IntegrationsView KSPM Integrations |
| LocalPlatformAgent (System Role) | System role used by subsystems for local scanning agent |  |  |