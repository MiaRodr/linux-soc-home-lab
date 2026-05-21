# Process Relationship Investigation

## Objective

Investigate process relationships to understand how parent and child processes interact and determine why terminated processes continued to reappear.

## Commands Used

```bash
ps aux | grep sleep
ps -fp 1874
ps -fp 1869
jobs
kill 1874
kill %2
```

## Findings

- Identified active `sleep` processes running under user `mia`
- Process `sleep 9999` was observed with PID `1874`
- Process tracing identified Parent Process ID (PPID) relationships
- Repeated `sleep 30` processes continued appearing with new PIDs after termination
- Child processes were recreated even after individual termination
- Background process `./updater.sh` continued running and creating new child processes

## Analysis

Process investigation showed that terminating the child process temporarily removed the active process but did not eliminate the source of activity.

Repeated process creation occurred because the parent process remained active and continued spawning new child processes. Tracing process relationships through PID and PPID analysis identified that the `updater.sh` background script was responsible for creating additional `sleep` processes.

This investigation demonstrated the importance of identifying process origins instead of focusing only on visible activity.

## Conclusion

The repeated process activity was determined to be expected behavior because the process originated from a user-created script within the controlled lab environment.

Terminating the parent process successfully stopped repeated child process creation.

## Recommended Actions

- Investigate parent-child process relationships during process analysis
- Trace suspicious activity using PID and PPID information
- Determine the originating process before terminating activity
- Avoid assuming repeated process activity automatically indicates compromise
- Investigate root causes rather than only symptoms

## Skills Practiced

- Process investigation
- PID analysis
- PPID analysis
- Parent-child process relationships
- Background job investigation
- Process termination
- Evidence-based analysis
