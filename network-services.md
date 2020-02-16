# Unit Files

Unit Files location:
    /usr/lib/systemd/system
Run time generated unit files:
    /usr/run/systemd/system 
    *.scope is scope of "this" session

e.g:
HTTPD service:
    /usr/lib/systemd/system/httpd.service
systemctl show httpd
```bash sudo cp /usr/lib/systemd/httpd.service /etc/systemd/system ```
systemctl daemon-reload /reloads all of the daemons
/etc/systemd/system has a higher precedence than /usr/lib/systemd/system/httpd.service

# CGroups (aka: control groups)

shows control group slices:
```bash systemd-cgls```

* slice: grouping of scopes and services together

shows realtime cgroup:
```bash systemd-cgtop```

```bash systemctl show <$SERVICENAME> # shows all of the attributes related to that service.```

Example: memory usage of httpd service:
```bash systemctl show httpd | grep mem # mem is short for memory```
if you would like to limit the memory usage of that service you can change the Unit file of the service. 
 ```bash /etc/systemd/system/httpd.service```

# Journald : systemd's logging mechanism

to create a persistent data storage: 
```bash
mkdir -p /var/log/journal
systemctl restart systemd-journald
```

journalctl -f  # tail
journalctl -o verbose # log entries stored inside of journald
E.g: 
``` 
journalctl _UID=1000  # quering it with UID attribute.
journalctl _SYSTEMD_UNIT=sshd.service 
journalctl --since "1 hour ago"
journalctl --since 09:00
```
* man page for fields: man systemd.journal-fields

# Extended Internet Services Daemon 

* Meta deamon
* Upon connection, the xinetd daemon starts up the approperiate daemon
* Used for the services that have a short life and are infrequently used (TFTP,TELNET: non encrypted
  protocol: used for legacy programs. TCP wrapper)

/etc/xinetd.d
vim tftp
touch /var/lib/tftpboot/file.txt
# server side:
firewall-cmd --permanent --add-port=69/udp
firewall-cmd --reload
# client side:
sudo firewall-cmd --permanent --add-service=tftp-client
sudo firewall-cmd --reload
tftp 192.168.1.1 -c get file.txt

Refrences:
Rethinking PID 1 - http://bit.ly/2b0wZil
https://access.redhat.com/documentation/en-US/Red_Hat_Enterprise_Linux/7/html/System_Administrators_Guide/
chap-Managing_Services_with_systemd.html
https://access.redhat.com/documentation/en-US/Red_Hat_Enterprise_Linux/7/html/System_Administrators_Guide/
sect-Managing_Services_with_systemd-Unit_Files.html
https://access.redhat.com/documentation/en-US/Red_Hat_Enterprise_Linux/7/html/System_Administrators_Guide/
sect-Managing_Services_with_systemd-Targets.html
https://www.freedesktop.org/software/systemd/man/systemd.unit.html
https://www.freedesktop.org/software/systemd/man/systemd.html
https://www.freedesktop.org/software/systemd/man/systemd.service.html
https://www.freedesktop.org/software/systemd/man/systemd.target.html
https://www.freedesktop.org/software/systemd/man/systemd-journald.service.html
http://man7.org/linux/man-pages/man5/systemd.cgroup.5.html
http://linux.die.net/man/8/xinetd
