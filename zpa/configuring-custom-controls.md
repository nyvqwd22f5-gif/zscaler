# Configuring Custom Controls
Source: https://help.zscaler.com/zpa/configuring-custom-controls
PDF: https://help.zscaler.com/pdf/com/en/1484986.pdf

Within the ZPA Admin Portal, you can add custom controls to use as part of your AppProtection profiles. To learn more, see [About AppProtection Profiles](/zpa/about-appprotection-profiles). For a complete list of ranges and limits for custom controls, see [Ranges & Limitations](/zpa/ranges-limitations#Inspection).
To add a new custom control:
- Go to **Configuration & Control **>** Security **> **AppProtection Controls** > **Custom Controls**.
- Click **Add Custom Controls**.
The **Add Custom Control** window appears.
- In the **Add Custom Control** window, complete the following:
- [Step 1: Select Control Type](#type)
- [Step 2: Set Control Definition](#definition)
- [Step 3: Set Severity and Action](#action)
- [Step 4: Review](#review)
- Click **Save**.
- []Enter a name for the custom control. The name cannot contain special characters, with the exception of periods (.), hyphens (-), and underscores ( _ ).
- Select a **Control Type**:
- **Request**: A message from the client to the server.
- **Response**: A response from the server to the client for the request.
- Choose one or more control parameters for the selected control type, and click **Done**. Click **Select All **to choose all parameters, or click **Clear Selection** to remove all selections.
- Request
- **Request Header**
- **Request Uri**
- **Query String**
- **Request Cookie**
- **Request Body**
- **Request Method**
- Response
- **Response Header**
- **Response Body**
[See image.](#img-controltype)
- (Optional) Enter a description.
- Click **Next**.
[]![Selecting Response Type parameters when adding a Custom Control in the ZPA Admin Portal](/downloads/zpa/inspection-management/configuring-custom-controls/zpa-addcustomcontrol-select-responsetypes.png)
[]On the **Set Control Definition** tab, you see the control parameters selected on the **Select Control Type** tab. There are different required settings to enter depending on what you selected. This lets you define how the ZPA service inspects user traffic.
To set the control:
- For each control parameter, expand to view the required settings.
- Enter the relevant identifying item, if required for the control parameter. For example, if the control parameter is a Request Header, enter the header name.
There is a limit of 2,500 characters for the text field.
- For **Size**, select an operator and enter a value for the control parameter’s size. Click **Add More** if you need additional sizes for this control parameter. There is a 1 MB inspection limit for Request and Response Headers, so only the first 1 MB will be inspected.
If =, >, or < are used once when setting up a custom control, you can’t use it again in the same custom control.
- For **Value**, select an operator and, if required, enter a value for the control parameter’s value:
- **Regex**: A regular expression control parameter that matches the value specified.
- **Does not match Regex**: A regular expression control parameter that does not match the value specified.
- **Contains**: A control parameter that contains the value specified.
- **Does not contain**: A control parameter that does not contain the value specified.
- **Starts with**: A control parameter that starts with the value specified.
- **Does not start with**: A control parameter that does not start with the value specified.
- **Ends with**: A control parameter that ends with the value specified.
- **Does not end with**: A control parameter that does not end with the value specified.
- **Exists**: A control parameter to check if a control type is present. This parameter is available only for Request Header, Request Cookie, Query String, and Response Header.
- **Does not exist**: A control parameter to check if a control type is absent. This parameter is available only for Request Header, Request Cookie, Query String, and Response Header.
Click **Add More** if you need additional values for this control parameter. To learn more about the available Regex values, see [Defining Regular Expression Values](/zpa/defining-regular-expression-values).
[See image.](#img-value)
- For **Request Method**, select from one of the available options:
- **GET**
- **Not GET**
- **POST**
- **Not POST**
- **PUT**
- **Not PUT**
- **PATCH**
- **Not PATCH**
- **CONNECT**
- **Not CONNECT**
- **HEAD**
- **Not HEAD**
- **OPTIONS**
- **Not OPTIONS**
- **DELETE**
- **Not DELETE**
- **TRACE**
- **Not TRACE**
- **CHECKOUT**
- **Not CHECKOUT**
- **COPY**
- **Not COPY**
- **LOCK**
- **Not LOCK**
- **MERGE**
- **Not MERGE**
- **MKACTIVITY**
- **Not MKACTIVITY**
- **MKCOL**
- **NOT MKCOL**
- **MOVE**
- **NOT MOVE**
- **PROPINFO**
- **Not PROPINFO**
- **PROPPATCH**
- **Not PROPPATCH**
- **UNLOCK**
- **Not UNLOCK**
- Repeat the previous steps for each control parameter.
- Click **Show Preview** to review how the controls are expressed.
- Click **Next**.
[]![Defining a custom control value in the Add Custom Control window on the ZPA Admin Portal](/downloads/zpa/inspection-management/configuring-custom-controls/zpa-addcustomcontrol-definition.png)
- []For **Severity**, select the severity level for this custom control:
- **Critical**: The greatest level of concern.
- **High**: The second greatest level of concern.
- **Medium**: The third greatest level of concern.
- **Low**: The least level of concern.
In addition to severity levels, custom controls have a paranoia level of 1 as they are used in an [AppProtection profile](/zpa/configuring-appprotection-profiles).
- For **Action**, select how the user traffic is handled for the control parameters selected on the **Select Control Type** tab and defined on the **Set Control Definition** tab:
- **Allow**: The user is allowed to proceed with the current URL.
- **Block**: The user receives a 403 response code.
- **Redirect**: The user receives a different URL. Enter an alternative URL that the user is redirected to.
[See image.](#img-blockaction)
- Click **Next**.
[]![Severity and action for a custom control when adding a custom control in the ZPA Admin Portal](/downloads/zpa/inspection-management/configuring-custom-controls/zpa-addcustomcontrol-severity-block.png)
[]On the **Review** tab, review the custom control configurations. The details are divided into the general information about the custom control and how the control is defined.
[See image.](#img-review)
[]![Review information when creating a Custom Control in the ZPA Admin Portal](/downloads/zpa/inspection-management/configuring-custom-controls/zpa-addcustomcontrol-review.png)