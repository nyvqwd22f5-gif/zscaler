# Configuring LogRhythm to Forward Active Directory Event Logs
Source: https://help.zscaler.com/deception/configuring-logrythm-forward-active-directory-event-logs
PDF: https://help.zscaler.com/pdf/com/en/1531473.pdf

You can configure LogRhythm to filter event logs from the Active Directory (AD) domain controllers for decoy accounts or enumeration detection. You can forward these logs to the Zscaler Deception Admin Portal when adversary actions are detected.
Prerequisites
Make sure that the following prerequisites are met:
- Configure all AD servers to forward security logs to the LogRhythm server.
- If you have selected the Deception Admin Portal to receive logs, make sure that there is network connectivity from the LogRhythm server to the Deception Admin Portal on TCP port 443.
- If you have selected a Decoy Connector to receive logs, make sure that there is network connectivity from the LogRhythm server and the Decoy Connector’s management IP on TCP port 80.
Configuring LogRhythm to Forward AD Event Logs to the Zscaler Deception Admin Portal
To configure LogRhythm to forward logs to the Deception Admin Portal:
- [Step 1: Configure and Download the LogRhythm Trigger Script](#deception-logrythm-config-download-trigger-script)
- [Step 2: Extract the LogRhythm Trigger Script Files](#deception-logrythm-extract-folder-structure)
- [Step 3: Create the LogRhythm's SmartResponse Plugin File](#deception-logrythm-create-plugin)
- [Step 4: Create Advanced Intelligence (AI) Engine Rules for Event IDs](#deception-logrhrythm-creat-ai-engine-rule)
[]A trigger script sends logs from the LogRhythm server to the Deception Admin Portal. [Configure and download the LogRhythm trigger script](/deception/configuring-and-downloading-trigger-script) to forward AD event logs to the portal.
- []Copy the LogRhythm trigger script downloaded in Step 1 to the server running LogRhythm.
- Create a folder and extract the contents of the .zip file.
- Create sub-folders for each individual tar.gz file that is extracted.
![LogRythm trigger script folder structure](/downloads/deception/deceive/active-directory-decoys/configuring-logrythm-forward-active-directory-event-logs/zscaler-deception-logrythm-folder-structure.png)
- []Log in to the LogRhythm Client console.
- On the main toolbar, click **Deployment Manager**.
- On the **Tools** menu, go to **Administration** > **SmartResponse Plugin Manager**.
- In the **SmartResponse Plugin Manager **window, click **Create Plugin**.
- Browse to the folder containing the plugin configuration files (Powershell and Actions.xml).
-
Select the files, and click **Validate**.
The .lpi plugin file is created.
- Click **Actions** > **Import**.
- Browse and select the .lpi file that you created in Step 3.f, and then click **Open**.
- []On the main toolbar, click **Deployment Manager**.
- Click the **AI Engine** tab.
- Click the **Rules** tab, and then click the plus icon.
-
In the **Rule Block Types** pane, drag and drop the **Log Observed** rule block icon to the **Rule Block Designer** pane.
The **AI Engine Rule Block Wizard** page appears.
- Click the **Rule Blocks** tab at the bottom of the **AI Engine Rule Block Wizard** page.
-
Click the **Primary Criteria** tab, and click **New.**
The **Log Message Filter **window appears**.**
- Add a filter criterion with the following settings. To learn more, see the [LogRhythm documentation](https://docs.logrhythm.com/docs/enterprise/client-console-analyst-guide/filters-and-wizards/use-the-filter-editor/filtersprimary-criteria):
- **Field**: `Vendor Message ID`
- **Filter Mode**: `Filter In (Is)`
- **Filter Value**: `{Event ID}`
- Click **Add Item**.
- On the **Include Filters** tab, add a filter with the following settings to trigger an alarm when a specific user logs in. To learn more, see the [LogRhythm documentation](https://docs.logrhythm.com/docs/enterprise/client-console-analyst-guide/filters-and-wizards/use-the-filter-editor/filtersinclude-filter).
- **Field**: `User (Origin)`
- **Filter Mode**: `Filter In (Is)`
- **Filter Value**: `{decoy username or list}`
- Click **Add Item**.
- Click the **Log Source Criteria** tab, and select the AD domain controller's security logs as the log source's option. To learn more, see the [LogRhythm documentation](https://docs.logrhythm.com/docs/enterprise/client-console-analyst-guide/filters-and-wizards/use-the-filter-editor/filterslog-source-criteria).
- Click the **Group By** tab, and select the following fields (event IDs) to forward to the Deception Admin Portal. To learn more, see the[ LogRhythm documentation](https://docs.logrhythm.com/docs/enterprise/client-console-analyst-guide/filters-and-wizards/use-the-filter-editor/filtersgroup-by):
- `4625`
- `4648`
- `4768`
- `4769`
- `4771`
- `4776`
- Click the **Settings** tab at the bottom of the **AI Engine Rule Block Wizard** page, and enter the event name.
- Click the **Actions** tab at the bottom of the **AI Engine Rule Block Wizard** page:
- **Set Action**: Select **SmartResponse Plugin** from the drop-down menu.
- **Parameters:** Configure the following settings for each event ID:
- **Type**: `Alarm Field`
- **Value**: Enter the event name.
- In the **Execute SmartResponse Action From** section, select a Security Information and Event Management (SIEM) to launch the SmartResponse plugin.
-
Click **Save Action**.
The AI Engine rule is created.
- Right-click on the rule, and select **Actions** > **Enable **to enable the rule.
- Click **Restart AI Engine Servers **for the rule to take effect.
To test AD decoys, log in to a decoy AD user account. You can see events triggered on the LogRhythm server and Deception Admin Portal.
Event Field Mapping
The following tables map the XML version of the events (as viewed in the Event Viewer on Windows) to the fields parsed by the LogRhythm server. If the fields don't match, you might have to make changes in the actions.xml file for the corresponding SmartResponse plugin.
- [4625](#deception-logrhythm-even-mapping-4625)
- [4648](#deception-logrhythm-event-mapping-4648)
- [4768](#deception-logrhythm-event-mapping-4768)
- [4769](#deception-logrhythm-event-mapping-4769)
- [4771](#deception-logrhythm-event-mapping-4771)
- [4776](#deception-logrhythm-event-mapping-4776)
| **LogRhythm** | **PowerShell Parameter** | **Event Viewer** |
| ------------- | ------------------------ | ---------------- |
| Domain Origin | -SubjectDomainName | SubjectDomainName |
| User (Origin) | -TargetUserName | TargetUserName |
| Domain Origin | -TargetDomainName | TargetDomainName |
| Status | -Status | Status |
| Object Name | -SubStatus | SubStatus |
| Command | -LogonType | LogonType |
| Hostname (Origin) | -WorkstationName | WorkstationName |
| IP Address (Origin) | -IpAddress | IpAddress |
| TCP/UDP Port (Origin) | -IpPort | IpPort |
[]
| **LogRhythm** | **PowerShell Parameter** |
| ------------- | ------------------------ |
| User (Origin) | -SubjectUserName |
| Domain Origin | -SubjectDomainName |
| User (Impacted) | -TargetUserName |
| Domain Origin | -TargetDomainName |
| Hostname (Impacted) | -TargetServerName |
| IP Address (Origin) | -IpAddress |
| TCP/UDP Port (Origin) | -IpPort |
[]
| **LogRhythm** | **PowerShell Parameter** |
| ------------- | ------------------------ |
| User (Origin) | -TargetUserName |
| Hostname(impacted) | -Workstation |
| IP Address (Origin) | -IpAddress |
| Policy | -TicketOptions |
| Version | -TicketEncryptionType |
| Object | -PreAuthType |
| Subject | -Status |
[]
| **LogRhythm** | **PowerShell Parameter** |
| ------------- | ------------------------ |
| User (Origin) | -TargetUserName |
| Domain Origin | -TargetDomainName |
| Hostname (Impacted) | -ServiceName |
| Policy | -TicketOptions |
| Version | -TicketEncryptionType |
| IP Address (Origin) | -IpAddress |
| TCP/UDP Port (Origin) | -IpPort |
[]
| **LogRhythm** | **PowerShell Parameter** |
| ------------- | ------------------------ |
| User (Origin) | -TargetUserName |
| Group | -ServiceName |
| IP Address (Origin) | -IPAddress |
| TCP/UDP Port (Origin) | -IPPort |
[]
| **LogRhythm** | **PowerShell Parameter** |
| ------------- | ------------------------ |
| User (Origin) | -TargetUsername |
| Hostname (Origin) | -Workstation |
| Object Name | -Status |
[]