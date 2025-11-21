# Viewing Internet & SaaS Quarterly Business Review Reports
Source: https://help.zscaler.com/unified/viewing-internet-saas-quarterly-business-review-reports
PDF: https://help.zscaler.com/pdf/com/en/1497556.pdf

The Internet & SaaS Quarterly Business Review (QBR) reports provide customers with extensive insight into how Zscaler is helping protect their network quarter to quarter. It helps customers observe emerging traffic trends and the types of threats that Zscaler is blocking.
A new QBR is generated on the first weekend of every month. However, if the first weekend falls on the first or second day of the month, then the QBR is generated on the following weekend. The QBRs are securely stored as a PowerPoint file in the Zscaler cloud. Up to 15 reports are stored. Admins can download their reports in the Admin Portal (Analytics > Internet & SaaS > Analytics > QBR Reports). If you don't see the QBR, contact your support team or open a Zscaler Support ticket to have it enabled.
If you want to include or exclude road warrior traffic, contact your Zscaler Account team team.
Viewing the QBR Report
The report is divided into different sections and shows the following information:
- [Highlights of Zscaler in Your Environment](#highlights)
- [Access to the Internet and SaaS Apps](#internet-access)
- [Global Traffic Distribution](#traffic-distribution)
- [Quarterly Snapshot](#quarterly-napshot)
- [Company Risk Posture](#risk-score)
- [Protection Against Advanced Threats](#advanced-threats)
- [Protection with SSL Inspection](#ssl-inspection)
- [Threats and Locations by Botnet Callbacks](#botet-callbacks)
- [Phishing Attempts](#phishing)
- [Top Cloud Applications](#cloud-apps)
- [Top Application Categories](#cloud-app-category)
- [Office 365 Growth](#o365)
- [Standard or Advanced Sandbox](#sandbox)
- [Zscaler Support Incidents](#support-incidents)
- [Subscription Information](#subscriptions)
[]An architectural overview of your internet, SaaS, and Private App traffic. Additionally, it provides an overview of your end users' digital experience data.
[]The growth graph of your internet-bound traffic on a monthly basis for the last 12 months. The donut-pie chart breaks down the proxy latency percentage for your organization's overall transactions.
[]A geospatial distribution of your users around the world by showing the number of users and the traffic percentage originating from each location.
[]The growth in your organization's transaction count, bandwidth per user, threats stopped, and policy blocks for the current, previous, and last year's same quarter. You can also see how your organization compares to your peers. Peers are defined by analyzing your industry, geography, and company size.
[]Your company's risk score, computed based on different types of risky events. To gain more insights about your most infectious users and locations, log in to the Admin Portal. To learn more, see [Company Risk Score Report](/unified/about-company-risk-score-report).
The company risk scores are calculated with the help of Advanced Threat Protection. The risk scores are calculated on a 7-day moving window of risk events. For a risk score to be calculated, there needs to be at least 100 risky users in the 7-day window. If there aren't at least 100 authenticated users in the organization, each with at least one risky transaction within that window, then the risk score isn't computed for that day.
[]The most advanced threats blocked by Zscaler can't be detected by firewall, proxy, or anti-virus solutions. Zscaler blocks botnet calls from reaching your command and control centers. Cyber criminals trick your employees into clicking on malicious links to infect their devices and transforming them into botnets. To drill down further into this data, log in to the Admin Portal.
[]How Zscaler solutions can provide the best value for SSL Inspection by blocking highly sophisticated threats which are usually hidden in encrypted traffic. Over 85% of attacks are encrypted. To learn more, see [Spoiler: New ThreatLabz Report Reveals Over 85% of Attacks Are Encrypted](https://www.zscaler.com/blogs/security-research/2022-encrypted-attacks-report) on the Zscaler website.
The qualified SSL in this section refers to the SSL traffic that excludes UCaaS traffic, O365 traffic, and any customer-defined bypass traffic which must be inspected to the fullest extent possible. SSL inspection can be a complex and complicated process for certain organizations. Hence, to learn about trade-offs and privacy considerations, see [Encryption, Privacy, and Data Protection: A Balancing Act](https://www.zscaler.com/resources/white-papers/encryption-privacy-data-protection.pdf) on the Zscaler website.
[]The advanced threats that Zscaler blocked which can't be detected by firewall, proxy, or anti-virus solutions. Zscaler's Advanced Threats Protection policy protects your traffic from fraud, unauthorized communications, and other malicious objects and scripts. To ensure your organization's web security, the Zscaler service identifies a variety of these objects and scripts and prevents them from downloading in the end user's browser.
[]The real examples of phishing attempts on your users that were blocked by Zscaler.
[]The growth in the cloud application traffic on a monthly basis for the last 12 months and the breakdown in the amount of data transferred by each cloud application.
[]The category-wise data transfer breakdown of cloud applications for allowed traffic.
[]The Office 365 growth by month for the last 12 months and the data transfer breakdown for each Office 365 service. Zscaler simplifies Office 365 deployment and provides fast and secure access for all users.
[]The amount of data protected using Standard or Advanced Sandbox. The following distribution is displayed:
- **Total Transactions**: The total number of transactions performed by users in your organization in the last quarter
- **Transactions with Files**: The total number of transactions where users attempted to download files
- **Files required Sandbox**: The total number of files that were sent to the Sandbox for analysis. They were either known files with a unique MD5 and a verdict associated with it, or unknown files that were submitted to the Sandbox for offline analysis.
- **Files unique to your org**: The total number of files submitted by your organization to the sandbox for offline analysis
- **Malicious Files Seen**: The total number of files sent for sandbox analysis and were found to be malicious.
[]The number of incidents and their breakdown by priority over the last 90 days and their user impact.
[]An overview of the Zscaler services you are subscribed to.