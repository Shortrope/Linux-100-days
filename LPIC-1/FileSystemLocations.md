# Disk partitions
Commands

    mount
    lsblk
    fdisk -l /dev/sdx
    swapon --summary

# FHS (Filesystem Hierarchy Standard)
http://www.pathname.com/fhs/  

# Find files on the filesystem
## `locate`
looks for files containing a string  
Creates a db of file names and locations  
/etc/updatedb.conf  

    locate <filename>
    updatedb                # updates the db
    whereis                 # locacets binary, source and manual pages



