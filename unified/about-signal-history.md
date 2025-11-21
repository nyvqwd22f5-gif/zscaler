# About Signal History
Source: https://help.zscaler.com/unified/about-signal-history
PDF: https://help.zscaler.com/pdf/com/en/1508481.pdf

You can view the history of context signals over time and investigate security incidents that happened in the past. You can view and analyze the context signals for each [Adaptive Access profile](/unified/about-adaptive-access-profiles).
Signal history includes the following benefits and enables you to:
- View the list of context signals for specific durations and investigate the user and device activities.
- View the source of the context signals and review the context types.
- Analyze the signals for any suspicious activities and remediate the issues.
About the Signal History Page
On the Signal History page (Policies > Common Configuration > Adaptive Access > Signal History), you can do the following:
- View the list of context signals. For each signal, you can see:
- **Subject**: The username or device type for which the signal is logged.
- **Subject Type**: The user or device activity that triggered this event.
- **Source**: The source (Okta, CrowdStrike, Microsoft Entra ID) from where the context signal was received.
- **Context Type**: The type of signal received.
- **Value**: The risk (Low, High) associated with the user or device.
- **Creation**: The date and time the signal was generated.
- Use the filters to view specific information.
- Reset the page to the original settings.
- Search for a specific context signal.
- Modify the table and its columns.
![The Signal History page](/downloads/unified/policies/adaptive-access-engine/viewing-signal-history/aae-signalhistorypage.png)