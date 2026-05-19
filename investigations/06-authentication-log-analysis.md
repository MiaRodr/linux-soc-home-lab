# Authentication Log Investigation

## Objective

Investigate suspicious authentication activity to determine whether login attempts indicate possible unauthorized access.

## Commands Used

```bash
grep "Failed" auth-events.log
grep "Accepted" auth-events.log
grep "203.0.113.25" auth-events.log
```

## Findings

- Multiple failed login attempts were identified for the `admin` account from external IP `203.0.113.25`
- Successful login activity was identified for the privileged `root` account from the same external IP
- A successful login for `mia` originated from internal IP `192.168.1.10`, which appeared normal
- Additional failed login attempts were identified from external IP `185.220.101.5`

## Analysis

The log activity suggests repeated failed authentication attempts followed by successful access to a privileged account. Multiple failed attempts occurring before successful access may indicate suspicious authentication activity or possible credential compromise.

Current evidence does not confirm a system compromise. Additional investigation is required to determine whether the login activity was authorized.

## Conclusion

**Observed:**

Repeated failed login attempts against the `admin` account from `203.0.113.25` followed by successful authentication to the `root` account.

**Status:**

Compromise suspected but not confirmed.

**Recommended Actions:**

- Review additional authentication logs
- Investigate related processes and active sessions
- Examine source IP activity
- Search for indicators of compromise (IOCs)
