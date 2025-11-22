# Adding Custom Certificate to an Application Specific Trust Store
Source: https://help.zscaler.com/unified/adding-custom-certificate-application-specific-trust-store
PDF: https://help.zscaler.com/pdf/com/en/1493746.pdf

Whenever Zscaler SSL inspection is enabled to maintain secure connections on the corporate network, admins can use the organization-generated certificate to connect to any secure website. By default, the root and intermediate certificates, which are required to trust the organization's generated certificate, are already added to the end user's system certificate store.
Some applications maintain a custom trust store instead of using the default system trust store. As a result, the application is not able to validate Zscaler-generated server certificates and the TLS connection fails. In such cases, the users need to manually add the custom root CA to the custom trust store, or disable server certificate validation.
You can add custom certificates for the following applications:
If you are an end user, you can get the root CA certificate for your organization from your administrator. If you are an administrator, provide your users with the root CA certificate (i.e., Zscaler root CA certificate or custom root CA certificate) that is applicable to your organization. To learn how to download the Zscaler root CA certificate from the Admin Portal, see [Choosing the CA Certificate for SSL Inspection](/unified/choosing-ca-certificate-ssl-inspection).
- [Snowflake ODBC Driver](#snowflake)
- [Python](#python)
- [NPM](#npm)
- [Linux](#linux)
- [Java](#java)
- [IntelliJ Platform (Jetbrains)](#intellij)
- [Git](#git)
- [Ruby](#ruby)
- [Curl](#curl)
- [Wget](#wget)
- [Docker](#docker)
- [Android Studio](#android)
- [Mozilla Firefox](#firefox)
- [Microsoft Edge](#edge-browser)
[]Data science tools, such as RStudio and PowerBI, can connect to Snowflake's cloud data warehouse using HTTPS. For Snowflake traffic to work seamlessly in any environment over HTTPS in a proxy environment, you must replace the PEM file under `C:\Program Files\Snowflake ODBC Driver\etc` with your custom CA PEM file.
Ensure that you rename your custom PEM file to the same name as that of the PEM file originally present in the location.
[]Different Python modules or installers implement their own certificate stores separately. This section covers the following two modules:
- [PIP](#pip)
- [Requests](#requests)
[]Use one of the following methods to configure the custom CA certificate for Python:
- [Add custom certificate using Bash commands](#pip-add-custome-certificate)
- [Set the SSL_CERT_FILE environment variables](#pip-SSL-cert-file)
- [Patching PIP to use system certificates](#pip-Patching)
- [Installing PIP with certifi package](#pip-certifi-package)
[]To add the custom certificates for PIP to the trust store:
- On macOS and Linux platforms:
- Create or download the certificate bundle in PEM format.
- Create a new directory and move the bundle to the new location using the following Bash commands:
mkdir ~/ca_certs
mv ~/Downloads/custom-ca-bundle.pem ~/ca_certs
- Add the custom certificate using the following Bash command:
pip config set global.cert ~/ca_certs
- On Windows platform:
- Create or download the certificate bundle in PEM format.
- Create a new directory and move the bundle to `C:\` drive.
- Add the certificate to the trust store using the following commands on PowerShell:
mv $env:HOMEPATH\Downloads\custom-ca-bundle.pem $env:APPDATA
pip config set global.cert $env:APPDATA\custom-ca-bundle.pem
[]Run the following commands to set the SSL_CERT_FILE config option:
export CERT_PATH=/etc/ssl/certs/ZscalerRootCA.pem
export CERT_DIR=/etc/ssl/certs/
export SSL_CERT_FILE=${CERT_PATH}
export SSL_CERT_DIR=${CERT_DIR}
export REQUESTS_CA_BUNDLE=${CERT_PATH}
[]You can install the pip-system-certs package, which patches the PIP and the requests at runtime to use certificates from the default system store rather than the bundled certificates CA.
Install the system certificates** **using the following command:
pip install -trusted-host files.pythonhosted.org pip_system_certs
After entering the command, PIP trusts HTTPS sites that are trusted by your host OS. It also trusts all the direct uses of the requests library and the other packages that use requests.
[]Use one of the following methods to configure the CA certificate:
- [Set the cacert.pem config option](#pip-set-cacert)
- [Set the system variables](#pip-set-system-variables)
You cannot add a custom CA certificate using the certifi package option. You can only overwrite it when you update the certifi package.
- []Install the certifi package using the following command:
pip install certifi | pip install --upgrade certifi
- Check for the certificate’s location, `python -m certifi`
- Update the cacert.pem with Zscaler certificate using the following command:
cat ZscalerRootCA.pem >> $(python -m certifi)
You can also set the PIP config global certificate using the following command:
pip config set global.cert $(python -m certifi)
[]Run the following command:
export CERT_PATH=$(python -m certifi)
export SSL_CERT_FILE=${CERT_PATH}
export REQUESTS_CA_BUNDLE=${CERT_PATH}
[]Requests automatically search for any valid certificate in the `REQUESTS_CA_BUNDLE` environment variable.
To configure the `REQUESTS_CA_BUNDLE` environment variable:
- On macOS, run the following Bash command:
echo "export REQUESTS_CA_BUNDLE=<Path to Certificate>/ca-bundle.pem" >> $HOME/.bash_profile
- On Linux, run the following Bash command:
echo "export REQUESTS_CA_BUNDLE=<Path to Certificate>/ca-bundle.pem" >> $HOME/.bashrc
- On Windows, run the following PowerShell command:
[System.Environment]::SetEnvironmentVariable("REQUESTS_CA_BUNDLE", "<Path to Certificate>\ca-bundle.pem", "Machine")
[]Use one of the following methods to configure the custom CA certificate for NPM:
- [Set the cafile config option.](#cafile)
- [Set the NODE_EXTRA_CA_CERTS environment variable.](#env-variable)
[]Run the following command to set the `cafile` config option:
npm config set cafile <Path to Certificate>/ca-bundle.pem
Ensure that the PEM certificate bundle includes both root and intermediate certificates.
- []On macOS, run the following Bash command:
echo "export NODE_EXTRA_CA_CERTS=<Path to Certificate>\bundle.pem" >> $HOME/.bashrc
- On Windows, run the following PowerShell command:
[System.Environment]::SetEnvironmentVariable("NODE_EXTRA_CA_CERTS", "C:\<Path to Certificate>\ca-bundle.pem", "Machine")
[]On CentOS and a few other Linux-based systems, there is a built-in system command to add self-signed certificates to the trust store.
- [CentOS 6, Fedora, and Red Hat](#centos)
- [Ubuntu/Debian](#ubuntu-debian)
- [OpenSUSE](#opensuse)
- []Copy both root and intermediate certificates as individual files in PEM format into the location, `/etc/pki/ca-trust/source/anchors/`.
- Update the CA store using the following command:
update-ca-trust
- []Copy both root and intermediate certificates as individual files in PEM format into the location,` /usr/local/share/ca-certificates/`.
- Update the CA store using the following command:
sudo chmod 644 <root certificate file path>
- []Copy both root and intermediate certificates as individual files in PEM format into the location,` /etc/pki/trust/anchors/.`
- Update the CA store using the following command:
sudo update-ca-certificates
[]To import a custom certificate for Java:
- Download the certificate bundle in DER format to the `JAVA_HOME/bin` directory using the keytool utility.
To convert a .crt certificate to DER format, use the command, `openssl x509 -in ``<filename.pem>`` -inform pem -out ``<filename.der>`` -outform der`
- Run the following keytool command for your certificate:
keytool  -import  -trustcacerts -alias <certAlias> -file <certFile> -keystore <trustStoreFile>
For example:
keytool  -import  -trustcacerts -alias zscalerrootca -file zscalerrootca.der -keystore $JAVA_HOME/jre/lib/security/cacerts
- You might be prompted to enter a password if you are running the tool for the first time.
- Enter `yes` to confirm.
- Verify if the certificate is imported successfully using the following keytool command:
keytool -list -v -keystore cacerts
To learn more about keytool commands, refer to the [Oracle documentation.](https://docs.oracle.com/javase/8/docs/technotes/tools/unix/keytool.html#keytool_option_importcert)
[]IntelliJ IDEA provides its own storage for trusted certificates for Windows, Linux, and Mac platforms.
- Download the custom certificates (intermediate and root) in PEM format.
- Add the certificate to the trust store based on the instructions provided in the [IntelliJ IDEA documentation](https://www.jetbrains.com/help/idea/settings-tools-server-certificates.html).
[]To add the custom certificate for Git to the trust store on the following platforms:
- [macOS and Linux](#git-macos)
- [Windows](#git-win)
- []Create or download the certificate bundle in PEM format.
- Create a new directory and move the bundle to the new location using the following commands:
mkdir ~/ca_certs
mv ~/Downloads/custom-ca-bundle.pem ~/ca_certs
- Add the certificate to the trust store using the following Git command:
git config --global http.sslcainfo ~/ca_certs/custom-ca-bundle.pem
- []Create or download the certificate bundle in PEM format.
- Create a new directory and move the bundle to the `C` drive using the following commands:
mv $env:HOMEPATH\Downloads\custom-ca-bundle.pem $env:APPDATA
git config --global http.sslcainfo $env:APPDATA\custom-ca-bundle.pem
[]To add the custom certificate for Ruby to the trust store on the following platforms:
- [macOS and Linux](#ruby-macos)
- [Windows](#ruby-windows)
[]Run the following Bash command to set the SSL cert file environment variable:
echo "export SSL_CERT_FILE=<Path to Certificate>/ZscalerRootCA.pem" >> $HOME/.bashrcrun
- []Create or download the certificate bundle in PEM format.
- Run the following PowerShell command to move the bundle to the C drive:
[System.Environment]::SetEnvironmentVariable("SSL_CERT_FILE",
"C:\<Path to Certificate>\ZscalerRootCA.pem", "Machine")
[]Use one of the following methods to configure the custom CA certificate for Curl:
- [Set the cacert config option](#curl-cacert)
- [Set the CURL_CA_BUNDLE environment variable](#curl-CURL_CA_BUNDLE)
- [Set the SSL_CERT_FILE environment variable](#curl-SSL_CERT_FILE)
[]Run the following command to set the `cacert` file config option:
echo "cacert=<Path to Certificate>/ZscalerRootCA.pem" >> $HOME/.curlrc
[]Run the following Bash command:
echo "export CURL_CA_BUNDLE=<Path to Certificate>/ZscalerRootCA.pem" >> $HOME/.bashrc
[]Run the following Bash command:
echo "export SSL_CERT_FILE=<Path to Certificate>/ZscalerRootCA.pem" >> $HOME/.bashrc
[]To add the custom CA certificate for Wget, run the following command to set the `ca_certificate` environment variable:
echo "ca_certificate=<Path to Certificate>/ZscalerRootCA.pem" >> $HOME/.wgetrc
[]On Windows, macOS, and Linux, Docker will use the OpenSSL CA Trust for its connections to allow it to download packages as you instantiate them in your Dockerfile.
After the Dockerfile is loaded and processed, Docker containers make their connections, which need to trust the Zscaler certificate. Therefore, ensure that your Docker container has the Zscaler certificates installed.
You can add the custom CA certificate for Docker by using the following three files. In this example, we assume Zscaler is "in path" for the development environment (developers workstation) but "out of path" for the production environment (e.g., AKS/GKS).
- [Environment Variable File​​​​​​](#docker-env-file)
- [Docker Compose File](#docker-compose-file)
- [Docker File](#docker-file)
[]The environment file (.env) is used to identify if the build is run in a production or development environment.
Create a `docker.env` file with the following command:
BUILD_ENV=production
OR
BUILD_ENV=development
This example sets the variables to be read in the Docker Compose file.
[]The docker compose file (.yaml) reads the BUILD_ENV variables and passes them to the Dockerfile.
Create a `dockercompse.yaml` file with the following command:
version: '3.1'
services:
dotnetconf19:
image: dockersamples/dotnetconf:19
build:
context: .
args:
- BUILD_ENV=${BUILD_ENV:-production}
- CERT_FILE=${CERT_FILE:-/etc/ssl/certs/ca-certificates.crt}
environment:
- BUILD_ENV=${BUILD_ENV:-production}
- CERT_FILE=${CERT_FILE:-/etc/ssl/certs/ca-certificates.crt}
This example reads the docker.env file created previously. If no variable is set for BUILD_ENV, it is assumed to be production. If no variable is set for CERT_FILE, the default is set to be the local certificate store.
[]The docker file installs the certificate for the development environments as it requires all traffic to be inspected. The certificate for the production environment can be installed in Kubernetes and be directed to the internet where inspection is not required or moved to a non-Zscaler customer where the certificate is not installed.
Create a Dockerfile with the following commands:
FROM mcr.microsoft.com/dotnet/core/sdk:3.0.100-preview9 AS builder
#No need to install certificates here - no Internet requests made
WORKDIR /src
COPY src/WebRequests.csproj .
RUN dotnet restore
COPY src/ .
RUN dotnet publish -c Release -o /out WebRequests.csproj
FROM mcr.microsoft.com/dotnet/core/runtime:3.0.0-preview9
#Image runs internet requests over HTTPS - Install Certs if dev environment
#Set ARG BUILD_ENV default = production
ARG BUILD_ENV=production
#Assign the $BUILD_ENV the BUILD_ENV ENV so that it can be accessed
ENV BUILD_ENV $BUILD_ENV
#Add the CA Certificate to the container
ADD src/ZscalerRootCertificate-2048-SHA256.crt /tmp/ZscalerRootCertificate-2048-SHA256.crt
#Use BUILD_ENV variable within the container to copy the CA certificate into the certificate directory and update
RUN if [ "$BUILD_ENV" = "production" ] ; then echo "production env"; else echo
"non-production env: BUILD_ENV"; CERT_DIR=(openssl version -d | cut -f2 -d \")/certs ;
cp /tmp/ZscalerRootCertificate-2048-SHA256.crt $CERT_DIR ; update-ca-certificates ;
fi
#Continue the build where the HTTPS Connections are made
WORKDIR /app
ENTRYPOINT ["dotnet", "WebRequests.dll"]
ENV DotNetBot:Message="docker4theEdge!"
COPY --from=builder /out/ .
The Docker file reads the environment variables and copies the Zscaler root certificate from the source folder. If the build is in a production environment, then it proceeds as usual. If the build is in a development environment, then the location of OpenSSL is determined, and the Zscalerroot certificate is added to the trusted root certificate store and updated.
[]When Android Studio starts, it may detect and report an untrusted certificate error. You can accept to trust the incoming certificate, and add it to the local keystore.
If you are using a Gradle plugin, which is a Java app that runs from the JRE embedded in Studio, you need to add the certificates into the JRE local keystore.
To add the certificate to the JRE local keystore:
- Download the certificate bundle in CER format to the `JAVA_HOME/bin` directory using the keytool utility.
- Run the following keytool command for your certificate:
- On macOS:
keytool -import -trustcacerts -file <Path to Certificate>/ca-abc_111.cer -alias custom-Root-CA -keystore /Applications/Android\ Studio.app/Contents/jbr/Contents/Home/lib/security/cacerts
keytool -import -trustcacerts -file <Path to Certificate>/ca-abc_222.cer -alias custom-Intermediate-CA -keystore /Applications/Android\ Studio.app/Contents/jbr/Contents/Home/lib/security/cacerts
- On Windows:
cd "\Program Files\Android\Android Studio\jre\bin"
keytool -import -trustcacerts -file <Path to Certificate>/ca-abc_111.cer -alias custom-Root-CA -keystore ..\jre\lib\security\cacerts
keytool -import -trustcacerts -file <Path to Certificate>/ca-abc_222.cer -alias custom-Intermediate-CA -keystore ..\jre\lib\security\cacerts
Ensure that you specify the full path to the Android Studio Keystore.
- You may be prompted to enter a password if you are running the tool for the first time.
- Enter `yes` to confirm.
- Verify if the certificate is imported successfully using the following keytool command:
keytool -list -v -cacerts
To learn more about keytool commands, refer to the [Oracle documentation.](https://docs.oracle.com/javase/8/docs/technotes/tools/unix/keytool.html#keytool_option_importcert)
- [][Deploy custom certificate to the Mozilla Firefox browser](#deploy-custom-certificate-mozilla-firefox-browser)
- [Configure Mozilla Firefox settings to automatically add the custom certificate](#configure-mozilla-firefox-settings)
[]To deploy the Zscaler root certificate to the Mozilla Firefox browsers of your users:
- [1. Import the certificate into the Firefox browser of a user.](#importing-cert)
- [2. Copy the certificate into the users' Firefox profiles to automatically install the Zscaler root certificate.](#coping-cert)
[]The Firefox profile includes a `cert#.db` file, where # indicates the version number of the .db file that is available with your Firefox profile. This file contains all the security certificates installed on the browser. Installing the Zscaler root certificate in the browser automatically updates the `cert#.db` file with the newly installed certificate.
To import the certificate:
- Open the Mozilla Firefox browser and go to **Options** by clicking the** gear** icon.
- Go to **Privacy & Security**, then** **scroll down to the **Certificates **section and click **View Certificates...**.
[See image.](#view-certificate)
- From the **Authorities **tab, click **Import** to browse and select the Zscaler root certificate from your local directory.
[See image.](#authorities-tab)
- After selecting the certificate, click **OK**. The imported certificate is automatically stored in the Application Data folder, which is hidden by default.
- []In Microsoft Windows, open the **Run** prompt, type `%appdata%`**, **and click** OK**.
[See image.](#run-prompt)
- Navigate to `Mozilla/Firefox/Profiles/xxxxx.default-xxxx/cert#.db`. In this example, the Firefox profile uses the `cert9.db` file.
[See image.](#cert-file)
- Copy this file into the Firefox profiles of your other users.
[]You can configure Mozilla Firefox running version 49 or later to use the Windows root certificate store to automatically import and install SSL root certificates for your user. To learn more, refer to the [Mozilla Firefox documentation](https://wiki.mozilla.org/CA/AddRootToFirefox).
To configure Mozilla Firefox browser settings:
- Open the Mozilla Firefox browser and enter `about:config` in the address bar.
A caution prompt appears.
- Click **Accept the Risk and Continue**.
[See image.](#proceed-caution-message)
- In the search bar, enter `security.enterprise_roots.enabled`.
By default, the value is set to false.
[See image.](#security-settings-false)
- Click the **toggle** icon to set the value to true.
[See image.](#security-settings-true)
[]![Screenshot of Firefox Options page View Certificates button](/downloads/zia/policies/ssl-inspection/deploying-zscaler-certificate-mozilla-firefox-browsers-0/View%20Cerificates.png)
[]![Screenshot of Firefox Certificate Manager window Authorities tab](/downloads/zia/policies/ssl-inspection/deploying-zscaler-certificate-mozilla-firefox-browsers-0/Authorities%20tab.png)
[]![Screenshot of Windows Run prompt](/downloads/zia/policies/ssl-inspection/deploying-zscaler-certificate-mozilla-firefox-browsers-0/Win%20Run%20Prompt.png)
[][![Screenshot of navigating to Firefox cert9.db](/downloads/zia/policies/ssl-inspection/deploying-zscaler-certificate-mozilla-firefox-browsers-0/cert%20db%20file.png)
]
[]To import the Zscaler root certificate into the certificate store of Microsoft Edge browser:
- Open the Microsoft Edge browser, click the menu icon on the upper-right corner, and go to **Settings**.
[See image.](#menu)
- Go to **Privacy, search, and services**, then scroll down to the **Security** section and click **Manage certificates**. Alternatively, use the search field to go to the **Manage certificates** option.
[See image.](#manage-cert)
- From the **Trusted Root Certification Authorities **tab** **and click **Import**.
[See image.](#trusted-cert)
- When the **Certificate Import Wizard** appears, click **Next**.
- Browse and select the Zscaler root certificate from your local directory and then click **Next**.
[See image.](#browse-cert)
- Place the Zscaler root certificate in the **Trusted Root Certification Authorities **store and click** Next**.
[See image.](#cert-store)
- Click **Finish **to** **complete the import process. The Zscaler root certificate is successfully imported to the Microsoft Edge browser.
[]![Opening Settings from the Menu option](/downloads/zia/policies/ssl-inspection/adding-custom-certificate-application-specific-trusted-store/ZIA-microsoft-edge-ca-cert-setting-option.png)
[]![Screenshot of the Certificates button](/downloads/zia/policies/ssl-inspection/adding-custom-certificate-application-specific-trusted-store/ZIA-microsoft-edge-ca-cert-settings-page-screenshot.png)
[]![Screenshot of the Import button](/downloads/zia/policies/ssl-inspection/adding-custom-certificate-application-specific-trusted-store/ZIA-microsoft-edge-ca-cert-trusted-root-certification-authorities.png)
[][![Screenshot of the Certificate Import Wizard](/downloads/zia/policies/ssl-inspection/adding-custom-certificate-application-specific-trusted-store/ZIA-microsoft-edge-ca-cert-root-certificate-location.png)
]
[]![Screenshot of selecting certificate store for Zscaler root certificate](/downloads/zia/policies/ssl-inspection/adding-custom-certificate-application-specific-trusted-store/ZIA-microsoft-edge-ca-cert-store-certificate.png)
[]![Screenshot of the Mozilla Firefox browser Proceed with Caution message](/downloads/zia/policies/ssl-inspection/adding-custom-certificate-application-specific-trusted-store/ZIA-adding-cert-caution-message.png)
[]![Screenshot of the Mozilla Firefox browser "security.enterprise_roots.enabled" settings set to false](/downloads/zia/policies/ssl-inspection/adding-custom-certificate-application-specific-trusted-store/ZIA-adding-cert-value-false-image.png)
[]![Screenshot of the Mozilla Firefox browser "security.enterprise_roots.enabled" settings set to true](/downloads/zia/policies/ssl-inspection/adding-custom-certificate-application-specific-trusted-store/ZIA-adding-cert-value-true.png)