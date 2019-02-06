# GRUB
## Legacy GRUB
Grand Unified Boot loader

Bios  
 |  
Stage 1: boot.img - MBR (first 512bytes), on drive marked w boot flag  
 |  
Stage 1.5: core.img - locates the boot partition  
 |  
Stage 2: /boot/grub, grub.conf or menu.lst, device.map

### install GRUB
    grub-install /dev/vda1
    grub-install '(hd0)'

The grub shell

    grub> help
    grub> find /grub/stage1
    grub> quit


## GRUB2
### MBR vs GPT
MBR
- 26 total partitions
- partition size 2TB max

GPT
- 128 partitions
- partition size in ZB range
- Needs UEFI to boot
    - Replacement fo rtraditional BIOS
    - Requires 64bit OS
    - Prevents unauthorized OSs from bootin gon the system

### GRUB2 on GPT w UEFI
UEFI BIOS  
 |  
Stage 1: boot.img - MBR (first 512bytes), on drive marked w boot flag  
 |  
GPT Header - Partition Entry Array  
 |  
Stage 1.5: core.img - locates the boot partition  
 |  
ESP partition /boot/efi, must be vfat or fat32  
 |  
Stage 2: boot/grub2 - grubenv and themes

### GRUB2 config commands
- Rhel - grub2-cmd
- Debian - grub-cmd

commands

    grub2-editenv list
    grub2-mkconfig      # modifies /boot/grub2/grub.cfg
    update-grub         # debian based

    vim /etc/default/grub
    grub2-mkconfig 

/etc/grub.d/:  These files used to create the grub.cfg file
    00_header
    ...
    04_custom

## Interacting with the boot loader
### Legacy
Press the 'a' key on any of the kernel boot options to modify that boot option  
Press the 'c' key for the boot command line
- help
- reinstall grub
    - setup (hd0)
- read files

### GRUB2
Press the 'e' key on any of the kernel boot options to modify that boot option  
- systemd.unit=rescue.target  
- ctrl-x or F10 to boot


Press the 'c' key for the boot command line  
- `ls` to view partitions
- `ls (hd0, 1)/`  lists files in a partition
- `set root=(hd0,1)`   set root partition
- `linux /boot/vmlinuz-tab-complete root=/dev/vda1` 
- `initrd /boot/initrd.img-tab-complete`     setup initial ram disk
- `boot`

