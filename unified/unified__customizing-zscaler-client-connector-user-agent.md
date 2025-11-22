# Customizing the Zscaler Client Connector User Agent
Source: https://help.zscaler.com/unified/customizing-zscaler-client-connector-user-agent
PDF: https://help.zscaler.com/pdf/com/en/1496341.pdf

You can customize the User Agent with a suffix that the IdP reads as specific strings it expects during authentication to identify the user agent. You can create a user agent suffix globally or for each domain.
To create either a global or domain-based suffix for a user agent:
- In the Admin Portal, go to **Infrastructure > Connectors > Client > User Agent**.
- In the **Customize User Agent Suffix** drop-down menu, select one of the following:
- [Global](#G-Suffix)
- [Domain-Based](#D-Suffix)
[]To enable the Global suffix:
- In the **Global User Agent Suffix **field, enter the suffix you want Zscaler Client Connector to append to user agents.
- Click **Save**.
[See image.](#global)
[]To create a user agent suffix for each domain:
-
For **Manage User Agent Suffix**, click **Add User Agent Suffix**.
[See image.](#domain)
- In the** Add Custom Suffix** window, complete the following fields:
- In the **Select Domain** drop-down menu, select a domain provisioned for your organization.
- In the **Enter Suffix** field, enter the suffix you want Zscaler Client Connector to append to user agents associated with this domain.
- Click **Add**.
[See image.](#add)
-
Click **Save **to add your user agent suffix.
[See image.](#save)
​​​​​To delete a suffix:
- Click the **Delete **icon (![Delete.png](/downloads/tech-pubs-drafts/client-connector-draft-articles/customizing-zscaler-client-connector-user-agent-doc-43330/Delete.png)
) next to the suffix.
-
In the **Confirm Delete** window, click **OK**.
[See image.](#delete)
- Click **Save**.
[]![Add Global Suffix to User Agent](/downloads/tech-pubs-drafts/client-connector-draft-articles/show-hide-version/Client-Connector-User-Agent-Global-Suffix.png)
[]![User Agent Suffix for Domain Based](/downloads/tech-pubs-drafts/client-connector-draft-articles/show-hide-version/User_Agent_Domain_Add_Suffix.png)
[]![Add Custom Suffix window](/downloads/tech-pubs-drafts/client-connector-draft-articles/show-hide-version/Domain-Add-Custom-Suffix.png)
[]![Save Domain Based Suffix](/downloads/tech-pubs-drafts/client-connector-draft-articles/show-hide-version/Domain-Based-Suffix-Save.png)
[]![Delete a User Agent](/downloads/tech-pubs-drafts/client-connector-draft-articles/show-hide-version/Delete%20Windows.png)