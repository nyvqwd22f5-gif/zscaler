# About Privileged Credentials Policy
Source: https://help.zscaler.com/zpa/about-privileged-credentials-policy
PDF: https://help.zscaler.com/pdf/com/en/1485566.pdf

Privileged credentials policy rules enable you to designate privileged consoles with allocated credentials. When you create a privileged credential, you can select the protocol (SSH, RDP, or VNC) and add the related login details (i.e., username, password, SSH key, etc). After the privileged credential and privileged credential pools are set up, you can create the privileged credentials policy to map the privileged credentials to the associated privileged console using SAML and SCIM information.
Privileged credential policy rules provide the following benefits and enable you to:
- Set up credentials for SSH, RDP, or VNC protocols.
- Assign privileged consoles to have designated privileged credentials or privileged credential pools to allow users to access them.
If you want to configure privileged credentials-based control, you must first create the [privileged consoles](/zpa/about-privileged-consoles) that you want to assign control to. Then you need to create the [privileged credential](/zpa/about-privileged-credentials) or [privileged credential pools](/zpa/about-privileged-credential-pools) that you're going to apply the policy to.
About the Privileged Credentials Policy Page
On the Privileged Credentials Policy page (Policy > Privileged Policies > Privileged Credentials Policy), you can do the following:
- View a list of applied filters available from the current and previous user sessions. Applied filters must be saved to the user session first before they can be viewed. Use the drop-down menu to select the applied filters to view. To learn more, see [Using Tables](/zpa/using-tables#filterData).
- Hide the filters on the page by clicking **Hide Filters.** Click **Show Filters** to display the filters.
- Refresh the Privileged Credentials Policy page to reflect the most current information.
- Filter the information that appears in the table. By default, no filters are applied. You can also save applied filters to your preferences so that they're visible in future user sessions. To learn more, see [Using Tables](/zpa/using-tables#filterData).
- [Add a new privileged credentials policy rule.](/zpa/configuring-privileged-credentials-policies)
- Expand all the displayed rows in the table to see more information about each policy rule.
- View a list of all privileged credentials policy rules that were configured. For each rule, you can see:
- **Rule Order**: The [policy evaluation order](/zpa/about-access-and-application-group-policies#PolicyEvalOrder) number for the rule. ZPA applies policy rules based on the order they are listed here. Change the rule order by clicking on the number and manually entering a new value.
You need to have at least two privileged credential policies created for the first rule privileged credential policy to apply. The privileged credential associated with the last privileged credential policy won't be applied to its related privileged console. Ensure that the last privileged credential policy is one that you do not need to use.
- **Name**: The name of the privileged credentials policy rule. The description is also displayed here, if available.
- **Status**: The status of the rule as being enabled or disabled to privileged credentials.
- **Credential**: The name of the privileged credential or privileged credential pool you have assigned for that specific policy rule. The privileged credential or privileged credential pool icon is also displayed.
- Copy an existing privileged credentials policy rule's criteria, and use it to create a new rule.
- [Edit an existing privileged credentials policy rule.](/zpa/editing-privileged-credentials-policy)
- Delete a privileged credentials policy rule.
- [Modify the columns displayed in the table.](/zpa/using-tables)
- Display more rows or a different page of the table.
- Depending on your Privileged Remote Access (PRA) subscriptions, you see the following privileged policy options:
- [Consoles Policy](/zpa/about-consoles-policy)
- [Portals Policy](/zpa/about-portals-policy)
- Depending on your ZPA Admin Portal subscriptions, you see the following ZPA policy options:
- [Access Policy](/zpa/about-access-policy)
- [Timeout Policy](/zpa/about-reauthPolicy)
- [Client Forwarding Policy](/zpa/about-client-forwarding-policy)
- [Isolation Policy](/zpa/about-isolation-policy)
- [Security Policy](/zpa/about-security-policy)
- [Redirection Policy](/zpa/about-redirection-policy)
![Privileged Credentials Policy page within the ZPA Admin Portal](/downloads/zpa/policies/privileged-remote-access-policy/about-privileged-credentials-policy/Credentials%20Policy%20page%20w%20steps_0.png)