# Configuring AppProtection Dynamic Rules
Source: https://help.zscaler.com/zpa/configuring-appprotection-dynamic-rules
PDF: https://help.zscaler.com/pdf/com/en/1485796.pdf

After you have created [access policies](/zpa/about-access-policy) and have set up [AppProtection](/zpa/about-appprotection-profiles), you can create dynamic rules to automatically create AppProtection policies to inspect the traffic of your domains.
To add a dynamic rule to an AppProtection profile:
- Go to **Configuration & Control** > **Security** > **AppProtection Profiles**.
- Click **Add Dynamic Rule**.
The **Add Dynamic Rule** window appears.
- In the **Add Dynamic Rule** window, enter the following information:
- [Step 1: Select Policies](#Step1)
- [Step 2: Profile Details](#Step2)
- [Step 3: Create Policies](#Step3)
- [Step 4: Review](#Step4)
- []On the **Select Policies** tab in the **General Information** section, select access policies from the drop-down menu. Access policies enabled with privileged approvals do not appear as they are bypassed by dynamic rules.
- Click **Next**.
[See image.](#Step1im)
[]![Select access policies for the dynamic rule in the ZPA Admin portal](/downloads/zpa/appprotection-private-application-traffic-formerly-inspection/appprotection-private-application-traffic-profiles-formerly-inspection/configuring-appprotection-profiles/Step1.png)
[]On the **Profile Details** tab, in the **Selected Access Policies** section, the access policies that you selected in the previous step are listed.
- In the **AppProtection Profile** section, select the **AppProtection Profile Type**, either a **Default Profile** or an **Existing Profile**. If you attempt to select the **Default Profile **option and a default AppProtection profile already exists, an error appears. If you select **Existing Profile**, you need to then select an existing AppProtection profile from the drop-down menu.
- Click **Next**.
[See image.](#Step2im)
[]![Select the AppProtection profile type for the dynamic rule in the ZPA Admin portal](/downloads/zpa/appprotection-private-application-traffic-formerly-inspection/appprotection-private-application-traffic-profiles-formerly-inspection/configuring-appprotection-profiles/Step2.png)
[]On the **Create Policies** tab, in the **Profile and Policies** section, the AppProtection profile and the access policies you selected in the previous steps are listed.
- To automatically create AppProtection policies, select the **Auto create AppProtection policies** checkbox.
- Click **Save and Review**.
[See image.](#Step3im)
[]![Automatically create AppProtection policies with the dynamic rule in the ZPA Admin portal](/downloads/zpa/appprotection-private-application-traffic-formerly-inspection/appprotection-private-application-traffic-profiles-formerly-inspection/configuring-appprotection-profiles/Step3.png)
[]On the **Review** tab, review your dynamic rule configuration, then click **Save**.
[See image.](#Step4im)
[]![Review the newly created dynamic rule in the Add Dynamic Rule window in the ZPA Admin Portal](/downloads/zpa/appprotection-private-application-traffic-formerly-inspection/appprotection-private-application-traffic-profiles-formerly-inspection/configuring-appprotection-dynamic-rules/step4updated.png)