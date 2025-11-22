# Modifying a Zscaler Incident Receiver
Source: https://help.zscaler.com/unified/modifying-zscaler-incident-receiver
PDF: https://help.zscaler.com/pdf/com/en/1493361.pdf

To edit or delete a Zscaler Incident Receiver:
- Go to **Policies** > **Data Protection** > **Common Resources** > **DLP Incident Receiver**.
- Click the **Zscaler Incident Receiver** tab.
- Locate the Zscaler Incident Receiver in the table and click **Edit**.
The **Edit Incident Receiver** window appears.
- In the **Edit Incident Receiver** window:
- Change the **Incident Receiver Name**.
- Change the **Status** to **Enabled** or **Disabled**.
- For **IP Address**, change the incident receiver URI. If you change the URI, make sure you update the incident receiver virtual machine (VM). To learn more, see [Configuring the Zscaler Incident Receiver](/unified/configuring-zscaler-incident-receiver-premises-vms).
- Download or regenerate the **Certificate**. If you regenerate the certificate, make sure you update the incident receiver VM with the new file. To learn more, see [Configuring the Zscaler Incident Receiver](/unified/configuring-zscaler-incident-receiver-premises-vms).
If you want to remove the incident receiver, click **Delete**.
- Click **Save** and activate the change.
![The Edit Zscaler Incident Receiver window](/downloads/zia/policies/data-loss-prevention/modifying-zscaler-incident-receiver/ZIA-Edit-Incident-Receiver-window.png)