# Viewing the Post-Quantum Cryptography Visibility Report
Source: https://help.zscaler.com/zia/viewing-post-quantum-cryptography-visibility-report
PDF: https://help.zscaler.com/pdf/com/en/1532188.pdf

To view the [Post-Quantum Cryptography Visibility Report](/zia/understanding-post-quantum-cryptography-pqc-report), go to Analytics > Interactive Reports > Standard Reports > Web Activity. You can hover over the chart’s data in the report and click on it to gain more insights. To view information either in the form of logs or charts:
- Click the **View Logs** option to view the chart’s logs in the [Insights Logs](/zia/about-insights-logs) page. To go back to the report, click **Back to Original**.
- Click the **Analyze Chart** option to view the chart in the [Insights Logs](/zia/about-insights-logs) page. To go back to the report, click **Back to Original**.
The Post-Quantum Cryptography Visibility Report allows you to view information from the following perspectives:
- [1. PQC vs. Classical Key Exchange](#pqc_vs_cke)
- [2. Top PQC Key Exchange Algorithms](#top_pqc_kex)
- [3. Top Users with PQC Key Exchange](#top_users_kex)
- [4. TLS Version - Client](#client_side_tls)
- [5. TLS Version - Server](#server_side_tls)
[]You can gain insights into the distribution of transactions showing the customer Post-Quantum Cryptography (PQC) readiness. The graphs show a comparison between the PQC algorithm and the Classical Key Exchange algorithm of your organization's web traffic.
- **Classical**: When you click within the Classical section, you can view all transactions where the Client Key Exchange has either **Classical **or **Unknown **type set.
- **PQC**: When you click within the PQC section of the chart, you can view all transactions where the Client Key Exchange offer has either **PQC **or the **Hybrid **type set.
![The Post-Quantum Cryptography Visibility Report shows the PQC vs. Classical Key Exchange Algorithms for the web traffic.](/downloads/zia/dashboard-analytics/reports/understanding-post-quantum-cryptography-pqc-report/PQC_vs_classical.gif)
[]You can gain insights into the client-side negotiated PQC or Hybrid Key Exchange algorithms that are ranked by their frequency in your transactions. This chart allows you to see which quantum-safe cryptographic methods are most prevalent in your network traffic.
![The chart shows the top PQC Key exchange algorithms](/downloads/zia/dashboard-analytics/reports/understanding-post-quantum-cryptography-pqc-report/Top_PQC_Key_exchange.gif)
[]You can gain insights into user activity related to PQC or Hybrid Key Exchange algorithms. The data presented ranks users based on their total transaction count, offering a clear overview of who is most frequently engaging with these advanced cryptographic methods.
![You can view information regarding top users with PQC key exchange algorithms.](/downloads/zia/dashboard-analytics/reports/understanding-post-quantum-cryptography-pqc-report/Top_users_pqc_kex.gif)
[]You can view insights into the TLS versions used for communications between the client and ZIA Public Service Edge. The charts help you analyze trends over time to identify any potential vulnerabilities or areas for improvement in security posture.
PQC support requires TLS 1.3 and cannot be negotiated in TLS 1.2 and earlier versions.
![You can view and analyze information about the TLS versions used in your organization organization during client side and Zscaler Public Edge service communications.](/downloads/zia/dashboard-analytics/reports/understanding-post-quantum-cryptography-pqc-report/TLS_version_client.gif)
[]You can view insights into the TLS versions used for communications between ZIA Public Service Edge and the server. The charts help you analyze trends over time to identify any potential vulnerabilities or areas for improvement in security posture.
PQC support requires TLS 1.3 and cannot be negotiated in TLS 1.2 and earlier versions.
![You can view and analyze information about the TLS versions used in your organization during server and Zscaler Public Edge service communications..  ](/downloads/zia/dashboard-analytics/reports/understanding-post-quantum-cryptography-pqc-report/TLS_version_server.gif)
![The Post-Quantum Cryptography Visibility Report showing the different charts with respect the PQC.](/downloads/zia/dashboard-analytics/reports/viewing-post-quantum-cryptography-visibility-report/PQC_visibility_report_numbered.png)