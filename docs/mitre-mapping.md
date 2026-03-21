# MITRE ATT&CK Mapping

This document maps the adversarial ML detection lab to relevant MITRE ATT&CK techniques.

---

## T1059 – Command and Scripting Interpreter
### Why it applies
The simulation relies on script and command execution to generate ML-related events.

Observed execution chain:
- python.exe
- cmd.exe
- eventcreate.exe

### Relevance
This reflects script-based execution used to trigger suspicious activity in the environment.

---

## T1204 – User Execution
### Why it applies
The simulation requires execution initiated by the user to generate and trigger the suspicious activity.

### Relevance
This matches user-driven execution of tools or scripts that result in security-relevant events.

---

## TA0002 – Execution
### Why it applies
The entire simulation depends on execution behavior that leads to event generation, detection, and escalation.

### Relevance
This tactic represents the attacker’s ability to run code or commands that produce suspicious telemetry.

---

## Behavioral Interpretation
This lab does not represent a full real-world adversarial ML attack against a production model.

Instead, it maps the observable execution behavior that a SOC can detect when ML-related anomaly signals are generated and transformed into Windows events.

The ATT&CK mapping is therefore based on:
- execution behavior
- command usage
- user-triggered activity
- detection visibility

---

## Summary
The lab demonstrates how AI-related security behavior can be mapped into existing ATT&CK-style SOC workflows, making machine learning anomalies more understandable and actionable for security analysts.
