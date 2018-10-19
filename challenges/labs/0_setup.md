### Cloud provider : AWS

```
### Linux release
[tarek@t1 ~]$ cat /etc/centos-release
CentOS release 6.5 (Final)

### Disk space

Filesystem      Size  Used Avail Use% Mounted on
/dev/xvde1      148G  977M  140G   1% /
tmpfs           7.2G     0  7.2G   0% /dev/shm

### yum repolist enabled

[tarek@t1 ~]$ yum repolist enabled
Loaded plugins: fastestmirror, presto
Determining fastest mirrors
 * base: mirror.23media.de
 * epel: mirror.23media.de
 * extras: ftp.rz.uni-frankfurt.de
 * updates: mirror.23media.de
epel                                                                                                                    12515/12515
repo id                                    repo name                                                                          status
base                                       CentOS-6 - Base                                                                     6,713
epel                                       Extra Packages for Enterprise Linux 6 - x86_64                                     12,515
extras                                     CentOS-6 - Extras                                                                      33
updates                                    CentOS-6 - Updates                                                                    205
repolist: 19,466

```

### /etc/passwd entries for raffles and fullerton 

```
[tarek@t1 ~]$ sudo tail -2 /etc/passwd
raffles:x:2000:3002::/home/raffles:/bin/bash
fullerton:x:3000:3001::/home/fullerton:/bin/bash
```

### /etc/group entries for hotels and shops 

```
[tarek@t1 ~]$ sudo tail -2 /etc/group
hotels:x:3001:
shops:x:3002:
```

