# raspi-daemon-supervisor

## Step-by-step
### Install supervisor
#### Install via apt-get
`$ sudo apt-get install supervisor`
* If you can see your supervisor version, installation is success.
`$ supervisord -v`

### Writing configuration
* Save the below content as `/etc/supervisor/conf.d/example.conf` (Change `example.conf` as you like)
```
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
```

### Reboot
`$ sudo reboot`

### Check if the daemon is working properly
`$ sudo supervisor status`
* You can see your supervisor process name, status, pid, uptime

### Stop the daemon
`$ sudo supervisor stop ProName:ProName_process`
* You can stop daemon "ProName"

### Start the daemon
`$ sudo supervisor start ProName:ProName_process`
* You can start daemon "ProName"

### Restart the daemon
`$ sudo supervisor restart ProName:ProName_process`
* You can restart daemon "ProName"

## References
* https://creepfablic.site/2020/04/01/raspberrypi-supervisor-daemon/
