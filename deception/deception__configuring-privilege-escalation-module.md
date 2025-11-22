# Configuring the Privilege Escalation Module
Source: https://help.zscaler.com/deception/configuring-privilege-escalation-module
PDF: https://help.zscaler.com/pdf/com/en/1531303.pdf

The Privilege Escalation module in landmine policies enables you to detect Man-in-the-Middle (MITM), brute force, and memory credential attacks on the endpoints.
To configure privilege escalation for a landmine policy:
- Go to **Deceive **> **Landmine **> **Policies**.
-
In the landmine policies table, locate the landmine policy you want to use on endpoints to detect different types of privilege escalation attacks, and click the **Edit **icon.
[See image.](#option-to-edit-policy)
- In the policy configuration window, click **Privilege Escalation**, and configure the required options:
- [MITM Attack Detection](#mitm-attack-detection)
- [Brute Force Attack Detection](#brute-force-detection)
- [In Memory Credentials Attack Detection](#in-memory-credential-detection)
[]![A screenshot capturing the option to edit a landmine policy](/downloads/deception/deceive/landmine-decoys/policies/configuring-privilege-escalation-module/deception-landmine-policy-edit-one.png)
[]In an MITM attack, adversaries eavesdrop or pretend to be a legitimate participant and intercept an existing conversation or data transfer on a network. To the unsuspecting user, it appears as though a standard exchange of information is underway. However, the adversaries insert themselves into the middle of the data transfer and steal information.
Adversaries use link-local multicast name resolution (LLMNR) poisoning to become the MITM for unsuspecting users on the network. In a production environment where LLMNR is enabled, users broadcast requests in an attempt to locate other systems on the network. Adversaries use the LLMNR poisoning method to gain privileged access by responding to requests for hostnames on the network. You can configure MITM detection to detect attacks like LLMNR poisoning via the landmine agent.
To configure MITM Detection:
- Under the **Man-in-the-Middle Attack Detection **section:
- Select **Enabled**.
- Enable **LLMNR poisoning**.
- Enter a value in the **Interval (In minutes) **field to broadcast LLMNR name requests.
-
Enter one or more **Hostnames** that are not present on the network. For example, enter `Admin-PC`. These hostnames are used for name resolution requests. For each request, a hostname is randomly selected. If this field is blank, the Zscaler Deception Admin Portal generates the hostnames at random.
[See image.](#deception-privilege-escalation-mim-detection)
- Click **Save**.
[]Adversaries make repeated attempts to gain unauthorized access to accounts with usernames and passwords. They systematically check all possible passwords and passphrases until the correct credentials are found. You can configure brute force attack detection against local admin accounts via the landmine agent. You can set a limit on failed login attempts. When this limit is exceeded, the agent sends an alert to the Deception Admin Portal.
To configure Brute Force Detection:
-
Under the **Brute Force Detection **section:
- Enable **Local Users** to detect brute force attacks against local admin accounts.
- Enter a number for the **Threshold of logon attempts **field** **to define the number of consecutive unsuccessful login attempts that must be used as a threshold for brute force attack detection. The default value is 5.
-
Enter a value for the **Monitoring interval (in minutes) **field to define the time period to monitor the unsuccessful login attempts. The default value is 30 minutes.
For a series of consecutive unsuccessful login attempts to be considered a brute force attack, the login attempts must reach the threshold within the monitoring interval time period. If the **Threshold of logon attempts **value is 5 and the **Monitoring interval (in minutes) **value is 30 minutes, then a brute force attack is detected only if there are at least 5 unsuccessful login attempts within 30 minutes.
[See image.](#deception-privilege-escalation-brute-force)
- Click **Save**.
[]Adversaries harvest credentials from the local security authority subsystem service (LSASS) process in the memory after they obtain administrative or system privileges. You can configure the detection of credential theft from the memory via the landmine agent.
To configure Memory Credentials Detection:
- Under the **In Memory Credentials **section:
- Enable **Use AD Decoy Users** to plant decoy credentials in the memory using the username configured for the accounts in the Active Directory (AD) decoys.
- Select an AD User Decoy from the drop-down menu.
- Enable **Use Additional Custom Credentials** to deploy decoy credentials for the specified username and domain in the system's memory.
- Enter a domain name.
-
Enter a username.
[See image.](#deception-privilege-escalation-in-memory)
- Click **Save**.
[]![A screenshot showing configuration of Privilege escaltion module](/downloads/deception/deceive/landmine-decoys/policies/configuring-privilege-escalation-module/zscaler-deception-privilege-escalation.png)
[]![Configure Brute Force attack detection](/downloads/deception/product-documentation/deceive/endpoint-decoys/policies/configuring-privilege-escalation/zscaler-deception-brute-force-attack.jpg)
[]![Configure memory credential detection](/downloads/deception/deceive/landmine-decoys/policies/deception-module-configuration/configuring-privilege-escalation/zscaler-deception-cpe-imcredentails.png)