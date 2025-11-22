# About Privileged Credentials
Source: https://help.zscaler.com/unified/about-privileged-credentials
PDF: https://help.zscaler.com/pdf/com/en/1492556.pdf

Privileged credentials can be used to streamline access to privileged consoles by mapping authentication details using a [privileged credentials policy](/unified/about-privileged-credentials-policy). The user can then gain access to the privileged console that the privileged credentials were designated to. After you create a privileged credential, you can map it to a privileged console by creating a privileged credential policy using the SAML and SCIM policy criteria types.
Privileged credentials provide the following benefits and enable you to:
- Allow controlled access to users by using a privileged console with allocated credentials.
- Provide users access to the privileged console without having to manually log in.
- Allow users to start a privileged console session without needing to provide credentials.
If you want to use privileged credentials, you must first create the [privileged portals](/unified/about-privileged-portals) and [privileged consoles](/unified/about-privileged-consoles) that you want to assign the credentials to.
About the Privileged Credentials Page
On the Privileged Credentials Policy page (Policies > Clientless > Privileged Credentials), you can do the following:
- [Add a new privileged credential](/unified/configuring-privileged-credentials).
-
Filter the information that appears in the table. By default, no filters are applied.
If you are using a [Microtenant](/unified/about-microtenants), then the **Microtenant Ownership Type** filter is available. By default, the **Configured within Microtenant** filter option is applied to show the privileged credentials configured within that specific Microtenant. The options for the filter are based on access type (**Global **and **Configured within Microtenant**). The **Global** option filters the information in the table that is configured within the Default Microtenant. The only available operator for this filter type is **Equals**.
- View a list of all privileged credentials that are configured. For each privileged credential, you can see:
- **Name**: The name of the privileged credential.
- **Type**: The protocol type that was designated for that particular privileged credential. The protocol type options are SSH, RDP, and VNC. Each protocol type has its own credential requirements.
After the type is selected and the privileged credential is saved, this option can’t be changed.
- **Username**: The username associated with the credentials you are using.
- **Updated Time**: The date, time, and time zone that the privileged credential was created on.
Privileged credentials that are created in the Default Microtenant are inherited across Microtenants.
- [Edit an existing privileged credential.](/unified/editing-privileged-credentials)
If the credentials are changed after you created and saved the privileged credential, you need to edit the privileged credential to update the new credential details (e.g., Username, Password, Private Key) for the privileged credential to continue being used.
-
[Move the privileged credential in a Microtenant](/unified/moving-resources-microtenant#PrivilegedCredentials).
If privileged credential policies are associated with the privileged credential, then the policies must be deleted to move the privileged credential to a different Microtenant.
- Delete a privileged credential.
![Viewing and managing privileged credentials in the Privileged Credentials page](/downloads/unified/policies/private-applications/access-control/clientless/privileged-remote-access-management/privileged-credentials/about-privileged-credentials/unified-privileged-credentials-page.png)