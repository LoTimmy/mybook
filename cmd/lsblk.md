`lscpu - display information about the CPU architecture`

`lsusb - list USB devices`

`lspci - list all PCI devices`

`lsblk - list block devices`

`lshw - list hardware`

`dmidecode - DMI table decoder`


```
shell> lscpu
shell> lsusb
shell> lspci
shell> lspci -v

shell> lsblk
shell> lsblk -f
shell> lshw
```

```
shell> apt-get install dmidecode
shell> dmidecode -t
shell> dmidecode -t 16
shell> dmidecode -t 17
shell> dmidecode -t memory
shell> dmidecode -t system
shell> dmidecode -t processor
shell> dmidecode -t bios
```