# Xen

Supports Hardware and Paravirtualization  
Support for Xen is built into the kernel since ver 3  
Taken out of Rhel/CentOS 6

Virtualization Extentions must be enabled in the bios for HW virtualization  

Use LVM  
Install bridge-utils  
Config a new bridge  (/etc/network/interfaces)

    # auto enp0s3
    # iface enp0s3 inet dhcp

    auto xenbr0
    iface xenbr0 inet dhcp
    bridge_ports enp0s3

Bring the bridge up

    ifdown enp0s3 && ifup xenbr0

Network manager may cause problems

    NetworkManager.service


## Install
### Rhel/CentOS

    /etc/yum.repos.d/CentOS-Base.repo       # must have CentOS-Extras repo enabled
    yum install centos-release-xen
    yum update
    yum install xen
    yum groupinstall 'Virtualization'

### Ubuntu

    apt update && apt upgrade -y
    apt install xen-system-amd64        # for Debian install: xen-linux-system

## Reboot into Xen kernel
Done for you automatically  
see /etc/default/grub.d/

## Cmds

    xl list             # list all domains
    xl info             # info about xen host
    xl top              # real time info about domains
        console
        destroy
        dmesg
        migrate
        reboot
        restore
        save
        shutdown

    apt install xen-tools
    /etc/xen-tools/xen-tools.conf
    /usr/share/xen-tools/               # list of OS's you can use w xen tools

    xen-create-image
    xen-list-images
    xen-delete-image

    xen-create-image --hostname=web1 \
                     --lvm=mubuntu_vg \
                     --vcpus=1 \
                     --memory=256M \
                     --maxmem=512M \
                     --size=8G \
                     --swap=1000m \
                     --dhcp
                     --dist=jessie

    xenstore-ls
    xenstore-..

## Xen Project Management API (XAPI)
`xe` command line tool

    xe <cmd> <arg=val>                                  # from xen dom0
    xe -s <host> -u <username> -pw <passwd> <cmd>       # from remote host

