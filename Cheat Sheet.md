# Linux Enumeration Cheat Sheet


## Find SUID or Programs Accessbile to User:
```
find / -perm -4000 2>/dev/null 

find / -perm -u=s -type f 2>/dev/null

find / -name user.txt 2>/dev/null
```
## Get Capabilites
```
getcap -r / 2>/dev/null - get capapbilities
```
## Find Commands
```
find. -name flag.txt
find /home -name flag.txt
find / -type d -name config
find / -type f -perm 0777
find / -perm a=x
find /home -user frank
find / -mtime
find / -atime
find / -cmin
find / -amin
find / -size +/- 50m
find / -writable -type d 2>/dev/null
find / -writable -type f 2>/dev/null
find / -perm -222 -type d 2>/dev/null
find / -perm -o w -type d 2>/dev/null
find / -perm -o x -type d 2>/dev/null
find / -name python*
```
## Basic Enumeration Commands
```
ls /etc/*-release                                                        -> looks for version numbers

cat /etc/os-release                                                      -> cat out the file with the version numbers

hostname                                                                 -> return hostname of target

cat /etc/passwd                                                          -> read passwd file for possible users

cat /etc/group                                                           -> read groups for possible users

sudo cat /etc/shadow                                                     -> read out shadow file for password hashes

ls -lh /var/mail                                                         -> checks mail directories

ls /usr/bin/ & /sbin                                                     -> for applications 

rpm -qa                                                                  -> list installed packages on RPM linux distro

dpkg -l                                                                  -> list installed packages on Debian linux distro

who                                                                      -> shows logged in users

whoami                                                                   -> shows what user you are logged in as

w                                                                        -> shows who is logged in and what they are doing

id                                                                       -> gives you your current UID and Group

last                                                                     -> displays login and logout info for users

sudo -l                                                                  -> what commands we can run sudo as
```
## Networking Enumeration
```
ip a s                                                                   -> shows current ip

cat /etc/resolv.conf                                                     -> shows the DNS servers

netstat -> shows info about network connections
	-a -> show both listening and non-listening sockets
	-l -> show only listening sockets
	-n -> show numeric output instead of resolving the IP address and port number
	-t -> TCP
	-u -> UDP
	-x -> UNIX
	-p -> show the PID and name of the program to which the socket belongs

sudo netstat -atupn                                                      -> show all TCP / UDP listening and established conn with ports

sudo lsof -i                                                             -> List of open files

sudo lsof - :port number                                                 -> Checks for open files on a specific port
```
## Running Services
```
ps 									 -> snapshot of running process on the machine
	-e -> all processes
	-f -> full-format listing
	-j -> jobs format
	-l -> long format
	-u -> user-orented format
	
ps aux 									 -> displays all processes
ps axjf 								 -> displays all processes in a "tree" format
```
