# Configuring a Service Connector
Source: https://help.zscaler.com/itdr/configuring-service-connector
PDF: https://help.zscaler.com/pdf/com/en/1531715.pdf

You can configure a Service Connector on your Windows or Linux system by downloading and running the Service Connector executables from the Zscaler ITDR Admin Portal.
Prerequisites
Make sure that before configuring a Service Connector, you must have:
- An always-on system or endpoint that can run the Service Connector executable.
- Network reachability from the server or endpoint to the ITDR Admin Portal.
- Network reachability from the system running the Service Connector or endpoint to the SIEM solution.
Configuring a Service Connector
Follow these steps to configure a Service Connector:
- [Step 1: Add a Service Connector](#itdr-add-siem-connector)
- [Step 2: Download and Run the Service Connector Executable](#itdr-download-run-siem-connector)
- []Go to **Orchestrate** > **Service Connectors**.
-
Click **Add Connector**.
[See image.](#itdr-add-siem-connector-button)
- In the **Service Connector Details** window:
- Under **General**, enter the **Name** of the Service Connector.
-
If you plan to forward events from an IBM QRadar SIEM server to the ITDR Admin Portal Service Connector, under **Syslog Receiver**:
- Select a syslog **Source Type** from the drop-down menu.
- Add the IP addresses of SIEM servers to the **Source Allowed IPs** list.
[See image.](#itdr-config-siem-connector-details)
-
Click **Save**.
API tokens are generated.
-
In the **API Token generated** window, click the **Windows** or **Linux **tab, and copy the API token.
[See image.](#itdr-copy-api-token)
For security purposes, the token is not be displayed again after closing the window.
-
Click **Close**.
The Service Connector is added to the **Service Connectors** table.
[See image.](#itdr-siem-connector-added)
- []On the **Service Connectors** page, click **Download Connector**.
-
Select a Service Connector executable from the drop-down menu.
[See image.](#itdr-download-siem-executables)
The executable is downloaded to your local system.
- In the command prompt, run the following command to configure the Service Connector on your local system:
- [Windows](#itdr-windows-commands)
- [Linux](#itdr-deception-linux-commands)
- []Without proxy:
SiemConnector-windows.exe --host=<ITDR Admin Portal instance> --api=<API Token> -v
- With proxy:
./SiemConnector-windows.exe --host=<ITDR Admin Portal instance> --api=<API Token> --proxy=http://<username:password@proxy-server:proxy-port>
- []Without proxy:
SiemConnector-linux --host=<ITDR Admin Portal instance> --api=<API Token> -v
- With proxy:
./SiemConnector-linux --host=<ITDR Admin Portal instance> --api=<API Token> --proxy=http://<username:password@proxy-server:proxy-port>
You can configure a service or daemon to start the Service Connector at boot and keep the Service Connector running.
After you configure a Service Connector, you can integrate the ITDR Admin Portal with a supported SIEM solution.
[]![Add SIEM Connector option](/downloads/itdr/orchestrate/siem-integrations/configuring-service-connector/itdr-add-siem-connector-option.png)
[]![Configure SIEM Connector details](/downloads/itdr/orchestrate/siem-integrations/configuring-service-connector/itdr-add-siem-connector-details.png)
[]![Copy the API token for the Service Connector](/downloads/itdr/orchestrate/siem-integrations/configuring-service-connector/itdr-add-siem-connector-api-token.png)
[]![Service Connector added](/downloads/itdr/orchestrate/siem-integrations/configuring-service-connector/itdr-siem-connector-added.png)
[]![Download Service Connector Executables](/downloads/itdr/orchestrate/siem-integrations/configuring-service-connector/itdr-download-service-connector-executables.png)