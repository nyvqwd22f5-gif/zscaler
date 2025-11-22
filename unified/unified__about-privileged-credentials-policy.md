# About Privileged Credentials Policy
Source: https://help.zscaler.com/unified/about-privileged-credentials-policy
PDF: https://help.zscaler.com/pdf/com/en/1493851.pdf

Privileged credentials policy rules enable you to designate privileged consoles with allocated credentials. When you create a privileged credential, you can select the protocol (SSH, RDP, or VNC) and add the related login details (i.e., username, password, SSH key, etc). After the privileged credential and privileged credential pools are set up, you can create the privileged credentials policy to map the privileged credentials to the associated privileged console using SAML and SCIM information.
Privileged credential policy rules provide the following benefits and enable you to:
- Set up credentials for SSH, RDP, or VNC protocols.
- Assign privileged consoles to have designated privileged credentials or privileged credential pools to allow users to access them.
If you want to configure privileged credentials-based control, you must first create the [privileged consoles](/unified/about-privileged-consoles) that you want to assign control to. Then you need to create the [privileged credentials](/unified/about-privileged-credentials) or [privileged credential pools](/unified/about-privileged-credential-pools) that you're going to apply the policy to.
About the Privileged Credentials Policy Page
On the Privileged Credentials Policy page (Policies > Access Control > Clientless > Privileged Policies > Privileged Credentials), you can do the following:
- View a list of applied filters available from the current and previous user sessions. Applied filters must be saved to the user session first before they can be viewed. Use the drop-down menu to select the applied filters to view. To learn more, see [Using Tables](/unified/using-tables#filterData).
- Hide the filters on the page by clicking **Hide Filters**. Click **Show Filters** to display the filters.
- Refresh the Privileged Credentials Policy page to reflect the most current information.
- Filter the information that appears in the table. By default, no filters are applied. You can also save applied filters to your preferences so that they're visible in future user sessions. To learn more, see [Using Tables](/unified/using-tables#filterData).
- [Add a new privileged credentials policy rule.](/unified/configuring-privileged-credentials-policies)
- Expand all the displayed rows in the table to see more information about each policy rule.
- View a list of all privileged credentials policy rules that were configured. For each rule, you can see:
- **Rule Order**: The policy evaluation order number for the rule. Policy rules are applied based on the order they are listed here. Change the rule order by clicking on the number and manually entering a new value.
You need to have at least two privileged credential policies created for the first rule privileged credential policy to apply. The privileged credential associated with the last privileged credential policy won't be applied to its related privileged console. Ensure that the last privileged credential policy is one that you do not need to use.
- **Name**: The name of the privileged credentials policy rule. The description is also displayed here, if available.
- **Status**: The status of the rule as being enabled or disabled to privileged credentials
- **Credential**: The name of the privileged credential you have assigned for that specific policy rule.
- Copy an existing privileged credentials policy rule's criteria, and use it to create a new rule.
- [Edit an existing privileged credentials policy rule.](/unified/editing-privileged-credentials-policies)
- Delete a privileged credentials policy rule.
- [Modify the columns displayed in the table.](/unified/using-tables)
- Display more rows or a different page of the table.
- Depending on your Admin Portal subscriptions, you see the following policy options:
- Consoles Policy
- [Portals Policy](/unified/about-portals-policy)
![Viewing and managing privileged credentials policies on the Privileged Credentials Policy page](/downloads/unified/policies/private-applications/access-control/clientless/privileged-remote-access-policy/about-privileged-credentials-policy/experience-center-privileged-credentials-policy-page.png)