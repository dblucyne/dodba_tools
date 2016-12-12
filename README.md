#doDBA

The doDBA tools is a console-based remote system monitor. 
that does not require special software on the remote system.
it collects real-time performance data from system and MySQL. 
And can generate a trace file to help you analyze the MySQL database.
This program is free software.
doDBA is written in go.

#Download

git clone https://github.com/dblucyne/dodba_tools
cd dodba_tools/
chmod +x doDBA 

#Usage
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
        mysql trace on Threads_running. (default 50)
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
        Print to file by day.
        
#Configuration 
for json:
{
    "Host":"",
    "Huser": "root",
    "Hport": "22",
    "Hpwd":  "",
    "Muser": "dodba",
    "Mpwd":  "dodba",
    "Mport":"3306"
}

#Example 
./doDBA -h=10.1.xx.xx -mysql