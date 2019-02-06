# LVM Logical Volume Manager

Cannot be mounted for the /boot

- allows resizing of volumes
- Snapshots: allows 'point in time' copies of your logical volume

PV: Physical Volumes: /dev/sda, /dev/sdb  
VG: Volume Group: contains physical volumes - vg_base  
LV: Logical Volume: lv_root, lv_var, lv_swap, lv_home  
File System created on LV  

Commands

    pvs     # physical volume scan
    vgs     # volume group scan
    lvs     # logical volune scan


