# Configuring and Downloading a Trigger Script
Source: https://help.zscaler.com/deception/configuring-and-downloading-trigger-script
PDF: https://help.zscaler.com/pdf/com/en/1531333.pdf

A trigger script runs on either an Active Directory (AD) domain controller or security information and event management (SIEM) system when it detects any interaction with an AD decoy. A trigger script sends logs from either a domain controller or a supported SIEM tool to the Zscaler Deception Admin Portal. You can configure a trigger script to customize how to forward AD event logs to the portal and download the script based on your requirements.
The Deception Admin Portal supports the following trigger sources from which the AD event logs are sent to the portal:
- Domain controller (Task scheduler)
- Splunk
- IBM QRadar
- LogRhythm
- Azure Sentinel
To configure and download a trigger script:
- Go to **Deceive** > **Active Directory Decoys** > **Triggers**.
-
Under **Download AD Trigger Scripts**:
- **Trigger Source**: Select a trigger source from the drop-down menu. You can select either a domain controller (via Task Scheduler) or a SIEM that you have deployed in your environment.
- **Domain**: Select a domain from the drop-down menu for which you want to generate the trigger script.
- **Alert Receiver**: Select a receiver from the drop-down menu to use as an endpoint for the Deception Admin Portal to receive alerts from the trigger source.
- **Attack Use Case**: Select a use case to trigger alerts from the drop-down menu. You can select to trigger alerts when AD decoy user accounts are accessed, or when enumeration attempts across AD decoy user or computer objects are detected.
[See image.](#deception-ad-trigger-script-config)
-
Click **Download Alert Configuration Files**.
A file containing trigger details is downloaded to your system.
You can use the trigger script to configure either your AD domain controllers or the SIEM that you have selected to forward AD event logs to the Deception Admin Portal.
You can configure:
- [Windows Task Scheduler to enable alerting](/deception/configuring-windows-task-scheduler-enable-alerting).
- [Splunk to forward AD event logs](/deception/configuring-splunk-forward-active-directory-event-logs).
- [QRadar to forward AD event logs](/deception/configuring-ibm-qradar-forward-active-directory-event-logs).
[]![Configure ad download trigger scripts](/downloads/deception/deceive/active-directory-decoys/configuring-and-downloading-trigger-script/zscaler-deception-ad-decoys-config-trigger-scripts-1.png)