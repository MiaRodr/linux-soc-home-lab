# Process Investigation

## Objective
Investigate running processes and identify potentially suspicious activity.

## Commands Used
cat process.log
grep "python3" process.log
grep "updater" process.log
grep "PID" process.log | wc -l

## Findings
- Identified `python3 suspicious_script.py`
- Identified `updater.sh`
- Found normal system processes including `nginx`, `SSHD`, and `cron`
- Detected 6 process records

## Analysis
The process `python3 suspicious_script.py` deserves additional investigation because scripts can automate malicious activity such as persistence, downloading payloads, or unauthorized actions.

`cron` alone is not automatically suspicious because it is commonly used for scheduled tasks. However, suspicious scripts configured to run through cron would increase concern.

## Skills Practiced
- Process investigation
- Linux command line
- Pattern recognition
- Security analysis mindset
