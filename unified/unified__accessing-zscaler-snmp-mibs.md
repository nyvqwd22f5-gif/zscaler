# Accessing the Zscaler SNMP MIBs
Source: https://help.zscaler.com/unified/accessing-zscaler-snmp-mibs
PDF: https://help.zscaler.com/pdf/com/en/1496366.pdf

The Simple Network Management Protocol (SNMP) is used for network monitoring. It collects and organizes management information about devices on IP networks. SNMP exposes this information in the management information bases (MIBs).
A MIB is a database used to manage the objects within a network. The Zscaler Enterprise SNMP MIBs are downloadable as files, which define all counters and assign them within the Zscaler database. You can use the MIBs to perform health monitoring on several different instances, like the [Nanolog Streaming Service (NSS)](/unified/understanding-nanolog-streaming-service) and the Internet & SaaS [Virtual Service Edges](/unified/about-virtual-service-edges).
To access the Zscaler Enterprise SNMP MIBs:
- [Step 1: Download the MIBs](#mibs)
- [Step 2: Configure the SNMP Admin User](#configure-snmp-admin)
- [Step 3: Load and View the MIBs](#load-view-mibs)
[]The Zscaler service supports the list of MIBs in the following tables. You can download the MIB files using the links provided in each table.
- [Virtual Service Edge MIBs](#vzen_mibs)
- [NSS MIBs](#nss_mibs)
- [Zscaler MIB Files](#zscaler_mibs)
[]
[](/downloads/zia/documentation-knowledgebase/analytics/snmp-mibs/about-the-zscaler-snmp-mibs/vzenmibs.tgz)
-
-
-
-
-
-
-
| **Virtual Service Edge MIBs** |
| ----------------------------- |
| VZENMIBS.tgz | This file contains the following MIB files:ZSCALER-OSNIC-MIBZSCALER-PROCESSHEALTH-MIBZSCALER-PROCESSWATCHDOG-MIBZSCALER-ROLEHEALTH-MIBZSCALER-SWAPINFO-MIBZSCALER-VSE-MIBZSCALER-ZSCALERNIC-MIB |
[]
[](/downloads/zia/documentation-knowledgebase/analytics/snmp-mibs/about-the-zscaler-snmp-mibs/nssmibs.tgz)
-
-
-
-
-
-
-
-
| **NSS MIBs** |
| ------------ |
| NSSMIBS.tgz | This file contains the following MIB files:ZSCALER-NSSFEED-MIBZSCALER-NSS-MIBZSCALER-OSNIC-MIBZSCALER-PROCESSHEALTH-MIBZSCALER-PROCESSWATCHDOG-MIBZSCALER-ROLEHEALTH-MIBZSCALER-SWAPINFO-MIBZSCALER-ZSCALERNIC-MIB |
[]
[](/downloads/zia/documentation-knowledgebase/analytics/snmp-mibs/about-the-zscaler-snmp-mibs/zscaler-nssfeed-mib.mib)[](/downloads/zia/documentation-knowledgebase/analytics/snmp-mibs/about-the-zscaler-snmp-mibs/zscaler-nss-mib.mib)[](/downloads/zia/documentation-knowledgebase/analytics/snmp-mibs/about-the-zscaler-snmp-mibs/zscaler-osnic-mib.mib)[](/downloads/zia/documentation-knowledgebase/analytics/snmp-mibs/about-the-zscaler-snmp-mibs/zscaler-processhealth-mib.mib)[](/downloads/zia/documentation-knowledgebase/analytics/snmp-mibs/about-the-zscaler-snmp-mibs/zscaler-processwatchdog-mib.mib)[](/downloads/zia/documentation-knowledgebase/analytics/snmp-mibs/about-the-zscaler-snmp-mibs/zscaler-rolehealth-mib.mib)[](/downloads/zia/documentation-knowledgebase/analytics/snmp-mibs/about-the-zscaler-snmp-mibs/zscaler-swapinfo-mib.mib)[](/downloads/zia/documentation-knowledgebase/analytics/snmp-mibs/about-the-zscaler-snmp-mibs/ZSCALER-VSE-MIB.mib)[](/downloads/zia/documentation-knowledgebase/analytics/snmp-mibs/about-the-zscaler-snmp-mibs/zscaler-zscalernic-mib.mib)
| **Zscaler MIB Files** | **Description** |
| --------------------- | --------------- |
| ZSCALER-NSSFEED-MIB.mib | This module describes information specific to NSS feeds. |
| ZSCALER-NSS-MIB.mib | This module describes information specific to the NSS instance. |
| ZSCALER-OSNIC-MIB.mib | This module describes the NIC devices managed by the OS. On a Zscaler system, there are NIC devices managed by the Zscaler instances and also by the base OS. |
| ZSCALER-PROCESSHEALTH-MIB.mib | This module describes health information for all watched processes in the Zscaler instance. |
| ZSCALER-PROCESSWATCHDOG-MIB.mib | This module describes the process watchdog information for each of the managed processes of a Zscaler instance (e.g., for an SME type of instance, the watched processes are sme, smavd, smavd2, smcdsc, and sctimer). |
| ZSCALER-ROLEHEALTH-MIB.mib | This module describes the health information for a Zscaler instance. This includes many of the OS level information for the instance such as CPU, memory, and also some instance specific information (e.g., current connections on SME). |
| ZSCALER-SWAPINFO-MIB.mib | This module describes the status of the swap devices present on the system. |
| ZSCALER-VSE-MIB | This module describes the health status of Virtual Service Edge connection to Zscaler Central Authority (CA) and Log and Reporting servers. |
| ZSCALER-ZSCALERNIC-MIB.mib | This module describes the NIC devices managed by the Zscaler instance. On a Zscaler system, there are NIC devices managed by the Zscaler instances and also by the base OS. |
[]To configure the SNMP admin user, you must log in to the Virtual Service Edge with software such as Xshell or Mobaxterm. In this example, Xshell is used.
The steps for configuring [NSS ](/unified/understanding-nanolog-streaming-service)are identical to the Virtual Service Edge example shown in this article.
- Enter the following command to log in to the Virtual Service Edge:
ssh zsroot@<Virtual Service Edge Management IP Address>
In this example, the Virtual Service Edge management IP address is 10.66.79.165.
[See image.](#virtual-service-edge-login)
- In the **SSH User Authentication **window, choose **Keyboard Interactive **and click **OK**.
[See image.](#keyboard-interactive-ssh-auth)
- In the window that appears, enter the **Password**, zsroot, and click **OK**.
[See image.](#ssh-auth)
- After you have logged in, change the user using the sudo su command,** **and enter the password zsroot.
[See image.](#sudo)
- Check if the Virtual Service Edge service is running using the vzen status command.
[See image.](#vzen-status)
For NSS, use the nss status command.
[See image.](#nss-status)
- Check if SNMP is running using the top command.
[See image.](#snmp-status)
- If the SNMP (snmpd) process is running, configure an SNMP admin user using the vzen snmp-admin-configure command.
Follow the prompts to configure the username, password, authentication type, and encryption type for the admin user.
[See image.](#snmp-admin-configuration)
[]![Screenshot of the command used to log in to the Zscaler VZEN](/downloads/zia/documentation-knowledgebase/analytics/snmp-mibs/about-the-zscaler-snmp-mibs/command_for_logging_into_vzen_screenshot.png)
[]![Screenshot of the Keyboard Interactive window](/downloads/zia/documentation-knowledgebase/analytics/snmp-mibs/about-the-zscaler-snmp-mibs/keyboard_interactive_window_screenshot.png)
[]![Screenshot of the SSH User Authentication window](/downloads/zia/documentation-knowledgebase/analytics/snmp-mibs/about-the-zscaler-snmp-mibs/ssh_user_authentication_window_screenshot.png)
[]![Screenshot of the command for changing the user](/downloads/zia/documentation-knowledgebase/analytics/snmp-mibs/about-the-zscaler-snmp-mibs/sudo_su_command_screenshot.png)
[]![Screenshot of the command for checking the status of the Zscaler VZEN](/downloads/zia/documentation-knowledgebase/analytics/snmp-mibs/about-the-zscaler-snmp-mibs/vzen_status_command_screenshot.png)
[]![Screenshot of the command for checking the status of the Zscaler NSS.](/downloads/NSS%20Status.png)
[]****![Screenshot of the command for checking if SNMP is running](/downloads/zia/documentation-knowledgebase/analytics/snmp-mibs/about-the-zscaler-snmp-mibs/top_command_screenshot.png)
****
[]![ Screenshot of the command for configuring an SNMP admin user](/downloads/zia/documentation-knowledgebase/analytics/snmp-mibs/about-the-zscaler-snmp-mibs/configuring_an_snmp_user_screenshot.png)
- [][Load the MIBs](#load-mibs)
- [View the MIBs](#view-mibs)
[]Load the downloaded MIBs into your SNMP monitoring tool.
[]Before viewing the MIBs, you need to add the SNMP admin user configured in [step 2](/zia/about-the-zscaler-snmp-mibs#configure-snmp-admin) to the SNMP monitoring tool. In this example, the **iReasoning MIB Browser** is used.
- Open the MIB browser, then go to **Tools **> **Options**.
[See image.](#mib-browser-tools-options)
- In the **Options** window, navigate to the **Agents **tab. Click **Add **to add the SNMP admin user.
[See image.](#add-snmp-agent)
The **Advanced Properties of SNMP Agents **window appears.
- In the **Advanced Properties of SNMP Agents **window:
- In the **Address** field, enter the Virtual Service Edge management IP address.
- For the **SNMP Version** field, select **3**. New fields appear after selecting **3**.
- **USM User**: Enter the username of the SNMP admin user
- **Security Level**: Select **auth, priv** for the security level
- Enter the password of the SNMP admin user in the **Auth Password** and **Privacy Password** fields.
[See image.](#configure-snmp-agent)
- Click **Ok** to save the SNMP admin user. The Virtual Service Edge management IP address and the SNMP admin user's credentials appear in the **Agents** tab.
[See image.](#view-configured-user)
- Exit the **Options** window. From the **MIB Tree**, open the folder containing the Zscaler MIBs by navigating to **iso.org.dod.internet** > **private** > **enterprises** > **zscaler**.
[See image.](#zscaler-mibs)
- Open the folder for the MIB for which you want to view the details. Right-click on the table icon, then click **Get Bulk**.
[See image.](#fetch-mib-table)
- From the **Results Table**, you can view the **OID**, **Value**, and **Type **of the MIB object. To view more details, double-click the entry from the **Results Table**. The details appear in the left column.
For example, for the **snmpTargetSpinLock **object:
- The **OID** is **.1.3.6.1.6.3.12.1.1.0**
- The **Value** is **0**
- The **Type **is **Integer**
[See image.](#more-object-details)
[]![ Screenshot of the MIB browser Tools menu](/downloads/zia/documentation-knowledgebase/analytics/snmp-mibs/about-the-zscaler-snmp-mibs/mib_browser_tool_menu_screenshot.png)
[]![ Screenshot of the MIB browser Options window](/downloads/zia/documentation-knowledgebase/analytics/snmp-mibs/about-the-zscaler-snmp-mibs/mib_browser_options_window_screenshot.png)
[]![Screenshot of the MIB browser Advanced Properties of SNMP Agents window](/downloads/zia/documentation-knowledgebase/analytics/snmp-mibs/about-the-zscaler-snmp-mibs/mib_browser_advanced_properties_of_snmp_agents_window_screenshot.png)
[]![Screenshot of the Agents tab of the Options window](/downloads/zia/documentation-knowledgebase/analytics/snmp-mibs/about-the-zscaler-snmp-mibs/mib_browser_options_agents_tab_screenshot.png)
[]![ Screenshot of the MIB Tree folder that contains the Zscaler MIBs](/downloads/zia/documentation-knowledgebase/analytics/snmp-mibs/about-the-zscaler-snmp-mibs/mib_tree_screenshot.png)
[]![Screenshot of Get Bulk option for Zscaler MIB](/downloads/zia/documentation-knowledgebase/analytics/snmp-mibs/about-the-zscaler-snmp-mibs/get_bulk_option_for_mib_screenshot.png)
![Screenshot of the Zscaler MIB details in the Result Table](/downloads/zia/documentation-knowledgebase/analytics/snmp-mibs/about-the-zscaler-snmp-mibs/mib_browser_result_table_screenshot.png)
[]****![ Screenshot of the Zscaler MIB details on the MIB browser](/downloads/zia/documentation-knowledgebase/analytics/snmp-mibs/about-the-zscaler-snmp-mibs/mib_details_screenshot.png)
****