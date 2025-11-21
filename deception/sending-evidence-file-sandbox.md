# Sending an Evidence File to a Sandbox
Source: https://help.zscaler.com/deception/sending-evidence-file-sandbox
PDF: https://help.zscaler.com/pdf/com/en/1531393.pdf

Zscaler Deception is integrated with Zscaler Sandbox. This allows you to send evidence files to the Sandbox, and download an analysis report to enrich incident investigations and response. To learn more, see [About Sandbox](/zia/about-sandbox).
Only Indicators of Compromise (IOC) files can be sent to the sandbox.
In addition to the Sandbox integration, Deception also supports the following third-party sandboxes:
- Palo Alto Networks WildFire
- Hybrid Analysis:
- Linux (Ubuntu 20.04, 64-bit)
- Windows 7 64-bit
- Windows 7 32-bit (HWP Support)
- Windows 7 32-bit
- Joe Sandbox
- Windows 10 64-bit
- Windows 10 64-bit (Native)
- Windows 7 64-bit
- Linux (Ubuntu 16.04, 64-bit)
- Linux (Ubuntu 20.04, 64-bit)
- Mac (Mojave)
- CrowdStrike Falcon X:
- Linux (Ubuntu 16.04, 64-bit)
- Windows 7 64-bit
- Windows 7 32-bit
- Windows 10 64-bit
- VirusTotal
Before sending an evidence file to a third-party sandbox, you must configure the sandboxes for enrichment integration. To learn more, see [About Enrichment Integrations](/deception/about-enrichment-integration).
To send an evidence file to a sandbox:
-
On the **Investigate** page, click the **Zscaler Deception Admin Portal** or **Decoy Connector** icon on the alert graph.
[See image.](#alert-graph-dashboard)
-
When the details pane appears, click **View Extended Details**.
[See image.](#view-extended-details-button-details-pane)
- Click the **Evidence** tab.
-
Locate the IOC evidence file that you want to analyze using a sandbox solution, and click the **Send to Sandbox** icon.
You can use the **Type** drop-down menu, and select **IOC** to list only the IOC type evidence files.
[See image.](#ioc-type-drop-down)
[See image.](#send-sandbox-icon)
-
In the **Send to Sandbox** window, select a sandbox option.
[See image.](#select-sandbox)
- Click **Send**.
-
Click **OK** in the confirmation window.
The evidence file is submitted to the sandbox.
Submitting an evidence file can take a few minutes depending on the file type and size.
After you send the evidence file to a sandbox, you can [download the report](/deception/downloading-sandbox-report) for analysis.
[]![Alert graph on the Investigate dashboard](/downloads/deception/investigate/sending-evidence-file-sandbox/zscaler-deception-investigate-alert-graph-sandbox.png)
[]![View Extended Details button on the details pane](/downloads/deception/investigate/sending-evidence-file-sandbox/zscaler-deception-view-extended-details-sandbox.png?1661495513)
[]![Send to Sandbox option on the Evidence page](/downloads/deception/investigate/sending-evidence-file-sandbox/Evidence%20Report.jpg)
[]![A screenshot highlighting the option to select the IOC type evidence files](/downloads/deception/investigate/accessing-extended-details/evidence/sending-evidence-file-sandbox/zscaler-deception-drop-down-tupe-ioc.png)
[]![Selecting a sandbox to send the evidence file](/downloads/deception/investigate/accessing-extended-details/evidence/sending-evidence-file-sandbox/Zscaler-deception-evidence-file-sandbox-option.png)