# soc-style-log-anomaly-detection
A lightweight SOC-oriented host behavior anomaly detection system for Linux using authentication and network logs. Built with Isolation Forest and One-Class SVM to detect behavioral deviations instead of signature-based threats.
# Adaptive Log-Based Anomaly Detection (SOC-Oriented)

## Overview

This project is a lightweight, SOC-inspired host monitoring system designed to detect behavioral deviations on a Linux machine using authentication and network logs.

It does NOT aim to detect specific malware signatures or replace traditional IDS/IPS systems.  
Instead, it focuses on identifying deviations from normal host behavior using unsupervised machine learning techniques.

This project is developed as a personal Blue Team laboratory on a Linux VM.

---

## Objectives

- Monitor authentication and network behavior
- Establish a behavioral baseline
- Detect deviations using:
  - Isolation Forest (Forest-based model)
  - One-Class SVM (Boundary-based model)
- Generate SOC-style alert outputs
- Keep the system lightweight and explainable

---

## Design Philosophy

This project intentionally avoids:

- Signature-based detection
- Packet-level deep inspection (no Suricata)
- Automatic blocking or response
- Malware classification

Instead, it focuses on:

- Host behavioral shifts
- Time-based aggregation
- Explainable anomaly scoring
- SOC-style interpretation

---

## Log Sources

### Authentication Logs
- `/var/log/auth.log`
- SSH login success/failure
- sudo activity

### Network Activity
- `ss -tunap` snapshots
- Connection states
- Remote IP analysis
- Port usage patterns

---

## Architecture (Conceptual)

Logs → Parsing → Time Window Aggregation → Feature Extraction  
→ Isolation Forest + One-Class SVM → Alert Scoring → SOC-style Output

---

## Feature Examples

Authentication:
- Login success count
- Login failure count
- Unique source IPs
- sudo usage frequency
- Night login indicator

Network:
- Outbound connection count
- Unique remote IPs
- New remote IP detection
- Uncommon port usage
- Connection spike detection

---

## Labeling Strategy

Labels are not based on "attack vs normal."

Instead, this system defines:

- BASELINE → Normal host behavior
- DEVIATED → Behavioral deviation from baseline

This reflects real SOC practice, where analysts evaluate anomalies rather than rely solely on attack signatures.

---

## Project Structure (Planned)
adaptive-log-based-anomaly-detection/
│
├── logs/
├── parser/
├── features/
├── ml/
├── output/
└── README.md


---

## Current Status

Environment setup phase:
- Ubuntu Server 22.04 (VM)
- Cron-based network snapshot collection
- Authentication log monitoring

Machine learning pipeline development in progress.

---

## Future Extensions

- Feature importance visualization
- Multi-level alert severity scoring
- Host role simulation (server vs workstation)
- Drift-aware model updates
- Optional HIDS-style process behavior integration

---

## Author

Developed as a personal Blue Team research and skill-building project.
