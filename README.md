# ClearLog
 clear log in **/var/log** in Ubuntu 18.04

## Prepare

* Open **/etc/logrotate.d/rsyslog**, comment "notifempty"  line. The modified **/etc/logrotate.d/rsyslog** may be like: 

  > ```shell
  > /var/log/syslog
  > {
  > 	rotate 7
  > 	daily
  > 	missingok
  > #	notifempty
  > 	delaycompress
  > 	compress
  > 	postrotate
  > 		/usr/lib/rsyslog/rsyslog-rotate
  > 	endscript
  > }
  > 
  > /var/log/mail.info
  > /var/log/mail.warn
  > /var/log/mail.err
  > /var/log/mail.log
  > /var/log/daemon.log
  > /var/log/kern.log
  > /var/log/auth.log
  > /var/log/user.log
  > /var/log/lpr.log
  > /var/log/cron.log
  > /var/log/debug
  > /var/log/messages
  > {
  > 	rotate 4
  > 	weekly
  > 	missingok
  > #	notifempty
  > 	compress
  > 	delaycompress
  > 	sharedscripts
  > 	postrotate
  > 		/usr/lib/rsyslog/rsyslog-rotate
  > 	endscript
  > }
  > ```
## Running command

```shell
sudo ./run_logrotate_30_times
```

You can check the log file content in **/var/log**. If everything is ok, there are new log files generated just now.