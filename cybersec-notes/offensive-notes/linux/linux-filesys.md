## Linux File System – Short Notes

### 1. What It Is

The Linux file system is the method used by Linux to organize, store, and manage files and directories. Everything in Linux is treated as a file — including devices and processes.



### 2. Hierarchical Structure

Linux uses a **tree-like structure** that starts from the root directory:

```
/
```

All files and folders branch out from this root.



### 3. Important Directories

* `/` → Root directory (top of the hierarchy)
* `/home` → User personal files
* `/bin` → Essential user commands
* `/etc` → Configuration files
* `/var` → Log and variable data files
* `/usr` → Installed software and libraries
* `/dev` → Device files
* `/tmp` → Temporary files



### 4. File Types in Linux

* Regular files
* Directories
* Device files
* Symbolic links
* Pipes
* Sockets



### 5. File Permissions

Each file has:

* Owner
* Group
* Others

With three permission types:

* Read (r)
* Write (w)
* Execute (x)

### 6. Key Features

* Case-sensitive
* Supports multiple users
* Strong security through permissions
* Everything is treated as a file

---

## Linux Root (`/`) Directories and Their Uses


Below are the main directories directly under `/` and what each one is used for (based on the Filesystem Hierarchy Standard).



### `/` – Root

The top-level directory. Everything in Linux starts from here.



### `/bin` – Essential User Binaries

Contains basic command programs needed for system operation (e.g., `ls`, `cp`, `mv`).
Required for booting and single-user mode.



### `/sbin` – System Binaries

Contains important system administration commands (e.g., `fsck`, `reboot`).
Mostly used by the system or administrator.



### `/boot` – Boot Files

Stores files needed to start the system:

* Linux kernel
* Bootloader files (e.g., GRUB)



### `/dev` – Device Files

Contains special files representing hardware devices:

* Hard disks
* USB devices
* Printers
  In Linux, devices are treated like files.



### `/etc` – Configuration Files

Stores system-wide configuration settings:

* Network configuration
* User account settings
* Service configuration



### `/home` – User Home Directories

Contains personal folders for users.
Example: `/home/student`



### `/root` – Root User Home

Home directory of the system administrator (root user).



### `/lib` and `/lib64` – Shared Libraries

Contain essential libraries required by programs in `/bin` and `/sbin`.



### `/usr` – User Programs & Data

Contains installed software, libraries, and documentation.
Not for personal user files.

Subdirectories include:

* `/usr/bin`
* `/usr/lib`
* `/usr/share`



### `/var` – Variable Data

Stores files that change frequently:

* Log files (`/var/log`)
* Mail
* Print spool files



### `/tmp` – Temporary Files

Stores temporary data created by programs.
Files may be deleted automatically after reboot.



### `/opt` – Optional Software

Used for installing third-party software packages.



### `/media` – Removable Media

Mount point for USB drives, CDs, etc.



### `/mnt` – Temporary Mounts

Used to manually mount filesystems temporarily.



### `/proc` – Process Information (Virtual Filesystem)

Provides information about running processes and system status.
Files are generated dynamically by the kernel.



### `/sys` – System Information

Virtual filesystem containing hardware and kernel information.



### `/srv` – Service Data

Stores data for services provided by the system (e.g., web server files).



## Short Summary Table

| Directory | Purpose              |
| ------ | -------------------- |
| `/bin`    | Essential commands   |
| `/etc`    | Configuration files  |
| `/home`   | User files           |
| `/var`    | Logs & variable data |
| `/usr`    | Installed software   |
| `/dev`    | Device files         |
| `/proc`   | Process/system info  |
| `/tmp`    | Temporary files      |



