# About Labels
Source: https://help.zscaler.com/zdx/about-labels
PDF: https://help.zscaler.com/pdf/com/en/1461826.pdf

Admins can create labels and then assign the labels as an option during alert rule configuration. After assigning the label, the label becomes part of the alert details and is seen in the delivered alert details when you configure webhooks.
Labels provide the following benefits and enable you to:
- Create and apply multiple labels to an alert rule for grouping purposes.
- Increase the number of alert details for ease of use when configuring webhooks.
To manage and assign labels, you must have the Full Alerts permission. To learn more, see [Adding ZDX Roles](/zdx/adding-zdx-roles).
On the Labels page (Administration > Resources> Labels), you can do the following:
-
[Add a new label.](/zdx/managing-labels#addlabel)
After creating the label, you can assign it to an alert rule in either the** **Add New Alert Rule or Edit Alert Rule window. To learn more, see [Configuring an Alert Rule](/zdx/configuring-alert-rule) and [Editing an Alert Rule](/zdx/editing-alert-rule).
- View a list of created labels. For each label, you can view:
- **Name**: The label name.
- **Description**: The label description.
- **Alert Rules Tagged**: The number of alert rules tagged with the label.
- **Actions**: The actions you can do for a label.
- Search for a label.
- Select which table options to display on the created labels list.
-
Select one of the actions for the label:
- [View the label.](/zdx/managing-labels#viewlabel)
- [Edit the label.](/zdx/managing-labels#editlabel)
- [Delete the label.](/zdx/managing-labels#deletelabel)
You cannot delete a label if an alert rule is tagged with it.
- Navigate through the pages of labels.
![Labels Overview Page](/downloads/zdx/alerts/about-labels/AboutLabels-0.jpg)