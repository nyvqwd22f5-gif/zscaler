# Access Policy Configuration Examples
Source: https://help.zscaler.com/unified/access-policy-configuration-examples
PDF: https://help.zscaler.com/pdf/com/en/1492061.pdf

You can [configure access policies](/unified/about-access-policy) to meet the specific needs of your organization.
The following examples illustrate the best way to configure policies for a variety of scenarios:
- [Allow any user access to any application segments or segment groups](#allowalluserstoallapps)
- [Allow specific users access to specific segment groups](#allowallsomeuserstoapps)
- [Allow specific users access to any application segments or segment groups](#allowsomeuserstoappsgroups)
- [Allow specific users access to specific application segments or segment groups](#allowsomeuserstospecificappgroups)
- [Block specific users access to any application segments or segment groups](#denysomeusers)
- [Block specific users access to specific application segments or segment groups](#denysomeuserssomeapps)
[]To allow any user access to any application segments or segment groups:
- In the** Add Access Policy **window, for **Rule Action**,** **select **Allow Access**.
- Under **Criteria**, leave the **Application Segments** and **Segment Groups** fields blank with the **SAML Attributes** field set to **Any SAML attribute from an IdP**. By not selecting a specific application segment, segment group, or SAML attribute you are indicating that the policy rule should allow any user (from any IdP) access to any application segment and segment group.
- Click **Save**.
![Add Access Policy window within the ZPA Admin Portal](/downloads/zpa/documentation-knowledgebase/policies/access-policy/policy-configuration-examples/zpa-accesspolicy-allowanysamlandappsegorseggrp.png)
[]This configuration is useful if you have a set of applications that you want to group together, and you want to specify who can access that set of applications. For example, you might have a set of applications that you want all users in your organization to access (i.e., an intranet application and a benefits application). For this example, you would [set up your policy rule using this configuration](#withthefollowingconfiguration).
In another example, you might have a set of applications that you only want users from a specific department to access (i.e., HR applications that only users from the Sales department can access). For this example, you would [set up your policy rule using this configuration](#thefollowingconfiguration2).
- [][Create a segment group](/unified/configuring-segment-groups) that includes the applications you want to configure policies for.
- In the** Add Access Policy **window, for **Rule Action**,** **select **Allow Access**.
- Under **Criteria**:
- For **Segment Groups**, select the segment group you created in step 1 (e.g., HR App Group).
- For **SAML Attributes**, leave the field set to **Any SAML attribute from an IdP** for this example. This will apply the policy rule to any user from any IdP you have [configured for user single sign-on (SSO)](/unified/configuring-idp-single-sign).
If you had more than one IdP configured for your organization and you only wanted to apply this policy rule to a specific one, you would click **Select IdP** to choose it and then select **Any SAML Attribute **from the drop-down menu.
- Click **Save**.
![Add Access Policy window within the ZPA Admin Portal](/downloads/zpa/documentation-knowledgebase/policies/access-policy/policy-configuration-examples/zpa-accesspolicy-samlanyandseggrp.png)
- [][Create a segment group](/unified/configuring-segment-groups) that includes the applications you only want users in the Sales department to have access to.
- In the** Add Access Policy **window, for **Rule Action**,** **select **Allow Access**.
- Under **Criteria**:
- For **Segment Groups**, select the segment group you created in step 1 (e.g., HR App Group).
- For **SAML Attributes**:
- Click **Select IdP** and choose the IdP configuration you want include in the policy rule. The IdP must be [configured for user SSO](/unified/configuring-idp-single-sign).
- Select the [SAML attribute](/unified/about-saml-attributes) you want to use (e.g., Department) from the drop-down menu and provide the proper entry for it (e.g., Sales).
- Click **Save**.
![Add Access Policy window within the ZPA Admin Portal](/downloads/zpa/documentation-knowledgebase/policies/access-policy/policy-configuration-examples/zpa-accesspolicy-samlandhrseggrp.png)
[]This configuration is useful if you have a set of users (i.e., users from your IT organization) who must be able to access all applications in your organization.
To allow specific users access to any application segments or segment groups:
- In the** Add Access Policy **window, for **Rule Action**,** **select **Allow Access**.
- Under **Criteria**:
- Leave the **Application Segments** and **Segment Groups** fields blank. By not entering specific applications or segment groups you are indicating that the policy should apply to any application segments or segment groups.
- For **SAML Attributes**:
- Click **Select IdP** and choose the IdP configuration you want include in the policy rule. The IdP must be [configured for user SSO](/unified/configuring-idp-single-sign).
- Select the [SAML attribute](/unified/about-saml-attributes) you want to use (e.g., Group) from the drop-down menu and provide the proper entry for it (e.g., IT Staff).
- Click **Save**.
![Add Access Policy window within the ZPA Admin Portal](/downloads/zpa/documentation-knowledgebase/policies/access-policy/policy-configuration-examples/zpa-accesspolicy-samlandanyappsegorseggrp.png)
[]To allow specific users access to specific application segments or segment groups:
- In the** Add Access Policy **window, for **Rule Action**,** **select **Allow Access**.
- Under **Criteria**:
- Select the **Application Segments **or **Segment Groups** you've configured from the drop-down menus. In this example, the "All Marketing apps" application segment was selected. This allows users in the "Marketing Dept" access to the "All Marketing apps" applications.
- For **SAML Attributes**:
- Click **Select IdP** and choose the IdP configuration you want include in the policy rule. The IdP must be [configured for user SSO](/unified/configuring-idp-single-sign).
- Select the [SAML attribute](/unified/about-saml-attributes) you want to use (e.g., Group) from the drop-down menu and provide the proper entry for it (e.g., Marketing Dept).
- Click **Save**.
![Add Access Policy window within the ZPA Admin Portal](/downloads/zpa/documentation-knowledgebase/policies/access-policy/policy-configuration-examples/zpa-accesspolicy-samlandallmarketingappseg.png)
[]To block specific users from accessing any application segments or segment groups:
- In the** Add Access Policy **window, for **Rule Action**,** **select **Block Access**.
- Under **Criteria**:
- Leave the **Application Segments** and **Segment Groups** fields blank. By not selecting any specific application segments or segment groups you are indicating that the policy should apply to any application segments or segment groups.
- For **SAML Attributes**:
- Click **Select IdP** and choose the IdP configuration you want include in the policy rule. The IdP must be [configured for user SSO](/unified/configuring-idp-single-sign).
- Select the [SAML attribute](/unified/about-saml-attributes) you want to use (e.g., Group) from the drop-down menu and provide the proper entry for it (e.g., Sales).
- Click **Save**.
Because policy rules are enforced in the order listed, if the users you want to block are covered under another access policy rule which allows them access, that allow policy must be listed after this block policy. For example, if you have two access policy rules, one allowing access and one blocking, they must be listed in the following order:
- Block Policy: Blocking users within the Sales group (authenticating using a specific IdP) from any application segments or segment groups
![Add Access Policy window within the ZPA Admin Portal](/downloads/zpa/documentation-knowledgebase/policies/access-policy/policy-configuration-examples/zpa-accesspolicy-blocksamlandanyappsegorseggrp.png)
- Allow Policy: Allowing any other users (authenticating from any other IdP) access to any application segments or segment groups
![Add Access Policy window within the ZPA Admin Portal](/downloads/zpa/documentation-knowledgebase/policies/access-policy/policy-configuration-examples/zpa-accesspolicy-allowanysamlandappsegorseggrp.png)
For this example, the Rule Order within the [Access Policy](/unified/about-access-policy) page would appear as follows:
![Access Policy page within the ZPA Admin Portal](/downloads/zpa/documentation-knowledgebase/policies/access-policy/policy-configuration-examples/zpa-accesspolicypage-blockallowrules.png)
[]You can block specific users from accessing specific applications and segment groups, however, this is only necessary under specific circumstances. By default, until you configure policy rules for applications, users are blocked from accessing any applications or segment groups. They can access applications and segment groups only if you explicitly configure policy rules allowing them to do so. So, configuring a policy rule to deny users access would only be useful for the following circumstances:
- The number of users being blocked from application segments or segment groups is relatively small compared to the number of users with access. For example, if your organization wants to make application segments or segment groups available to most users, but block just a few users, you would create an access policy blocking the specific users, then another access policy allowing any other users. In this example, you would [set up your policy rules using this configuration](#clicktoseeex1).
- You want to allow a specific group of users access to application segments or segment groups, but also want to block individual users within that group. In this example, you would [set up your policy rules using this configuration](#clicktoseeex2).
- []In the** Add Access Policy **window, for **Rule Action**,** **select **Block Access**.
- Under **Criteria**:
- Select the **Application Segments **or **Segment Groups** you've configured from the drop-down menus. In this example, the Intranet Application was selected.
- []For **SAML Attributes**:
- Click **Select IdP** and choose the IdP configuration you want include in the policy rule. The IdP must be [configured for user SSO](/unified/configuring-idp-single-sign).
- Select the [SAML attribute](/unified/about-saml-attributes) you want to use (e.g., Group) from the drop-down menu and provide the proper entry for it, in this case the user group you want to block (e.g., Temp Staff).
- Click **Save**.
![Add Access Policy window within the ZPA Admin Portal](/downloads/zpa/documentation-knowledgebase/policies/access-policy/policy-configuration-examples/zpa-accesspolicy-blocktempstaffintranet.png)
- On the **Access Policy** page, click **Add Rule** again.
- In the** Add Access Policy **window, for **Rule Action**,** **select **Allow Access**.
- Leave the **Application Segments** and **Segment Groups** fields blank. By not selecting a specific application segment or segment group you are indicating that the policy should apply to any application segment and segment group.
- For **SAML Attributes**:
- Click **Select IdP** and choose the same IdP configuration you included in step 2b above.
- Select **Any SAML Attribute** from the drop-down menu.
- Click **Save**.
![Add Access Policy window within the ZPA Admin Portal](/downloads/zpa/documentation-knowledgebase/policies/access-policy/policy-configuration-examples/zpa-accesspolicy-allowallintranet.png)
- []In the** Add Access Policy **window, for **Rule Action**,** **select **Block Access**.
- Under **Criteria**:
- Select the **Application Segments **or **Segment Groups** you've configured from the drop-down menus. In this example, the Sales App Group was selected.
- []For **SAML Attributes**:
- Click **Select IdP** and choose the IdP configuration you want include in the policy rule. The IdP must be [configured for user SSO](/unified/configuring-idp-single-sign).
- Select the [SAML attribute](/unified/about-saml-attributes) you want to use, in this case the user in the group you want to block (e.g., Email address), and provide the proper entry for it (e.g., jane.doe@example.com).
- Click **Save**.
![Add Access Policy window within the ZPA Admin Portal](/downloads/zpa/documentation-knowledgebase/policies/access-policy/policy-configuration-examples/zpa-accesspolicy-blocksamlnameid.png)
- On the **Access Policy** page, click **Add Rule** again.
- In the new** Add Access Policy **window, for **Rule Action**,** **select **Allow Access**.
- Select the **Application Segments **or **Segment Groups** you've configured from the drop-down menus. In this example, the Sales App Group was selected.
- For **SAML Attributes**:
- Click **Select IdP** and choose the same IdP configuration you included in step 2b above.
- Select the [SAML attribute](/unified/about-saml-attributes) you want to use, in this case the group you want to allow (e.g., Group), and provide the proper entry for it (e.g., Sales).
- Click **Save**.
![Add Access Policy window within the ZPA Admin Portal](/downloads/zpa/documentation-knowledgebase/policies/access-policy/policy-configuration-examples/zpa-accesspolicy-allowsamlsalestosalesappseggrp.png)