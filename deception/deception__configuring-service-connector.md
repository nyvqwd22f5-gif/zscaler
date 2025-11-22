# Configuring a Service Connector
Source: https://help.zscaler.com/deception/configuring-service-connector
PDF: https://help.zscaler.com/pdf/com/en/1531398.pdf

You can configure a Service Connector on your Windows or Linux system by downloading and running the Service Connector executables from the Zscaler Deception Admin Portal.
Prerequisites
Before you configure a Service Connector, make sure that you have:
- An always-on system or endpoint that can run the Service Connector executable.
- Network reachability from the server or endpoint to the Deception Admin Portal.
- Network reachability from the system running the Service Connector or endpoint to the SIEM solution.
Configuring a Service Connector
Follow these steps to configure a Service Connector:
- [Step 1: Add a Service Connector](#add-siem-connector)
- [Step 2: Download and Run the Service Connector Executable](#download-run-siem-connector)
- []Go to **Orchestrate** > **Service Connectors**.
-
Click **Add Connector**.
[See image.](#add-siem-connector-button)
- In the **Service Connector Details** window:
- Under **General**, enter the **Name** of the Service Connector.
- If you plan to forward events from an IBM QRadar SIEM server to the Deception Service Connector, under **Syslog Receiver**:
- Select a syslog **Source Type** from the drop-down menu.
-
Add the IP addresses of SIEM servers to the **Source Allowed IPs** list.
[See image.](#config-siem-connector)
-
Click **Save**.
API tokens are generated.
-
In the **API Token generated** window, click the **Windows** or **Linux **tab, and copy the API token.
[See image.](#copy-api-token)
For security purposes, the token is not displayed again after closing the window.
-
Click **Close**.
The Service Connector is added to the **Service Connectors** table.
[See image.](#siem-connector-added)
- []On the **Service Connectors** page, click **Download Connector**.
-
Select a Service Connector executable from the drop-down menu.
[See image.](#download-siem-executables)
The executable is downloaded to your local system.
- In the command prompt, run the following command to configure the Service Connector on your local system:
- [Windows](#windows-commands)
- [Linux](#deception-linux-commands)
- []Without proxy:
SiemConnector-windows.exe --host=<Deception Admin Portal instance> --api=<API Token> -v
- With proxy:
./SiemConnector-windows.exe --host=<Deception Admin Portal instance> --api=<API Token> --proxy=http://<username:password@proxy-server:proxy-port>
- []Without proxy:
SiemConnector-linux --host=<Deception Admin Portal instance> --api=<API Token> -v
- With proxy:
./SiemConnector-linux --host=<Deception Admin Portal instance> --api=<API Token> --proxy=http://<username:password@proxy-server:proxy-port>
You can configure a service or daemon to start the Service Connector at boot and keep the Service Connector running.
After you configure a Service Connector, you can integrate the Deception with a [supported SIEM solution](/deception/about-siem-integrations).
[]![Add Service Connector option ](/downloads/deception/orchestrate/siem-integrations/configuring-service-connector/zscaler-deception-add-connector-option.png)
[]![Configure a Service Connector](/downloads/deception/orchestrate/siem-integrations/configuring-service-connector/zscaler-deception-service-connector-details-1.png)
[]![Copy the API token](/downloads/deception/orchestrate/siem-integrations/configuring-service-connector/zscaler-deception-siem-connector-copy-api-token-3.png)
[]![Service Connected added](/downloads/deception/orchestrate/siem-integrations/configuring-service-connector/zscaler-deception-service-connector-added-1.png)
[]![Download Service Connector Windows or Linux executables](/downloads/deception/orchestrate/siem-integrations/configuring-service-connector/zscaler-deception-download-service-connector-executables-1.png)