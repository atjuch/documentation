---
title: Parsing nginx Access Log with GoAccess
description: Learn how to parse the nginx-access.log file with GoAccess to gather information on your visitors and referral traffic.
keywords: log, access log, nginx access log, nginx log, nginx access
---
Pantheon uses nginx webservers for optimal performance. Events and activities of the webserver are recorded into log files which can be used to identify potential issues and gather information about users.

[GoAccess](http://goaccess.io/) is a free, open sourced utility that is used to create on the fly server reports by parsing the `nginx-access.log` file. Use it to quickly identify most used browsers and operating systems, or debug failed requests - all from the command line.

## Before You Begin

Be sure that you have:

- [Local copy of the target site environment's `nginx-access.log` file.](/docs/articles/sites/logs)
- [GoAccess](http://goaccess.io/) installed:
 - **Mac OS X**: Install via [homebrew](http://brew.sh/)
 - **Windows**: Use [Cygwin](http://cygwin.com/install.html)

## Edit GoAccess Configuration
To parse the Pantheon `nginx-access.log` file with GoAccess, we have to specify the unique log formats.

Add the following lines to the `goaccess.conf` file, located in either `/etc/`, `/usr/etc/` or `/usr/local/etc/` depending on your installation method:

```
time_format %H:%M:%S %z
date_format %d/%b/%Y
log_format %^ %^ %^ [%d:%t]  "%r" %s %b "%R" "%u" %T "%h"
```
## Generate Report
You can run the following command, which will parse the log file and open a dashboard in your terminal application so you may view the results:
```
goaccess -f nginx-access.log
```
If you would like to generate an HTML report, execute the following commands:
```
goaccess -f nginx-access.log > report.html
open report.html
```

## See Also
- [Log Files on Pantheon](/docs/articles/sites/logs)
- [Debugging Sites with Log Files](/docs/articles/sites/logs/debugging-sites-with-log-files)
- [MySQL Slow Log](/docs/articles/sites/logs/mysql-slow-log/)
- [PHP Slow Log](/docs/articles/sites/logs/php-slow-log/)
- [PHP Errors and Exceptions](/docs/articles/sites/php-errors-and-exceptions/)
- [Bots and Indexing](/docs/articles/sites/code/bots-and-indexing/)