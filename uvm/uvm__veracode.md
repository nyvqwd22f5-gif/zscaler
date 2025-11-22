# Veracode
Source: https://help.zscaler.com/uvm/veracode
PDF: https://help.zscaler.com/pdf/com/en/1528321.pdf

![The Veracode and Veracode SCA tiles](/downloads/uvm/configure/sources/veracode/4fb8fbd5-e252-49c7-86c0-51ba1e89420b.png)
Veracode provides visibility into application threats by continuously finding flaws and vulnerabilities at every stage of the software development lifecycle.
The SecOps platform Veracode Connection gathers information about open and mitigated findings associated with applications and development sandboxes.
The SecOps platform has two Veracode connectors:
- Veracode: Retrieves Static Analysis, Dynamic Analysis, Manual Penetration Testing, and Software Composition Analysis findings.
- Veracode SCA: Retrieves Software Composition analysis findings. This is separate since Veracode does not combine SCA findings with other finding types.
Required Parameters
- Access Key
- Secret Key
Permissions
To set up the Veracode API, you need to have one of the following accounts:
- An API service account with the **Results API** role. To learn more, refer to the [Veracode documentation](https://docs.veracode.com/r/c_API_roles_details).
- A user account with the **Reviewer** or **Security Lead** role. To learn more, refer to the [Veracode documentation](https://docs.veracode.com/r/c_role_permissions).
Generating API Credentials
- In the Veracode Platform, from the user account drop-down menu, select **API Credentials**.
- Click **Generate API Credentials**.
- Copy the ID and secret key to a secure place. They are not accessible after you exit the window.
To learn more, refer to the [Veracode documentation](https://docs.veracode.com/r/c_api_credentials3).
Veracode also requires HMAC authentication, which is done on the SecOps platform and does not require any actions on the Veracode platform. To learn more, refer to the [Veracode documentation](https://docs.veracode.com/r/c_enabling_hmac).
Creating an API Service Account
You cannot change an existing user account to an API service account. You must create a new user:
- In the Veracode platform, from the top right, click the gear icon and select **Admin**.
- On the **Users** tab, click **Add New User**.
- Enter a descriptive first and last name.
- Select the **Non-Human User** checkbox.
- Provide a valid email address. Veracode sends notifications about error messages, password expiration, and other automated success and error messages to this email.
- Optionally, define the IP range restrictions for the user. To learn more, refer to the [Veracode documentation](https://docs.veracode.com/r/admin_ip).
-
In the **User Roles** section, select the APIs you want the API service account to access.
You must select the **Results API** role.
- Click **Save** to create and enable the user. You receive an activation email.
To learn more, refer to the [Veracode documentation](https://docs.veracode.com/r/c_video_create_and_manage_api_users).