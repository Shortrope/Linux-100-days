# File Permissions

    r = read
    w = write
    x = execute
    - = no permissions

    4 = read
    2 = write
    1 = execute
    0 = no permissions

    4 = suid
    2 = sgid
    1 = sticky bit

Owner, Group, Other         # Other sometimes call World 

    - = regular file
    d = directory
    b = block device
    c = character device

## Advanced Permissions

## suid
'Set user id'  
Anyone who executes this file will run it as the user/owner of the file  

Will not work on Bash scripts anymore???  
Many file systems can be mounted w the 'nosuid' option???  
suid: 's' in place of the 'x' for the 'user'

    rwsr-xr-x

See the /usr/bin/passwd

    mario@Mobile-PC:~$ ll `which passwd`
    -rwsr-xr-x 1 root root 59K Jan 25  2018 /usr/bin/passwd*

Set the suid bit

    chmod 4760 file.txt
    chmod u+s file.txt
    chmod 0760 file.txt
    chmod u-s file.txt

## sgid
Set Group ID  
Assigns group ownership to files  
Useful for shared group directories

    rwxrws---

    chmod 1777 file.txt


## sticky bit
Has a 't' inplace of an 'x' in the 'others' column.  
This permission allows only the owner/creator of a file to remove it  
This is given to a directory - /tmp has this permission

    rwxrwxrwt   /tmp


## chmod
Change the mode of a file or dir  

    chmod o-r file.txt 
    chmod -R o-r dir/*
    chmod -R 600 dir/*

## chown
Change the ownership of a file or dir  
Only the root user can change the 'owner' of a file or directory  
Can use a : or a . as a separator  

    chown  mario:devs file.txt
    chown  mario.devs file.txt
    chown  :devs file.txt

## chgrp
Change the group 

    chgrp devs file.txt


# Default permissions

## umask
Default persions for a directory is 777  
Default persions for a files is 666  

    umask           # 0002
    umask           # 0022 for root user

The umask subtracts from full permissions and makes 
- directories 775
- files 664

Permanently config in 
- /etc/bashrc       # for whole system
- ~/.bashrc         # for individual user

Set umask

    umask u=rwx,g=,o=
    umask                   #0077
