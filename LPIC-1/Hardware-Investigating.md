# Investigating Hardware

## `udev`: Linux device manager (service)
all communication goes thru the `D-Bus`  

udev > dbus > /dev  
lsblk > dbus > /dev  

## `lspci`
Qweries the /dev directory and lists all devices connected to the pci bus  
`-k` show kernel modules used by the devices

## `lsusb`
`-t` tree view

## `lscpu`

## `lsblk`
`-f` see the file system on each partition

