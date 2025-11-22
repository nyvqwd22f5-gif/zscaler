# About VPN User Enablement
Source: https://help.zscaler.com/zpa/about-vpn-user-enablement
PDF: https://help.zscaler.com/pdf/com/en/1529081.pdf

User enablement rules define which users gain access to VPN tunnels. A VPN connected user can't connect to the VPN Service Edge if they aren't entitled for VPN (for Legacy Apps). The user enablement rules validate if the VPN connected user is allowed to access VPN (for Legacy Apps).
You can configure the following criteria types with user enablement: posture profiles, SAML attributes, and SCIM attributes. The posture profile criteria option provides continuous validation checks of VPN connected users’ device posture. If the device's posture changes and no longer meets the defined requirements set by the posture profile rule, then the VPN (for Legacy Apps) session is deactivated. VPN (for Legacy Apps) sessions only remain active when VPN connected users’ devices remain compliant. The SAML and SCIM attributes criteria options allow you to select which VPN connected users are allowed VPN tunnel access.
User enablement provides the following benefits and enables you to:
-
Manage which VPN connected users have access to VPN tunnels for VPN (for Legacy Apps).
-
Set continuous posture profile validation for a VPN connected user's device.
User enablement rules are comprised of two main building blocks:
- Criteria: These are the conditions of a user enablement rule. A VPN tunnel request must match all the conditions within a user enablement rule.
- Boolean Operators: These are the operands used between criteria. User enablement rules use AND and OR operators.
About the User Enablement Page
On the User Enablement page (VPN (for Legacy Apps) > User Enablement > User Enablement), you can do the following:
- View a list of applied filters available from the current and previous user enablement rules. Applied filters must be saved to the user enablement rule first before they can be viewed. Use the drop-down menu to select the applied filters to view. To learn more, see [Using Tables](/zpa/using-tables#filterData).
- Hide the filters on the page by clicking **Hide Filters**. Click **Show Filters** to show the filters.
- Refresh the** User Enablement** page to reflect the most current information.
- Filter the information that appears in the table. By default, no filters are applied. You can also save applied filters to your preferences so that they're visible in future user enablement rules. To learn more, see [Using Tables](/zpa/using-tables#filterData).
- [Add a new user enablement rule.](/zpa/configuring-vpn-user-enablement)
- Expand all the displayed rows in the table to see more information about each user enablement rule.
- View a list of all user enablement rules that were configured. For each rule, you can see:
- **Rule Order**: ZPA applies rules based on the order they are listed here. Change the rule order by clicking the number and manually entering a new value. When the row is expanded, the description is displayed if available and a **Criteria** section provides a visual representation of the criteria (e.g., SCIM attributes, SAML attributes, and posture profiles) and Boolean logic used within the rule.
- **Name**: The name of the user enablement rule.
- **Status**: Indicates if the user enablement rule is enabled or disabled.
- **Rule Action**: Indicates if the user enablement rule will allow access** **or block access.
- Copy an existing user enablement rule, and use it to create a new user enablement rule.
- [Edit an existing user enablement rule.](/zpa/editing-vpn-user-enablement)
- Delete a user enablement rule.
- [Modify the columns displayed in the table.](/zpa/using-tables)
- Display more rows or a different page of the table.
- Open the [Zscaler Help Browser](/zpa/using-zscaler-help-browser) and view Help Portal articles without leaving the ZPA Admin Portal.
![VPN User Enablement page within the ZPA Admin Portal](/downloads/zpa/editing-vpn-user-enablement/5.1.25%20update%20user%20enablement%20page%20w%20steps.png)