# Command List


## Systemd boot

    systemctl list-unit-files
    systemctl cat xyz.unit
    systemctl cat httpd.service




## Bash

    env         # Lists all environment variables
    set         # Displays shell settings of shell variables for the session
    set -x      # start debugging
    set +x      # end debugging
    unset       # Removes a variable
    unset -f    # Removes custom function
    shopt       # Displays shell options and their settings
    shopt -s    # set or enable an option



## apt

    cat /etc/apt/sources.list
    apt update
    apt upgrade
    apt dist-upgrade
    apt install <package>
    apt remove <package>    # keeps config files and dependecies
    apt autoremove          # removes unused dependencies
    apt purge <package>     # removes  the app and its config files
    apt download            # download but do not install
    apt-cache search <package>
    apt-cache show <package>        # Info about the package
    apt-cache showpkg <package>     # More Info about the package

    dpkg --info <package>       # same as apt-cache show
    dpkg --status <package>     # like 'info' but for currently installed app
    dpkg -l string
    dpkg -i <packages>          # install package
    dpkg -L <package>           # lists all files installed w the package
    dpkg -r <package>           # removes a package.. NOT the config files
    dpkg -P <package>           # purge: removes a package.. AND the config files
    dpkg -S <package>           # search
    dpkg-reconfigure



## File management

    find ./ -empty -type f -exec rm -f {} \;    # run 'rm -f' on each found file

    dd if=infile of=outputfile
    dd if=/dev/vda of=/tmp/mbr.img bs=512 count=1
    dd if=/dev/urandom of=myfile bs=1024 count=10

    tar -cf bu.tar mydir        # -c create, -f out file
    tar -tf bu.tar              # list files in the tarball
    tar -xf bu.tar              # extract the files from the tarball

    tar -czf bu.tar.gz mydir         # -z  use gzip com
    tar -czf bu.tgz mydir            # alternate name extention
    tar -cjf bu.tar.bz2 mydir        # -j  use bzip2 com

    tar -xzf bu.tar.gz          # -x  extract 
    tar -xvjf bu.tar.gz         # -v  verbose 

    gzip file               # replaces the orig file w file-name.gz
    gunzip file.gz

    bzip2 file
    bunzip2 file.bz2

    xz file
    unxz file.xz