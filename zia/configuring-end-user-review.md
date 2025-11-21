# Configuring End User Review
Source: https://help.zscaler.com/zia/configuring-end-user-review
PDF: https://help.zscaler.com/pdf/com/en/1450436.pdf

The End User Review is a type of Automated Workflow in 3rd-Party App Governance that allows you to maintain a leaner and more secure App Inventory, while engaging users in application governance.
In the review process, users [confirm via Slack or email](#confirm-slack-email) if they are using the apps currently enabled for them. Based on their response, their access to the app is either automatically revoked or maintained, and their [response is recorded](#recorded-user-activity) as a User Activity in 3rd-Party App Governance.
Initiating End User Reviews
You can initiate an end user review for all users or individual users of a connected app.
- [End User Review for All Users](#end-review-all-users)
- [End User Review for Individual Users](#end-user-review-individual-users)
[]Responding to End User Review Requests
Depending on your configuration, users receive requests to review their app usage either via Slack message or email.
- [End User Review Request via Slack](#responding-review-request-slack)
- [End User Review Request via Email](#responding-review-request-email)
Depending on the platform (e.g., Google), access to the app can be automatically revoked. For example, if an individual user confirms the app is not in use and the platform supports the Revoke action, individual user access is automatically revoked. If all users of an app each confirm that the app is not in use and the platform supports the Revoke action, then access is automatically revoked and the App Status changes to `Deleted` in the App Inventory. To learn more, see [Revoking and Banning Apps](/zia/revoking-banning-apps).
[]Reviewing End User Review Responses
After users submit their responses, the responses are recorded in the Activities tab of the App Panel and User Panel, as well as the Audit Log. To see user responses as they are received, enable the `User Responded to App Review `policy and configure notifications. To learn more, see [3rd-Party App Governance Policies](/zia/3rd-party-app-governance-policies).
- [End User Review Response in the Activities Tab](#end-user-review-response-activity-tab)
- [End User Review Response in the Audit Log](#end-user-review-response-audit-log)
[]You can initiate an end user review for all users in the App Inventory or the App Panel header.
- [Initiate an End User Review in the App Inventory](#end-user-review-app-inventory)
- [Initiate an End User Review in the App Panel Header](#end-user-review-app-panel)
[]To initiate an end user review:
- In the left-side navigation, go to **Inventory**.
- In the App Inventory, go to the** Automated Workflow** column for the app.
You can update the Automated Workflow of multiple apps at the same time. To learn more, see [Taking Bulk Actions on Apps](/zia/taking-bulk-actions-on-apps).
- In the drop-down menu, select **End User Review**.
[See image.](#img-end-user-review-app-inventory)
A review window appears.
- In the review window:
- (Optional) Add a note to share with users in the request for review.
- Choose whether to send the request for review to users via Slack or email.
- Click **Review**.
[See image.](#img-end-user-review-summary)
[]To initiate an end user review:
- Select the app.
The App Panel opens.
- In the **Automated Workflow **drop-down menu, located in the App Panel header, click **End User Review**.
[See image.](#img-end-user-review-app-panel)
A review window appears.
- In the review window:
- (Optional) Add a note to share with users in the request for review.
- Choose whether to send the request for review to users via Slack or email.
- Click **Review**.
[See image.](#img-app-panel-end-user-review-summary)
[]You can initiate an end user review for individual users on the Access tab in the App Panel or User Panel.
- [Initiate an End User Review in the App Panel](#end-user-review-access-tab-app-panel)
- [Initiate an End User Review in the User Panel](#end-user-review-access-tab-user-panel)
[]From the Access tab in the App Panel:
- Select the app.
The App Panel opens.
- Click the **Access** tab.
[See image.](#img-app-panel-access-tab)
- Under **Authorized User Accounts**, click the ellipsis menu next to the user, then click **Ask User to Review**.
[See image.](#img-app-panel-ask-user-to-review)
A review window appears.
- In the review window:
- (Optional) Add a note to share with users in the request for review.
- Choose whether to send the request for review to users via Slack or email.
- Click **Start Review**.
[See image.](#img-app-panel-start-review)
[]From the Access Tab in the User Panel:
- Select the user.
The User Panel opens.
- In **Access** > **Top** **Apps and User's Permissions**, click the ellipsis menu next to the app, then click **Ask User to Review**.
[See image.](#img-user-panel-ask-user-to-review)
A review window appears.
- In the review window:
- (Optional) Add a note to share with users in the request for review.
- Choose whether to send the request for review to users via Slack or email.
- Click **Start Review**.
[See image.](#img-user-panel-start-review)
[]If you configure the request for review to be sent via Slack, the user receives the following message:
[See image.](#img-end-user-review-slack-message)
The user can submit one of the following responses:
- **I'm using this app**: Access to the app is maintained.
- **I'm not using this app**: Access to the app is revoked.
- **I don't remember installing it**: Access to the app is revoked.
[]If you configure the request for review to be sent via email, the user receives the following email:
[See image.](#img-end-user-review-request-email)
Clicking the **Review** button redirects the user to the form:
[See image.](#img-end-user-review-email)
The user can submit one of the following responses:
- **I'm not using this app**: Access to the app is revoked.
- **I'm using this app**: Access to the app is maintained.
- **I don't remember installing it**: Access to the app is revoked.
[]To view the end user review responses in Activities tab of the App Panel:
- Select the app.
The App Panel opens.
- Click the **Activities** tab.
[See image.](#img-app-panel-activities-tab)
- (Optional) Filter by **User Activity** to narrow your search.
[See image.](#img-app-panel-user-activity)
(Optional) View end user review responses in the User Panel by selecting the user and following the preceding steps.
[See image.](#img-user-panel-user-activity)
[]To view the end user review responses in the Audit Log:
- In the left-side navigation, go to **Audit Log**.
[See image.](#img-audit-log-tab-nav)
- Locate the user activity.
[See image.](#img-audit-log-end-user-review-response)
[]![End-User Review in the App Inventory](/downloads/zia/policies/data-loss-prevention/3rd-party-app-governance/using-3rd-party-app-governance/configuring-end-user-review/End_User_Review.png)
[]![End-User Review configuration window ](/downloads/zia/policies/data-loss-prevention/3rd-party-app-governance/using-3rd-party-app-governance/configuring-end-user-review/Mail_Merge_Review.png)
[]![End-User Review option in the App Panel](/downloads/zia/policies/data-loss-prevention/3rd-party-app-governance/using-3rd-party-app-governance/configuring-end-user-review/End_User_Review_AppPanel.png)
[]![End-User Review configuration window ](/downloads/zia/policies/data-loss-prevention/3rd-party-app-governance/using-3rd-party-app-governance/configuring-end-user-review/Mail_Merge_Review.png)
[]![Screenshot of the Access tab in the App Panel ](/downloads/zia/apptotal/how/general/end-user-review-process/apptotal_app_panel_access_tab.png)
[]![Screenshot of Ask User to Review button on the Access tab in the App Panel](/downloads/zia/apptotal/how/general/end-user-review-process/app_panel_ask_user_review.png)
[]![Screenshot of the End-User Review configuration window for an individual user ](/downloads/zia/apptotal/how/general/end-user-review-process/apptotal_app_panel_end_user_start_review.png)
[]![Screenshot of Ask User to Review button on the Access tab in the User Panel](/downloads/zia/apptotal/how/general/end-user-review-process/user_panel_ask_user_review.png)
[]![Screenshot of the End-User Review configuration window for an individual user in AppTotal.](/downloads/zia/apptotal/how/general/end-user-review-process/apptotal_user_panel_end_user_start_review.png)
[]![Screenshot of the Slack message sent to users in an end-user review.](/downloads/zia/apptotal/how/general/end-user-review-process/end_user_review_slack.png)
[]![Screenshot of End-User Review request sent via email.](/downloads/zia/apptotal/how/general/end-user-review-process/end_user_review_request_email.png?1688757645)
[]![Screenshot of the email sent to users in an end-user review.](/downloads/zia/apptotal/how/general/end-user-review-process/end_user_review_email.png)
[]![Screenshot of the Activities tab in the App Panel](/downloads/zia/apptotal/how/general/end-user-review-process/apptotal_app_panel_activities_tab.png)
[]![Screenshot of the User Activity filter in the App Panel.](/downloads/zia/apptotal/how/general/end-user-review-process/apptotal_app_panel_user_activities_filter.png)
[]![Screenshot of user activities in the User Panel](/downloads/zia/apptotal/how/general/end-user-review-process/apptotal_user_panel_activities_tab.png)
[]![Screenshot of the Audit Log tab in the left-side navigation.](/downloads/zia/apptotal/how/general/end-user-review-process/apptotal_audit_log_nav_button.png)
[]![Screenshot of an End-User Review response in the Audit Log.](/downloads/zia/apptotal/how/general/end-user-review-process/apptotal_end_user_response_audit_log.png)