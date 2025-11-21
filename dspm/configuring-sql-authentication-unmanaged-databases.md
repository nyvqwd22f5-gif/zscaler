# Configuring Server Role for Unmanaged Databases
Source: https://help.zscaler.com/dspm/configuring-sql-authentication-unmanaged-databases
PDF: https://help.zscaler.com/pdf/com/en/1519401.pdf

To add an [unmanaged database](/dspm/about-unmanaged-database) to DSPM using any authentication type, you need to create a custom server role with the necessary permissions to access the database.
Configuring Server Role for Unmanaged MSSQL Database
To configure a server role for an unmanaged MSSQL database:
- Log in to the virtual machine where the SQL server is installed.
- Open [SQL Server Management Studio](https://learn.microsoft.com/en-us/sql/ssms/quickstarts/ssms-connect-query-sql-server?view=sql-server-ver16#connect-to-a-sql-server-instance) and run the following queries:
- [a. Create a server role.](#create-server)
- [b. Grant role permissions.](#read-databases)
- [c. Create login credentials for the database.](#create-login)
- [d. Assign the server role to the user.](#assign-login)
- [e. Apply read permissions to all databases.](#database-level)
- [f. Assign permissions to the newly created databases.](#trigger)
After you run these queries, the custom role has read-only access to all databases, allowing DSPM to scan the unmanaged MSSQL databases.
Configuring Server Role for Unmanaged PostgreSQL Database
To configure a server role for an unmanaged PostgreSQL database:
- Download the latest [pgAdmin](https://www.pgadmin.org/download/) version and install it on your system.
- Open pgAdmin and connect to your server. To learn more, refer to the [pgAdmin documentation](https://www.pgadmin.org/docs/pgadmin4/9.1/connecting.html#).
-
Run the following query in the [pgAdmin query tool](https://www.pgadmin.org/docs/pgadmin4/9.1/query_tool.html) to grant the `select` permission:
`GRANT SELECT ON ALL TABLES IN SCHEMA public TO <USERNAME>;`
Replace `<USERNAME>` with the PostgreSQL username.
After running this query, the custom role has read-only access to all databases, allowing DSPM to scan the unmanaged PostgreSQL databases.
[]Creates a server role named `ReadOnlyServerRole` in the master database.
`use master;
CREATE SERVER ROLE ReadOnlyServerRole;`
[]Provides the server role with permissions to view or connect to all databases.
`
GRANT VIEW ANY DATABASE TO ReadOnlyServerRole;
GRANT CONNECT ANY DATABASE TO ReadOnlyServerRole;
GRANT VIEW ANY DEFINITION TO ReadOnlyServerRole;`
[]Login credentials are required to connect to the database server. Depending on the authentication type, run the following commands to create the login credentials:
- [SQL](#ds-sql)
- [Managed Identity](#ds-managedid)
- [Service Princial](#ds-service-pricipal)
[]
` CREATE LOGIN dspmloginuser WITH PASSWORD = 'password@123';`
[]
`CREATE LOGIN [user_managed_identity_name] FROM EXTERNAL PROVIDER;`
Replace `usermanaged_identity_name` with the actual name of the managed identity.
[]
`CREATE LOGIN [service_principal_name] FROM EXTERNAL PROVIDER;`
Replace `service_principal_name` with the actual name of the service principal.
[]Assigns the user with a server role, granting them read-only access to the server.
`ALTER SERVER ROLE [ReadOnlyServerRole] ADD MEMBER [dspmloginuser];`
[]Assigns read permissions to the `db_datareader` custom role in all databases. A server roles functions at the instance level. This query is to ensure that the custom role has read permissions for all databases, including system databases such as master, MSDB, etc.
``DECLARE @DatabaseName NVARCHAR(100);`
`DECLARE @SQL NVARCHAR(MAX);`
`– Loop through all databases (excluding tempdb)`
`DECLARE db_cursor CURSOR FOR`
`SELECT name`
`FROM sys.databases`
`WHERE state_desc = 'ONLINE' – Only online databases`
`AND name NOT IN ('tempdb'); – Exclude tempdb (permissions on tempdb are not persistent)`
`OPEN db_cursor;`
`FETCH NEXT FROM db_cursor INTO @DatabaseName;`
`WHILE @@FETCH_STATUS = 0`
`BEGIN`
`SET @SQL = '`
`USE [' + @DatabaseName + '];`
`IF DATABASE_PRINCIPAL_ID(''dspmreaduser'') IS NULL`
`BEGIN`
`– Create the database user for the server role, if it doesn't already exist`
`CREATE USER [dspmreaduser] FOR LOGIN [dspmloginuser];`
`END;`
`– Add the server role to the db_datareader role in the database`
`EXEC sp_addrolemember ''db_datareader'', ''dspmreaduser'';`
`';`
`– Execute the SQL statement`
`EXEC sp_executesql @SQL;`
`FETCH NEXT FROM db_cursor INTO @DatabaseName;`
`END;`
`CLOSE db_cursor;`
`DEALLOCATE db_cursor;``
[]Creates a trigger to automatically assign permissions to new databases.
`CREATE TRIGGER GrantReadAccessOnNewDatabase
ON ALL SERVER
FOR CREATE_DATABASE
AS
BEGIN
DECLARE @DatabaseName NVARCHAR(100);      -- Get the name of the newly created database
SELECT @DatabaseName = EVENTDATA().value('(/EVENT_INSTANCE/DatabaseName)[1]', 'NVARCHAR(100)');      -- Grant read access to the new database
DECLARE @SQL NVARCHAR(MAX);
SET @SQL = '
USE [' + @DatabaseName + '];
IF DATABASE_PRINCIPAL_ID(''ReadOnlyServerRole'') IS NULL
BEGIN
CREATE USER [ReadOnlyServerRole] FOR LOGIN [ReadOnlyServerRole];
END;
EXEC sp_addrolemember ''db_datareader'', ''ReadOnlyServerRole'';
';
EXEC sp_executesql @SQL;
END;
GO`