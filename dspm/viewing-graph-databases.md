# Viewing the Graph for Databases
Source: https://help.zscaler.com/dspm/viewing-graph-databases
PDF: https://help.zscaler.com/pdf/com/en/1532158.pdf

The graph for a database (unmanaged, on-premises, or Snowflake) is a visual representation of the scan result. The graph provides in-depth details of the databases containing sensitive data, the DLP engines and dictionaries that match the sensitive data, whether data is publicly exposed to the internet, including the public exposure path, and the list of entities that can access the databases. These details are helpful to quickly evaluate and remediate the issues, protect the sensitive data, and maintain a strong security posture.
DSPM provides support for scanning [unmanaged databases](/dspm/about-unmanaged-database) (PostgreSQL Flexible server and PostgreSQL database) and identifies the posture-related risks of the virtual machine that hosts the database. It also identifies the users and entities that have access to the database, and if there are any risks.
To view the graph for a database:
- Go to **Analytics** > **Resource Inventory**.
- On the **Resource Inventory** page, click the resource name.
- The graph is displayed on the **Risk Explorer** tab.
- [On-Premises Database](#on-premisesdatabase)
- [Unmanaged Database](#unmanageddatabase)
- [Snowflake Database](#ds-snowflake)
[]The following graph is for an on-premises database:
[See image.](#ds-on-premisesgraph)
Click the nodes to view additional details of each entity:
- [1. Primary Resource](#ds-primaryresource)
- [2. Database with Sensitive Data](#ds-impacteddatabase)
- [3. Table with Sensitive Data](#ds-onprem-table-with-sensitive-data)
- [4. Sensitive Records](#ds-sensitiverecords)
- [5. Databases](#ds-databases)
- [6. Database Principals](#ds-onprem-database-principals)
- [7. Admin Principals](#ds-onprem-admin-principals)
- [8. Server Principals](#ds-onprem-server-principals)
[]View the following details of the primary resource:
- **Data Store Type**: The type of data store.
- **Resource Type**: The type of resource.
- **Data Center ID**: The unique identifier of the data center.
- **Data Center Name**: The name of the data center.
- **Region**: The region where the resource is located.
- **Last Completed Scan**: The date and time when the last scan was completed.
- **Data Scanned**: The amount of data scanned.
- **Triggers**: The number of alerts raised for this resource.
- **Matched Files**: The number of files that match the DLP engines.
- **DLP Engines**: The [DLP engines](/dspm/understanding-dlp-engines-and-dictionaries) that match sensitive records.
- **DLP Dictionaries**: The [DLP dictionaries](/dspm/understanding-dlp-engines-and-dictionaries) associated with DLP engines.
- **ID**: The unique identifier of the resource.
- **Posture**: The [security posture](/dspm/understanding-security-posture-state) of the resource.
- **Metadata**: Click to view the metadata for the resource.
![Shows the details related to the primary resource](/downloads/tech-pubs-drafts/dspm-draft-articles/1-13-0-viewing-graph-databases/on-prem-1.png)
[]View the details of the database that contains sensitive data.
![Shows the details of database with sensitive data](/downloads/tech-pubs-drafts/dspm-draft-articles/1-13-0-viewing-graph-databases/ds-onprm-resource-with-sensitive-data.png)
[]View the details of the table within the impacted database that contains sensitive data.
![Shows the details of the table within the database that contains sensitive data](/downloads/tech-pubs-drafts/dspm-draft-articles/1-13-0-viewing-graph-databases/ds-table-indatabase-with-sensitivedata_1.png)
[]View the details of sensitive records.
![Shows details of sensitive records](/downloads/tech-pubs-drafts/dspm-draft-articles/1-13-0-viewing-graph-databases/ds-onprem-sensitive-record.png)
[]View all the databases, including those that do not contain any sensitive data and the ones that are not scanned.
![Shows the databases associated with the resource](/downloads/tech-pubs-drafts/dspm-draft-articles/1-13-0-viewing-graph-databases/ds-onprem-database.png)
[]
- View the list of all database principals that can access the resource.
![Shows details of database principals that can access the resource](/downloads/tech-pubs-drafts/dspm-draft-articles/1-13-0-viewing-graph-databases/ds-onprem-database-principals_0.png)
-
Click the **Entity Name** to view additional details.
[See image.](#ds-onprem-databaseprincipals-path)
-
Click **Show Access Path** to view another graph that displays the entities and their assigned permissions that allow access to the database.
[See image.](#ds-onprem-databaseprincipals-graph)
[]
![Shows details of on-prem database principals](/downloads/tech-pubs-drafts/dspm-draft-articles/1-13-0-viewing-graph-databases/ds-onprem-databaseprincipals-path.png)
[]
![Shows access path graph for a database principal](/downloads/tech-pubs-drafts/dspm-draft-articles/1-13-0-viewing-graph-databases/ds-onprem-databaseprincipals-graph.png)
[]
- View the list of all admin principals that can access the resource.
![Shows details of admin principals that access the resource](/downloads/tech-pubs-drafts/dspm-draft-articles/1-13-0-viewing-graph-databases/ds-onprem-admin-principals_0.png)
-
Click the **Entity Name** to view additional details.
[See image.](#ds-onprem-adminprincipals-path)
-
Click **Show Access Path** to view another graph that displays the entities and their assigned permissions that allow access to the database.
[See image.](#ds-onprem-adminprincipals-graph)
[]
![Shows details of the admin principals](/downloads/tech-pubs-drafts/dspm-draft-articles/1-13-0-viewing-graph-databases/ds-onprem-adminprincipals-path.png)
[]
![Shows access path of the admin principal](/downloads/tech-pubs-drafts/dspm-draft-articles/1-13-0-viewing-graph-databases/ds-onprem-adminprincipals-graph.png)
[]
- View the list of all server principals that can access the resource.
![Shows details of server principals that can access the resource](/downloads/tech-pubs-drafts/dspm-draft-articles/1-13-0-viewing-graph-databases/ds-onprem-server-principals_0.png)
-
Click the **Entity Name** to view additional details.
[See image.](#ds-onprem-serverprincipals-path)
-
Click **Show Access Path** to view another graph that displays the entities and their assigned permissions that allow access to the database.
[See image.](#ds-onprem-serverprincipals-graph)
[]
![Shows details of server principals](/downloads/tech-pubs-drafts/dspm-draft-articles/1-13-0-viewing-graph-databases/ds-onprem-serverprincipals-path.png)
[]
![Shows the access path details of server principal](/downloads/tech-pubs-drafts/dspm-draft-articles/1-13-0-viewing-graph-databases/ds-onprem-serverprincipals-graph.png)
[]The following graph is for an unmanaged database:
[See image.](#ds-unmanaged-database-graph)
Click the nodes to view additional details of each entity:
- [1. Primary Resource](#ds-unmanaged-primary-resource)
- [2. Resource with Sensitive Data](#ds-ResourcewithSensitiveData)
- [3. Sensitive Records](#ds-unmanaged-sensitive-records)
- [4. Resource](#ds-unmanaged-resource)
- [6. Admin Principals](#ds-unmanaged-admin-principals)
- [7. Server Principals](#ds-unmanaged-server-principals)
- [8. Database Principals](#ds-unmanaged-database-principals)
[]
- **Data Store Type**: The type of data store.
- **Resource Type**: The type of resource.
- **Subscription ID**: The unique identifier of the subscription in which the resource is stored.
- **Subscription Name**: The name of the subscription in which the resource is stored.
- **Tenant ID**: The unique identifier of the tenant to which the subscription belongs.
- **Region**: The region where the resource is located.
- **Last Completed Scan**: The date and time when the resource was last scanned.
- **Data Scanned**: The amount of data scanned.
- **Triggers**: The number of sensitive records in the resource.
- **Matched Tables**: The number of tables that matched the DLP engines.
- **DLP Engines**: The [DLP engines](/dspm/understanding-dlp-engines-and-dictionaries) that match sensitive records.
- **DLP Dictionaries**: The [DLP dictionaries](/dspm/understanding-dlp-engines-and-dictionaries) associated with DLP engines.
- **ID**: Copy the tenant ID to identify the resource.
- **Tags**: The tags associated with the resource.
- **Posture**: The [security posture](/dspm/understanding-security-posture-state) of the resource.
- **Metadata**: Click to view the metadata for the resource.
![Shows the details of the primary resource](/downloads/tech-pubs-drafts/dspm-draft-articles/1-13-0-viewing-graph-databases/ds-unmanaged-primary-resource.png)
[]View the details of the database that contains sensitive data.
![Shows the database that contains sensitive data](/downloads/tech-pubs-drafts/dspm-draft-articles/1-13-0-viewing-graph-databases/ds-unmanaged-resourcewith-sensitive-data.png)
[]View the details of sensitive records.
![Shows details of sensitive records](/downloads/tech-pubs-drafts/dspm-draft-articles/1-13-0-viewing-graph-databases/unmanaged-1.png)
[]View all the associated resources, including those that do not contain any sensitive data and the ones that are not scanned. In this scenario, the Azure PostgresSQL server has two databases that contain sensitive data.
![Shows the details of the associated resources](/downloads/tech-pubs-drafts/dspm-draft-articles/1-13-0-viewing-graph-databases/unmanaeged-2.png)
[]
-
View the list of admin principals that can access the resource.
![Shows the details of all the admins that can access the resource](/downloads/tech-pubs-drafts/dspm-draft-articles/1-13-0-viewing-graph-databases/ds-unmanaged-admin-principals.png)
- Click the **Entity Name** to view additional details.
[See image.](#ds-unmanaged-admin-principals-path)
-
Click **Show Access Path** to view another graph that displays the entities and their assigned permissions that allow access to the database.
[See image.](#ds-unmanaged-admin-principals-access-graph)
[]
![Shows details of unmanaged database admin principals](/downloads/tech-pubs-drafts/dspm-draft-articles/1-13-0-viewing-graph-databases/ds-unmanaged-adminprincipals-path.png)
[]
![Shows access path of admin principals for an unmanaged database](/downloads/tech-pubs-drafts/dspm-draft-articles/1-13-0-viewing-graph-databases/ds-unmanaged-adminprincipals-graph.png)
[]
- View the list of all server principals that can access the resource.
![Shows the details of all the entities that can access server resources](/downloads/tech-pubs-drafts/dspm-draft-articles/1-13-0-viewing-graph-databases/ds-unmanaged-server-principals.png)
- Click the **Entity Name** to view additional details.
[See image.](#ds-unmanaged-server-principals-path)
-
Click **Show Access Path** to view another graph that displays the entities and their assigned permissions that allow access to the database.
[See image.](#ds-unmanaged-server-principals-access-graph)
[]
![Shows details of unmanaged database server principals](/downloads/tech-pubs-drafts/dspm-draft-articles/1-13-0-viewing-graph-databases/ds-unmanaged-server-principals-path.png)
[]
![Shows access path of server principals](/downloads/tech-pubs-drafts/dspm-draft-articles/1-13-0-viewing-graph-databases/ds-unmanaged-server-principals-graph.png)
[]
- View the list of all database principals that can access the resource.
![Shows details of database principals](/downloads/tech-pubs-drafts/dspm-draft-articles/1-13-0-viewing-graph-databases/ds-unmanaged-database-principals.png)
- Click the **Entity Name** to view additional details.
[See image.](#ds-unmanaged-database-principals-access-path)
- Click **Show Access Path** to view another graph that displays the entities and their assigned permissions that allow access to the database.
[See image.](#ds-unmanaged-database-principals-access-graph)
[]
![Shows details of database principals](/downloads/tech-pubs-drafts/dspm-draft-articles/1-13-0-viewing-graph-databases/ds-unmanaged-database-principals-path.png)
[]
![Shows access path of database principals](/downloads/tech-pubs-drafts/dspm-draft-articles/1-13-0-viewing-graph-databases/ds-unmanaged-database-principals-graph.png)
[]The following graph is for a Snowflake database:
[See image.](#ds-snowflake-main-graph)
Click the nodes to view additional details of each entity:
- [1. Primary Resource](#ds-snowflake-primary-resource)
- [2. Resource with Sensitive Data](#ds-snowflake-resource-sensitive-data)
- [3. Sensitive Records](#ds-snowflake-sensitive-records)
- [4. Table](#ds-snowflake-table)
- [5. Service](#ds-snowflake-service)
- [6. Admin Principals](#ds-snowflake-admin-principals)
- [6. Users](#ds-snowflake-user)
[]
- **Data Store Type**: The type of datastore.
- **Resource Type**: The type of resource.
- **Account ID**: The unique identifier of the account in which the resource is located.
- **Account Name**: The name of the account in which the resource is located.
- **Organization ID**: The unique identifier of the organization to which the account belongs.
- **Region**: The region where the organization is located.
- **Last Completed Scan**: The date and time when the resource was last scanned.
- **Data Scanned**: The amount of data scanned.
- **Triggers**: The number of alerts raised for this resource.
- **Matched Tables**: The number of tables that matched the DLP engines.
- **DLP Engines**: The [DLP engines](/dspm/understanding-dlp-engines-and-dictionaries) that match sensitive records.
- **DLP Dictionaries**: The [DLP dictionaries](/dspm/understanding-dlp-engines-and-dictionaries) associated with DLP engines.
- **ID**: Copy the tenant ID to identify this resource in the tenant.
- **Tags**: The tags associated with the resource.
- **Posture**: The [security posture](/dspm/understanding-security-posture-state) of the resource.
- **Metadata**: Click to view the metadata for the resource.
![Shows the details of the primary resource](/downloads/tech-pubs-drafts/dspm-draft-articles/1-13-0-viewing-graph-databases/ds-snowflake-primary-resource.png)
[]View the details of the tables that contain sensitive data.
![Shows details of tables that contain sensitive data](/downloads/tech-pubs-drafts/dspm-draft-articles/1-13-0-viewing-graph-databases/ds-snowflake-database-sensitive-data.png)
[]View the details of sensitive records.
![Shows the details of sensitive records](/downloads/tech-pubs-drafts/dspm-draft-articles/1-13-0-viewing-graph-databases/ds-snowflake-sensitive-record.png)
[]View all the associated resources, including those that do not contain any sensitive data and the ones that are not scanned.
![Shows details of all the associated resources](/downloads/tech-pubs-drafts/dspm-draft-articles/1-13-0-viewing-graph-databases/ds-snowflake-tables.png)
[]
- View the list of all the services that can access the Snowflake database.
![Shows the details of services that can access the Snowflake database](/downloads/tech-pubs-drafts/dspm-draft-articles/1-13-0-viewing-graph-databases/ds-snowflake-services.png)
- Click the **Entity Name** to view additional details.
[See image.](#ds-snowflake-service-path)
- Click **Show Access Path** to view another graph that displays the entities and their assigned permissions that allow access to the database.
[See image.](#ds-snowflake-service-path-graph)
[]
- View the list of all admin entities that can access the Snowflake database.
![Shows the details of all the admins that can access the Snowflake database](/downloads/tech-pubs-drafts/dspm-draft-articles/1-13-0-viewing-graph-databases/ds-snowflake-admin-principals.png)
-
Click the **Entity Name** to view additional details.
[See image.](#ds-snowflake-admin-principal-path)
- Click **Show Access Path** to view another graph that displays the entities and their assigned permissions that allow access to the database.
[See image.](#ds-snowflake-admin-principal-graph)
[]
- View the list of all the users that can access the Snowflake database.
![Shows the details of users that can access the Snowflake database](/downloads/tech-pubs-drafts/dspm-draft-articles/1-13-0-viewing-graph-databases/ds-snowflake-users.png)
- Click the **Entity Name** to view additional details.
[See image.](#ds-snowflake-user-access-path)
- Click **Show Access Path** to view another graph that displays the entities and their assigned permissions that allow access to the database.
[See image.](#ds-snowflake-user-access_-graph)
[]
![Shows the risk explorer graph for Snowflake](/downloads/tech-pubs-drafts/dspm-draft-articles/1-13-0-viewing-graph-databases/ds-snowflake-main-graph_0.png)
[]
![Shows the risk explorer graph for an on-premises database](/downloads/tech-pubs-drafts/dspm-draft-articles/1-13-0-viewing-graph-databases/ds-on-prem-main-graph_0.png)
[]
![Shows the Risk Explorer graph for an unmanaged database.](/downloads/tech-pubs-drafts/dspm-draft-articles/1-13-0-viewing-graph-databases/ds-unmanged-database-graph_0.png)
[]
![Shows detail about Snowflake user](/downloads/tech-pubs-drafts/dspm-draft-articles/1-13-0-viewing-graph-databases/ds-snowflake-user-access-path.png)
[]
![Shows the access path graph for Snowflake user](/downloads/tech-pubs-drafts/dspm-draft-articles/1-13-0-viewing-graph-databases/ds-snowflake-user-access-path-graph_0.png)
[]
![Shows the details of Snowflake service](/downloads/tech-pubs-drafts/dspm-draft-articles/1-13-0-viewing-graph-databases/ds-snowflake-service-path.png)
[]
![Shows the access path for a Snowflake service](/downloads/tech-pubs-drafts/dspm-draft-articles/1-13-0-viewing-graph-databases/ds-snowfake-service-path-graph.png)
[]
![Shows details of Snowflake admin principal](/downloads/tech-pubs-drafts/dspm-draft-articles/1-13-0-viewing-graph-databases/ds-snowflake-admin-principals-path_0.png)
[]
![Shows the access path graph of Snowflake admin principal](/downloads/tech-pubs-drafts/dspm-draft-articles/1-13-0-viewing-graph-databases/ds-snowflake-admin-principal-graph.png)