# About Attributes
Source: https://help.zscaler.com/unified/about-attributes
PDF: https://help.zscaler.com/pdf/com/en/1505306.pdf

ZIdentity supports user attributes and session attributes that are necessary to configure SAML-based single sign-on (SSO) access for users. For both user attributes and session attributes, ZIdentity allows you to define custom attributes (user-defined) in addition to the default attributes (system-defined). These attributes can be used for defining various sign-on policies or access control policies in other Zscaler services.
By default, ZIdentity provides 5 system-defined user attributes and 4 system-defined session attributes that are part of the predefined schema, serving as foundational fields for user identities and user sessions, respectively. The system-defined attributes are a minimal set of attributes that are commonly used to create access control policies. Based on your organization's requirements, administrators can also define custom user attributes and custom session attributes to provide more granular access control for users. For example, ZIdentity can receive, calculate, or retrieve attributes related to the user and session and make them available to Private Applications, so Private Application policies can enforce user access based on the context.
The following table lists the system-defined attributes in each category:
-
-
-
-
-
-
-
-
-
| Category | System-Defined Attributes |
| -------- | ------------------------- |
| User Attributes | `displayname``firstname``lastname``primaryemail``department` |
| Session Attributes | `created_at``last_authenticated_at``identity_provider``is_device_managed` |
Attributes provide the following benefits and enable you to:
- Use attributes for Zscaler services (e.g., Internet & SaaS, Private Applications, etc.) in order to control access to internet or private applications.
- Configure sign-on policies and control user access to the Admin Portal.
- Use the attributes for SSO.
- Use the session attributes to manage user sessions.
About the Attributes Page
On the Attributes page (Administration > Identity > ZIdentity > Attributes), you can do the following:
- View a list of system-defined and user-defined user and session attributes. By default, the User Attributes tab is selected. For each user attribute, you can see:
- **Display Name**: The name that is visible throughout the Admin Portal.
- **Attribute Name**: The name of the attribute with proper syntax.
- **Data Type**: The data type (String, Integer, Boolean, etc.) of the attribute.
- **Required**: Whether the user attribute is a mandatory requirement.
- **Origin**: Whether the attribute is system-defined or user-defined. You cannot edit or delete a system-defined attribute.
- [Add a user attribute](/unified/adding-user-attributes).
- Import a CSV file that contains a list of user attributes.
- Bulk delete user attributes. This option is visible only when you select more than one user attribute.
- View the session attribute details and [add a session attribute](/unified/adding-session-attributes).
- Search for an attribute.
- Edit a user-defined attribute.
- Delete a user-defined attribute.
- Select attributes to perform bulk deletions. Select more than one user attribute to view the **Delete **option.
![The Attributes page](/downloads/zidentity/administration/attributes/about-attributes/zidentity-about-attributes_0.png)