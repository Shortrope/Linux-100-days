# Pseudo File Systems

Only exists in RAM while the system is up and running  
Everthing is plain text files  
2 main Pseudo file systems  
- /proc
- /sys

## /proc
directories for each process - pid  
Cpuinfo, uptime, version, partitions...  
Check the 'cmdline' file for a process id  

## /sys
Hardware and the kernel is exposed in plain text files here  
- fs: filesystem 
    - error, log, stats for the filesystem
- module
- dev

## /dev
Actual file handles for hardware devices




