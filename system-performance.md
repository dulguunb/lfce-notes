# Disk

Sectors 
 - Actual storage unit of disk, 512k or 4kb
 blocks (logical)
 - Fundamental unit of I/O, allocation
 Disks have finite performance characteristics
   - Bandwidth - how much data
   - Latency - how fast
Storage interconnects
   - Internal 
   - External
# Filesystem
XFS
Mount Time option
  - Access Time - noatime
  - Read only - ro

# sysstat

/etc/cron.d/sysstat
/var/log/sa -> sa${date}
/usr/lib64/sa/sa2 -A
 
/etc/sysconfig/sysstat

sar -q -> load average
sar -q -f sa${date} -> load average from old logs.

