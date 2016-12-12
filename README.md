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