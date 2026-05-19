# Incident Response Simulation: Suspected Brute Force and Persistence Activity

## Objective

Investigate suspicious authentication activity and determine whether indicators of compromise exist.

## Alert Information

Authentication logs:

```bash
Failed password for root from 185.22.61.7
Failed password for admin from 185.22.61.7
Accepted password for root from 185.22.61.7
```

Processes observed:

```bash
root 2033 python3 backdoor.py
root 2148 nc -lvp 4444
```

## Investigation Steps

1. Reviewed authentication events
2. Identified repeated failed login attempts
3. Identified successful root authentication
4. Investigated suspicious Python processes
5. Investigated listening services

## Findings

- Multiple failed login attempts from the same external IP suggested possible brute-force activity
- Successful root login increased concern level
- Suspicious process `python3 backdoor.py` identified
- Netcat listening on port 4444 identified

## Conclusion

Multiple indicators suggested a high-confidence suspected compromise requiring further investigation and containment procedures.
