# Linux Partitioning and Persistence
##### Assignment dated 25 May 2025



## Commands used
After login to the user account once the Linux OS is successfully launched.

First come to root user (#) and home directory (~) by entering command 
- command:          sudo -i 

### 1. Identify an available disk (e.g., /dev/sdb)
- command           fdisk -l
### 2. Create a new partition
- command          fdisk /dev/sda
- option                     n
- Partition number   5 press enter until the partition created
- option                      w (for writing the partition to the table)
- option                      q (to exit the fdisk command)

### 3. Format the new partition with ext3 filesystem
- command                mkfs.ext3 /dev/sda5

### 4. Mount the partition /mnt/mypartition

   As the first step we need to create the mount point directory as /mnt/mypartition

   - command         mkdir /mnt/mypartition
   
   Now we need to mount the new partition on the mount point directory.
   - command         mount /dev/sda5 /mnt/mypartition

### 5. Create a file with a Fake Address

Navigate to the mount point directory from Home Directory.

- command             cd /mnt/mypartition

Create a new file with name address in this point with a fake address as its content

- command             vim address

To reveal the content of the file named address

- command             cat address


### 6. Persistence after reboot

To reveal the UUID of the new partition

- command          blkid /dev/sda5

Edit /etc/fstab to add the new partition

- command          vim /etc/fstsb

Add the new partition with the mount point directory, filesystem type, permission details, dump and pass values in the file and save (:wq)

To mount all the drives

- command         mount -a

To reboot the system

- command         reboot

To shutdown (Grace Shut down) the system

- command         shutdown -h now


### Contents of the /etc/fstab file

 /etc/fstab: static file system information.

 Use 'blkid' to print the universally unique identifier for a
 device; this may be used with UUID= as a more robust way to name devices
 that works even if disks are added and removed. See fstab(5).

 <file system> <mount point>   <type>  <options>       <dump>  <pass>
 
 / was on /dev/sda2 during curtin installation
/dev/disk/by-uuid/f881c102-dea0-478e-9b6e-65099d4ffa75 / ext4 defaults 0 1

 /home was on /dev/sda3 during curtin installation
/dev/disk/by-uuid/4fd9f6d5-c811-46fe-a871-cffb40e07f89 /home ext4 defaults 0 1

 /boot was on /dev/sda4 during curtin installation
/dev/disk/by-uuid/6e400bf4-24f9-4de8-ac77-3dbf5c521814 /boot ext4 defaults 0 1

/swap.img       none    swap    sw      0       0

/dev/sda5       /mnt/mypartition        ext3    defaults        0       0

### Output of ls /mnt/mypartition after reboot

root@ubuntu:~# ls /mnt/mypartition

address  lost+found






  
  
 
