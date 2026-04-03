Week 2 — Detection Rules Configuration (FIM, Rootcheck & Vulnerability Detection)

Objective

The objective of Week 2 was to configure detection logic inside the Wazuh SIEM environment by enabling File Integrity Monitoring (FIM), Rootcheck monitoring, and Vulnerability Detection modules.

These configurations help detect unauthorized file modifications, suspicious system activity, and known vulnerabilities on monitored endpoints.

This phase strengthened endpoint visibility and enabled real-time detection alerts inside the SOC dashboard.

---

Detection Architecture Flow

Windows Endpoint / Linux Endpoint

↓

File Changes / Registry Changes / System Activity

↓

Wazuh Agent Monitoring

↓

Wazuh Manager Correlation Engine

↓

Security Alerts Generated in Dashboard

---

Tools Used

Tool| Purpose
Wazuh Manager| Detection engine
Wazuh Agent| Endpoint monitoring
Rootcheck| Suspicious system activity detection
FIM Module| File integrity monitoring
Vulnerability Detector| CVE detection

---

Step 1 — Enable File Integrity Monitoring (FIM)

FIM monitors sensitive system files and directories for:

- File modification
- File deletion
- File creation
- Permission changes

Open configuration file:

Linux agent:

/var/ossec/etc/ossec.conf

Add monitored directory:

<syscheck>
  <directories realtime="yes">/etc</directories>
</syscheck>

Restart agent service:

sudo systemctl restart wazuh-agent

This enables real-time monitoring of critical Linux system files.

---

Step 2 — Trigger FIM Alert Manually

Create test directory:

sudo mkdir /tmp/ransomware_test

Create test files:

sudo touch /tmp/ransomware_test/file1

sudo touch /tmp/ransomware_test/file2

Delete directory:

sudo rm -rf /tmp/ransomware_test

Wazuh detects these changes instantly.

---

Step 3 — Verify FIM Alerts Inside Dashboard

Navigate:

Wazuh Dashboard → Security Events

Observed alerts:

File added to system
Integrity checksum changed
File deleted

This confirms File Integrity Monitoring is working correctly.

---

Step 4 — Enable Rootcheck Monitoring

Rootcheck detects:

- Rootkits
- Hidden processes
- Suspicious binaries
- System anomalies

Open configuration file:

/var/ossec/etc/ossec.conf

Ensure rootcheck enabled:

<rootcheck>
  <disabled>no</disabled>
</rootcheck>

Restart agent:

sudo systemctl restart wazuh-agent

Rootcheck monitoring activated successfully.

---

Step 5 — Verify Rootcheck Alerts

Navigate:

Security Events → Filter → rootcheck

Observed alerts:

Host-based anomaly detection event (rootcheck)

This confirms rootcheck detection is operational.

---

Step 6 — Enable Vulnerability Detection Module

Open configuration file:

/var/ossec/etc/ossec.conf

Add:

<vulnerability-detector>
  <enabled>yes</enabled>
  <interval>5m</interval>
</vulnerability-detector>

Restart manager:

sudo systemctl restart wazuh-manager

This enables CVE scanning capability.

---

Step 7 — Verify Vulnerability Detection

Navigate:

Dashboard → Vulnerabilities

Detected:

Outdated packages
Known CVEs
Security exposure indicators

Confirms vulnerability monitoring active.

---

Output Verification

Detection system confirmed operational by:

- File change alerts generated
- Rootcheck anomaly alerts detected
- Integrity checksum alerts visible
- Vulnerability detector enabled successfully
- Events visible inside Security Dashboard

---

Screenshots

Screenshots stored inside:

week2-detection-rules/screenshots/

---

Rootcheck Alert Detection

"Rootcheck Alert" (screenshots/week2-rootcheck-alert.png)

Shows host-based anomaly detection events triggered by rootcheck module.

---

File Integrity Monitoring Alerts

"FIM Alert" (screenshots/week2-fim-file-change-alert.png)

Shows file addition, deletion, and checksum modification alerts detected by Wazuh.

---

Alerts JSON Log Verification

"Alerts JSON Log" (screenshots/week2-alerts-json-rootcheck-log.png)

Shows raw alerts.json log entries confirming backend detection processing.

---

Problems Faced During Implementation

Problem 1 — FIM Alerts Not Appearing Initially

Issue:

File modification alerts were not visible inside dashboard.

Cause:

Realtime monitoring not enabled inside configuration.

Solution:

Updated configuration:

<directories realtime="yes">/etc</directories>

Restarted agent service:

sudo systemctl restart wazuh-agent

Alerts appeared successfully afterward.

---

Problem 2 — Rootcheck Alerts Delayed

Issue:

Rootcheck alerts appeared after delay.

Cause:

Rootcheck scheduled scan interval.

Solution:

Executed manual scan:

sudo /var/ossec/bin/rootcheck_control -u

Alerts generated immediately.

---

Problem 3 — Vulnerability Detector Not Starting

Issue:

Vulnerability module not generating alerts.

Cause:

Manager restart required after enabling module.

Solution:

Restarted manager service:

sudo systemctl restart wazuh-manager

Module activated successfully.

---

Conclusion

In Week 2, detection capabilities of the SOC environment were significantly improved by enabling File Integrity Monitoring, Rootcheck anomaly detection, and Vulnerability Detection modules.

These configurations allowed real-time monitoring of critical system files, detection of suspicious behavior, and identification of known security vulnerabilities, strengthening the defensive monitoring posture of the SOC infrastructure.
