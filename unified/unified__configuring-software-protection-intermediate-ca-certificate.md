# Configuring Software Protection Intermediate CA Certificate
Source: https://help.zscaler.com/unified/configuring-software-protection-intermediate-ca-certificate
PDF: https://help.zscaler.com/pdf/com/en/1493791.pdf

To configure a Software Protection certificate for your organization during SSL negotiations:
- Go to **Policies **>** Common Configuration **>** SSL/TLS Inspection **> **SSL/TLS Inspection Intermediate Certificate**.
- Click **Add an Intermediate CA Certificate **and select **Software Protection**.
- In the** Add Software Intermediate CA Certificate **window, under the **General** tab:
- **Name**: Enter a name for the certificate.
- **Protection Type**: This field is set to **Software Protection** by default.
- **Region**: This field is set to **Global** by default.
- **Status**: Enable or disable the certificate.
- **Description**: Additional notes or information about the certificate.
- In the **Generate Key Pair** tab, you can view and download your public key pair for the intermediate certificate using the **Download Public Key** at the bottom.
- In the **Generate CSR** tab:
- **CSR File Name: **Enter a name for the Certificate Signing Request (CSR) file.
- **Common Name (CN): **Enter the common name (CN) of your organization, such as `zscaler.com`.
- **Organization: **Enter the name of your organization or company.
- **Department Name: **Enter the name of your department or division.
- **Town/City: **Enter the name of your town/city.
- **Province, Region, County, or State: **Enter the province, region, county, or state where your organization is located.
- **Country: **Enter the country where your organization is located.
- **Key Size: **The key size is set to 2048 by default.
- **Signature Algorithm: **The signature algorithm is set to SHA-256 by default.
- **Path Length Constraint: **Select the path length constraint for the software intermediate certificate. This field can either be set to 0 or 1.
- Click **Generate and** **Save** **New** **CSR**. The CSR certificate is generated.
- Click **CSR for Custom Certificate** to download the file.
After you download the CSR, send it to your CA for signing. Ensure that the CSR is signed as a Subordinate Certification Authority or Intermediate Certification Authority.
If you use OpenSSL, ensure that the following attributes are set during signing:
basicConstraints=CA:TRUE
keyUsage=keyCertSign, cRLSign
To learn more, see [Signing a CSR Using the Active Directory Certificate Services.](/unified/signing-csr-using-active-directory-certificate-services)
-
In the **Upload Intermediate Certificate** tab, browse and upload your intermediate certificate. The file must be in .pem format.
Ensure that your organization’s root certificate is installed on the browsers of your users. Browsers will trust the new intermediate certificate and any certificate signed by it. If you upload a custom certificate that is invalid, for example, and the common name in the certificate does not match, the Zscaler service will not use the Zscaler root certificate. Instead, it will continue to use the previously uploaded self-signed certificate.
You can optionally upload the intermediate certificate chain that includes any other intermediate certificates that complete the chain to the intermediate root certificate you upload. When you upload the certificate chain, the Zscaler service sends the intermediate root certificate along with this key chain and the signed server certificate to your users’ machines during SSL inspection. If you do not upload the certificate chain, the Zscaler service sends only your organization’s intermediate root certificate and its signed server certificate to the user’s machine.
Uploading the certificate chain provides important benefits. The certificate chain ensures that your users’ machines can validate the server certificate signed by your organization’s intermediate CA even if the users’ browsers have only the root certificate in their certificate store.
If you change your certificate due to the compromise of an intermediate root certificate, or simply as a routine security measure, the ability to send the certificate chain to users’ machines during SSL inspection is a key benefit. It enables you to rotate certificates efficiently without the need for a new key ceremony or certificate push to your organization’s users.
You can also replace the intermediate certificate or the intermediate certificate chain for an existing custom certificate. Ensure that the new intermediate certificate is not the default certificate and is associated with an SSL policy.
- In the **Review** tab, review or edit all the information you have entered. Enable the **Default Certificate **option** **to make this certificate as the default intermediate CA certificate.
- Click **Save** and activate the changes.