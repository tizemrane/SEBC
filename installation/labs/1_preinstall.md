### 1. Check vm.swappiness on all your nodes
#### Set the value to 1 if necessary
```
[tarek@ip-172-31-24-141 ~]$ cat /proc/sys/vm/swappiness
60
[tarek@ip-172-31-24-141 ~]$ sudo sed -i '$a\vm.swappiness=1' /etc/sysctl.conf
[tarek@ip-172-31-24-141 ~]$ sudo sysctl -p
net.ipv4.ip_forward = 0
net.ipv4.conf.default.rp_filter = 1
net.ipv4.conf.default.accept_source_route = 0
kernel.sysrq = 0
kernel.core_uses_pid = 1
net.ipv4.tcp_syncookies = 1
kernel.msgmnb = 65536
kernel.msgmax = 65536
kernel.shmmax = 68719476736
kernel.shmall = 4294967296
vm.swappiness = 1
```

### 2. Show the mount attributes of all volumes
```
[tarek@ip-172-31-24-141 ~]$ cat /etc/mtab | grep ext4
/dev/xvde1 / ext4 rw 0 0
```

### 3. Show the reserve space of any non-root, ext-based volumes
at this point we have only a root disk 

### 4. Disable transparent hugepage support
In my AMI the transparent hugepage support is desabled by default.
here is the used AMI : https://aws.amazon.com/marketplace/pp/B00A6KUVBW?ref=cns_1clkPro
 ```
 [tarek@ip-172-31-24-141 ~]$ sudo cat /sys/kernel/mm/transparent_hugepage/enabled
cat: /sys/kernel/mm/transparent_hugepage/enabled: No such file or directory

 ```

### 5. List your network interface configuration
```
[tarek@ip-172-31-24-141 ~]$ ifconfig
eth0      Link encap:Ethernet  HWaddr 06:63:93:14:28:F8
          inet addr:172.31.24.141  Bcast:172.31.31.255  Mask:255.255.240.0
          UP BROADCAST RUNNING MULTICAST  MTU:9001  Metric:1
          RX packets:4004 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2784 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:307859 (300.6 KiB)  TX bytes:310103 (302.8 KiB)
          Interrupt:24

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)

```

### 6. List forward and reverse host lookups using getent or nslookup

```
[root@n1 ~]# for f in 172.31.24.141 n1.sebcdomain 172.31.19.154 n2.sebcdomain 172.31.24.226 n3.sebcdomain 172.31.26.160 n4.sebcdomain 172.31.29.200 n5.sebcdomain ; do getent hosts $f; done
172.31.24.141   n1.sebcdomain
172.31.24.141   n1.sebcdomain
172.31.19.154   n2.sebcdomain
172.31.19.154   n2.sebcdomain
172.31.24.226   n3.sebcdomain
172.31.24.226   n3.sebcdomain
172.31.26.160   n4.sebcdomain
172.31.26.160   n4.sebcdomain
172.31.29.200   n5.sebcdomain
172.31.29.200   n5.sebcdomain
```

### 7. Show the nscd service is running

```
[tarek@n1 ~]$ sudo service nscd status
nscd: unrecognized service
```

we need to install it

```
[tarek@n1 ~]$ sudo yum install nscd
...
[tarek@n1 ~]$ sudo service nscd start
Starting nscd:
[tarek@n1 ~]$ sudo service nscd status
nscd (pid 1069) is running...
```

### 8. Show the ntpd service is running

```
[tarek@n1 ~]$ sudo service ntpd status
ntpd: unrecognized service

```

we need to install it

```
[tarek@n1 ~]$ sudo yum install ntp
...
[tarek@n1 ~]$ sudo service ntpd start
Starting ntpd: 
[tarek@n1 ~]$ sudo service ntpd status
ntpd (pid  1230) is running...

```