# Manage SaaS Application Components
Source: https://help.zscaler.com/zia/manage-saas-application-components
PDF: https://help.zscaler.com/pdf/com/en/1529449.pdf

SaaS applications, such as SharePoint, might have dozens, hundreds, or even thousands of individual component sites. Instead of creating DLP policies for each of them individually, you can create groups of sites that you want to share the same DLP policies.
Create Groups
To create groups:
- From the **Manage SaaS Application Components** page, select the **Groups** tab.
-
At the top right of the page, select an available application.
[See image.](#group_app)
-
Click **Add Group**.
[See image.](#group_add)
The **Add Group** window appears.
-
In the **Add Group** window, enter a name for your group, and under **SaaS Application Tenant** select one of your tenants. If you haven't added one yet, see [Adding SaaS Application Tenants](/zia/adding-saas-application-tenants).
[See image.](#add_group_window)
- Under **Sites**, you can choose to manually add or import sites. A group can contain a maximum of 10,000 sites.
-
**Add Sites**: Click the drop-down menu, select your desired sites from the list, and click **Done**.
[See image.](#add_sites)
-
**Import Sites**: Click **Choose File** and select a CSV file with your list of desired sites. A sample file is available to download by clicking **Sample Import CSV File**.
[See image.](#import_sites)
- In the **Comment** field, you can enter optional information regarding the group you are creating.
- Click **Save**.
To learn more about setting up the DLP policies for groups, see [About Data at Rest Scanning DLP](/zia/about-data-rest-scanning-dlp) and [Configuring the Data at Rest Scanning DLP Policy](/zia/configuring-data-rest-scanning-dlp-policy).
Manage Groups and Components
In addition to creating groups, you can manage your groups and download lists of them as well.
From the **Groups** tab, you can click the **Edit** button to make any changes to an existing group. You can also download a list of your groups in a CSV file by clicking **Download**.
[See image.](#group_edit)
From the **Components** tab, you can view a list of all of your sites and the group and tenant they are associated with. You can also download a list of your sites in a CSV file by clicking **Download**.
[See image.](#comp_tab)
[]![Manage SaaS Application Tenant page, group tab selected with annotation around the drop-down menu](/downloads/zia/saas-applications/Manage%20Tenant%20drop.png)
[]![Manage SaaS Application Tenant page, group tab selected with annotation around Add Group button](/downloads/zia/saas-applications/Manage%20Tenant%20add%20group.png)
[]![Manage SaaS Application Components Add Group window](/downloads/zia/saas-applications/Manage%20tenant%20Add%20Group%20Window.png)
[]![Add Group page, with the manual Add Sites option selected and the drop-down menu open](/downloads/zia/saas-applications/Manage%20Tenant%20add%20sites.png)
[]![Add Groups page with Import Sites option selected](/downloads/zia/saas-applications/Manage%20Tenant%20import.png)
[]![Manage SaaS Application Tenant page, Group tab selected with annotation around the Edit button](/downloads/zia/saas-applications/Manage%20Tenant%20edit3.png)
[]![Manage SaaS Application Tenant page, Component tab selected.](/downloads/zia/saas-applications/Manage%20Tenant%20components%20tab2.png)