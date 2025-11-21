# Managing ZSDK Private Service Edges
Source: https://help.zscaler.com/zsdk/managing-zsdk-private-service-edges
PDF: https://help.zscaler.com/pdf/com/en/1520941.pdf

When ZSDK Private Service Edges are added, you allow users to connect to them to access private resources. To maintain your Private Service Edges, ZSDK allows you to edit or delete them as needed when they need to be reused or removed from use, respectively.
To manage your Private Service Edges on the Private Service Edges page (Configuration & Control > Private Infrastructure > Private Service Edge Management > Private Service Edges), you can:
- [Add a Private Service Edge.](#Add)
- [Edit a Private Service Edge.](#Edit)
- [Delete a Private Service Edge.](#Delete)
The [Private Service Edge must be deployed ](/zpa/about-deploying-service-edges)to appear on the Private Service Edges page.
Considerations & Limitations
When configuring Private Service Edges:
- You can have up to 100 Private Service Edges. To learn more, see [Ranges & Limitations](/zsdk/ranges-limitations#privateserviceedge).
- If the location of the Private Service Edge group is updated for an existing connection, the Public Service Edge uses the old location until the next time it makes a new connection. Location changes via a GeoIP configuration override are not supported for Private Service Edges.
[]
-
Click **Add **to create a Private Service Edge.
The **Add Private Service Edge** window appears.
- In the **Add Private Service Edge** window:
- [a. Choose Key](#ChooseKey)
- [b. Signing Certificate](#SigningCertificate)
- [c. Private Service Edge Group](#PrivateServiceEdgeGroup)
- [d. Create Provisioning Key](#CreateProvisioningKey)
- [e. Review](#Review)
- [f. Review Documentation](#ReviewDocumentation)
After a Private Service Edge is added, you must [deploy the Private Service Edge](/zpa/about-deploying-service-edges). After deployment, the created Private Service Edge appears on the [Private Service Edges page](/zsdk/about-zsdk-private-service-edges).
[]
A provisioning key is a secure and randomly generated string that is required when you deploy the Private Service Edge on a mobile application. Each key acts as an ID that is associated with a specific Private Service Edge.
On the **Choose Key** tab, choose one of the following:
- [Choose an Existing Provisioning Key](#ChooseKey-Existing)
- [Create a New Provisioning Key](#ChooseKey-Create)
[]
-
Select an existing provisioning key from the drop-down menu. You can click **Clear Selection** to reset your selection.
[See image.](#IMG_ChooseKey-Existing)
- Click **Next** to go to the [Review Documentation](#SkipReviewDocumentation) step.
[][]
Click **Next**.
[See image.](#IMG_ChooseKey-Create)
[]
![Choose an existing provisioning key](/downloads/zsdk/private-service-edge/managing-zsdk-private-service-edges/ZSDK-AddPrivateServiceEdge-1ChooseKey-Existing.png)
[]
![Create a new provisioning key](/downloads/zsdk/private-service-edge/managing-zsdk-private-service-edges/ZSDK-AddPrivateServiceEdge-1ChooseKey.png)
[]
-
Select the type of enrollment certificate (preloaded or uploaded) for the Private Service Edge. The certificate that is used to enroll the Private Service Edge must have the same root certificate that the enrollment certificate used for enrolling App Connectors and Zscaler Client Connector.
The preloaded certificates are:
- **Root**: The root (i.e., parent) certificate for the Client or Connector signing certificates.
-
**Client**: A signing certificate that can be used for enrollment certificates issued to Zscaler Client Connector. The certificate's trust is established by the Zscaler public key infrastructure (PKI).
Its parent certificate is the Zscaler Root certificate. ZSDK automatically uses this to sign certificates issued to Zscaler Client Connector, unless you configure another Zscaler-issued certificate.
- **Connector**: A signing certificate that can be used for enrollment certificates issued to Zscaler Client Connectors. The certificate’s trust is also established by the Zscaler PKI.
- **Service Edge**: A signing certificate that can be used for enrollment certificates issued to Private Service Edges.
[See image.](#IMG_SigningCertificate)
These signing certificates are 2,048-bit key RSA certificates, which support TLS 1.2 connections (with cipher suite ECDHE-RSA-AES128-GCM-SHA256).
- Click **Next**.
[]
![Select a certificate to enroll your Private Service Edge](/downloads/zsdk/private-service-edge/managing-zsdk-private-service-edges/ZSDK-AddPrivateServiceEdge-2SigningCertificate-1.png)
[]A Private Service Edge group allows you to group together similar Private Service Edges to permit access to your mobile applications.
On the **Private Service Edge Group** tab, select one of the following options:
- [Select Private Service Edge Group](#PrivateServiceEdgeGroup-Select)
- [Add Private Service Edge Group](#PrivateServiceEdgeGroup-Add)
To learn more, see [About ZSDK Private Service Edge Groups](/zsdk/about-zsdk-private-service-edge-groups).
[]
-
Select an existing Private Service Edge group from the drop-down menu. Search for a specific group or click **Clear Selection** to remove any selections. Private Service Edge groups can be associated with multiple provisioning keys. Therefore, a Private Service Edge can be assigned to an existing group with an existing provisioning key.
[See image.](#IMG_PrivateServiceEdgeGroup-Select)
- Click **Next**.
[]
![Select an existing ZSDK Private Service Edge Group](/downloads/zsdk/private-service-edge/managing-zsdk-private-service-edges/ZSDK-AddPrivateServiceEdge-3PrivateServiceEdgeGroup.png)
[]
-
Enter the following information:
- **Name**: Enter a name for the group. The name cannot contain special characters, except for periods (.), hyphens (-), and underscores ( _ ).
- **Description**: (Optional) Enter a description of the group.
- **Status**: Ensure **Enabled** is selected to start using the group.
- **Publicly Accessible**: Determines whether the Private Service Edge group's specific trusted network mapping is also available publicly for all users outside these trusted networks.
- **Enabled**: Zscaler recommends setting to **Enabled** to ensure the Private Service Edge is reachable over a public IP address if you need remote users to be able to connect to it.
-
**Disabled**: Zscaler recommends setting to **Disabled **if the Private Service Edge has a public IP address or a published IP address set to a public IP address of a Source Network Address Translation (SNAT) such as a firewall.
When you disable **Publicly Accessible** without a trusted network, the IP address of the Private Service Edge is returned to the client for both on-premises and roaming users who are located closest to the Private Service Edge. To mitigate connectivity issues for remote users who want to connect to this Private Service Edge, ensure that the Private Service Edge is reachable over a public IP address.
- **Client Connector Trusted Networks**: Your organization's [trusted networks](/zscaler-client-connector/about-trusted-networks) that are mapped to the Private Service Edge group. Use this option to prioritize Private Service Edges when users connect from those trusted networks.
- **Disaster Recovery**: Enable to designate the Private Service Edge for [disaster recovery](/zsdk/viewing-disaster-recovery). Private Service Edge groups that are designated for disaster recovery bypass the ZSDK cloud to ensure business continuity in the event of a disaster scenario. Disaster recovery is disabled by default.
- **Persist Local Version Profile**: Enable if the Private Service Edge group should persist the local version profile. By default, **Disabled** is selected.
- **Version Profile**: Displays the current version profile. The default value is set to **Default**. To learn more, see [Configuring a Version Profile](/zpa/configuring-version-profile).
- **Private Service Edge Location**: Enter the location where the Private Service Edges in the group are set up. The map displays the location you've entered. After the location marker appears on the map, the **Latitude**, **Longitude**, and **Location Address** fields are then automatically populated.
- **Latitude**: Displays the latitude coordinate.
- **Longitude**: Displays the longitude coordinate.
- **Country Code**: Displays the country code for the location address you’ve entered.
- **Location Details**: Displays the location address you've entered.
[See image.](#IMG_PrivateServiceEdgeGroup-Add)
- Click **Next**.
[]
![Adding a ZSDK Private Service Edge Group](/downloads/zsdk/private-service-edge/managing-zsdk-private-service-edges/ZSDK-AddPrivateServiceEdge-3PrivateServiceEdgeGroup-Add-1.png)
[]If you selected to [create a provisioning key](#ChooseKey-Create-Key), you can configure the following information:
- **Name**: Enter the name of the provisioning key. The name cannot contain special characters, except for periods (.), hyphens (-), and underscores ( _ ).
This name is automatically assigned as a prefix to the name of each Private Service Edge enrolled with it. This means that all Private Service Edges in a given Private Service Edge group use the same prefix in their name. To help distinguish between the different Private Service Edges in a group, each Private Service Edge also has a number automatically added to its name upon being enrolled. This number signifies that it is the nth Private Service Edge to be enrolled with the key. For example, if you enter `AWS Oregon` as a provisioning key name in this step, the first Private Service Edge you enroll with this key is named `AWS Oregon-1`. The next Private Service Edge you enroll with the same key is named `AWS Oregon-2`, and so on.
- **Maximum Reuse of Provisioning Key**: Enter the maximum number of instances where this key can be used to enroll a Private Service Edge. After adding the Private Service Edge, you can modify this number.
Click **Next**.
[See image.](#IMG_CreateProvisioningKey)
[]
![Create a provisioning key to limit the amount of reuse](/downloads/zsdk/private-service-edge/managing-zsdk-private-service-edges/ZSDK-AddPrivateServiceEdge-4CreateProvisioningKey.png)
[]
-
Review the Private Service Edge configuration information.
[See image.](#IMG_Review)
- Click **Save**.
[]
![Review the Private Service Edge information that you have configured](/downloads/zsdk/private-service-edge/managing-zsdk-private-service-edges/ZSDK-AddPrivateServiceEdge-5ReviewDocumentation.png)
[][]You can copy your provisioning key to deploy the Private Service Edge or select to view documentation on how to deploy the Private Service Edge for your platforms.
Click **Done** to save the Private Service Edge configuration.
![Copy the provisioning key or view how to deploy the ZSDK Private Service Edge on a platform](/downloads/zsdk/private-service-edge/managing-zsdk-private-service-edges/ZSDK-AddPrivateServiceEdge-6ReviewDocumentation-1.png)
[]
- Click the **Edit** icon to edit a deployed Private Service Edge's configuration.
-
In the **Edit Private Service Edge** window:
-
**Name**: Edit the name of the Private Service Edge.
If you edit the name, make sure to keep the prefix followed by the number that indicates that this is the nth Private Service Edge to have been deployed with its key. The name cannot contain special characters, except for periods (.), hyphens (-), and underscores ( _ ).
- **Description**: Edit the description of the Private Service Edge.
- **Status**: Enable or disable the Private Service Edge.
-
**Publish IPs or Domains**: Enter the IP addresses or domains that clients and App Connectors use to open a connection to the Private Service Edge. If these are not specified, then the clients and App Connectors try to connect using the Listen IPs.
When to use Publish IPs or domains:
- The primary use case is to specify ZSDK Private Cloud by name and use a DNS to find it.
- The second use case is if the Private Service Edge system is using a static external IP address (e.g., AWS) because the IP address used by clients and App Connectors to connect to the Private Service Edge is not a part of the Private Service Edge.
Click **Add More** to enter another IP address or domain.
-
**Listen IPs**: The interface addresses for the Private Service Edge system that the Private Service Edge listens to for connection requests from clients and App Connectors at set addresses. If not configured, the Private Service Edge automatically listens to all interfaces.
Click **Add More** to enter another IP address.
- **Location**: Indicates where the Private Service Edge's location is.
- **Signing Certificate**: Edit the Private Service Edge certificate.
- **Private Service Edge Group**: Edit the Private Service Edge group.
- **Session Status**: Indicates whether the Private Service Edge is connected or disconnected.
- **Periodic Software Update On**: Indicates when the last periodic software update was.
- **Scheduled Software Version**: Indicates what software version the scheduled update is.
- **Last Software Update On**: Indicates when the last software version update of the Private Service Edge happened.
- **Current Software Version**: Indicates the current software version of the Private Service Edge.
[See image.](#img_edit)
- Click **Save**.
[]
![Edit Private Service Edge configuration fields](/downloads/zsdk/private-service-edge/managing-zsdk-private-service-edges/ZSDK-Private-Service-Edge-Edit.png)
[]
- Click the **Delete** icon** **to begin the deletion of a deployed Private Service Edge.
- Select the checkbox.
- Click **Delete**.
![Confirm ZSDK Private Service Edge deletion](/downloads/zsdk/private-service-edge/managing-zsdk-private-service-edges/ZSDK-Private-Service-Edge-Delete.png)