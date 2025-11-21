# About ML Recommendations for Resource Groups
Source: https://help.zscaler.com/zpa/about-ml-recommendations-resource-groups
PDF: https://help.zscaler.com/pdf/com/en/1531949.pdf

When [configuring resource groups](https://help.zscaler.com/zpa/configuring-resource-groups) for [Microsegmentation policies](/zpa/configuring-microsegmentation-policies), admins can eliminate manual time and effort spent on reviewing [resources](https://help.zscaler.com/zpa/about-resources). To help admins easily find resources with enough similarities to group together, admins can generate machine-learning (ML) recommendations to provide suggestions for configuration. To learn more, see [About Resources](/zpa/about-resources).
ML recommendations automatically find and generate suggestions for resource groups based on user-defined cloud tags, cloud environment metadata, and host data. Admins can review an ML recommendation and accept and approve it, edit and approve it, or ignore it for resource group configuration. Selecting a recommendation for approval means it will automatically be configured as a resource group. Selecting a recommendation to be ignored means that its specific data won't be regenerated in a future recommendation.
Admins must first accept the terms agreement that appears on the ML Recommended Resource Groups page in order to begin seeing recommendations. To disable it, admins must contact Zscaler Support.
The ML Recommended Resource Groups page provides the following benefits and enables you to:
- View machine-learning recommendations for configuring resource groups.
- Compare similar resource information.
- Discover insights about collective resource data.
About the ML Recommended Resource Groups Page
On the ML Recommended Resource Groups page (Microsegmentation > Analytics > Resource Groups > ML Recommended), you can do the following:
- Refresh the ML Recommended page to reflect the most current information.
- Show or hide the ignored list of ML recommendations.
- [Display user-defined resource groups.](https://help.zscaler.com/zpa/about-resource-groups)
- Display ML-recommendations for resource groups.
- View a list of all ML recommendations for your organization. For each recommendation, you can see:
- **Name**: The name of the recommendation.
- **Resource Type**: The type of resource (**Managed** or **Unmanaged**).
- **Member Count**: How many resources are in the recommendation.
- **Confidence Score**: The likelihood from 1 to 100 of how optimal the recommendation is for configuration. A score of 1 is considered the lowest confidence, and a score of 100 is considered the highest confidence.
- Click an individual ML recommendation to view its complete information and accept, edit, or ignore it for configuration.
[See image.](#resource-info-window)
- Review a recommendation.
- Delete a recommendation.
- [Modify the columns displayed in the table.](https://help.zscaler.com/zpa/using-tables)
- Display more rows or a different page of the table.
- View the last time a recommendations check was run, and when the next check is scheduled for.
- View instructions to have Zscaler Support enable or disable ML recommendations for your organization.
- Go to the [Resources](/zpa/about-resources) page to view resource information.
- Go to the [AppZones](/zpa/about-appzone-page) page to view AppZone information.
![A view of the Resources page and it's filters: Name, Type, Platform, AppZone, Agent ID, Cloud, and Resource ID.](/downloads/tech-pubs-drafts/zws-draft-articles/about-ml-recommendations-resource-groups-draft-doc-57218/About-Resource-Page_ML-Recommendations2.png)
[]![The information details for an individual resource.](/downloads/zpa/microsegmentation/resource-management/resources/about-ml-recommendations-resource-groups/ML-Recommendation-Edit-page2.png)