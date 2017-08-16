<img src="http://i.imgur.com/q56y6pm.png" alt="" width=300> 

> `LVM` 是`逻辑盘卷管理`(`Logical Volume Manager`)的简称

> `LVM` 通过在硬盘和分区之间建立一个逻辑层，可以让多个分区或者物理硬盘作为一个逻辑卷 ( 相当于一个逻辑硬盘 )，提高了磁盘分区管理的灵活性。
> `物理卷` `physical volumes`(`PV`)
> `逻辑卷` `logical volumes`(`LV`)
> `卷组` `logical volume group`(`VG`)




`PhysicalVolume`
`VolGroup00` 

```
dd if=/dev/zero of=PhysicalVolume bs=512 count=1

pvcreate /dev/sdd1 /dev/sde1 /dev/sdf1
pvcreate /dev/hdb1
pvcreate /dev/sdb
pvremove

pvs --all
pvdisplay
pvscan
vgs --all
vgdisplay
vgscan
lvs --all
lvdisplay
lvscan

vgs -v
vgdisplay
vgremove

pvscan
vgscan
lvscan

lvmdiskscan
pvs -o+pv_used
```

`pvs — report information about physical volumes`
`vgs — report information about volume groups`
`lvs — report information about logical volumes`
`vgdisplay — display attributes of volume groups`
`pvmove — move physical extents`

`Linux LVM`
`8e`

```
shell> fdisk -c /dev/sdb

shell> pvcreate /dev/sdb1
shell> pvdisplay /dev/sdb1

shell> vgextend vg1 /dev/sdb1
shell> vgdisplay vg1

shell> lvscan
shell> lvdisplay -v
shell> lvresize -l +100%FREE /dev/myvg/testlv
shell> lvresize -l +100%PVS /dev/myvg/testlv /dev/sdb1 
shell> resize2fs -p /mount/device node

shell> lsblk
```

`100%FREE`
`100%VG`
`100%PVS`


```
shell> pvmove /dev/sdb1
shell> vgreduce myvg /dev/sdb1
```

```
shell> pvdisplay /dev/hda1
shell> vgreduce my_volume_group /dev/hda1
shell> pvmove /dev/sdb1 /dev/sdc1
```

#### :books: 參考網站：
- https://www.centos.org/docs/5/html/Cluster_Logical_Volume_Manager/physical_volumes.html
- https://www.centos.org/docs/5/html/Cluster_Logical_Volume_Manager/physvol_create.html
- https://docs.fedoraproject.org/en-US/Fedora/14/html/Storage_Administration_Guide/ext4grow.html
- https://access.redhat.com/documentation/en-US/Red_Hat_Enterprise_Linux/4/html/Cluster_Logical_Volume_Manager/disk_remove_ex.html
- https://kb.vmware.com/selfservice/microsites/search.do?language=en_US&cmd=displayKC&externalId=1006371
- https://www.ibm.com/support/knowledgecenter/en/SSZJY4_3.1.0/liabp/liabplvmcommands.htm
- https://www.ibm.com/developerworks/cn/linux/l-cn-pclvm-rstr/