# Viewing Self Service User Notifications
Source: https://help.zscaler.com/unified/viewing-self-service-user-notifications
PDF: https://help.zscaler.com/pdf/com/en/1495041.pdf

This article consolidates the Zscaler Digital Experience Monitoring Self Service user notifications that can help identify the root cause of device and network issues, allowing users to investigate potential solutions without the need to contact customer support. Each notification contains a brief description, diagnosis, and recommendation for issues that have been detected and might need attention.
[See image.](#ssit-notification-example)
To learn more about configuring the notifications for users, see [Configuring Self Service Settings](/unified/configuring-self-service-settings). To learn more about notification data and its correlation with users, see [Monitoring the Self Service Dashboard](/unified/monitoring-self-service-dashboard-0).
-
-
-
-
-
-
-
-
-
-
-
-
-
-
-
-
-
| Issue | Notification | Description | Diagnosis | Recommendation |
| ----- | ------------ | ----------- | --------- | -------------- |
| High CPU | CPU is running around <value> and might reduce performance. | CPU is running at <value> for a sustained period of time and might affect the performance of your applications. | Top processes affecting performance: <list of processes> | Close applications contributing to high CPU usage. Alternatively, go to the Activity Monitor or Task Manager to end the processes. |
| Degraded Wi-Fi | Caused by suboptimal band or the Wi-Fi access point is far from your location. | The current Wi-Fi network <home Wi-Fi> signal is weak. | Latency to the access point <Basic Service Set Identifier> is high.Signal strength at <value> is low.Bandwidth at <value> is low. | Move closer to the access point or adjust the antenna of your access point to get a better signal.If you have administrative access to the access point, configure a different channel, or set auto-channel if your access point supports it.Check for other radio sources that might create noise and interference (e.g., a microwave, cordless phone, or poorly-shielded satellite dishes or cables). Also check wireless devices, such as a garage door opener, speaker, baby or camera monitor, and LCD displays running at 2.4 GHz.Verify that your access point is installed away from power lines or breaker rooms. |
| Suboptimal Wi-Fi Access Point | Weak signal detected for the connected Wi-Fi access point with SSID <value>. | The connected Wi-Fi access point <home basement> is suboptimal. | Latency to the access point <Basic Service Set Identifier> is high.Signal strength at <value> is low.Bandwidth at <value> is low. | Connect to a better access point in your SSID network.Review your mesh network setup.Turn your Wi-Fi off and on so the device reconnects to the access point with the strongest signal. <list from history home living room> |
| Suboptimal Wi-Fi Band | Connecting to 802.11ac provides better performance. | The connected SSID <ATT-4G> is suboptimal. Better band connectivity is available. | Latency to the access point <Basic Service Set Identifier> is high.Physical mode is 802.11n.Signal strength at <value> is low.Bandwidth at <value> is low. | Connect to the SSID on the 5 GHz band.<list from history> |
[]![Example Self-Service IT User Notification](/downloads/tech-pubs-drafts/zdx-draft-articles/viewing-self-service-it-user-notifications/zdx-ssit-notification-example.png)