# SOC-SIEM Wazuh Lab — Enterprise EDR & Threat Hunting Project

## Project Overview

This project demonstrates the implementation of a centralized Security Operations Center (SOC) monitoring environment using Wazuh SIEM.

The lab simulates real-world enterprise security monitoring workflows including endpoint visibility, detection rule configuration, active response automation, MITRE ATT&CK mapping, and ransomware-style threat simulation using Atomic Red Team techniques.

This project replicates an industry-level SOC detection pipeline from log collection to automated response.

---

# Project Objectives

The objectives of this project were:

- Deploy centralized Wazuh SIEM infrastructure
- Configure endpoint monitoring using Wazuh Agents
- Enable Sysmon telemetry collection
- Implement File Integrity Monitoring (FIM)
- Detect authentication failures and brute-force attempts
- Configure Active Response automation
- Simulate attacker behavior using Atomic Red Team
- Map alerts to MITRE ATT&CK techniques
- Perform threat hunting using Wazuh dashboards

---

# Lab Architecture

SOC monitoring workflow:

```
Endpoints (Windows + Linux)
        ↓
Wazuh Agent Log Collection
        ↓
Wazuh Manager Analysis Engine
        ↓
Detection Rules & Decoders
        ↓
MITRE ATT&CK Mapping
        ↓
Wazuh Dashboard Visualization
        ↓
Active Response Automation
```

---

# Tools & Technologies Used

| Tool | Purpose |
|------|---------|
| Wazuh SIEM | Log analysis & threat detection |
| Sysmon | Windows telemetry collection |
| Kali Linux | Attack simulation |
| Hydra | SSH brute-force simulation |
| Atomic Red Team | Adversary technique simulation |
| MITRE ATT&CK Framework | Threat technique mapping |
| Linux Server | Wazuh Manager hosting |
| Windows Endpoint | Security monitoring target |

---

# Project Implementation Timeline

## Week 1 — Infrastructure Setup

Implemented:

- Installed Wazuh Manager
- Connected Windows endpoint agent
- Enabled Sysmon logging
- Verified agent heartbeat
- Validated dashboard visibility

Folder:

```
week1-infrastructure/
```

---

## Week 2 — Detection Rules & File Integrity Monitoring

Configured:

- File Integrity Monitoring (FIM)
- Rootcheck alerts
- Registry monitoring
- Custom detection visibility
- Vulnerability detection module

Folder:

```
week2-detection-rules/
```

---

## Week 3 — Active Response Automation (IPS)

Simulated:

SSH brute-force attack using Hydra

Detected:

Multiple authentication failures

Triggered:

Automatic firewall blocking using Active Response

Folder:

```
week3-active-response/
```

---

## Week 4 — Threat Simulation & MITRE ATT&CK Mapping

Simulated:

- Registry key deletion activity
- Credential abuse attempts
- Malware-like executable behavior
- Suspicious PowerShell execution

Mapped detections to:

MITRE ATT&CK techniques such as:

- T1078 Valid Accounts
- T1070 Indicator Removal
- T1485 Data Destruction Behavior
- T1548 Privilege Escalation
- T1490 Shadow Copy Deletion Simulation

Folder:

```
week4-threat-simulation/
```

---

# Detection Capabilities Implemented

This SOC lab successfully detects:

- SSH brute-force attacks
- Authentication failures
- Registry modifications
- File integrity violations
- Suspicious PowerShell activity
- Malware execution indicators
- Privilege escalation attempts
- Shadow copy deletion simulation
- Threat hunting dashboard alerts
- MITRE ATT&CK mapped adversary behavior

---

# Active Response Automation Example

Example automated workflow implemented:

```
SSH Brute Force Attack
        ↓
Authentication Failures Detected
        ↓
Detection Rule Triggered
        ↓
Active Response Script Executed
        ↓
Firewall Drop Command Applied
        ↓
Attacker IP Blocked Automatically
```

---

# MITRE ATT&CK Techniques Observed

Mapped detections include:

| Technique ID | Technique Name |
|-------------|----------------|
| T1078 | Valid Accounts |
| T1070 | Indicator Removal |
| T1485 | Data Destruction Behavior |
| T1548 | Privilege Escalation |
| T1490 | Shadow Copy Deletion |

---

# Threat Hunting Visibility

Threat hunting dashboards used to analyze:

- Logon failures
- Malware execution alerts
- Registry key deletion events
- Suspicious PowerShell behavior
- Authentication anomalies

This enables proactive SOC investigation workflow.

---

# Repository Structure

```
SOC-SIEM-Wazuh-Lab
│
├── architecture/
├── week1-infrastructure/
├── week2-detection-rules/
├── week3-active-response/
├── week4-threat-simulation/
└── screenshots/
```

---

# Key Learning Outcomes

Through this project I gained hands-on experience with:

- SIEM deployment
- Endpoint monitoring
- Detection engineering
- Threat simulation
- Active response automation
- MITRE ATT&CK mapping
- SOC investigation workflow
- Security event correlation
- Threat hunting techniques

---

# Conclusion

This project demonstrates a complete enterprise-style SOC monitoring pipeline using Wazuh SIEM including detection engineering, automated response, threat simulation, and adversary technique mapping.

The implementation replicates a real-world cybersecurity analyst workflow from monitoring to mitigation inside a centralized SOC environment.
