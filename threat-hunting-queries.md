# Threat Hunting Queries

This document contains the main hunting queries used to investigate the adversarial ML detection lab.

---

## Query 1 – Detect individual ML anomaly alerts
```text
rule.id:100501

Purpose
Used to identify each individual event classified as adversarial ML activity.
Outcome
Returns alerts triggered by the custom detection rule.


Query 2 – Detect correlated attack campaigns
Plain text
rule.id:100502
Purpose
Used to identify repeated adversarial ML behavior within a short period of time.
Outcome
Returns high-severity correlated alerts indicating a possible attack campaign.
Query 3 – Search for ML indicators in command line
Plain text
data.win.eventdata.commandLine: "ml_inference_alert"
Purpose
Used to locate raw command-line executions related to the adversarial ML simulation.
Outcome
Helps analysts trace where the suspicious ML indicator appeared in the process chain.
Query 4 – Search for the custom event source
Plain text
data.win.system.providerName: "WazuhML"
Purpose
Used to locate Windows application events created specifically for the ML simulation.
Outcome
Helps validate that the endpoint generated ML-related telemetry.
Query 5 – Hunt suspicious process execution chain
Plain text
data.win.eventdata.commandLine: "eventcreate" AND data.win.eventdata.commandLine: "ml_inference_alert"
Purpose
Used to track process execution responsible for generating ML anomaly signals.
Outcome
Helps identify execution flow connected to the simulation.
Query 6 – Search by alert description
Plain text
rule.description: "Adversarial ML attack detected via custom Windows event trigger"
Purpose
Used to search based on the exact detection description.
Outcome
Helps confirm whether the detection rule triggered successfully.
Query 7 – Search by correlated alert description
Plain text
rule.description: "Repeated adversarial ML activity detected (possible attack campaign)"
Purpose
Used to identify correlation-based escalation alerts.
Outcome
Helps confirm repeated suspicious behavior over time.
Hunting Notes
These queries are useful for:
validating rule execution
investigating suspicious events
confirming repeated behavior
analyzing attack chains
They demonstrate how machine learning-related anomalies can be transformed into huntable SIEM telemetry.
