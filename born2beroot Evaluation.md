Evaluation Q&A #
##### Q: Why Debian?
A: It's easier to install and configure than CentOS.
##### Q: What is virtual machine?
A: A Virtual Machine (VM) is a computer resource that uses software instead of a physical computer to run programs and deploy apps. Each virtual machine runs its own operating system and functions separately from the other VMs, even when they are all running on the same host. For example, you can run a virtual MacOS machine on a physical PC. 
##### Q: What it's purpose?
A: VMs may be deployed to accommodate different levels of processing power needs, to run software that requires a different operating system, or to test applications in a safe, sandboxed environment. 
##### Q: How does it works?
A: VM working through "Virtualisation" technology. Virtualisation uses software to simulate virtual hardware that allows VMs to run on a single host machine.
##### Q: Diff between aptitude and APT?
A: Aptitude is a high-level package manager while APT is lower-level package manager which can be used by other higher-level package managers 
(read more: https://www.tecmint.com/difference-between-apt-and-aptitude/)
##### Q: What is AppArmor?
A: AppArmor ("Application Armor") is a Linux kernel security module that allows the system administrator to restrict programs'
capabilities with per-program profiles.
(read more: https://en.wikipedia.org/wiki/AppArmor)
##### Q: What is SSH?
A: SSH, also known as Secure Shell or Secure Socket Shell, is a network protocol that gives users, particularly system administrators, a secure way to access a computer over an unsecured network.
(read more: https://searchsecurity.techtarget.com/definition/Secure-Shell)
##### Create new user
*`$ sudo adduser username`*
`creating new user (yes (no))
*`$ sudo chage -l username`*
`Verify password expire info for new user
*`$ sudo adduser username sudo`*
*`$ sudo adduser username user42`*
`assign new user to sudo and user42 groups`
##### Q: How your script works?
A: [[born2beroot 1]]
### Part two: What to check? 

|     |                                   |                                                              |
| --- | --------------------------------- | ------------------------------------------------------------ |
| 1   | `lsblk`                           | Check partitions                                             |
| 2   | `sudo aa-status`                  | AppArmor status                                              |
| 3   | `getent group sudo`               | sudo group users                                             |
| 4   | `getent group user42`             | user42 group users                                           |
| 5   | `sudo service ssh status`         | ssh status, yep                                              |
| 6   | `sudo ufw status`                 | ufw status                                                   |
| 7   | `ssh username@ipadress -p 4242`   | connect to VM from your host (physical) machine via SSH      |
| 8   | `nano /etc/sudoers.d/<filename>`  | yes, `sudo config file`. You can `$ ls /etc/sudoers.d` first |
| 9   | `nano /etc/login.defs`            | password expire policy                                       |
| 10  | `nano /etc/pam.d/common-password` | password policy                                              |
| 11  | `sudo crontab -l`                 | cron schedule                                                |

I think this one needs an addition to make it more easy to pass evaluation. So, here we are on our checklist and its commands.
##### How to change hostname?
`sudo nano /etc/hostname
##### Where is sudo logs in `/var/log/sudo?`
`$cd /var/log/sudo/00/00 && ls

You will see a lot of directories with names like 01 2B 9S 4D etc. They contain the logs we need.

`$ sudo apt update
`$ ls`

Now you see that we have a new directory here.
`$ cd <nameofnewdirectory> && ls
`$ cat log` - Input log
`$ cat ttyout` - Output log
##### How to add and remove port 8080 in UFW?
`$ sudo ufw allow 8080` - allow
`$ sudo ufw status` - check
`$ sudo ufw deny 8080` - deny (yes yes)
##### How to run script every 30 seconds?
`$ sudo crontab -e]`
Remove or commit previous cron "schedule" and add next lines in crontab file

 `*/1 * * * * /path/to/monitoring.sh
`*/1 * * * * sleep 30s && /path/to/monitoring.sh

To stop script running on boot you just need to remove or commit the following line in crontab file.
`@reboot /path/to/monitoring.sh

#### References
[[born2beroot]]