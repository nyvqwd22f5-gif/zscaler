# Creating a New Investigation
Source: https://help.zscaler.com/dspm/creating-new-investigation
PDF: https://help.zscaler.com/pdf/com/en/1477771.pdf

[Watch a video on Investigation with DSPM.](https://fast.wistia.net/embed/iframe/my630v87t6)
You can choose to investigate a resource when required. For example, you might want to investigate publicly accessible virtual machines that have admin permissions or EC2 instances that contain sensitive data. To learn more, see [About Investigation](/dspm/about-investigation).
To create a new investigation:
- Go to **Analytics** > **Investigation**.
-
On the **Investigation** page, click **New Investigation**.
[See image.](#ds-addnew)
- On the** New Investigation** page, select the cloud type (AWS, Azure, or GCP).
- Build the investigation query by adding the required predicates.
- [View the list of predicates and operators](#ds-buildquery)
-
Click **Run Query** to see the results.
[See image.](#ds-result)
-
Click the **Resource Name** to view additional details in the drawer.
[See image.](#ds-resourcedrawer)
-
Click **Save as Policy** if you want to convert this query into a custom policy. You are directed to the **Create Policy** page. Add additional predicates, as required, and save the policy. To learn more, see [Creating Custom Policies](/dspm/creating-custom-policies).
[See image.](#ds-saveaspolicy)
-
Click **Export** to export the data and [download the report](/dspm/about-reports) as an Excel file.
[See image.](#ds-exporticon)
- Click **Save Investigation**.
-
In the **Save Investigation** window, enter a name for the investigation.
[See image.](#ds-name)
-
Click **Save**.
The investigation is displayed on the **Saved** tab.
[See image.](#ds-savedqueries)
[]
Primary resources are the [main data stores](/dspm/supported-data-stores) that DSPM scans for sensitive data. You can build investigation queries and custom policies to identify what type of secondary resources and entities (users, services, roles, databases, virtual machines, etc.) have access to the primary resource and how they are associated with the primary resource. You can also query if there are vulnerabilities in the primary and secondary resources and evaluate their security posture. The investigation results enable you to evaluate and remediate the issues and ensure the resources and sensitive data are secure.
DSPM offers predicates and operators in the following categories to build highly contextual queries:
- [Property](#ds-property)
- [Access](#ds-asset)
- [Relationship](#ds-relationship)
- [Entitlement](#ds-entitlement)
- [Data](#ds-data)
- [Vulnerability](#ds-vulnerability)
- [Posture](#ds-posture)
- The combination of predicates and operators is specific to each primary resource.
- You can select multiple values when using the Like (%), Not Like !(%), iLike (i%), and Not iLike !(i%) operators.
[See image.](#ds-queryanimation)
[]You can use various attributes to identify what type of entities are associated with the primary resource. You can use a combination of operators and conditions to build the query.
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
| Resource Property Predicates | Description | Operators |
| ---------------------------- | ----------- | --------- |
| Resource ID | Returns the resource ID of the primary resource. | = : Is≠ : Is not⊆ : Included In∋ : Contains |
| Resource Name | The name of the resource, as defined by the cloud service provider (CSP). | = : Is≠ : Is not⊆ : Included In∋ : Contains(%) : Likei% : iLike (Applicable only for Azure resources.) |
| Resource Property | Search the resource metadata (JSON file) for the attributes mentioned. | = : IsTrueFalse≠ : Is not⊆ : Included InTrueFalseDoesn't ExistNullYou can select multiple values. For example, ⊆ (Included In) [Value 1] OR [Value 2] OR [Doesn't Exist].⊈ : Not Included In<= : Less or equal>= : Greater or equal< : Less than> : Greater than= : On date|… : After date…| : Before date|...| : Between∋ : Contains∌ : Doesn't Contain[≠] : Is not (No match for all array records.)[⊈] : Not included in (No match for all array records.)∅ : NullO : Not Null× : Doesn't exist(%) : Like!(%) : Not Like[!(%)] : Not Like (No match for all array records.)i% : iLike!(i%) : Not iLike (Applicable only for Azure resources.)And: Use this operator to select the object's multiple attributes when the resource metadata property is part of an array of multiple objects (e.g., In AWS, find Resources Where Primary Resource Type == "EC2 Instance", Resource Property "EC2 Instance".Instance.BlockDeviceMappings[*] .Ebs.Status == Enabled And .Ebs.VolumeID == ID123456789).List: Select a set of values (e.g., Regions (List) includes a list of regions that can be queried for sensitive data.) |
| Tags | The tags associated with the resource. You can select multiple keys. | = : Is≠ : Is not⊆ : Included In⊈ : Not Included In(%) : Like!(%) : Not Like |
| Region | The region where the resource is located. | = : Is≠ : Is not⊆ : Included In∋ : Contains∌ : Doesn't Contain!(%) : Not Like |
| Account | The account in which the resource is stored. | = : Is≠ : Is not⊆ : Included In∋ : Contains |
| MFA required for login | Whether MFA is required for login. | TrueFalse |
| Data Store | The main data store type. | **=** : Is |
[]Access predicates define the network access levels for the resource.
-
-
| Access Predicates | Description | Operators |
| ----------------- | ----------- | --------- |
| Publicly Accessible | Returns "true" if the resource can be accessed from the internet. | TrueFalse |
| Public Exposure Details | Returns a JSON object that contains the details of the public exposure. For example, in case of a network level exposure, the object contains the exposed ports and IP ranges. | Enter key and value |
[]Use the relationship predicates to identify the secondary resources that are associated with or can access the primary resource, check the security posture of the primary resource, whether the primary resource has vulnerabilities, malware, etc.
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
- [](https://nvd.nist.gov/)
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
- [](https://threatlibrary.zscaler.com/)
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
| Relationship Predicates | Description | Additional Predicates | Operators/Conditions/Resource Types |
| ----------------------- | ----------- | --------------------- | ----------------------------------- |
| Has Package | The package installed in the resource. | Package NamePackage Version |  |
| Has Data | Check the type of the detected data. | You can use the following predicates to identify the specific data types:Is Sensitive: Returns "true" if the resource contains sensitive data.DLP Engine: Describes the DLP engines.Dictionary: Describes the dictionaries.Document Type: Select the required document type.Document Category: Describes the document category.Sensitive Data Triggers: Enter the number of DLP trigger matches that the resource permits.Sensitive Data Matches: Enter the number of sensitive files/tables that the resource permits.Sensitive Data Volume: Enter the permitted file size value of the files containing sensitive information (in KB).Last Completed Scan: Returns the time stamp when the resource was last scanned successfully. | = : Is≠ : Is not⊆ : Included In⊈ : Not Included In**>** : Greater than**≥** : Greater or equal**< **: Less than**≤** : Less than or equal= On date|... Before date...| After date|...| Between< Less than> More than |
| Has Vulnerability | Check for the specific vulnerability details. | CVE ID: Returns the CVE ID as defined in the National Vulnerability Database (NVD). You can select a predefined list of vulnerabilities, allowing you to query multiple values at the same time.CVSS Score: Returns the numeric open industry standard for assessing the severity of the vulnerability.CVE Severity: Returns the CVE severity as defined in the NVD.Age of CVE: Returns the age of the vulnerability discovery as defined in the NVD.Package Name: Search for a specific package name that is affected by a vulnerability.Package Version: Search for a specific package version that is affected by a vulnerability.Fix Available: Returns "true" if a fix is available as defined in the NVD. |  |
| Has Access to | The secondary resources that can access the primary resource. You can select multiple resource types. |  |  |
| Associated with | The relationship between this resource and another associated resource. You can select multiple resource types. |  |  |
| Has Password | Whether the resource is password protected or not. |  |  |
| Can be accessed by | IAM entities can be a service, user, or a role that can access the primary resource. | You can use the following additional predicates and operators, allowing you to build the query with more granularity:Entity ID: Enter the entity ID.Account: Select the account that is associated with the entity.Region: Select the region where the account is located.Tags: Select the tags associated with the entity.Action over Parent Resource: Define the actions that the accessing resource can apply to the parent resource.Access Level over Parent Resource: Define the access level (Full Access, Edit, Read) that the accessing resource can apply to the parent resource.Has Access To: Relationship to another resource that can be accessed by the current resource.Via Role: The entity accesses the primary resource via a role that is assigned to another entity.The following additional predicates are available only for GCP resources:Has Service Account Keys: The service account keys associated with the resource. The following sub-predicates are available:Expiry: The date when the service account key expires.Created On: The date when the service account key was created.Type: Classification of key types, whether they are user-managed or system-managed.This predicate is not available for the unmanaged Azure Microsoft SQL server and unmanaged Azure PostgreSQL server. | **=** : Is**≠** : Is not**⊆** : Included In**⊈** : Not Included In |
| Has Entitlement | Relationship to all entitlements granted to the resource. | When you select this predicate, the following additional conditions are available:Access Level: Check the access level (Full Access, Read, Edit) of the entity.Allowed Action: Define the action that the entitlement permits.Over Resource: The primary resource has entitlement over another resource. | This predicate is shown only for the following resource types:**AWS**EC2 InstanceLambda FunctionIAM UserIAM External UserIAM Unmanaged UserOrganizations AccountExternal AccountIAM RoleIAM External RoleIAM Federated User**Azure**Virtual MachineAzure App ServiceUserService PrincipalsApplications (App Registrations)Managed Identities (User Assigned or System Assigned)IAM Roles**GCP**Virtual MachineApp EngineUsersService AccountsIAM Roles |
| Has Access Keys | Whether the resource has access keys and whether it is rotated or not. |  |  |
| Has Malware | Whether the resource contains malware. Malware is detected in AWS S3 buckets, Azure virtual machines and storage accounts, and GCP storage buckets. | When you select this predicate, the following predicates are available:Is Malware: Check if the resource contains malware.Malware Category: Check if the resource contains malware of a specific category.Malware Name: Check if the resource contains malware with a specific name.Detection Accuracy Level: Check the accuracy level to determine if this is malware. | = : Is⊆ : Included In(%) : Like |
| Has Models | Whether the resource contains the AI model or not. | Model Name: Search for specific models either in AI deployment instances or resources.Model Format: Search and filter by a specific model name.Model Version: Search for the model version. |  |
| Has AI/ML Package | Whether the resource contains AI/ML package or not. | Package Name: Search for the name of the AI package.Package Publisher URL: Search for link to the package homepage where the package is published.Package Type: Search for the type of AI package.Package Language: Search for the language of the AI package.Package Version: Search for the version of the AI package.Package Has Vulnerability: Check for vulnerability in the AI package. |  |
[]Use the entitlement predicates to identify the secondary resource's access level and the type of actions it can perform on the primary resource.
-
-
-
-
-
-
-
| Entitlement Predicates | Description | Additional Predicates | Operators |
| ---------------------- | ----------- | --------------------- | --------- |
| Has Access to | Access to all entitlements granted to the resource. | Access Level: Full Access, Read, or Edit.Allowed Action: Define the action that the entitlement permits. | = : Is≠ : Is not⊆ : Included In(%) : Likei% : iLike (Applicable only for Azure resources.) |
[]Use the vulnerability predicate to check if the resource contains vulnerabilities.
-
-
| Vulnerability Predicate | Description | Operator |
| ----------------------- | ----------- | -------- |
| Is Vulnerable | Check if the resource contains packages with vulnerabilities. | TrueFalse |
[]Use the posture predicates to check if security policies are enabled or disabled for resources.
- [AWS](#ds-awsposturepredicate)
- [Azure](#ds-azureposturepredicate)
- [GCP](#ds-gcp-posture)
- [Snowflake](#ds-snowflalkeposture)
[]
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
| Posture | Description | Operator | Value |
| ------- | ----------- | -------- | ----- |
| Encrypted | The encryption type applied to the resource. | **=** : Is**≠** : Is not**⊆** : Included In**⊈** : Not Included In | AWS Managed KeysCustomer Managed KeysEncryptedNot EncryptedPlatform Managed Keys |
| Logging | Returns the logging state of the resource. | **=** : Is**≠** : Is not**⊆** : Included In**⊈** : Not Included In | Data LogsFlow LogsManagement LogsEnabledDisabledPartial |
| Data Retention | The data retention policy for the resource. | **=** : Is**≠** : Is not | EnabledDisabled |
| Backup | The data backup policy that is applied to the primary resource. | **=** : Is**≠** : Is not | EnabledDisabled |
| Guardrails | Check if Guardrails is enabled or not for an AWS Bedrock Agent. |  | EnabledDisabled |
[]
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
| Posture | Description | Operator | Value |
| ------- | ----------- | -------- | ----- |
| Encrypted | The encryption type applied to the resource. | **=** : Is**≠** : Is not**⊆** : Included In**⊈** : Not Included In | Platform Managed KeysCustomer Managed KeysPlatform and Customer Managed Keys (managed disk only)EncryptedNot Encrypted |
| Logging | Returns the logging state of the resource. | **=** : Is**≠** : Is not**⊆** : Included In**⊈** : Not Included In | EnabledDisabledUnmanaged PostgreSQL Server:Partial |
| Data Retention | The data retention policy for the resource. | **=** : Is**≠** : Is not | EnabledDisabled |
| Backup | The data backup policy that is applied to the primary resource. | **=** : Is**≠** : Is not | EnabledDisabled |
| Exposed to AI service | Returns "true" if the resource is exposed to an AI service, such as Azure AI Foundry. | **=** : Is | truefalse |
[]
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
| Posture | Description | Operator | Value |
| ------- | ----------- | -------- | ----- |
| Encrypted | The encryption type of the resource. | **=** : Is**≠** : Is not**⊆** : Included In**⊈** : Not Included In | Customer Managed KeysPlatform Managed Keys |
| Logging | The date the resource was created in the cloud environment. | **=** : Is**≠** : Is not**⊆** : Included In**⊈** : Not Included In | All logsData Access Admin ReadData Access ReadData Access WriteGCP Cloud SQL Instance:EnabledDisabledGCP Compute Instance:All logsData Access Admin ReadData Access ReadData Access WriteOps Agent Logs |
| Data Retention | The data retention policy for the resource. | **=** : Is | EnabledDisabled |
| Backup | The data backup policy for the resource. | **=** : Is**≠** : Is not | EnabledDisabled |
[]
-
-
-
-
-
-
| Posture | Description | Operator | Value |
| ------- | ----------- | -------- | ----- |
| Data Retention | The data retention policy for the resource. | **=** : Is | EnabledDisabled |
| Is Dormant | Check if the user has logged in over the last 90 days. |  | truefalse |
| Stale Access Keys | Check if the access keys have been rotated in the last 90 days. | = : Is | truefalse |
[]The Has Data predicate can be used to check if the resource contains sensitive data, document types, document categories, and identify the DLP engines and dictionaries that match the content in the resource, check for the volume of sensitive data, and more.
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
| Predicate | Description | Operators |
| --------- | ----------- | --------- |
| Is Sensitive | Check if the resource contains sensitive data or not. | **=** : Is |
| Dictionary | Dictionaries matching the content in the resource. | **=** : Is**≠** : Is not**⊆** : Included In**⊈** : Not Included In |
| DLP Engine | DLP engines matching the content in the resource. | **=** : Is**≠** : Is not**⊆** : Included In**⊈** : Not Included In |
| Document Type | The document type matches the content in the resource. | **=** : Is**≠** : Is not**⊆** : Included In**⊈** : Not Included In |
| Document Category | The document category matches the content in the resource. | **=** : Is**≠** : Is not**⊆** : Included In**⊈** : Not Included In |
| Sensitive Data Triggers | The number of DLP trigger matches. | **=** : Is**≠** : Is not**>** : Greater than**≥** : Greater or equal**< **: Less than**≤** : Less than or equal |
| Sensitive Data Matches | The number of matched sensitive data or tables. | **=** : Is**≠** : Is not**>** : Greater than**≥** : Greater or equal**< **: Less than**≤** : Less than or equal |
| Sensitive Data Volume | The volume of sensitive data found in the data store and the size (in KB) of the file containing sensitive data. | **=** : Is**≠** : Is not**>** : Greater than**≥** : Greater or equal**< **: Less than**≤** : Less than or equal |
| Last Completed Scan | The date when the data store was last scanned successfully. | Select a date from the calendar |
[]![ds-investigationquery.gif](/downloads/dspm/ds-investigationquery.gif)
[]![Viewing the results of the query](/downloads/DOC-52620%20-%20Investigation%20Results.png)
[]![Add a new investigation](/downloads/dspm/investigation/creating-new-investigation/ds-addnewbutton.png)
[]![Provide a name for the investigation](/downloads/dspm/investigation/creating-new-investigation/ds-investigate-name.png)
[]![View the resource details](/downloads/dspm/investigation/creating-new-investigation/ds-investigate-resourcedetails.png)
[]![View the saved investigations](/downloads/dspm/investigation/creating-new-investigation/ds-savedtab.png)
[]![Save the query as a policy](/downloads/dspm/analytics/investigation/creating-new-investigation/ds-savequeryaspolicynew.png)
[]![Export the data](/downloads/dspm/analytics/investigation/creating-new-investigation/ds-exportquery.png)