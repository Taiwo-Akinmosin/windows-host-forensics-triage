# Windows Host Forensics & Incident Triage Lab

## Objective
To simulate a local endpoint compromise (unauthorized execution and registry persistence) and perform end-to-end forensic artifact collection, triage, and analysis using industry-standard open-source tools.

---

## Lab Architecture & Environment
* **Host OS:** Dell Precision 3541 (VirtualBox Hypervisor)
* **Target VM (Victim):** Windows 10 Pro (Isolated virtual environment)
* **Analysis Toolkit:** KAPE (Kroll Artifact Parser and Extractor), Eric Zimmerman's Tools (PECmd, RECmd, EvtxECmd), Volatility 3.

---

## Step-by-Step Methodology

### Phase 1: The Live Lab & Artifact Generation
1. Provisioned an isolated Windows 10 Pro virtual machine in VirtualBox.
2. Simulated adversary behavior by executing test commands via PowerShell.
3. Created persistence via a mock registry run key: `HKCU\Software\Microsoft\Windows\CurrentVersion\Run`.
4. Extracted live artifacts using KAPE.

### Phase 2: Deep-Dive Artifact Analysis
* **Prefetch Analysis:** Parsed `.pf` files to confirm execution timestamps and run counts.
* **Registry Analysis:** Inspected user run keys to identify persistence mechanisms.
* **Event Log Triage:** Reviewed `.evtx` files focusing on Event ID 4688 (Process Creation) and Event ID 7045 (Service Installation).

---

## Remediation & Hardening Recommendations
1. **Endpoint Protection:** Configure EDR/XDR solutions to flag anomalous PowerShell invocation strings.
2. **Registry Monitoring:** Implement continuous auditing on user and system startup registry keys.
