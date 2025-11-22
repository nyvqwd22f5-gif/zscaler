# About the System Audit Report
Source: https://help.zscaler.com/unified/about-system-audit-report
PDF: https://help.zscaler.com/pdf/com/en/1497466.pdf

The System Audit Report highlights the status of GRE tunnels, PAC files, authentication frequency, PAC file sizes, Office 365 One Click, and IP visibility. The report runs on the first of every month, and the analysis is presented on everything as of that date. If there are any present issues, the report shows recommendations on how to fix them.
Some issues might involve having no backup or updated GRE tunnels, failing to set up monitoring on the failover tunnel, and not using the ${GATEWAY} MACRO to help forward traffic to Zscaler. These issues might result in traffic inadequately being sent to the Zscaler cloud, which can lead to an internet outage. You might also run into authentication issues and other issues that impact your user experience when sending traffic to Zscaler. For example, the Microsoft-Recommended Office 365 One Click Configuration option ensures a smoother Office 365 experience by automatically exempting the required URLs so that authentication and SSL interception is performed appropriately. If this button is disabled, you might run into user experience issues.
You can view the report in the Admin Portal by going to Analytics > Internet & SaaS > Analytics > System Audit Report.
[See image.](#report)
In some cases, the previous month's report will be unavailable to view. In these cases, you'll be shown the month *prior* to the previous month's report. For example, if you generate your report some time in September, and your August report is unavailable, you'll be shown your July report.
About the System Audit Report
The report has three main sections:
- High Availability Configuration
- [GRE Tunnels](#GRE)
- [PAC Files](#PAC)
- User Experience Configuration
- [Authentication Frequency](#auth)
- [PAC File Size](#pacsize)
- Other Configuration
- [Office 365 One Click](#o365)
- [IP Visibility](#IP)
The overall grade for each main section is the lowest grade received in that section.
The overall grade for the report is the overall grades for High Availability Configuration and User Experience Configuration combined. It's not dependent on Other Configuration.
[]In this section, we aggregate your last month's internet-bound traffic sent in both the Primary or Failover tunnel, and detect whether there's any activity on the tunnel. Tunnel activity includes things like GRE Keep-alives, IPSLA, and regular traffic sent to us. The report only shows tunnels with issues and also shows whether there is missing activity on the Primary or Failover tunnel or both. Information is sorted on Failover missing, followed by Primary missing, followed by both tunnels missing.
[See image.](#greimage)
The following table shows the rubric used to grade this section:
| Issues | Grade |
| ------ | ----- |
| No GRE tunnels | No Grade |
| Issues with *less than *10% of all GRE tunnels | A |
| Other issues between 10% and 90% of all GRE tunnels | B |
| Issues with *more than* 90% of all GRE tunnels | C |
If you receive a grade of B or C, see [Best Practices for Deploying GRE Tunnels](/unified/best-practices-deploying-gre-tunnels).
Even if the GRE tunnels are shown as zero, and you get a letter grade, it's because we are seeing traffic from that IP address. You should create a location associated with that IP address.
[]In this section, we check all PAC files to see if they use an Internet & SaaS Public Service Edge’s static FQDN name or VIP address in the return statement. The PAC files can use Global Internet & SaaS Public Service Edge IP address, Virtual Service Edge IP address, Private Service Edge IP address, or an on-premises proxy solution, and it won’t be flagged in this report.
[See image.](#pacimage)
You can view all the static IPs of a PAC file by clicking **View All** next to the **Static IP Addresses** column. A dialog box appears listing all the static IPs. You can search for static IPs or download the list as a CSV file.
[See image.](#staticIPs)
The following table shows the rubric used to grade this section:
| Issues | Grade |
| ------ | ----- |
| No PAC files | No Grade |
| Issues with *less than *10% of all PAC files | A |
| Other issues between 10% and 90% of all PAC files | B |
| Issues with *more than* 90% of all PAC files | C |
If you receive a grade of B or C, see [Best Practices for Writing PAC Files](/unified/best-practices-writing-pac-files).
[]In this section, we check the authentication frequency configuration. We also check to see if authentication is enabled for any location.
[See image.](#authimage)
The following table shows the rubric used to grade this section:
| Status | Grade |
| ------ | ----- |
| Authentication Disabled for all locations | No Grade |
| Configured Only Once | A |
| Other (Weekly, Custom, etc.) | B |
| Configured Daily or Once Per Session | C |
[]In this section, we check the size of all PAC files and flag files that are greater than 25 KB. Shorter PAC files are evaluated more quickly, enhancing the user experience.
[See image.](#pacsizeimg)
The following table shows the rubric used to grade this section:
| Issues | Grade |
| ------ | ----- |
| No PAC files | No Grade |
| Issues with *less than *10% of all PAC files | A |
| Other issues between 10% and 90% of all PAC files | B |
| Issues with *more than* 90% of all PAC files | C |
If you receive a grade of B or C, see [Best Practices for Writing PAC Files](/unified/best-practices-writing-pac-files).
[]In this section, we check to see if the Microsoft-Recommended Office 365 One Click Configuration is enabled.
[See image.](#O365image)
The following table shows the rubric used to grade this section:
| Status | Grade |
| ------ | ----- |
| Enabled | A |
| Disabled | B |
[]In this section, we check the overall traffic on each GRE tunnel, and also obtain the overall internal IPs seen inside the tunnel. We then calculate the approximate number of users for that GRE tunnel. If the difference between the internal IPs and the approximate number of users is high, we flag the GRE tunnel to say that NAT is performed.
[See image.](#ipvisimage)
The following table shows the rubric used to grade this section:
| Issues | Grade |
| ------ | ----- |
| No GRE tunnels | No Grade |
| Tunnels with NAT are *less than *10% of all GRE tunnels | A |
| Other issues between 10% and 90% of all GRE tunnels | B |
| Tunnels with NAT are *more than* 90% of all GRE tunnels | C |
If you receive a grade of B or C, see [Best Practices for Deploying GRE Tunnels](/unified/best-practices-deploying-gre-tunnels).
[]****![System Audit Report](/downloads/zia/dashboard-analytics/reports/about-system-audit-report/updated-system-audit-report_0.png)
****
[]****![GRE Tunnels](/downloads/zscaler-tech-pubs-style-guide/draft-articles/about-system-audit-report/updated-gre-tunnels.png)
****
[]****![PAC Files](/downloads/unified/analytics/internet-saas/reports/about-system-audit-report/Static%20PAC%20Files.png)
****
[]![Static IPs Dialog Box](/downloads/zscaler-tech-pubs-style-guide/draft-articles/about-system-audit-report/PAC%20Files%20Static%20IP%20wo%20scroll.png)
[]****![Authentication Frequency](/downloads/zscaler-tech-pubs-style-guide/draft-articles/about-system-audit-report/updated-authentication-frequency.png)
****
[]****![PAC Files](/downloads/zscaler-tech-pubs-style-guide/draft-articles/about-system-audit-report/updated-PAC-file-size_0.png)
****
[]****![Other Configuration](/downloads/zscaler-tech-pubs-style-guide/draft-articles/about-system-audit-report/updated-other-configuration.png)
****
[]****![IP Visibility](/downloads/zscaler-tech-pubs-style-guide/draft-articles/about-system-audit-report/updated-IP-visibility.png)
****