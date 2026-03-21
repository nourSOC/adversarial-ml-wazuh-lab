# Incident Report

## Incident Title
Adversarial Machine Learning Activity Detected and Correlated

---

## Executive Summary
A simulated adversarial machine learning attack was detected using Wazuh SIEM.

The activity was generated through a Python-based simulation that produced dynamic ML anomaly indicators, which were converted into Windows events and ingested into the SIEM pipeline.

Two custom rules were used:
- Rule 100501 for detecting individual suspicious ML events
- Rule 100502 for correlating repeated adversarial behavior within a short timeframe

The result was a successful end-to-end detection pipeline capable of identifying and escalating suspicious AI-related activity.

---

## Detection Source
- Endpoint: Windows host
- SIEM: Wazuh
- Telemetry Source: Windows Event logs
- Detection Logic: Custom rules + correlation

---

## Timeline
- Python simulation executed on the Windows endpoint
- Windows events generated with ML anomaly indicators
- Wazuh agent collected the events
- Rule 100501 triggered on suspicious activity
- Rule 100502 triggered after repeated detections within 60 seconds
- Alerts became visible in the Wazuh dashboard

---

## Detection Details

### Rule 100501
This rule detects suspicious command-line activity containing the string `ml_inference_alert`.

It is used to identify individual adversarial ML indicators embedded in process execution telemetry.

### Rule 100502
This rule correlates repeated occurrences of Rule 100501.

If suspicious ML-related activity appears 3 times within 60 seconds, the system escalates the event into a higher-severity alert.

---

## Attack Behavior
The simulation created a process execution chain similar to real-world attacker behavior:

`python.exe → cmd.exe → eventcreate.exe`

This chain was monitored by Wazuh using Windows process creation logs.

The command line contained:
- unique input identifiers
- confidence values
- accuracy degradation values
- adversarial status indicators

---

## Severity Assessment
- Initial detection severity: Level 12
- Correlated detection severity: Level 15

The first alert indicated suspicious behavior.  
The second alert indicated repeated activity consistent with an attack campaign.

---

## Impact
This simulated attack demonstrates how adversarial ML activity can:
- degrade trust in machine learning systems
- bypass AI-driven controls
- remain invisible to traditional SOC workflows unless transformed into security signals

In a real environment, such behavior could affect fraud detection, malware analysis, anomaly detection, or automated decision systems.

---

## Root Cause
The environment had no direct visibility into ML anomalies by default.

Detection became possible only after:
- simulating ML behavior
- converting it into Windows event data
- building custom SIEM rules

---

## Recommendations
- Monitor AI and ML systems as attack surfaces
- Convert ML anomaly signals into security telemetry
- Use correlation rules for repeated suspicious behavior
- Track command-line execution chains linked to ML event generation
- Improve observability around model confidence and prediction drift

---

## Lessons Learned
This incident simulation shows that detection engineering can extend beyond traditional infrastructure threats.

AI-based activity can be modeled as behavioral telemetry and integrated into SOC workflows using:
- log generation
- process monitoring
- rule-based detection
- event correlation

This creates a practical path for monitoring machine learning security risks in operational environments.
