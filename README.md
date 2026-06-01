# splunk-siem-detection-lab
A security lab environment focused on log analysis, file integrity monitoring, and SPL detection queries for brute-force attacks.
# Splunk SIEM Detection & Log Analysis Lab

## 📌 Project Overview
This repository contains a security monitoring and log analysis lab built to demonstrate how an enterprise SIEM (Splunk) surfaces and alerts on cyber threats. By analyzing raw security logs, creating customized Search Processing Language (SPL) queries, and monitoring host system activity, this lab simulates real-world security analyst workflows.

## 📁 Repository Structure
* */logs* - Contains sanitized tracking artifacts from simulated network and system incidents.
* /dection queries* - contain the detection querry
* /bruteforce queries* - contain the bruteforce detection querry
* /file activity monitoring* - contain the file activity monitoring querry
* */screenshots* 

---

## 🔍 Core Security Use Cases Monitored

### 1. FTP Brute-Force Attack Detection
* *Objective:* Detect automated credential-stuffing and password-guessing attempts against an internal FTP server.
* *Log Sources:* FTP Server Authentication Logs (ftp logs, Bruteforce Attack).
* *Analysis Focus:* Tracking high-frequency authentication failures (action=failure or status=530) coming from a single source IP address within a short time window.

### 2. File Integrity Monitoring (FIM) & Activity Tracking
* *Objective:* Surface unauthorized modifications, deletions, or read access to highly sensitive system files.
* *Log Sources:* Host Operating System Event Logs (Files activity monitoring).
* *Analysis Focus:* Identifying anomalous file modifications outside of standard change-management windows, tracking user account privileges, and flagging mass changes.

---

## 🛠️ Tools & Technologies Used
* *SIEM Platform:* Splunk Enterprise / Splunk Light
* *Query Language:* Splunk Search Processing Language (SPL)
* *Log Formats:* Plain text syslog (.txt), authentication audit trails
* *Environment:* Virtualized Sandbox (Home Lab)

---

## 🚀 How to Use This Lab
1. *Ingest the Logs:* Upload the log samples from the /logs directory into your local Splunk instance.
2. *Execute Queries:* Copy the tailored search strings from the /queries folder and run them inside the Splunk Search & Reporting application.
3. *Analyze Results:* Review the resulting statistics, event graphs, and triggered alerts to map out the attacker's timeline.
