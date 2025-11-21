# Understanding Quality of Service Events
Source: https://help.zscaler.com/deception/understanding-quality-service-qos-events
PDF: https://help.zscaler.com/pdf/com/en/1532826.pdf

Zscaler Deception generates Quality of Service (QoS) events to maintain platform integrity and prevent malicious actors from overwhelming resources. This mechanism helps preserve resource availability for legitimate detections and analytics while throttling abusive or automated tools that exceed reasonable event generation limits.
QoS Events for Threat Intelligence (TI) Decoys
The QoS mechanism functions as a lightweight, automated DDoS protection layer for TI decoys. It prevents malicious or misconfigured sources from saturating the logging capabilities with repetitive probes, connection attempts, or payloads. By capping the event rate per attacker, Deception ensures:
- Legitimate threat telemetry remains accurate and actionable.
- TI decoy integrity and uptime are maintained.
- Resources are fairly distributed across multiple attackers and decoys.
- Logs capture only high-value events, improving signal-to-noise ratio and analytical efficiency.
When an attacker or automated tool repeatedly triggers a TI decoy, Deception monitors the event rate and automatically applies QoS controls if the threshold is exceeded. The QoS event is generated when the threshold of 10,000 events exceeds within 60 minutes. This is treated as potential DDoS-like behavior, and Deception applies a cool-down period of two hours. During the cool-down period, no new QoS event is generated for the same attacker. Normal detection and logging resume automatically after the attacker's event rate falls below the threshold.