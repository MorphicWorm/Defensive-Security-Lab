# 🛡️ Defensive Security Lab

Welcome to my **Defensive Security Lab** — a personal, hands-on learning space focused on simulating and detecting common attacker techniques such as persistence, process injection, and system tampering on Windows systems.

This repo demonstrates real-world investigation and detection skills using **safe, malware-free simulations**. Each lab focuses on specific techniques, tools, or scenarios to build your blue team expertise.

---

## 📘 Table of Contents
- [🔬 Lab Environment Setup](#-lab-environment-setup)
- [🖥️ Virtual Machine Layout](#-virtual-machine-layout)
- [🔒 Simulation Approach](#-simulation-approach)
- [🧪 Lab Index](#-lab-index)
- [🧰 Tools Used Across Labs](#-tools-used-across-labs)
- [📌 Author & Updates](#-author--updates)

---

## 🔬 Lab Environment Setup

All labs are run in a fully isolated virtual environment built on **VirtualBox**.  
The core setup includes a Windows target system used for simulation and analysis, with room for expansion as new tools and detection methods are explored.

---

## 🖥️ Virtual Machine Layout

| VM                          | Role                                                 | Tools / Configs                                                                              |
|----------------------------|------------------------------------------------------|----------------------------------------------------------------------------------------------|
| Windows Server 2025        | Primary system for persistence simulation & detection| RegShot, Process Explorer, PowerShell, Sysmon, Event Viewer                                 |
| (Optional) Analyst Workstation | For future centralized log collection and IR tools   | Splunk, Velociraptor, Wireshark, Notepad++                                                  |
| Network Configuration       | Internal virtual switch only (`SOC_Lab_Net`)         | Dual NIC: NAT (for Windows updates) + Internal (lab-only communication)                    |

---

## 🔒 Simulation Approach

> ✅ All labs are safe and malware-free.  
Simulations use harmless batch files, Windows-native commands, and the industry-standard **EICAR** test string (where applicable).

Key Focus Areas:
- Simulated persistence techniques (e.g., Startup folder, Run keys, Scheduled Tasks)
- System changes, registry behavior, process trees, and autostarts
- Windows logging visibility and forensic markers
- Every lab includes setup steps, detection techniques, and cleanup procedures

---

## 🧪 Lab Index

| Lab | Description | Status |
|-----|-------------|--------|
| 01 - RegShot & Process Explorer | Detect registry-based persistence using RegShot and analyze startup processes | ✅ Complete |
| 02 - Startup Folder Persistence | Simulate persistence via Startup folder entries | 🔜 Planned |
| 03 - Scheduled Task Persistence | Detect benign scheduled tasks created for persistence | 🔜 Planned |
| 04 - Active Setup Persistence | Analyze how Active Setup can be abused for stealthy execution | 🔜 Planned |
| 05 - Windows Logs Investigation | Review Event Viewer and Sysmon logs related to persistence activity | 🔜 Planned |
| 06 - Phishing Header Analysis | Parse and analyze email headers using test phishing messages | 🔜 Planned |

---

## 🧰 Tools Used Across Labs

| Tool            | Purpose                                                  |
|-----------------|----------------------------------------------------------|
| RegShot         | Registry snapshot and diffing                            |
| Process Explorer| Advanced process inspection                              |
| PowerShell      | Scripting and automation of benign simulations           |
| Sysmon          | System event logging for advanced detection visibility   |
| Event Viewer    | Manual log inspection and event tracking                 |
| Notepad++       | Log and diff file analysis                               |

---

## 📌 Author & Updates

**Author**: [MorhicWorm](https://github.com/MorphicWorm)  
**Last Updated**: April 2025  
**Focus**: Detection engineering, hands-on lab building, and SOC analysis skills

---

