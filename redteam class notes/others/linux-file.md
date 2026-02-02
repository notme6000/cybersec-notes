## Linux file system

- _in linux everything is a file_
- _most system resources can be accessed through file operations (`open, read, write, close`)_

#### Types of files in linux
- Text files -> files
- Directory -> files
- Hard drives -> files
- USB devices -> files
- System info -> files

#### single directory tree
- linux has one root directory

/
|- bin
|- boot
|- dev
|- etc
|- home
|- lib
|- lib64
|- media
|- mnt
|- opt
|- proc
|- root
|- run
|- sbin
|- srv
|- sys
|- tmp
|- usr
|- var


- no `C:` or `D:`
- external drives are mounted into the tree
- example
    `/media/usb`
    `/mnt/external_disk`

#### essential system directories 

---

1. __/bin__

- `/bin` - essential user binaries
- basic commands needed for the system to work:
- Examples
    - ls
    - cp
    - mv
    - cat
    - bash
- available to all users
- merged (syslinks)
- `/bin = /usr/bin`

---

2. __/sbin__

- administrative commands (mostly root-only)
- Examples
    - mount 
    - fsck
    - reboot
    - ip
- merged (syslinks)
- `/sbin = /usr/sbin`
- difference in some distros

---

3. __/lib and /lib64__

- system libraries required by _/bin_ and _/sbin_
- example 
    - _libc.so_
    - kernel modules
- /lib -> x86
- /slib -> x64
 
---

4. __/boot__

- bootloader & kernel
- contains
    - linux kernel (vmlinuz)
    - initramfs
    - GRUB config
- if _/boot_ is broken -> system won't start

---

5. __/etc__

- configuration & user data
- almost everything here is plain text
- Examples:
    - /etc/passwd -> user accounts
    - /etc/shadow -> encrypted passwords
    - /etc/fstab -> filesystem mount rules
    - /etc/hostname 

---

6. __/home__ 

- user home directories
- each user gets a folder
    - _/home/alice_
    - _/home/bob_
- contains:
    - Documents
    - Downloads
    - Desktop files
    - User-specific config (.bashrc, .config)

---

7. __/root__

- _/root_ - root user's home
- home directory for the administrator
- not the same as _/_

---

8. Variable 

- _/var_ - variable data
- data that changes during normal operations
- subdirectories:
    - _/var/log_ -> system logs
    - _/var/cache_ -> cached data 
    - _/var/spool_ -> main, print jobs 
- Examples:
    - _/var/log/syslog_
    - _/var/log/auth.log_

---

9. __/tmp__

- temporary files
- used by programs
- often cleared on reboot

---

10. __/run__

- runtime data
- stores temporary runtime information
    - PID files
    - sockets
    - system state
- recreated every boot

---

11. __/dev__

- Devices and virtual filesystems
- Hardware appears as files
- Examples : 
    - _/dev/sda_ -> hard disk
    - _/dev/sda1_ -> partition 
    - _/dev/tty -> terminal 
    - _/dev/null -> discard output 

---

12. __/proc__

- process & kernel info 
- not real files on disk
- Examples: 
    - _/proc/cpuinfo_
    - _/proc/meminfo_
    - _/proc/1234/_ -> process with PID 1234

---

13. __/sys__

- hardware & kernel interface
- modern replacement of _/proc_
- used to inspect devices
- change kernel parameters

---

14. __/usr__

- user applications
- contains
    - _/usr/bin_
    - _/usr/lib_
    - _/usr/share_
- most installed software lives here
    - python
    - git 
    - vim
    - firefox

---

15. __/opt__

- optional software
- add-on application software packages
- its own bin, lib, and icons
- Examples : 
    - /opt/google/
    - /opt/brave-bin

---

16. __/srv__

- data for services provided by the system
- Examples:
    - web server files
    - FTP data

---

