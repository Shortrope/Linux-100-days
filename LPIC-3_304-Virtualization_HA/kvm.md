# KVM

- qcow2 is the only format that supports snapshots

Default storage location for images: /var/lib/libvirt/images

## Create disk images

    dd if=/dev/zero of=/path/to/disk_img bs=1M count=10240          # creates a raw image file
    or
    qemu-img create -f qcow2 /path/to/disk_img 10G                  # qcow: QEMU copy on write

## Networking
### user networking
The VM can communicate out but nothing can communicate in

    qemu-kvm -hda /path/to/hda.img
    or
    qemu-kvm -hda /path/to/hda.img \
             -netdev user,id=net0  \
             -device e1000,netdev=net0

*For Debian/Ubunt us qemu-system-x86_64 instead of qemu-kvm

### Private Bridge
VMs can communicate with each other

    ip
    brctl   # deprecated - use ip link instead
    tunctl  # deprecated - use ip tuntap and ip link instead

    ip link add br0 type bridge
    qemu-kvm -hda /path/to/hda.img \
             -device e1000,netdev=net0,mac=xxxxxxxx \
             -netdev tap,id=net0,script=/path/to/qemu-ifup 

### Public Bridge
looks the same as a private bridge



## Install
    lsmod | grep kvm

    modprobe kvm
    modprobe kvm_intel

    ll /dev/kvm


## KMV Utilities
### qemu-ga
### qemu-img

    check
    create
    commit
    compare
    convert
    info
    map
    snapshot        # 
    rebase
    resize
    amend

## qemu-nbd

## qemu-kmv, qemu-system-x86_64
Main Qemu command utility

    qemu-system-x86_64 --drive file=ssh://user@host/path/to/disk.img
    qemu-system-x86_64 --drive file=nbd:192.168.1.44:30000
