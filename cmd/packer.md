
```
packer build
```

`<bs>` - Backspace
`<del>` - Delete
`<enter>` and `<return>` - Simulates an actual "enter" or "return" keypress.
`<esc>` - Simulates pressing the escape key.
`<f1>` - `<f12>` - Simulates pressing a function key.


```json
{
  "variables": {
  },
  "builders": [{
    "type": "vmware-iso",
    "boot_command": [
      "<enter><wait><<f6><esc><bs><bs><bs><bs><bs><bs><bs><bs><bs><bs><bs><bs><bs><bs><bs><bs><bs>",
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


```json
{
  "variables": {
  },
  "builders": [{
    "type": "vmware-iso",
    "headless":
    "guest_os_type": "ubuntu-64",

    "http_directory": "httpdir",
    "disk_size": "20000",
    "disk_type_id" "thin",
    "vm_name": "ubuntu-1604",

    "output_directory": "ubuntu-1604.vmwarevm",
    "boot_wait": "5s",
    "tools_upload_flavor": "linux",

    "iso_url": "http://releases.ubuntu.com/16.04/ubuntu-16.04.1-server-amd64.iso",
    "iso_checksum": "d2d939ca0e65816790375f6826e4032f",
    "iso_checksum_type": "md5",

    "remote_type": "esx5",
    "remote_host": "192.168.8.179",
    "remote_username": "root",
    "remote_password": "",
    "keep_registered": true,

    "vmx_data": {
      "cpuid.coresPerSocket": "1",
      "memsize": "1024",
      "numvcpus": "2",
      "ethernet0.networkName" ="VM Network"
    },

    "ssh_username": "ubuntu",
    "ssh_password": "insecure",
    "ssh_port": 22,
    "ssh_wait_timeout": "30000s",

    "boot_command": [
      "<enter><wait><<f6><esc><bs><bs><bs><bs><bs><bs><bs><bs><bs><bs><bs><bs><bs><bs><bs><bs><bs>",
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

    "shutdown_command": "echo 'insecure' | sudo -S shutdown -P now"
  }]
}
```

- https://help.ubuntu.com/12.04/installation-guide/example-preseed.txt
- https://help.ubuntu.com/16.04/installation-guide/example-preseed.txt
- https://www.packer.io/docs/builders/vmware-iso.html
- https://www.ibm.com/support/knowledgecenter/pl//SSPLFC_7.3.0/com.ibm.taddm.doc_7.3/SensorGuideRef/r_cmdb_sensor_vmware_troubleshooting.html