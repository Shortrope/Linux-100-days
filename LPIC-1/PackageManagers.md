# Package Manageres
## Apt, Yum, Emerge

## Search
    apt-cache search package  
    yum search package  
    yum whatprovides name  
    emerge --search package  
    emerge --searchdesc package  

## Install
    apt install package  
    yum install package  
    emerge -atv package     # --ask --tree --verbose  (dependency tree)  

## Uninstall
    apt remove package  
    apt purge package  
    yum remove package  
    yum autoremove package  
    emerge --depclean package  