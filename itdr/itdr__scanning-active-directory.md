# Scanning an Active Directory
Source: https://help.zscaler.com/itdr/scanning-active-directory
PDF: https://help.zscaler.com/pdf/com/en/1531621.pdf

[Watch a video on Scanning an Active Directory.](https://fast.wistia.net/embed/iframe/1uidumi112)
You can add an Active Directory (AD) domain and assign a [Windows endpoint agent](/itdr/about-endpoint-settings) to scan the AD domain for identity misconfigurations and vulnerabilities. You can also schedule the scan frequency.
To scan an AD domain:
- Go to **ITDR** > **Manage** > **Active Directory Posture**.
-
Click **Set up new scan**.
[See image.](#deception-itdr-scan-ad-domain)
-
Select an AD domain from the drop-down menu, and click **Next**.
[See image.](#deception-add-ad-domain-to-scan)
The drop-down menu only lists the domains where the endpoint agent is installed. If the required domain is not listed, install a endpoint agent on one of the machines joined to the required domain.
-
Select a Windows endpoint agent from the drop-down menu, and click **Next**. The menu lists only the active agents that belong to the specified domain.
[See image.](#itdr-add-landmine-agent)
-
Select a scan frequency (**Daily**, **Weekly**, **Monthly**, or **Quarterly**) from the drop-down menu, and click **Next**.
[See image.](#deception-scan-ad-frequency)
-
Select a scan time.
[See image.](#deception-scan-ad-domain-time)
The scan only happens during the scheduled time using your browser's time zone setting. If the endpoint agent is available, the scan might be delayed by up to 10 minutes. If the agent doesn't connect within an hour after the scheduled scan time, the AD domain is not scanned until the next selected time period.
-
Click **Finish Set Up**.
The AD domain is added for scanning. It is scanned according to the scheduled frequency and time. You can [run an on-demand scan](/itdr/triggering-demand-scan).
After the AD domain is scanned for vulnerabilities, you can view the results on the [Active Directory Posture](/itdr/about-active-directory-posture-dashboard) dashboard.
[]![Configure an AD scan](/downloads/itdr/active-directory-posture/scanning-active-directory/itdr-start-new-scan-button.png)
[]![Add an AD domain to scan](/downloads/deception/identity/scan-agents/scanning-active-directory/zscaler-deception-scan-agents-add-ad-domain-4.png)
[]![Select an agent to run the scan](/downloads/itdr/itdr/active-directory-posture-scan/scanning-active-directory/itdr-scan-ad-select-agent.png)
[]![Select scan frequency](/downloads/deception/identity/scan-agents/scanning-active-directory/zscaler-deception-scan-agents-scan-frequency.png)
[]![Select a scan time](/downloads/deception/identity/scan-agents/scanning-active-directory/zscaler-deception-scan-agents-add-time.png)