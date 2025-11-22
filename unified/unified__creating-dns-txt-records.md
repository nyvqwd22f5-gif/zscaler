# Creating DNS TXT Records
Source: https://help.zscaler.com/unified/creating-dns-txt-records
PDF: https://help.zscaler.com/pdf/com/en/1496976.pdf

Disaster Recovery Mode is triggered when you upload the DNS TXT records to the DNS server for the disaster recovery domain name. Zscaler recommends that you are aware of the following:
- If your current epoch time that is configured in the DNS TXT record is between the start (`t`) and end (`x`) times, and has both values inclusive, then disaster recovery is activated if you upload the DNS TXT records to the DNS server for the disaster recovery domain name.
- If your disaster recovery record does not have designated start and end times, then disaster recovery is triggered as soon as you upload the DNS TXT records to the DNS server for the disaster recovery domain name.
- The DNS TXT record assigned to the disaster recovery domain name must be unique.
- Only one DNS TXT record is necessary per unique disaster recovery domain name.
To learn more, see [Understanding Disaster Recovery](/unified/understanding-disaster-recovery) and [About Disaster Recovery Settings](/unified/about-disaster-recovery-settings).
This article describes the steps to create the signed or unsigned DNS TXT records and keys using the Zscaler DNS Record Generator and assumes the user has downloaded and installed the [Zscaler DNS TXT Record Generator](/unified/understanding-and-installing-zscaler-dns-record-generator).
The Zscaler DNS TXT Record Generator is only supported for Windows OS devices, and must be run as an administrator. To run the application as an administrator, right-click the application and select **Run as administrator**.
- [Generate the Signed DNS TXT Records and the Disaster Recovery Key Pairs](#signed)
- [Generate the Unsigned DNS TXT Records and the Disaster Recovery Key Pairs](#unsigned)
[]To generate the signed DNS TXT records and the public key:
- When asked if you want to sign the DNS TXT record name used to trigger disaster recovery, enter `Yes`, and then press `Enter`.
- Enter `Yes`, and then press `Enter` to create a new disaster recovery public key.
The disaster recovery private key is successfully read and written into `Files/dr_privatekey.pem`. The disaster recovery public key is written into `Files/dr_publickey.pem`.
- If Internet & SaaS is not deployed, enter `No`, and then press `Enter.`
- If Internet & SaaS is deployed, enter `Yes`, and then press `Enter`. Proceed to enter one of the following Internet & SaaS forwarding profile values to overwrite the Zscaler Client Connector Portal configuration, and then press `Enter`:
- `Failopen`: The traffic is sent directly.
- `Failclose`: The internet access is disabled.
- To enable disaster recovery, enter one of the following values to set the disaster recovery status for the disaster recovery domain name, and then press `Enter`:
- `On`: Enables the disaster recovery domain name.
- `Off`: Disables the disaster recovery domain name.
- `Test`: Enables Disaster Recovery Test Mode.
- To configure the start time or designated time of disaster recovery:
- Enter `Yes`, and then press `Enter` to start disaster recovery immediately.
- []Enter `No`, and then press `Enter` to configure the designated end time of disaster recovery.
- Enter the designated end time of disaster recovery in Coordinated Universal Time (UTC) using the following format, and then press `Enter`: `years-month-days` `(yyyy-mm-dd)`. For example, `2022-12-01`.
- Enter the designated end time in the following format, and then press `Enter`: `hours-minutes-seconds` `(hh-mm-ss)`. For example, `05-10-55`.
- Confirm the designated end time. If `No` is entered, re-enter the designated end time. If `Yes` is entered, the disaster recovery DNS TXT record is written to the `Files` folder.
The DNS TXT records, private and public keys, and signatures are stored in the `Files` folder. The `Files` folder is located in the folder where the Zscaler DNS Record Generator is downloaded.
- Confirm the start time, designated time, or end time of disaster recovery using the following values, and then press `Enter`:
- `Yes`: Confirms the start time of disaster recovery.
- `No`: Starts the prompt to configure the designated end time. To learn more, see [Step 5b](#step5b).
- `Ignore`: Confirms no end time for disaster recovery.
- Press `Q`, and then press `Enter` to exit the Zscaler DNS Record Generator.
After the signed DNS TXT records and keys are created, upload the public key in the [Disaster Recovery Settings](/unified/about-disaster-recovery-settings) page and when configuring [Zscaler Client Connector Profiles](/client-connector/configuring-zscaler-client-connector-profiles). This is used to trigger Disaster Recovery Mode and is considered a signed disaster recovery activation. For improved security, Zscaler recommends that the signed DNS TXT records are used with the [Zscaler DNS Record Generator](/unified/understanding-and-installing-zscaler-dns-record-generator).
[]To generate the unsigned DNS TXT records:
- When asked if you want to sign the DNS TXT record name used to trigger disaster recovery, press `No`, and then press `Enter`.
- If Internet & SaaS is not deployed, press `No`, and then press `Enter`.
- If Internet & SaaS is deployed, enter `Yes` and then press `Enter`. Proceed to enter one of the following Internet & SaaS forwarding profile values to overwrite the Zscaler Client Connector Portal configuration, and then press `Enter`:
- `Failopen`: The traffic is sent directly.
- `Failclose`: The internet access is disabled.
- To enable disaster recovery for, enter one of the following values to set the disaster recovery status for the disaster recovery domain name, and then press `Enter`:
- `On`: Enables the disaster recovery domain name.
- `Off`: Disables the disaster recovery domain name.
- `Test`: Enables Disaster Recovery Test Mode.
- To configure the start time or designated time of disaster recovery:
- Enter `Yes`, and then press `Enter` to start disaster recovery immediately.
- []Enter `No`, and then press `Enter` to configure the designated end time of disaster recovery.
- Enter the designated end time of disaster recovery in Coordinated Universal Time (UTC) using the following format: `years-month-days` `(yyyy-mm-dd)`. For example, `2022-12-01`.
- Enter the designated end time in the following format: `hours-minutes-seconds` `(hh-mm-ss)`. For example, `05-10-55`.
- Confirm the designated end time. If `No` is entered, re-enter the designated end time. If `Yes` is entered, the disaster recovery DNS TXT record is written to the `Files` folder.
- Confirm the start time, designated time, or end time of disaster recovery using the following values, and then press `Enter`:
- `Yes`: Confirms the start time of disaster recovery.
- `No`: Starts the prompt to configure the designated end time. To learn more, see [Step 4b](#step4b).
- `Ignore`: Confirms no end time of disaster recovery.
- Press `Q`, and then press `Enter` to exit the Zscaler DNS Record Generator.
In the case of an unsigned disaster recovery activation, the public key does not need to be uploaded to the [Disaster Recovery Settings](/unified/about-disaster-recovery-settings) page to activate disaster recovery.