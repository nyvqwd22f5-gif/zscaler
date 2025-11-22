# Modifying the Default DNS Control Rule
Source: https://help.zscaler.com/unified/modifying-default-dns-control-rule
PDF: https://help.zscaler.com/pdf/com/en/1516466.pdf

The DNS Control policy has a default rule that allows all DNS traffic. The default rule always maintains the lowest precedence. You can modify its actions, but you cannot delete or duplicate it.
To modify the default DNS Control rule:
- Go to **Infrastructure** > **Connectors** > **Cloud** > **DNS for VM** for Cloud Connector or **Infrastructure** > **Connectors** > **Edge** > **DNS** for Branch Connector.
- Navigate to the default rule and select the **Edit **icon.
- Under **Action**, from **Network Traffic**, select an option for the default rule.
- **Allow**: Allows DNS requests and responses that match the rule.
- **Block**: Silently blocks all DNS requests and responses that match the rule.
- **Resolved by ZPA**: Requests the Cloud or Branch Connector to resolve DNS requests using the IP pool.
- In the **IP Pool **field, you can select the default ZPA IP pool or any other IP pool from the drop-down menu based on your requirement.
- **Redirect Request**: Redirect all DNS requests and responses to a DNS gateway.
- **DNS Gateway**: Select a DNS gateway where requests are redirected.
- Click **Save** and [activate the change](/unified/saving-and-activating-changes-admin-portal).