# Moving Resources from a Microtenant
Source: https://help.zscaler.com/zpa/moving-resources-microtenant
PDF: https://help.zscaler.com/pdf/com/en/1485741.pdf

Resources can be moved from one Microtenant to another. The following resources can be moved:
- [Defined application segments](#DefinedApplicationSegments)
- [Privileged credentials](#PrivilegedCredentials)
[]
Prior to moving a defined application segment to another Microtenant, the following prerequisites must be met:
- The target segment group and server group associated to the application segment must be configured.
- The associated policy must be deleted.
To move a defined application segment:
- Go to **Resource Management **> **Application Management** > **Application Segments** > **Defined Application Segments**.
- In the table, locate the application segment you want to move and click the **Move** icon. The **Move to Microtenant** window appears.
The **Move **icon is only visible if there are one or more Microtenants available.
-
In the **Move to Microtenant** window:
- Review the application segment name to confirm it is the one you want to move.
-
Select the [Microtenants](/zpa/about-microtenants) from the **Microtenant** drop-down menu that the application segment will be moved to. After you select the Microtenants, the **Segment Group** and **Server Group** drop-down menus appear.
If you are using a Microtenant, the only **Microtenant** option to move your application segment to is **Default**.
- Select the **Segment Group** from the drop-down menu that the application segment will be moved to.
- Select the **Server Group** from the drop-down menu that the application segment will be moved to.
![The Move to Microtenant window on the Defined Application Segment page within the ZPA Admin Portal](/downloads/zpa/documentation-knowledgebase/applications/application-segments/moving-defined-application-segments/Updated%20Move%20window.png)
- Click **Save**.
The ability to move a defined application segment is also available using the ZPA cloud service API. To learn more, see [Configuring Application Segments Using API](/zpa/configuring-application-segments-using-api#MicrotenantMoving).
[]Prior to moving a privileged credential, the associated privileged credential policy must be deleted.
To move a privileged credential:
- Go to **Resource Management** > **Privileged Remote Access** > **Privileged Credentials**.
- In the table, locate the privileged credential you want to move and click the **Move **icon. The **Move to Microtenant** window appears.
The **Move **icon is only visible if there are one or more Microtenants available.
-
In the **Move to Microtenant** window:
- Review the privileged credential name to confirm it's the one you want to move.
- Select the Microtenants from the **Microtenant** drop-down menu that the privileged credential will be moved to.
![Move to Microtenant window](/downloads/zpa/documentation-knowledgebase/applications/application-segments/moving-defined-application-segments/zpa-move-to-microtenant-privileged-credential.png)
- Click **Save**.
The ability to move a privileged credential is also available using the ZPA cloud service API. To learn more, see [Configuring Privileged Credentials Using API](/zpa/configuring-privileged-credentials-using-api#moveCredential).
Zscaler recommends you are aware of the following when moving a resource from one Microtenant to another:
- Browser Access on an application segment does not persist if the application segment is moved from the Default Microtenant to another Microtenant. You must select the web server certificate after the application segment is moved.
- Moving an application segment that is referenced in a privileged approval is not supported.
- Moving an application segment is not supported if the Privileged Remote Access-enabled application associated with the application segment is used in the privileged console.