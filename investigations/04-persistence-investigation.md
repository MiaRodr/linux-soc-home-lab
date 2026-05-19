# Persistence Investigation

## Objective
Investigate potential persistence mechanisms that could allow continued execution or access on a Linux system.

## Investigation Steps

### Reviewed startup scripts

Created and reviewed:

startup.sh


Contents:

python3 backdoor.py


### Reviewed file permissions

ls -l

Observed:

- Owner: mia
- File had execute permissions enabled
- Multiple users had the ability to execute the script

### Reviewed user cron jobs

crontab -l

Result:

no crontab for mia


### Reviewed system cron locations

ls /etc/cron*

Observed common system tasks:

- apt-compat
- dpkg
- logrotate
- man-db
- e2scrub_all

## Findings

Startup scripts and cron jobs can be used as persistence mechanisms. The startup script contained a suspicious Python command:

python3 backdoor.py


No suspicious cron entries were identified during investigation.

## Conclusion

Persistence mechanisms should be investigated by reviewing file contents, ownership, permissions, startup behavior, and scheduled tasks before determining malicious intent.
