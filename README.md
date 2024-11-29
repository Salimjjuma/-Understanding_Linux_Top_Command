# Understanding Linux Top Command

The top command is a powerful Linux utility that provides real-time insights into system performance, resource usage, and processes.

> Understanding the output of top helps identify resource bottlenecks, troubleshoot high resource usage, and manage processes effectively.

Below is a breakdown of its output to help you understand it better:

## Top Section (System Overview)

1. First Line Summary

```bash
top - 12:45:32 up 2 days,  4:17,  2 users,  load average: 0.34, 0.29, 0.23
```

- `12:45:32`: Current system time.
- `up 2 days, 4:17`: System uptime (how long the system has been running).
- `2 users`: Number of logged in users.
- `load average: 0.34, 0.29, 0.23`: The system load average over the last 1, 5, and 15 minutes.
  - **Load Average** indicates the average number of active processes.
  - A value close to the number of CPU cores suggests the system is fully utilized.

2. Task Summary

```bash
Tasks: 130 total, 1 running, 129 sleeping, 0 stopped, 0 zombie

```

- `130 total`: Total no of processes.
- `1 running`: Processes currently executing on the CPU.
- `129 sleeping`: Processes waiting for resources or events.
- `0 stopped`: processes stopped or paused (e.g. via ctrl+Z).
- `0 zombie`: Zombie processes(terminated processes waiting for their parent to collect their status).

3. CPU Usage.

```scss
%Cpu(s): 2 us, 1 sy, 0 ni, 96.5 id, 0.5 wa, 0 hi, 0 si, 0 st;
```

- `2.0 us` : Percentage of CPU time spent on user-space processes (non kernel processes).

- `1.0 sy`: Percentage of CPU time spent on system/kernel processes.

- `0.0 ni`: Percentage of CPU time spent on processes with altered priority(nice value).

- `95.6 id`: Percentage of CPU time spent idle (not doing work).

- `0.5wa`: Percentage of CPU time spent waiting for I/O operations.

- `0.0 hi`: Percentage of CPU time spent on hardware interrupts.

- `0.0 si`: Percentage of CPU time spent on software interrupts.

- `0.0 st`: PercentageMiB Mem : 7982.3 total, 3200.5 free, 2000.3 used, 2781.5 buff/cache
  MiB Swap: 2048.0 total, 1800.5 free, 247.5 used. 5000.0 avail Mem
  of CPU time stolen by the hypervisor in virtualized environment.

4. Memory Usage.

```yaml
MiB Mem: 7982.3 total,  3200.5 free,  2000.3 used,  2781.5 buff/cache
MiB Swap: 2048.0 total,  1800.5 free,   247.5 used.  5000.0 avail Mem
```

- Memory (RAM):

  - `7982.3 total`: Total Pyhsical Memory.
  - `3200.5 free`: Memory not currentlu used.
  - `200.3 used`: Memory actively used by processes.
  - `2781.5 buff/cache`: Memory used for buffers and cache (used temporarily but available for use if needed).

- Swap:
  - `2048.0 total`: Total swap space (disk space used as memory overflow).
  - `1800.5 free`: Swap space not in use.
  - `247.5 used`: Swap space currenly used.
  - `5000.0 avail Mem`: Memory available for use, including free and reclaimable cache.

## Lower Section (Process List)

The process list shows active processes with details. Here's a typical row and its explanation:

```perl

PID   USER      PR  NI    VIRT    RES    SHR S  %CPU  %MEM     TIME+ COMMAND

```

1. Columns in details.

- `PID`: Process ID(unique identifier for the process).

- `USER`: User account that owns the process.
- `PR`: Priority of the process.

  > Lower number indicate higher priority.

- `NI`: Nice Value(Priority modifier).

  > Negative values = higher priority; positive values = lower priority.

- `VIRT`: Virtual memory used by the process.
- `RES`: Resident memory (actual physical memory used by the process).
- `SHR`: Shared memory (shared with other processes).

- `S`: Process state

  - `R`: Running.
  - `S`: sleeping.
  - `D`: Uninterruptible sleep (usually waiting for I/O).
  - `Z`: Zombie
  - `T`: Stopped

- `%CPU`: Percentage of CPU time used by the process.
- `%MEM`: Percentage of RAM used by the process.
- `TIME+`: Total CPU time used by the process (since it started)
- `COMMAND`: Name of the command or process.

## Useful Interactions

You can interact with top while it is running:

`h`: Help screen.
`k`: Kill a process (you'll need to enter the PID).
`r`: Renice a process (change its priority).
`P`: Sort by CPU usage.
`M`: Sort by memory usage.
`T`: Sort by process runtime.
`q`: Quit top.
