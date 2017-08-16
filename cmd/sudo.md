`sudo, sudoedit — execute a command as another user`

```
shell> visudo
shell> vi /etc/sudoers
```
```
# Allow members of group sudo to execute any command
%sudo   ALL=(ALL:ALL) ALL

# Uncomment to allow members of group sudo to not need a password
%sudo ALL=NOPASSWD: ALL
```
```
shell> groupadd sudo
shell> usermod -G sudo <username>
shell> sudo su -

shell> sudo -H -s
shell> sudo -K
```

```
sudo: unable to resolve host 
```
