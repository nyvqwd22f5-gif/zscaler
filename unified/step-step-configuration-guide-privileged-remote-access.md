# Step-by-Step Configuration Guide for Privileged Remote Access
Source: https://help.zscaler.com/zpa/step-step-configuration-guide-privileged-remote-access
PDF: https://help.zscaler.com/pdf/com/en/1485881.pdf

This guide takes you through the configuration steps to use Zscaler Privileged Remote Access (PRA) for your organization.
Before you begin configuring PRA, Zscaler recommends reading [Understanding Privileged Remote Access](/zpa/understanding-privileged-remote-access).
Prerequisites
You must be authorized to access Privileged Remote Access. Contact your Zscaler Account team for more information.
Configuring PRA
- [Step 1: Creating the PRA Portal](#Step1)
- [Step 2: Add PRA Application Segments](#Step2)
- [Step 3: Add Privileged Consoles](#Step3)
- [Step 4: Add Privileged Policies](#Step4)
- [Step 5: Add Privileged Approvals](#Step5)
- [Step 6: Emergency Access and Arbitrary Domains](#Step6)
[]To use the PRA feature, you must first create a privileged portal, known as the PRA Portal. After you have established a privileged portal, you can add other PRA features to it. To create a privileged portal, see [Configuring Privileged Portals](/zpa/configuring-privileged-portals).
[]After the privileged portal has been created, you can select application segments that you want the privileged portal to include. To designate application segments for PRA, see [Configuring Defined Application Segments.](/zpa/configuring-application-segments)
[]To use the PRA-enabled application segments, you need to assign them to a privileged console. The privileged console is housed in the PRA Portal and is how the end user gets to the set applications. Ensure that the protocol (i.e., SSH, RDP, or VNC) is set up before creating a privileged console, as you must assign a protocol to the privileged console. To create a privileged console, see [Configuring a Privileged Console](/zpa/configuring-privileged-consoles).
[]After you have set up the PRA basics (i.e., privileged portal, PRA-enabled application segments, and privileged consoles), you can begin adding PRA-specific policies to include features to enhance the end user’s PRA experience.
Privileged credentials can be created to allow end users to enter a PRA Portal without needing credentials assigned specifically to them. After a privileged credential is created, a privileged credentials policy rule can be set to apply that privileged credential to a privileged console. To create privileged credentials, see:
- [Configuring Privileged Credentials](/zpa/configuring-privileged-credentials)
- [Configuring Privileged Credentials Policies](/zpa/configuring-privileged-credentials-policies)
Privileged capabilities policies can be created to:
- Allow end users to copy and paste to and from the privileged console to their server.
- Provide admins with the ability to record a privileged session of an end user using a privileged console.
- Give end users the ability to upload with or without inspection, and also download within a privileged console.
To create a privileged capabilities policy, see [Configuring a Privileged Capabilities Policy](/zpa/configuring-privileged-capabilities-policies).
[]To set the amount of time that an end user has access to a privileged console, create a privileged approval. Choose a start and end date, time, and time zone that the end user is authorized to use the privileged console. The end user cannot use the privileged console before the scheduled time, and after the time expires, the end user loses access to that privileged console. For time windows spanning multiple days, you can configure working hours as well as the days of the week for which access is permitted. To create a privileged approval, see [Configuring Privileged Approvals](/zpa/configuring-privileged-approvals).
[]If you use Okta as an IdP, then you have the option to dynamically create end users with Okta. When you are [configuring Okta](/zpa/configuration-guide-okta) for the ZPA Admin Portal, you can enable the Arbitrary Domains feature. After the IdP has been created, you can use API integration to dynamically create end users from Okta to assign emergency access. You can use privileged approvals with emergency access to create end users. To create emergency access users, see:
- [Configuring an IdP for Single Sign-On](/zpa/configuring-idp-single-sign)
- [Configuring Emergency Access](/zpa/configuring-emergency-access)