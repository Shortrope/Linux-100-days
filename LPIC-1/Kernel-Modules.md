# Kernel Modules

## GNU
Tools you use on the system
- shells
- ls

## Kernel
System to operate w hardware, memory, networking and itself
- The Linux kernel is monolithic:  
    - handles all memory management and hardware device interactions 
    - Extra functionality can be loaded and unloaded dynamically w _kernel modules_
    - The system will not need to be rebooted into a diff kernel image for added functionality
    - ability to load an unload drivers
- Many third-party linux kernel modules are device drivers

## uname command
uname gives us info about the kernel

    -a, --all
            print all information, in the following order, except omit -p and -i if unknown:

    -s, --kernel-name
            print the kernel name

    -n, --nodename
            print the network node hostname

    -r, --kernel-release
            print the kernel release

    -v, --kernel-version
            print the kernel version

    -m, --machine
            print the machine hardware name

    -p, --processor
            print the processor type (non-portable)

    -i, --hardware-platform
            print the hardware platform (non-portable)

    -o, --operating-system
            print the operating system

    --help display this help and exit

    --version
            output version information and exit

## `lsmod` command
List kernel modules.  
Its just a nicely formated display of /proc/modules file.  
It show the module name, mem used, dependent modules  
### `modinfo <module name>`: displays info about a specific module

## `modprobe`
Dynamically load/unload a kernel module

    modprobe floppy
    modprobe -r floppy