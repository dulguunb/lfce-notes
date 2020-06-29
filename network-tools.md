
# New tooling

| net-tools | iproute2        |
|-----------:|---------------:|
| ifconfig   |ip addr, ip link|
|ifconfig (interface stats)|ip -s link|
| route  | ip route |
|arp | ip neigh |
|netstat | ss |
|netstat -M | conntrack -L |
|netstat -g | ip maddr |
|netstat -i | ip -s link |
|netstat -r | ip route |
| iptunnel  |ip tunnel |
|ipmaddr |ip maddr|
|tunctl | ip tuntap (since iproute-2.6.34)|
|(none) for interface rename | ip link set dev OLDNAME name NEWNAME|
| brctl |bridge (since iproute-3.5.0) |