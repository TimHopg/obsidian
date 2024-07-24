#todo #School42 #Programming 

[Github gemartin](https://github.com/gemartin99/Born2beroot-Tutorial/blob/main/README_EN.md)

As of _2024-05-14_ [[Debian]] Bookworm 12.5 is the latest stable version.
Oracle VM Virtual Box
`/sgoinfre/thopgood` goinfre is french for gluttony. s must be student
Add Debian download to `sgoinfre` folder
#### Installing Virtual Machine
Create new virtual machine in Virtual Box
Change name, folder and ISO image
Check `Skip Unattended Installation`
1024MB RAM
1 CPU
30GB HDD (for bonus) (12GB otherwise)
Start
Scaled sizing

_[[LVM]]_ - Logical Volume Manager. Dynamic volume system
`/var` - holds variable data files that are expected to grow and shrink [[/var]]

Password requirements: 10 chars, 1 upper, 1 lower, 1 number no more than 3 consecutive chars.
	must not include name of user. Must contain at least 7 chars that are not part of the previous password.

host name:  login name then 42: __thopgood42__
password: Rootpassword1!
domain name: left blank
username: thopgood (login name)
password: Palavrapasse1!

Bonus
Manual disk set up
* Select SCSI
* pri/log FREE SPACE
* Create new partition

_there can only be four primary partitions per hdd or 3 primary and one extended_
_there can be only one secondary partition_
_logical - occupies entire primary or part of it. max 15 for linux_

* 500m, primary (because it's the OS destination), beginning
* mount point /boot
* create new in FREE SPACE
* max size, logical, mount point = none
* configure encrypted volumes
* encrypt the larger drive

* configure logical volume manager
* create volume group
* Name: LVMGroup
* Select encrypted partition
* Create Logic Volume, select LVMGroup
* root, 10g
* swap, 2.3g
* home, 5g
* var, 3g
* srv, 3g
* tmp, 3g
* var-log, 4g (only one dash is required. two will be created by the installer)

* then configure file systems and mount points
* home (click partition size to select) use as: ext4, mount point: home
* root, ext4, root
* srv, ext4, srv
* swap, swap area, 
* tmp, ext4, tmp
* var, ext4, var
* var-log, ext4, /var/log
* finish and write to disk

Decline all additional packages
Choose country and best mirror
Blank proxy info
Decline stats
Remove all software
Install GRUB on our device

_[[GRUB Bootloader]]_ - allows user to choose which kernel or OS to use when booting

_apt_ - apt is a frontend tool that focuses on high level package management and lets tools like dpkg take care of low level management
_aptitude_ - is more feature rich and advanced with an interactive interface based on ncurse. it doesn't come as standard so needs to be installed

`lsblk` - list block devices

#### Installing sudo
`su -` - effectively log in as super user. to allow root permissions
`apt-get update -y` - updates package lists `-y` automatically answer yes
`apt-get upgrade -y` - upgrades package lists found `-y` automatically answer yes
`apt install sudo` - install high level package manager [[sudo]]
`sudo reboot` - for changes to take effect
`sudo -V | more` - check sudo version, with pages. or `| less` or  `> SudoVersion.txt`
`sudo adduser thopgood`
`sudo addgroup user42`
`getent group user42` - (get entries) checks group was created successfully
or `cat /etc/group/` - edits group info (to check if user is present in sudo and user42
`sudo adduser thopgood <groupname>` - sudo and user42
`groups user` - shows groups user is part of
// `sudo usermod -aG sudo thopgood` - adds user to sudo group `-a` append `-g` groups
#### Installing SSH
`sudo apt update`
`sudo apt install openssh-server` - open ssh server allows incoming communication over SSH
`sudo service ssh status` - to check it is enabled
`sudo apt install vim`
`su -` - switch to root
`vim /etc/ssh/sshd_config` - edit the ssh config file from root
`Port 4242`
`PermitRootLogin no`
`vim /etc/ssh/ssh_config` - edit the ssh config file from root
`Port 4242`
`sudo service ssh restart` - to allow changes to take place
`sudo service ssh status` - check ports 4242 are open
_ssh_ secure shell
_sshd_ secure shell daemon - the server component
#### Configuring UFW
_ufw_  - uncomplicated firewall. command line tool for managing firewall rules (setting up iptables)
_firewall_ - monitors incoming and outgoing activity based on rules
`sudo apt install ufw`
`sudo ufw enable`
`sudo ufw allow 4242` - allows connections of port 4242
`sudo ufw status verbose` - checks
#### Setting up sudo policies
`touch /etc/sudoers.d/sudo_config` - sudoers.d allows modular configs without changing original sudoers directory
`mkdir /var/log/sudo` - to log commands, input and output
`vim /etc/sudoers.d/sudo_config`:

```
Defaults  passwd_tries=3
Defaults  badpass_message="Incorrect password: Three tries allowed"
Defaults  logfile="/var/log/sudo/sudo_config"
Defaults  log_input, log_output
Defaults  iolog_dir="/var/log/sudo"
Defaults  requiretty
Defaults  secure_path="/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/snap/bin"
```

`log_input, log_output` - logs inputs from user and output (result of those commands)
`logfile` - sudo commands log
`requiretty` - requires teletypewriter for sudo commands ie not scripts
`secure_path` - only executables located in these paths will be run
#### Password Policy
`vim /etc/login.defs`
`PASS_MAX_DAYS 30` - days until exp
`PASS_MIN_DAYS 2` - days before password can be changed
`PASS_WARN_AGE` - days til warning

`sudo apt install libpam-pwquality -y` - install PAM modules for password quality
_PAM_ - pluggable authenitcation modules
`vim /etc/pam.d/common-password`

`password requisite pam_pwquality.so` - on the same line as
`retry=3`
`minlen=10`
`ucredit=-1` - 1 minimum uppercase (-1 so it's minimum, +5 would be max of 5 etc.)
`dcredit=-1` - 1 digit
`lcredit=-1` - 1 lowercase
`maxrepeat=3`
`reject_username` cannot contain username
`difok=7` - at least 7 different chars to previously
`enforce_for_root` - same rules for root password
#### Connecting via SSH
Configure network settings of virtual machine.
`Network > Advanced > Port Forwarding` - [[Port Forwarding]]
Add new rule with Host Port as `4243` and Guest Port as `4242`
Virtual Box will move the request to port `4242` so it's the same

// `hostname -i` gets host ip address [[hostname]]
// REMOTE HOST ID HAS CHANGED
// `ssh-keygen -R '[localhost]:4243` - the exact ip/hostname from the error msg

`ssh thopgood@localhost -p 4243` - connects to the virtual machine
#### Creating the Script
1. __ARCHITECTURE:__ `uname -a`
	* unix name prints details about the machine (`-a` - all) [[uname 1]]
2. __PHYSICAL CORES:__ `grep "physical id" /proc/cpuinfo | sort-u | wc -l`
	* no. of physical cores searches for phrase in folder
	* [[sort]] -u (unique) ignores duplicates
	* pipes to word count which returns number of lines [[wc 1]] [[grep 1]]
3. __VIRTUAL CORES:__ `grep ^processor /proc/cpuinfo | wc -l`
	* lines beginning with processor, pipes to word count (lines)
	* no. of virtual cores
4. __RAM TOTAL:__ `free --mega | awk '$1 == "Mem:" {print $2}'`
	* total memory field
	* `--mega` - for megabytes (MB) otherwise `-M` returns mebibytes (MiB) which are slightly smaller
1. __RAM USED:__ `free --mega | awk '$1 == "Mem:" {print $3}`
	* [[free 1]] displays free and used memory then pipes to [[awk 1]] which if 1st ($1) field is equal to string prints what's in the 3rd ($3) field (used memory). in `--mega`bytes as requested. 
2. __RAM PERCENTAGE:__ `free --mega | awk '$1 == "Mem:" {printf("(%.2f%%)\n", $3/$2*100)}'`
	* used memory / total memory * 100 for percentage. `%%` to print percent `%.2f` - 2 decimal places
3. __DISK MEMORY TOTAL:__  `df -BG | awk '$1 ~ /^\/dev\// && $NF != "/boot" {tot += $2} END {print tot}'`
	* [[du 1|df]] (disk filesystem) `-BG` - blocks in gigabytes (not gibis)
	* `awk` command checks if `$1` first field matches (`~`) the following REGEX
	* `/^\/dev\//` - a forward slash at each end delimits the expression, `^` caret states beginning of field, `\/` backslash escapes the forward slash = `"^/dev/"`
	* i.e. any entry in the first field that starts with `"/dev/"`
	* if that is true and also `$NF` (last field (number of fields)) doesn't contain `/boot`
	* then total adds what is found in `$2` (second field).
	* Possibly issue, `G` might be _gibibytes_ not gigabytes, but `g` produces the same results...
1. __DISK MEMORY USED:__ `df -BM | awk '$1 ~ /^\/dev\// && $NF != "/boot" {used+=$3} END {print used}'`
	* see disk memory total
2. __DISK MEMORY PERCENTAGE:__ `printf "%.0f" "$(echo "scale=4; (($disk_use / 1024) / $disk_tot) * 100" | bc)"`
	* `printf "%.0f"` - rounds to nearest whole percentage point
	* `echo` sends following line to [[bc 1]] (basic calculator) including `scale=4` - accuracy of 4 decimal places
	* Uses previously assigned variables `disk_use` & `disk_tot`
3. __CPU LOAD:__ `top -bn1 | grep '^%Cpu' | awk '{printf("%.1f%%"), $2 + $4}'`
	* [[top]] (table of processes). `-b` batch mode `-n1` - 1 iteration of processes
	* greps the line near the top that begins with `%Cpu`
	* `awk` prints a float to 1dp and % sign of the sum of fields 2 and 4 (count the spaces) in the grep result
4. __LAST BOOT:__ `who -b | awk '$1 == "system" {print $3 " " $4}'`
	* [[who]] shows who is logged on. `-b` shows time of last system boot
	* if the first field (`$1`) is "system", prints 3rd field (date) and 4th (time)
	* may require $5 fifth field also depending on date format
5. __LVM ACTIVE?:__ `lsblk -o TYPE | grep -qw "lvm" && echo "yes" || echo "no"`
	*  `grep -q` quiet mode, stops when it finds one and quiets the output `-w` complete word
	* `lsblk -o` - list block, output `TYPE` column only
6. __ACTIVE CONNECTIONS:__`ss -t state established | wc -l`
	* [[ss]] socket stats `-t` shows TCP sockets
7. __LOGGED USER COUNT:__ `users | wc -w`
	* [[users]] prints users and word count `-w` prints number of words
8. __IP ADDRESS:__ `hostname -I | awk '{print $1}'`
	* `hostname -I` returns all IP addresses of the host excluding loopback addresses
	* `awk` - prints the first field
9. __MAC ADDRESS:__ `ip link show | grep "ether" | awk '{print $2}'`
	* `ip link` is used to manage network interfaces. `show` shows detailed info
	* `awk` prints second field, the MAC address
10. __SUDO COMMAND COUNT:__ `journalctl _COMM=sudo | grep COMMAND | wc -l`
	* `journalctl` - queries the systemd journal specifically for `sudo` in the `_COMM` column
	* grep filters for only COMMANDS and counts the number of results
11. __WALL__:
	* Write all
#### Finished Script:
```shell
#!/usr/bin/env bash  
  
#Architecture  
arch=$(uname -a)  
  
#CPUs  
cpu_phys=$(grep "physical id" /proc/cpuinfo | sort -u | wc -l)  
cpu_vir=$(grep "^processor" /proc/cpuinfo | wc -l)  
  
#RAM  
ram_tot=$(free --mega | awk '$1 == "Mem:" {print $2}')  
ram_use=$(free --mega | awk '$1 == "Mem:" {print $3}')  
ram_per=$(free | awk '$1 == "Mem:" {printf("%.2f"), $3/$2*100}')  
  
#Disk Usage  
disk_tot=$(df -BG | awk '$1 ~ /^\/dev\// && $NF != "/boot" {tot += $2} END {print tot}')  
disk_use=$(df -BM | awk '$1 ~ /^\/dev\// && $NF != "/boot" {used+=$3} END {print used}')  
disk_per=$((($disk_use * 100) / ($disk_tot *1024)))  
  
#CPU Load  
cpu_load=$(top -bn1 | grep '^%Cpu' | awk '{printf("%.1f%%"), $2 + $4}')  
  
#Last boot  
boot_last=$(who -b | awk '$1 == "system" {print $3 " " $4}')  
  
#LVM Use?  
lvm=$(lsblk -o TYPE | grep -qw "lvm" && echo "yes" || echo "no")  
  
#TCP Connections  
tcp=$(ss -t state established | wc -l)  
  
#User Count  
user_count=$(users | wc -w)  
  
#IP and MAC Address  
ip=$(hostname -I | awk '{print $1}')  
mac=$(ip link show | grep "ether" | awk '{print $2}')  
  
#Number of sudo Commands  
cmds=$(journalctl _COMM=sudo | grep COMMAND | wc -l)  
  
wall " #Architecture: $arch  
#CPU physical: $cpu_phys  
#vCPU: $cpu_vir  
#Memory Usage: $ram_use/${ram_tot}MB ($ram_per%)  
#Disk Usage: $disk_use/${disk_tot}Gb ($disk_per%)  
#CPU load: $cpu_load  
#Last boot: $boot_last  
#LVM use: $lvm  
#Connections TCP: $tcp ESTABLISHED  
#User log: $user_count  
#Network: IP $ip ($mac)  
#Sudo: $cmds cmd"
```

Save script in `/home/thopgood/monitoring.sh`
#### Scheduling with Crontab
`sudo crontab -u root -e` - user root editor
`*/10 * * * * sh /home/thopgood/monitoring.sh`
* /minutes (/10)/hours/day of month/month/day of week/file type/path
### Bonus
#### Lighttpd
A super lean web server consumes less CPU and RAM than others (Apache, NGINX (Engine X))
`sudo apt install lighttpd -y`
`sudo ufw allow 80` - opens port 80
Port 80 allows communication in plain text
`sudo ufw status` - to check it was successful
Also add rules in Network Settings on Virtual Box
#### WordPress
_Wordpress_ is a content management system for creating websites.
`sudo apt install wget zip` - install wget and zip
_wget_ - allows downloading of files from the net on the command line
_zip_ - archive too
`cd /var/www/` 
`sudo wget https://wordpress.org/latest.zip` - download latest version of WordPress
`sudo unzip latest.zip`
`sudo mv html/ html_old/` - rename `html` folder to `html_old`
`sudo mv wordpress/ html` - rename `wordpress` folder to `html`
`sudo chmod -R 755 html` - mod the permissions to all for owner, 5 = read and execute for group and others. `-R` recursive
#### MariaDB
_MariaDB_ is a database management system.
`sudo apt install mariadb-server` - installs mariadb
`sudo mysql_secure_installation` - to make MariaDB more secure
* DO NOT enter root password
* Unix socket authentication: N -> we already have protected root account
* Change the root password: N
* Remove anonymous users: Y -> anonymous users mainly used for testing before production environment
* Disallow root login remotely: Y -> only able to connect to root from localhost
* Remove test database and access to it: Y
* Reload privilege tables: Y
In home/thopgood: `mariadb`
`CREATE DATABASE wp_database;`
`SHOW DATABASES;` - to check
`CREATE USER 'thopgood'@'localhost' IDENTIFIED BY '12345';` - creates user inside database
`GRANT ALL PRIVILEGES ON wp_database.* TO 'thopgood'@'localhost';`
`FLUSH PRIVILEGES;` - to allow changes to take effect
`exit;` - quit MariaDB
#### PHP
_PHP_ is a programming language. Used to develop web apps and websites on the server side.
`sudo apt install php-cgi php-mysql` - CGI is for web apps, CLI is for standalone apps, mysql is for databases

To test php is working with lighty, create a file in `/var/www/html` named `info.php`. In that php file, write:

```PHP
<?php
phpinfo();
?>
```

Save and go to host browser and type in the address `http://127.0.0.1:8080/info.php`. You should get a page with PHP information.
#### Configure WordPress
`cd /var/www/html`
`cp wp-config-sample.php wp-config.php` - copy and rename config file
`vim wp-config.php` - edit config file
* DB_NAME, 'wp_database'
* DB_USER, 'thopgood'
* DB_PASSWORD, '12345'
`sudo lighty-enable-mod fastcgi` - improves speed/performance of web apps
`sudo lighty-enable-mod fastcgi-php` - improves speed/performance of PHP apps
`sudo service lighttpd force-reload` - allows changes to take effect
#### BUG FIXES
Updated PHP version
Changed port forwarding rule from 80 to 8080 and left guest port as 80
[mcombeau github](https://github.com/mcombeau/Born2beroot/blob/main/guide/bonus_debian.md)
#### Setup
Open browser and navigate to `localhost:8080`
input username, site name, password: 12345
Install
`localhost/wp-admin` - to make changes
### Additional Services
#### LiteSpeed
_LiteSpeed_ is a proprietary web server. Used by an estimated 10% of websites
`wget -O - https://repo.litespeed.sh | sudo bash` - litespeed repo.sh is a script that simplifies the installing and management of litespeed packages.
`wget -O - http://rpms.litespeedtech.com/debian/enable_lst_debian_repo.sh | sudo bash` - adds repository for Debian
`sudo apt install openlitespeed` - installs openlitespeed
`sudo /usr/local/lsws/admin/misc/admpass.sh` - to change the default password
`sudo ufw allow 8088/tcp` - openlitespeed runs on 8088
`sudo ufw allow 7080/tcp` - openlitespeed webadmin console
Update port forwarding in network settings to reflect new ports being used
`localhost:7080`
#### Obtaining Signature
`shasum machinename.vdi`
Add output to `signature.txt` which is uploaded to repo
`shasum` determines the integrity of a file by using the SHA-1 has check sum.
#### Passwords
host name: thopgood42  
Rootpassword1!  
user name: thopgood  
Palavrapasse1!  
encryption phrase:  
Penguin42!  
group  
user42  
GID 1001  
db password: 12345  
site name:  
Thopgood WP  
username: wp-thopgood  
password: 12345  
openlitespeed  
username: idroot  
pass: Palavrapasse1!  
newuser  
Password12345
#### Notes
`sudo cryptsetup luksChangeKey /dev/sda5` to change passkey
`sudo ufw status numbered` - displays ufw rules numbered
`sudo ufw delete 3` - deletes rule 3
vmwgfx error - change display settings to VboxVGA
`sudo apt list --installed` - shows all installed packages
`free -m = mebibytes`
`free --mega = megabytes`
`tmpfs` - Temporary File System - stored in RAM not on SSD or HDD. Fast but volatile. Do not include in total disk space
#### References
[[born2beroot 1]]
[[Shell Commands 1]]
[PasqualeRossi Guide](https://github.com/pasqualerossi/Born2BeRoot-Guide)
[GE Martin Guide](https://github.com/gemartin99/Born2beroot-Tutorial/blob/main/README_EN.md)
[Mcombeau bonus](https://github.com/mcombeau/Born2beroot/blob/main/guide/bonus_debian.md)

_2024-05-14 17:04_