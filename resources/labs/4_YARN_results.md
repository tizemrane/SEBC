Fastest Teragen
[tarek@n2 ~]$ ./YARNtest.sh
Testing loop started on Tue Oct 16 23:17:28 UTC 2018
nb mappers = 8
nb reducers = 8
memory = 1024

real    4m35.174s
user    0m12.850s
sys     0m2.201s

Slowest Teragen
[tarek@n2 ~]$ ./YARNtest.sh
Testing loop started on Tue Oct 16 23:47:59 UTC 2018

nb mappers = 14
nb reducers = 7
memory = 2048

real    10m32.819s
user    0m14.526s
sys     0m2.581s


Fastest Terasort ==> with parameter yarn.scheduler.minimum-allocation-mb=512M
[tarek@n2 ~]$ ./YARNtest.sh
Testing loop started on Tue Oct 16 23:29:41 UTC 2018
nb mappers = 14
nb reducers = 7
memory = 512

real    12m24.810s
user    0m18.260s
sys     0m2.966s

Slowest Terasort
[tarek@n2 ~]$ ./YARNtest.sh
Testing loop started on Tue Oct 16 23:47:59 UTC 2018
nb mappers = 14
nb reducers = 7
memory = 2048

real    25m34.810s
user    0m15.972s
sys     0m3.143s
