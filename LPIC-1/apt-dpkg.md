# Advanced Package Manager - apt
- For Debian/Ubuntu distributions
- Installs applicatoin and **dependencies**
- Remove apps
- Updates

## How it works:
- Reads `/etc/apt/sources.list`  
    - Url list of repositories you can install software from  
- Directs installation and uninstallition of packages to `dpkg`

## Commands

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

### apt update
Downloads a list of all packages and dependencies into a cache  

### apt upgrade
Upgrades any packeges that have a newer version.. along with dependencies

### apt dis-upgrade
Upgrades all packages to the next release version of the distribution  
Installs new packages required to upgrade - (upgrade does not install new packages)

### apt remove ...
- Removes the application  
- Does NOT remove config files or dependencies
- Use `apt autoremove` to remove the unused dependencies
- Use `apt purge <package>` to remove the app and config files

# dpkg

    dpkg --info <package>       # same as apt-cache show
    dpkg --status <package>     # like 'info' but for currently installed app
    dpkg -l string
    dpkg -i <packages>          # install package
    dpkg -L <package>           # lists all files installed w the package
    dpkg -r <package>           # removes a package.. NOT the config files
    dpkg -P <package>           # purge: removes a package.. AND the config files
    dpkg -S <package>           # search
    dpkg-reconfigure
