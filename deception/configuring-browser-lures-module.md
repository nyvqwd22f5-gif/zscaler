# Configuring the Browser Lures Module
Source: https://help.zscaler.com/deception/configuring-browser-lures-module
PDF: https://help.zscaler.com/pdf/com/en/1531305.pdf

The Browser Lures module enables you to add decoy credentials, cookies, and bookmarks to browsers such as Google Chrome, Mozilla Firefox, Microsoft Edge, and Internet Explorer on endpoints.
To configure browser lures for a landmine policy:
- Go to **Deceive** > **Landmine** > **Policies**.
-
In the landmine policies table, locate a landmine policy you want to use to deploy browser lures on endpoints, and click the **Edit** icon.
[See image.](#edit-icon-browser-lures)
- In the policy configuration window:
- Click **Browser Lures**.
- Enter a folder name in the **Favorites Folder **field to use while creating favorites for all supported browsers.
-
Select the type of lures you want to deploy for the browser of your choice. The available lures are **Cookies**,** Favorites**, and** Credentials**.
For Edge browser lures, if your environment includes endpoints running landmine agent or agentless up to version 4.23, you can select the **Force Apply** option to disable the **Startup boost **option in the browser settings. When the **Startup boost **option is enabled in the browser settings, the browser runs in the background with minimal processes to improve performance. However, this can prevent landmine policies from being applied to the browser. By default, the **Force Apply** option is disabled.
For newer versions (later than 4.23) of landmine agent and agentless, the polices are applied even if the **Startup boost **option is enabled in Edge browsers without using the **Force Apply** option.
[See image.](#force-apply-policy-edge)
- Cookie lures are not supported in Internet Explorer.
- For Chrome browsers, a new profile with a random name is created to store lures. This is maintained as a hidden profile and exists alongside the default user profile. The lures are deployed in the newly created profile.
-
Select a network decoy or threat intelligence decoy from the **Target decoys** drop-down menu as targets for the lures.
If the **Target decoys** field is blank, all of the decoys running the web service are used as a default pool. The landmine agent randomly selects the decoys from the pool of target decoys and adds them to the browser. A maximum of two decoys are deployed for each browser and the type of lure.
[See image.](#config-browser-lures-deception-module)
- The **GenAI** icon indicates browser lures that support generative AI decoys as target decoys.
- If the target decoy is an authentication-enabled generative AI decoy and the **Credentials **lure option is enabled for a browser, then adversaries can use the fake credentials stored in the browsers to log in to the generative AI decoys. To learn more about authentication-enabled generative AI decoys, see [Configuring Services on a Network Decoy](/deception/configuring-services-network-decoy).
-
Click **Save**.
The landmine policy is configured with browser lures.
[See image.](#browser-lure-deception-module-added)
Passwords for the browser lures are generated according to the rules configured in the [Password Settings](/deception/configuring-password-settings) deception module.
[]![A screenshot capturing the option to edit a landmine policy](/downloads/deception/deceive/landmine-decoys/policies/configuring-browser-lures-module/deception-landmine-policy-edit-one.png)
[]![A screenshot of the Browser Lures module in a landmine policy](/downloads/deception/deceive/landmine-decoys/policies/configuring-browser-lures-module/zscaler-deception-browser-lures.png)
[]![Browser Lures deception module added](/downloads/deception/deceive/landmine-decoys/policies/configuring-browser-lures-module/deception-policy-added-browser-lures.png)
[]
![Enabling Force Apply option for a landmine policy](/downloads/deception/product-documentation/deceive/endpoint-decoys/policies/configuring-browser-lures-module/zd-rn-edge-forceapply.png)