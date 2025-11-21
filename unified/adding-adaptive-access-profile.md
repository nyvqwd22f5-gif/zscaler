# Adding an Adaptive Access Profile
Source: https://help.zscaler.com/unified/adding-adaptive-access-profile
PDF: https://help.zscaler.com/pdf/com/en/1508396.pdf

The Adaptive Access profile is a measure to calculate the risks associated with users and devices accessing applications via Zscaler. The Adaptive Access profile allows you to define how Zscaler detects any suspicious behavior or malicious activity and remediate the risk by enforcing adaptive policies.
You can configure the Adaptive Access profiles by combining and aggregating context signals from Zscaler and third-party services. Any user or device that matches the profile criteria is notified to the policy enforcement points (Internet & SaaS (Zscaler Internet Access (ZIA)) and Private Applications (Zscaler Private Access (ZPA))) that enforce policies based on the nature of the identities, the resources being accessed, and the context signals associated with the identities accessing the resources.
Prerequisites
Make sure the following prerequisites are met:
- You must complete the integration of third-party services, such as [Okta](/unified/integrating-okta-adaptive-access-engine), [CrowdStrike](/unified/integrating-crowdstrike-adaptive-access-engine), or Azure AD that are relevant to your organization, before defining the Adaptive Access profiles.
- Only administrators can add the Adaptive Access profiles.
Adding an Adaptive Access Profile
To add an Adaptive Access profile:
- Go to **Policies** > **Common Configuration** > **Adaptive Access **>** Profiles**.
-
Click **Add Profile**.
[See image.](#aae-addprofilebutton)
The **Add Profiles** window appears.
-
In the **Add Profiles** window:
- **Profile Name**: Provide a name for the profile.
- **(Optional) Description**: Enter a short description, if required.
-
**Criteria**: Select **All** or **Any** from the drop-down menu, then click the **Add** icon to define the criteria.
[See image.](#aae-plus-icon)
- Select the third-party tool from where the context signal must be received.
- Select the event that must be monitored. The events or incidents differ for each third-party tool.
-
Select the **Operator**, logical expression, condition, or numerical value, as required.
[See image.](#aae-crowdstrikecriteria)
The JSON expression is automatically updated as you define the criteria.
[See image.](#aae-addprofile)
- Click **Save**.
The newly created profile is displayed on the **Profiles **page. The Adaptive Access Engine receives context signals which are evaluated against the profile criteria, and these signals are displayed on the [Signal History page](/unified/about-signal-history).
[]![Add a profile](/downloads/unified/policies/adaptive-access-engine/adding-adaptive-access-profile/aae-addoktaprofile.png)
[]![Click the Add Profile button](/downloads/unified/policies/adaptive-access-engine/adding-adaptive-access-profile/aae-addprofilebutton.png)
[]![Select the profile criteria](/downloads/unified/policies/adaptive-access-engine/adding-adaptive-access-profile/aae-okta-criteria.png)
[]![Click the Plus icon](/downloads/unified/policies/adaptive-access-engine/adding-adaptive-access-profile/aae-plusimage.png)