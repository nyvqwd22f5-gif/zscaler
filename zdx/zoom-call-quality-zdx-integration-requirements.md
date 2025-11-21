# Zoom Call Quality for ZDX Integration Requirements
Source: https://help.zscaler.com/zdx/zoom-call-quality-zdx-integration-requirements
PDF: https://help.zscaler.com/pdf/com/en/1389081.pdf

Review the following Zoom application requirements before configuring and using Zoom Call Quality for Zscaler Digital Experience (ZDX). You must already have a ZDX subscription and ZDX admin access.
Installing Zoom Call Quality from the Zoom App Marketplace
To install Zoom Call Quality for ZDX from the Zoom App Marketplace:
- Sign in to the [Zoom App Marketplace](https://zoom.us/signin).
- Search for **Zscaler Digital Experience**.
- Click **Visit Site to Install**. You are automatically redirected to the following URL to access the ZDX Admin Portal:
https://admin.zdxcloud.net/zdx/login
- Log in to the ZDX Admin Portal and follow the configuration steps provided in [Configuring Zoom Call Quality for ZDX](/zdx/configuring-zoom-call-quality-zdx).
Using Zoom API Scopes
The following Zoom API scopes are used with Zoom Call Quality for ZDX:
| **Name** | **Description** |
| -------- | --------------- |
| dashboard_meetings:read:admin | Required by the Zoom API for meeting data. |
| meeting:read:admin | Required by the Zoom API webhook start and stop meeting notifications. |
| user:read:admin | Required by the Zoom API for user data. |
Zoom Call Quality for ZDX receives webhook notifications from Zoom for your organization when a meeting starts or stops. ZDX then makes periodic Quality of Service (QoS) user API calls to retrieve meeting QoS data and makes the data available via APIs to display on the UI.
Data is captured in real time as a meeting is in progress. User and device information garnered from the API for call participants is mapped to ZDX users and devices. While incremental data is available for calls in progress, complete call data is available approximately 10 minutes after a call has ended.
To learn more, see [Understanding Zoom Call Quality for ZDX](/zdx/understanding-zoom-call-quality-zdx).
Removing Zoom Call Quality from the ZDX Admin Portal
To remove Zoom Call Quality for ZDX from the ZDX Admin Portal:
- Go to **Configuration **>** Applications**.
- Click **Delete** to remove the tenant for Zoom Call Quality.
Removing Zoom Call Quality from the Zoom App Marketplace
To remove Zoom Call Quality for ZDX from the Zoom App Marketplace:
- Sign in to the [Zoom App Marketplace](https://zoom.us/signin).
- Go to **Manage **>** Installed Apps**.
- Click the **Zoom Call Quality for ZDX** app.
- Click **Uninstall**.