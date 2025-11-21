# Zscaler Authentication Bridge Server Certificate Renewal Process
Source: https://help.zscaler.com/zia/zscaler-authentication-bridge-server-certificate-renewal-process
PDF: https://help.zscaler.com/pdf/com/en/1402261.pdf

A server certificate that is uploaded onto the [Zscaler Authentication Bridge](/zia/about-zscaler-authentication-bridge) (ZAB) will eventually expire. When the certificate expires, it can be renewed using the following method.
- [Step 1: Create a Directory on the ZAB](#Step1)
- [Step 2: Verify that the Files are on the ZAB](#Step2)
- [Step 3: Perform a Test and Validate the New ZAB Server Certificate](#Step3)
- []Create a directory on the ZAB to host the certificate files.
- SCP into the ZAB and copy the certificate files to `var/cacert`.
- Server Certificate - `example.pem`
- Certificate Key - `example.key`
- Root Chain - `example.pem`
- []Validate that the files are copied onto the ZAB.
- During the maintenance window, install the certificate files from the directory. To learn more, see [Deploying a Zscaler Authentication Bridge](/zia/deploying-zscaler-authentication-bridge#cert-signed-trusted-cert-auth).
- Restart the ZAB service and validate the ZAB status.
- []After the new certificate files are uploaded to the ZAB and services are started, establish the SSL connection to the ZAB by using OpenSSL. Validate that the new certificate is being returned by the ZAB and look for the validity period of the certificate returned. Then, get redirected to the ZAB.
- Test the browser and ensure that there are no certificate errors on the ZAB authentication page.
- Configure the browser proxy settings to `gateway.<Zscaler cloud name>.net:9443`* *and add the ZAB hostname to proxy bypass. To learn more, see [What is my cloud name for ZIA?](/zia/what-my-cloud-name-zia) With proxy settings in place, access any internet page to get redirected for authentication. On the Zscaler authentication page, use a dummy `user@domain.com` account to get redirected to ZAB.
- Sign in and validate the new certificate. After clicking **Sign In**, you will be redirected to the ZAB for authentication. Ensure the internet page loads without any certificate errors.
- Validate that the new certificate is being presented on the ZAB authentication page.