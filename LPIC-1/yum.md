# yum - yellow dog updater modified
- originally used for Yellowdog linux distribution
- installs, upgrades and removes packages
- Handles RPM package dependencies
- RHEL, CentOS, Scientific Linux and older Fedora

## yum config
- global yum config in `/etc/yum.conf`
- Reads repo files in `/etc/yum.repos.d/`
- caches repo info in `/var/cache/yum`

## Other RPM package managers
- Zypper: on SUSE Linux
- DNF - Dandified yum
    - Fedora
    - Future replacement for yum in Rhel
    - Same commad syntax as yum

## Commands

    yum update              # upgrades all packages
    yum search <package>
    yum info <package>
    yum list installed      # list all installed packages
    yum clean all           # Clean out the yum db, next yum cmd will re-populate it
    yum install <package>   
    yum remove <package>    # package only, NOT dependencies
    yum autoremove <package>        # remove dependencies
    yum whatprovides */<package>    # What package provides that utility/package
    yum reinstall <package>         # re-download and re-install the package

    # Download package without installing
    yum install yum-utils
    yumdownloader <package>


# RPM
## .rpm package contains
- Application
- config files
- How and where to install
- List of dependencies

## rpm database
- in `/var/lib/rpm`
- yum handles dependencies

corrupt db fix

    rpm --rebuilddb     # Repair a corrupt rpm database

## Commands

    rpm -qpi <package>  # query, package, info
    rpm -qpl <package>  # query, package, list files in package
    rpm -qa             # query all packages
    rpm -ivh <package>  # install, verbose, Hash progress bar
    rpm -Uvh <package>  # update, verbose, Hash progress bar
    rpm -e <package>    # erase / remove
    rpm -Va             # Verify, all packages on the system

    # convert .rpm to and archive .cpio file
    #   cpio -idmv  
    #       -i  extract the archive
    #       -d  keep dir sturcture
    #       -m  keep modified time
    #       -v  verbose

    rpm2cpio <package> | cpio -idmv  