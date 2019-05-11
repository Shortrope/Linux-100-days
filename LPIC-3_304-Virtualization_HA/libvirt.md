# libvirt

- Manages virtualization platforms
- Supports:
    - ESX
    - Xen
    - KVM
    - Qemu
    - LXC
- Remote machine support
- Manage storage
- Manage Networking

Common tools
- virsh
- virt-install
- virt-manager

## Networking
Default switch VMs connect to `virbr0`  
Mode: NAT using IP masquerading  
Each nSwitch has an instance of `dnsmasq` for dhcp  

### Switch Routing Types
- Routed
- Isolated
- NAT

### Virsh sub-commands for vNetworks

    net-list
    net-start
    net-destroy
    net-undefine
    net-edit
    net-dumpxml

## Storage
Supported Storage Pools
- Filesystem
- NFS
- Directory
- LVM Volume
- Disk
- iSCSI
- Gluster

### Storage Management Commands
virsh
- pool-build
- pool-define-as
- delete
- destroy
- edit
- list
- start

## Build a Storage Pool
    virsh pool-define-as lvm_pool logical --source-name vg-libvirt --target /dev/vdb1
    virsh pool-build lvm_pool
    virsh pool-start lvm_pool
    virsh pool-autostart lvm_pool
    virsh pool-list --all
    virsh vol-create-as lvm_pool vol1 8G
    virsh vol-create-as lvm_pool vol2 8G
    virsh vol-list lvm_pool
    virsh pool-destroy lvm_pool
