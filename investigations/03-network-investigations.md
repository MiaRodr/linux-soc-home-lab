# Network Investigation

## Objective
Investigate listening services and network activity to identify potentially suspicious behavior.

## Commands Used

```bash
ss -tunap
grep "LISTEN" services.log
grep "python" services.log
```

## Findings
- Identified `python3 backdoor.py` listening on port `4444`
- Observed `0.0.0.0` listening state
- Identified normal services including `nginx`, `sshd`, `systemd-resolved`, and `chronyd`

## Analysis
The process `python3 backdoor.py` deserves additional investigation because Python scripts can automate activity and the filename suggests a possible backdoor.

The process was in a LISTEN state on `0.0.0.0:4444`, meaning it was accepting connections on all available network interfaces. This behavior could indicate unauthorized access or persistence and would require further investigation.

## Skills Practiced
- Network investigation
- Process analysis
- Listening service analysis
- Pattern recognition
- Security investigation mindset
