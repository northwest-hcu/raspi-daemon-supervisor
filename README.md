
$sudo apt-get install supervisor
(Install supervisor)


$supervisord -v
(If you can see your supervisor version, installation is success.)


< write config file like this content as /home/pi/example.conf (/home/pi/example.conf is your like file name 
and .conf) >

[program:ProName] ;Proname is your process name when you start process.
process_name=ProName_process ;Proname_process is your process_name. If you set this parametor, your process name 
is "ProName:ProName_process".
command=node index.js ;Here is command you want to do as daemon.(example:node index.js)
directory=/home/pi/Daemon/ ;Here is directory where you want to do the process.
autostart=true ;Process start automatically enabled or disabled.
autorestart=true ;Process restart automatically enabled or disabled.
user=pi ;Boot user
redirect_stderr=true ;Standard error outputting enabled or disabled.
stdout_logfile=/home/pi/log/err.log ;Where this process log file.


$mv  /home/pi/example.conf /etc/supervisor/conf.d/example.conf
(move file to under /etc/supervisor/conf.d/)


$sudo reboot
(please reboot your PC)


$sudo supervisor status
(you can see your supervisor process name, status, pid, uptime)


$sudo supervisor stop ProName:ProName_process
(you can stop daemon "ProName")


$sudo supervisor start ProName:ProName_process
(you can start daemon "ProName")


$sudo supervisor restart ProName:ProName_process
(you can restart daemon "ProName")


Reference source https://creepfablic.site/2020/04/01/raspberrypi-supervisor-daemon/
