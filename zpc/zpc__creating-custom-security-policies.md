# Creating Custom Security Policies
Source: https://help.zscaler.com/zpc/creating-custom-security-policies
PDF: https://help.zscaler.com/pdf/com/en/1392806.pdf

ZPC supports creating custom security policies to expand security coverage to your cloud infrastructure beyond the 300+ predefined security policies.
ZPC offers custom security policies so that you can secure your cloud deployment:
- Add a new custom security policy to an existing protected asset. For example, you can create a custom security policy to control the configuration of a new feature released by your cloud service provider on an existing asset type.
- Add a new custom security policy to asset types that currently do not have predefined security policies. For example, you can create custom security policies to protect a completely new service offered by your cloud service provider.
To create a custom security policy:
- [1. Provide general information.](#general-information)
- [2. Build a query.](#query-builder)
- [3. (Optional) Enter remediation instructions.](#remediation)
- [4. (Optional) Select severity and enter description.](#severity-description)
[]
- On the left pane menu, select **Policies**.
- Click **Create Policy**.
- Select your **Cloud Type**.
- Under **Focus on**, select either **Assets** or **Identities**.
- Click **Next**.
![View the general information tab in custom policy.](/downloads/zpc/policies/creating-custom-security-policies/zpc-custom-policy-general-information.png)
[
ZPC offers the following predicates and respective operators to build highly contextual queries:
Asset Predicates
- [Property](#asset-properties)
- [Access](#asset-access)
- [Relationship](#asset-relationship)
- [Vulnerability](#asset-vulnerability)
Identity Predicates
- [Property](#identity-properties)
- [Source](#identity-source)
- [Authentication](#identity-authentication)
- [Relationship](#identity-relationship)
- [Permission](#identity-permission)
The following predicate values can also be entered via text along with selecting from the available drop-down menu:
- Asset Name
- Asset ID
- Asset Type
- Identity Name
- Identity ID
- Permission Set Name
- Allowed Action
- Permission Set Type
- Group Membership
- Account ID
- CVE ID
- Package Name
- Image ID
Use Cases
Consider the following use cases:
Asset Focus Use Case
Consider that you want to investigate publicly accessible virtual machine instances which have admin permissions.
![View the asset focussed query.](/downloads/zpc/investigation/creating-new-investigation/zpc-asset-focus-query-builder.gif)
Identity Focus Use Case
Consider that you want to investigate powerful human identities that do not have MFA enabled.
![View the identity focussed query.](/downloads/zpc/investigation/creating-new-investigation/zpc-identity-focus-query-builder.gif)
[]
You can use the following asset property predicates:
- [Asset ID](#asset-id-properties)
- [Asset Property](#asset-property-properties)
- [Asset Metadata](#asset-metadata-properties)
- [Asset Name](#asset-name-properties)
- [Asset Type](#asset-type-properties)
- [Cloud Provider](#cloud-provider-properties)
- [Creation Date](#creation-date-properties)
- [Tags](#asset-tags)
- [Clusters](#clusters-properties)
- [Namespaces](#namespaces-properties)
- [Running](#running-properties)
- [Publicly Exposed](#publicly-exposed-properties)
[]
Returns assets that are associated with the specified tags. Accepts the following operators:
- **⊆** : Included In
- **⊈** : Not Included In
[]
The asset property predicate translates the entire asset metadata for all asset types into predicates. The asset metadata describes all the asset attributes as key-value pairs. ZPC ensures a holistic metadata by consolidating the attributes of each asset from the cloud service providers on asset details. For example, information regarding hard drives connected to EC2s is not part of the EC2 metadata on AWS, but ZPC collects the information and presents it as part of the metadata.
ZPC offers a drop-down menu for the asset properties and their corresponding values. ZPC accommodates for attributes with array values and multiple values. ZPC also allows you to search for attributes by entering partial values. For example, the metadata for an Azure VM contains a disk name with multiple statuses. The asset property predicate can find matches across all the available statuses. [See image.](#metadata)
The asset property predicate accepts the following operators:
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
| Property Type | Operators |
| ------------- | --------- |
| String | **=** : Is**≠** : Is not**⊆** : Included In**⊈** : Not Included In**∋** : Contains**∌** : Doesn't Contain**⊇** : Includes**⊉** : Doesn't Include |
| Date | **=** : Is**<=** : Before or on**>=** : After or on |
| Boolean | **=** : Is**≠** : Is not |
| Number | **=** : Is**≠** : Is not**<= **: Less than or Equal**>=** : More than or Equal**⊆** : Included In**⊈** : Not Included In |
| IP Address | **=** : Is**≠** : Is not**⊆** : Included In**⊈** : Not Included In |
Consider the following use case to learn more about using the asset property predicate:
- [Investigate AWS EC2 instances that run Linux, SUSE Linux, or Red Hat Enterprise Linux](#linux-ec2-investigate)
[]
![View the asset property predicate usecase.](/downloads/zpc/investigation/creating-new-investigation/zpc-investigate-asset-property-predicate-usecase.gif)
[]
Returns the asset display name. Accepts the following operators:
- **==** : Equal to
- **!=** : Not equal to
- **in** : Match in a list of values
- **like** : Compare with the **%** wildcard
[]
Returns the asset ID. Accepts the following operators:
- **==** : Equal to
- **!=** : Not equal to
- **in** : Match in a list of values
- **like** : Compare with the **%** wildcard
[]
Returns the cloud service provider where the asset is defined. Accepts the following operators:
- **==** : Equal to
- **!=** : Not equal to
- **in** : Match in a list of values
- **like** : Compare with the **%** wildcard
[]
Returns the asset configuration metadata JSON object. Requests a key-value pair. Accepts the following operators:
- **==** : Equal to
- **!=** : Not equal to
[]
Returns the asset type. Accepts the following operators:
- **==** : Equal to
- **!=** : Not equal to
- **in** : Match in a list of values
- **like** : Compare with the **%** wildcard
[]
Returns the date the asset was created. Accepts the following operators:
- **==** : Equal to
- **≤** : Lesser than or equal to
- **≥** : Greater than or equal to
[]
Returns Kubernetes clusters. Accepts the following operators:
- **=** : Is
- **≠** : Is not
- **⊆** : Included In
- **∋** : Contains
This predicate is only available for investigating Kubernetes clusters.
[]
Returns Kubernetes namespaces. Accepts the following operators:
- **=** : Is
- **≠** : Is not
- **⊆** : Included In
- **∋** : Contains
This predicate is only available for investigating Kubernetes clusters.
[]
Returns true if the kubernetes cluster is running. Accepts the following operator:
**=** : Is
This predicate is only available for investigating Kubernetes clusters.
[]
Returns true if the kubernetes cluster is publicly exposed. Accepts the following operator:
**=** : Is
This predicate is only available for investigating Kubernetes clusters.
[]
The relationship predicates switch to discovering identities related to the described asset. The relationship predicates do not need operators, but opens a nested condition to describe the identity using the identity predicates. You can always use the outer **Add** icon to continue describing the assets.
![View the query builder.](/downloads/zpc/investigation/creating-new-investigation/zpc-investigation-relationship-asset-predicate.png)
You can use the following relationship asset predicates:
- [Can be accessed by Identity](#can-be-accessed-by-identity-relationship)
- [Has Package](#has-package-relationship)
- [Has Identity](#has-identity-relationship)
[]
Create a relationship with all identities that can access the asset.
[]
Returns **True** if the asset is attached to an identity.
[]
Describes the package name or package version of an asset.
[]
You can use the following network access asset predicates:
- [Internet Facing](#asset-internet-facing)
- [Public Exposure Details](#asset-public-exposure-details)
- [Publicly Accessible](#asset-publicly-accessible)
[]
Returns **True** if the asset is exposed to access from the internet. Accepts the following operator:
**==** : Equal to
[]
Returns the public exposure details JSON object. Requests a key-value pair. Accepts the following operators:
- **==** : Equal to
- **!=** : Not equal to
- **like** : Compare with the **%** wildcard
- **≤** : Lesser than or equal to
- **≥** : Greater than or equal to
- **<** : Lesser than
- **>** : Greater than
[]
Returns true if the asset is publicly exposed to the internet. Accepts the following operator:
**=** : Is
[]
You can use the following asset vulnerability predicates:
[Is Vulnerable](#asset-is-vulnerable)
[]
Returns true if the asset has at least one vulnerability found by the ZPC vulnerability scanner. Accepts the following operator:
**=** : Is
[]
You can use the following asset data security predicates:
[Sensitive Data](#sensitive-data-asset)
[]
You can use the following identity property predicates:
- [Is Permission Management](#is-permission-management)
- [Identity Name](#identity-name-properties)
- [Identity ID](#identity-id-properties)
- [Identity Metadata](#identity-metadata-properties)
- [Creation Date](#identity-creation-date-properties)
[]
Returns true if the identity can manage other identities. Accepts the following operator:
**==** : Equal to
[]
Returns the identity name. Accepts the following operators:
- **==** : Equal to
- **!=** : Not equal to
- **in** : Match in a list of values
- **like** : Compare with the **%** wildcard
[]
Returns the Identity ID. Accepts the following operators:
- **==** : Equal to
- **!=** : Not equal to
- **in** : Match in a list of values
- **like** : Compare with the **%** wildcard
[]
Returns the identity configuration metadata JSON object. Requests a key-value pair. Accepts the following operators:
- **==** : Equal to
- **!=** : Not equal to
- **like** : Compare with the **%** wildcard
- **≤** : Lesser than or equal to
- **≥** : Greater than or equal to
- **<** : Lesser than
- **>** : Greater than
[]
Returns the timestamp for when the IAM user was created on the cloud service provider.
- **=** : Is
- **≤** : Lesser than or equal to
- **≥** : Greater than or equal to
- **≬** : Between
[]
You can use the following identity source predicates:
- [Human Identity](#human-identity-source)
- [Local Identity](#local-identity-source)
- [External](#external-source)
[]
Returns true for human identities. Accepts the following operator:
**==** : Equal to
[]
Returns true for local identities. Accepts the following operator:
**==** : Equal to
[]
Returns true for external users. Accepts the following operator:
**==** : Equal to
[]
You can use the following identity authentication predicates:
- [MFA required for login](#mfa-required-for-login-authentication)
- [Can use password](#can-use-password)
- [Can use Access Keys](#can-use-access-keys)
- [Assigned Certificate](#assigned-certificate)
[]
Returns true if the identity needs to use multi-factor authentication. Accepts the following operator:
**==** : Equal to
[]
Returns "Yes" if the IAM user has a password, "No" if the IAM user does not have a password, and "Unknown" for identities that ZPC does not have visibility into. Accepts the following operator:
**=** : Is
Available only for AWS identity focus queries.
[]
Returns "Yes" if the IAM user has an acess key and the access key status is active, "No" if the IAM user does not have an access key, and "Unknown" for identities that ZPC does not have visibility into . Accepts the following operator:
**=** : Is
Available only for AWS identity focus queries.
[]
Returns "Yes" if the IAM user has an X.509 signing certificate and the certificate status is active, "No" if the IAM user does not have signing certificate, and "Unknown" for identities that ZPC does not have visibility into. Accepts the following operator:
**=** : Is
Available only for AWS identity focus queries.
[]
The relationship predicates switch to discovering resources related to the described identity. The relationship predicates do not need operators, but open a nested condition to describe the resource using the resource-specific predicates. You can always use the outer **Add** icon to continue describing the identity.
![View the identity relationship predicates.](/downloads/zpc/investigation/creating-new-investigation/zpc-investigation-identity-relationships.png)
You can use the following identity relationship predicates:
- [Has Password](#has-password-identity-relationship)
- [Has Access Keys](#has-access-keys-identity-relationship)
- [Has Certificate Identity](#has-certificate-identity-relationship)
[]
You can use the following predicates to describe the password in relationship to the identity:
- [Password Last Used](#password-last-used)
- [Password Last Changed](#password-last-changed)
- [Password Next Rotated](#password-next-rotated)
[]
Returns the timestamp for AWS local identities that authenticated on to the AWS website. You can specify the time range using operators and the calendar value drop-down menu. Accepts the following operators:
- **=** : Is
- **≤** : Lesser than or equal to
- **≥** : Greater than or equal to
- **≬** : Between
[]
Returns the timestamp for AWS local identities that had their password changed. You can specify the time range using operators and the calendar value drop-down menu. Accepts the following operators:
- **=** : Is
- **≤** : Lesser than or equal to
- **≥** : Greater than or equal to
- **≬** : Between
[]
Returns the timestamp for AWS local identities that need to have their password changed based on the password policy for the cloud account. You can specify the time range using operators and the calendar value drop-down menu. Accepts the following operators:
- **=** : Is
- **≤** : Lesser than or equal to
- **≥** : Greater than or equal to
- **≬** : Between
[]
You can use the following predicates to describe the access keys in relationship to the identity:
- [Access Key Last Used](#access-key-last-used)
- [Access Key Last Changed](#access-key-last-rotated)
- [Last Used Region](#access-key-last-used-region)
- [Last Used Service](#access-key-last-used-service)
[]
Returns the timestamp for AWS local identities that used an access key to sign an AWS API request. When an access key is used more than once in a 15-minute span, only the first use is recorded in this field on AWS. You can specify the time range using operators and the calendar value drop-down menu. Accepts the following operators:
- **=** : Is
- **≤** : Lesser than or equal to
- **≥** : Greater than or equal to
- **≬** : Between
[]
Returns the timestamp for AWS local identities that had an access key created or changed. You can specify the time range using operators and the calendar value drop-down menu. Accepts the following operators:
- **=** : Is
- **≤** : Lesser than or equal to
- **≥** : Greater than or equal to
- **≬** : Between
[]
Returns the AWS Region where the access key was most recently used. When an access key is used more than once in a 15-minute span, only the first use is recorded in this field on AWS. Accepts the following operators:
- **=** : Is
- **≠** : Is not
- **∋** : Contains
[]
Returns the AWS Service in which the access key was most recently used to access. When an access key is used more than once in a 15-minute span, only the first use is recorded in this field on AWS. Accepts the following operators:
- **=** : Is
- **≠** : Is not
- **∋** : Contains
[]
You can use the following predicates to describe the certificate in relationship to the identity:
- [Certificate Last Rotated](#certificate-last-rotated)
[]
Returns the timestamp for AWS local identities that had a signing certificate created or changed. You can specify the time range using operators and the calendar value drop-down menu. Accepts the following operators:
- **=** : Is
- **≤** : Lesser than or equal to
- **≥** : Greater than or equal to
- **≬** : Between
[]
You can use the following identity permission predicates:
- [Power Score](#power-score-permission)
- [Root](#root-permission)
- [Access Key Enabled](#access-key-enabled-permission)
- [Admin](#admin-permission)
- [Power User](#power-user-permission)
[]
Returns a numerical value between 1-100 which is the identity's power score. Accepts the following operators:
- **==** : Equal to
- **!=** : Not equal to
- **≤** : Lesser than or equal to
- **≥** : Greater than or equal to
- **<** : Lesser than
- **>** : Greater than
[]
Returns true if the identity is a root account. Accepts the following operator:
**==** : Equal to
[]
Returns true if the identity has active access keys. Accepts the following operator:
**==** : Equal to
[]
Returns true if the identity is an administrator in at least one account. Accepts the following operator:
**==** : Equal to
[]
Returns true if the power score for the identity is above 80. Accepts the following operator:
**==** : Equal to
[![View the Cloud Assets Metadata](/downloads/zpc/policies/creating-custom-security-policies/zpc-asset-metadata-array-support_0.png)
]
[]Returns true if the asset has at least one file containing sensitive data detected by the ZPC data security scan. Accepts the following operators:
**=** : Is
]
[]
- On the **Remediation Procedure** tab, click **Add Remediation Procedure**.
- Enter the remediation procedure in Markdown, then click **Save**.
- On the **Recommendations** tab, click **Add Recommendations**.
- Enter the recommendation in Markdown, then click **Save**.
- Click **Next**.
![View the remediation tab in custom policy.](/downloads/zpc/policies/creating-custom-security-policies/zpc-custom-policy-remediation.png)
[]
-
Enter the following information:
- **Policy Name**: The name of the security policy.
- **Policy Description**: The description of the policy.
- **Policy Severity**: Static value signaling the severity of policy failure. The value can be Critical, High, Medium, or Low.
- **Alert Description**: The description of the alert.
- **Threat Category**: The threat category to which the policy belongs.
- **MITRE ATT&CK**: The link to the technique on the MITRE ATT&CK website.
- **Compliance**: The compliance benchmark associated with the policy.
To enter compliance details, the query logic must be focused on assets and the asset type predicate has to be defined.
- **Domain**: The compliance benchmark domain associated with the policy.
- **Control Section**: The control section associated with the compliance benchmark domain of the policy.
- Click **Finish**.
[See image.](#severity-desc-image)
[]
[![View the severity and description tab in custom policy](/downloads/zpc/policies/creating-custom-security-policies/zpc-custom-policy-severity-description-img.png?1662976987)
]
[]![Click and drag to move](data:image/gif;base64,R0lGODlhAQABAPABAP///wAAACH5BAEKAAAALAAAAAABAAEAAAICRAEAOw==)
![Click and drag to move](data:image/gif;base64,R0lGODlhAQABAPABAP///wAAACH5BAEKAAAALAAAAAABAAEAAAICRAEAOw==)
![Click and drag to move](data:image/gif;base64,R0lGODlhAQABAPABAP///wAAACH5BAEKAAAALAAAAAABAAEAAAICRAEAOw==)
![Click and drag to move](data:image/gif;base64,R0lGODlhAQABAPABAP///wAAACH5BAEKAAAALAAAAAABAAEAAAICRAEAOw==)
![Click and drag to move](data:image/gif;base64,R0lGODlhAQABAPABAP///wAAACH5BAEKAAAALAAAAAABAAEAAAICRAEAOw==)
![Click and drag to move](data:image/gif;base64,R0lGODlhAQABAPABAP///wAAACH5BAEKAAAALAAAAAABAAEAAAICRAEAOw==)
[]