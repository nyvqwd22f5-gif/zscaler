# Adding a Custom Compliance Framework
Source: https://help.zscaler.com/dspm/adding-custom-compliance-framework
PDF: https://help.zscaler.com/pdf/com/en/1529783.pdf

You can add custom compliance frameworks either by cloning the predefined ones or by creating new ones from scratch. When you clone an existing framework, only the policies from that framework are added to the new one.
To add a custom framework:
- Go to **Analytics **> **Compliance**.
-
Click **Add Framework**.
[See image.](#addframework)
The **Create Custom Framework** page appears.
- Do one of the following:
- Click **Create New Template** to create a new one.
- Click **Use This Template **to choose an existing compliance framework.
-
Click **Next**.
[See image.](#choosetemplate)
-
On the **Configure Categories** page:
- **Category Name**: Enter a name for the [compliance ](/dspm/supported-frameworks)category.
- **Control Numbers**: Enter control numbers to assign to the category.
- Click **Add Category** to add more categories and assign control numbers.
[See image.](#configurecategories)
- Click **Next**.
-
On the** Select Policies **page, under **Available Policies**, select the policies that detect issues relevant to this framework and click **Next**.
You can filter the policies based on the available filters, search for a specific policy, or click **Select All** to select all the listed policies.
[See image.](#select-policies)
-
On the **Assign Categories** page, map each policy to a specific category and control number.
[See image.](#assigncategories)
You can also assign the same category to multiple policies.
[See image.](#multiplepolicies)
- Click **Next**.
-
On the **Select Engines** page, select the DLP engines that identify the data types relevant for this framework and click **Next**.
You need to select at least one DLP engine, or click **Select All** to select all the listed DLP engines.
[See image.](#selectengines)
-
On the **Summary **page:
- **Framework Name**: Enter a name for the custom framework.
- **Framework Description** (Optional): Enter the description.
- Review the custom framework details and edit if required, then click **Finish**.
[See image.](#summary-page)
The custom compliance framework is added and displayed on the [Compliance ](/dspm/about-compliance)page and enabled by default.
[]![The Compliance dashboard with the list of compliance frameworks and annotations around Add Framework button.](/downloads/dspm/analytics/compliance/adding-custom-compliance-framework/dspm-add-custom-framework.png)
[]![The Choose Template page displaying the list of all the available frameworks.](/downloads/dspm/analytics/compliance/adding-custom-compliance-framework/dspm-choose-template-no-annotations.png)
[]![The Configure Categories page to add compliance category and control numbers.](/downloads/dspm/analytics/compliance/adding-custom-compliance-framework/dspm-congure-categories-page.png)
[]![The Select Policies page with displaying the list of available policies.](/downloads/dspm/analytics/compliance/adding-custom-compliance-framework/dspm-select-policies-page.png)
[]![Select multiple policies to map the compliance categories and control numbers.](/downloads/dspm/analytics/compliance/adding-custom-compliance-framework/dspm-select-multiple-policies-new.png)
[]![The Assign Categories page with the list of selected policies to map the control category and control number.](/downloads/dspm/analytics/compliance/adding-custom-compliance-framework/dspm-assign-categories.png)
[]![The Select Engines page displaying the list of available DLP engines.](/downloads/dspm/analytics/compliance/adding-custom-compliance-framework/dspm-select-engines-page.png)
[]![The Summary page to review the custom framework details ](/downloads/dspm/analytics/compliance/adding-custom-compliance-framework/dspm-summary-page.png)