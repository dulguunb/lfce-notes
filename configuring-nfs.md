# NFS architecture

===========
 NFS Server| --> client1 /mnt/share1
=========== --> client2 /mnt/share2
	    --> .... clientn
/share1
/share2

Transport Protocol: Default on v4(TCP) or UDP(default v3)
default PORT: TCP/2049 (Dynamically allocated)

# NFS services
RPS based services
Server side:
* nfs-server - TCP based service (Version4)
* rpcbind - manages RPC port reservations and connections (only needed for v3)

Client side:
* rpcbind

Version3 - RPC over UDP
Version4 - TCP (limited RPC)
Both v3 and v4 are installed when you install NFS and CENTOS 7.2

# NFS server configuration

exports - are shared resources
/etc/exports
 /share1  host(options)
exportfs - maintains a table of exported file

/var/lib/nfs/etab -> table contains runtime configuration about nfs server

/share1 server1.psdemo.local

Default options:

* ro (read-only)
* sync (reply when writes are commited on disk)
* wdelay (delayed disk writes)
* root_squash (changes root to anonymous)

Other common options:

* rw/ro - allow read/write access
* sync/async - write acknowledgments
* all_squash - all users mapped to an anonymous users

Authentication settings:

* sec=krb5(user authentication only), krb5i (+integrity checking) or krb5p (+integrity + encyption)
  (kerberos)

Hostname formats
Single machine
 Ip or Name
    server1.psdemo.local
IP networks
 CIDR Notations:
  192.168.2.0/25
 Range of Machines:
  * or ? character classes [a-z]
   * \*.psdemo.local
   * server?.psdemo.local
   * server[2-9].psdemo.local
# Mounting

## Runtime Mounting
```bash
mount -t nfs -o rw server0.psdemo.local:/share1 /mnt/share1

```
## Persistent mounting
/etc/fstab

```bash
server0.psdemo.local:/share1 /mnt/share1 nfs rw 0 0
```

## Dynamic/On Demand mounting
autofs

/etc/nfsmount.conf configuration file for NFS mounts

Common NFS Client Options

ro - readonly
sync - wait for write confirmations
nosid - don't allow setuid programs
noexec - don't allow exection of binary
soft - error if server is offline
sec=krb5,krbi5 or krb5p - use Kerberos authentication method
port - use specified port

> Demo

server0: 

server1: sudo mount -t nfs server0.psdemo.local:/share1 /mnt

