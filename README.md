#doDBA

The doDBA tools is a console-based remote system monitor. 
that does not require special software on the remote system.
it collects real-time performance data from system and MySQL. 
And can generate a trace file to help you analyze the MySQL database.
This program is free software.doDBA is written in go.

Authors:dblucyne@gmail.com

WeChat:doDBA

#Download
```
git clone https://github.com/dblucyne/dodba_tools
cd dodba_tools/
chmod +x doDBA 
```
#Usage
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