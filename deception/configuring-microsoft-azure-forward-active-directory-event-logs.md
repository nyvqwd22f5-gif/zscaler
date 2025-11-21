# Configuring Microsoft Azure Sentinel to Forward Active Directory Event Logs
Source: https://help.zscaler.com/deception/configuring-microsoft-azure-forward-active-directory-event-logs
PDF: https://help.zscaler.com/pdf/com/en/1531474.pdf

You can configure Microsoft Azure Sentinel to filter event logs from the Active Directory (AD) domain controllers for decoy accounts or enumeration detection. You can forward these logs to the Zscaler Deception Admin Portal when adversary actions are detected.
Prerequisites
Make sure the following prerequisites are met:
- Configure all AD servers to forward security logs to Azure Sentinel.
- There is network connectivity from the Azure Sentinel instance to the Deception Admin Portal on TCP port 443.
Configuring Microsoft Azure Sentinel to Forward AD Event Logs
Follow these steps to configure Azure Sentinel to forward logs to the Deception Admin Portal:
- [Step 1: Configure and Download the Azure Sentinel Trigger Script](#deception-azure-ad-trigger-download-trigger-script)
- [Step 2: Configure Azure Sentinel to Forward Logs to the Deception Admin Portal](#deception-azure-ad-trigger-config-forward-logs)
[]A trigger script sends logs from Azure Sentinel to the Deception Admin Portal. To download the Azure Sentinel trigger scripts, see [Configuring and Downloading a Trigger Script](/deception/configuring-and-downloading-trigger-script).
- []Create a new logic app in the same resource group as the log analytics workspace. To learn more, refer to the [Microsoft documentation](https://learn.microsoft.com/en-us/azure/logic-apps/).
-
In the **Logic Apps Designer**, click **Blank Logic App**.
[See image.](#deception-azure-ad-trigger-script-blank-logic-app)
-
In the **Add a trigger** window, go to **All** > **Schedule** > **Triggers **>** Sliding Window**.
[See image.](#deception-azure-trigger-script-sliding-window)
-
In the **Sliding Window **window, on the **Parameters **tab, configure the window for 1 minute.
[See image.](#deception-azure-ad-trigger-config-parameter)
-
In the **Add an action** window, go to **All** > **Azure Monitor Logs **> **Actions** > **Run query and list results**.
[See image.](#deception-azure-ad-trigger-run-query-results-action)
- In the **Azure Monitor Logs** window, under **Tenant**, select the tenant with your Azure log analytics workspace and sign in to create a connection to Azure monitor logs.
- In the **Run query and list results** window:
- Select the same **Subscription**, **Resource Group**, and **Resource Type** as your log analytics workspace on Azure Sentinel.
- Enter the **Resource Name**.
-
In **Query**, copy the `SecurityEvent` code from the [trigger script](#deception-azure-ad-trigger-download-trigger-script) you downloaded.
The downloaded trigger script for Azure Sentinel has a different `SecurityEvent` code depending on the attack use case (Decoy User Accounts or Enumeration Detection) that you selected and the domain controller configuration.
-
For **Time Range**, enter `"Last hour"`.
[See image.](#deception-azure-ad-trigger-config-run-query)
- Click **New Step**.
-
Click **Condition Control**.
[See image.](#deception-azure-ad-trigger-add-control-condition)
- Under **Condition**,** **build your condition:
- Click **Choose a value**.
-
On the **Expression** tab, select **length(collection)**.
[See image.](#deception-azure-ad-trigger-build-condition-expression)
-
On the **Dynamic content** tab, select **value** under **Run query and list results**.
The **value** field is added within the **length** expression.
[See image.](#deception-azure-ad-trigger-dynamic-content-condition)
- Click **OK**.
-
Select **is greater than** from the drop-down menu, and enter `0`.
[See image.](#deception-azure-ad-trigger-is-great-than-condition)
-
Under **True**, click **Add an action**, and then select **HTTP**.
[See image.](#deception-azure-ad-trigger-true-operation-http)
-
In the **HTTP** window:
- Under **Method**, select **POST** from the drop-down menu.
-
Under **URI**, copy the URI from the [trigger script](#deception-azure-ad-trigger-download-trigger-script) you downloaded.
The downloaded trigger script for Azure Sentinel has a different URI depending on the attack use case (Decoy User Accounts or Enumeration Detection) that you selected and the domain controller configuration.
-
Under **Body**, select **Body** from **Run query and list results**.
[See image.](#deception-azure-ad-trigger-config-http)
To avoid data trimming, go to **HTTP** > **Settings** > **Networking** > **Content Transfer** and disable **Allow chunking**.
[See image.](#deception-ad-azure-allow-chunking)
-
Click **Save** to save the logic app.
[See image.](#deception-azure-ad-trigger-save-logic-app)
To test AD decoys, log in to a decoy AD user account. You can see events triggered in Azure Sentinel and the Deception Admin Portal.
[]![Create a blank logic app in Azure](/downloads/deception/deceive/active-directory-decoys/configuring-microsoft-azure-forward-active-directory-event-logs/zscaler-deception-azure-trigger-script-blank-logic-app.png)
[]![Add a sliding window trigger in Azure](/downloads/deception/deceive/active-directory-decoys/configuring-microsoft-azure-forward-active-directory-event-logs/zscaler-deception-azure-trigger-script-sliding-window-trigger.png?1681126773)
[]![Configure the sliding window parameter](/downloads/deception/deceive/active-directory-decoys/configuring-microsoft-azure-forward-active-directory-event-logs/zscaler-deception-azure-trigger-script-sliding-window-trigger-parameter.png)
[]![Add Azure Monitor Logs action](/downloads/deception/deceive/active-directory-decoys/configuring-microsoft-azure-forward-active-directory-event-logs/zscaler-deception-azure-trigger-script-logic-app-action.png)
[]![Configure run query and list results in Azure](/downloads/deception/deceive/active-directory-decoys/configuring-microsoft-azure-forward-active-directory-event-logs/zscaler-deception-azure-trigger-script-run-query-list-1.png)
[]![Add a control condition](/downloads/deception/deceive/active-directory-decoys/configuring-microsoft-azure-forward-active-directory-event-logs/zscaler-deception-azure-trigger-script-add-condition-1.png)
[]![Configure the expression for a condition in Azure](/downloads/deception/deceive/active-directory-decoys/configuring-microsoft-azure-forward-active-directory-event-logs/zscaler-deception-azure-trigger-script-build-condition-expression.png)
[]![Configure dynamic content ](/downloads/deception/deceive/active-directory-decoys/configuring-microsoft-azure-forward-active-directory-event-logs/zscaler-deception-azure-trigger-script-add-condition-dynamic-content_2.png)
[]![Select values for a condition in Azure](/downloads/deception/deceive/active-directory-decoys/configuring-microsoft-azure-forward-active-directory-event-logs/zscaler-deception-azure-trigger-script-is-greater-than.png)
[]![Configure the True path for the condition in Azure](/downloads/deception/deceive/active-directory-decoys/configuring-microsoft-azure-forward-active-directory-event-logs/zscaler-deception-azure-trigger-script-select-true-path.png)
[]![Configure HTTP operation in Azure](/downloads/deception/deceive/active-directory-decoys/configuring-microsoft-azure-forward-active-directory-event-logs/zscaler-deception-azure-trigger-script-config-http-1.png)
[]![Disable the Allow chunking toggle](/downloads/deception/deceive/active-directory-decoys/configuring-microsoft-azure-forward-active-directory-event-logs/zscaler-deception-ad-logs-azure-allow-chunking.png)
[]![Save the logic app in Azure](/downloads/deception/deceive/active-directory-decoys/configuring-microsoft-azure-forward-active-directory-event-logs/zscaler-deception-azure-trigger-script-save-logic-app.png)