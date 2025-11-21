# Configuring Services on a Network Decoy
Source: https://help.zscaler.com/deception/configuring-services-network-decoy
PDF: https://help.zscaler.com/pdf/com/en/1531279.pdf

This article describes how to customize the services (Generative AI (Gen AI), Web, SSH, Telnet, SCADA/IoT, FTP, etc.).
To configure services:
- [Stop the decoys](/deception/starting-and-stopping-decoys#stop-decoys).
- Go to **Deceive** > **Network Decoys**.
- Select the **Internal** or **Zero Trust Network **tab.
-
Click **Add Decoys** to create a new decoy, or click the **Edit **icon for an existing decoy.
[See image.](#deception-add-edit-network-decoy)
-
In the **Network Decoy Detail** window, click the **Services **tab and configure the following services:
[See image.](#deception-nw-decoy-services-list)
- [Gen AI](#deception-config-gen-ai-service-network-decoys)
- [Web](#configuring-web-service)
- [Shares](#configuring-shares-service)
- [FTP](#configuring-ftp-service)
- [SSH](#configuring-ssh-service)
- [Telnet](#configuring-telnet-service)
- [Windows](#configuring-windows-service)
- [AMQP, MQTT, MySQL, PostgreSQL, and MongoDB](#enabling-mqtt-mysql)
- [SCADA/IoT](#configuring-scada-iot-service)
- [Custom](#configuring-custom-service)
- [Custom Docker](#configuring-custom-docker-service)
- Click **Submit** to save the configuration.
- [Start the decoys](/deception/starting-and-stopping-decoys#start-decoys).
To disable a service, you can deselect it and click **Submit** to save the changes.
[See image.](#disable-service)
[]
- Enable **GenAI**.
- Under **General**, choose one of the following Gen AI application dataset types from the **Type of Application** drop-down menu:
- [Static](#deception-config-service-gen-ai-static-app-section)
- [High Interaction](#deception-config-service-gen-ai-hi-interaction-app-section)
- [Adaptive](#deception-config-service-gen-ai-adaptive-app-section)
- []**Application Datasets**: Select a Gen AI static application dataset.
-
**Web Server Banner**: Select a banner. You can also click **Create Web Server Type**,** **enter the name of the banner, and then click **Save** to create a banner.
[See image.](#deception-config-service-gen-ai-general-static)
-
Under **Ports**, enter the port number and enable or disable **SSL** for each port per your requirement.
[See image.](#deception-config-service-gen-ai-port-static)
-
(Optional) Under **Certificate Settings**:
- **SSL Certificat**e: Upload an SSL certificate in the privacy-enhanced mail (PEM) format.
-
**SSL Private Key**: Upload an unencrypted SSL private key in the PEM format.
The Zscaler Deception Admin Portal doesn't support encrypted private keys for custom SSL certificates.
- **Favorites Title (Browser Lures)**: Enter a favorite title to be displayed in browser favorites.
- **Cookie Name (Browser Lures)**: Enter a cookie name.
[See image.](#deception-config-service-gen-ai-cert-sett)
-
Under **Response Headers**:
- **Enable Security Headers**: Select to add HTTP security headers, such as X-Content-Type-Options, Referrer-Policy, Permissions-Policy, and Content-Security-Policy to the Gen AI service.
- **Enable HTTP Strict-Transport-Policy Response Header**: Select to add the HTTP Strict-Transport-Security (HSTS) response header to the Gen AI service.
[See image.](#deception-config-service-gen-ai-response-header)
-
Under **Custom Response Headers:**
- Click **Add** to add custom response headers that you can use to manipulate the HTTP response headers. The custom response headers are visible in a browser when an adversary accesses an Internal decoy. Custom headers make the decoy look realistic, so that an adversary engages with the decoy for a longer time.
- Enter the custom header key and value.
[See image.](#deception-config-service-gen-ai-custom-header)
- []**High Interaction Dataset**: Select a Gen AI high-interaction container.
- **Model Name**: Select an AI model name. An AI model is a program trained to identify patterns, process information, and make decisions with little human intervention. You can add model names according to your organization’s use case by configuring Gen AI model names in a [datalist](/deception/configuring-and-managing-datalists).
-
**System Prompt**: Edit the text per your requirements. The system prompt outlines the chatbot's behavior and provides initial instructions to guide its responses. Deception provides a default system prompt and automatically retrieves some details. For example, the customer's name is automatically populated, and if ZPA is enabled for a customer, the domain names configured in the ZPA Admin Portal are automatically populated.
[See image.](#deception-config-service-gen-ai-hi-general)
- Under **Decoy Type**, choose one of the following decoy types to customize the decoy:
-
Select **API** to use APIs that are fully compatible with OpenAI specifications. Optionally, enable **Authentication**. When enabled, adversaries can leverage decoy credentials deployed via [browser lures](/deception/configuring-browser-lures-module) or [file decoys](/deception/configuring-file-decoys-module#credential-file-decoys) to authenticate the API, and then use the returned bearer token to access other APIs that provide functionalities such as chat completion and model retrieval.
[See image.](#deception-config-service-gen-ai-hi-api-type)
- Select **UI** to configure the decoy user interface (UI).
- (Optional) Enable **Authentication**.
-
Under **Customize Theme**:
- **Mode**: Select **Light** or **Dark** to configure the background theme for the UI.
- **Header Color**: Select a color for the header, or enter a hexadecimal color code and click **Add** to include it in the palette. If you add multiple custom colors, only the last selected and saved color is applied and persists. When you close and reopen the modal, the palette displays the default colors along with the last selected and saved custom color.
- **Icon Color**: Enter a hexadecimal color code for the **Edit** icon.
- **Brand Name**: Enter the company or brand name to display.
- **Brand Color**: Enter a hexadecimal color code to configure the color for the company or brand name.
- **SVG Icon**: Upload a company or brand logo in SVG format.
[See image.](#deception-config-service-gen-ai-hi-config-theme)
-
Click **Preview** to review your customizations before deploying the decoy.
[See image.](#deception-config-service-gen-ai-hi-config-preview)
If **Authentication** is enabled and the decoy is deployed, then adversaries are required to access the decoy via a login page using credentials deployed via [browser lures](/deception/configuring-browser-lures-module) or [file decoys](/deception/configuring-file-decoys-module#credential-file-decoys).
[See image.](#deception-config-service-gen-ai-enter-decoy_credentials)
-
Under **Ports**, enter the port number.
[See image.](#deception-config-service-gen-ai-hi-ports)
-
(Optional) Under **Certificate Settings**:
- **SSL Certificat**e: Upload an SSL certificate in the privacy-enhanced mail (PEM) format.
-
**SSL Private Key**: Upload an unencrypted SSL private key in the PEM format.
The Deception Admin Portal doesn't support encrypted private keys for custom SSL certificates.
[See image.](#deception-config-service-gen-ai-hi-cert-settings)
-
Under **Response Headers**:
- **Enable Security Headers**: Select to add HTTP security headers, such as X-Content-Type-Options, Referrer-Policy, Permissions-Policy, and Content-Security-Policy to the Gen AI service.
- **Enable HTTP Strict-Transport-Policy Response Header**: Select to add the HTTP Strict-Transport-Security (HSTS) response header to the Gen AI service.
[See image.](#deception-config-service-gen-ai-hi-response-header)
[]An adaptive Gen AI application is an interactive application that dynamically adjusts to attackers' requests and provides tailored responses using AI. It addresses attacks such as SQL injection, exfiltration of exposed cloud credentials (e.g., `https://``<application server>``/.aws/credentials`), etc., by adapting to the requests and generating contextually appropriate responses that lure attackers into entering various crafted malicious intent requests.
- **High Interaction Dataset**: Select a Gen AI high-interaction container.
-
**Model Name**: Select an AI model name. An AI model is a program trained to identify patterns, process information, and make decisions with little human intervention. You can add model names according to your organization’s use case by configuring Gen AI model names in a [datalist](/deception/configuring-and-managing-datalists).
[See image.](#deception-config-gen-ai-adaptive-app-type)
-
Under **Ports**, enter the port number and enable or disable **SSL** for each port per your requirement.
[See image.](#deception-config-gen-ai-adaptive-ports)
-
(Optional) Under **Certificate Settings**:
- **SSL Certificat**e: Upload an SSL certificate in the privacy-enhanced mail (PEM) format.
-
**SSL Private Key**: Upload an unencrypted SSL private key in the PEM format.
The Deception Admin Portal doesn't support encrypted private keys for custom SSL certificates.
[See image.](#deception-config-gen-ai-adaptive-ssl-cert)
-
Under **Response Headers**:
- **Enable Security Headers**: Select to add HTTP security headers, such as X-Content-Type-Options, Referrer-Policy, Permissions-Policy, and Content-Security-Policy to the Gen AI service.
- **Enable HTTP Strict-Transport-Policy Response Header**: Select to add the HTTP Strict-Transport-Security (HSTS) response header to the Gen AI service.
[See image.](#deception-config-gen-ai-adaptive-response-headers)
-
Under **Custom Response Headers:**
- Click **Add** to add custom response headers that you can use to manipulate the HTTP response headers. The custom response headers are visible in a browser when an adversary accesses an Internal decoy. Custom headers make the decoy look realistic, so that an adversary engages with the decoy for a longer time.
- Enter the custom header key and value.
[See image.](#deception-config-gen-ai-adaptive-custom-response)
[]
- Enable **Web**.
- Under **General**, choose one of the following web application types from the **Type of Application** drop-down menu:
- [Static](#deception-nw-service-web-static-section)
- [Dynamic](#deception-nw-service-web-dynamic-section)
- [High Interaction](#deception-nw-service-web-hi-int-section)
-
Under **Ports**, enter the port number and enable or disable **SSL** for each port per your requirement.
[See image.](#configure-port-web-service)
-
(Optional) Under **Certificate Settings**:
- **SSL Certificat**e: Upload an SSL certificate in the privacy-enhanced mail (PEM) format.
-
**SSL Private Key**: Upload an unencrypted SSL private key in the PEM format.
Deception Admin Portal doesn't support encrypted private keys for custom SSL certificates.
- **Favorites Title (Browser Lures)**: Enter a favorite title to be displayed in browser favorites.
- **Cookie Name (Browser Lures)**: Enter a cookie name.
[See image.](#configure-certificate-browser-lures-web-service)
-
Under **Response Headers**:
- **Enable Security Headers**: Select to add HTTP security headers, such as X-Content-Type-Options, Referrer-Policy, Permissions-Policy, and Content-Security-Policy to the Gen AI service.
- **Enable HTTP Strict-Transport-Policy Response Header**: Select to add the HTTP Strict-Transport-Security (HSTS) response header to the Gen AI service.
[See image.](#deception-enable-security-headers-web-service)
-
Under **Custom Response Headers**:
- Click **Add** to add custom response headers that you can use to manipulate the HTTP response headers. The custom response headers are visible in a browser when an adversary accesses an Internal decoy. Custom headers make the decoy look realistic, so that an adversary engages with the decoy for a longer time.
- Enter the custom header key and value.
[See image.](#deception-config-custom-headers-web-service)
- []**Application Dataset**: Select a static dataset from the drop-down menu.
-
**Web Server Banner**: Select a banner. You can also click **Create Web Server Type**, enter the name of the banner, and then click **Save** to create a banner.
[See image.](#configure-static-web-service)
- []**Dynamic Dataset**:** **Select a dynamic dataset from the drop-down menu.
-
**Server Type**:** **Select a server. You can also click **Create Web Server Type**, enter the name of the server, and then click **Save** to create a server.
[See image.](#configure-dynamic-web-service)
-
[]**High Interaction Dataset**: Select a high-interaction dataset from the** **drop-down menu.
[See image.](#configure-high-interaction-container-service)
[]
- Enable **Shares**.
- Enable **Admin$ share** to create an Admin$ shared folder.
- Enable **C$ share** to create a C$ shared folder.
-
Enable **Guest Accessible** to allow access to the shared folder with guest access privileges.
[See image.](#configure-admin-c-shared-folders)
Disable **Guest Accessible** to specify custom user credentials for accessing the shared folder.
[See image.](#deception-configure-shared-folders-custom-creds)
-
Under **File Shares**, click **Add** to add a shared folder:
- **Folder Name**: Enter a folder name.
- **Read Only**: Enable or disable per your requirements.
- (Optional) **Comment**: Enter a comment for your reference.
- **File Dataset**: Select a file dataset. To learn more, see [dynamic](/deception/adding-dynamic-application-dataset) or [static](/deception/adding-static-application-dataset) dataset.
[See image.](#configure-file-shares)
[]
- Enable **FTP**.
- Select an existing FTP banner from the **Banner **drop-down menu, or click **Create FTP Banner**, enter the name of the banner, and then click **Save** to create a new custom banner.
-
Select a preconfigured application or a service you want to deploy on the decoy from the **Pre-configured Application/Service** drop-down menu.
[See image.](#configure-ftp-service)
[]
- Enable **SSH**.
- Select an operating system (OS) from the **Operating System **drop-down menu.
-
In the **Banner** field, enter the text for the decoy. The banner text is visible when the decoy is accessed via SSH.
[See image.](#configure-ssh-service)
[]
- Enable **Telnet**.
- Select an operating system (OS) from the **Operating System **drop-down menu.
-
In the **Banner **field, enter the text for the decoy. The banner text is visible when the decoy is accessed via telnet.
[See image.](#configure-telnet-service)
[]
- Enable **Windows**.
-
Select a Windows virtual machine from the **Virtual Machine **drop-down menu.
[See image.](#configure-windows-service)
[]Enable the respective services and click **Submit **to save the configuration.
No additional configuration is required for these services.
[See image.](#enable-amqp-mqtt-services)
[]
- Enable **SCADA/IoT**.
-
Select an application or service you want to deploy on the decoy from the **Pre-configured Application/Service **drop-down menu.
[See image.](#configure-scada-iot-service)
[]A custom service enables you to add a TCP or UDP port to the network decoy. You can enable multiple TCP and UDP ports on a single network decoy. You can configure a custom service dataset, which includes a customizable banner, request, and response. A custom service dataset mimics network signatures of systems, which use proprietary text or binary-based protocols that run on customized ports.
- Enable **Custom Service**.
- Click **Add**.
- In the **Port** field, enter a port number.
- Choose a protocol from the **Protocol **drop-down menu:
-
Select **UDP**.
[See image.](#configure-custom-udp-service)
- Select **TCP**:
- Select an application dataset from the **Dataset **drop-down menu.
-
Enable or disable **Keep Connection Open** per the decoy application's requirement.
[See image.](#configure-custom-tcp-service)
[]
- Enable **Custom Dockers**.
-
Select a docker dataset from the **Custom Docker Dataset **drop-down menu.
[See image.](#configure-custom-docker)
[]![Add or edit a network decoy](/downloads/deception/deceive/network-decoys/configuring-services-network-decoy/zscaler-deception-access-service-tab-network-decoys.png)
[]![Click the Service tab](/downloads/deception/deceive/network-decoys/configuring-services-network-decoy/deception-network-decoy-services-tab-list-1.png)
[]![Configure Gen AI static application ](/downloads/deception/deceive/network-decoys/configuring-services-network-decoy/zscaler-deception-config-gen-ai-static-general.png)
[]![Configure ports for Gen AI static app](/downloads/deception/deceive/network-decoys/configuring-services-network-decoy/zscaler-deception-config-gen-ai-static-ports.png)
[]![Configure certification settings for Gen Ai static app](/downloads/deception/deceive/network-decoys/configuring-services-network-decoy/zscaler-deception-config-gen-ai-static-certificate-settings.png)
[]![Configure response headers for Gen AI static app](/downloads/deception/deceive/network-decoys/configuring-services-network-decoy/zscaler-deception-config-gen-ai-static-response-header-1.png)
[]![Configure custom response header for Gen AI static app](/downloads/deception/deceive/network-decoys/configuring-services-network-decoy/zscaler-deception-config-gen-ai-static--custom-header.png)
[]![Configure Gen AI high-interaction app](/downloads/deception/deceive/network-decoys/configuring-services-network-decoy/zscaler-deception-config-gen-ai-hi-int-general.png)
[]![Configure ports for Gen AI hi-interaction app](/downloads/deception/deceive/network-decoys/configuring-services-network-decoy/zscaler-deception-config-gen-ai-hi-int-ports.png)
[]![Select API decoy type](/downloads/deception/deceive/network-decoys/configuring-services-network-decoy/deception-gen-ai-service-hi-decoy-type-api-auth.png)
[]![Configure the decoy UI theme](/downloads/deception/deceive/network-decoys/configuring-services-network-decoy/deception-gen-ai-service-hi-decoy-type-ui-auth-1.png)
[]![Preview decoy](/downloads/deception/deceive/network-decoys/configuring-services-network-decoy/deception-gen-ai-service-hi-decoy-preview-4.png)
[]![Access decoy via login page](/downloads/deception/deceive/network-decoys/configuring-services-network-decoy/deception-gen-ai-service-hi-decoy-login-page.png)
[]![Configure certification settings](/downloads/deception/deceive/network-decoys/configuring-services-network-decoy/deception-gen-ai-hi-int-decoy-type-certificate.png)
[]![Configure response headers for Gen AI high interaction decoy](/downloads/deception/deceive/network-decoys/configuring-services-network-decoy/deception-gen-ai-hi-int-decoy-type-response-header.png)
[]![Configure adaptive Gen AI app](/downloads/deception/deceive/network-decoys/configuring-services-network-decoy/itdr-adaptive-gen-ai-app-type-config.png)
[]![Configure adaptive Gen AI app port details](/downloads/deception/deceive/network-decoys/configuring-services-network-decoy/itdr-adaptive-gen-ai-service-port.png)
[]![Configure adaptive Gen AI SSL certificate details](/downloads/deception/deceive/network-decoys/configuring-services-network-decoy/itdr-adaptive-gen-ai-sl-cert.png)
[]![Configure adaptive Gen AI response headers](/downloads/deception/deceive/network-decoys/configuring-services-network-decoy/itdr-adaptive-gen-ai-app-response-header.png)
[]![Configure adaptive Gen AI app custom response headers](/downloads/deception/deceive/network-decoys/configuring-services-network-decoy/itdr-adaptive-gen-ai-app-custom-header.png)
[]![Configure an SSH service](/downloads/deception/deceive/network-decoys/configuring-services-network-decoy/zscaler-deception-configure-ssh-2.png)
[]![Configure a telnet service](/downloads/deception/deceive/network-decoys/configuring-services-network-decoy/zscaler-deception-configure-telnet-2.png)
[]![Configure SCADA and IOT services](/downloads/deception/deceive/network-decoys/configuring-services-network-decoy/zscaler-deception-enable-mqtt-scada-iot-2.png)
[]![Configure an FTP service](/downloads/deception/deceive/network-decoys/configuring-services-network-decoy/zscaler-deception-configure-ftp-2.png)
[]![Configure a UDP protocol](/downloads/deception/deceive/network-decoys/configuring-services-network-decoy/zscaler-deception-config-udp-protocol-2.png)
[]![Configure a TCP protocol](/downloads/deception/deceive/network-decoys/configuring-services-network-decoy/zscaler-deception-config-tcp-protocol-2.png)
[]![Configure Admin$ and C$ share services](/downloads/deception/deceive/network-decoys/configuring-services-network-decoy/zscaler-deception-configure-shares-2.png)
[]![Specify custom user credentials to access the shared folder](/downloads/deception/deceive/network-decoys/configuring-services-network-decoy/deception-shares-service-custom-user-pwd-3.png)
[]![Configure file shares](/downloads/deception/deceive/network-decoys/configuring-services-network-decoy/zscaler-deception-configure-shares-folder-3.png)
[]![Configure a static web application](/downloads/deception/deceive/network-decoys/configuring-services-network-decoy/zscaler-deception-configure-web-static-3.png)
[]![Configure a dynamic web application](/downloads/deception/deceive/network-decoys/configuring-services-network-decoy/zscaler-deception-configure-web-dynamic-4.png)
[]![Configure an high-interaction container application](/downloads/deception/deceive/network-decoys/configuring-services-network-decoy/zscaler-deception-configure-web-hi-int-3.png)
[]![Configure ports for the web application](/downloads/deception/deceive/network-decoys/configuring-services-network-decoy/zscaler-deception-configure-web-ports-3.png)
[]![Configure SSL certificate settings](/downloads/deception/deceive/network-decoys/configuring-services-network-decoy/zscaler-deception-configure-web-certificates-3.png)
[]![Enable response headers for the web service](/downloads/deception/deceive/network-decoys/configuring-services-network-decoy/zscaler-deception-configure-web-response-headers-3.png)
[]![Configure custom response headers](/downloads/deception/deceive/network-decoys/configuring-services-network-decoy/zscaler-deception-configure-web-custom-response-headers-3.png)
[]![Configure a windows service](/downloads/deception/deceive/network-decoys/configuring-services-network-decoy/zscaler-deception-configure-windows-2.png)
[]![Enable AMQP, MQTT, MySQL, PostgreSQL, and MongoDB Services](/downloads/deception/deceive/network-decoys/configuring-services-network-decoy/zscaler-deception-enable-mqtt-mysql-2.png)
[]![Configure custom docker service](/downloads/deception/deceive/network-decoys/configuring-services-network-decoy/zscaler-deception-config-customer-docker-service-2.png)
[]![Disable a service](/downloads/deception/deceive/network-decoys/configuring-services-network-decoy/zscaler-deception-disable-service-2.png)