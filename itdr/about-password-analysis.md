# About Password Analysis
Source: https://help.zscaler.com/itdr/about-password-analysis
PDF: https://help.zscaler.com/pdf/com/en/1531850.pdf

Credential or password mismanagement in Active Directory (AD) domains pose significant security risks. Adversaries use leaked credentials to perform credential stuffing attacks to gain unauthorized access to other accounts by exploiting reused passwords across multiple platforms. The Zscaler ITDR server agent detects compromised identities and weak passwords in both regular and privileged AD user accounts.
After you [enable password analysis in the server agent policy](/itdr/configuring-server-agent-policy), the agent identifies compromised or weak passwords by checking hashes against leaked databases, common patterns, and custom dictionaries while also monitoring for password reuse or rotation. The analysis is done locally on the selected domain controller (DC) and does not leave the customer environment, ensuring security and compliance.
The Password Analysis dashboard provides the following benefits:
- Provides a summary of compromised or weak passwords in AD user accounts.
- Enables you to analyze password vulnerabilities and enforce stronger password policies to reduce the risk of unauthorized access and prevent potential security breaches.
- Provides a graphical representation of AD users who have reused passwords.
About the Password Analysis Dashboard
On the Password Analysis dashboard (ITDR > Dashboard > Password Analysis > Dashboard), you can do the following:
- Filter password analysis data by AD domains.
- View the total number of AD user accounts analyzed, including both regular and privileged AD user accounts.
- View the total number and percentage of AD user accounts with weak or easily guessed passwords.
- View the total number and percentage of AD user accounts whose passwords have been found in leaked password databases.
- View password analysis for privileged accounts, such as the total number of AD user accounts discovered, passwords cracked, passwords leaked, and passwords found in leaked databases. The data is represented in a Venn diagram.
- View the percentage of AD users who have reused passwords. The data is represented in pie charts for both regular and privileged users.
![About the Password Analysis dashboard](/downloads/itdr/dashboard/password-analysis/about-password-analysis/itdr-ad-password-analysis-dashboard-4.png)