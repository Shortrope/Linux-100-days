# Reboot and Shutdown

## Reboot

    telinit 6
    reboot
    shutdown -r now
    systemctl reboot.target

## Shutdown

    telinit 0
    halt
    shutdown -h 1 min       # this will invoke 'wall' command
        - ctrl - C  will cancel the shutdown
    systemctl poweroff.target
    systemctl shutdown.target
    poweroff

### Send messages to logged in users

    wall
    <type message> System going down in 2 min!
    crtl - D

## ACPId
Advanced Configuration and Power Interface  

Registers events
- laptop lid closing
- hitting the power button
- ctrl-alt-del
- kbd input
- mouse movent

Power Management  

    ll /etc/acpi/events  
    ll /etc/acpi/actions  
