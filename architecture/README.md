# SOC-SIEM Wazuh Lab Architecture

## Overview

This project implements a centralized Security Operations Center (SOC) monitoring lab using Wazuh SIEM to detect, analyze, and respond to security threats in real time.

The architecture includes a Wazuh Manager server, multiple monitored endpoints, attack simulation using Kali Linux, and visualization through the Wazuh Dashboard.

The goal of this architecture is to simulate enterprise-level security monitoring infrastructure.

---

# Architecture Components

The SOC lab environment consists of the following components:

| Component | Role |
|----------|------|
| Wazuh Manager | Central log collection and analysis engine |
| Wazuh Agents | Installed on monitored endpoints |
| Windows Endpoint | Registry, PowerShell, Sysmon monitoring |
| Linux Server | SSH monitoring and brute-force detection |
| Kali Linux Machine | Attack simulation system |
| Wazuh Dashboard | Alert visualization and threat hunting |
| MITRE ATT&CK Module | Attack technique mapping |

---

# Architecture Diagram Explanation

The monitoring workflow operates as follows:

Endpoints (Windows + Linux)

↓

Wazuh Agent collects logs

↓

Logs forwarded to Wazuh Manager

↓

Rules and decoders analyze events

↓

Alerts generated

↓

MITRE ATT&CK mapping applied

↓

Dashboard visualization

↓

Active Response triggered if required

---

# Network Layout

The SOC monitoring lab environment includes:

- Linux server hosting Wazuh Manager
- Windows machine configured with Sysmon
- Kali Linux attacker machine
- Communication between agents and manager over secure channels

Example architecture flow:

```
Kali Linux (Attacker)
        ↓
Simulated Attack Activity
        ↓
Windows / Linux Endpoint
        ↓
Wazuh Agent
        ↓
Wazuh Manager
        ↓
Alert Detection Engine
        ↓
MITRE ATT&CK Mapping
        ↓
Wazuh Dashboard Visualization
        ↓
Active Response (Firewall Blocking)
```

---

# Monitoring Capabilities Implemented

This SOC architecture supports:

- File Integrity Monitoring (FIM)
- Registry change detection
- SSH brute-force attack detection
- PowerShell suspicious activity detection
- Malware behavior detection
- Authentication failure monitoring
- Threat hunting dashboard visibility
- MITRE ATT&CK technique mapping
- Automated firewall blocking (Active Response)

---

# Security Detection Workflow

Security monitoring lifecycle implemented:

```
Log Collection
→ Event Processing
→ Rule Matching
→ Alert Generation
→ Threat Classification
→ MITRE Mapping
→ Dashboard Visualization
→ Active Response Execution
```

This workflow represents a real SOC detection pipeline.

---

# MITRE ATT&CK Techniques Detected

During the project implementation the following techniques were detected:

| Technique ID | Technique Name |
|-------------|----------------|
| T1078 | Valid Accounts |
| T1070 | Indicator Removal |
| T1485 | Data Destruction Behavior |
| T1548 | Privilege Escalation |
| T1490 | Shadow Copy Deletion Simulation |

These mappings confirm enterprise-level threat visibility capability.

---

# Active Response Integration

The architecture includes automated response capability.

Example response actions:

- Detect SSH brute-force attack
- Identify attacker IP address
- Trigger firewall-drop command
- Block attacker automatically using iptables

This demonstrates IPS-style automated defense.

---

# Threat Hunting Capability

Threat hunting dashboards were used to analyze:

- Logon failures
- Malware execution behavior
- Registry key deletion activity
- Suspicious PowerShell execution
- Authentication anomalies

This enables proactive threat investigation inside SOC environment.

---

# Conclusion

This SOC-SIEM Wazuh Lab architecture successfully demonstrates centralized log monitoring, attack detection, MITRE ATT&CK mapping, threat hunting visibility, and automated response capabilities.

The implemented environment replicates a real-world enterprise SOC monitoring workflow using Wazuh SIEM.
