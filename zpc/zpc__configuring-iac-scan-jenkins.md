# Configuring IaC Scan for Jenkins
Source: https://help.zscaler.com/zpc/configuring-iac-scan-jenkins
PDF: https://help.zscaler.com/pdf/com/en/1392426.pdf

This article provides step-by-step instructions for integrating the Zscaler IaC Scan plugin with Jenkins.
The IaC Scan plugin scans and identifies security misconfigurations and policy violations in the IaC Terraform, Kubernetes, Helm, ARM, and CloudFormation templates for both freestyle and pipeline jobs in Jenkins, and displays the scan results within the code.
Prerequisites
The administrator must install and authorize the Zscaler IaC Scan plugin on Jenkins to access the code repositories. Jenkins version 2.319.1 is required for this installation.
Ensure you use the [supported operating systems](/zpc/supported-os-versions-iac-scanning) only, otherwise the IaC integration fails.
Download the Zscaler IaC Scan plugin from the [Jenkins Marketplace](https://plugins.jenkins.io/zscaler-iac-scan/) and install it on Jenkins. To learn more about installing plugins, see the [Jenkins documentation](https://www.jenkins.io/doc/book/managing/plugins/).
Configuring the Zscaler IaC Scan Plugin for Jenkins
To configure the Zscaler IaC Scan plugin for Jenkins:
- After you've installed the plugin from the [Jenkins Marketplace](https://plugins.jenkins.io/zscaler-iac-scan/), log in to the Zscaler Posture Control (ZPC) Admin Portal.
- Go to **Administration**** **> **Version Control & CI/CD Systems**.
- On the **IaC Integrations **page, click **Add IaC Integration**.
[See image.](#jenkins)
- Under **General Information**:
- For **IaC Scanner Type**, select **CI/CD**.
- For **Platform**, select **Jenkins**.
[See image.](#select-j)
- Click **Next**.
- Under **Configuration**:
- Enter the local identifier for your Jenkins server, then click **Confirm**. Enter a unique name. For example, you can provide the name of your organization, Jenkins job, or a repository.
- Copy the **Client ID** and **Client Secret Key** that are generated. Make sure to copy and save these values as they are displayed only once. These values are required to establish a connection between the Jenkins server and the ZPC service.
- Click **Finish**.
[See image.](#configure)
The Jenkins account is displayed on the **Version Control & CI/CD Systems** page, but the status of this account is shown as *Pending*.
[See image.](#pending)
- [Complete the configuration on the Jenkins user interface (UI).](#jenkins-config)
After you complete the configuration, the status changes to *Success* and the Jenkins URL is displayed for the account.
- []Sign in to the Jenkins Web UI.
- Go to **Manage Jenkins > Configure System**.
- Under **Zscaler IaC plugin Configuration**:
- **Choose Environment**: Select the environment (EU or US) where your tenant resides.
- **Credential**: Click **Add**, then select **Jenkins**.
[See image.](#region)
- In the **Add Credentials** window, for **Domain**, select **Global Credentials (unrestricted)**.
- For **Kind**, select **Username with password**.
- For **Scope**, select **Global (Jenkins, nodes, items, all child items, etc.)**.
- For **Username**, paste in the client ID that you copied in step 6b.
- For **Password**, paste in the client secret key that you copied in step 6b.
- For **ID**, provide a name for the credential.
- (Optional) Add a **Description** for the credential.
- Click **Add**.
[See image.](#credential-details)
The **Credential **field under **Zscaler IaC plugin Configuration** is populated with a value.
- Click **Validate**.
A message is displayed indicating that the connection between the Jenkins server and the ZPC Admin Portal is established.
- Click **Save**.
Configuring a Zscaler IaC Scan Job for Jenkins
You can configure the Zscaler IaC Scan plugin to scan a freestyle job or a pipeline job in Jenkins.
- [Configure a Jenkins freestyle job.](#freestyle)
- [Configure a Jenkins pipeline job.](#pipeline)
- []On the Jenkins Dashboard, go to **PA Freestyle**.
- Select **Configure **from the left-side navigation.
- On the **Build Triggers** tab, under **Build Environment**:
- Select **Zscaler IaC Scan**.
- Make sure that **Fail Build** is selected. This option is enabled by default and the IaC Scan plugin fails the job if it identifies high severity violations in the IaC template. If you disable this option, the IaC Scan plugin continues to identify security misconfigurations in the template, but it will not fail the job.
[See image.](#fail-build)
- Click **Save** and **Apply**.
The IaC Scan plugin triggers a scan whenever a build is submitted for deployment, detects misconfigurations and policy violations, and displays the scan results within the code. It also generates a report with the summary of the scan results for the Jenkins job. To learn more, see [Viewing Jenkins Scan Results](/zpc/viewing-iac-scan-results-jenkins-ui).
- On the Jenkins Dashboard, select **Zscaler IaC Scan Results** to view the [graphical report](/zpc/viewing-iac-scan-results-jenkins-ui).
- Click **Export CSV **or **Export PDF **to export the IaC scan results in the required format.
The ZPC service generates alerts for the specific IaC policy violations detected during the scan. You can view the alert and policy violation details on the Alerts page. To learn more, see [About Alerts](/zpc/about-alerts).
- []Go to the Jenkins Dashboard.
- Select the required pipeline project where you want to enable the IaC scanning.
- Select **Configure** from the left-side navigation.
- On the **Pipeline** tab, select **Pipeline script** from the drop-down menu.
- In the **Script** field, add the following step to enable IaC Scan for pipeline projects. By default, Zscaler IaC scan plugin performs a scan of the entire Jenkins repository. In case you want to scan only a specific file or directory, then provide either the file path or directory path, but not both at the same time.
stage('Zscaler IaC scan') {
steps{
wrap([$class: 'ZscalerScan', failBuild: true, file_path: path of file, dir_path: path of the dir]) {
}
}
}
When you set the `failBuild` value to '`true`', then IaC scan will fail the build if there are policy violations. However, if you set the `failBuild` value to '`false`', then IaC scan will not fail the build even if there are policy violations.
- Click **Save** and **Apply**.
[![Add a Jenkins integration](/downloads/zpc/iac-integrations/cicd-tools/configuring-iac-scan-jenkins/zpc-jenkins.png)
]
[![Select Jenkins as the CICD platform](/downloads/zpc/iac-integrations/cicd-tools/configuring-iac-scan-jenkins/zpc-select-jenkins.png)
]
[![Configure IaC Scan for Jenkins](/downloads/zwp/administration/integrations/iac-integrations/configuring-iac-scan-jenkins/zwp-jenkins-config1.png?1650906227)
]
[![Status shows as pending for the Jenkins account](/downloads/zwp/administration/integrations/iac-integrations/configuring-iac-scan-jenkins/zwp-jenkins-pendingstate.png)
]
[![Select the region where your tenant resides](/downloads/zpc/iac-integrations/cicd-tools/configuring-iac-scan-jenkins/zpc-region-jenkins.png)
]
[![Add the credential details for Jenkins](/downloads/zwp/administration/integrations/iac-integrations/configuring-iac-scan-jenkins/zpc-add-jenkins-credentials.png)
]
[![Select the fail build option for IaC scan](/downloads/zwp/administration/integrations/iac-integrations/configuring-iac-scan-jenkins/zpc-jenkins-buildenv.png)
]