# Configuring the Hosted User Database
Source: https://help.zscaler.com/zia/configuring-hosted-user-database
PDF: https://help.zscaler.com/pdf/com/en/1399551.pdf

With this [provisioning method](/zia/choosing-provisioning-and-authentication-methods), you can upload user information to the Zscaler database by simply adding the information manually in the ZIA Admin Portal, importing the information from a CSV (Comma-Separated Value) file, or using the [Zscaler Authentication Bridge](/zia/about-zscaler-authentication-bridge). There is no limit to the number of users that an organization can store in the database.
When users are added directly to the Zscaler database, password-based authentication is the default authentication method. The passwords are uploaded with the username, group and department information, and they are stored in the database in an encrypted format. You can define the complexity of passwords and configure expiry periods. For additional security, you can require users to enter a password that is different from their corporate password.
The Zscaler Central Authority (CA) authenticates users according to the method configured for the organization. With password-based authentication, the CA displays the password request form to the user after it receives the request with the username from the ZIA Public Service Edge. After the user submits the password, the CA matches it with the password in the database. It authenticates the user when it finds a match.
Configuring the Hosted User Database
To configure the Hosted User Database as your provisioning method:
- [1. Enable Enforce Authentication for the Location](#enable-enforce-authentication-location)
- [2. Configure the Hosted User Database](#configure-hosted-user-datebase)
- [3. Add Users, Groups, and Departments in Database](#add-users-groups-departments)
Troubleshooting
If a hosted user is unable to authenticate, go to **Administration **>** User Management** and verify the user's **User ID** and **Password**. The user might have entered an incorrect password, so try resetting it.
[]To enable authentication for a location:
- Go to **Administration **>** Location**.
- Click the **Edit** icon next to the location.
The **Edit Location** window appears.
- In the **Edit Location** window, enable **Enforce Authentication**.
- Click **Save** and [activate the change](/zia/saving-and-activating-changes-admin-portal).
[]To configure the Zscaler Hosted User Database:
- Go to **Administration** >** Authentication Settings**.
- In the **Authentication Profile **section:
- **Directory Type**: Choose **Hosted DB**.
- **Authentication Frequency**: Choose how often users are required to authenticate to the Zscaler service. If you select **Custom**, specify 1 to 180 days.
- **Authentication Type**: Choose **Form-Based**.
- **Temporary Authentication**: Choose [One-Time Token or One-Time Link](/zia/about-one-time-tokens-or-links) if you would like to use a temporary authentication method.
- **Password Strength**: Choose one of the following options:
- **None**: Have no restriction on the strength or complexity of the passwords. This is the default.
- **Medium**: Require users to set passwords that are at least eight characters long and contain at least one non-alphabetic character. Only ASCII characters are allowed.
- **Strong**: Require users to set passwords that are at least eight characters long and contain at least one digit, one capital letter, and one special character. Only ASCII characters are allowed.
- **Password Expiry**: Choose the duration after which users must change their passwords. The default is **Never**.
- Click **Save** and [activate the change](/zia/saving-and-activating-changes-admin-portal).
[]To add users, groups, and departments in the Zscaler database:
- Go to **Administration **>** User Management**.
- In the **Users** tab, you can:
- [Manually add each user along with their group and department](/zia/adding-user-account)
- [Import a CSV file with user information](/zia/importing-user-information-csv-file)
- [Use the Zscaler Authentication Bridge to import user information](/zia/about-zscaler-authentication-bridge)