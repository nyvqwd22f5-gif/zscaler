# Adding a Snowflake Database Account
Source: https://help.zscaler.com/dspm/adding-snowflake-database-account
PDF: https://help.zscaler.com/pdf/com/en/1529987.pdf

You can add a [Snowflake account](/dspm/about-service-registration) to DSPM. DSPM scans the Snowflake databases for sensitive data and identifies any potential security posture risks.
Prerequisites
Before adding a Snowflake account to DSPM, ensure the following prerequisites are met:
- [1. Create a warehouse for DSPM.](#dspm-warehouse)
- [2. Create a role with required permissions.](#role-and-permissions)
- [3. Create a user for DSPM.](#create-user)
- [4. Configure network policy for the DSPM user.](#network-policy)
- [5. Provide SQL connection strings and authentication credentials to allow DSPM to access the Snowflake account.](#ds-step5-connectionstring)
[]When deploying DSPM components in Azure, a specific configuration is required to ensure secure communication with Snowflake. Use the Azure CLI to create a private key and secret, as the Azure portal does not support multiple inputs for secrets.
`az keyvault secret set --vault-name snowflakekeyvaultvikas --name azuremultilinersakey --file "<filepath>"`
[]Network policy allows communication between the DSPM components deployed in the customer scanner account and Snowflake.
- Get the public IP address of the NAT that will be used to perform the data scan.
-
Create a network rule in Snowflake to allow ingress traffic from the NAT public IP:
`CREATE NETWORK RULE ALLOW_INGRESS_ZSCALER_POLICY
MODE = 'INGRESS'
TYPE = 'IPV4'
VALUE_LIST = ('xx.xx.xx.xx');`
If you need to modify or update an existing network rule to include additional IP addresses:
`ALTER NETWORK RULE ALLOW_INGRESS_ZSCALER_POLICY
SET VALUE_LIST = ('xx.xxx.xx.xxx', 'xx.xx.xxx.xxx','xxx.xx.xxx.xx/xx');`
-
After the network rule is created, create a network with allowed network rule:
`CREATE NETWORK POLICY ALLOW_INGRESS_ZSCALER_POLICY
ALLOWED_NETWORK_RULE_LIST = ('ALLOW_INGRESS_ZSCALER_POLICY');`
-
Attach the created network policy to the user:
`ALTER USER dspmdatascanuser SET NETWORK_POLICY = ALLOW_INGRESS_ZSCALER_POLICY;`
[]Choose any of the two options to create and authenticate a user for DSPM:
- [Basic Authentication (Using PAT)](#basic-auth)
- [Private Key Authentication](#private-key-auth)
After the user is created, verify that the default warehouse and role are set correctly.
[See image.](#img-ds-snowflake-verify-configuration)
[]![Snowflake Edit User window displaying the fields such as login name, display name, default role, and default warehouse.](/downloads/dspm/administration/service-registration/snowflake-database/adding-snowflake-database-account/ds-snowflake-verify-configuration.png)
- []Create a private key using either an unencrypted or encrypted format:
-
Unencrypted key (without passphrase)
`openssl genrsa 2048 | openssl pkcs8 -topk8 -inform PEM -out rsa_key.p8 -nocrypt`
-
Encrypted key (with passphrase)
`openssl genrsa 2048 | openssl pkcs8 -topk8 -v2 des3 -inform PEM -out rsa_key.p8`
-
Use the generated private key to create a corresponding public key:
`openssl rsa -in rsa_key.p8 -pubout -out rsa_key.pub`
-
Create the user account in Snowflake using the public key:
`CREATE USER dspmdatascanuser DEFAULT_ROLE = "dspmdatascanrole" DEFAULT_WAREHOUSE = "dspmwarehouse" RSA_PUBLIC_KEY="<rsa_public_key>";`
-
Assign the role to the user:
`GRANT ROLE dspmdatascanrole TO USER dspmdatascanuser;`
- Store the private key in the scanner account's secret manager for DSPM authentication.
-
[]Create a user account in Snowflake with default configurations:
`CREATE USER dspmdatascanuser DEFAULT_ROLE = "dspmdatascanrole" DEFAULT_WAREHOUSE = "dspmwarehouse";`
-
Assign the role to the user:
`GRANT ROLE dspmdatascanrole TO USER dspmdatascanuser;`
-
Generate a programmatic access token (PAT) for this newly created user from the Snowflake UI.
[See image.](#img-ds-snowflake-generate-pat)
- Store the PAT for authenticating with DSPM.
[]![Creating a programmatic access token for a user in the Snowflake admin panel UI](/downloads/dspm/administration/service-registration/snowflake-database/adding-snowflake-database-account/ds-snowflake-generate-pat.png)
[]To create a role and grant DSPM with permissions to query the Snowflake data for scanning, run the following command:
`CREATE ROLE dspmdatascanrole;
GRANT usage ON WAREHOUSE dspmwarehouse TO ROLE dspmdatascanrole ;
grant MONITOR SECURITY ON ACCOUNT to role dspmdatascanrole;
grant MONITOR USAGE ON ACCOUNT to role dspmdatascanrole;
GRANT DATABASE ROLE SNOWFLAKE.SECURITY_VIEWER TO ROLE dspmdatascanrole;`
Run the following script to grant necessary privileges to the role:
`CREATE OR REPLACE PROCEDURE z_dspm_grant_db_read()
RETURNS varchar
LANGUAGE SQL
AS
DECLARE
cur CURSOR FOR SELECT db_name FROM regular_databases;
db_name STRING;
dspm_role_name STRING := 'dspmdatascanrole';
grants NUMBER := 0;
BEGIN
SHOW DATABASES;
CREATE OR REPLACE TEMP TABLE regular_databases AS
SELECT "name" AS db_name
FROM TABLE(RESULT_SCAN(LAST_QUERY_ID()))
WHERE "origin" = '';
FOR record IN cur DO
db_name := record.db_name;
EXECUTE IMMEDIATE 'GRANT USAGE ON DATABASE "' || db_name || '" TO ROLE ' ||  dspm_role_name;
EXECUTE IMMEDIATE 'GRANT USAGE ON ALL SCHEMAS IN DATABASE "' || db_name || '" TO ROLE ' ||  dspm_role_name;
EXECUTE IMMEDIATE 'GRANT USAGE ON FUTURE SCHEMAS IN DATABASE "' || db_name || '" TO ROLE ' ||  dspm_role_name;
EXECUTE IMMEDIATE 'GRANT SELECT ON ALL TABLES IN DATABASE "' || db_name || '" TO ROLE ' ||  dspm_role_name;
EXECUTE IMMEDIATE 'GRANT SELECT ON FUTURE TABLES IN DATABASE "' || db_name || '" TO ROLE ' ||  dspm_role_name;
grants := grants + 5;
END FOR;
RETURN grants || ' grants executed on non-shared databases.';
END;`
Run the following `grant` procedure that the script created:
`CALL z_dspm_grant_db_read();`
Optional: In case you want this DSPM role to automatically discover and scan the newly added databases, run the following command once. This creates a Snowflake task that runs the `grant` procedure at regular intervals to get access to any newly added databases:
`CALL z_dspm_grant_db_read();
CREATE OR REPLACE TASK z_dspm_role_grant_task
schedule = 'USING CRON 0 2 * * * UTC'   -- runs every day at 2am UTC; edit as needed
AS
CALL z_dspm_grant_db_read();`
[]A dedicated warehouse is required so that DSPM has the necessary resources in Snowflake.
Run the following command in Snowflake to create a warehouse:
`CREATE OR ALTER WAREHOUSE dspmwarehouse;
- By default this will create with size x-small`
Adding a Snowflake Account
To add a Snowflake account:
- Go to **Administration **>** Configuration **>** Service Registration**.
-
On the **Service Registration** page, select the **Snowflake** tab, and click **Add Account**.
[See image.](#img_add)
The **Add Snowflake Account** window appears.
- In the **Add Snowflake Account** window, update the required fields:
-
In the **Account Information** section:
- **Account Alias** (Optional): Enter a name to identify the Snowflake account in DSPM.
- **Account Edition**: Select the edition of the Snowflake account.
- **Account Name**: Snowflake account name as configured in the Snowflake.
- **Organization Name**: Enter the Snowflake organization name.
- **Cloud Provider**: Select the cloud service provider hosting the Snowflake account (AWS, Azure, or GCP).
- **Cloud Region**: Search for and select the region where the Snowflake account is located.
- **Business Unit**: Assign the [business unit](/dspm/about-business-units) to the Snowflake account.
- **DSPM Integration Alias**: Enter the DSPM alias for the Snowflake account.
[See image.](#ds-addsnow-accinfo)
-
In the **Authentication** section, select the **Secret Provider Type**:
The authentication option differs depending on the cloud service provider.
- [AWS Secrets Manager](#aws-secret-manager)
- [Azure Key Vault](#azure-key-vault)
- [GCP Secrets Manager](#gcp-secret-manager)
- Click **Save**.
The Snowflake account is added and displayed on the [Snowflake](/dspm/about-service-registration) page. To configure the scan settings, see [Configuring Scan Settings for Snowflake Databases](/dspm/configuring-scan-settings-snowflake-databases).
[]For the Authentication Type, select any of the following:
-
Key-Pair
- **Username**: Enter the DSPM username.
- **Private Key AWS Secret ARN**: Enter the ARN of the HashiCorp Vault instance where the database credentials are stored.
- **Passphrase AWS Secret ARN** (Optional): Enter the ARN of the HashiCorp Vault instance where the database credentials are passphrased.
[See image.](#ds-snowflake-aws-key)
-
Username/Password
- **Username**: Enter the DSPM username.
- **AWS Secret ARN**: Enter the ARN of the secret storing the password. In order for DSPM to read the password and connect to the database, ensure to create and store the secret in the AWS account where the orchestrator account is present.
[See image.](#ds-snowflake-aws-us)
[]For the Authentication Type, select any of the following:
-
Key-Pair
- **Username**: Enter the DSPM username.
- **Private Key Azure Key Vault URI**: Enter the URI of the HashiCorp Vault instance where the database credentials are stored.
- **Passphrase Azure Key Vault URI** (Optional): Enter the URI of the HashiCorp Vault instance where the database credentials are passphrased.
[See image.](#ds-snowflake-azure-key)
-
Username/Password
- **Username**: Enter the DSPM username.
- **Azure Key Vault URI**: Enter the URI of the secret storing the password. In order for DSPM to read the password and connect to the database, ensure to create and store the secret in the Key Vault of the worker plane resource group [integration_id_worker_plane_rg] of the Azure subscription where the orchestrator account is present.
[See image.](#ds-snowflake-azure-us)
[]For the Authentication Type, select any of the following:
-
Key-Pair
- **Username**: Enter the DSPM username.
- **Private Key GCP Secret ID**: Enter the Secret ID path of the HashiCorp Vault instance where the database credentials are stored.
- **Passphrase GCP Secret ID** (Optional): Enter the Secret ID path of the HashiCorp Vault instance where the database credentials are passphrased.
[See image.](#ds-snowflake-gcp-key)
-
Username/Password
- **Username**: Enter the DSPM username.
- **GCP Secret ID**: Enter the Secret ID path of the secret storing the password. In order for DSPM to read the password and connect to the database, ensure to create and store the secret in the secret manager of the GCP project where the orchestrator account is present.
[See image.](#ds-snowflake-gcp-us)
[]![Add Snowflake Account page with the necessary account information details filled.](/downloads/dspm/administration/service-registration/snowflake-database/adding-snowflake-database-account/ds-add-snowflake-accinfo.png?s34394d1751351751)
[]![The Snowflake page with a list of accounts and annotation around the Add Account button.](/downloads/dspm/administration/service-registration/snowflake-database/adding-snowflake-database-account/snowflake-add-button.png)
[]![AWS authentication with Username, and AWS Secret ARN.](/downloads/dspm/administration/service-registration/snowflake-database/adding-snowflake-database-account/ds-snowflake-aws-us.png)
[]![AWS authentication with Key-Pair.](/downloads/dspm/administration/service-registration/snowflake-database/adding-snowflake-database-account/ds-snowflake-aws-kp.png)
[]![Azure authentication with Username, and Azure Key Valut URI.](/downloads/dspm/administration/service-registration/snowflake-database/adding-snowflake-database-account/ds-snowflake-azure-un.png)
[]![Azure authentication with Key-Pair.](/downloads/dspm/administration/service-registration/snowflake-database/adding-snowflake-database-account/ds-snowflake-azure-key.png)
[]![GCP authentication with Username, and GCP Secret ID.](/downloads/dspm/administration/service-registration/snowflake-database/adding-snowflake-database-account/ds-snowflake-gcp-un.png)
[]![GCP authentication with Key-Pair.](/downloads/dspm/administration/service-registration/snowflake-database/adding-snowflake-database-account/ds-snowflake-gcp-key.png)