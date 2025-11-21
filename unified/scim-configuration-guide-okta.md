# SCIM Configuration Guide for Okta
Source: https://help.zscaler.com/unified/scim-configuration-guide-okta
PDF: https://help.zscaler.com/pdf/com/en/1491506.pdf

This guide provides information on how to configure and install the Zscaler Private Access (ZPA) 2.0 app in Okta. Zscaler Private Access 2.0 enables you to use SAML as your method of authentication and SCIM as your method of provisioning.
Prerequisites
Ensure that you have:
- An Okta account with admin privileges.
- An existing directory in Okta.
- A Private Applications account with an administrator role that allows you to add a SCIM configuration.
- A SCIM provisioning subscription for Okta. Contact your Okta representative to ensure your organization has the appropriate subscription.
Configuring SCIM for Identity Management
Using SCIM allows you to quickly remove users from Private Applications when you delete them in your user directory. SCIM also ensures that information flows to Private Applications and policies are updated accordingly when you make a change to the group information for a user. To use [SCIM](/unified/about-scim), you must enable it in Okta.
The following procedures apply to SCIM configurations for the Private Applications application in Okta. You need to begin the [SCIM configuration](/unified/enabling-scim-identity-management) process in the Admin Portal to get the SCIM Service Provider Endpoint and bearer token required in steps 4 and 5.
To configure SCIM in Okta:
- Click the **Provisioning **tab.
[See image.](#See1)
- Click **Configure API Integration**.
[See image.](#See2)
- Select the **Enable API Integration** checkbox.
- In the **Base URL** field, enter the **SCIM Service Provider Endpoint** that is provided when [enabling SCIM](/unified/enabling-scim-identity-management) in the Admin Portal.
- In the **API Token** field, enter the **Bearer Token** that is provided when [enabling SCIM](/unified/enabling-scim-identity-management) in the Admin Portal.
- Click **Test API Credentials**. Okta attempts to connect to the SCIM endpoint. When the connection is successful, a verification message appears.
[See image.](#See3)
If the attempt fails, make sure you save your IdP configuration in the Admin Portal when [enabling SCIM](/unified/enabling-scim-identity-management), and then try again.
- Click **Save** after a successful connection to save your credentials.
- After the **To App **settings load, click **Edit** next to Provisioning to App.
[See image.](#See4)
- For **Create Users**, select the **Enable** checkbox.
- For **Update User Attributes**, select the **Enable** checkbox.
- For **Deactivate Users**, select the **Enable** checkbox.
- Click **Save**.
[See image.](#See5)
After SCIM is enabled, Zscaler checks if a user is present in the SCIM database. Based on this information, Zscaler decides if the user is allowed or blocked access to Private Applications. Customers need to ensure SCIM user sync is complete prior to enabling SCIM policies for these users, otherwise the Private Applications service does not recognize the users and evaluate policies for them. Before enabling SCIM for policies, Zscaler recommends monitoring the user and group count in the Admin Portal until it is equal to the user and group count in Okta. The duration of the SCIM sync is dependent on the amount of users and groups that are being synced. This can take up to a week in certain scenarios. To learn more, see [Enabling SCIM for Identity Management](/unified/enabling-scim-identity-management).
To assign users or groups to Zscaler Private Access 2.0:
- Click the **Assignments** tab.
- In the **Assign** drop-down menu, you can:
- Select **Assign to People**: Assigns a user.
[See image.](#See6)
- Select **Assign to Groups**: Assigns a group of users.
[See image.](#See7)
- After finding the correct users or groups, click **Assign**.
- Click **Done**.
When assigning users to an application, Zscaler recommends creating one assignment group with all Okta users to leverage assignments and define policies in the Admin Portal. After the assignments are complete, push the groups you want to sync with Zscaler Private Access 2.0.
To sync groups with Zscaler Private Access 2.0:
- Click the **Push Groups** tab.
- Click the **Push Groups** drop-down menu.
- To define which groups are synced with the service provider:
- Select **Find groups by name**: Searches for specific groups to push.
[See image.](#See8)
- Select **Find groups by rule**: Creates a search rule that pushes any groups that match the rule.
[See image.](#See9)
- After searching for the group by name or rule, click **Save** or **Save & Add Another**.
[]To sync attributes (e.g. department, job title) with SCIM for Private Applications:
- Select **Directory**.
- Select **Profile Editor**.
- Select the relevant SCIM application configured for Private Applications authentication.
- Click **Add Attribute**.
[See image.](#AddAttribute)
- Enter the necessary information:
- **Data type**: Select **string**.
- **Display name**: Enter the attribute you are going to sync (e.g., department, job title).
- **Variable name**: Enter the attribute you are going to sync (e.g., department, job title).
- **External name**: Enter the attribute you are going to sync (e.g., department, job title).
- **External namespace**: Enter the url `urn:ietf:params:scim:schemas:extension:enterprise:2.0:User`
- **Description**: The description for the attribute, if available.
Fill in the additional fields if necessary.
- Click **Save attribute**.
[See image.](#Attributewindow)
- Select the relevant SCIM application again.
- Click **Mappings**.
[See image.](#selectmappings)
- Click the **Okta Users to Zscaler Private Access** tab.
- Enter the necessary information:
- Locate the attribute name in the right column under the SCIM application name.
- In the left field, next to the attribute name enter `user.` with the attribute (e.g. user.department, user.jobtitle).
- Click **Save Mappings**.
[See image.](#editingmappings)
- Click **Profile Editor**.
- Review the attributes to confirm that the new attribute is synced.
- Click the **View** icon under an Internal User ID to confirm that the SCIM User is reflected in the Admin Portal.
[See image.](#SCIMUserstab)
[]![Setting up SCIM provisioning in Okta](/downloads/zpa/identity-management/scim-configurations-guides/scim-configuration-guide-microsoft-azure-ad/zpa-scim-okta-provisioning.png)
[]![Setting up SCIM provisioning in Okta to configure API integration](/downloads/zpa/identity-management/scim-configurations-guides/scim-configuration-guide-microsoft-azure-ad/zpa-scim-okta-api-integration.png)
[]![Verifying the API credentials to connect the SCIM endpoint in Okta](/downloads/zpa/identity-management/scim-configurations-guides/scim-configuration-guide-microsoft-azure-ad/zpa-scim-okta-endpoint-connection.png)
[]![Edit the Provisioning to App settings in Okta](/downloads/zpa/identity-management/scim-configurations-guides/scim-configuration-guide-microsoft-azure-ad/zpa-scim-okta-provisioning-app.png)
[]![Setting up Provisioning to App settings in Okta](/downloads/zpa/identity-management/scim-configurations-guides/scim-configuration-guide-microsoft-azure-ad/zpa-scim-okta-to-app-provisioning.png)
[]![Assigning Users to Zscaler Private Access 2.0 in Okta](/downloads/zpa/identity-management/scim-configurations-guides/scim-configuration-guide-microsoft-azure-ad/zpa-scim-okta-assign-people.png)
[]![Assigning Groups to Zscaler Private Access 2.0 in Okta](/downloads/zpa/identity-management/scim-configurations-guides/scim-configuration-guide-microsoft-azure-ad/zpa-scim-okta-assign-groups.png)
[]![Pushing groups by name to Zscaler Private Access 2.0](/downloads/zpa/identity-management/scim-configurations-guides/scim-configuration-guide-microsoft-azure-ad/zpa-scim-okta-push-names.png)
[]![Pushing groups by rule to Zscaler Private Access 2.0](/downloads/zpa/identity-management/scim-configurations-guides/scim-configuration-guide-microsoft-azure-ad/zpa-scim-okta-push-rule.png)
[][![Adding an attribute to Zscaler Private Access 2.0 in Okta](/downloads/zpa/identity-management/scim-configuration-guides/scim-configuration-guide-okta/Click%20Add%20attribute.png)
]
[][![Adding an attribute in the Add Attribute window to Zscaler Private Access 2.0 in Okta ](/downloads/zpa/identity-management/scim-configuration-guides/scim-configuration-guide-okta/Add%20Attribute%20fields.png)
]
[][![Select Mappings in the Profile Editor For Private Access 2.0 in Okta](/downloads/zpa/identity-management/scim-configuration-guides/scim-configuration-guide-okta/Click%20Mappings.png)
]
[][![Editing Profile Mappings for Private Access 2.0 in Okta](/downloads/zpa/identity-management/scim-configuration-guides/scim-configuration-guide-okta/Mappings%20steps.png)
]
[][![SCIM Users page in the ZPA Admin Portal](/downloads/zpa/identity-management/scim-configuration-guides/scim-configuration-guide-okta/ZPA%20Admin%20view.png)
]