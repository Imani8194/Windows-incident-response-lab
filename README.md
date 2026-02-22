# Windows-incident-response-lab
Hands-on Windows incident response lab analyzing Security Event Logs to identify brute-force login attempts and post-compromise PowerShell activity

---

# 🛡️ Windows Incident Response Lab

## 📌 Overview
This project simulates a basic Windows security incident investigation. The objective was to analyze Windows Security Event Logs to identify suspicious authentication activity and post-login system behavior.

This lab demonstrates foundational skills used by SOC Analysts and Incident Responders.

---

## 🎯 Objectives
- Identify repeated failed login attempts
- Detect successful login following brute-force behavior
- Analyze process creation events
- Investigate PowerShell execution activity
- Document Indicators of Compromise (IOCs)

---

## 🧰 Tools Used
- Windows 10 / 11
- Event Viewer
- PowerShell
- VirtualBox (Lab Environment)

---

## 🔍 Investigation Scenario

A workstation displayed unusual authentication behavior. Multiple failed login attempts were detected before a successful login occurred. Shortly after authentication, PowerShell was executed.

---

## 📊 Log Analysis

### Failed Login Attempts
- Event ID: 4625
- Logon Type: 3 (Network)
- Multiple attempts from same source

### Successful Login
- Event ID: 4624
- Occurred shortly after repeated failures

### Process Creation
- Event ID: 4688
- powershell.exe executed after login

---

## 🧪 PowerShell Log Filtering Example

```powershell
Get-WinEvent -LogName Security | Where-Object {$_.Id -eq 4625}
