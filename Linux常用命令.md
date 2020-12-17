#### 查看磁盘空间
```
df -h
du -sh *
```

#### TOP命令
```
top - 14:26:21 up 10 days,  1:40,  0 users,  load average: 0.10, 0.17, 0.20
Tasks:  23 total,   1 running,  22 sleeping,   0 stopped,   0 zombie
%Cpu(s):  2.0 us,  1.5 sy,  0.0 ni, 96.4 id,  0.0 wa,  0.0 hi,  0.0 si,  0.0 st
KiB Mem : 16777216 total,   745240 free,  5347116 used, 10684860 buff/cache
KiB Swap:        0 total,        0 free,        0 used.   745240 avail Mem

   PID USER      PR  NI    VIRT    RES    SHR S  %CPU %MEM     TIME+ COMMAND
  1353 admin     20   0 8609592   4.9g  79380 S  26.6 30.7   3308:26 java
   477 root      20   0 2475236  20444   6072 S   1.0  0.1  84:19.11 staragentd
  1115 root      39  19 3043452  50600  19580 S   1.0  0.3 107:53.92 argusagent
   916 root      20   0  130784  44776  12988 S   0.7  0.3  94:53.15 ilogtail
     1 root      20   0   90108  14772   6536 S   0.0  0.1  32:33.56 systemd
   399 root      20   0  231544  12020  10684 S   0.0  0.1   0:00.43 syslog-ng
   438 root      20   0  108296   7468   6492 S   0.0  0.0   0:08.52 sshd
   442 root      20   0  124244   3204   2536 S   0.0  0.0   0:06.61 crond
   914 root      20   0   50644   4272   2780 S   0.0  0.0   0:00.00 ilogtail
  3188 root      20   0   40208   4736   1908 S   0.0  0.0   0:00.00 tengine
  3191 admin     20   0    4240    664    588 S   0.0  0.0   0:00.00 cronolog
  3192 admin     20   0    4372   1300   1200 S   0.0  0.0   0:11.94 cronolog
  3193 admin     20   0   40208   4948   2120 S   0.0  0.0   0:00.00 tengine
  3194 admin     20   0   54544  15808   3948 S   0.0  0.1   4:02.11 tengine
  3195 admin     20   0   54544  15880   4012 S   0.0  0.1   4:04.16 tengine
  3196 admin     20   0   54544  15808   3948 S   0.0  0.1   3:58.91 tengine
  3197 admin     20   0   54544  15808   3948 S   0.0  0.1   4:03.36 tengine
  3198 admin     20   0   54544  15808   3948 S   0.0  0.1   4:06.03 tengine
  3199 admin     20   0   54544  15808   3948 S   0.0  0.1   3:57.01 tengine
  3200 admin     20   0   54544  15808   3948 S   0.0  0.1   4:00.02 tengine
  3201 admin     20   0   54544  15780   3920 S   0.0  0.1   3:57.31 tengine
153108 admin     20   0  115980   4100   3132 S   0.0  0.0   0:00.03 bash

```