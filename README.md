# NetMonitor

### Version 1.0.1

=======

## Description

This tool monitors the network status from _inside_ the server.  There have been occurances where a server is inaccessible from the outside appearing to be locked up, requiring a reboot only to find that once the server has been rebooted that the logs show that all services were running the whole time and it only appears as if the network layer has gone missing (i.e. the Ethernet cable has been unplugged). The problem is that a a reboot alone would not fix a cable unplugged.  It would, however, resolve a network layer issue.  That's that this attempts to do since there's no logging of the network layer itself.

## Usage

Basically, clone the repo to the folder you want (i.e. `/opt/netmonitor`), then setup a CRON job to run at the desired intervals.

    * * * * * /opt/netmonitor/netmonior

## Log

There's nothing output to STDOUT, it's just sent to the log located at `/var/log/network_monitor.log`.  The log file continues until it's 10MB in size, at which point the log rotator does it's job, then `network_monitor.log` becomes `network_monitor.log.1` and a new `network_monitor.log` file is created.  A total 7 logs are kept (6 backups and the current live one).

During testing, over the course of 12 hours and running each minute during that 12 hour period, the log file was 238KB, so that's 476KB per day.  That should give you about 21 days per log, giving a grand total of about 126 days of data. Your mileage may vary based on failures or a more/less frequent logging interval setup in your CRON.

=======
## License
This work is licensed under the Creative Commons Attribution-ShareAlike 4.0 International License. To view a copy of this license, visit http://creativecommons.org/licenses/by-sa/4.0/.