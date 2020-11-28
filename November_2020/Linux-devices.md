# Devices
## /dev directory
When you connect a device to your machine, it would need a **device driver** to function properly.
You can interact with device drivers through *device files or device nodes*. These are special files that look like regular files.
> Device files are generally in the /dev directory
> /dev/null: Any output you send to it, the driver will discard it.


### Device Types

```
$ ls -l /dev
brw-rw----   1 root disk      8,   0 Dec 20 20:13 sda
crw-rw-rw-   1 root root      1,   3 Dec 20 20:13 null
srw-rw-rw-   1 root root           0 Dec 20 20:13 log
prw-r--r--   1 root root           0 Dec 20 20:13 fdata
```
Device files are denoted as the following:
 - c - character
 - b - block
 - p - pipe
 - s - socket


**Character Device**: These devices transfer data, but one character at a time. These devices aren't physically connected to the machine, but they allow the operating system greater functionality (eg /dev/null).
**Block Device**: These devices transfer data, but in large *fixed-sized blocks* (eg hard-drives/file-systems).
**Pipe Device**: Allows two or more processes to communicate with each other (ie these are similar to character devices, but instead is sending output to another process)
**Socket Device**: Facilitate communication between *multiple* processes.
**Device Characterization**: Devices are characterized using two numbers (major device number/minor device number) (eg 8, 0)
 - Major device number represents the **device driver** that is used (eg 8 often means sd block devices).
 - Minor device number tells the kernel which unique device is in the driver class (eg 0 is used to represent the first device (a)).


### Device Names
Most Common device names you will encounter:
**SCSI Devices** (AKA Small Computer System Interfaces): 
If you are using any sort of mass storage, you are most likely using SCSI ("scuzzy") protocol. This protocol allows you to communicate between
 - disks
 - printers
 - scanners
 - other peripherals to your system
Examples:
 - /dev/sda - First hard disk
 - /dev/sdb - Second hard disk
 - /dev/sda - Third partition on the first hard disk

**Pseudo Devices**: They aren't physically connected to your system
 - /dev/zero - accepts and discards all input, produces a continuous stream of NULL (zero value) bytes
 - /dev/null - accepts and discards all input, produces no output
 - /dev/random - produces random numbers

**PATA Devices**: Sometimes older systems use hard drives referenced with an hd prefix.
 - /dev/hda - First hard disk
 - /dev/hdd2 - Second partition on the 4th hard disk


## sysfs
**sysfs**: A virtual filesystem, often mounted to the /sys directory
 - It produces more detailed information than what we would be able to see in the /dev directory
> /sys filesystem contains all the information for all devices on your system such as state of the device, manufacturer, model, where the device is plugged in, and more.
```bash
JoshuEo➜  ~  ᐅ  ls /sys/block/sda
alignment_offset  device             events_poll_msecs  inflight   ro      subsystem
bdi               discard_alignment  ext_range          queue      size    uevent
capability        events             hidden             range      slaves
dev               events_async       holders            removable  stat
```


## udev
You can create device nodes using a command like:
```bash
$ mknod /dev/sdb1 b 8 3
# This will create a block device with a major number of 8 and minor number of 3 in the /dev/sdb1 node
```
> To remove a device, use "rm <device file>"
But with the power of udev, the system dynamically creates and removes device files for us depending on whether or not they are connected.
With the **udevadm** command, you can view the udev database and sysfs.
```bash
$ udevadm info --query=all --name=/dev/sda
```


## lsusb, lspci, lssci
These commands are similar to the ls command, but they specifically list information about devices.
Listing USB Devices: $ lsusb
Listing PCI Devices: $ lspci
Listing SCSI Devices: $ lsscsi


## dd
A useful command for converting and copying data.
```bash
$ dd if=/home/pete/backup.img of=/dev/sdb bs=1024
```
if=file - Input file, read from a file instead of standard input
of=file - Output file, write to a file instead of standard output
bs=bytes - Block size, it reads and writes this many bytes of data at a time. You can use different size metrics by denoting the size with a k for kilobyte, m for megabyte, etc, so 1024 bytes is 1k
count=number - Number of blocks to copy.

You will see some dd commands that use the count option, usually with dd if you want to copy a file that is 1 megabyte, you'll usually want to see that file as 1 megabyte when it's done being copied.
```bash
$ dd if=/home/pete/backup.img of=/dev/sdb bs=1M count=2
```
Our backup.img file is 10M, however, we are saying in this command to copy over 1M 2 times, so only 2M is being copied, leaving our copied data incomplete. Count can come in handy in many situations, but if you are just copying over data, you can pretty much omit count and even bs for that matter. If you really want to optimize your data transfers, then you'll want to start using those options.

dd is extremely powerful, you can use it to make backups of anything, including whole disk drives, restoring disks images, and more. Be careful, that powerful tool can come at a price if you aren't sure what you are doing.
