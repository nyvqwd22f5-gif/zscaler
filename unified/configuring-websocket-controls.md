# Configuring WebSocket Controls
Source: https://help.zscaler.com/zpa/configuring-websocket-controls
PDF: https://help.zscaler.com/pdf/com/en/1485211.pdf

Within the ZPA Admin Portal, you can add WebSocket Controls to use as part of your [AppProtection profiles](/zpa/about-inspection-profiles). To learn more, see [About WebSocket Controls](/zpa/about-websocket-controls).
To add a new WebSocket control:
- Go to **Configuration & Control **>** Security** > **AppProtection Controls** > **WebSocket Controls**.
- Click **Add WebSocket Controls**.
The **Add WebSocket Control** window appears.
- In the **Add WebSocket Control** window, complete the following steps:
- [Step 1: Control Details](#Tab1)
- [Step 2: Control Definition](#Tab2)
- [Step 3: Severity](#Tab3)
- [Step 4: Review](#Tab4)
- Click **Save**.
- []Enter a name for the WebSocket control. The name cannot contain special characters, with the exception of periods (.), hyphens (-), and underscores ( _ ).
- Select a **Control Type**:
- **Request**
- **Response**
- Choose one of the following control parameters for the selected **Control Type**.
- Request
- **Max Payload Size**
- **Max Fragments Per Message**
- Response
- **Max Payload Size**
- **Max Fragments Per Message**
[See image.](#Step1)
- (Optional) Enter a description.
- Click **Next**.
[]On the **Control Definition** tab, you see the control parameters selected on the **Control Details** tab. There are different required settings to enter depending on what you selected. This lets you define how the ZPA service inspects user traffic.
To set the control:
- For either **Max Payload Size** or **Max Fragments Per Message**, enter the value for that specific parameter. Use the top and bottom arrows if you want to adjust the value.
- For **Control Action**, select how the user traffic is handled for the control parameters selected on the **Control Details** tab:
- **Allow**: The user is allowed to proceed with the control parameters you set.
- **Block**: The user receives a 403 response code for the control parameters you set.
[See image.](#Step2)
- Click **Next**.
- []For Severity, select the severity level for this WebSocket custom control:
- **Critical**: The greatest level of concern.
- **High**: The second greatest level of concern.
- **Medium**: The third greatest level of concern.
- **Low**: The least level of concern.
In addition to severity levels, WebSocket custom controls have a paranoia level of 1 as they are used in an[ AppProtection profile](/zpa/configuring-inspection-profiles#paranoia-execution).
[See image.](#Step3)
- Click **Next**.
[]On the **Review** tab, review the custom control configurations. The details are divided into the general information about the custom control and how the control is defined.
[See image.](#Step4)
[![Selecting Control Details parameters when adding a WebSocket Custom Control in the ZPA Admin Portal](/downloads/zpa/inspection-management/configuring-custom-controls/ConfigWScntrltype.png)
]
[![Defining a Websocket custom control value in the Control Definition tab in the Add WebSocket Custom Control window on the ZPA Admin Portal](/downloads/zpa/inspection-management/configuring-custom-controls/controldeftab.png)
]
[![Severity for a WebSocket custom control when adding a WebSocket custom control in the ZPA Admin Portal](/downloads/zpa/inspection-management/configuring-custom-controls/Severity%20tab.png)
]
[![Review information when creating a WebSocket Custom Control in the ZPA Admin Portal](/downloads/zpa/inspection-management/configuring-custom-controls/Reviewtab.png)
]