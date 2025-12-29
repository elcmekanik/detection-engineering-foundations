# Attack to Log Mapping

This document maps common cyber attack techniques to how they appear in logs.
The goal is to understand detecction logic before writting SIEM rules.

---

## 1. Brute Force Attack

- MITRE ATT&CK: T1110
- Log Source: Windows Security Log
- Event IDs:
   - 4625 (Failed logon)
   - 4624 (Successful logon)

### Detection Idea
- Same username
- Multiple failed logons (4625)
- Short time window
- Followed by a successful logon (4624)

---

## 2. Password Spraying
- MITRE ATT&CK: t1110.003
- Log Source: Windows Security Log
- Event IDs:
    - 4625

### Detection Idea
- Many different usernames
- Same source IP
- Same time window
- All failures


---

## 3. New Service Installation (Persistence)

- MITRE ATTCK: T1543.003
- Log Source: Windows System Log
- Event IDs:
    - 7045(A service was installed)

### Detection Idea
- New service installed
- Service name is unusual
- Installed outside maintenance hours
- Installed by non-admin user


---

## 4. Encoded PowerShell Execution

- MITRE ATT&CK: T1059.001
- Log Source: Windows Security Log / Sysmon
- Event IDs:
    - 4688 (Process creation)

### Detection Idea
- powershell.exe execution
- Command line contains "-EncodedCommand"
- Parent process is suspicious (e.g. Office, browser)


---

## 5. RDP Login from Unusual IP

- MITRE ATT&CK: T1021.001
- Log Source: Windows Security Log
- Evemt IDs:
    - 4624 (Logon Type 10)

### Detection Idea
- Successful RDP login
- Source IP not see before
- Outside normak working hours



