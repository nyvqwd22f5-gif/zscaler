# Configuring URL Filtering Policies
Source: https://help.zscaler.com/unified/configuring-url-filtering
PDF: https://help.zscaler.com/pdf/com/en/1488016.pdf

URL filtering policies allow you to use predefined URL categories to determine how internet traffic in each of the categories is handled by Zscaler. There are three ways to route traffic:
- **Block**: websites belonging to blocked categories cannot be accessed by users in your organization.
- **Isolate**: websites belonging to isolated categories will open in a remote browser in a Zscaler data center, preventing any active content from the web page from reaching the user's device. To learn more, see [Isolation Policy](/unified/policies/private-applications/access-control/clientless/isolation-policy).
- **Allow**: websites belonging to allowed categories will open normally within the user's browser.
To define URL filtering policies:
- After you have set up users and traffic forwarding, click **Set Up Policies**.
- The U**RL Filtering** page shows a recommended setup to route internet traffic when users visit websites matching each of the specified URL categories. You can drag the URL categories to the **Block**, **Isolate**, or **Allow **columns to set up the filtering policy appropriate for your organization.
- When done, click **Next** to move on to [configure SSL inspection](/unified/configuring-ssl-inspection).
You can fine-tune your configuration later in the Admin Portal. To learn more about how URLs are categorized, see [About URL Categories](/unified/about-url-categories)*.*