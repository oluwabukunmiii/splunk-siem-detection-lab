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
1. *Ingest the Logs:* Upload the log samples from the /logs directory into your local Splunk instance.This is the sample of thge logs I ingested
    *2026-04-05 10:05:11 LOGIN FAILED user=admin ip=192.168.1.10
    2026-04-05 10:06:15 LOGIN SUCCESS user=john ip=192.168.1.15
    2026-04-05 10:07:18 FILE UPLOAD user=john file=project2.zip
    2026-04-05 10:08:28 FILE DOWNLOAD user=sarah file=report.pdf
 
2. *Execute Queries:* Copy the tailored search strings from the /queries folder and run them inside the Splunk Search & Reporting application.
      *Bruteforce Querries
   index=main "LOGIN FAILED" rex "user = (?<user>/5+)"
   | rex "ip = (?<ip>/5+)"
   | stats count by user ip where count >=1
   | sort = count

      *Dectection Querries
   index=main "LOGIN PASSED" rex "user = (?<user>/5+)"
   | rex "ip = (?<ip>/5+)"
   |stats count by user ip
   | sort - count

     *Files activity monitoring
   index=main ("FILE DOWNLOADED" OR "FILE UPLOAD" OR "FILE DELETION") rex "user = (?<user>/5+)"
   | rex "file = (?<file>/5+)"
   | stats count by user file


5. *Analyze Results:* Review the resulting statistics, event graphs, and triggered alerts to map out the attacker's timeline.
