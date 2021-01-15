## 12/1/2020

1. Linux Inodes:
  - Inode is a data structure that stores various information about a file in Linux, such as the access mode (read, write, execute), ownership, file type, file size, group, number of links, etc.
  - Each inode is identified by an integer number (eg 123014) which is assigned to a file when it is created
```bash
$ ls -il
total 12
5575 drwxr-xr-x. 2 <user> users 4096 Nov 30 09:45 bin
131127 drwxrwxr-x. 5 <user> users 4096 Nov  6 09:07 labs
131778 drwxr-xr-x. 4 <user> users 4096 Nov 30 09:41 Practice
```
2. Practicality of inode
 - If your disk is giving an error that you don't have enough space, even though you do
 - This may be caused from **inode exhaustion** where you've used too many inodes (Every file needs an inode. So no matter the space you have, you can't add more data to your filesystem).
```bash
# How to see the amount of inodes you've used/have left
$ df -i
Filesystem                     Inodes IUsed   IFree IUse% Mounted on
/dev/mapper/vg_cmsy255-lv_root 2334720 75710 2259010    4% /
tmpfs                 	       240221     1  240220    1% /dev/shm
/dev/sda1             	       128016    62  127954    1% /boot
```

3. Command "stat": This command displays the status of the file or file system.
```bash
$ stat bin
  File: `bin'
  Size: 4096            Blocks: 8          IO Block: 4096   directory
Device: fd00h/64768d    Inode: 5575        Links: 2
Access: (0755/drwxr-xr-x)  Uid: (  760/    <user>)   Gid: (  100/   users)
Access: 2020-11-30 09:45:51.832427445 -0500
Modify: 2020-11-30 09:45:46.922225392 -0500
Change: 2020-11-30 09:45:46.922225392 -0500
```


> Inodes do not store the content of the file and filename
Resource: https://geek-university.com/linux/inode/#:~:text=An%20inode%20is%20a%20data,file%20when%20it%20is%20created.


## 12/2/2020
1. **Homomorphic encryption**: A form of encryptiong allowing one to initially perform calculations on encrypted data without decrypting it first.
  - When decrypted, the output is the same as if the operations had been performed on the unencrypted data.
  - Microsoft SEAL is one type of homomorphic encryption

2. **Pretexting**: Creating a believable scenario to trick the victim into releasing personal information.

3. **Digital Living Network Alliance**: An organization working to standardize different kinds of appliance s and network devices used in our homes

4. **Digital Rights Management (DRM)**: System of access that allows only **limited** use of material that's been legally purchased

5. **Blockchain**: A centered source where cryptocurrency transactions are kept.

## 12/7/2020
1. All about Git 
