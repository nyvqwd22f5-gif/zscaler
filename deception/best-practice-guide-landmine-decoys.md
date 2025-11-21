# Best Practice Guide for Landmine Decoys
Source: https://help.zscaler.com/deception/best-practice-guide-landmine-decoys
PDF: https://help.zscaler.com/pdf/com/en/1531586.pdf

This guide provides use cases and deployment recommendations for landmine decoys.
Landmine decoys are deployed in endpoint machines to lure attackers, typically within an organization. Landmine decoys are typically deployed to detect different types of techniques, defined in the MITRE ATT&CK framework, such as defense evasion ([T1562.001](https://attack.mitre.org/techniques/T1562/001/)), impact ([T1489 ](https://attack.mitre.org/techniques/T1489/)and [T1485](https://attack.mitre.org/techniques/T1485/)), credential access ([T1552.001](https://attack.mitre.org/techniques/T1552/001/) and [T1557.001](https://attack.mitre.org/techniques/T1557/001/)), and collection ([T1005](https://attack.mitre.org/techniques/T1005/)).
Landmine decoys are deployed via [landmine policies](/deception/v4_23/about-policies). To deploy landmine decoys, Zscaler recommends having two different types of policies: a policy for simple detections that requires no customization, and a policy for advanced detections that requires minimal customization to detect adversarial techniques.
- [Policy for Simple Detections](#policy-for-simple-detections)
- [Policy for Advanced Detections](#policy-for-advanced-detections)
In addition, a custom policy must be created for each department in the organization based on the function for which the department is responsible. Typically, a department can have up to 4 policies tailored for them, and at least two policies must be configured for business-critical departments.
To learn how to create a landmine policy, see [Creating a Landmine Policy](/deception/v4_23/creating-landmine-policy).
- Before configuring a landmine policy, ensure that you have customized the landmine installer name. To learn more, see [Customizing Landmine Installer](/deception/v4_23/customizing-landmine-installer).
-
The deployment can be done in phases for each department, starting from the highest priority based on the department's security risk.
[See example](#department-list)
A typical deployment must have one policy for simple detections, and one policy for advanced detections covering all endpoints and a custom policy tailored for the department.
Some use cases for creating custom policies are as follows:
- [Use Case: Custom Policy for Known Departments (IT, Security, HR, Finance, Legal, etc.)](#known-department-use-case)
- [Use Case: Custom Policy for Critical Job Functions](#critical-function-use-case)
[]The following list of departments is an example of prioritization (from highest to lowest) of departments for a phased deployment of landmine policies:
- Security and Active Directory (AD) Administrators
- Network Infrastructure
- IT or Critical Application Administrators
- Senior Management
- Marketing
- Others
[]The following table provides information on the recommended configurations of a landmine policy for simple detections.
-
-
-
-
-
-
-
[](/deception/v4_23/configuring-privilege-escalation-module)
-
-
-
[](/deception/v4_23/configuring-file-decoys-module)
-
-
-
[](/deception/v4_23/configuring-password-settings-module)
| Landmine Policy Module | Recommended Configurations |
| ---------------------- | -------------------------- |
| Privilege Escalation | Enable **Man-in-the-Middle Attack Detection** with the following configurations:Enable **LLMNR **poisoning.Set **Interval **to 5 minutes.Enable **In-Memory Credentials **with the following configurations (for all Windows-based endpoints):Enable **Use AD Decoy Users**.Select an AD Decoy User.(Optional) Select **Use additional Custom Credentials** and add **Domain **and **User **values as required.To learn more, see Configuring the Privilege Escalation Module. |
| File Decoys | Create a credential file decoy with the following configurations:**Name**: `password1.txt`**Path**: `%userprofile%\Imp`**Hidden**: EnabledTo learn more, see Configuring the File Decoys Module. |
| Password Policy | Configure a password policy similar to your Active Directory (AD) password policy. If you do not have an AD password policy, then you can create a policy with the following configurations:Enable **Must have special characters**.Set **Min Length **to `8`.Set **Max Length **to `12`.To learn more, see Configuring the Password Settings Module. |
[]The following table provides information on the recommended configurations of a landmine policy for advanced detections.
-
-
-
-
-
-
-
-
-
[](/deception/v4_23/configuring-defense-evasion-module)
-
-
-
[](/deception/v4_23/configuring-advanced-deception-capabilities-module)
| Landmine Policy Module | Recommended Configurations |
| ---------------------- | -------------------------- |
| Defense Evasion | Enable **Fake Security Processes** and configure fake security processes resembling popular applications that are usually targeted by adversaries. Some examples of fake security processes for popular applications are listed as follows:Symantec Endpoint Protection:**Name**: `ccSvcHst.exe`**Path**: `C:\Program Files\Symantec\Symantec Endpoint Protection\`Microsoft Word:**Name**: `winword.exe`**Path**: `C:\Program Files\Microsoft Office\Word`Acronis:**Name**: `AcronisAgent.exe`**Path**: `C:\Program Files\tmp_shared\`While configuring fake process paths, ensure that you do not use the actual paths of the legitimate applications as they might cause some issues. However, Zscaler recommends using paths that look similar to the default paths of the legitimate application. For example, if Symantec uses `C:\Program Files\Symantec\ccsvchost.exe` as the default path, then the fake process path can be `C:\Program Files\Common Files\Symantec\ccsvchost.exe`.To learn more, see Configuring the Defense Evasion Module. |
| Advanced Deception Capabilities | Enable the following options:**PsExec Detection****Ransomware Detection****Triage**To learn more, see Configuring the Advanced Deception Capabilities Module. |
[]
[](/deception/v4_23/configuring-cloud-lures-module)[](/deception/v4_23/configuring-browser-lures-module)[](/deception/v4_23/configuring-session-lures-module)
-
-
-
[](/deception/v4_23/configuring-file-decoys-module)
| Landmine Policy Module | Recommended Configurations |
| ---------------------- | -------------------------- |
| Cloud Lures | Enable one or more AWS or Azure lures and select appropriate **Target Decoys **for each lure. To learn more, see Configuring the Cloud Lures Module. |
| Browser Lures | Enable browser lures for Chrome, Firefox, Edge, and Internet Explorer, and enable **Cookies**, **Favorites**, and **Credentials **options as applicable. Select the appropriate **Target Decoys **for each department. To learn more, see Configuring the Browser Lures Module. |
| Session Lures | Enable session lures based on the applications used in a department, and select the appropriate **Target Decoys** for each department. For example, you can enable FileZilla, PuTTY, RDP, WinSCP, Windows Credentials, etc. To learn more, see Configuring the Session Lures Module. |
| File Decoys | Create file decoys using **Pre-Configured File Datasets** for each department:**Dataset**: Based on the department, select a dataset (**IT Security**, **Information Technology - General**, **Finance** **- Banking**, **Finance - Strategy**, **Human Resources**,** **etc.).**Path**: `%userprofile%\Imp`**Hidden**: EnabledTo learn more, see Configuring the File Decoys Module. |
[]
[](/deception/v4_23/configuring-cloud-lures-module)[](/deception/v4_23/configuring-browser-lures-module)[](/deception/v4_23/configuring-session-lures-module)
-
-
-
[](/deception/v4_23/configuring-file-decoys-module)
| Landmine Policy Module | Recommended Configurations |
| ---------------------- | -------------------------- |
| Cloud Lures | Enable one or more AWS or Azure lures and select appropriate **Target Decoys **for each lure. To learn more, see Configuring the Cloud Lures Module. |
| Browser Lures | Enable browser lures for Chrome, Firefox, Edge, and Internet Explorer, and enable **Cookies**, **Favorites**, and **Credentials **options as applicable. Select the appropriate **Target Decoys **for the business-critical function. To learn more, see Configuring the Browser Lures Module. |
| Session Lures | Enable session lures based on the applications used in a department, and select the appropriate **Target Decoys** for the business-critical function. For example, you can enable FileZilla, PuTTY, RDP, WinSCP, Windows Credentials, etc. To learn more, see Configuring the Session Lures Module. |
| File Decoys | Create file decoys using **Custom Files **with the following configurations:**Dataset**: Select a custom file dataset**Path**: `%userprofile%\Imp`**Hidden**: EnabledTo learn more, see Configuring the File Decoys Module. |