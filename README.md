#doDBA

The doDBA tools is a console-based remote system monitor. 
that does not require special software on the remote system.
it collects real-time performance data from linux and MySQL. 
And can generate a doing file to help you analyze the MySQL database.
This program is free software.doDBA is written in go.

Author:dblucyne@gmail.com

WeChat:doDBA

#Download
```
wget https://raw.githubusercontent.com/dblucyne/dodba_tools/master/doDBA --no-check-certificate
wget https://raw.githubusercontent.com/dblucyne/dodba_tools/master/doDBA.conf --no-check-certificate
chmod +x doDBA
```
or
```
git pull https://github.com/dblucyne/dodba_tools
```

#help
```
./doDBA -help
Usage: doDBA [OPTIONS]
  -help
        Display this help.
  -c string
        configuration file. (default "doDBA.conf")
  -h string
        Connect to host/IP.
  -sys
        Print system info.
  -myall
        Print system and mysql info.
  -mysql
        Print mysql info.
  -innodb
        Print innodb info.
  -mytop
        Print mysql prcesslist info , like top.
  -i duration
        refresh interval in seconds. (default 1s)
  -t int
        mysql doing on Threads_running. (default 50)
  -hP string
        Connect host port. (default "22")
  -hp string
        Connect host password.
  -hu string
        Connect host user. (default "root")
  -mP string
        Connect mysql port. (default "3306")
  -mp string
        Connect mysql password.
  -mu string
        Connect mysql user.
  -rds
        Ignore system info.
  -log
        Print to file by day.
  -nocolor
        Print to nocolor.
```

#Configuration 
```
doDBA.conf
{
    "Host":"",
    "Huser": "root",
    "Hport": "22",
    "Hpwd":  "",
    "Muser": "dodba",
    "Mpwd":  "dodba",
    "Mport":"3306"
}

For example:
./doDBA -c=doDBA.conf
```
#Example 
```
./doDBA -h=10.1.xx.xx -myall

DoDBA tools on host 10.1.xx.xx
---------+---load--avg---+-----cpu-usage-----+-swap+----net----+----mysql-status-------+-slow---th---+---bytes---
time     |   1m   5m  10m| usr  sys  iow  ide|si so| recv  send|QPS  TPS  ins  upd  del| sql run  con| recv  send
---------+---------------+-------------------+-----+-----------+-----------------------+-------------+-----------
13:52:00 | 4.00 3.68 3.60| 0.7  0.3  0.0 99.0| 0  0| 316K  4.3M|203   58   22   36    0|   0   2   52|  86K  1.8M
13:52:01 | 4.00 3.68 3.60| 5.3  0.3  0.1 94.3| 0  0| 275K  2.0M|251   67   27   40    0|   0   3   76| 104K  3.2M
13:52:02 | 4.00 3.68 3.60| 6.4  0.5  0.1 93.0| 0  0| 371K  4.1M|380  810   24  786    0|   0   3   40| 311K  5.0M
13:52:03 | 4.00 3.68 3.60| 5.4  0.4  0.0 94.2| 0  0| 510K  4.2M|648  283   30  253    0|   1   3   52| 216K  1.4M
13:52:04 | 4.00 3.68 3.60| 5.7  0.4  0.0 93.8| 0  0| 385K  2.7M|108   69   45   24    0|   0   4   48|  71K  2.1M
13:52:05 | 3.92 3.66 3.59| 6.2  0.5  0.0 93.3| 0  0| 206K  2.0M|339   96   52   44    0|   0   3   37| 107K  1.9M
```

```
./doDBA -h=10.1.xx.xx -myall -rds
DoDBA tools on host 10.1.xx.xx
---------+----load--avg----+-----cpu-usage-----+swap+----net----+-----mysql-status------+-slow---th---+---bytes---
time     |   1m    5m   10m| usr  sys  iow  ide|siso| recv  send|QPS  TPS  ins  upd  del| sql run  con| recv  send
---------+-----------------+-------------------+----+-----------+-----------------------+-------------+-----------
17:19:17 | 0.00  0.00  0.00| 0.0  0.0  0.0  0.0| 0 0|   0K    0K|144  155   73   82    0|   0   1    5| 113K  229K
17:19:18 | 0.00  0.00  0.00| 0.0  0.0  0.0  0.0| 0 0|   0K    0K| 66  113   32   81    0|   0   2    6|  79K  109K
17:19:19 | 0.00  0.00  0.00| 0.0  0.0  0.0  0.0| 0 0|   0K    0K|273  117   30   87    0|   1   2   20| 135K  502K
17:19:20 | 0.00  0.00  0.00| 0.0  0.0  0.0  0.0| 0 0|   0K    0K|207  173   74   99    0|   1   2   17| 137K  279K
17:19:21 | 0.00  0.00  0.00| 0.0  0.0  0.0  0.0| 0 0|   0K    0K|161  233  105  128    0|   0   1    5| 146K  193K
```

```
./doDBA -h=10.1.xx.xx -myall -t=3
2016/12/14 11:47:52 ----------------processlist---------------
ID:606374462
User:ums_read
Host:10.1.xx.xx:31886
DB:mia
Command:Query
Time:3121
State:Sending data
Info:SELECT ......................

=====================================
2016-12-14 11:49:16 7f93ece24700 INNODB MONITOR OUTPUT
=====================================
Per second averages calculated from the last 1 seconds
-----------------
BACKGROUND THREAD
-----------------
srv_master_thread loops: 11256164 srv_active, 0 srv_shutdown, 27867 srv_idle
srv_master_thread log flush and writes: 11284031
----------
SEMAPHORES
----------
OS WAIT ARRAY INFO: reservation count 1562657988
OS WAIT ARRAY INFO: signal count 11589318962
Mutex spin waits 7915500772, rounds 7044249291, OS waits 29061199
RW-shared spins 15964124137, rounds 99809511531, OS waits 1188604739
RW-excl spins 1056480533, rounds 26766008869, OS waits 261290579
........................................
```
#image 

![alt](https://raw.githubusercontent.com/dblucyne/dodbaimg/master/system.png)

![alt](https://raw.githubusercontent.com/dblucyne/dodbaimg/master/mysql.png)

![alt](https://raw.githubusercontent.com/dblucyne/dodbaimg/master/mytop.png)