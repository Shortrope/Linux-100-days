# Boot Process

Bios  
  |  
Boot sector  
  |  
Linux Kernel  
  |  
Initial RAM Disk  
    Loads device drivers  
  |  
Initialization Sysem  
    mount file system  
    removes init RAM disk  
    starts services  


## `init`
Based on system V init in Unix systems  
Services are started one after the other  

- locates and runs /sbin/init
- reads the config settings in /etc/inittab

/sbin/init  
  |  
/etc/inittab  
  |  
/etc/rc.d/rc.sysinit  
  |  
/etc/rc.d/rcx.d (in sequential order)  
  |  
login prompt  


### /etc/inittab

\<identifier>:\<runlevel>:\<action>:\<process>

| Runlevel | Purpose |
| -------- | ------- |
| 0 | Halt |
| 1 | Single user Mode |
| 2 | Multi user (no networking) |
| 3 | Multi user (with networking) |
| 4 | unused |
| 5 | Multi user with networking and Gui |
| 6 | reboot |


### Startup scripts

Rhel:   /etc/rc.d/  
Debian: /etc/init.d  

## Upstart init
**rarely used any more**
- First used on Ubuntu
- Then in RHEL 6, Debian and Fedora 9
- Offers asynchonous starting of services - faster boot time
- Works off of real-time events
- monitors services for their availability

### Job states
waiting - starting - running - stopping - killed - post-stop - waiting
respawning

## Systemd
- Gets rid of shell scripts - they relied on Bash 
- replaces shell scripts w compiled C code
- still compatible with system V init scripts

### Unit Files
- found in /usr/lib/systemd/system
- admins can edit /etc/systemd/system
- Runtime unit files: /run/systemd/system

View all unit files with

    systemctl list-unit-files

    systemctl cat xyz.unit
    systemctl cat httpd.service