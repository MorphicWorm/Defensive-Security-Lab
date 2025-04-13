# 🔍 Persistence Detection Lab – RegShot + Process Explorer

This lab demonstrates how to simulate and detect registry-based persistence on a Windows Server VM using **RegShot** and **Process Explorer**. The exercise uses a **safe, benign batch file** to mimic common persistence techniques and reinforces registry monitoring and runtime analysis.

---

## 🖥️ Lab Environment

- **VM Used:** Windows Server Victim VM  
- **Tools Required:**
  - [RegShot](https://sourceforge.net/projects/regshot/)
  - [Process Explorer (Sysinternals)](https://learn.microsoft.com/en-us/sysinternals/downloads/process-explorer)

---

## 🧪 What You’ll Learn

| Tool              | Skill Practiced                                                               |
|-------------------|--------------------------------------------------------------------------------|
| RegShot           | Detecting registry-based persistence using before/after snapshot comparisons |
| Process Explorer  | Investigating runtime persistence, startup entries, and process trees        |
| Safe Simulation   | Practicing detection using 100% benign test files                             |

---

## 📁 Simulation Script

The full step-by-step simulation process is available in the `persistence_simulation.md` file (or equivalent script folder).

---

## 🧹 Clean-Up

Includes optional cleanup commands to remove the test file and registry key after testing.

---

## ✅ Outcome

This lab builds hands-on blue team skills for detecting registry-based persistence and analyzing suspicious startup behavior — essential for SOC and IR workflows.

