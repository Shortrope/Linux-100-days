# Mounting / Unmounting File Systems

    mount /dev/sdc1 /data

Auto mount at boot with /etc/fstab

    LABEL=DATA  /data   ext4    defaults    1 2

## `mount`

    man mount               # Check out 'independent mount options'
        auto        Can be mounted w the -a option
        remount     Attempt to remount an already mounted fs - make a ro fs writable

    mount                   # list all mount points and fs types and options
    mount -t ext4           # list only specific file types

    mount /dev/sdc1 /data   # mount a file system
    mount -o remount,rw /dev/sdc1 /data

Gets the info from /etc/mtab -> /proc/self/mounts

## `umount`

    umount /dev/sda1
    umount /data
    umount -L DATA -t xfs -o rw,noexec /data

## /media
Used for CD-ROM, DVD, USB Thumb, External drives  
Use 'loop' option for mounting a file 

    mount /root/install.iso -t iso9660 -o rw,loop /media
    mount /root/install.iso -o ro,loop /media