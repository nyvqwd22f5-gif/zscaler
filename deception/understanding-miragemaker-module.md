# Understanding the Miragemaker Module
Source: https://help.zscaler.com/deception/understanding-miragemaker-module
PDF: https://help.zscaler.com/pdf/com/en/1531560.pdf

The Miragemaker module in Zscaler Deception allows you to configure and manage various ready-to-use resources that are typically used to build and deploy different types of decoys. By default, the Miragemaker module includes preconfigured resources such as datasets, ThreatParse rules, templates, strategies, decoy personalities, banners, and tags. You can also create custom resources based on your business requirements. The various resources that you can configure and manage in the Miragemaker module are as follows:
- [Application Datasets](#zd-miragemaker-application-datasets)
- [SCADA/IoT Datasets](#zd-miragemaker-scada-iot-datasets)
- [Keyword Datasets](#zd-miragemaker-keyword-datasets)
- [Custom Service Datasets](#zd-miragemaker-custom-service-datasets)
- [ThreatParse Rules](#zd-miragemaker-threatparse-rules)
- [File Datasets and Templates](#zd-miragemaker-file-datasets-templates)
- [Strategy Builder](#zd-miragemaker-strategy-builder)
- [Banners](#zd-miragemaker-banners)
- [Tags](#zd-miragemaker-tags)
[]Application datasets are resources used to build and deploy decoy web applications. You can create static, dynamic, or high-interaction web application decoys by deploying the datasets using [Threat Intelligence (TI) decoys](/deception/about-threat-intelligence-decoys) or [web services on network decoys](/deception/configuring-services-network-decoy#configuring-web-service). The following list of application datasets in Miragemaker allows you to create different types of application decoys:
- **Static Application Datasets**: Used to create the front ends of decoy web applications.
- **Vulnerable Application Datasets**: Used to create specific dynamic interactions for decoy web applications.
- **Dynamic Application Datasets**: Used to create dynamic applications by combining appropriate front ends (static application datasets) and dynamic interactions (vulnerable application datasets) for decoy web applications.
- **High-Interaction Container Datasets**: Used to create fully interactive web application decoys based on docker images of real applications.
To learn more about application decoys, see [Understanding Application Datasets](/deception/understanding-application-datasets).
[]SCADA/IoT datasets are resources used to build [network decoys](/deception/configuring-services-network-decoy#configuring-scada-iot-service) that mimic Supervisory Control and Data Acquisition (SCADA) and Internet of Things (IoT) devices used in industrial processes, such as sensors, actuators, and other logical controllers. To learn more, see [About SCADA/IoT Datasets](/deception/about-scada-iot-datasets).
[]Keyword datasets are a set of keywords that can be used to autogenerate recommendations for decoy parameters, such as hostnames, file and folder names, network decoy names, etc. Zscaler uses a proprietary algorithm to randomly generate recommendations for decoy parameters. To learn more, see [Understanding Keyword Datasets](/deception/understanding-keyword-datasets).
[]Custom service datasets are resources that are used to create [custom network services](/deception/configuring-services-network-decoy#configuring-custom-service) that include requests and responses. The custom services are deployed using [network decoys](/deception/about-network-decoys). To learn more, see [About Custom Service Datasets](/deception/about-custom-service-datasets).
[]ThreatParse rules are conditions that are used to parse details of an attack event and translate them into plain English using natural language reconstruction. Deception uses the rules to provide information about an attack event on the [Deception Dashboard](/deception/viewing-and-managing-zscaler-deception-dashboard). To learn more, see [About ThreatParse Rules](/deception/about-threatparse-rules).
[]File datasets and templates are resources that allow you to create decoy files and folders that can be deployed using [network decoy](/deception/about-network-decoys)s or landmine decoys. To learn more, see [About File Datasets](/deception/about-file-datasets) and [About File Templates](/deception/about-file-templates).
[]Strategy Builder allows you to [deploy](/deception/about-deploy-strategy) different types of decoys in your environment with a single click using strategies. The strategies are built using decoy personalities that serve as templates for different types of decoys.
- **Deception Strategy**: A mechanism that combines different decoy personalities to configure and deploy different types of decoys with a single click.
- **Network Decoy Personalities**: A template used to create [network decoys](/deception/about-network-decoys) either manually or via deception strategies.
- **Threat Intelligence Decoy Personalities**: A template used to create [TI decoys](/deception/about-threat-intelligence-decoys) via deception strategies.
- **Landmine Decoy Personalities**: A template used to create [landmine decoys](/deception/about-landmine-decoys) via deception strategies.
- **Active Directory Decoy Personalities**: A template used to create [AD decoys](/deception/configuring-active-directory-decoy-personality) via deception strategies.
To learn more, see [Understanding Strategy Builder](/deception/understanding-strategy-builder).
[]Banners are metadata about services running on a server. These banners are used in [network decoys](/deception/about-network-decoys) configured with [FTP services](/deception/configuring-services-network-decoy#configuring-ftp-service) or [web services](/deception/configuring-services-network-decoy#configuring-web-service) to mimic legitimate services. To learn more, see [Configuring and Managing FTP Banners](/deception/configuring-and-managing-ftp-banners) and[ Configuring and Managing Web Server Banners](/deception/configuring-and-managing-web-server-banners).
[]Tags are used to group various resources across Deception. For example, you can associate tags with personalities and reference them using their tags in [deception strategies](/deception/about-deception-strategy). To learn more, see [Configuring and Managing Tags](/deception/configuring-and-managing-tags).