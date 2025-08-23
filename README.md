# wazuh-siem-lab
Wazuh SIEM lab on Linode: manager + indexer + dashboard + Ubuntu agent. Includes detection scenarios (FIM, failed logins, user creation, sudo abuse) and docs.

# 🛡️ Wazuh SIEM Deployment & Detection Lab

## 📖 Overview
This project documents my hands-on deployment of **Wazuh SIEM** and simulation of real-world detection scenarios.  
I deployed a Wazuh Manager on a **Linode VPS**, connected a Linux agent, and verified detections through the Wazuh dashboard.  
The goal: showcase my ability to deploy, configure, and simulate SIEM detections like a SOC Analyst.

---

## ⚙️ Environment/Architecture Details

- **Manager (Linode VPS)**: Collects and analyzes logs.  
- **Indexer**: Stores and indexes alerts (OpenSearch).  
- **Dashboard**: Web UI for visualization.  
- **Agent (Ubuntu VM)**: Endpoint monitored for events.  

---

## 🚀 Deployment Steps
1. **Provision VPS (Linode)**  
   - Ubuntu 22.04, 4 vCPUs, 6GB RAM, 80GB disk.  
   - Installed Wazuh All-in-One (Manager + Indexer + Dashboard).  

2. **Configure Wazuh Dashboard**  
   - Edited `wazuh.yml` to connect API.  
   - Accessed dashboard via `https://<server-ip>`.  

3. **Register Agent**  
   - Installed Wazuh Agent on Ubuntu VM.  
   - Exchanged keys with the server.  
   - Verified agent was `Active` on the dashboard.  

---

## 🔎 Detection Scenarios

### Step 1: File Integrity Monitoring (FIM)
- **Config:** Added `/home` to `<syscheck>` in `ossec.conf`.  
- **Test:** Created/modified/deleted `testfile.txt`.  
- **Result:** Alert appeared on dashboard under *Integrity Monitoring*.  

📸 *[Insert screenshot of dashboard FIM alert]*  

---

### Step 2: Failed Login Attempts
- **Test:** Repeated invalid SSH logins (`ssh wronguser@localhost`).  
- **Result:** Alerts raised under *Authentication* in dashboard.  

📸 *[Insert screenshot of failed login alert]*  

---

### Step 3: User Account Creation
- **Test:** Created user `hacker` (`sudo useradd hacker`).  
- **Result:** Alert appeared under *User and Account Activity*.  

📸 *[Insert screenshot of account creation alert]*  

---

### Step 4: Privilege Escalation (Sudo Abuse)
- **Test:** Attempted unauthorized privileged commands (`sudo su`, `sudo cat /etc/passwd`).  
- **Result:** Alerts raised for suspicious sudo activity.  

📸 *[Insert screenshot of sudo abuse alert]*  

---

## ✅ Key Takeaways
- Successfully deployed a SIEM (Wazuh) in a cloud environment.  
- Integrated endpoint agent and verified communication.  
- Simulated **4 detection scenarios** relevant to SOC analyst work:
  - File Integrity Monitoring  
  - Failed SSH Logins  
  - User Account Creation  
  - Privilege Escalation via Sudo Abuse  
- Gained practical experience with log collection, alerting, and dashboard analysis.  

---


## Full Lab Report (Google Doc)
[https://docs.google.com/document/d/1TajXG_ZfgNebhn_WjOxBBDD-Tk4DBF-6S7uW6WpgIL0/edit
](https://docs.google.com/document/d/1TajXG_ZfgNebhn_WjOxBBDD-Tk4DBF-6S7uW6WpgIL0/edit?tab=t.0)

## 📌 Next Steps
- Add more detection scenarios (e.g., process execution, port scans).  
- Deploy Windows agent for cross-platform detection.  
- Explore Wazuh rules tuning and alert forwarding 

---

## 🧑‍💻 Author
**Charles Ekaluo**  
- GitHub: [charles-ekaluo](https://github.com/charles-ekaluo)  
- LinkedIn: *https://www.linkedin.com/in/charles-e-804969299/*  
