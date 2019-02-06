# Runlevels

| Runlevel | Purpose |
| -------- | ------- |
| 0 | Halt |
| 1 | Single user Mode |
| 2 | Multi user (no networking) |
| 3 | Multi user (with networking) |
| 4 | unused |
| 5 | Multi user with networking and Gui |
| 6 | reboot |

## Current runlevel

    runlevel

## Change runlevel

    telinit <runlevel>
    init <runlevel>

# systemd targets
- state w just a command line: multi-user.target
- state w a desktop environment: graphical.target

May have several `unit`s that support a target  

sysint.target  
basic.target  
rescue.target - like runlevel 1  
multi-user.target - like runlevel 3  
graphical.target - like runlevel 5 

    man 5 systemd.target
    man 7 systemd.special

## View a target file

    systemctl cat graphical.target

## List unit files

    systemctl list-unit-files -t target

## List active target units

    systemctl list-units -t target

## Default target

    systemctl get-default
    systemctl set-default multi-user.target

## Change current target (like changing runlevels)
The target must be '`isolated`'

    systemctl isolate multi-user.target
    or
    systemctl multi-user.target
    systemctl reboot.target
    systemctl poweroff.target




