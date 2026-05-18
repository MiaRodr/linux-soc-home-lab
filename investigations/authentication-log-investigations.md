# Authentication Log Investigation

## Objective
Investigate authentication logs to identify suspicious login activity and potential brute-force attempts.

## Commands Used
grep "Failed" suspicious-login.txt
grep "Failed" suspicious-login.txt | wc -l


## Findings
- Detected multiple failed login attempts targeting `root` and `admin`
- Observed repeated failed attempts from external IP `185.23`
- Internal IP `192.x.x.x` showed successful activity for user `mia`

## Analysis
Repeated failed attempts against privileged accounts may indicate a brute-force attack. External IP activity is more suspicious than internal activity and deserves further investigation.

## Skills Practiced
- Log analysis
- Authentication investigation
- Pattern recognition
- Security mindset
