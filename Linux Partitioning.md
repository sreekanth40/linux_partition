# Linux Partitioning and Persistence
##### Assignment dated 25 May 2025



## Commands used
After login to the user account once the Linux OS is successfully launched.

First come to root user (#) and home directory (~) by entering command 
- command:          sudo -i 

1. Identify an available disk (e.g., /dev/sdb)
- command           fdisk -l
2. Create a new partition
- command          fdisk /dev/sda
- option                     n
- Partition number   5 press enter until the partition created
- option                      w (for writing the partition to the table)
- option                      q (to exit the fdisk command)

3. Format the new partition with ext3 filesystem
- command                mkfs.ext3 /dev/sda5

4. Mount the partition /mnt/mypartition

   As the first step we need to create the mount point directory as /mnt/mypartition
   - command         mkdir /mnt/mypartition
   
   Now we need to mount the new partition on the mount point directory.
   - command         mount /dev/sda5 /mnt/mypartition
  
 
