# Editing or Deleting a Snowflake Database Account
Source: https://help.zscaler.com/dspm/editing-or-deleting-snowflake-account-details
PDF: https://help.zscaler.com/pdf/com/en/1530677.pdf

You can modify or delete a Snowflake database account as required.
Editing a Snowflake Database Account
To edit a Snowflake database account:
- Go to **Administration **>** Configuration **>** Service Registration**.
- On the **Service Registration** page, select the **Snowflake **tab.
-
Do one of the following:
-
Click **Actions** (![fa-action.png](/downloads/dspm/administration/unmanaged-database/editing-or-deleting-unmanaged-database/fa-action.png)
), and select **Edit** for the required database account.
[See image.](#ds-unmd-action-edit)
-
Click the name of the database server to go to the [About Service Registration](/dspm/about-service-registration) details page, then Click **Actions**, and select **Edit**.
[See image.](#ds-unmd-details-edit)
The **Edit Snowflake Account** window appears.
-
In the **Edit Snowflake Account** window, click **Proceed** to continue.
[See image.](#img_confirm-message)
-
In the **Edit Snowflake Account** window, update the required fields:
- In the **Account Information** section:
- **Account Edition**: Update the edition of the Snowflake account.
- **Cloud Provider**: Update the cloud service provider hosting the Snowflake account.
- **Cloud Region**: Update the region where the Snowflake account is located.
- **Business Unit**: Update the [business unit](/dspm/about-business-units) to the Snowflake account.
- **DSPM Integration Alias**: Update the DSPM alias for the Snowflake account.
-
In the **Authentication** section, select the **Secret Provider Type**:
The authentication option differs depending on the cloud provider.
- [AWS Secrets Manager](#aws-secret-manager)
- [Azure Key Vault](#azure-key-vault)
- [GCP Secrets Manager](#gcp-secret-manager)
[See image.](#img_edit-snowflake)
- Click **Save**.
The Snowflake database account is updated.
Changes made to the Snowflake account configuration take effect only at the next scheduled scan.
[]For the **Authentication Type**, select any of the following:
-
Key-Pair
- **Username**: Update the DSPM username.
- **Private Key AWS Secret ARN**: Update the ARN of the HashiCorp Vault instance where the database credentials are stored.
- **Passphrase AWS Secret ARN** (Optional): Update the ARN of the HashiCorp Vault instance where the database credentials are passphrased.
[See image.](#ds-snowflake-aws-key)
-
Username/Password
- **Username**: Update the DSPM username.
- **AWS Secret ARN**: Update the ARN of the secret storing the password.
[See image.](#ds-snowflake-aws-us)
[]For the **Authentication Type**, select any of the following:
-
Key-Pair
- **Username**: Update the DSPM username.
- **Private Key Azure Key Vault URI**: Update the URI of the HashiCorp Vault instance where the database credentials are stored.
- **Passphrase Azure Key Vault URI** (Optional): Update the URI of the HashiCorp Vault instance where the database credentials are passphrased.
[See image.](#ds-snowflake-azure-key)
-
Username/Password
- **Username**: Update the DSPM username.
- **Azure Key Vault URI**: Update the URI of the secret storing the password.
[See image.](#ds-snowflake-azure-us)
[]For the **Authentication Type**, select any of the following:
-
Key-Pair
- **Username**: Update the DSPM username.
- **Private Key GCP Secret ID**: Update the Secret ID path of the HashiCorp Vault instance where the database credentials are stored.
- **Passphrase GCP Secret ID** (Optional): Update the Secret ID path of the HashiCorp Vault instance where the database credentials are passphrased.
[See image.](#ds-snowflake-gcp-key)
-
Username/Password
- **Username**: Update the DSPM username.
- **GCP Secret ID**: Update the Secret ID path of the secret storing the password.
[See image.](#ds-snowflake-gcp-us)
[]![The Edit Snowflake Account page with information relating to the account and authentication.](/downloads/dspm/administration/service-registration/snowflake-database/editing-or-deleting-snowflake-account-details/edit-snowflake.png)
[]![Confirm editing snowflake account window](/downloads/dspm/administration/service-registration/snowflake-database/editing-or-deleting-snowflake-account-details/confirm_message.png?s14629d1751373487)
[]![Service Registration page with the Actions menu open, and showing the Edit option annotated.](/downloads/dspm/administration/service-registration/snowflake-database/editing-or-deleting-snowflake-account-details/ds-snow-action-edit.png)
[]![Unmanaged Databases details page with a highlighted edit icon.](/downloads/dspm/administration/service-registration/snowflake-database/editing-or-deleting-snowflake-account-details/ds-snowflake-details-edit.png)
Deleting a Snowflake Account
To delete a Snowflake account:
- Go to **Administration **>** Configuration **>** Service Registration**.
- On the **Service Registration** page, select the **Snowflake **tab.
-
Do one of the following:
-
Click **Actions** (![fa-action.png](/downloads/dspm/administration/unmanaged-database/editing-or-deleting-unmanaged-database/fa-action.png)
), and select **Delete **for the required database server.
[See image.](#ds-unmd-action-delete)
-
Click the name of the database server to go to the [Unamanaged Database details](/dspm/about-unmanaged-database#db-details) page, then Click **Actions**, and select **Delete**..
[See image.](#ds-unmd-details-delete)
The **Delete Snowflake Account** window appears.
-
In the **Delete Snowflake Account** window, read the message, and then enter `CONFIRM` in the text box.
[See image.](#img_delete-db)
- Click **Delete Account**.
The Snowflake account is deleted from the DSPM Admin Portal.
[]![Snowflake page with the Actions menu open, and showing the Delete option annotated.](/downloads/dspm/administration/service-registration/snowflake-database/editing-or-deleting-snowflake-account-details/ds-snow-action-delete.png)
[]![Snowflake account details page with a highlighted delete option.](/downloads/dspm/administration/service-registration/snowflake-database/editing-or-deleting-snowflake-account-details/ds-snowflake-details-delete.png)
[]![Confirming deletion of a snowflake account](/downloads/dspm/administration/service-registration/snowflake-database/editing-or-deleting-snowflake-account-details/delete-message.png)
[]![AWS authentication with Username, and AWS Secret ARN.](/downloads/dspm/administration/service-registration/snowflake-database/adding-snowflake-database-account/ds-snowflake-aws-us.png)
[]![AWS authentication with Key-Pair.](/downloads/dspm/administration/service-registration/snowflake-database/adding-snowflake-database-account/ds-snowflake-aws-kp.png)
[]![Azure authentication with Username, and Azure Key Valut URI.](/downloads/dspm/administration/service-registration/snowflake-database/adding-snowflake-database-account/ds-snowflake-azure-un.png)
[]![Azure authentication with Key-Pair.](/downloads/dspm/administration/service-registration/snowflake-database/adding-snowflake-database-account/ds-snowflake-azure-key.png)
[]![GCP authentication with Username, and GCP Secret ID.](/downloads/dspm/administration/service-registration/snowflake-database/adding-snowflake-database-account/ds-snowflake-gcp-un.png)
[]![GCP authentication with Key-Pair.](/downloads/dspm/administration/service-registration/snowflake-database/adding-snowflake-database-account/ds-snowflake-gcp-key.png)