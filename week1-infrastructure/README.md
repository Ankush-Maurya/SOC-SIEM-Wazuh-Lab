Week 1 — Infrastructure Setup & Agent Deployment

Objective

The objective of Week 1 was to design and deploy the foundational Security Operations Center (SOC) infrastructure using Wazuh SIEM. This included installing the Wazuh Manager on a Linux server, deploying a Windows agent endpoint, and configuring Sysmon to enhance process-level visibility for advanced threat monitoring.

This setup enabled centralized log collection, endpoint monitoring, and real-time security event visibility through the Wazuh Dashboard.

---

Infrastructure Architecture

SOC Server (Linux)

↓

Wazuh Manager + Dashboard

↓

Windows Endpoint Agent

↓

Sysmon Telemetry Forwarded to Wazuh

---

Tools Used

Tool| Purpose
Wazuh Manager| Central SIEM platform
Wazuh Agent| Endpoint log forwarding
Sysmon| Deep Windows telemetry
VirtualBox| Lab virtualization
Ubuntu Linux| SOC Server
Windows 11| Target endpoint

---

Step 1 — Install Wazuh Manager on Linux SOC Server

Download Wazuh installation script:

curl -sO https://packages.wazuh.com/4.7/wazuh-install.sh

Run installer:

sudo bash wazuh-install.sh -a

This installs:

- Wazuh Manager
- Wazuh Dashboard
- OpenSearch backend
- Filebeat log shipper

---

Step 2 — Access Wazuh Dashboard

Open browser:

https://<SOC-SERVER-IP>

Example:

https://10.132.255.89

Login using credentials generated during installation.

Dashboard confirms successful deployment of SIEM infrastructure.

---

Step 3 — Deploy Windows Wazuh Agent

Navigate inside dashboard:

Agents → Deploy New Agent

Select:

Operating System = Windows

Download installer

Run installer on Windows system:

.\wazuh-agent-4.7.x.msi

Enter Manager IP:

10.132.255.89

Start agent service:

net start wazuhsvc

Agent successfully connects with Wazuh Manager.

---

Step 4 — Verify Agent Connection

Navigate:

Dashboard → Agents

Confirm status:

Active

This verifies endpoint communication with SIEM server.

---

Step 5 — Install Sysmon for Deep Telemetry Monitoring

Sysmon improves detection capability by logging:

- Process creation
- Network connections
- Registry activity
- File activity
- Driver loading

Download Sysmon from Microsoft Sysinternals.

Extract files

Run installation command:

Sysmon64.exe -i

Verify installation:

Event Viewer → Applications and Services Logs → Microsoft → Windows → Sysmon

Presence of Event ID 1 confirms successful installation.

---

Step 6 — Confirm Sysmon Logs Forwarding to Wazuh

Navigate:

Wazuh Dashboard → Security Events

Search:

sysmon

Logs confirm telemetry pipeline is working correctly.

---

Output Verification

Successful infrastructure deployment confirmed by:

- Wazuh Dashboard accessible
- Windows Agent connected successfully
- Agent status showing Active
- Sysmon installed successfully
- Endpoint logs visible inside Wazuh Dashboard

This confirms SOC monitoring infrastructure is operational.

---

Screenshots

Screenshots stored inside:

week1-infrastructure/screenshots/

Included verification evidence:

screenshots/week1-agent-active.png

Shows Windows agent successfully connected with Wazuh Manager.

screenshots/week1-sysmon-installed.png

Shows Sysmon event logs inside Windows Event Viewer confirming installation.

---

Problems Faced During Implementation

Problem 1 — Agent Not Connecting to Manager

Issue:

Windows agent initially showed disconnected status.

Cause:

Incorrect Manager IP entered during installation.

Solution:

Updated Manager IP inside configuration file:

C:\Program Files (x86)\ossec-agent\ossec.conf

Restarted service:

net stop wazuhsvc

net start wazuhsvc

Agent connected successfully afterward.

---

Problem 2 — Browser Showing Security Warning

Issue:

Browser displayed security warning:

Not Secure Connection

Cause:

Self-signed SSL certificate used by Wazuh Dashboard.

Solution:

Selected:

Advanced → Proceed Anyway

Dashboard opened successfully.

---

Problem 3 — Sysmon Logs Not Appearing Initially

Issue:

Sysmon logs were not visible inside Wazuh Dashboard.

Cause:

Agent restart required after Sysmon installation.

Solution:

Restarted Wazuh agent service:

net stop wazuhsvc

net start wazuhsvc

Logs started appearing successfully.

---

Conclusion

In Week 1, a fully functional SOC monitoring environment was successfully deployed using Wazuh SIEM. The Wazuh Manager was installed on a Linux server, a Windows endpoint agent was integrated successfully, and Sysmon telemetry was enabled for enhanced visibility into endpoint activity.

This infrastructure forms the foundation for implementing detection rules, active response automation, and threat simulation activities in the upcoming phases of the SOC project.
