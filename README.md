# LinEnum
For more information visit www.rebootuser.com

Note: Export functionality is currently in the experimental stage.

General usage:

version 0.6

* Example: ./LinEnum.sh -k keyword -r report -e /tmp/ -t 

OPTIONS:
* -k	Enter keyword
* -e	Enter export location
* -t	Include thorough (lengthy) tests
* -r	Enter report name
* -h	Displays this help text


Running with no options = limited scans/no output file

* -e Requires the user enters an output location i.e. /tmp/export. If this location does not exist, it will be created.
* -r Requires the user to enter a report name. The report (.txt file) will be saved to the current working directory.
* -t Performs thorough (slow) tests. Without this switch default 'quick' scans are performed.
* -k An optional switch for which the user can search for a single keyword within many files (documented below).

See CHANGELOG.md for further details

High-level summary of the checks/tasks performed by LinEnum:

* Kernel and distribution release details
* System Information:
  * Hostname
  * Networking details:
  * Current IP
  * Default route details
  * DNS server information
* User Information:
  * Current user details
  * Last logged on users
  * Shows users logged onto the host
  * List all users including uid/gid information
  * List root accounts
  * Extracts password policies and hash storage method information
  * Checks umask value
  * Checks if password hashes are stored in /etc/passwd
  * Extract full details for ‘default’ uid’s such as 0, 1000, 1001 etc
  * Attempt to read restricted files i.e. /etc/shadow
  * List current users history files (i.e .bash_history, .nano_history etc.)
  * Basic SSH checks
* Privileged access:
  * Determine if /etc/sudoers is accessible
  * Determine if the current user has Sudo access without a password
  * Are known ‘good’ breakout binaries available via Sudo (i.e. nmap, vim etc.)
  * Is root’s home directory accessible
  * List permissions for /home/
* Environmental:
  * Display current $PATH
  * Displays env information
* Jobs/Tasks:
  * List all cron jobs
  * Locate all world-writable cron jobs
  * Locate cron jobs owned by other users of the system
* Services:
  * List network connections (TCP & UDP)
  * List running processes
  * Lookup and list process binaries and associated permissions
  * List inetd.conf/xined.conf contents and associated binary file permissions
  * List init.d binary permissions
* Version Information (of the following):
  * Sudo
  * MYSQL
  * Postgres
  * Apache
    * Checks user config
    * Shows enabled modules
* Default/Weak Credentials:
  * Checks for default/weak Postgres accounts
  * Checks for default/weak MYSQL accounts
* Searches:
  * Locate all SUID/GUID files
  * Locate all world-writable SUID/GUID files
  * Locate all SUID/GUID files owned by root
  * Locate ‘interesting’ SUID/GUID files (i.e. nmap, vim etc)
  * List all world-writable files
  * Find/list all accessible *.plan files and display contents
  * Find/list all accessible *.rhosts files and display contents
  * Show NFS server details
  * Locate *.conf and *.log files containing keyword supplied at script runtime
  * List all *.conf files located in /etc
  * Locate mail
* Platform/software specific tests:
  * Checks to determine if we're in a Docker container
  * Checks to see if the host has Docker installed
  
  
  LinEnum是一个Linux主机本地信息自动提取的shell脚本，它有超过65项安全检查功能，比如潜在的SUID/GUID文件、Sudo/rhost错误配置等。另外这个脚本还可以根据关键字（比如Password）搜索*.conf和*.log文件，这些功能对于渗透测试人员来说，是非常有用的。

主要功能：
