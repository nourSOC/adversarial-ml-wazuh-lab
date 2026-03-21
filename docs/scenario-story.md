# Scenario Story

## Overview
This lab simulates how adversarial machine learning activity can become a real security concern inside modern environments.

Traditional SOC monitoring focuses on malware, brute force attempts, suspicious logins, and process anomalies. However, as organizations increasingly rely on machine learning models in fraud detection, malware analysis, anomaly detection, and automated decision-making, attackers can begin targeting the model itself rather than the operating system or application directly.

---

## Realistic Scenario
Imagine a financial organization that uses a machine learning model to detect suspicious transactions.

Under normal conditions:
- The model receives transaction data
- It analyzes patterns
- It classifies transactions as legitimate or fraudulent

An attacker does not need to exploit the server directly.  
Instead, the attacker can manipulate the input in a subtle way so the model makes a wrong prediction.

Examples of adversarial behavior:
- Fraudulent transactions classified as legitimate
- Malicious files classified as safe
- Suspicious activity classified as normal behavior

This is dangerous because the infrastructure may remain intact while the AI decision layer is compromised.

---

## Why Adversarial Attacks Matter
Adversarial attacks are dangerous because they target the logic of the model itself.

They can cause:
- Accuracy degradation over time
- High confidence in wrong predictions
- Detection bypass
- Reduced trust in AI-driven systems

In many environments, these attacks are hard to detect because the SOC does not directly monitor ML inference behavior by default.

---

## Why I Built This Lab
I built this lab to bridge the gap between AI security and SOC detection.

The goal was not only to simulate adversarial machine learning behavior, but also to transform ML-related signals into observable events that can be detected by a SIEM.

This lab demonstrates that:
- AI can become a real attack surface
- SOC teams need visibility into ML anomalies
- Detection engineering can convert ML behavior into security alerts

---

## Lab Objective
The main objective of this project was to simulate adversarial ML behavior and detect it using a security monitoring pipeline.

The lab includes:
- Python-based simulation
- Windows event generation
- Wazuh log ingestion
- Custom detection rules
- Correlation logic
- Dashboard visualization

---

## Key Message
If the SOC cannot see ML-related anomalies, it cannot detect attacks that target machine learning systems.

This lab shows how adversarial ML activity can be represented as security telemetry and integrated into a traditional SOC workflow.
