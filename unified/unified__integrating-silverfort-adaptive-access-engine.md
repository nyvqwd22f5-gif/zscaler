# Integrating Silverfort with Adaptive Access Engine
Source: https://help.zscaler.com/unified/integrating-silverfort-adaptive-access-engine
PDF: https://help.zscaler.com/pdf/com/en/1532397.pdf

The Adaptive Access Engine receives user risk signals from Silverfort, which might be used to control user access to applications via Zscaler. You can configure the Silverfort settings in Experience Center and establish the connection between Silverfort and Adaptive Access Engine. Silverfort shares the context signals (User Risk Level) with the Adaptive Access Engine.
Prerequisites
Ensure that you have:
- A Silverfort version 5.3 and above.
- A Silverfort account with admin privileges.
- An admin role in Experience Center that allows you to configure the Adaptive Access Engine settings.
Ensure you complete the following on Silverfort:
- Get the shared signals framework (SSF) well-known endpoint for the Silverfort tenant.
-
Generate a bearer token on the Silverfort console.
Refer to the Silverfort documentation to get these details.
Configuring Silverfort Integration
To configure the Silverfort integration in Experience Center:
- Go to **Policies** > **Common Configuration** > **Adaptive Access** > **Integrations**.
-
On the **Integrations** page, click the **Edit** icon for Silverfort.
[See image.](#aae-integpage-sf)
The** Edit Silverfort** window appears.
-
In the** Edit Silverfort** window:
- **Bearer Token**: Enter the bearer token generated on the Silverfort console.
- **SSF Config Endpoint**: Enter the URL SSF well-known endpoint from Silverfort.
- **Status**: Enable to make the integration active.
- **Signal **and** Value Type**: The context signal type (User Risk Level) that Silverfort shares with Adaptive Access Engine.
[See image.](#aae-editsilverfort)
- Click **Save**.
-
Click **Test Integration** to verify the connection between Adaptive Access Engine and Silverfort.
A message appears indicating that the connection is successful. The Silverfort configuration is complete. You can proceed to create user and device profiles.
[]![Configure Silverfort](/downloads/unified/policies/adaptive-access-engine/integrating-silverfort-adaptive-access-engine/aae-silverfort-edit.png)
[]![Click the Edit icon to configure Silverfort.](/downloads/unified/policies/adaptive-access-engine/integrating-silverfort-adaptive-access-engine/aae-integpage-silverfort.png)