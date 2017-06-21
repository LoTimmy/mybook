
### 安裝 {#installing}

```console
shell> 
```

`Tool for creating identical machine images for multiple platforms`

- `<bs>` - Backspace
- `<del>` - Delete
- `<enter>` and `<return>` - Simulates an actual "enter" or "return" keypress.
- `<esc>` - Simulates pressing the escape key.
- `<f1>` - `<f12>` - Simulates pressing a function key.


```json
{
  "variables": {
  },
  "builders": [{
    "type": "vmware-iso",
    "boot_command": [
      "<enter><wait><f6><esc><bs><bs><bs><bs><bs><bs><bs><bs><bs><bs><bs><bs><bs><bs><bs><bs><bs>",
      "<bs><bs><bs><bs><bs><bs><bs><bs><bs><bs><bs><bs><bs><bs><bs><bs><bs><bs><bs><bs><bs><bs>",
      "<bs><bs><bs><bs><bs><bs><bs><bs><bs><bs><bs><bs><bs><bs><bs><bs><bs><bs><bs><bs><bs><bs>",
      "<bs><bs><bs><bs><bs><bs><bs><bs><bs><bs><bs><bs><bs><bs><bs><bs><bs><bs><bs><bs><bs><bs>",
       "/install/vmlinuz noapic ",
       "preseed/url=http://{{ .HTTPIP }}:{{ .HTTPPort }}/preseed.cfg ",
       "debian-installer=en_US auto locale=en_US kbd-chooser/method=us ",
       "hostname={{ .Name }} ",
       "fb=false debconf/frontend=noninteractive ",
       "keyboard-configuration/modelcode=SKIP keyboard-configuration/layout=USA ",
       "keyboard-configuration/variant=USA console-setup/ask_detect=false ",
       "initrd=/install/initrd.gz -- <enter><wait>"
    ],
    "http_directory": "httpdir",
    "disk_size": "20000",
    "vm_name": "ubuntu-1604",
    "vmx_data": {
      "cpuid.coresPerSocket": "1",
      "memsize": "1024",
      "numvcpus": "2"
    },
    "output_directory": "ubuntu-1604.vmwarevm",
    "boot_wait": "5s",
    "tools_upload_flavor": "linux",
    "guest_os_type": "ubuntu-64",
    "iso_url": "http://releases.ubuntu.com/16.04/ubuntu-16.04.1-server-amd64.iso",
    "iso_checksum": "d2d939ca0e65816790375f6826e4032f",
    "iso_checksum_type": "md5",
    "ssh_username": "ubuntu",
    "ssh_password": "insecure",
    "ssh_port": 22,
    "ssh_wait_timeout": "30000s",
    "shutdown_command": "echo 'insecure' | sudo -S shutdown -P now"
  }]
}

```            

#### :books: 參考網站：

- https://www.packer.io/docs/builders/virtualbox-iso.html
- https://www.packer.io/docs/builders/vmware-iso.html
- https://www.packer.io/docs/builders/vmware-vmx.html
- https://www.packer.io/docs/builders/virtualbox-iso.html

---

```
shell> esxcli system settings advanced set -o /Net/GuestIPHack -i 1
```

```
shell> cat <<EOF > /etc/vmware/firewall/vncServer.xml
<ConfigRoot>
  <service>
    <id>vncServer</id>
    <rule id='0000'>
      <direction>inbound</direction>
      <protocol>tcp</protocol>
      <porttype>dst</porttype>
      <port>
        <begin>5900</begin>
        <end>5999</end>
      </port>
    </rule>
    <enabled>true</enabled>
    <required>false</required>
  </service>
</ConfigRoot>
EOF
shell> esxcli network firewall refresh
shell> esxcli network firewall ruleset list
```

#### :books: 參考網站：
- https://www.netiq.com/documentation/cloudmanager22/ncm22_reference/data/bxzaz5n.html

`PACKER_LOG=1`

`PACKER_LOG_PATH="packerlog.txt"`

```json
{
  "builders": [{
    "type": "vmware-iso",
    "headless": "false",
    "guest_os_type": "ubuntu-64",

    "http_directory": "httpdir",
    "disk_size": "20000",
    "disk_type_id": "thin",

    "output_directory": "ubuntu-64",
    "boot_wait": "5s",
    "tools_upload_flavor": "linux",

    "iso_urls": ["ubuntu-16.04.2-server-amd64.iso", "http://releases.ubuntu.com/16.04/ubuntu-16.04.2-server-amd64.iso"],
    "iso_checksum": "2bce60d18248df9980612619ff0b34e6",
    "iso_checksum_type": "md5",

    "floppy_files": [
      "preseed.cfg"
    ],

    "remote_type": "esx5",
    "remote_host": "{{user `remote_host`}}",
    "remote_username": "{{user `remote_username`}}",
    "remote_password": "{{user `remote_password`}}",
    "remote_datastore": "{{user `remote_datastore`}}",
    "keep_registered": true,

    "vm_name": "ubuntu-64",
    "vmx_data": {
      "cpuid.coresPerSocket": "1",
      "memsize": "1024",
      "numvcpus": "2",
      "ethernet0.networkName": "VM Network"
    },

    "ssh_username": "ubuntu",
    "ssh_password": "insecure",
    "ssh_port": 22,
    "ssh_wait_timeout": "30000s",

    "boot_command": [
      "<enter><wait><f6><esc><bs><bs><bs><bs><bs><bs><bs><bs><bs><bs><bs><bs><bs><bs><bs><bs><bs>",
      "<bs><bs><bs><bs><bs><bs><bs><bs><bs><bs><bs><bs><bs><bs><bs><bs><bs><bs><bs><bs><bs><bs>",
      "<bs><bs><bs><bs><bs><bs><bs><bs><bs><bs><bs><bs><bs><bs><bs><bs><bs><bs><bs><bs><bs><bs>",
      "<bs><bs><bs><bs><bs><bs><bs><bs><bs><bs><bs><bs><bs><bs><bs><bs><bs><bs><bs><bs><bs><bs>",
      "/install/vmlinuz noapic ",
      "preseed/file=/floppy/preseed.cfg ",
      "debian-installer=en_US auto locale=en_US kbd-chooser/method=us ",
      "hostname={{ .Name }} ",
      "fb=false debconf/frontend=noninteractive ",
      "keyboard-configuration/modelcode=SKIP keyboard-configuration/layout=USA ",
      "keyboard-configuration/variant=USA console-setup/ask_detect=false ",
      "initrd=/install/initrd.gz -- <enter><wait>"
    ],

    "shutdown_command": "echo 'insecure' | sudo -S shutdown -P now"
  }]
}
```

`variables.json`
```
{
  "remote_host": "192.168.8.196",
  "remote_username": "root",
  "remote_password": "",
  "remote_datastore": "datastore1",
}
```

`preseed.cfg`

```
# https://help.ubuntu.com/lts/installation-guide/example-preseed.txt

d-i debian-installer/language string en
d-i debian-installer/locale string en_US.UTF-8
d-i localechooser/supported-locales en_US.UTF-8

d-i console-setup/ask_detect boolean false
d-i keyboard-configuration/xkb-keymap select us

d-i netcfg/choose_interface select auto
d-i netcfg/get_hostname string ubuntu
d-i netcfg/get_domain string unassigned-domain

d-i passwd/user-fullname string Ubuntu User
d-i passwd/username string ubuntu
d-i passwd/user-password password insecure
d-i passwd/user-password-again password insecure
d-i user-setup/allow-password-weak boolean true
d-i user-setup/encrypt-home boolean false

d-i clock-setup/utc boolean true
#d-i time/zone string US/Eastern
d-i time/zone string Asia/Taipei
d-i clock-setup/ntp boolean true
d-i clock-setup/ntp-server string time.asia.apple.com

d-i partman-auto-lvm/guided_size string max
d-i partman-auto/choose_recipe select atomic
d-i partman-auto/method string lvm
d-i partman-lvm/confirm boolean true
d-i partman-lvm/confirm boolean true
d-i partman-lvm/confirm_nooverwrite boolean true
d-i partman-lvm/device_remove_lvm boolean true
d-i partman-partitioning/confirm_write_new_label boolean true
d-i partman/choose_partition select finish
d-i partman/confirm boolean true
d-i partman/confirm_nooverwrite boolean true

d-i partman-partitioning/confirm_write_new_label boolean true

d-i mirror/http/proxy string

tasksel tasksel/first multiselect standard
d-i pkgsel/include string openssh-server 
d-i pkgsel/update-policy select none
d-i pkgsel/upgrade select none

d-i grub-installer/only_debian boolean true

d-i finish-install/reboot_in_progress note
```

```
shell> packer build -var-file=variables.json ubuntu-16.04.2-server-amd64.json
```

#### :books: 參考網站：
- https://help.ubuntu.com/12.04/installation-guide/example-preseed.txt
- https://help.ubuntu.com/16.04/installation-guide/example-preseed.txt
- https://www.packer.io/docs/builders/vmware-iso.html
- https://www.ibm.com/support/knowledgecenter/pl//SSPLFC_7.3.0/com.ibm.taddm.doc_7.3/SensorGuideRef/r_cmdb_sensor_vmware_troubleshooting.html
- https://www.packer.io/docs/other/debugging.html
- https://www.packer.io/docs/templates/user-variables.html



---




      "communicator": "ssh"
      "communicator": "winrm"

"winrm_username": ""
"winrm_password": ""
"winrm_timeout": "30m"


#### :books: 參考網站：
- https://www.packer.io/docs/templates/communicator.html
- https://www.packer.io/docs/builders/hyperv-iso.html