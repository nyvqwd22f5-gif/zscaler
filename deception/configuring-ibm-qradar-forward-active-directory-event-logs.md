# Configuring IBM QRadar to Forward Active Directory Event Logs
Source: https://help.zscaler.com/deception/configuring-ibm-qradar-forward-active-directory-event-logs
PDF: https://help.zscaler.com/pdf/com/en/1531339.pdf

You can configure the IBM QRadar SIEM tool to filter event logs from an Active Directory (AD) domain controller for decoy accounts or enumeration detection. You can forward the event logs to the Zscaler Deception Admin Portal via a Decoy Connector when an adversary's actions are detected.
Prerequisites
Make sure that the following prerequisites are met:
- Configure the AD servers to forward logs to QRadar.
- Configure a Decoy Connector as a syslog receiver with an IP address of the QRadar server in its allowed IP list.
- Make sure that there is network connectivity between the QRadar server and the Decoy Connector’s management IP on TCP port 9514.
Configuring QRadar to Forward Logs to the Zscaler Deception Admin Portal
To configure QRadar to forward logs to the Deception Admin Portal:
- [Step 1: Configure a Decoy Connector as a Syslog Receiver](#configure-decoy-connector-syslog-server)
- [Step 2: Add a Forwarding Destination](#add-forwarding-destination)
- [Step 3: Create an Event Rule](#create-event-rule)
- [Step 4: Add Tests to the Event Rule](#add-tests-event-rule)
- [Step 5: Specify Rule Response](#specify-rule-response)
[]Before you configure QRadar to forward logs, you must configure a Decoy Connector as a syslog receiver.
- Go to **Orchestrate** > **SIEM** > **Connectors**.
-
Select a Decoy Connector that you want to use as a syslog receiver to collect the AD event logs from the QRadar server, and then click the **Edit **icon.
[See image.](#config-dc-syslog-receiver-img)
-
In the **SIEM Connector Details** window, under **Syslog Receiver**:
- **Source Type**: Select **IBM QRadar**.
- **Source Allowed IPs**: Enter the QRadar server's IP address.
[See image.](#config-siem-connector-details)
- Click **Save**.
- []Open an IBM QRadar SIEM console.
-
On the navigation menu, click **Admin**.
[See image.](#navigate-admin-qradar)
-
On the **System Configuration** page, click **Forwarding Destinations**.
[See image.](#navigate-forward-destination-qradar)
-
On the toolbar, click **Add**.
[See image.](#add-forward-destination-qradar)
-
In the **Forwarding Destinations Properties** window:
- **Name**: Enter a name for the forwarding instance.
- **Destination Address**: Enter the Decoy Connector’s management IP address, which is configured as a syslog receiver.
- **Event Format**: Select **Payload** from the drop-down menu.
- **Destination Port**: Enter `9514`.
- **Protocol**: Select **TCP** from the drop-down menu.
- **Prefix a Syslog header if it is missing or invalid**: Select the checkbox.
[See image.](#forward-destination-properties-qradar)
-
Click **Save**.
The forward destination entry is added to the table.
[See image.](#forward-destination-added-qradar)
- []On the navigation menu, go to **Offenses** > **Rules**.
-
Click **Actions** > **New Event Rule**.
[See image.](#add-event-rule-qradar)
- On the **Rule Wizard** page, click **Next** to select the source from which you want the rule to be generated.
- Under **Choose the source from which you want this rule to generate,** select **Events**.
-
Click **Next**.
[See image.](#select-source-event-rule-qradar)
-
Under the **Rule** section, enter a rule name in **Apply**. For example, enter "`Decoy account usage is detected"`. Make sure quotation marks are included around the rule name.
[See image.](#apply-event-rule-qradar)
- []Add a QID filter.
- On the **Rule Wizard** page, click the **Add** icon next to **when the event QID is one of the following QIDs**.
-
Under the **Rule** section, click the **QIDs** link.
[See image.](#apply-qid-qradar)
-
Browse or search for the following QIDs, select a QID, and click **Add**. You can add only one QID at a time.
- `5000937`
- `5000475`
- `5000945`
- `5000940`
- `5000938`
- `5000581`
- `5000589`
- `5000584`
- `5000835`
[See image.](#search-add-qids-qradar)
-
After the QIDs are added, click **Submit**.
[See image.](#submit-qids-qradar)
- Add a user filter.
- On the **Rule Wizard** page, click the **Add** icon next to **when the event matches this search filter**.
-
Under the **Rule** section, click the **this search filter** link.
[See image.](#apply-search-filter)
- Select **Username** from the drop-down menu.
- Select **Equals any of** from the drop-down menu.
- Enter the decoy username and click the **Plus** icon to add the decoy username to the list.
-
Click **Add** to add the filter.
[See image.](#add-user-filter)
-
Verify that all the decoy users are added to the filter, and then click **Submit**.
[See image.](#submit-user-filter)
-
Click **Next** to go to the **Rule Response **section.
[See image.](#navigate-rule-wizard)
- []Under the **Rule Response** section, select the **Dispatch New Event** checkbox.
- Enter an **Event Name**.
- Enter the **Event Description**.
- Select the **Ensure the dispatched event is part of an offense** checkbox.
- Under **Offense Naming**, select **This information should set or replace the name of associated offense(s)**.
-
Select the **Send to Forwarding Destinations** checkbox, and then select the Decoy Connector’s management IP that was configured as a forwarding destination from the list of destinations.
[See image.](#specify-rule-response-qradar)
- Under **Enable Rule**, select the **Enable this rule if you want it to begin watching events right away** checkbox.
-
Click **Next**, and then click **Finish**.
[See image.](#enable-rule-qradar)
[]![Configure a Decoy Connector as a syslog receiver](/downloads/deception/deceive/active-directory-decoys/configuring-ibm-qradar-forward-active-directory-event-logs/zscaler-deception-configure-decoy-connector-as-receiver.png?1655356528)
[]![Configure SIEM Connector details](/downloads/deception/deceive/active-directory-decoys/configuring-ibm-qradar-forward-active-directory-event-logs/zscaler-deception-configure-qradar-SIEM-details.png)
[]![Navigate to the Admin page in the QRadar console](/downloads/deception/deceive/active-directory-decoys/configuring-ibm-qradar-forward-active-directory-event-logs/zscaler-deception-qradar-navigate-admin.png)
[]![Navigate to Forward Destination in QRadar](/downloads/deception/deceive/active-directory-decoys/configuring-ibm-qradar-forward-active-directory-event-logs/zscaler-deception-qradar-forward-destination.png)
[]![Add a forward destination in QRadar](/downloads/deception/deceive/active-directory-decoys/configuring-ibm-qradar-forward-active-directory-event-logs/zscaler-deception-qradar-forward-destination-add.png)
[]![Configure forward destination properties in QRadar](/downloads/deception/deceive/active-directory-decoys/configuring-ibm-qradar-forward-active-directory-event-logs/zscaler-deception-qradar-forward-destination-properties.png?1655803134)
[]![Forward destination added in QRadar](/downloads/deception/deceive/active-directory-decoys/configuring-ibm-qradar-forward-active-directory-event-logs/zscaler-deception-qradar-forward-destination-added.png)
[]![Add a new event rule in QRadar](/downloads/deception/deceive/active-directory-decoys/configuring-ibm-qradar-forward-active-directory-event-logs/zscaler-deception-add-new-event-qradar.png)
[]![Select the event source for the rule in QRadar](/downloads/deception/deceive/active-directory-decoys/configuring-ibm-qradar-forward-active-directory-event-logs/zscaler-deception-choose-event-source-qradar.png)
[]![Apply the event rule in QRadar](/downloads/deception/deceive/active-directory-decoys/configuring-ibm-qradar-forward-active-directory-event-logs/zscaler-deception-apply-rule-qradar.png)
[]![Apply QIDs in QRadar](/downloads/deception/deceive/active-directory-decoys/configuring-ibm-qradar-forward-active-directory-event-logs/zscaler-deception-apply-qid-qradar.png)
[]![Search and add QIDs in QRadar](/downloads/deception/deceive/active-directory-decoys/configuring-ibm-qradar-forward-active-directory-event-logs/zscaler-deception-add-qids-qradar.png)
[]![Submit QIDs in QRadar](/downloads/deception/deceive/active-directory-decoys/configuring-ibm-qradar-forward-active-directory-event-logs/zscaler-deception-submit-qids-qradar.png)
[]![Apply search filter](/downloads/deception/deceive/active-directory-decoys/configuring-ibm-qradar-forward-active-directory-event-logs/zscaler-deception-apply-search-filter-qradar.png)
[]![Add user filter QRadar](/downloads/deception/deceive/active-directory-decoys/configuring-ibm-qradar-forward-active-directory-event-logs/zscaler-deception-add-filter-qradar.png)
[]![Submit user filter in QRadar](/downloads/deception/deceive/active-directory-decoys/configuring-ibm-qradar-forward-active-directory-event-logs/zscaler-deception-submit-filter-qradar.png)
[]![Navigate to Rule Wizard](/downloads/deception/deceive/active-directory-decoys/configuring-ibm-qradar-forward-active-directory-event-logs/zscaler-deception-navigate-rule-response-qradar.png)
[]![Specify rule response in QRadar](/downloads/deception/deceive/active-directory-decoys/configuring-ibm-qradar-forward-active-directory-event-logs/zscaler-deception-specify-rule-response-qradar.png)
[]![Enable response rule in QRadar](/downloads/deception/deceive/active-directory-decoys/configuring-ibm-qradar-forward-active-directory-event-logs/zscaler-deception-enable-response-rule-qradar.png)