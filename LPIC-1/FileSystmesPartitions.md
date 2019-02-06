# Partitions and File systems

    lsblk

## fdisk
Legacy command to create MBR (DOS) partitions  
- 4 primary partitions
- 23 logical partitions

cmds

    fdisk /dev/sda
    m               # help
    p               # print partition table
    n               # create new partition
    w               # write partition table

    Id 83           # Linux partition
    Id 82           # Swap partition
    Id 8e           # Linux LVM volumes

    fdisk -l /dev/sda   # list partition table of a disk

## parted
Modern command to create MBR or GPT partitions  

    parted /dev/sda
    help
    p               # print partition table
    mklabel msdos   # create MBR 
    mkpart          # create partition
        - primary
        - type      # ext2 default - same as ID 83 label
        - start? 1  # start at 1 (megabyte)
        - end? 1000 # creates 1G partition
        quit

    mklabel gpt     # create MBR 
## gdisk
GPT
- 128 partitions

cmds

    gdisk /dev/sda
    ?                   # help - just like fdisk
    p                   # print partitions
    n                   # create new partition
    partition number
    first sector
    last sector  +500M  # no input uses entire disk  
        - ID 8300       # same as 83
    w                   # write to disk
        - proceed y/n   # confirm write
    
## Swap partitions
Can be created w fdisk, gdisk, parted  
Swap can be a 
- file          # slower
- partition     

Swap partition number
- 82
- 8200
- 0x82

After making the partition format as swap

    mkswap -L SWAP /dev/sda2        # -L label the partition w the name 'SWAP'
    swapon -a                       # -a all swap space listed in fstab
    swapon -U 23452345...           # -U uuid
    swapon -L SWAP                  # -L use label
    swapoff

Edit /etc/fstab so swap is loaded on boot

    /dev/sda2                       # not best practice
                                    # use LABEL or UUID

    LABEL=SWAP  swap    swap    defaults    0 0

## File Sytems
- Non-Journaling
    - ext2 - legacy linux file system
- Journaling
    - ext3 -    added journaling to ext2
    - ext4 -    extra features
    - XFS -     Fast parallel fs. Default on Rhel/CentOS 7

### Btrfs 
- Uses CoW (Copy on Write) 
- Subvolues - like a partition an accessed like a directory
- Snapshot - reference to the original data location, includes metadata and dir structure

### FAT File Systems
- vfat 
    - can use long file names
    - EFI boot requires FAT
- exFAT - Extended FAT
    - Large files, greater than 2G
    - Primarily for external disks for backups

### Create File System

    mkfs -t <fstype> -L SRV /dev/sda1       # -L apply label
    mkfs.<fstype>

    lablk -f                # show fs info and uuid's
    blkid                   # show uuid and labels 
    blkid /dev/sda1

## inodes

    ls -i
    df -i
    du --inode

## Maintain file systems with `fsck`
### `fsck`
/etc/fstab tells if a file system will be checked at boot and in what order.  
Number in last column  

/ is checked 1st  
/boot is check 2nd  
swap is not checked  

    /dev/sda2   /boot   vfat    noatime   0 2
    /dev/sda3   /   ext4    noatime   0 1
    /dev/sdb1   none    swap    sw    0 0

Device must be unmounted before running the check  

    umount /srv
    umount /dev/sda1

    fsck -r /dev/sda1               # Report on /dev/sda1
    fsck -r LABEL=SRV

### `e2fsck`
Check utility for ext2, ext3, ext4 file systems  
Can be used to 'replay' the file systems journal  

    e2fsck /dev/sda1
    e2fsck -f /dev/sda1             # force run
    e2fsck -p /dev/sda1             # force repair

### `mke2fs`
Creating ext2, ext3, ext4 file systems  
Config file: /etc/mke2fs
Used by `mkfs`

    mke2fs -t ext4 -L EXTRA /dev/sda1       # -t fs type, -L label

### `tune2fs`
Adjust parameters on ext2, ext3, ext4

    tune2fs -l /dev/sda1 | less             # list options - tunable
    tune2fs -i 3w /dev/sdb1                 # check interval: every 3 weeks

Check creates a 'lost+found' directory
- lost or damaged data moved to 'lost+found'

### `xfs_repair`
Repair XFS file systems
7 phases

    xfs_repair /dev/sdb1

### `xfs_fsr`
Reorganizes data blocks on XFS  
Similar to 'defrag' on Windows  
fs must be mounted!

    xfs_fsr /opt

### `xfs_db`
Debug XFS  
fs must be unmounted  

    xfs_db
        frag                # check how fragmented
        freesp              # check free space


