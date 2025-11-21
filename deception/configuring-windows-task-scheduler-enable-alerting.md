# Configuring Windows Task Scheduler to Enable Alerting
Source: https://help.zscaler.com/deception/configuring-windows-task-scheduler-enable-alerting
PDF: https://help.zscaler.com/pdf/com/en/1531337.pdf

After you download the trigger script from the Zscaler Deception Admin Portal, you can import it to the Windows Task Scheduler to enable alerts for the Active Directory (AD) decoys.
Prerequisites
Make sure that the following prerequisites are met:
- You must have admin access to the AD domain controller to import the trigger script.
- All AD domain controllers must have access to the selected Decoy Connector on port 80 or the Deception Admin Portal on port 443.
Configuring Windows Task Scheduler to Enable Alerting
To configure the Task Scheduler:
-
[Download the trigger script](/deception/configuring-and-downloading-trigger-script) from the Deception Admin Portal.
The Windows system can block the trigger script, so you must unblock the script before importing it to the Task Scheduler.
- To unblock the trigger script, right-click on the script (.xml file) and select **Properties**.
-
In the **Properties** window on the **General** tab, select **Unblock** and click **OK**.
[See image.](#deception-task-sche-unblock)
- Press the `Windows key+R` on your system.
- In the **Run** window, enter `taskschd.msc`, and then click **OK** to open the Task Scheduler.
- In the left-side navigation, go to **Task Scheduler Library**.
-
In the **Actions** pane, click **Import Task**.
[See image.](#deception-task-sched-import-task)
- Browse to select the trigger script (.xml file), then click **Open**.
-
In the **Create Task** window, select the latest available version of Windows from the **Configure for** drop-down menu for which you want to import the scheduled task, and click **OK**.
[See image.](#deception-task-sche-config-window-version)
The trigger script is imported to the Task Scheduler.
[See image.](#deception-task-sche-imported)
You must import the trigger script into every domain controller in the AD domain.
[]![Unblock the trigger script in the Windows system](/downloads/deception/deceive/active-directory-decoys/configuring-windows-task-scheduler-enable-alerting/zscaler-deception-task-scheduler-unblock-script.png)
[]![Import a task in the Windows Task Scheduler](/downloads/deception/deceive/active-directory-decoys/configuring-windows-task-scheduler-enable-alerting/zscaler-deception-task-scheduler-actions-import-task.png?1655351589)
[]![Create a task in the Windows Task Scheduler](/downloads/deception/deceive/active-directory-decoys/configuring-windows-task-scheduler-enable-alerting/zscaler-deception-task-scheduler-create-task.png?1655352663)
[]![Task imported successfully into the Windows Task Scheduler](/downloads/deception/deceive/active-directory-decoys/configuring-windows-task-scheduler-enable-alerting/zscaler-deception-task-scheduler-task-imported.png?1655352904)